---
title: "apache configuration help plz"
date: 2006-07-04
forum: Server Platforms
---

### Post by mrcdan on 2006-07-04
I had my apache up and running and everything was working mt dir was /var/www. Then because i needed ftp access to the site files i went to /etc/apache2/sites enabled and i changed everything under the virtual directory to /home/dan/www. Now my apache doesnt work. I put and index.html into the directory but when i try to load the page in a browser it says it couldnt connect. How do i fix this?

---

### Post by Randomskk on 2006-07-04
The first thing to do is paste the last few lines of /var/log/apache2/error.log and see what it says there.
Most likely, you messed up the configuration somehow, and Apache will not start.

---

### Post by mrcdan on 2006-07-04
```
[Tue Jul 04 13:11:18 2006] [notice] child pid 7065 exit signal Segmentation fault (11)
[Tue Jul 04 13:11:18 2006] [notice] child pid 7068 exit signal Segmentation fault (11)
[Tue Jul 04 13:11:18 2006] [notice] child pid 7069 exit signal Segmentation fault (11)
[Tue Jul 04 13:11:18 2006] [notice] child pid 7075 exit signal Segmentation fault (11)
*** glibc detected *** free(): invalid next size (normal): 0x082fa9c0 ***
[Tue Jul 04 13:12:35 2006] [notice] child pid 7084 exit signal Aborted (6)
[Tue Jul 04 13:12:37 2006] [notice] child pid 7085 exit signal Segmentation fault (11)
[Tue Jul 04 13:12:38 2006] [notice] child pid 7086 exit signal Segmentation fault (11)
*** glibc detected *** double free or corruption (!prev): 0x082c89c0 ***
[Tue Jul 04 13:12:40 2006] [notice] child pid 7087 exit signal Aborted (6)
[Tue Jul 04 13:12:41 2006] [notice] child pid 7088 exit signal Segmentation fault (11)
[Tue Jul 04 13:34:28 2006] [error] [client 24.160.69.154] File does not exist: /var/www/favicon.ico
*** glibc detected *** double free or corruption (!prev): 0x08289a48 ***
[Tue Jul 04 13:37:04 2006] [notice] child pid 7077 exit signal Aborted (6)
[Tue Jul 04 13:37:08 2006] [notice] child pid 7102 exit signal Segmentation fault (11)
[Tue Jul 04 13:37:10 2006] [notice] child pid 7103 exit signal Segmentation fault (11)
[Tue Jul 04 13:37:14 2006] [notice] child pid 7104 exit signal Segmentation fault (11)
[Tue Jul 04 13:37:21 2006] [error] [client 24.160.69.154] File does not exist: /var/www/favicon.ico
[Tue Jul 04 13:38:58 2006] [notice] caught SIGTERM, shutting down

```

---

### Post by Randomskk on 2006-07-04
Ouch, that doesn't look fun.
Paste the default virtual host file?

---

### Post by mrcdan on 2006-07-04
NameVirtualHost 192.168.1.104
<VirtualHost 192.168.1.104>
ServerName clanlao.servegame.com               - Allows requests by domain name without the "www" prefix.
ServerAlias [www.clanlao.servegame.com](www.clanlao.servegame.com)          - CNAME (alias www) specified in Bind configuration file (/var/named/...)
ServerAdmin [email]mrcdan@gmail.com[/email]
DocumentRoot /home/dan/www/
ErrorLog /home/dan/wwwlogs/lao_errlog
TransferLog /home/dan/wwwlogs/lao_translog
<Directory /home/dan/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		#RedirectMatch ^/$ /apache2-default/
	</Directory>
</VirtualHost>

---

### Post by harisund on 2006-07-05
> [Tue Jul 04 13:34:28 2006] [error] [client 24.160.69.154] File does not exist: /var/www/favicon.ico
Why is a link like this there? That means it is still searching in /var/www. 

Could you post the file in which you made the change from /var/www to /home/.... ? I think it is the /etc/apache2/sites-available/default file?

---

### Post by Randomskk on 2006-07-05
I'm assuming the line
> ServerAlias [www.clanlao.servegame.com](www.clanlao.servegame.com) - CNAME (alias www) specified in Bind configuration file (/var/named/...) has that - CNAME... part added by you, and is not in the configuration file?

What is the exact content of the config file?

Also, if you do this:
```

sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start

```
Do you get any errors on the command line or in /home/dan/wwwlogs/lao_errlog
?

---

