---
title: "Cannot boot to window after install elementary os"
date: 2015-03-18
forum: Ubuntu/Debian BASED
---

### Post by hoangnguyen2 on 2015-03-18
[COLOR=#141823][FONT=Helvetica]Elementary os is a distro of Ubuntu so i posy my problem here.
Last week, i install elemetary on on of my 3 partition so that i can dual boot it with window 8. After a couple day plaaying with eOS, i back to window 8.
The problem is window 8 appeared in grub, but whenever i select window 8 and hit enter, it reload the grub.
I think it was the grub problem so i decided to recover MBR from Grub. I read something in the internet and i install boot-repair in eOS and i select "recover mbr" but it didnt fix the problem.
Then i think it was the OS problem, and i decided to uninstall eOS, 1 important thing is that i can not boot in to window 8. Then i boot from my usb stick which include window installation disk. Select repair my computer, command prompt and i delect the eOS partition and i use the "bootrec /fixmbr" and "bootrec /fixboot" hope it would fix the problem but.. After reboot, the display show a black screen with a blinking cursor. How can i fix it?[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]Update: i try to reinstall window 8 on 2 of my 3 partition (the other partition is important so i can not install win 8 on it) but the black screen with blinking cursor show up again!
[/FONT][/COLOR]

---

### Post by QIII on 2015-03-19
Moved the ***Ubuntu/Debian Based***.

Elementary is based on Ubuntu, but it is not a flavor of Ubuntu.  It is a distinct distribution.

I'm sure someone will be happy to help you, though.

Cheers!

---

### Post by reef2dive on 2015-03-19
For Windows 8, I seem to remember that it uses 2 partitions, of which one is hidden. That is the partition that Windows 8 actually boots on.
If you use gparted, the partition manager, to view your disk, is the Windows partition the first and do you see 1 or 2 windows partitions?

---

### Post by hoangnguyen2 on 2015-03-19
> **reef2dive said:**
> For Windows 8, I seem to remember that it uses 2 partitions, of which one is hidden. That is the partition that Windows 8 actually boots on.
If you use gparted, the partition manager, to view your disk, is the Windows partition the first and do you see 1 or 2 windows partitions?
I have 3 partition, the dev/sda1 is window 8, the dev/sda2 is my data and dev/sda3 is free where i free it from delete elementary os

---

### Post by reef2dive on 2015-03-20
As you have cleaned the boot record, there is no grub anymore.
You can check the boot flag of sda1 in gparted, if it is set or not.
I do not know how to fix mbr for a Win8 setup.

---

### Post by pi32 on 2015-03-24
Hi there,

I'm running Freya and Win 8 on my current computer with no particular issue.
Could you tell me a bit about what happened when you tried to re-install windows 8? This should have replaced the MBR and ou should have boot on it.
Also, does your computer have UEFI boot? In my case, I know that when the computer boots I can select the partition and boot straigh to windows. This seems to shunt some part of the process.

Last question: which version of EOS are you using?

Note: I'm pretty new to this forum and just trying to give a hand based on my own experience ;)

---

