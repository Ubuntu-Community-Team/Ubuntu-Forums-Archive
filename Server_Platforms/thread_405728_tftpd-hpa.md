---
title: "tftpd-hpa"
date: 2007-04-10
forum: Server Platforms
---

### Post by flanderp on 2007-04-10
Hi, 

I have installed tftpd-hpa , all working fine, can anyone tell me if/how you can tftp a file (cisco running-config) to a tftpd-hpa server without having to touch an empty file on the tftpd server first.

Thanks 
Paul

---

### Post by sgenchev on 2007-04-11
Use -c option (man tftpd). In default mode (runs from inetd) change /etc/inetd.conf and change 
tftp           dgram   udp     wait    root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot 
  to
tftp           dgram   udp     wait    root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -c -s /var/lib/tftpboot

If you run tftpd as a daemon, edit /etc/default/tftpd-hpa and change the OPTIONS variable to look something like
OPTIONS="-c -l -s /var/lib/tftpboot"

---

### Post by flanderp on 2007-04-11
Brill , thanks for the reply , I should have checked the man page.

Paul

---

### Post by geezerone on 2007-07-02
I am trying to copy  to Ubuntu but anyone know how to go about this a tad confusing and getting timeouts from other device but can ping Ubuntu ok?

I run **tftpd** in terminal but should I be assigning switches or just modify my inetd.conf file?

My inetd.conf is:

```
tftp		dgram	udp	wait 	root /usr/sbin/tcpd /usr/sbin/in.tftpd -c -s /var/lib/tftpboot
--tftpd-timeout 300 --retry-timeout 5     --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5  /tftpboot
```

Thanks

---

### Post by davidgarcin on 2007-11-21
You might try this how-to, it worked for everyone but me:

[http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)

hope that helps.
-Dave

---

