---
title: "[HOWTO] Install Symfony2 with MySQL in ubuntu 11.10 (Oneiric)"
date: 2012-01-12
forum: Server Platforms
---

### Post by kevpatts on 2012-01-12
Hey all,

The installation procedure makes you install things in drips and drabs, so I thought I'd put up a no-nonsense install guide:

1. Install Ubuntu 11.10 server without any extra packages.
2. Run (putting in the appropriate timezone):```

sudo apt-get install -y unzip firefox git mysql-server mysql-admin apache2 php5 libapache2-mod-php5 php5-mysql php-apc php5-xsl php5-intl php5-sqlite acl
sudo sed -i "s/^short_open_tag = On$/short_open_tag = Off/" /etc/php5/apache2/php.ini
sudo sed -i "s/^;date.timezone =.*$/date.timezone = Europe\/Dublin/" /etc/php5/apache2/php.ini
sudo aptitude -y dist-upgrade
sudo usermod -a -G www-data `whoami`
sudo chown -R www-data:www-data /var/www
sudo chmod -R g+w /var/www
sudo reboot

```
3. Run:```

cd /var/www
wget http://symfony.com/get/Symfony_Standard_Vendors_2.0.9.zip
unzip Symfony_Standard_Vendors_2.0.9.zip
rm Symfony_Standard_Vendors_2.0.9.zip
cd Symfony
sudo setfacl -R -m u:www-data:rwx -m u:`whoami`:rwx app/cache app/logs
sudo setfacl -dR -m u:www-data:rwx -m u:`whoami`:rwx app/cache app/logs
./bin/vendors install --reinstall    # This can take a long time...
sudo chown -R www-data:www-data /var/www
```
4. I'd recommend running:```
sudo apt-get install -y ufw
sudo ufw default deny
sudo ufw allow ssh
sudo ufw allow http
sudo ufw enable
```
5. Set up a dedicated user and schema in "mysql-admin" and ensure that the user has full access to that schema
6. Then set the rest up through the we interface:```
firefox --no-remote http://localhost/Symfony/web/config.php
```

Done!

---

