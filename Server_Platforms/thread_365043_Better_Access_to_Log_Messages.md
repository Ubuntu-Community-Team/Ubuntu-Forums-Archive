---
title: "Better Access to Log Messages"
date: 2007-02-19
forum: Server Platforms
---

### Post by AllBuntu on 2007-02-19
Hi All,

I have this gui-server I converted to raid and then got into a mess after some package upgrades, Installing the same setup from scratch in vmware, I can see that there is a difference in boot up sequence between a non-raid-converted-into-raid and an installed-as-raid machine. boot is md0, root file system md1, and var is md2. To be able to back up the file systems in off-line mode, I also added a 512 MB prompt-only boot partition with tools like sshfs, partimage, and openssh-server.

If I go into boot/grub/menu.lst and remove the "quiet splash," I can get a screenfull of messages on regular boot up (the same as for single mode.) However, bootlogd captures only a handful of these messages and valuable error-clues are missed. Errors scroll by quickly, so I resorted to filming it all with my camera so that I could examine each error in detail. These errors are not logged in any file in /var/log.

example 1: mount: wrong fs type, bad option, bad superblock on /dev/shm/var.run, missing codepage or other error In some cases useful info is found in syslog - try dmesg | tail or so

example 2: mount: special device /var/run does not exist

example 3: /etc/rcS.d/S40ifrename: line 12: /sbin/ifrename: No such file or directory

Q1 Is there a way to capture every character printed at startup, ie. from grub to login?
Q2 How do I capture the same on shutdown?
Q3 How do I get rid of the splash screen on-the-go, some magic keypress?

The errors I get seems to be because /var/run and /sys are not available at the early boot stages before raid is started. I will post about these and my findings soon too.

Don Buntu

---

### Post by AllBuntu on 2007-02-24
That key is Alt-F1

---

### Post by tgalati4 on 2007-02-24
I've noticed that as well and I have resorted to using a digital camera in video mode as a cheezy boot log capture.

Hitting esc a few times right before the boot splash seems to work for me, but I will take note of alt-F1.

Perhaps there is a boot code or simply pipe the kernel and initrd to standard out files?

Someone must know.

---

### Post by AllBuntu on 2007-03-03
So,
bootlogd seems to be inoperative in 6.10 Edgy
The kernel command quiet added by grub (see /boot/grub/menu.lst) suppresses most output during a regular boot

therefore,
if you boot your installation using the recovery entry, you will get every message there is, very briefly displayed on the console during boot. You have to be a quick reader.

Boot, camera, action

Harald Rudell

---

