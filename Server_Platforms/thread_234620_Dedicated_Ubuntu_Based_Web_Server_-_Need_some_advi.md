---
title: "Dedicated Ubuntu Based Web Server - Need some advise from the experts"
date: 2006-08-11
forum: Server Platforms
---

### Post by AMD RULES on 2006-08-11
Hello Everyone!
Well I would like to be able to host my own from a web server which would be at my home. My question is, can I use Ubuntu for this and do you think I will be able to host it from home?

Does ubuntu have a webserver feature built-in?

Thanks

AMD RULES

---

### Post by chrisfay on 2006-08-11
Ubuntu ships in either 'desktop' or 'server' versions. If you choose the latter than yes, you can have a LAMP stack configured durring OS installation. 

There are tons of howto's all over the place on setting this up including one that I wrote a couple weeks ago. [http://howtoforge.com/lamp_installation_ubuntu6.06](http://howtoforge.com/lamp_installation_ubuntu6.06)

Do some good research on things like security hardening and configuration methods as opening your box up to the net invites unwanted guests. 

Places like howtoforge.com and the howto section of this forum are great places to start. Google, google and some more googleing....

---

### Post by az on 2006-08-11
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Just install the LAMP stack and you are good to go.

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server


You can install LAMP on your desktop, but you probably don't want to run a desktop on the box you connect to the net as a web server host.

From there, install a web application.  For example:
[https://help.ubuntu.com/community/Servers#head-ed0a847767fb61cd99eed5e6b641c2ccf11cdea4](https://help.ubuntu.com/community/Servers#head-ed0a847767fb61cd99eed5e6b641c2ccf11cdea4)

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)
That guide will describe how to set up a web server in you home for playing around with.

---

### Post by AMD RULES on 2006-08-11
ok. thanks alot guys. Do I need a T1 connection or will just a basic broadband connection do fine?    :confused: :)

---

### Post by chrisfay on 2006-08-11
Your ISP most likely deligates dynamic IP's so in order to host your own webserver (using a domain name) you will have to do some creative configuration. If it rarely changes, then you could setup Bind9 and serve your domain names yourself.

If you don't mind typing in an ip to browse to your web page than its as easy as installing apache, putting your site in /var/www and pointing your browser to your WAN ip address.

---

### Post by az on 2006-08-11
> **AMD RULES said:**
> ok. thanks alot guys. Do I need a T1 connection or will just a basic broadband connection do fine?    :confused: :)

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by chrisfay on 2006-08-11
If you want to go the dyndns route, [http://www.zoneedit.com](http://www.zoneedit.com) is my pick. I used them before setting up my dns and they give you full control over your zone records. 

Not sure if the others do....

You can route your registered domain to them, or create a subdomain of theirs and use that for free...

---

### Post by JamesieAB on 2006-08-12
Chris I am using your guide to setting up a lamp server for noobs and I am stuck. I hope you can help.

I am trying to install webmin and when I try to run the "sudo ./setup.sh /usr/local/webmin" command in the webmin-1.290 folder I get the following error. "sudo: ./setup.sh: Command not found".

I am pretty sure that I have followed everything up to that point, running the apt-get install for the build-essential and so on but I may have missed something.

Any suggestions as to how I can find/run the setup.sh or do I need to start again?

Thanks in advance.

---

### Post by chrisfay on 2006-08-12
try it without "sudo"

---

### Post by JamesieAB on 2006-08-12
That was quick! Thanks.

Unfortuanately that didn't work, I now get the following error message.

"bash: ./setup.sh: No such file or directory"

When I ls the webmin-1.290 folder I don't see a setup.sh folder.

---

### Post by JamesieAB on 2006-08-12
Just in case anyone else managed to snooker themselves like I did, here is what I did to get a working webmin login.

I uninstalled webmin - sudo /etc/webmin/uninstall.sh

I then downloaded (using firefox) the file webmin-1.290.tar.gz from the webmin site. I chose the option to download it to archive manager.

Once downloaded I right clicked the file in the archive manager and chose to install to the desktop and set the file option to "all files".

I then ran setup.sh (this file was somehow missing before, perhaps there was an all files option I missed somewhere).

I got all the prompts that are mentioned in the guide and selected the defaults and added my own username and password.

This time when I went to [http://myname.10000](http://myname.10000) I got the login prompt and was able to log on.

---

### Post by JamesieAB on 2006-08-12
.

---

### Post by JamesieAB on 2006-08-12
I am still having problems with webmin.

I made the changes to the apache server config as listed in the guide and had to restart the machine. When I rebooted I could no longer access webmin.

I uninstalled webmin and reinstalled it but instead of making the changes I rebooted. When I was logged back in I was still unable to access webmin.

when I uninstalled webin there was a kill (process id) stage that reported the process as not found.

Does anyone have any ideas?

---

