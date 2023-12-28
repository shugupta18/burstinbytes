### Azure VM
- Make sure the port 80, 443 are *enabled*
- configure GoDaddy *properly*

### Ubuntu
```
ls -l privkey.pem
sudo chown shugupta18:shugupta18 /var/privkey.pem
```

### SET up site

**Become superuser:**
```
sudo su
```

**install nginx:**
```
apt update
apt install nginx
```

**install certbot:**
```
apt install certbot python3-certbot-nginx

sudo certbot --nginx -d burstinbutes.in -d www.burstinbutes.in
```

**make dir `/var/www`:**
```
mkdir -p /var/www
```

**git clone repo:**
```
cd /var/www
git clone https://github.com/shugupta18/burstinbytes.git
```

**configure nginx:**
```
scp /var/www/burstinbytes/burstinbytes /etc/nginx/sites-available

nano /etc/nginx/sites-available/burstinbytes
```

**update according to need nginx:**
```
# sites, url
```

**Create a symbolic link to enable the configuration:**
```
ln -s /etc/nginx/sites-available/burstinbytes /etc/nginx/sites-enabled/

ln -s /etc/nginx/sites-available/digitalorder.in /etc/nginx/sites-enabled/

```

**Test Nginx configuration:**
```
nginx -t
```

**Restart nginx:**
```
service nginx restart
```

**setup cron**
```
sudo crontab -e
0 */12 * * * certbot renew --quiet
```




