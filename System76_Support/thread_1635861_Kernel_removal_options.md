---
title: "Kernel removal options"
date: 2010-12-02
forum: System76 Support
---

### Post by andrewdied on 2010-12-02
I'm trying to prune my ever-growing list of kernels when I boot (ubuntu 10.10).  From various articles I see that I should search for "linux-image" and then either choose "removal" or "complete removal."  

My understanding of "complete removal" is that it does a more thorough job of removing files that are dependent on the selected package.  Normally this doesn't bother me, but for kernels I tend to panic (pun intended).  *I really* don't want to remove a module in one kernel that is required by a newer one.

What's the real preferred choice?  I still surprised that there isn't a standard Ubuntu method to do this since it must happen with all users, and users are (understandably) concerned about making their system un-bootable.

---

### Post by HotShotDJ on 2010-12-02
> **andrewdied said:**
> My understanding of "complete removal" is that it does a more thorough job of removing files that are dependent on the selected package.  Normally this doesn't bother me, but for kernels I tend to panic (pun intended).  *I really* don't want to remove a module in one kernel that is required by a newer one.Using "complete removal" is safe for removing kernel packages.  I do it whenever I need to remove old, unused kernels.  Different kernels do not share module "trees."  Each kernel has its own complete set of modules stored under /lib/modules/.

---

### Post by libssd on 2010-12-02
> **andrewdied said:**
> I'm trying to prune my ever-growing list of kernels when I boot (ubuntu 10.10).  From various articles I see that I should search for "linux-image" and then either choose "removal" or "complete removal."  

My understanding of "complete removal" is that it does a more thorough job of removing files that are dependent on the selected package.  Normally this doesn't bother me, but for kernels I tend to panic (pun intended).  *I really* don't want to remove a module in one kernel that is required by a newer one.

What's the real preferred choice?  I still surprised that there isn't a standard Ubuntu method to do this since it must happen with all users, and users are (understandably) concerned about making their system un-bootable.
I have done removed old kernels with Synaptic, but Ubuntu Tweak has a simpler UI for this. I normally keep latest + two older kernels installed; they don't take up that much space, and you never know....

---

### Post by Flyers2391 on 2010-12-03
I removed several old kernels through synaptic, although I didn't do a "complete removal" and my list did not change at boot ... all of the removed ones were still there.  I'm not sure if this is usual and a second step is required (editing grub menu.lst or something)

---

### Post by isantop on 2010-12-03
Two old kernels is easily enough. I only keep one, for a total of two kernels total. There is certainly nothing wrong with keeping more than that, since many Ubuntu users don't do anything with old kernels at all. However, if you want to prune, more than two, while fine, is a bit redundant. The odds of having two bad kernels at a time are astronomically low, and if you can't boot one of two, I'd be looking at a configuration issue instead.

Flyers2391: What version of Ubuntu are you using? You may just need to remove a few configuration files.

---

### Post by Derath on 2010-12-06
You can also use the grub configuration to trim down the boot list, I usually keep mine between 3-5 kernel versions. I guess I'll have to check synaptic to see how many kernels are still loaded on this laptop.

---

### Post by isantop on 2010-12-06
I should note that my two-kernel limit doesn't apply to recovery mode entries. *Always* keep a recovery mode option for each kernel you have, unless you are absolutely sure how to invoke it at boot up.

---

### Post by andrewdied on 2010-12-07
Complete removal worked just fine for me, by the way.  A good chunk of the reason I like to have fewer kernels is I dual boot with XP, and XP is way down at the bottom of the list.  Yes, I'm that lazy that I avoid having to down arrow too much.  (vi keystrokes don't work in the GRUB menu.)

---

### Post by libssd on 2010-12-07
> **andrewdied said:**
> Complete removal worked just fine for me, by the way.  A good chunk of the reason I like to have fewer kernels is I dual boot with XP, and XP is way down at the bottom of the list.  Yes, I'm that lazy that I avoid having to down arrow too much.  (vi keystrokes don't work in the GRUB menu.)
You can always edit the grub/grub2 menu to put XP as the first choice; of course, then you MUST invoke the Grub menu to choose. It all depends on what is least inconvenient.

---

