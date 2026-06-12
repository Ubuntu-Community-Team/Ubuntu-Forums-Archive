---
title: "Hardy Virtualbox 2.0.6 iPod will not restore"
date: 2008-12-14
forum: Virtualisation
---

### Post by alphaakenny1 on 2008-12-14
I am trying to restore my iPod via Virtualbox, my virtual machine can see the iPod and even begins to restore it.  Unfortunately half way through iTunes gives me an error (1429).  Anybody know why this is, I have an iPod Classic 6G.  Thanks.

---

### Post by dartmusic on 2008-12-18
I'm having the same problem on Intrepid 32bit, with VirtualBox 2.1.  

Anyone have any ideas?

Thanks!

---

### Post by rootrhift on 2009-07-02
I am having the same problem on Jaunty 9.04

Virtualbox-2.2.4 (non-free)
hosting a Windows XP v5.1 SP2
with iTunes 8.2.0.23

Have enabled USB filter for the iPod and have a guest addition of Virtualbox running in the Windows XP guest.

The iPod is a black 6G 80GB Classic (xB147)

iTunes will recognize and interface with the iPod, but when it goes to restore it will fail with a 1429 error.

My /etc/fstab contains:
```
none /proc/bus/usb usbfs devgid=128,devmode=666,nodev,nosuid,noexec 0 0
```

and I'm a member of the vboxusers group which has a gid of 128.

I can browse the iPod's file using Windows Explorer.

Any help would be appreciated.  Thanks.

---

### Post by alphaakenny1 on 2009-07-02
Hey I tried plenty of ways to accomplish this but none worked.  I'm guessing it's because the ipod is mounted with a specific name (John's Ipod) on the linux host.  So by the time you get to the 1429 error the virtual machine is trying to change this information or other information related to how the device is mounted.

For future reference, if you want to restore your ipod:

[INDENT]Use a Windows computer and restore it using iTunes.[/INDENT]

[INDENT]BEFORE PUTTING MUSIC ON IT make a backup of it.  Do this the linux way (dd command) so that if you ever want to restore your ipod in the future you can simply use dd again and voila you ipod is restored the same way iTunes would have done it.[/INDENT]

---

### Post by rootrhift on 2009-07-02
It's definitely not mounted in GNU/Linux when it's passed to the guest environment, or at least mount tells me it's not.

The most bizarre thing is that I can read and write to it through Windows Explorer, or sync using iTunes, but the restore operation fails.

Even "got a hold of" a copy of Vista and used iTunes 8 on that and it failed, so it does seem like there is some mishandling with Virtualbox's driver interface.  Maybe some special incompatibility case with the iTunes restore operation call to the Vbox drivers?

Tried to futz around with the driver settings in the guest OS too and nothing worked.  I'm hoping that somebody upstream knows about this or has a solution because that functionality would be nice for many reasons.

---

