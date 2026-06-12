---
title: "Turn off FTP server"
date: 2009-02-23
forum: Server Platforms
---

### Post by mistypotato on 2009-02-23
I installed 8.10 server and ubuntu-desktop.

an FTP server is installed by default.

How can I find out what ftp server it is and how can I turn it off ?

---

### Post by pdtpatrick on 2009-02-23
8.10 installs an FTP server by default? I don't recall that. 

anyway check /etc/init.d/ and see which one is listed in there: vsftpd or proFTPd .. then check and see if the service is running: > sudo /etc/init.d/<service name> status

---

### Post by mistypotato on 2009-02-24
thanks patrick.  It was vsftpd

---

### Post by vsiege on 2009-03-27
if  i get
>  * Usage: /etc/init.d/vsftpd {start|stop|restart|reload}
does that mean it is stopped???

---

### Post by kevmitch on 2009-03-27
vsiege: No that's the usage message telling it you gave an invalid command. To stop it run
```
/etc/init.d/vsftp stop
```
That particular initscript probably doesn't have a "status" option. To check if its running do a 
```
ps aux | grep ftp
```

---

### Post by vsiege on 2009-03-27
I adjusted what you wrote so that vsftp had a d at the end
```
sudo /etc/init.d/vsftpd stop
```
got this:
```
 * Stopping FTP server: vsftpd 
```
then i typed like you said:
> sudo ps aux | grep ftp
and got this:
```
userNameHere       9636  0.0  0.0   7452   872 pts/0    R+   22:07   0:00 grep ftp
```
What does that mean?? thanks

---

### Post by kevmitch on 2009-03-28
Touche, you'd need to sudo the daemon stopping command. You don't however need to sudo the "ps aux" command since it's just requesting non-secured information. In general you'll find that the Unix philosophy is to allow a regular use to LOOK at as much as possible, though only allow root to actually change it. 

LOL on the result of 

```
ps aux | grep ftp
```

I forgot to mention that the result would be a  little brain bending. That command returns all processes that were started by commands containing the string "ftp". 

Remember that the "grep ftp" command itself is a process so it had better return itself! If that's all you see, then you're in the clear there's no FTP daemon running. If you'd be more at ease seeing nothing returned from that command you can instead use

```
ps aux | grep [f]tp
```

---

### Post by Mister.Vash on 2009-03-28
Are you trying to permanently disable it or just be able to start and stop it as needed?  Issuing the stop command will stop it until you either manually restart it or reboot your system.

---

### Post by kevmitch on 2009-03-28
> **Mister.Vash said:**
> Are you trying to permanently disable it or just be able to start and stop it as needed?  Issuing the stop command will stop it until you either manually restart it or reboot your system.

Aye, tis true. If you want to prevent the deamon from starting:
```
sudo update-rc.d -f rsync remove
```
(or use a GUI like BUM)

And if you don't see yourself needing an ftp server at all in the near future
```
sudo aptitude purge vsftpd
```
(the purge will also remove any ftp configuration files)

---

### Post by vsiege on 2009-03-28
thanks kevmitch

---

