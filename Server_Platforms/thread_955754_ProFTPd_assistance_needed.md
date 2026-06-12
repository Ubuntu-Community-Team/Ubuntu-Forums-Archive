---
title: "ProFTPd assistance needed"
date: 2008-10-22
forum: Server Platforms
---

### Post by edpatterson on 2008-10-22
Attempting to get ProFTPd running...

I installed proftpd using sudo apt-get install proftpd and selected inetd as the server type. I then tried to ftp into the server from a windows box and received a ftp: connect :Unknown error number. Next I tried 'ftp localhost' as root on the server and received connection refused. Much reading later I tried '/etc/init.d/inetd restart'. I received The program inetd is currently not installed. You can install ...'

I am trying to set it up so I can use my favorite text editor on a Windows box for configuration files and html/php pages.

SSH is installed on the server and I can use Winscp and putty to communicate with it, I just can not get the ftp portion to work.

X is not loaded on the server.

Ed

---

### Post by mschutte on 2008-10-22
Just to clarify, the installation of proftpd was done from the console of the server and you chose the 'start from xinetd' option?

---

### Post by edpatterson on 2008-10-22
That is correct.

---

### Post by mschutte on 2008-10-22
I installed proftpd on my server. Getting the same error though. Just give me a few minutes, will have it sorted out quickly.

---

### Post by mschutte on 2008-10-22
Problem solved on my side, silly me. If you choose the install with the xinetd option you also have to check that the xinetd deamon is installed. You can verify that the deamon is installed by using the following command:
***sudo apt-cache search xinetd***

If you get a response it means xinetd is installed. If not you will have to install it using ***sudo apt-get install xinetd***

Once that is done you can try to ftp again. Let me know if it worked.

---

### Post by lykwydchykyn on 2008-10-22
You can also reconfigure proftpd to run as a daemon.  Just do:
```

sudo dpkg-reconfigure proftpd

```

Neither inetd nor xinetd are installed by default.

---

### Post by mschutte on 2008-10-22
Yes lykwydchykyn is right, thanks I forgot about that one....

---

### Post by edpatterson on 2008-10-22
> **lykwydchykyn said:**
> You can also reconfigure proftpd to run as a daemon.  Just do:
```

sudo dpkg-reconfigure proftpd

```

Neither inetd nor xinetd are installed by default.

Never being one to show my stupidity, I am under the impressions that if I want it to load automatically at system boot I should configure it for inetd. If I reconfigure it for stand alone will I have to fire it off manually each reboot.

Famous last words, this box will only be used for Squid and maintaining a related MySQL database. 

I use Boxer Text Editor for css and html, it will ftp the edited pages to the server for me and set the correct file rights. It will not have any 'users' per say...

Ed

---

### Post by mschutte on 2008-10-22
The xinetd deamon only fires up proftpd once a ftp request is made to the server. If the ftp session is terminated xinetd shuts down proftpd. Hence you have to ensure that xinetd is started at boot if you want to run proftpd in that mode. Alternatively configure it as lykwydchykyn suggested.

---

### Post by lykwydchykyn on 2008-10-22
> **edpatterson said:**
> Never being one to show my stupidity, I am under the impressions that if I want it to load automatically at system boot I should configure it for inetd. If I reconfigure it for stand alone will I have to fire it off manually each reboot.
.

Ed

Nope, you're confused.  Inetd (and its variants) is a service that launches services on demand.  So basically proftpd is not running until you ask for it.  This causes you some latency when you connect, but it saves you cpu cycles while you aren't using FTP.  Daemon mode means it runs all the time, like a normal service.

Unless you're setting this up on an ancient (read: pre-pentium 2) piece of hardware, proftpd isn't likely to cause much overhead.  I just use daemon mode, typically.

---

### Post by edpatterson on 2008-10-22
> **lykwydchykyn said:**
> Nope, you're confused.  Inetd (and its variants) is a service that launches services on demand.  So basically proftpd is not running until you ask for it.  This causes you some latency when you connect, but it saves you cpu cycles while you aren't using FTP.  Daemon mode means it runs all the time, like a normal service.

Unless you're setting this up on an ancient (read: pre-pentium 2) piece of hardware, proftpd isn't likely to cause much overhead.  I just use daemon mode, typically.

Thanks, I reconfigured and it is working as expected.

Ed

---

### Post by rockrhino27 on 2009-01-03
WOW.  I just ran into the same problem.  I automatically assumed that I had xinetd installed...  

This worked.  Thanks.

---

