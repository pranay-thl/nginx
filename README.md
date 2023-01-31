# NGINX Config



# How to configure nginx reverse proxy
- `sudo apt-get update`
- `sudo apt-get install nginx`
- `sudo unlink /etc/nginx/sites-enabled/default`
- `cd /etc/nginx/sites-available/`
- `vim nginx.conf`
- ```
    server {
        listen 80;
        location / {
            proxy_pass http://127.0.0.1:8080;
        }
    }
    ```
- `sudo ln -s /etc/nginx/sites-available/nginx.conf /etc/nginx/sites-enabled/nginx.conf`
- `sudo service nginx restart`
- `sudo service nginx configtest`

# How to setup firewall for nginx
- `sudo ufw app list`
- `sudo ufw allow 'Nginx FULL'`
- `sudo ufw allow ssh`
- `sudo ufw enable`
- `sudo ufw status`

# How to setup ssl
- `openssl req -new -newkey rsa:2048 -nodes -keyout mycert.key -out mycert.csr`
- `Paste ssl zip to location`
- `cat filename.crt filename_bundle.crt >> mycert.crt`
- `cp mycert.crt mycert.key /etc/nginx/ssl`
