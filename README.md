# Nginx S3 File Upload Proxy
S3 file upload proxy using Nginx, complete with AWS authentication.

## References

- https://github.com/openresty/set-misc-nginx-module#installation

- https://www.vultr.com/docs/how-to-compile-nginx-from-source-on-ubuntu-16-04

## Installation

Create a `.env` file to hold your environment variables for Nginx. You can base on the `.env.example` file contained in root folder.

Using Docker, build the image.
```bash
$ docker build -t nginx/nginx-s3-upload .
```

After the image is built, create a container.
```bash
$ docker run -d -p 80:80 --env-file=.env nginx/nginx-s3-upload
```

## Usage

Once the container is running, give it a try!
```bash
$ curl -T path/to/file/to/upload http://nginx-s3-upload.yourdomain.com/uploads/entity/property/filename.extension
```

The response will contain a header, `X-File-URL`, with the location of the file on your S3 bucket.

## Adding Nginx to systemd as service

```bash
sudo cp nginx.service  /etc/systemd/system/nginx.service
```

## Enabling Nginx Service

```bash
sudo systemctl start nginx.service && sudo systemctl enable nginx.service

```
## Is Nginx Service enabled

```bash
sudo systemctl is-enabled nginx.service
```

## Start / Stop Nginx Service

```bash
sudo systemctl start nginx
sudo systemctl stop nginx
```

## License

nginx-s3-upload is released under the MIT license.
