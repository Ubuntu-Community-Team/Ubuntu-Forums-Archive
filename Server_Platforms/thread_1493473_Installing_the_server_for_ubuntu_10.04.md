---
title: "Installing the server for ubuntu 10.04"
date: 2010-05-25
forum: Server Platforms
---

### Post by kc0hwa on 2010-05-25
Hi I trying to install ubuntu server 10.04 and I can not get throw the install cd with out geting debootstrap warning
warning file:///cdrom/pool/main/x/xfonts0terminus/console-terminus)4.30-2_all.deb was corrupt

I have down load the cd for 32 10time
I will get this evertime
I order the server cd and it is only for 32

---

### Post by exodus_ on 2010-05-25
hey there.

There are a couple of things that you can try to make sure that your downloaded CD will work for you!

Checking the MD5SUM of the .iso file *before* you burn it is very important.  It will make sure that the file you downloaded is exactly the same as the one on the server.

[Check out this page]("https://help.ubuntu.com/community/HowToMD5SUM") It will show you how to check the integrity of your downloaded .iso file.

Also, you could try burning the image at the slowest possible speed for your CD burner.  This can often ensure the CD is created properly.  It may take a lot longer to burn, but if it results in a CD that will boot properly and install properly than the time is worth it.

If you just cant get the CD to burn properly then you could also check out [the installation page]("https://help.ubuntu.com/community/Installation") in the community wiki.  there are many install options listed on this page and maybe you will have better luck with one of those options.

I hope I have been of some help for you and good luck! Ubuntu server is a fine release :D

---

### Post by tgalati4 on 2010-05-25
Also run the "Check CD" option when the installer boots.  It checks every file on the CD and compares it to the checksum stored in the integrity file.  This helps to avoid a botched installation because you can't read a file.

---

### Post by kc0hwa on 2010-05-25
15342636441181f7a19c65984b44e24c  ubuntu-10.04-server-i386.iso

---

### Post by exodus_ on 2010-05-25
It looks like the .iso file downloaded just fine because the md5sum result matches.

Try burning it at 1X speed and as suggested by tgalati4 run the "check CD" option in the boot menu.  If that check also works then you should be able to install it properly.

If you are STILL having issues with it, maybe you have a dirty or even faulty CD-RW drive and it needs to maybe be cleaned.

You could also try some of the options for installing without a CD drive (as I often do when I don't have a spare disc)  I have installed for many people using nothing more than a USB flash drive made for this purpose.

Hope you can get it up and running!

---

### Post by kc0hwa on 2010-05-25
Im buring at x1 and I have used 3 diffrent drive]
dl 2 year old
cd 1 year old
blue 6mounth old

k3b
on mandriva 2010

I clean then weekly

---

### Post by kc0hwa on 2010-05-25
I burt it at x1 on all 3 drive
all of the cd on the self chech ffailed I will try to get another cd drive
that is the only that I can think of
I did try this on two other mations

---

### Post by exodus_ on 2010-05-26
Have you considered that you might actually have faulty DISCS?  Try using a different brand, or as I suggested earlier maybe try to install WITHOUT using a CD?

---

### Post by CharlesA on 2010-05-26
Try a different burning program.

---

### Post by kc0hwa on 2010-05-26
I chech the disk at work the the disk are check out on disk chech OK

I will ne4ed to get a diffrent drive for the two computer

---

### Post by ./daniel on 2010-05-30
The thread is labelled solved but how was it solved?

I think I have the same problem with the 32bit Ubuntu server install CD.

# Check sum for downloaded iso matches
# Integrity check of CD fails at "./pool/main/c/coreutils_7.4-2ubuntu2_i386.deb" 
# Install fails at "installing base system"

Is anyone else having this issue?

---

### Post by CharlesA on 2010-05-30
Try a different cd/dvd drive, or just "burn" the ISO to USB and do it that way to see if it makes any difference.

---

### Post by ./daniel on 2010-05-30
I found the problem. One of the 2 x memory DIMM's was faulty.

Memory test on the CD picked it up. 
I have removed the faulty Memory DIMM, Integrity test passed & i have completed an install without any errors!!

This explains why debian kept crashing on this computer... oh well i have already installed over debian, lets give ubuntu server a try!

---

### Post by CharlesA on 2010-05-30
D'oh! Glad you found the problem. :)

---

