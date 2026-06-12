---
title: "New Grub makes me happy!"
date: 2012-09-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ubername on 2012-09-14
Sometimes it's the little things that make a difference. I've been on ubuntu since 2007, literally gut the T-shirt for Gutsy Gibbon.

But the new grub menu has made me go 'That's so cool - that is indeed cool!' when I first saw it after reboooting today.

That's the first time for a while that a change to ubuntu has made me smile - a lot of changes I have learnt to love and some I have just learnt, but the new grub menu is very  nice!

---

### Post by GreatDanton on 2012-09-14
New Grub menu is working, however I didn't noticed any major differences. There is Ubuntu instead the number of kernel, and other versions of kernels are hidden, but that's all I noticed at the first sight. 

Regards.

---

### Post by EgoGratis on 2012-09-14
> **greatdanton said:**
> new grub menu is working, however i didn't noticed any major differences. There is ubuntu instead the number of kernel, and other versions of kernels are hidden, but that's all i noticed at the first sight. 

Regards.

> sometimes it's the little things that make a difference.

:d

---

### Post by xebian on 2012-09-14
It's a mess if your primary bootloader is from precise grub.

---

### Post by arpanaut on 2012-09-14
> **xebian said:**
> It's a mess if your primary bootloader is from precise grub.
That's a fact! [ATTACH]224129[/ATTACH]

I've updated two of my QQ installs to Grub2 and then gone back into my PP Grub controlling install and run update-grub. This a shot of the choice screen I a given, there are 20+ lines below what is visible.  Very much a mess and confusing...

I have 4 hard drives on this system and seldom allow the dev. release to control booting,
I guess I'm going to have to find a different solution  or tactic. Yikes.

Hopefully there will be a change in the os-prober script in the older grub to adjust for this situation.  Now I'm off to put grub2 (new) on to my primary boot drive and see what the new grub looks like from there, so I can have a better perspective before I go bugging this.

---

### Post by oldfred on 2012-09-14
Same issue, but first thing I do is turn off os-prober and copy my standard 40_custom into an install, so I only have entries for those I still want. I used to have several ISO boot entries, but converted that to one line with a config file.

I have this in my notes if I am using a new 40_custom to make the entry for my liveISOs. You can do the same for all the installs you may only want to boot on occassion and just have a couple of config files in 40_custom.
# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd2,4)/iso/livecdimage.cfg
#}

---

### Post by arpanaut on 2012-09-14
Thanks oldfred, I knew that, lol, I just had become accustomed to MY way of doing it.
Things change: Adapt or Perish.

In the long run this change will probably prove to be a great improvement.
Time will tell.

Edit: Well I tried the new selection screen and it looks nice but Meh!
I liked everything being up front and I sure miss the (on /dev/sdxy).
Guess I'll adjust over time.

---

