---
title: "Linux on a USB stick"
date: 2009-12-14
forum: The Cafe
---

### Post by rasmus91 on 2009-12-14
Hi there.

Yesterday i installed Ubuntu on my new 8 GB USB stick. not live CD, but full. it runs a little slower than when installed on hard disk... well a lot slower, but it's still quite smooth.

I've installed the Mac4Lin, and i like the "Mac" feel. (don't think i prefer mac, that would be a wrong assumption.)

I have a problem with The Aqua theme though. it's not all loading bars which are good looking, some of them look like they're windows 95, if anyone can help me out with this, please do.

Anyway. I'm considering building my own Linux using "Linux from Scratch" a Linux designed to boot from USB, with the features i want.

So i'd like to hear your opinions on two things:

1. have/do you use Linux on a usb (which, how good is it, and so forth)

2. I'd also like to know if any of you have ever build you own Linux distro using "Linux from Scratch" and if you have any tips for me.

See ya'll later, Rasmus

---

### Post by longtom on 2009-12-14
to 1.

Yes - I did Ubuntu on a stick and than Puppy.  Stayed with Puppy for what I use the stick for. Find it fast, sleek, pretty, adaptable, good hardware recognition (which is important to me) and works with most PCs who are still alive and kicking.

to 2.

No - no tips.  I just heard it is not for the faint hearted.  

I certainly have not accumulated enough wisdom nor do I have the time to accumulate it at present to use it.

But once you know it Linux will be a lot less cryptical for you than it is for me.

---

### Post by earthpigg on 2009-12-14
> 2. I'd also like to know if any of you have ever build you own Linux distro using "Linux from Scratch" and if you have any tips for me.

unless you plan to do something that hasn't already been done 500 times before, your time is probably more wisely invested in learning an ***existing*** system inside and out.

---

### Post by rasmus91 on 2009-12-14
> No - no tips. I just heard it is not for the faint hearted

Good thing I'm a quick learner when it comes to everything about software.

> unless you plan to do something that hasn't already been done 500 times before, your time is probably more wisely invested in learning an existing system inside and out.

not going to do anything like that at all, gonna try something a lot different.

---

### Post by soni1770 on 2009-12-14
is great for checking out your mates computers without them knowing

---

### Post by daverich on 2009-12-14
aye puppylinux is king for usb-sticky-os-ness

you can almost hear it go WhoooOOOSH! when it boots up :)

Kind regards

Dave Rich

---

### Post by Mighty_Joe on 2009-12-14
> **rasmus91 said:**
> 
1. have/do you use Linux on a usb (which, how good is it, and so forth)


I've been running Ubuntu on a USB drive since April.  No problems here.
I posted some links [here]("http://ubuntuforums.org/showthread.php?t=1193680") to some tips on how to optimize your USB install as well as minimize unnecessary writes to the drive (flash can wear out).

---

### Post by earthpigg on 2009-12-14
> **rasmus91 said:**
> not going to do anything like that at all, gonna try something a lot different.

outstanding. i wish you the best, then, and please be sure to share with us your trials, tribulations, and eventual successes, so we can all benefit.

---

### Post by Shpongle on 2009-12-14
try macpup , [http://macpup.org/](http://macpup.org/)

---

### Post by jeyaganesh on 2009-12-14
I have also installed Ubuntu 9.10 on an USB (4GB). I used it on a pc with 3 ghz, 512MB RAM and 64MB graphic. Compiz is working very well.

---

### Post by rokytnji on 2009-12-14
I run Puppy on Flash.> try macpupyep
I run AntiX on Flash.
I run Ubuntu on Flash.
As far as speed goes.
Fastest=Puppy
Next Fastest=AntiX
Ubuntu= Slight delay when opening tabs like tools or bookmarks in Firefox.

Running in flash is a little slower just because it is a flash drive. If you put swap on it you will just kill the drive sooner. All my persistent installs are EXT2 file systems with no swap. Have no use for running Compiz.

---

### Post by dragos240 on 2009-12-14
I do not suggest LFS. However, gentoo is very customizable. Almost as much as LFS. It comes with a few tools that make it easier to use. Like portage.

---

### Post by rasmus91 on 2009-12-15
> outstanding. i wish you the best, then, and please be sure to share with us your trials, tribulations, and eventual successes, so we can all benefit.

Well its not gonna be right ayaw, cus i don't have time for it atm, but I'm trying to get a chance to do it as a project in school, so i will have a month for it at school. And surely i will post a link for it here on the forum.

> I do not suggest LFS. However, gentoo is very customizable. Almost as much as LFS. It comes with a few tools that make it easier to use. Like portage.

Well... We'll see about it, as mentioned i don't have time now, so i'll decide in the future. I expect the first version within a year, but i don't know about it yet. Time will tell =)

