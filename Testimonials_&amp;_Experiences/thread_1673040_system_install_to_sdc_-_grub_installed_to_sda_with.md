---
title: "system install to sdc - grub installed to sda without prompting"
date: 2011-01-21
forum: Testimonials &amp; Experiences
---

### Post by cphuntington97 on 2011-01-21
I believe the installer has overstepped its bounds.

I selected "use entire disk" and installed (Lubuntu, actually, but I think everything is just set from upstream?) to sdc. With no prompts or warnings, the boot sector on sda was overwritten.

This is unusual and unexpected behavior. Every other distro has specifically asked where to install the bootloader, if anywhere.

Correct me if it was my error, but if a user selects a specific disk, the bootloader should not automatically install to a different disk without explicit permission.

I'm ok and I know how to fix this, but many users could be in for quite a surprise and could be turned off. The installer's behavior should be changed.

---

### Post by MartyBuntu on 2011-01-21
You can choose where to install the bootloader during installation.

It's hidden unless you select the ADVANCED feature.

---

### Post by 3rdalbum on 2011-01-22
I'd probably agree - it should default to the hard disk that you're installing Ubuntu to, with the option of changing it. Still, there IS the option to change it already for advanced users.

---

### Post by cphuntington97 on 2011-01-23
I am aware of the advanced option to control where the bootloader is installed.

However I believe - and you may consider this strong language - that to write anything to a partition other than the one the user has selected, without explicit warning or even so much as a notification, is borderline criminal.

The user's data should **always** be considered sacred, and this includes the boot sector.

---

### Post by MartyBuntu on 2011-01-23
> **cphuntington97 said:**
> 
However I believe - and you may consider this strong language - that to write anything to a partition other than the one the user has selected, without explicit warning or even so much as a notification, is borderline criminal.

You have every opportunity to configure the bootloader during installation.

1. There is no shortage of documentation detailing this procedure.

2. It is sensible to install the bootloader to the first "physical" disk. It isn't the duty of any *nix distro to "play nice" with Windows operating systems. At least linux distros accommodate Windows installs, which is more than I can say about Microsoft's position.

3. I would assume anyone doing a major procedure like setting up a multi-boot would have done a full system back-up in advance. If there's something about the install you don't fancy, you can always roll back.

---

### Post by Juan Largo on 2011-01-24
@ cphuntington97

I agree with you 100%.  I raised a similar argument back in 2006.  The option to choose which disk or partition GRUB is installed on should not be part of any "advanced" feature.  It should be built into the standard installer IMO.  

BTW, you can argue this point until you are blue in the face.  Ubuntu will not change it, and you'll get very little agreement in this forum.  If I were you, I'd just drop it and accept it as it is, because it won't change.

---

### Post by MartyBuntu on 2011-01-24
> **Juan Largo said:**
> @ cphuntington97

I agree with you 100%.  I raised a similar argument back in 2006.  The option to choose which disk or partition GRUB is installed on should not be part of any "advanced" feature.  It should be built into the standard installer IMO.  

BTW, you can argue this point until you are blue in the face.  Ubuntu will not change it, and you'll get very little agreement in this forum.  If I were you, I'd just drop it and accept it as it is, because it won't change.


Having multiple bootloaders across multiple drives and partitions is neither sensible, nor practical.

At least you *have the option* with Ubuntu, unlike Windows.
Everything is right there in the documentation.

---

### Post by cphuntington97 on 2011-01-24
Thank you Juan Largo for your voice of support.

I've been using gnu/linux for 15 years and I've never seen an installer behave like this. But I'm not spending my time making a point for me - I'm very comfortable with bootloaders. I'm spending my time because I think Ubuntu especially needs to look out for less knowledgeable users.

Here is what happened to me:

I have a netbook with a built in ssd and an sd card slot. I installed Lubuntu to the sd card. Without so much as a prompt or warning, the installer overwrote the boot partition on the ssd. This is not typical behavior for a linux system installer. 

Now, if I remove the sd card, I boot to a "grub rescue>" prompt and no use-able system. This is neither sensible, nor practical.

Of course, I was able to restore the boot sector on the ssd, but I fear a typical friend or family member would not have been able to recover so easily.

I hope some day this thread can be marked [solved] when developers come to their senses. But I do thank everyone who works on debian, ubuntu, lubuntu, gnu programs, the kernel, and the users who file bug reports and help others. We have created a remarkable piece of engineering. I'm speaking up on this issue because it is my way of contributing.

---

### Post by cariboo on 2011-01-25
This point was brought and bugged during the last testing cycle, it was felt by the desktop experience team that new users shouldn't have to choose where to install grub, so using automatic partitioning also automatically installs grub to /dev/sda.

It was also stated that experienced users don't use automatic partitioning, so the chance to choose where grub is installed is active using the manual partitioning option.

The above changes were made when ubiquity was rewritten for Maverick.

---

### Post by mastablasta on 2011-01-26
so in a way ubuntu is now behaving like Windows (i am not sure how this would be a strange thing to users coming to Linux from windows). but Ubuntu also offers advanced options where it behaves like Linux (or another OS).
 
the only shock i had was that linux overwrote the system restore parittion and automaticly partitioned the whole drive (not only "C drive"). meh, at least that notebook has some use now...

---

### Post by MarcusW on 2011-01-27
I agree that GRUB should only automatically be installed on the disk you installed the OS on. (even if I do know enough to do an "expert" install, there's no indication during the install that I *have* to do that to keep my GRUB on sda intact right?)

A simple "Do you want to install GRUB on sda aswell? (if you don't know, choose yes)" would have been nice IMO.

---

### Post by Elfy on 2011-01-28
I understand the issue - but posting in a forum that's unlikely to be visited by any dev involved isn't going to help.

Post a bug or add to an existing one.

Thanks for participating.

---

