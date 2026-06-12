---
title: "&quot;Boot loader didn't return any data&quot; following Xen Guide"
date: 2013-01-12
forum: Virtualisation
---

### Post by asdf32 on 2013-01-12
Hi,

I have an Ubuntu 12.10 install.  I followed the Xen Guide at [https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen) about two weeks ago and found everything worked fine.  I then tried again recently (another completely clean setup), and found I was unable to start the Ubuntu guest VM, receiving "Error: Boot loader didn't return any data".

I think the only difference is that the second time I did an "apt-get upgrade" before starting the Xen Guide.  There seems to be a bug reported:

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/1094247](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/1094247)

It sounds like pygrub can't handle the submenu blocks, although removing the submenus didn't seem to work for me - pygrub still doesn't find the kernel when I run pygrub directly, pointing it at the root partition of the guest.  Is anyone else seeing this issue?

Iain

---

### Post by asdf32 on 2013-01-13
Just did a clean install again without doing an upgrade and the same error occurs, so probably not due to the upgrade.
- The "sudo xm create<configfile> -c" gives "Error: Boot loader didn't return any data".
- Looking in /var/log/xen/xend.log the error is repeated, but I can see it is running pygrub pointing at the LVM volume for the guest.
- Running pygrub manually gives "RuntimeError: Unable to find partition containing kernel".  This is caused by an exception when parsing the Grub configuration "invalid literal for int() with base 10: ..."

It looks like there are some problems in the scripts called by pygrub.  In the Grub2ConfigFile I think the title_match should be minimal '^menuentry ["\'](.*?)["\'] (.*){', otherwise it gets the title of the configuration wrong.  Then in GrubDiskPart it assumes that everything after the first two characters in the "root" assignment in grub.conf is a number (why would this be?)  Just sticking a try/catch around this allows it to proceed a bit further, and I can get pygrub bringing up a menu, but I'm still not able to boot the guest.

Is there a problem with having LVM inside the LVM volume set aside for the guest?  (Looking online it appears other people seem to be able to do this?)

---

### Post by asdf32 on 2013-01-15
The issue appears to be using LVM in the guest.  Works fine without.

---

### Post by asdf32 on 2013-06-09
Thought I'd post the general solution here in case other people have this issue as this seems to be popping up on Google.  [COLOR=#000000][FONT=Arial]The usual reason for this error is a change to grub.cfg that the pygrub loader doesn't understand.  To make life more interesting the actual error is often masked by the "boot loader didn't return any data" message.  The steps below describe how to correct your grub.cfg.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Mount the disk image using kpartx (if you're using a real partition then just mount that - this is just for a disk image):[/FONT][/COLOR]

```
kpartx -av disk.img
```
[COLOR=#000000][FONT=Arial]
This will print out the loopback devices it has created in /dev/mapper, one for each partition.  Mount the boot partition:[/FONT][/COLOR]

```
mount /dev/mapper/loop2p1 mntpoint
```
[COLOR=#000000][FONT=Arial]
Find pygrub - it is probably in /usr/lib/xen-4.1/lib/python.  Determine where the libs are being loaded from, and track down the GrubConf.py file.  (the file lives in /usr/lib/xen-4.1/lib/python/grub under Ubuntu 12.04).
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
Run the GrubConf.py manually on the configuration in the boot partition.[/FONT][/COLOR]

```
python /usr/lib/xen-4.1/lib/python/grub/GrubConf.py grub2 mntpoint/grub/grub.cfg
```
[COLOR=#000000][FONT=Arial]
You should then be able to see the error message that is normally hidden by pygrub (usually something about brackets as it gets confused by submenus).  Adjust the grub.cfg as appropriate (make a backup first!), then unmount and retry booting the VM.[/FONT][/COLOR]

---

