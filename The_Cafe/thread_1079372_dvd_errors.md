---
title: "dvd errors"
date: 2009-02-24
forum: The Cafe
---

### Post by card_ace on 2009-02-24
i know this is supposed to be the non techy area, but i can't think of where else to put this.  over the summer i created a bunch of dvds with all my moms pictures on them so we could free up some disk space on our hard drive.  i made sure i checked every disk and they all worked fine and had the pictures when i made them.  we put the disks in yesterday and the computer is reading them as blank.  what happened to my pictures?  and she's threatened to disown me if i don't fix it soo.......:lolflag:

---

### Post by mips on 2009-02-25
> **card_ace said:**
> i know this is supposed to be the non techy area, but i can't think of where else to put this.  over the summer i created a bunch of dvds with all my moms pictures on them so we could free up some disk space on our hard drive.  i made sure i checked every disk and they all worked fine and had the pictures when i made them.  we put the disks in yesterday and the computer is reading them as blank.  what happened to my pictures?  and she's threatened to disown me if i don't fix it soo.......:lolflag:

First try it in another drive, does it work?
Did you create them as normal data DVDs?
What brand media did you use?

Some optical media is really crap and don't last long. I've had this happen with el-cheapo CDRs before. I now only buy Verbatim media. There are also Archival grade media available that is gauranteed for xx years.

---

### Post by handy on 2009-02-25
By the way, did you happen to create them in a version of windows?

If so, you could have created them in a way that is atypical as far a Linux is concerned.

UDF is not handled straight up in Linux, or at least Ubuntu anyway. You may need to change an optical drive parameter in your /etc/fstab to auto instead of noauto.

---

### Post by card_ace on 2009-02-25
> **handy said:**
> By the way, did you happen to create them in a version of windows?

If so, you could have created them in a way that is atypical as far a Linux is concerned.

UDF is not handled straight up in Linux, or at least Ubuntu anyway. You may need to change an optical drive parameter in your /etc/fstab to auto instead of noauto.

i created them in windows vista, and that's the same system i used to test them before and it worked.  Now on the same machine its reading them as blank.

---

### Post by handy on 2009-02-25
> **card_ace said:**
> i created them in windows vista, and that's the same system i used to test them before and it worked.  Now on the same machine its reading them as blank.

I think that your problem is most likely caused by Linux not reading the UDF type of disk.

If this is the case you can fix it by modifying your /etc/fstab file

To do this you will need to enter the following in the Terminal:

sudo nano /etc/fstab

after which look for the line in your fstab that has something like the following in it:

/dev/cdrom      /mnt/cdrom      iso9660   ro,user,***noauto***,unhide   0      0

Change the noauto to ***auto*** & see if that helps you out?

---

### Post by card_ace on 2009-02-25
i may not have been clear enough sorry.  i'm still trying to access them on the windows machine.  would i have better chances using ubuntu or my XP partition instead of vista?

---

### Post by card_ace on 2009-02-26
ok nevermind i figured it out.  for some reason windows vista just won't read the disks even though that's what i used to create them.  i used windows xp and it worked fine.

---

