---
title: "Can I install WordPress for local-only use on a normal desktop?"
date: 2021-02-23
forum: Server Platforms
---

### Post by Paddy Landau on 2021-02-23
I hope that this is the right forum for my query.

**Explanation of what I want**

[LIST=1]
[*]I have a few websites hosted by GoDaddy
[*]The websites are independent of each other (each has its own domain name, MySQL database, file storage area)
[*]I want to develop the websites on my machine rather than on the GoDaddy host (for speed)
[*]The sites need to be local only, because I don't have the skills to apply security against the wider internet
[*]However, the sites need to be able to access the internet, e.g. to install plugins and themes
[*]Once developed, I copy each website (files and MySQL database) to GoDaddy
[/LIST]
I know how to do step 6 (copy a website to a new domain name, area and database); I've done that many times.

But what I don't know is how to set up WordPress on my own machine.

I looked at the [Ubuntu tutorial for WordPress]("https://ubuntu.com/tutorials/install-and-configure-wordpress"). That method seems to be for local only, which is what I want. But, the method seems to allow for only one WordPress site, rather than multiple independent sites.

**Further information**

[LIST]
[*]I'm running a standard Ubuntu 20.04 desktop (not server)
[*]If security is too hard or problematic for my desktop, maybe I could install a server on a VirtualBox and use that as the server for my websites?
[/LIST]
Is there a "Local WordPress sites for Dummies" that I can follow to achieve this? It seems that it should be simple, but I don't understand the process and thus I could easily mess it up.

Thank you

---

