---
title: "[SOLVED] The Dream - LAN web host - help needed"
date: 2008-02-24
forum: Server Platforms
---

### Post by Kevin.S on 2008-02-24
I wanted a "LAN web host" for my web design business.

**The Dream:**
------------
1. Design a website on my windows box
2. "Upload" it to a LAN "web host"
3. Tweak it - see it run in Apache, PHP, MySQL, etc. Get it 100% ready for launch.
4. FTP it to my web host on the World Wide Web
5. As needed update the sites locally (LAN), tweak them, upload them again ;-)
------------

My entire computer life has been in a windows environment, so I'm a COMPLETE Linux noob, but I searched and searched the internet and came across Linux + Webmin + Virtualmin as a possible solution.

I found some great tutorials, so I decided to try:
ubuntu 7.10 server (LAMP install) + GUI
with Webmin (webmin_1.400_all.deb) + Virtualmin (3.522.gpl)

------------

**The Good News!**

After MUCH reading and careful work (trial and error) I have this all installed and working!

(I'm using Sendmail because I just could not get Postfix to work with it – though I don’t think this would matter at all for my use)

W00T! This site has been just AWESOWE! Thank you so much.

------------

**Now for the help I need:**

I've created a "sample" Virtual Server using Virtualmin named "local-SAMPLESITE.com" but now I have no idea how to access it from my design workstation (Windows).

I'm guessing it's a DNS issue - but honestly I'm baffled...

Tried all these:

[http://local-SAMPLESITE.com](http://local-SAMPLESITE.com) <<< nope :(
[http://192.168.1.02/](http://192.168.1.02/) <<< Apache default empty index :)
[http://192.168.1.02/SAMPLESITE.com](http://192.168.1.02/SAMPLESITE.com) <<< nope :(
[https://192.168.1.02:10000](https://192.168.1.02:10000) <<< Webmin + Virtualmin access :)
I even tried FTP (yes over my LAN) - 192.168.1.02:21 (with login and pass) <<< connection refused :(
I also tried to set the 3rd DNS in my router to 192.168.1.02 (it treats it as 192.168.1.2 - no idea why?) <<< no help

Now please understand I'm not a network engineer or hosting company and basically have no Linux skills to speak of, but I do follow instructions carefully ;-)

**What settings/configuration would I need to be able to get to (http + FTP):**
[http://local-SAMPLESITE.com](http://local-SAMPLESITE.com) through my LAN?
[http://local-SAMPLESITE2.com](http://local-SAMPLESITE2.com) through my LAN?
[http://local-SAMPLESITE3.com](http://local-SAMPLESITE3.com) through my LAN?

You get the idea... I'm lost at this point.

This noob would be eternally grateful for a clear explanation/instructions on how to accomplish "The Dream".

(NOTE: this is also posted on the Virtualmin forum)

---

### Post by k_grdn on 2008-02-24
Hi,

On your XP box:

Edit c:\windows\system32\drivers\etc\hosts and add a staic entry: 

192.168.1.2 local-SAMPLESITE.com 

This will enable you to access your site with a hostname.

I think this is an apache config problem.

Post the contents of /etc/apache2/sites-available/local-SAMPLESITE.

Good luck with the linux move!

Regards,

k_grdn

---

### Post by Kevin.S on 2008-02-24
> **k_grdn said:**
> Hi,

On your XP box:

Edit c:\windows\system32\drivers\etc\hosts and add a staic entry: 

192.168.1.2 local-SAMPLESITE.com 

This will enable you to access your site with a hostname.

I think this is an apache config problem.

Post the contents of /etc/apache2/sites-available/local-SAMPLESITE.

Good luck with the linux move!

Regards,

k_grdn

contents of /etc/apache2/sites-available/local-SAMPLESITE.com.conf
```
<VirtualHost 192.168.1.2:80>
SuexecUserGroup "#1003" "#1003"
ServerName local-samplesite.com
ServerAlias www.local-samplesite.com
DocumentRoot /home/local-samplesite/public_html
ErrorLog /home/local-samplesite/logs/error_log
CustomLog /home/local-samplesite/logs/access_log combined
ScriptAlias /cgi-bin/ /home/local-samplesite/cgi-bin/
DirectoryIndex index.html index.htm index.php index.php4 index.php5
<Directory /home/local-samplesite/public_html>
Options Indexes IncludesNOEXEC FollowSymLinks
allow from all
AllowOverride All
</Directory>
<Directory /home/local-samplesite/cgi-bin>
allow from all
</Directory>
</VirtualHost>
```

Thanks for looking into this for me k_grdn!

---

### Post by k_grdn on 2008-02-24
Hi,

Change:

<VirtualHost 192.168.1.2:80>

to:

<VirtualHost *>

And restart apache

/etc/init.d/apache2 restart

Regards,

k_grdn

---

### Post by Kevin.S on 2008-02-24
Problem solved!

[COLOR="Blue"]To browse (ie and Firefox):[/COLOR]

[http://local-samplesite.com](http://local-samplesite.com) 

**brings me to my shinny new LAN web server!**

[COLOR="Blue"]To use my FTP client:[/COLOR]

server address: local-samplesite.com
login: local-samplesite
pass: mypass

**Full site control on my sweet ubuntu 7.10 LAN web server!**


W00T! :guitar:

BIG THANKS k_grdn !!!

---

