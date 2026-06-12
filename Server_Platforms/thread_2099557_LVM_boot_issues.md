---
title: "LVM boot issues"
date: 2012-12-29
forum: Server Platforms
---

### Post by DavidKirkby on 2012-12-29
I have a 10.04 64-bit server that no longer boots with the message:

[FONT=Courier New]error: file not found[/FONT]

I booted with a 12.10 64-bit desktop liveCD and followed the instructions in this forum for installing and running boot-repair. My info is at [http://paste.ubuntu.com/1476779/](http://paste.ubuntu.com/1476779/). When I follow the "Recommended Repair" instructions, they fail at this step:

[FONT=Courier New]ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/mapper/darkmatter-root" apt-get install -y --force-yes mdadm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mdadm
0 upgraded, 1 newly installed, 0 to remove and 16 not upgraded.
Need to get 0B/239kB of archives.
After this operation, 676kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  mdadm
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 75, <> line 1.)
debconf: falling back to frontend: Readline
Preconfiguring packages ...
dpkg: warning: 'tar' not found on PATH.
dpkg: warning: 'update-rc.d' not found on PATH.
dpkg: 2 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/FONT]
Any advice on how to proceed or what might be wrong with my system is gratefully appreciated.

---

### Post by oldfred on 2012-12-29
Moved you to your own thread in the server area. In Boot-Repair thread you are buried at the end. Few that know LVM may look at Boot-Repair thread.

Do you have RAID or just LVM. I know neither.

Do you really have an 8GB LVM or drive? Or is that part of the issue?

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
lvm info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)

---

### Post by darkod on 2012-12-30
I don't see why boot-repair would try to install mdadm when you have only LVM and no mdadm. It might be a bug in boot-repair.

First, have you tried to boot the previous kernel? In the grub boot menu, instead of the latest 2.6.32-45 try booting the 2.6.32-44 kernel.

Second, boot again with the 12.10 live cd, add the lvm2 package to the live sesion and try to activate the LVM:
```
sudo apt-get install lvm2
sudo vgchange -ay
```

Do you get a message that both LVs activated all right?

Can you mount the root at some temp mount point and look inside? Does it open?

After that, if all looks fine, I suggest you try to purge and reinstall grub2 using chroot manually, not boot-repair.

---

