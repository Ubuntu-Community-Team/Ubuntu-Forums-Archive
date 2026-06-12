---
title: "VSftpd problems with  uninstall"
date: 2010-03-20
forum: Server Platforms
---

### Post by kgatan on 2010-03-20
Hi,
 
Im a bit of a beginner regarding ubuntu and have been messing around with SSL on apache and vsftpd.
 
I did some configurations on vsftpd and started receiving an error on restarts regarding stopping the server while trying new configs.
Changes to the config would neither set on restart or reboot so i decided to uninstall vsftpd and make a fresh install.
 
The problem is that after uninstall with apt-get purge/remove (also tried aptitude) i can still connect by ftp to my server over ssl. Reboot doesnt help either.
 
Is there some other ftp-server service running over ssl by default on Ubuntu?
 
Thanks
 
/Ola

---

### Post by inphektion on 2010-03-21
i wouldn't say there is a default one but not knowing your install there def could be another there.

run a netstat -an and see if you see anything still listening on port 21.
My best guess would be a pureftp

---

### Post by smc18 on 2010-03-21
Run this to see if you have anything ftp related installed and go from there.

```
dpkg --get-selections | grep ftp

```

---

### Post by kgatan on 2010-03-21
Oh forgot that, running ubuntu 9.10. I havnt installed any additional ftp server except vsftpd.
 
 
netstat -an returns:
 
[I]Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp        0      0 192.168.0.4:22          192.168.0.10:49308      ETABLERAD
tcp        0      0 192.168.0.4:139         192.168.0.14:60502      ETABLERAD
tcp        0      0 192.168.0.4:22          192.168.0.10:49357      ETABLERAD
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 ::1:631                 :::*                    LISTEN
udp        0      0 192.168.0.4:137         0.0.0.0:*
udp        0      0 0.0.0.0:137             0.0.0.0:*
udp        0      0 192.168.0.4:138         0.0.0.0:*
udp        0      0 0.0.0.0:138             0.0.0.0:*[/I]

 
192.168.0.10 is my windows machine which is connected with Putty and ftp when netstat was run.
 
 
 
dpkg --get-selections | grep ftp returned:
ftp                                             install
lftp                                            install
vsftpd                                          deinstall

 
 
Thanks for helping.
 
/Ola

---

### Post by kgatan on 2010-03-21
I have OpenSSH installed.. does that include a SFTP server?

---

### Post by inphektion on 2010-03-21
ok so there is no other ftp server.  so it comes down to a problem in your vsftpd config.
and yes ssh has sftp but that is completely different from an ftp server and uses port 22 while the ftp will be port 21 so not conflict there.

---

### Post by kgatan on 2010-03-21
Doh, i didnt know there was a ftp server up and running with SSH.
I mixed SFTP with SSL so it was the SSH server that was working all along and not the vsftpd.
 
Wish id know from the start it was that easy to set up a secure ftp instead of the hassle with ssl and vsftpd.
 
 
Thanks for all the replies and sorry for being a noob :P
 
/Ola

---

### Post by inphektion on 2010-03-21
its not too noobish to mix sftp with ftps.  I actually prefer ftps but a at least now with the latest openssh they make setting up a jail real simple for sftp users.

---

### Post by jmw86069 on 2012-02-04
I'm posting to this thread, and not the thread "vsftp Uninstall Problem" which was closed (for necromancy?)
[http://ubuntuforums.org/showthread.php?t=1410533&highlight=vsftpd+uninstall](http://ubuntuforums.org/showthread.php?t=1410533&highlight=vsftpd+uninstall)

I have a potential solution/workaround when vsftp will not uninstall, which could be related to your problem as well.  The problem as I understand it is that the vsftpd uninstall script expects to remove the user 'ftp' and group 'ftp' from the system. That step fails, causing the uninstall to fail. Thereafter, it leave the system in a state unable to remove vsftp, and until resolved no other packages can be installed. Kind of a pain.

My fix: Edit the file /var/lib/dpkg/info/vsftp.postrm and comment out the lines which remove the user 'ftp' and group 'ftp'.  Edit them as sudo, like this:

sudo nano /var/lib/dpkg/info/vsftpd.postrm

The run apt-get (or your favorite uninstaller) to remove vsftpd:

sudo apt-get remove vsftpd

---

