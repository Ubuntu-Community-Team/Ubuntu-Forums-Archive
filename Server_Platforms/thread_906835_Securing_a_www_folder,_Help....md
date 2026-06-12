---
title: "Securing a www folder, Help..."
date: 2008-08-31
forum: Server Platforms
---

### Post by rompstar420 on 2008-08-31
So I installed awstats for my apache web server that I run.  It's great because now I understand who visits.  But I want to secure this, I don't want everyone to see my logs and stats.

so in /etc/apache2/apache2.conf I have:

<Directory "/usr/local/awstats/wwwroot">
Options FollowSymLinks
#Options None
AllowOverride None
Order allow,deny
Allow from all
</Directory>

<Directory "/usr/local/awstats/wwwroot">
AuthType Basic
AuthName "Please Log In: Staff Only..."
AuthUserFile /var/www-passwords/passwords
Require user private

Options Indexes Includes FollowSymLinks MultiViews
</Directory>

rebooted the apache2 server

then with this command I create the password file with use ray to start out with

sudo htpasswd -c /var/www-passwords/passwords ray

if it helps in my error.log it reads this ( I enter the right user/password ):

[Sun Aug 31 17:57:03 2008] [error] [client 192.168.1.1] (13)Permission denied: cannot read directory for multi: /home/raymond/www/
[Sun Aug 31 18:19:31 2008] [error] [client 127.0.0.1] access to /awstats/awstats.pl failed, reason: user 'ray' does not meet 'require'ments for user/valid-user to be allowed access
[Sun Aug 31 18:19:35 2008] [error] [client 127.0.0.1] access to /awstats/awstats.pl failed, reason: user 'ray' does not meet 'require'ments for user/valid-user to be allowed access

Help needed....

---

### Post by skunkbad on 2008-09-01
by "everyone" do you mean other server users, or people looking at your websites within the /var/www ?

---

### Post by rompstar420 on 2008-09-01
I don't want to limit by IP address, I want to limit by ID/Password to "everone" including me, so that I can still show off the stats to who ever wants to see them with the right id/pass.

So even people from the outside world, need to use an ID/password.

---

### Post by rompstar420 on 2008-09-01
anyways, i did everything I know and followed the instructions...

The windows pops up asking for ID/Password, but when I enter it, it comes back again, so that's the problem I don't understand.

---

### Post by rompstar420 on 2008-09-01
I figured out the problem...

<Directory "/usr/local/awstats/wwwroot">
AuthType Basic
AuthName "Please Log In: Staff Only..."
AuthUserFile /var/www-passwords/passwords
Require user private

# removed this line --- > Options Indexes Includes FollowSymLinks MultiViews
</Directory>


restarted apache and it worked....

---

