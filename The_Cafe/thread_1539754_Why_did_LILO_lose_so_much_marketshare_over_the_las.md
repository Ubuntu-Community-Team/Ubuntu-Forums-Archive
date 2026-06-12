---
title: "Why did LILO lose so much marketshare over the last decade?"
date: 2010-07-26
forum: The Cafe
---

### Post by Cuddles McKitten on 2010-07-26
FOSS history question: I remember around 2002 virtually everyone used LILO.  Now it seems that almost everyone uses GRUB.  Is there any real reason for this?  I'm assuming it has a lot to do with Ubuntu using GRUB as the default, but why'd Canonical select it over LILO?

---

### Post by Kdar on 2010-07-26
Does openSuse is using GRUB now too?

If I remember correctly, it used Lilo, when I first tried it.

---

### Post by doorknob60 on 2010-07-26
I'm guessing sometime in that period (pre-Ubuntu), Debian decided to make GRUB the default, and since Ubuntu was built off Debian, they used GRUB too. That's just an educated guess though.

---

### Post by jerenept on 2010-07-26
LILO cannot load Windows, but GRUB can. There was a need to multiboot easily, and it was solved by GRUB.

---

### Post by cariboo on 2010-07-26
Back when I used LILO, I dual booted Windows and Redhat, later Mandrake, it has been able to multiboot for years.

---

### Post by mickie.kext on 2010-07-27
> **doorknob60 said:**
> I'm guessing sometime in that period (pre-Ubuntu), Debian decided to make GRUB the default, and since Ubuntu was built off Debian, they used GRUB too. That's just an educated guess though.
It was Red Hat. [http://lwn.net/Articles/89772/](http://lwn.net/Articles/89772/)

Today everyone use GRUB. Except Slackware I think.

---

### Post by Cuddles McKitten on 2010-07-27
> **mickie.kext said:**
> It was Red Hat. [http://lwn.net/Articles/89772/](http://lwn.net/Articles/89772/)

Today everyone use GRUB. Except Slackware I think.

Great link.  Thanks.

---

### Post by whiskeylover on 2010-07-27
Because she started doing drugs and violating her parole and... 

Oh wait, this thread is not about Lindsay Lohan :|

---

### Post by Guitar John on 2010-07-27
> **whiskeylover said:**
> Because she started doing drugs and violating her parole and... 

Oh wait, this thread is not about Lindsay Lohan :|

:mrgreen:

---

### Post by Slug71 on 2010-07-27
> **whiskeylover said:**
> Because she started doing drugs and violating her parole and... 

Oh wait, this thread is not about Lindsay Lohan :|

:lolflag:

---

### Post by realzippy on 2010-07-27
> **whiskeylover said:**
> Because she started doing drugs and violating her parole and... 

Oh wait, this thread is not about Lindsay Lohan :|

Thanks.1st smile today...:D

---

### Post by Eisenwinter on 2010-07-27
> **jerenept said:**
> LILO cannot load Windows, but GRUB can. There was a need to multiboot easily, and it was solved by GRUB.
LILO can load Windows.

---

### Post by SunnyRabbiera on 2010-07-27
Well I think its themability and its ability to access ext4

---

### Post by saulgoode on 2010-07-27
> **SunnyRabbiera said:**
> Well I think its themability and its ability to access ext4
LILO can boot EXT4 -- this is being posted from Slackware booting off an EXT4 partition. When the kernel devs get around to writing an EXT4 defrag utility, it will be necessary to re-run the 'lilo' command after defragging an EXT4 containing the /boot directory. If /boot is mounted to its own partition (a good idea in its own right) then one should never need to defrag it (nor would it need to be EXT4).

---

### Post by andrew.46 on 2010-07-28
A new version released recently:

[http://lilo.alioth.debian.org/](http://lilo.alioth.debian.org/)

Andrew

---

### Post by Dustin2128 on 2010-07-28
not sure.. I've always liked it. Also: It does support dual booting with any OS, ext4, and is the default in slackware as of 13.1.

---

### Post by ezsit on 2010-07-28
Back in the day, LILO was seen as old and limited because changing the boot menu required reinstalling LILO to the MBR each time to update the boot menu. GRUB allowed users to update a text file and be done with it. GRUB also allowed for more video modes to be used. 

GRUB was the future and LILO was the past, as many programs throughout history that still work are discarded for no better reason then that they have been around too long and no longer are sexy.

---

