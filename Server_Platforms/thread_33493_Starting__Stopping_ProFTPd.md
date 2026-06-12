---
title: "Starting / Stopping ProFTPd"
date: 2005-05-11
forum: Server Platforms
---

### Post by SychoSly on 2005-05-11
Hi Guys. I installed ProFTPd and it is running. I haven't configured it yet, but I want to know how to stop/start the server. I try going to: 

etc/init.d/proftpd stop 

Then I get the message that ProFTPd is started from "inetd/xinetd" . 

What it inetd/xinetd? I search for it and I find nothing. 

There is a usr/sbin/inetd and when write "usr/sbin/inetd start" nothing happens. 

Please help.

---

### Post by defkewl on 2005-05-11
$ apt-get inetd

or
$ apt-get xinetd

then start it:
$ /etc/init.d/inetd

Good luck :)

---

### Post by LordHunter317 on 2005-05-11
Inetd is already installed, you shouldn't ever have to install it.

If it's running from inetd, it'll be started when someone connects and stopped when someone disconnects automatically.

---

### Post by SychoSly on 2005-05-14
[QUOTE=LordHunter317]Inetd is already installed, you shouldn't ever have to install it.

If it's running from inetd, it'll be started when someone connects and stopped when someone disconnects automatically.[/QUOTE]
 I understand now. How do I make it so that I can start/stop the server whenever I want, instead of having it run the whole time. 

When I tried to stop it using the shell, it said "change to servertype to standalone" so I went into the proftpd.conf file and changed it. Now when I try to login it says "Connection closed by remote host".

I do not know how to start it.  I tried:

/usr/sbin/proftpd start

/etc/init.d/proftp start

both of those do nothing. 

Someone please help.

---

### Post by Gandalf on 2005-05-14
[QUOTE=SychoSly]I understand now. How do I make it so that I can start/stop the server whenever I want, instead of having it run the whole time. 

When I tried to stop it using the shell, it said "change to servertype to standalone" so I went into the proftpd.conf file and changed it. Now when I try to login it says "Connection closed by remote host".

I do not know how to start it.  I tried:

/usr/sbin/proftpd start

/etc/init.d/proftp start

both of those do nothing. 

Someone please help.[/QUOTE]
 try
dpkg-reconfigure proftpd
and choose standalone

---

### Post by LordHunter317 on 2005-05-14
[QUOTE=SychoSly]I understand now. How do I make it so that I can start/stop the server whenever I want, instead of having it run the whole time. [/quote]Here's the procedure:
[list=1]
[*]Edit /etc/inetd.conf or /etc/xinetd.d/proftp to disable the ftp service   
[*]Edit proftpd.conf to be in standalone mode   
[*]Restart inetd:```
/etc/init.d/inetd restart
```(Change to xinetd if necessary).   
[*]Start proftpd:```
/etc/init.d/proftpd start
``` 
[/list] That should be it if my memory serves me correctly.
 
>  Now when I try to login it says "Connection closed by remote host".Post your configuration files then, something still isn't right.

> I do not know how to start it.  I tried:

/usr/sbin/proftpd start

/etc/init.d/proftp start

both of those do nothing. You use the latter, not the former.  
**Always use the scripts in /etc/init.d/ to start/stop system daemons**, unless you know exactly what you're doing.  And if you have to ask, you don't know what you're doing, so **Always use the scripts in /etc/init.d to start/stop system daemons**.

---

### Post by SychoSly on 2005-05-15
[QUOTE=Gandalf]try
dpkg-reconfigure proftpd
and choose standalone[/QUOTE]


This worked. Thank You.

---

### Post by SychoSly on 2005-05-15
[QUOTE=LordHunter317]Here's the procedure:
[list=1]
[*]Edit /etc/inetd.conf or /etc/xinetd.d/proftp to disable the ftp service   
[*]Edit proftpd.conf to be in standalone mode   
[*]Restart inetd:```
/etc/init.d/inetd restart
```(Change to xinetd if necessary).   
[*]Start proftpd:```
/etc/init.d/proftpd start
``` 
[/list] That should be it if my memory serves me correctly.
 
Post your configuration files then, something still isn't right.

You use the latter, not the former.  
**Always use the scripts in /etc/init.d/ to start/stop system daemons**, unless you know exactly what you're doing.  And if you have to ask, you don't know what you're doing, so **Always use the scripts in /etc/init.d to start/stop system daemons**.[/QUOTE]

Thanks.

---

