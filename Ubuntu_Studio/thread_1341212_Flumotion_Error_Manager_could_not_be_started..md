---
title: "Flumotion Error: Manager could not be started."
date: 2009-11-29
forum: Ubuntu Studio
---

### Post by Khul123 on 2009-11-29
Hi,

-Im trying to use[COLOR=RoyalBlue]** [Flumotion]("http://www.flumotion.net") **[/COLOR], the thing is after a succesfull instalation,** i get an error when "trying to start a new manager and connect to it"**. And i cant even use the app for the first time.
-Im using Ubuntu 8.04 LTS in 32 bit in an Intel Core 2 Duo box, 2 gb RAM and plenty space in hard drive.

[COLOR=Red]This is what i did:[/COLOR]

-Added flumotion to repo list.
-Installed using terminal
-Got the error:
Error: Manager could not be started.

THe command that failed was: /usr/sbin/flumotion -C /tmp/tmpn-5uMW.flumotion/etc -L /tmp/tmpn-5uMW.flumotion/var/log -R /tmp/tmpn-5uMW.flumotion/var/run start manager admin The command exited with an exit code of 1 

-removed and purged flumotion.
[COLOR=Red]-Reinstalled.
[/COLOR][B]
Fix (i self reply):[/B]
[COLOR=Red]
-Apllied the following:[/COLOR] 
[[COLOR=RoyalBlue](as recomended in Ticket 1020 from FLumotion support)[/COLOR]]("https://code.fluendo.com/flumotion/trac/ticket/1020")
sudo openssl genrsa -out key.pem 1024 sudo 
sudo openssl req -batch -new -key key.pem -out server.pem sudo 
sudo openssl x509 -req -days 365 -in server.pem -signkey key.pem -out certificate.pem

[[COLOR=RoyalBlue](as recomended in another post in Ubuntu forum)[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1153164")

chmod 777 on certificate.pem,  same for  server.pem and key.pem. 
sudo chmod a+x /etc/flumotion

sudo adduser <username> flumotion
[B]
Note that Flumotion asks you to input some information when you are installing it. Right after it finished asking about the location of the place you live in, you should enter the name "certificate" (since we will create a file named certificate.pem) and in the fnal step the name should be "server" (since we willl create a file named "server.pem").

Important: this is not a how to or a guide to properly fix this issue, just the way i got it to work. Feel free to check the functionality with lower permissions since the use of 777 permissions is not recommended.
[/B] 
-------------------------------------------------------------------------------------
Addition info (for future reference and further explanation for whoever can give me a hand in solving this):

Ticket 1020 in Fluendo support site where the issue seems to be fixed.
[https://code.fluendo.com/flumotion/trac/ticket/1020](https://code.fluendo.com/flumotion/trac/ticket/1020)

Link to previous subject on Ubuntu forum: [http://ubuntuforums.org/showthread.php?t=1153164](http://ubuntuforums.org/showthread.php?t=1153164)

---

### Post by guillemsola on 2009-12-01
Hi, I'm a flumotion user aswell and AFAIK the version in ubuntu repos is quite older, if you're using hardy you can add the following line to /etc/apt/sources.list:

deb [http://www.flumotion.net/pkg/ubuntu](http://www.flumotion.net/pkg/ubuntu) hardy main

enjoy

---

### Post by joeld100 on 2010-01-12
Hey Khul, I saw your bug report on flumotion.net and then found this post. It looks like the same issue I am having.  I've tried Fedora core 12 and 11, and now Ubuntu hardy and still haven't gotten flumotion to work correctly out of the box.

I'll re-install tonight and focus on getting the ssl certificate workaround and permissions set up like you mention in your post.  I'm just making a proof of concept testbed, not a production server, so I just need it to work.

Do you have any further comments that might be useful on setting up flumotion in ubuntu (or other distros)?

Thanks,
Joel

---

### Post by Chanyc on 2010-04-01
I had come with the same prolblem
If you have any further comments that might be useful on setting up **[COLOR=#ff0000]flumotion[/COLOR]** in ubuntu,pleased tell me,thanks.

---

