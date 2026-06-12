---
title: "Problem getting FTP work"
date: 2006-01-03
forum: Server Platforms
---

### Post by kd35a on 2006-01-03
Hello

I'm new too linux=used too windows. But after several no-reason OS-craches i want too start use linux full-time. I have tried Ubuntu (5.04) some months ago, also tried Slackware and FedoraCore, but liked Ubuntu more.

Now a want too set up a smal-scale server, i made a normal installation of Ubuntu (5.10), not the server-install because i want too be able too use the OS normal in the same time its runnig as server.

For http i use Apache, wich works realy great. But i also want an ftp-server for upploading my files too the Apache-server and some other stuff maybee. I have tried two different ftp-servers, wu-ftpd and Pro-ftpd. But i can't make it work. First i just installed them (not att the same time ofcourse :p) but non of them worked with the default configuration. Soo i started looking in the *.conf-files, and made some changes soo that it looked like i wanted it. But still it didn't work. I tried too contact the server wia "ftp://localhost" from the server, and from an other computer, but with the correct ip ofcourse, but nothing worked.

Now i wonder, is there a good guide for installing an ftp-server, i have found some but non of them worked. Or if someone shoude want too explain how it works here in the forum. But be ware of, i'm used too next>next>next>everything works (great untill a OS-crach :p). I hope someone helps me because i'm realy getting sick of windows.

/KD35A

---

### Post by shroom on 2006-01-04
Tjenare kd35a. ;)     Welcome to UbuntuForums!

This is going to be my first reply with help since I joined the forum. I'm also kinda new to Linux but I have suceeded to configure both HTTP and FTP service propertly. I've been a Windows-user all my life but since a month ago I changed to Ubuntu and I don't regret it! We're all new, aren't we? ;)


To start off, I'm using Pro-FTPd as FTP-service and it works great. To install it, type this in the terminal; **apt-get update    |    apt-get install proftpd**

When that's done, make sure the service is started by typing this in the terminal and look for proftpd; **ps aux**

If the service isn't started, type this in the terminal; **sudo /etc/init.d/proftpd start** (you can also replace start with stop/restart)


I hope this helped you a bit!

---

### Post by kd35a on 2006-01-04
Tack!!

Now it seems too work, just some config and i hope i'm up and running!

/KD35A

---

### Post by shroom on 2006-01-04
No problem. Just ask if you have more questions in mind!

---

