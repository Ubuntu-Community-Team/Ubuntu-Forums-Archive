---
title: "HOWTO: chroot - admin [Ubuntu] Linux on another partition"
date: 2008-04-02
forum: Tutorials
---

### Post by charlieg on 2008-04-02
I have two linux partitions - a handy set up that allows me to admin one from the other should something go wrong (e.g. with an upgrade) or I want to install something without booting into the other.  I have discovered this through various tutorials / docs scattered around the web but nothing had them all in one place so here it is: **charlieg's ace and simple guide to using chroot**

[list][*]*This is a very handy way to update between major distro versions and I have done it for Gutsy->Hardy - if it doesn't boot, you can boot into the working partition and solve the problem from there!*
[*]The following howto should apply to most Linux distributions.  You should even be able to boot into a liveCD and do this from the console.
[*]You will need to install 'chroot', and 'mount' should be there by default.
[*]**You gotta be root** (sudo is ok)[/list]

So, here it is:
```
[charles@localhost ~]# sudo -s -H
Password:
[root@localhost ~]# mount --bind /dev/ /media/ubuntu/dev
[root@localhost ~]# mount --bind /dev/pts /media/ubuntu/dev/pts
[root@localhost ~]# mount --bind /dev/shm /media/ubuntu/dev/shm
[root@localhost ~]# chroot /media/ubuntu
root@localhost:/# mount -t sysfs sysfs /sys
root@localhost:/# mount -t proc proc /proc
```
And that's it!  You're in!  The environment is set up to basically use the core devices from your active partition.  Now you should be able to admin-away without trouble.
```
root@localhost:/# aptitude update && aptitude dist-upgrade
```

---

### Post by charlieg on 2008-04-03
Oops, the 'su -' command is what I use on my Fedora partition - from Ubuntu it has to be 'sudo -s -H' to get a root capable terminal.  Corrected.

---

### Post by az on 2008-04-03
I have always done it simpler:

If the chroot directory is called chroot:

sudo chroot chroot
mount /proc
mount /sys
mount -t devpts none /dev/pts

and then do whatever you want...


To leave, you need to run:

umount -lf /proc
umount -lf /sys
umount -lf /dev/pts
exit

---

### Post by alSee on 2008-09-11
Console applications work fine by this method. But GUI ones generate such error:
```
xpsgui: cannot connect to X server :0.0
```
I use the temporary solution of starting vnc-server in chroot and vnc-client in current environment. But it isn't true way. 
Any suggestions?

---

### Post by octoberdan on 2009-03-22
Thank you for the tutorial! I was running Slackware based environment (Backtrack3) chrooting into an Ubuntu environment. However, I ran into some difficulties regarding network connectivity; the chroot environment didn't have an IP address but couldn't get one as the Slackware environment had a dhcp client running. Here's what happened:

```

/# dhclient
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:08:74:e5:90:6b
Sending on   LPF/eth1/00:08:74:e5:90:6b
Listening on LPF/eth0/00:16:6f:55:68:77
Sending on   LPF/eth0/00:16:6f:55:68:77
Can't bind to dhcp address: Address already in use
Please make sure there is no other dhcp server
running and that there's no entry for dhcp or
bootp in /etc/inetd.conf.   Also make sure you
are not running HP JetAdmin software, which
includes a bootp server.

```

Oh nose! So I went into the host machine (non-chroot environment) and found the process of the dhcp program and killed it:

```

bt ~ # ps aux | grep dhcp
root      7830  0.0  0.0   1676   224 ?        Ss   22:18   0:00 /sbin/dhcpcd -t 60 eth0
root      8413  0.0  0.2   1760   512 pts/2    R+   22:54   0:00 grep dhcp
bt ~ # kill 7830

```

In other environments,  the dhcp program may be different. Debian based operating systems (such as Ubuntu) usually use dhclient.

Hope this info helps someone...

---

### Post by justin.perkins on 2012-05-16
thanx for this, cheers. :) using it to mount a usb-fs which I had loaded up into ramdisk, to update/switch contexts while running from ram, to disk, then exit back into the ramdisk version. handy. :)

---

### Post by nothingspecial on 2012-05-16
old thread.

Closed.

---

