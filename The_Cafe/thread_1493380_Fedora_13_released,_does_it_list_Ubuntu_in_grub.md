---
title: "Fedora 13 released, does it list Ubuntu in grub?"
date: 2010-05-25
forum: The Cafe
---

### Post by kahumba on 2010-05-25
Hi,
Fedora 13 has been released:
[http://fedoraproject.org/index.html.en](http://fedoraproject.org/index.html.en)

Did anyone install it on another partition with Ubuntu on another? Does it list Ubuntu in grub? I'm asking cause when I tried Fedora 12 it didn't hence I couldn't launch Ubuntu any longer so I had to do Google and extra work.

---

### Post by Hman242 on 2010-05-25
As long as Fedora 13 has GRUB2 you will be fine. If you are that worried, install Fedora without GRUB and update GRUB through Ubuntu with the following code in the Terminal.
```
sudo update-grub
```

---

### Post by kahumba on 2010-05-25
I didn't know/notice that the Live CD has such an option (not installing grub), I was also wondering whether this issue has been fixed since then.

---

### Post by neu5eeCh on 2010-05-25
According to Distrowatch, Fedora still uses Grub1. This means, unless they've tweaked it (which I doubt)  you will have the same problems.

Here's my solution (which is inelegant but works).

A.) Download and burn a copy of [Super Grub Disk]("http://www.supergrubdisk.org/").
B.) Install Fedora and let it completely screw with your MBR.
C.) Reboot (after install). 
D.) Run Super Grub Disk. SGD will generally show you all the OS's you can boot into (including Ubuntu).
E.) Boot into Ubuntu. Once Ubuntu is running: sudo update-grub and all will be well.

Note: You can probably do all this within SGD (without having to boot into Ubuntu).

---

### Post by RiceMonster on 2010-05-25
> **Hman242 said:**
> As long as Fedora 13 has GRUB2 you will be fine.

It still has the legacy grub.

---

### Post by wojox on 2010-05-25
I still have Fedora12 on mine, but you should be able to reinstall grub2 by using a Live CD of Ubuntu. I did it before.

---

### Post by kahumba on 2010-05-25
Thanks anyone I did as [Hman242]("http://ubuntuforums.org/member.php?u=925741") suggested (haven't installed Fedora's GRUB and did a sudo update-grub from Ubuntu), so now I can have both Fedora and Ubuntu in the bootup list without problems.

Hopefully Fedora 14 will come with grub 2.

---

### Post by RiceMonster on 2010-05-26
Just want to bump this thread, because I'm really liking this release, as is usual with Fedora

> **kahumba said:**
> Thanks anyone I did as [Hman242]("http://ubuntuforums.org/member.php?u=925741") suggested (haven't installed Fedora's GRUB and did a sudo update-grub from Ubuntu), so now I can have both Fedora and Ubuntu in the bootup list without problems.

Hopefully Fedora 14 will come with grub 2.

Why do you want grub 2?

---

### Post by oldfred on 2010-05-26
If Fedora is using grub legacy you can easily install it to the partition that you install Fedora to. Then add a custom entry to 40_custom to chainboot. You will have to go thru two menus, but the second will always have the current kernel as Fedora is updated.

Grub2 with chainboot examples
[http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0)

---

### Post by m4tic on 2010-05-26
Ubuntu 10.10 completely blocks mandriva 2010. I get a kernel panic. Mandriva is grub 1, anyone had this issue? I'm currently using mandriva since ubuntu came out

---

### Post by wojox on 2010-05-27
> **RiceMonster said:**
> Just want to bump this thread, because I'm really liking this release, as is usual with Fedora



Why do you want grub 2?

Yeah. I'm doing a fresh install now on my laptop. I was dual booting Fedora12 and Ubuntu10.04. I think I'm just gonna leave 13 as primary on my laptop.

---

### Post by wojox on 2010-05-27
> **m4tic said:**
> Ubuntu 10.10 completely blocks mandriva 2010. I get a kernel panic. Mandriva is grub 1, anyone had this issue? I'm currently using mandriva since ubuntu came out

I always let whatever distro install it's grub to the MBR than just reinstall Grub 2 with a LiveCD and have never had a problem.

---

