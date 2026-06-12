---
title: "XEN GUTSY - LOCkUP ON BOOT"
date: 2007-11-06
forum: Server Platforms
---

### Post by avalonpimp on 2007-11-06
Hello, I installed a fresh 32bit gutsy server install. I followed this guide to install XEN and create images. 
[http://www.howtoforge.com/ubuntu-7.10-server-install-xen-from-ubuntu-repositories-p2]("http://www.howtoforge.com/ubuntu-7.10-server-install-xen-from-ubuntu-repositories-p2")
I used Lvm instead of images, but people seem to be getting similar errors, as seen in this launchpad link. 
[https://bugs.launchpad.net/ubuntu/+source/xen-3.1/+bug/144631](https://bugs.launchpad.net/ubuntu/+source/xen-3.1/+bug/144631)[https://bugs.launchpad.net/ubuntu/+source/xen-3.1/+bug/144631]("https://bugs.launchpad.net/ubuntu/+source/xen-3.1/+bug/144631")

anyone used XEN in gutsy with success? i never had this problem in feisty. 
it locks-up after it tries to mount ext3 FS, the launchpad has the details. I'm looking for a fix>?? ideas?

---

### Post by Johnathon on 2007-11-07
Does it help to follow the things here:
[http://lists.cvsrepository.org/xen-tools/Jul07/0332.html](http://lists.cvsrepository.org/xen-tools/Jul07/0332.html) ??

---

### Post by jbalders on 2007-11-07
The problem has something to do with the initialization of the console, or outputting data to the console.  It seems to happen right after the root volume is mounted.  I forget the exact cause of it.  By default, Xen apparently looks for either ttyS0 or tty1, but the Ubuntu console is apparently attached to xvc0, or somesuch.

Edit /etc/xen-tools/xen-tools.cfg, and at the end of the file, you'll find:

# serial_device = tty1 #default
serial_device = xvc0
#
# disk_device = sda  #default
disk_device = xvda

Edit yours to match.

Here are my notes for creating a Gutsy domU hosts on a Gutsy dom0 host.

1) xen-create-image --memory 512 --swap 1024 --hostname xen4 --ip 1.2.3.4 --bridge xenbr0 --mac 00:16:3e:01:02:03 --dist gutsy --mirror [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) --lvm vg-xenimage
The defaults for this command can be found in /etc/xen-tools/xen-tools.conf
2) mount /dev/vg-xenimage/xen4-disk /mnt
2.1) cd /mnt/etc
2.2) vi securetty (add xvc0 under ttyS0)
2.3) cd /mnt/etc/event.d; cp tty1 xvc0; vi xvc0 (%s/tty1/xvc0/g)
2.4) cd / ; umount /mnt
3) vi /etc/xen/xen4.cfg (%s/sda/xvda/g)

Common
------
The MAC address must be manually set so that it will be consistent across 
reboots and be unique for each host.  It appears that any MAC address 
starting with 00:16:3e should work, but we can just start with a set point 
and increment: i.e., 00:16:3e:01:02:01, 00:16:3e:01:02:02, 00:16:3e:01:02:03

The /etc/xen/xen4.cfg config file created by the steps above looks like this (blanks and comments stripped for brevity):

kernel      = '/boot/vmlinuz-2.6.22-14-xen'
ramdisk     = '/boot/initrd.img-2.6.22-14-xen'
memory      = '512'
root        = '/dev/xvda1 ro'
disk        = [ 'phy:vg-xenimage/xen4-disk,xvda1,w', 'phy:vg-xenimage/xen4-swap,xvda2,w' ]
name        = 'xen4'
vif         = [ 'bridge=xenbr0,ip=10.3.1.223,mac=00:16:3e:70:cd:02' ]
on_poweroff = 'destroy'
on_reboot   = 'restart'
on_crash    = 'restart'
extra = ' TERM=xterm xencons=xvc console=xvc0'

I hope this helps.

---

### Post by jbalders on 2007-11-07
One other thing I just remembered,

edit /usr/lib/xen-tools/gutsy.d/15-disable-hwclock

and right after:
chroot ${prefix} /usr/sbin/update-rc.d -f hwclock.sh remove

add:
rm -f ${prefix}/etc/init.d/hwclock.sh ${prefix}/etc/init.d/hwclockfirst.sh ${prefix}/etc/udev/rules.d/85-hwclock.rules

Otherwise you'll have problems when it boots up trying to read the hardware clock, which isn't possible in a domU.

You'll need to make similar changes for any other Ubuntu distro that you use.  I seem to remember making the same change to install dapper.

---

### Post by ekimregnirps on 2007-11-08
Hi, great advice for xen on gutsy thanks. I got it to work in almost the same way, as Gutsy as DomU.


I used xen-tools and made these modications based on .... [HERE]("https://bugs.launchpad.net/ubuntu/+source/xen-3.1/+bug/144631")

===================================================================
===================================================================

```
sudo echo "extra = ' TERM=xterm xencons=tty console=tty1'" >> /etc/xen-tools/xm.tmpl
```

** To double check, after you create the Xen Image with Xen Tools...**
** make sure in your DomU config file, at the bottom has extra='xencons=tty' **


===================================================================
===================================================================

```
sudo nano /usr/lib/xen-tools/gutsy.d/30-disable-gettys 
```

Add this line = 

```
cat ${prefix}/etc/event.d/tty1 | sed "s/tty1/xvc0/" > ${prefix}/etc/event.d/xvc0
```

Added beneath:

```
rm ${prefix}/etc/event.d/tty[!1]
```

======================================================================================================================================

```

sudo nano /usr/lib/xen-tool/gutsy.d/25-disable-hwclock
```

Add this line = 

```
rm -f ${prefix}/etc/init.d/hwclock.sh ${prefix}/etc/init.d/hwclockfirst.sh ${prefix}/etc/udev/rules.d/85-hwclock.rules
```

Below these lines:

```
chroot ${prefix} /usr/sbin/update-rc.d -f hwclock.sh remove
chroot ${prefix} /usr/sbin/update-rc.d -f hwclockfirst.sh remove
```

then create your xen image using xen-create-image, and use a manuel MAC address in xen domU config file.

======================================================================================================================================

---

### Post by distratios on 2007-11-29
Hi!

I'm trying to set up a debian domU on gutsy and ran into the same problems. However, your fix does not work for me. Booting the debian guest hangs and after a while I get

[FONT="Fixedsys"]INIT: Id "1" respawning too fast: disabled for 5 minutes[/FONT]

I checked the guests inittab. tty's are commented out and the first line begins with 1 and ends with xvc1. There is also an xvc1 entry in securetty.

Obviously, there is a problem with the console, but I am not able to locate it. Any ideas?

---

### Post by UncleLumpy on 2008-02-01
Wonderful!  Thanks guys, worked for me on 7.10 AMD64

---

