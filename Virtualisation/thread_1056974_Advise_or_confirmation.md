---
title: "Advise or confirmation?"
date: 2009-02-01
forum: Virtualisation
---

### Post by arkiedan on 2009-02-01
Okay! I've finally gone completely over to Ubuntu 8.10 on the following  system and I could sure use some help:

AMD64 processor 3200+ 2.00 GHz
1Gb memory
2 250Gb sata Hard drives, the first EXT3 and the second NTFS (containing 120Gb of data, photos, etc) 

First, I think I made a rookie mistake installing Ubuntu on the first drive and not partitioning a separate "Home" partition. 

Second, I think I made another rookie mistake by installing Virtualbox (Windows XP in it) on the first drive, rather than on the second drive.

I'm getting a handle on Ubuntu and Virtualbox (and love it!) but I could use some advise in the following areas:

Would repartitioning a separate "Home" partition be of benefit and can I move the current Home contents over to that new partition?

Would adding a new virtual drive on the second hard drive and installing Windows XP there (rather than on the first drive) give me a noticeable speed boost? (I've turned off a lot of the unneccessary eye-candy in XP, stolen a little of the main memory from Linux in Virtualbox and it does run a bit faster without noticeably hurting Ubuntu's performance.)

Would adding a second Gb of memory give me a noticeable speed boost or would that be essentially a waste of time and money? 

I've dual-booted Linux and Windows in the past and it was always a pain to boot back and forth between the two systems. This virtualization thing is fantastic, giving me the option to put Windows XP on one desktop and Linux on another. A simple jump to desktop two and I'm in my Legacy genealogy program - back to Ubuntu for everything else. 

I should add that right now everything is rock solid. Ubuntu 8.10, Virtualbox, Windows XP and even Compiz, where I've enabled most features. 

Any thoughts - recommendations would be appreciated. Thanks in advance and sorry for the long post,

arkiedan

---

### Post by arkiedan on 2009-02-02
You know, I'll admit these aren't difficult questions I asked but I thought one of the more experienced guys here would be willing to give me a couple answers. I'm an old guy who's trying hard to get this down. But nope. Scrolled right off to page two and beyond.

Thanks boys

---

### Post by Dies on 2009-02-02
> **arkiedan said:**
> You know, I'll admit these aren't difficult questions I asked but I thought one of the more experienced guys here would be willing to give me a couple answers. I'm an old guy who's trying hard to get this down. But nope. Scrolled right off to page two and beyond.

Thanks boys

That is one of the unfortunate side effects of such an active forum. It is very easy for a post to get lost quickly. ;)


To answer your question, yes, it would be beneficial to have a separate "home" or data partition. And yes, you should probably resize your / partition and move your data over. Remember your OS is easily replaceable, your data is not.

To do this you can use something like

[http://partedmagic.com/](http://partedmagic.com/)

to resize your / partition and create a new partition, then copy the contents of your current /home over with something like

```
cp -rpv /currenthome /newhome
```

after checking to make sure everything is there, you can clean out your old home

```
rm -rf /home/*
```

and add your new home to fstab i.e.

```
gksudo gedit /etc/fstab
```
```

/dev/sda?     /home	  ext3  defaults    0  0
```
or if you labeled the new partition
```
LABEL=Home    /home     ext3   defaults   0  0
```


As far as VM performance goes, I've never had an issue, XP always runs at near native speeds, in some cases faster. But then I've always had 2 gigs or more of RAM and I use VMware.

More memory is never a waste of money, especially not at todays pricing, not unless you already have 4 gigs or more that is.

As for whether keeping the VM's themselves on a separate drive would help, I assume there would be some slight improvement but not sure on that. This should just be a matter of moving your VM's over and pointing VMware or Virtual Box to them, no need to "reinstall" anything since they're all just files. ;)

---

### Post by arkiedan on 2009-02-03
> **Dies said:**
> 

To answer your question, yes, it would be beneficial to have a separate "home" or data partition. And yes, you should probably resize your / partition and move your data over. Remember your OS is easily replaceable, your data is not.

To do this you can use something like

[http://partedmagic.com/](http://partedmagic.com/)

to resize your / partition and create a new partition, then copy the contents of your current /home over with something like

```
cp -rpv /currenthome /newhome
```

after checking to make sure everything is there, you can clean out your old home

```
rm -rf /home/*
```

and add your new home to fstab i.e.

```
gksudo gedit /etc/fstab
```
```

/dev/sda?     /home	  ext3  defaults    0  0
```
or if you labeled the new partition
```
LABEL=Home    /home     ext3   defaults   0  0
```


As far as VM performance goes, I've never had an issue, XP always runs at near native speeds, in some cases faster. But then I've always had 2 gigs or more of RAM and I use VMware.

More memory is never a waste of money, especially not at todays pricing, not unless you already have 4 gigs or more that is.

As for whether keeping the VM's themselves on a separate drive would help, I assume there would be some slight improvement but not sure on that. This should just be a matter of moving your VM's over and pointing VMware or Virtual Box to them, no need to "reinstall" anything since they're all just files. ;)

Much appreciated. I'm aware these are newbie questions but it looks like I'm going to be running this system for quite a while. Just ordered some new RAM and am moving on your instructions.

Thanks and Cheers! arkiedan

---

### Post by niteshifter on 2009-02-03
Hi,

I believe you'll want to delete your original /home after you edit fstab and restart.

---

