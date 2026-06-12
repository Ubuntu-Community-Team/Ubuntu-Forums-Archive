---
title: "Ubuntu LTSP illegal filename"
date: 2016-11-25
forum: Server Platforms
---

### Post by dshah on 2016-11-25
When I try to connect my client to server I receive below error:

```
PXE-T00: illegal filename (/ltsp/i386/pxelinux.0)  you may not attempt to descend or ascend directories
PXE-E36: Error received from TFTP server
PXE-H0F: Exiting PXE ROM
```

I am using ubuntu 16.04 server version.

---

### Post by dshah on 2016-11-25
the error gone when i setup next server to 192.168.1.2,,But now I face ARP timeout error

---

### Post by dshah on 2016-11-26
I was able to setup LTSP following this guide: [https://ubuntuforums.org/showthread.php?t=2173749](https://ubuntuforums.org/showthread.php?t=2173749)

When I used a normal PC I can login to the server but when I use thin client I only see my cursor on display with blank screen, there is no error in /var/log/syslog...

any help please?

---

