---
title: "Setting Up a Server - Newbie"
date: 2011-03-23
forum: Server Platforms
---

### Post by Spaceport on 2011-03-23
I have never used this software at all and am running a Win XP server for a n in house web site using Joomla. My XP box started to give problems as of today. So now I need to rebuild a web server box. I have always been told that Ubuntu is the way to go. So how easy would it be for a newbie to Ubuntu to get this up and running. It is rather urgent as my server is now down :(

---

### Post by arrrghhh on 2011-03-23
> **Spaceport said:**
> I have never used this software at all and am running a Win XP server for a n in house web site using Joomla. My XP box started to give problems as of today. So now I need to rebuild a web server box. I have always been told that Ubuntu is the way to go. So how easy would it be for a newbie to Ubuntu to get this up and running. It is rather urgent as my server is now down :(

Well I don't think learning a new system out of this would be such a good idea...

I'd say if you want to learn Ubuntu, take some time to learn it... I wouldn't want you to jump into something you're not comfortable with.

With that said, Ubuntu is a fairly newbie friendly distro - however, the Server edition does not include a GUI - it's all console (text) based.  So I would recommend grabbing the Desktop edition iso and playing around with it before jumping ship!

---

### Post by drdos2006 on 2011-03-23
Have a look at Cherokee for a web server GUI.


[http://www.cherokee-project.com/](http://www.cherokee-project.com/)


regards

---

### Post by NedHanlon on 2011-03-23
When I set up my first Ubuntu Server, and my first foray into linux, I relied on lots of web resources. Not sure what you need, but here is what I follow for my config. 

Install Ubuntu
	Configure:
		Static IP: [http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)
	(Windows Networking)	SMB: [http://www.faqs.org/docs/samba/ch09.html](http://www.faqs.org/docs/samba/ch09.html)
	(Mac Networking)	NETATALK: Reference CP of old one. 
				[http://www.zaphu.com/2008/04/29/ubuntu-guide-configure-a-netatalk-file-server-based-on-apple-filing-protocol-afp/](http://www.zaphu.com/2008/04/29/ubuntu-guide-configure-a-netatalk-file-server-based-on-apple-filing-protocol-afp/)
	(FTP) 	FTP: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html)
	(WebServer) 	Apache: [http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)


This was all I needed to do. There are plenty of other guides online as well.

Took me about two hours from start to finish. 
Now, I can do it in about 30 min. 

I would also recommend nano, instead of vi or vim if you are new to command line. I would not install a gui, it takes up unnecessary system resources, and you will end up resorting to the command line for most tasks anyway.

---

### Post by falko on 2011-03-23
You can easily set up a LAMP system on Ubuntu in a few minutes: [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.10-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.10-lamp)

---

### Post by Spaceport on 2011-03-23
Thanks guys well I will be checking out all this info today to see what direction I will be taking with this. 

> **falko said:**
> You can easily set up a LAMP system on Ubuntu in a few minutes: [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.10-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.10-lamp)

falko I noticed on this page he gives a number of links to various parts of the modules to install. The ubuntu link seems to take me to the desktop edition of ubuntu. So is this correct that you set it all up on the desktop or do you still use the server edition of ubuntu

---

### Post by wojox on 2011-03-23
I would use the Desktop Edition in your case. The Server Edition is all command line.

---

### Post by Spaceport on 2011-03-23
Ok thanks, so the desktop would at the end of it doe the same for me as what the server one would do. If possible I don't want to have to go into a command line interface right off like this.

---

### Post by arrrghhh on 2011-03-24
> **Spaceport said:**
> Ok thanks, so the desktop would at the end of it doe the same for me as what the server one would do. If possible I don't want to have to go into a command line interface right off like this.

Yup, you can run all the same services in a sessionless manner (just like on the Server edition - by sessionless I mean no body has to login to the box for the apache web server to come up, etc).

So you're not missing out on anything - server edition is meant to be lean and mean, bare minimum basically (which blows my mind they put Plymouth on the Server edition...)

---

### Post by cariboo on 2011-03-24
> **arrrghhh said:**
> Yup, you can run all the same services in a sessionless manner (just like on the Server edition - by sessionless I mean no body has to login to the box for the apache web server to come up, etc).

So you're not missing out on anything - server edition is meant to be lean and mean, bare minimum basically (which blows my mind they put Plymouth on the Server edition...)

I've got the Natty server installed in vbox, to play with samba4, I don't see any sign of plymouth. Aside from an error in my bind config, the server seems to take less than 5 seconds to boot.

---

### Post by arrrghhh on 2011-03-24
> **cariboo907 said:**
> I've got the Natty server installed in vbox, to play with samba4, I don't see any sign of plymouth. Aside from an error in my bind config, the server seems to take less than 5 seconds to boot.

So they removed it?  It was definitely present in Lucid... was not there in previous versions.  I usually stick to LTS releases on my server, but that is good to hear if they did remove it!

---

