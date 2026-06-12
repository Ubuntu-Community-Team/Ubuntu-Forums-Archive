---
title: "Can't start nfs, sshd, tftpd daemons"
date: 2006-08-21
forum: Server Platforms
---

### Post by bigsanta on 2006-08-21
Hi 

I am having some trouble getting the nfs-kernel-server, ssh, tftpd-hpa to start at boot

I have run update-rc.d "daemon" defaults several times on all three servers but when i restart it does'nt work, i have to manualy start the daemons with 

/etc/init.d/daemon start 

and then they run without problems 

Just discovered that my ltspswapd was causing this problem. Did an mv on the daemon start file from S20ltspswapd to S30ltspswapd so it will start after my other daemons.

Cheers 
Jesper

---

### Post by Jose Catre-Vandis on 2006-09-02
Check here for tftpd
[http://www.ubuntuforums.org/showthread.php?t=148027&highlight=tftpd+start](http://www.ubuntuforums.org/showthread.php?t=148027&highlight=tftpd+start)

---

