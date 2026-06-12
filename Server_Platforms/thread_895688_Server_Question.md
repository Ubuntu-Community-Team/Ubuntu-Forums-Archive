---
title: "Server Question"
date: 2008-08-20
forum: Server Platforms
---

### Post by Homelinux on 2008-08-20
I am wanting to host a small website at home, now since i am a verrry new ubuntu user i am wondering what is a good server to use for a new to linux user? and can i put server software and my site on my little micro atx pc and plug it into my regular pc and then run my site and server?  I took a look at the ubuntu server editoin and after install i just could not understand what to do with it. The was no GUI so i could not see how to set up a site. And last if i run the ubuntu server 7.10 can it run with ubuntu hardy heron 8.04? 

Sorry for all the questions if there is a tut that would be great to.

---

### Post by Titan8990 on 2008-08-20
There is no GUI by default on Linux server because it is 

a) not needed
b) usually administered remotely

You could install a GUI on it but it will not help because all the configuration will still be done via the CLI.

If you are say, trying to set up an apache web server then you should search google or the how to guides and tutorials section of the forums for:

set up apache web server

If doing a google search always throw the word "ubuntu" in there. Guides and tutorials for Linux I find to be much more helpful the a GUI infested Windows server environment.

If you are looking for a file server then look for tutorials on SAMBA.

I will tell you that diving right into Linux and trying to administer will not be an easy task. Many people who are already Linux desktop users would struggle with this.

---

### Post by louieb on 2008-08-20
I host [Lou's Home Server Stuff]("http://louieb.isa-geek.net/") on my desktop running Ubuntu. I don't mind the overhead of a server running on my desktop. Its just a do it because I can type of thing.  

To get a lamp server up and running. 
[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP") 

To add a lightweight desktop.
[HOWTO: Leightweight Gnome - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=298818&highlight=xorg+gdm+gnome-core") 

And finally administer your server from your desktop.
[SSH - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSHHowto?highlight=%28ssh%29") 
[Webmin]("http://www.webmin.com/") 
[Webmin on Dapper Server - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=195093") 


> and can i put server software and my site on my little micro atx pc and plug it into my regular pc and then run my site and server?

Easiest thing to do is share internet with a router. And port forward port 80 to your web server. And use a service like dyndns.org.  

Nothing particularly hard just a lot of pieces that have to fit together.  It takes a while. lol Titan8990 called it a struggle. It certainly is a challenge.

Good Luck.

---

### Post by Titan8990 on 2008-08-20
I called it a "struggle" mostly due to my own experience with it. I had been a Linux desktop user for about 6months and was comfortable with the command line. 

What really made it a struggle for me was jumping right into a Exim4 email server when I should have started out with something like a LAMP server.

---

### Post by bodhi.zazen on 2008-08-20
> **Homelinux said:**
> I am wanting to host a small website at home, now since i am a verrry new ubuntu user i am wondering what is a good server to use for a new to linux user? and can i put server software and my site on my little micro atx pc and plug it into my regular pc and then run my site and server?  I took a look at the ubuntu server editoin and after install i just could not understand what to do with it. The was no GUI so i could not see how to set up a site. And last if i run the ubuntu server 7.10 can it run with ubuntu hardy heron 8.04? 

Sorry for all the questions if there is a tut that would be great to.

You can run server software (apache) on a desktop installation. This may help you to learn. If you want a dedicated server, go with the server install and learn to ssh into the server of web config tools such as webmin.

---

### Post by moonpup on 2008-08-20
The Ubuntu server guide may help you...

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by Iowan on 2008-08-20
[Here]("http://www.spoffle.com/technical/how-to-set-up-lamp-on-ubuntu-desktop-edition/") is a How-To for LAMP on a desktop.

---

