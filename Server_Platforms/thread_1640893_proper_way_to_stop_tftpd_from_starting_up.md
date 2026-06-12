---
title: "proper way to stop tftpd from starting up?"
date: 2010-12-08
forum: Server Platforms
---

### Post by Skaperen on 2010-12-08
What is the proper way to stop tftpd from starting up?  There is no numbered rc script symlink for it so I can't use update-rc.d.  I don't want to just hack a file unless that is considered "the way".

---

### Post by windependence on 2010-12-08
Post the contents of your /etc/default/atftpd file.
 
-Tim

---

### Post by Skaperen on 2010-12-08
```
lorentz/root /root 146# cat /etc/default/atftpd
cat: /etc/default/atftpd: No such file or directory
lorentz/root /root 147# dpkg -l | grep tftp
ii  tftp-hpa                              5.0-14ubuntu1                                     HPA's tftp client
ii  tftpd-hpa                             5.0-14ubuntu1                                     HPA's tftp server
lorentz/root /root 148# cat /etc/default/tftpd-hpa
# /etc/default/tftpd-hpa

TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/var/lib/tftpboot"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="--secure"
lorentz/root /root 149# 
```I have the -hpa version installed, as that are the most recommended in various PXE documents.  Any reason I should go with another?

FYI, I want to stop tftpd from running only temporarily while I do tests of it at the command line with some changes.  Then I would go back to having it run as a real daemon.  I tried to kill the process, but it always comes back.  So the init system is always restarting it.  It might be a question of how to get that part of init to not restart it.

---

### Post by windependence on 2010-12-08
That's exactly it.
 
Add this line to your file:
 
```
 
USE_INETD=false

```
 
Then to start TFTP use this command:
 
sudo invoke-rc.d atftpd start
 
 
-Tim

---

### Post by Skaperen on 2010-12-10
> **windependence said:**
> That's exactly it.
 
Add this line to your file:
 
```
 
USE_INETD=false

```Then to start TFTP use this command:
 
sudo invoke-rc.d atftpd start
 
 
-Tim

It's already running standalone, not under inetd.  It's being started by the new init program.  In Ubuntu 9.10 it was started as a numbered symlink script SysV style.  I don't know where to tell init not to run it.  And it's not "atftpd".

In the mean time, I just uninstalled it from my desktop (10.10) and started it on a server running 9.10.  There it is as simple as changing "S" to "K" in symlinks in /etc/rc{1,2,3,4,5,6}.d

---

