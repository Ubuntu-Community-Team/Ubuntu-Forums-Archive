---
title: "Unable to install Ubuntu 13.10 64 bit via iDRAC"
date: 2013-12-03
forum: Server Platforms
---

### Post by ops2 on 2013-12-03
Hi,

I have installed previous versions of Ubuntu on Dell servers like R610, R620, etc. but never came across this issue. 

During boot from iso image it displays "Intialization failed" (screenshot attached). After this it shows the screen to "Try Ubuntu" or "Install Ubuntu" but keyboard and mouse doesn't work remotely. I have not tried it yet from physical location yet. I have downloaded multiple images and tried several times.

Any help would be appreciated.

Thanks,

---

### Post by oldfred on 2013-12-03
I do not know servers. There is a separate sub-forum for servers. I can move thread if you like.

Are you installing desktop or server installer. Desktop is the one with live mode, server does not have live mode.

And desktop does not have RAID drivers that a server install flash drive would have.

---

### Post by ops2 on 2013-12-03
I would appreciate if you move it there. 

I am installing Desktop version on sever as we have done in the past. RAID is at hardware level so should not impact it (I think).

Thanks,

---

### Post by oldfred on 2013-12-03
Moved to Server Platforms.

---

### Post by ops2 on 2013-12-04
I have figured it out. Installed ubuntu server 13.10 edition and used a PS/2 keyboard to quickly install  ssh after installing OS. Then via SSH edit /etc/default/grub line to  

GRUB_CMDLINE_LINUX_DEFAULT="usbcore.autosuspend=-1"

and ran
[LIST]
[*]sudo update-grub
[*]sudo update-initramfs -u
[*]sudo shutdowwn -r now
[/LIST]

I am able to use usb keyboard and mouse after it. Also, installed ubuntu desktop to get GUI.

Looks like a know bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1244176](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1244176)

[http://askubuntu.com/questions/363811/dell-idrac-keyboard-does-not-work-after-ubuntu-13-04-to-13-10-upgrade](http://askubuntu.com/questions/363811/dell-idrac-keyboard-does-not-work-after-ubuntu-13-04-to-13-10-upgrade)

---

### Post by ops2 on 2013-12-04
Please mark it as closed.

Thanks,

---

### Post by Iowan on 2013-12-04
> **ops2 said:**
> Please mark it as closed.

Thanks,
It doesn't need to be closed, but you can mark it [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