> yep
I run AntiX on Flash.
I run Ubuntu on Flash.
As far as speed goes.
Fastest=Puppy
Next Fastest=AntiX
Ubuntu= Slight delay when opening tabs like tools or bookmarks in Firefox.

Pretty sure i'll try Puppy today... Perhaps Macpup...

---

### Post by rasmus91 on 2009-12-15
Hey again
What program should be used to install Macpup to USB, from windows?

---

### Post by earthpigg on 2009-12-15
> **rasmus91 said:**
> Hey again
What program should be used to install Macpup to USB, from windows?

have you looked at unetbootin?

---

### Post by Chilli Bob on 2009-12-15
> **rasmus91 said:**
> Hey again
What program should be used to install Macpup to USB, from windows?


 I've always just burned the CD, booted that, then use the built-in puppy universal installer to create the USB stick.

And another vote for Macpup, that's what I'm using on stick at the moment.

---

### Post by rokytnji on 2009-12-15
> Hey again
What program should be used to install Macpup to USB, from windows?

Sorry. Not a Windows User. But if I was to use a Pendrive installer for Windows for Puppy. Unetbootin is the way to go.

---

### Post by andrewabc on 2009-12-16
I wouldn't recommend installing ubuntu to usb because it messes with GRUB.

Do the 
system->admin->usb startup disk creator

You say it is slower than installed version. It depends on your hardware and the speed of your USB stick.

I didn't find much difference comparing hard drive install to usb version. Although I am using ocz rally2 which is fast usb device. I've also installed to slower kingston device and the speed difference is somewhat noticeable.

liveusb is much better than livecd when it comes to testing and checking out new ubuntu dev builds.

check out my review of ubuntu 9.04 installation to my usb sticks. I timed stuff.
[LiveUSB faster than liveCD and other liveusb questions](http://ubuntuforums.org/archive/index.php/t-1107298.html)

---

### Post by Guitar John on 2009-12-16
+1 Puppy 4.3.1 on a 4GB USB stick.

---

### Post by julianb on 2009-12-16
> 1. have/do you use Linux on a usb (which, how good is it, and so forth)

My favorite distribution now is the one that's over 100 times smaller than Ubuntu, and it runs great off a flash drive.

It's Tiny Core Linux.

[www.tinycorelinux.com]("http://www.tinycorelinux.com")

Try it - you'll like it. Be sure to read a little about how to use it though.

---

### Post by Pogeymanz on 2009-12-16
I use Puppy on my USB stick. It's amazingly fast and does very well on all kinds of hardware. If you are really carrying around your whole OS and working for extended periods on different computers, you should stick with Ubuntu. Otherwise, use Puppy.

As for LFS- don't do it. Try a more advanced distro like Arch or Gentoo before you dive into LFS. You can always strip down almost any distro for your USB stick.

---

### Post by pwnst*r on 2009-12-16
> **rasmus91 said:**
> Hi there.

Yesterday i installed Ubuntu on my new 8 GB USB stick. not live CD, but full. it runs a little slower than when installed on hard disk... well a lot slower, but it's still quite smooth.

I've installed the Mac4Lin, and i like the "Mac" feel. (don't think i prefer mac, that would be a wrong assumption.)

I have a problem with The Aqua theme though. it's not all loading bars which are good looking, some of them look like they're windows 95, if anyone can help me out with this, please do.

Anyway. I'm considering building my own Linux using "Linux from Scratch" a Linux designed to boot from USB, with the features i want.

So i'd like to hear your opinions on two things:

1. have/do you use Linux on a usb (which, how good is it, and so forth)

2. I'd also like to know if any of you have ever build you own Linux distro using "Linux from Scratch" and if you have any tips for me.

See ya'll later, Rasmus

REAL slow?  you sure you're not using USB 1.0?

---

### Post by Mighty_Joe on 2009-12-18
> **andrewabc said:**
> I wouldn't recommend installing ubuntu to usb because it messes with GRUB.


I installed GRUB to the USB drive with Ubuntu.  No messing.

---

