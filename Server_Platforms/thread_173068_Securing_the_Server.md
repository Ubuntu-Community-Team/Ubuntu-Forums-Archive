---
title: "Securing the Server"
date: 2006-05-09
forum: Server Platforms
---

### Post by amitroy5 on 2006-05-09
I have a server with Apache2, mySQL 4.1, and PHP 4.4.0 installed. I do have a Gnome GUI, which makes ubuntu easier to use. Does anyone have any tips for securing the server a bit? I does not have to be hard core. Thanks! :)

---

### Post by chekov on 2006-05-09
Hi there,

I would first prove certain services, protocols, and ports. The ones which are not in use or necessary should be closed. It does not make the system directly more secure but it lowers the risk of becoming attacked by someone.

I think Ubuntu standard installation as a server mode is quite secure by itself, meaning that there's no compile tools included, etc.

Years ago when telnet was still de facto way to make a connection with some  certain server with terminal, it was soon replaced by ssh.

If you have telnet port running on your server, it would be good to close that, especially if you do not need incoming telnet connections to your linux box.

ftp should be closed as well and replaced with sftp.

If you are not running mail server (like postfix or sendmail) on your linux box, you can also disable such service and point (if needed) some other ubuntu services / programs to use some external smtp port for sending log / error messages to you, rather than using the local mail delivery system.


Cheers!

---

### Post by LordHunter317 on 2006-05-09
The standard Ubuntu installation doesn't have any listening services.  Provided you didn't install anyhting you don't want to listen to the world, you are OK.

Leaving X not running except when you need to use it is the next best thing to do.

---

### Post by Socratez on 2006-05-13
Could yo also install apache2 using chroot to enhance security? I am not fimiliar with chroot but I have been doing my first server setup in years and when I did my mail server up I chroot and from what I usnderstood this was a good practice to enhance security ... I could be wrong ... it is not uncommon

Soc

---

### Post by Tortanick on 2006-05-13
Making notes here but one thing I don't get, how to not leave X running? some special startup command?

---

### Post by Socratez on 2006-05-13
You need to edit the /etc/inittab file ... there is a section that shows the default run level ... change it from 5 to 3 and you will have console only login ... no graphical interface ....

Soc

---

### Post by rhipwell on 2006-05-23
If you edit your /etc/inittab file to boot to runlevel 3 ( im doing this off the top of my head, I'm at work ) you will always boot to console. After you log into console you will be able to initiate a X session with the command startx. 

By only using X ( gnome, kde etc ) when you need it, you avoid running any extra programs, services etc that you do not need, and thus do not open a potential security hole. 

Hope this helps! 


-Rob

---

### Post by MJN on 2006-05-25
I thought (K)Ubuntu (by virtue of the Debian base) was configured such that run levels 2-5 were essentially the same (by default at least) in-so-far that the same services are started/stopped in each? Thus, in this case x would be started in levels 2-5.

Mathew

---

