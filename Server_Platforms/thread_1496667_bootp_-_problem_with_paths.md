---
title: "bootp - problem with paths"
date: 2010-05-29
forum: Server Platforms
---

### Post by GL1zdA on 2010-05-29
I'm trying to boot an SGI using a Ubuntu box for bootp. There is however one small problem. The files that are needed for booting are:
/IRIX/boot/sa
/IRIX/boot/miniroot/UNIX.*

The entry in bootptab has hd=/IRIX/boot

This is what was logged:

```
May 29 21:03:34 ubuntu bootpd[29051]: recvd pkt from IP addr 192.168.1.4
May 29 21:03:34 ubuntu bootpd[29051]: bootptab mtime: Fri May 28 17:38:30 2010
May 29 21:03:34 ubuntu bootpd[29051]: request from IP addr 192.168.1.4
May 29 21:03:34 ubuntu bootpd[29051]: found 192.168.1.4 (indy)
May 29 21:03:34 ubuntu bootpd[29051]: requested path="/IRIX/boot"  file="sa"
May 29 21:03:34 ubuntu bootpd[29051]: bootfile="/IRIX/boot/sa"
May 29 21:03:34 ubuntu bootpd[29051]: vendor magic field is 0.0.0.0
May 29 21:03:34 ubuntu bootpd[29051]: sending reply (with no options)
May 29 21:03:34 ubuntu in.tftpd[29548]: connect from 192.168.1.4 (192.168.1.4)
May 29 21:03:34 ubuntu tftpd[29549]: tftpd: trying to get file: /IRIX/boot/sa 
May 29 21:04:20 ubuntu bootpd[29051]: recvd pkt from IP addr 192.168.1.4
May 29 21:04:20 ubuntu bootpd[29051]: bootptab mtime: Fri May 28 17:38:30 2010
May 29 21:04:20 ubuntu bootpd[29051]: request from IP addr 192.168.1.4
May 29 21:04:20 ubuntu bootpd[29051]: found 192.168.1.4 (indy)
May 29 21:04:20 ubuntu bootpd[29051]: requested path="/IRIX/boot"  file="sa"
May 29 21:04:20 ubuntu bootpd[29051]: bootfile="/IRIX/boot/sa"
May 29 21:04:20 ubuntu bootpd[29051]: vendor magic field is 0.0.0.0
May 29 21:04:20 ubuntu bootpd[29051]: sending reply (with no options)
May 29 21:04:20 ubuntu in.tftpd[29550]: connect from 192.168.1.4 (192.168.1.4)
May 29 21:04:20 ubuntu tftpd[29551]: tftpd: trying to get file: /IRIX/boot/sa 
May 29 21:05:36 ubuntu bootpd[29051]: recvd pkt from IP addr 192.168.1.4
May 29 21:05:36 ubuntu bootpd[29051]: bootptab mtime: Fri May 28 17:38:30 2010
May 29 21:05:36 ubuntu bootpd[29051]: request from IP addr 192.168.1.4
May 29 21:05:36 ubuntu bootpd[29051]: found 192.168.1.4 (indy)
May 29 21:05:36 ubuntu bootpd[29051]: requested path="/IRIX/boot/miniroot"  file="unix.IP22"
May 29 21:05:36 ubuntu bootpd[29051]: bootfile="/IRIX/boot/unix.IP22"
May 29 21:05:36 ubuntu bootpd[29051]: vendor magic field is 0.0.0.0
May 29 21:05:36 ubuntu bootpd[29051]: sending reply (with no options)
May 29 21:05:36 ubuntu in.tftpd[29552]: connect from 192.168.1.4 (192.168.1.4)
May 29 21:05:36 ubuntu tftpd[29553]: tftpd: trying to get file: /IRIX/boot/unix.IP22 

```

I don't understand this:
requested path="/IRIX/boot/miniroot"  file="unix.IP22"
bootfile="/IRIX/boot/unix.IP22"
Why is bootp ignoring the /miniroot part of the path? Of course it will work if I copy the content of minroot to /IRIX/boot, but I would still like to now, why it doesn't work as expected.

---

