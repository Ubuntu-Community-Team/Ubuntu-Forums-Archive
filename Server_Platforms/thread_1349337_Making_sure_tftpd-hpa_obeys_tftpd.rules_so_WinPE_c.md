---
title: "Making sure tftpd-hpa obeys tftpd.rules so WinPE can boot off PXE"
date: 2009-12-08
forum: Server Platforms
---

### Post by Xianath on 2009-12-08
For those who are trying to boot WinPE, you know that the boot loader uses "\" as a path separator in TFTP requests. So your pxeboot.n12 will be found, but not your \Boot\boot.ini or \Boot\boot.wim or any other file. tftpd-hpa supports rewriting requests, and most FAQs on the Web refer to /etc/default/tftpd.rules containing a line like this:
```
rg \\ /
```
This works when tftpd-hpa is started as a daemon, but in Ubuntu it is started via xinetd. The corresponding line in /etc/inetd.conf is:
```
tftp           dgram   udp     wait    root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot
```
As you can see, it has no mention of the tftpd.rules file, so rewriting rules are ignored. This results in WinPE being unable to find its boot files and therefore being unable to boot. The following small correction fixes this:
```
tftp           dgram   udp     wait    root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot -m /etc/default/tftpd.rules

```
Having spent over a week trying to get Windows to boot off iSCSI (more than it took me to assemble the hardware, mod the box to hold all the harddrives, install and configure Ubuntu as a NAS/SAN, and build a 12x1TB RAID6 array), I hope this post helps someone get past this tiny annoying bit.

Cheers,
Peter

---

