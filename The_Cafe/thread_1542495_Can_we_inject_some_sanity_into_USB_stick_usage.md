---
title: "Can we inject some sanity into USB stick usage?"
date: 2010-07-30
forum: The Cafe
---

### Post by rondackcpu on 2010-07-30
Can we do something to introduce some sanity into the USB stick world in Linux?

Specifically, when using a USB stick as a replacement for a recordable CD or DVD in (name-your-distribution).iso testing, the stick gets "trapped" in some condition which Ubuntu doesn't like to deal with.  "Mkfs" (in all its variations) refuses to erase or reformat the stick.  "Gparted" refuses to reformat the stick or delete the offending partitions.  Unetbootin and "Startup Disk Creator" are anxious about the presence of contents on the stick and refuse to run again to create a new instance.  Nautilus pretends there is no Trash folder to move the files to and no Delete option available.

Perhaps, the worst offenders are the distributions which ask you to put their iso on the stick by some "sudo dd if=XXX.iso of=/dev/sdYN" command, but Unetbootin and "Startup Disk Creator" can trap the stick, too.  So you end up playing around with "mkfs" and/or "Gparted" until one of them accidentally breaks the trap.  Oops.  Is there a race going on in there somewhere with a different winner occasionally?

Windows doesn't seem to care.  Just plug the stick in and click format.  Shazam.  The problem there is that I don't have a machine running Windows these days.

A second issue is the unpredictable action of "Startup Disk Creator."  Sometimes it will allow you to put a persistence file on the stick, but other times the option is grayed out and unavailable.  When you do get the persistence file, sometimes when booting a second or subsequent time, there is a complaint flashed by on boot-up saying some essential file is "mounted as read-only".  So much for continuing persistence.

Thank you for reading my "rant".  Please accept that is offered not as just a bunch of derogatory complaints, but as suggestions for improvements in Linux and Ubuntu that I don't know how to implement myself.

CRS

---

### Post by Elfy on 2010-07-30
Not support request moved to cafe

---

### Post by Paqman on 2010-07-30
> **rondackcpu said:**
> 
Windows doesn't seem to care.  Just plug the stick in and click format.  Shazam. 

Gnome does likewise. I had a b0rked stick that wouldn't format in Gparted just the other day, right click > format, job done.

---

### Post by red_Marvin on 2010-07-30
> **rondackcpu said:**
> Perhaps, the worst offenders are the distributions which ask you to put their iso on the stick by some "sudo dd if=XXX.iso of=/dev/sdYN" command

I've never had dd fail to write an usb image, so I don't see what is so bad about this, except that it is a console command -whose [infer|super]iority is *a matter of taste*.

It might be that the partition table of the drive has been borked/is not valid, then you might want to use _fdisk_ to create a new blank one.

---

### Post by Plumtreed on 2010-07-31
I usually make a point of formating, in Virtualbox Windows, any USB before using it. Saves a lot of effort and heartache!

---

### Post by Paqman on 2010-07-31
> **red_Marvin said:**
> I've never had dd fail to write an usb image, so I don't see what is so bad about this, except that it is a console command -whose [infer|super]iority is *a matter of taste*.


I don't think it is. dd is an extremely powerful app, and can cause serious carnage in the case of a typo or minor brainfart. It requires much more caution than the alternatives.

---

### Post by chris200x9 on 2010-07-31
protip: use fdisk to delete the partition(s) on the stick  then recreate it(them) and format it.

---

### Post by Legendary_Bibo on 2010-07-31
I tried creating a live USB, but I couldn't get it to work for any OS like Puppy or Lubuntu. So I just stick to CDs. It's so much less of a hassle.

---

### Post by red_Marvin on 2010-07-31
> **Paqman said:**
> I don't think it is. dd is an extremely powerful app, and can cause serious carnage in the case of a typo or minor brainfart. It requires much more caution than the alternatives.
You need superuser rights to write to anything in /dev, that alone should have you triple check your commands if you are afraid of borkage.

---

