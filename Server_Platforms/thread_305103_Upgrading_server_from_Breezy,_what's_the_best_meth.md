---
title: "Upgrading server from Breezy, what's the best method?"
date: 2006-11-22
forum: Server Platforms
---

### Post by glave on 2006-11-22
I've got a Breezy server that does our file sharing, LAMP, and mail server on it, and I was thinking about upgrading it. Should I do this or should I just let well enough alone?

If upgrading is feasible, should I do a standard apt-get dist-upgrade ?  


Any suggestions or comments appreciated!

---

### Post by JLTB on 2006-11-23
Hi glave,

A dist-upgrade should work just fine.  I upgraded my office's print / file server
a few months back with out trouble (was sharing over SMB/NFS with CUPS printer,
also a small Apache2 server for the dev guys).

The approach I took was to find and replace all the 'breezy' strings in my
/etc/apt/sources.list with 'dapper'.

You can do this with sed like so:
```

sudo sed -i 's/breezy/dapper/g' /etc/apt/sources.list

```

Then upgrade as normal :-)

Good luck!

PS: If you have a really wacky sources.list file, or you want to keep some lines
that say breezy from changing to dapper you might want to fine tune the results
by hand.  sed makes my life easier, so I use it.

---

### Post by glave on 2006-11-23
Did you just do an apt-get upgrade or an apt-get dist upgrade?

---

### Post by MJN on 2006-11-23
Check out [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades) - all you need to know.

(I am assuming you're upgrading to Dapper)

Mathew

---

### Post by glave on 2006-11-23
Death, destruction, and terror!!!


Ok, I went by the book on this, and everything went off without a hitch.... Until I rebooted.

```
Mounting /dev/md0 on /root failed: No such device
Mounting /root/dev on /dev/.static/dev failed: No such file or directory
Mounting /sys on /root/sys failed: No such file or directory
Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

```
At this point it drops me off to BusyBox v1.01 shell, and says
```
/bin/sh: can't access tty; job control turned off
#
```


Help please!

---

### Post by glave on 2006-11-23
Well, thankfully using grub's menu I was able to boot off of the previous kernel (2.6.12-9-386) and she booted up for me.

Any clue what to do on getting the correct kernel to boot for me now?

---

### Post by glave on 2006-11-24
I just checked my email, and I got this

```
WARNING! If you are using hard disks which have a md superblock from an
earlier installation in a different RAID array, you MUST zero the
superblock before activating the autostart feature.

To do this, do not start the RAID devices automatically. First, zero the
superblock (mdadm --zero-superblock /dev/mdX). Next, use `dpkg-reconfigure
mdadm` to reactivate the autostart feature.
```

I'll be honest, I have no idea what its talking about, but would this be the culprit thats keeping my new kernel from booting?

---

