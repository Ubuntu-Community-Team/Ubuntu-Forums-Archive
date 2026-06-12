---
title: "What distro should I use for a RW live environment on my 8GB usb flash drive?"
date: 2010-03-15
forum: The Cafe
---

### Post by user1397 on 2010-03-15
I've been thinking about making my 8GB usb flash drive into a re-writeable live environment, so that I can keep files/add new ones if I wish.

Don't know which distros can do this, sure would like some advice!

---

### Post by Bachstelze on 2010-03-15
Any distro can be installed on an USB Flash drive. It's a drive like any other...

---

### Post by ssam on 2010-03-15
there is a great distro with an african sounding name. i can't remember what its called though. maybe someone knows?

---

### Post by user1397 on 2010-03-15
Umm I don't know what you guys are talking about, but i don't think you can just put a live cd iso on a usb stick and hope it somehow can save your data on it in the live environment...

i know i can install it on a usb stick and use it just like a regular install, but i want a live environment to be able to show people with the option of installing it while still being able to use it to store files.

does such a thing exist in the linux world? i had the impression that it did, but i guess i might have been dreadfully mistaken...

---

### Post by snowpine on 2010-03-15
> **ubuntuman001 said:**
> Umm I don't know what you guys are talking about

I'll give you another hint, the first and last letter are both U...

---

### Post by SilverDragon on 2010-03-15
I am not sure why people are being sarcastic towards your question but as you said you may be "dreadfully mistaken". If I understand your question correctly, you're looking for software similar to Portable Apps which saves all of your settings without affecting the host computer and I can not think of an OS that accomplishes the same thing.

---

### Post by Kenny_Strawn on 2010-03-15
In Karmic or Lucid, "System > Administration > USB Startup Disk Creator". From here, you can write either a disk image (if you booted from your first hard disk), or the content of the Live CD (if you booted from it). At the bottom of the applet, you will se a slider. This slider allows you to allocate space to use as rewritable. I move it to 1024 MB on my 4 GB USB Flash drive. Set it to what you want, and click "Make Startup Disk". When it is done, you will see a file named "casper-rw" on the drive. This is your space to permanently store data.

---