### Post by ameinild on 2021-02-23
Yes it should be possible. I found the following link, which might help you (it's an older article, but I can't see why it shouldn't work).

[https://www.digitalocean.com/community/tutorials/how-to-set-up-multiple-wordpress-sites-on-a-single-ubuntu-vps](https://www.digitalocean.com/community/tutorials/how-to-set-up-multiple-wordpress-sites-on-a-single-ubuntu-vps)

Basically, what you have to do is "expand" the tutorial you linked to contain multiple sites in Apache, MySQL and Wordpress itself.

Good luck!

---

### Post by Paddy Landau on 2021-02-23
> **ameinild said:**
> … I found the following link, which might help you…
Thank you! I'll try it and see what happens.

---

### Post by kevdog on 2021-02-23
@Paddy Landau

You ever thought about using a combination of docker containers for wordpress? I'm assuming you'll need a database backend (mariadb or postgresql), a caching redis server, and likely a reverse proxy. With a reverse proxy such as caddy or traefik or nginx proxy manager you could even incorporate automatic retrieval and renewal of Let's Encrypt certificates if you wanted to be thorough in your testing.  I know Wordpress is tricky in terms of security and I like in these situations of relying on the container approach.

---

### Post by LHammonds on 2021-02-23
@Paddy Landau, what you want to accomplish is very possible.

Does not matter if you are running Ubuntu Desktop.  The Server and Desktop share the same core OS so installing MariaDB, Apache and PHP is the same process for either.

Being multi-site is also not a big deal.  However, most tutorials out there on the web just show you have 5 step install for a default site.  You need to setup separate folders for each wordpress site and configure apache to enable each one.

Example:
```

/var/www/my.coolsite.com
/var/www/his.coolsite.com

```

I would also create local DNS entries so my workstation would see "my.coolsite.com" and "his.coolsite.com" resolve to the local address.  ([Reference Example]("https://hammondslegacy.com/forum/viewtopic.php?p=848#p848"))

```
sudo vi /etc/hosts
```

```

127.0.0.1  my.coolsite.com
127.0.0.1  his.coolsite.com

```

Create apache config files for each site:

```

/etc/apache2/sites-available/my.coolsite.com.conf
/etc/apache2/sites-available/his.coolsite.com.conf

```

Test and enable each config:

```

sudo apache2ctl configtest
sudo a2ensite my.coolsite.com
sudo a2ensite his.coolsite.com

```

As long as you do not open ports on Ubuntu's firewall (assuming you have it enabled/running) and you do not have port-forwarding on your router/firewall to your PC, then those sites on your PC will not be accessible from the Internet but if you need to download files and whatnot, you should be able to do so since outbound traffic is rarely blocked...assuming your PC has Internet access (which it most-likely does).

You "could" set it up to be the exact same domain name as your GoDaddy site so all configurations such as links and the SITEURL / HOMEURL settings in the database will be 100% ready to be exported/imported.  But to access the GoDaddy sites instead of your local sites, you would need to edit your local hosts and remove the entries or change the IP address to match GoDaddy's.  The other option is to use a different URL but you will need to go through a preparation process before export/import on GoDaddy to fix the URL paths.  Be warned that if you use a different URL during development, you might run the risk of hard-coding links in your posts and not realizing it until you copy it to GoDaddy and later find that some things no longer work because they are pointing to a non-existing development URL.  Be sure to always use relative paths for all links to your own site so the ONLY URL you change when exporting to production is your SITEURL / HOMEURL variable in the database.  You should do this anyway as good practice (sometimes domain names change) but it is critically important when changing URLs from development to production.

LHammonds

---

### Post by Paddy Landau on 2021-02-25
> **kevdog said:**
> You ever thought about using a combination of docker containers for wordpress?
I had thought of a VM, but I hadn't thought of Docker — precisely because I don't understand how Docker works. I've tried looking it up, but everything that I found seems to be aimed towards someone who already understands it. I'd love to try, if you have a link to a simple how-to.
> **kevdog said:**
> I'm assuming you'll need a database backend (mariadb or postgresql)…
GoDaddy uses MySQL, so I should probably use the same for full compatibility.
> **kevdog said:**
> … a caching redis server, and likely a reverse proxy. With a reverse proxy such as caddy or traefik or nginx proxy manager you could even incorporate automatic retrieval and renewal of Let's Encrypt certificates if you wanted to be thorough in your testing.
Most of that I don't even understand! (I'm not sufficiently technical.) And, I hadn't thought about the SSL — unless it's easy to get around, that could prove to be a bit of a dealbreaker for me. I use Let's Encrypt on GoDaddy, using its API system, so I'm guessing that I can do the same on my machine.
> **kevdog said:**
> I know Wordpress is tricky in terms of security and I like in these situations of relying on the container approach.
That sounds wise.

Thank you for your help.

---

### Post by Paddy Landau on 2021-02-25
> **LHammonds said:**
> Being multi-site is also not a big deal.  However, most tutorials out there on the web just show you have 5 step install for a default site.  You need to setup separate folders for each wordpress site and configure apache to enable each one. …
Thank you. That makes it clearer.
> **LHammonds said:**
> I would also create local DNS entries so my workstation would see "my.coolsite.com" and "his.coolsite.com" resolve to the local address.
I've actually done something like this before, so it looks familiar to me.
> **LHammonds said:**
> Create apache config files for each site:
I don't know what goes in those files. I'm starting to worry that I've bitten off more than I can chew :confused:
> **LHammonds said:**
> As long as you do not open ports on Ubuntu's firewall…
At the moment, I haven't configured the firewall at all. I've depended on my router (and I haven't set up port forwarding). I shall have a look at the firewall.
> **LHammonds said:**
> You "could" set it up to be the exact same domain name as your GoDaddy site…
That's a clever idea, which I'll consider. I am aware of the tricky bits when moving a WordPress website from one domain to another. For that, I've used [InterconnectIT]("https://interconnectit.com/news/2009/10/07/migrating-a-wordpresswpmubuddypress-website/") as a great help.

Thank you for your advice.

---

### Post by LHammonds on 2021-02-25
> **Paddy Landau said:**
> I don't know what goes in those files. I'm starting to worry that I've bitten off more than I can chew
Nah, you'll do fine.  Start with the basics and add to it as needed.  Do not try to create the end-all-be-all config as a first step.  Just get it working enough so you can create a test php file to verify the basics are there.  Then add on bits specific for a WordPress site and test it.  Then add SSL if you want but that gets a bit trickier if your site is not accessible from the Internet for certbot to access.  For internal testing, you could just [create your own SSL certificate]("https://hammondslegacy.com/forum/viewtopic.php?p=849#p849") but you would then need to import the root cert into your browser so you do not get the warning about not being a trusted certificate authority.

Here is a basic config just so we can test that PHP works:

/etc/apache2/sites-available/my.coolsite.com.conf
```

<VirtualHost *:80>
  ServerAdmin webmaster@localhost
  ServerName my.coolsite.com
  ServerAlias my.coolsite.com
  DocumentRoot /var/www/my.coolsite.com
  ErrorLog ${APACHE_LOG_DIR}/my.coolsite.com-error.log
  CustomLog ${APACHE_LOG_DIR}/my.coolsite.com-access.log combined
</VirtualHost>

```

Test the site config file for any syntax errors:
```
sudo apache2ctl configtest
```

Enable the site config:
```
sudo a2ensite my.coolsite.com
```

Now create a test file:

```
echo "<?php phpinfo(); ?>" > /var/www/my.coolsite.com/phpinfo.php
chown www-data:www-data /var/www/my.coolsite.com/phpinfo.php
chmod 644 /var/www/my.coolsite.com/phpinfo.php
```

Open a browser and see if the test page shows up: [http://my.coolsite.com/phpinfo.php](http://my.coolsite.com/phpinfo.php)

Since you are testing the server on the same machine as the browser accessing it, there will be no firewall rules that will get in the way since you are not "crossing" the firewall line.  You would only need to worry about the firewall rules if you were to try and test this from another machine on your local network.

Once you verify the site is running and that you have all the modules enabled that WordPress requires, you can then proceed to install WordPress and make changes to the site config file as needed.  Example:

```

<VirtualHost *:80>
  ServerAdmin webmaster@localhost
  ServerName my.coolsite.com
  ServerAlias my.coolsite.com
  DocumentRoot /var/www/my.coolsite.com
  ErrorLog ${APACHE_LOG_DIR}/my.coolsite.com-error.log
  CustomLog ${APACHE_LOG_DIR}/my.coolsite.com-access.log combined
  <Directory /var/www/my.coolsite.com>
    Options FollowSymLinks
    AllowOverride Limit Options FileInfo
    DirectoryIndex index.php
    Order allow,deny
    Allow from all
  </Directory>
  <Directory /var/www/my.coolsite.com/wp-content>
    Options FollowSymLinks
    Order allow,deny
    Allow from all
  </Directory>
</VirtualHost>

```

Test and reload the apache configuration file.

```
sudo apache2ctl configtest
sudo systemctl apache2 reload
```

> **Paddy Landau said:**
> At the moment, I haven't configured the firewall at all. I've depended on my router (and I haven't set up port forwarding). I shall have a look at the firewall.

Here is a script I use to configure the firewall rules and turn it on...which will remain on even during a reboot.

You can copy this script and use it for your own purposes and tweak it for your environment.  Enough commands are used/documented in it that you should be able to modify it to fit your particular server.  For example, if running a web server, you can uncomment the commands to allow TCP port 80 and 443.

I NEVER simply copy this script and run it.  Each and every server requires a custom variation of this script tailored for it.  The application section has examples for commonly used services such as web, database, etc.  Feel free to uncomment lines you can use and modify to suit your needs.

/var/scripts/prod/en-firewall.sh ([GitHub Download]("https://github.com/LHammonds/ubuntu-bash/blob/20.04/en-firewall.sh"))
```
#!/bin/bash
#############################################################
## Name          : enable-firewall.sh
## Version       : 1.1
## Date          : 2017-04-13
## Author        : LHammonds
## Compatibility : Ubuntu Server 12.04 - 20.04 LTS
## Requirements  : Run as root
## Purpose       : Restore and enable firewall.
## Run Frequency : As needed
## Exit Codes    : None
###################### CHANGE LOG ###########################
## DATE       VER WHO WHAT WAS CHANGED
## ---------- --- --- ---------------------------------------
## 2015-08-28 1.0 LTH  Created script.
## 2017-04-13 1.1 LTH  Added comments in rules.
#############################################################

## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo -e "\nERROR: Root user required to run this script.\n"
  echo -e "Type 'sudo su' to temporarily become root user.\n"
  exit
fi

clear
echo ""
echo "Resetting Firewall to factory default"
echo y | ufw reset 1>/dev/null 2>&1
ufw default deny incoming 1>/dev/null 2>&1
ufw default allow outgoing 1>/dev/null 2>&1
echo "Allowing SSH from only LAN connections"
ufw allow from 192.168.1.0/24 to any port 22 comment 'SSH via LAN' 1>/dev/null 2>&1
echo "Allowing Samba file sharing connections"
ufw allow proto tcp to any port 135,139,445 comment 'Samba Share' 1>/dev/null 2>&1
ufw allow proto udp to any port 137,138 comment 'Samba Share' 1>/dev/null 2>&1
echo "Allowing Nagios connections"
ufw allow from 192.168.107.21 to any port 12489 comment 'Nagios' 1>/dev/null 2>&1
ufw allow from 192.168.107.21 proto tcp to any port 5666 comment 'Nagios' 1>/dev/null 2>&1
echo "Adding Application-specific rules"
#echo "Adding MySQL/MariaDB rules"
#ufw allow from 192.168.1.0/24 proto tcp to any port 3306 comment 'MariaDB via LAN' 1>/dev/null 2>&1
#ufw allow from 192.168.2.0/24 proto tcp to any port 3306 comment 'MariaDB via LAN' 1>/dev/null 2>&1
#echo "Adding FTP/FTPS rules"
#ufw allow proto tcp to any port 990 comment 'FTPS' 1>/dev/null 2>&1
#ufw allow proto tcp to any port 21 comment 'FTP' 1>/dev/null 2>&1
#ufw allow proto tcp to any port 2000:2020 comment 'FTP Passive' 1>/dev/null 2>&1
#echo "Adding Web Server rules"
#ufw allow proto tcp to any port 80 comment 'HTTP Service' 1>/dev/null 2>&1
#ufw allow proto tcp to any port 8080 comment 'HTTP Service' 1>/dev/null 2>&1
#ufw allow proto tcp to any port 443 comment 'HTTPS Service' 1>/dev/null 2>&1
echo "Enabling firewall"
echo y | ufw enable 1>/dev/null 2>&1
echo "Firewall enabled and all rules have been configured."

```

**EDIT:** Hopefully I did not miss any crucial bits, I did not sleep well.  If you have more questions / concerns, just post them.

---

### Post by Paddy Landau on 2021-02-25
> **LHammonds said:**
> Nah, you'll do fine…
Thanks so much for your help! I shall try to do all of this over the next couple of days, or maybe the weekend.

If I have further questions, I'll post again.

---

