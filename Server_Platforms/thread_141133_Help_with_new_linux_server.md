---
title: "Help with new linux server"
date: 2006-03-07
forum: Server Platforms
---

### Post by MisterCMK on 2006-03-07
I am going to be setting up a new network for a business soon.  We have around 10 computers in the office running WindowsXP due to needing to use AutoCAD and other windows only programs.  We also have around 10 laptops out in the field, but I am not worried about those yet.  We also have a T1 connection and 8 static public IPs.  Here is what I want to be able to do, and I will need some help.  I am a Windows Warrior, but I do not know much about linux.  I would love to use Ubuntu because Windows licenses are quite expensive.  I am starting to learn my way around linux, but I am in no way proficient yet.  Here is what I want to do:

1. FTP, HTTP, and E-Mail hosting in house.  
2. Central file sharing
3. I want the Windows machines to authenticate to the linux box
4. I want users to have a home directory that maps to whatever machine they log into.  I want their e-mail settings, favorites, and desktop settings to follow them to whatever machine they log into as well.
5. I would like to eventually setup a VPN so that our users can login from home.
6. I want users to have one login/password for the network.  I want them to be able to log into the FTP server, their email and their computer with a username that follows this format: firstname.lastname.
7. We have a domain name that we have registered already, and I want it to point to our static IP address for the internet services.  
8. I also want to be able to backup the configuration of the server incase of an emercency and make it easy to get up and running again.  


I will probably run a separate server for the http, ftp and e-mail, however I don't want to have to update various user databases.  I want to be able to add or remove users from the server and not have to do anything else.  

I would really appreciate any help you guys can give me.  If anyone is willing to walk me through this over the phone of IM that would be awesome as well.  Thanks.

---

### Post by Garyu on 2006-03-07
Samba configuration to share files with windows computers, might also give you some other hints:
[https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba)

FTP daemon vsftpd is an easy way to solve FTP:
[http://www.ubuntuforums.org/showthread.php?t=91887](http://www.ubuntuforums.org/showthread.php?t=91887)
Or I found this thread also about something called proftp, but I haven't tried that myself:
[http://www.ubuntuforums.org/showthread.php?t=79588](http://www.ubuntuforums.org/showthread.php?t=79588)

As for HTTP server, I guess the best choice is Apache2 as this is what many commercial servers are using.

I found a mail server howto you can look at here (also includes MySQL and lots of other stuff connected to running a mail server):
[http://www.charlesabrown.com/ubuntu/shareme.html](http://www.charlesabrown.com/ubuntu/shareme.html)

Well, I hope this solves some of your questions. I haven't tried setting up a server like this myself, but it would be nice to hear about your experiences as the need to do a setup like this may arise someday, if not for me maybe for someone else here on the forum. And hey, why not make a wiki page about it while your at it? :cool:

---

### Post by dk_pa on 2006-03-08
Here is a link for a mail server setup (a very complete one).  Never have done it myself but you can see what you're getting into.

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

### Post by nihilocrat on 2006-03-09
For the 'Windows users authenticating to Linux' I believe using OpenLDAP (slapd) would work, though I've never done it myself.

[http://www.openldap.org/doc/admin23/quickstart.html](http://www.openldap.org/doc/admin23/quickstart.html)

---

### Post by ttallos on 2006-03-10
Try this post I have laid out the files you must edit to get the vpn to work.
[http://ubuntuforums.org/showthread.php?t=122962](http://ubuntuforums.org/showthread.php?t=122962)

---

