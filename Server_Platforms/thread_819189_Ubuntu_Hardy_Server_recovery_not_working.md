---
title: "Ubuntu Hardy Server recovery not working"
date: 2008-06-05
forum: Server Platforms
---

### Post by Franic on 2008-06-05
Hi all,

I installed an Ubuntu Hardy Server which worked fine. The root was on a software raid1 /dev/md0 and the swap on another software raid1 /dev/md1.

The only problem is I made a mistake and it didn't work anymore.

Fortunately I knew it could happen, so when it was working I made an image of the root with partimage using SystemRescueCD.

When the Ubuntu Server was broken, I recovered using this image and put it back on the raid /dev/md0 which was the root of my system. Then I installed grub on the MBR in each disk.

When I reboot, grub runs fine. But the Ubuntu Server doesn't want to start and I have this error message:
ALERT DOES NOT FIND MD0
and it starts in busybox mode.

Unfortunately if I boot SystemRescueCD it finds perfectly my 2 software raid1.

I've checked the files mdadm.conf and menu.lst, and they seem correct.

Anyone knows why the recovered Ubuntu Hardy Server from a working image doesn't want to start? Why can't it find /dev/md0?

Thanks.

---

### Post by gtdaqua on 2008-06-05
Not sure - But Ubuntu uses UUID to gracefully identify volumes. The /dev/mdx numbers might change at every boot and that is why disks are identified by their UUID.

Btw, why do you want to use a soft raid? You said you made a mistake(!) - what exactly is that?

---

### Post by Franic on 2008-06-05
Thanks for your reply. The problem occurs every time I recover. I've tried many times to boot a Live CD, and every time it was /dev/md0. And the files menu.lst are exactly the same.

I have to use soft raid because I want to use shell scripts to change the raid whenever I want (I'm working on a home server). Hardware raid is managed from the bios, so I can only use soft raid.

For the mistake I'm currently working on shell scripts, and some modify important system settings like grub. For an unknown reason (maybe the umount -a...) my script was killed, and the system was broken. Because I knew it could easily happen I made a backup.

---

