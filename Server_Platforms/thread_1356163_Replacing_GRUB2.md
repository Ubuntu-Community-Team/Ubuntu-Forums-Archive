---
title: "Replacing GRUB2"
date: 2009-12-15
forum: Server Platforms
---

### Post by david-emm on 2009-12-15
Recently I downloaded the 64 bit UBUNTU 9.10 server edition. Unfortunately it wont install on my RAID1 AMD system. The installation fails when trying to install GRUB2. Some of the GRUB2 files are installed but there is no change to the MBR. This happens even when both disks have been erased and makes no difference if LVM is used or not.

I have reinstalled 64 bit UBUNTU 8.04LTS server edition without any problems and could carry one with this. However I would like to upgrade to 9.10.

Does anyone know how to change the iso file (or the install CD if I write the iso to a RW disk) so that I can use GRUB and not use GRUB2. I assume that the install script will need to change as well as replacing he GRUB2 files.

Thanks

---

### Post by craigp84 on 2009-12-16
I think there's a faster approach than re-mastering the install CD for 9.10 -- unless you're going to be using the install CD to install a bunch of boxes. Assuming this is only for installing one host:

Install as normal, but before the reboot into the system (i guess the installer might even terminate with grub2 install errors before it gets to the "reboot into your new system" stage) wget (or otherwise download) the grub .deb from whatever release you want ([http://packages.ubuntu.com/hardy/grub-pc](http://packages.ubuntu.com/hardy/grub-pc)) then try "dpkg -i that-grub-you-downloaded.deb".

You might have to force installation or otherwise override some checks, but it seems like the dependencies would allow this to install anyway.

Never tried this though so i can't guarantee it'll definately work. After install you'll need to tidy up dependencys for APT (otherwise it will forever more try to replace your grub with 9.10's grub).

If you get that far, give me a shout and we can sort that out.

---

### Post by david-emm on 2009-12-16
Thanks for your help. Yes the server installation crashes during installation when trying to install GRUB2. As the server edition does not include a live CD startup I've used a 9.10 desktop edition to see what is on the HDDs. Some GRUB2 files are written into /etc /grub.d and /etc/default/grub but theres nothing in /boot/grub. There's a program ISO Master in the UBUNTU Software Centre which allows one to view and change an iso image.  Interestingly both grub and grub2 are in the iso image as is grub-install which probably points to grub2. I tried to install grub using grub-install from the archives but I guess it was the wrong version. Anyway the attempt failed. So I think I'll try replacing grub-install in the iso with the version in 9.04 and see if that works. I'll let you know.

---

### Post by craigp84 on 2009-12-16
> As the server edition does not include a live CD startup

I've not installed 9.10 or even 9.04, but the things people keep saying, it sounds like Ubuntu server edition has gone off the rails!!!

---

### Post by Krupski on 2009-12-16
> **craigp84 said:**
> I've not installed 9.10 or even 9.04, but the things people keep saying, it sounds like Ubuntu server edition has gone off the rails!!!

9.10 is just fine. The biggest "speed bump" is the new Grub. The way it's configured is TOTALLY different than the old Grub.

Initially, it's a pain in the behind to search for the info and figure out how to reconfigure Grub to your liking, but learning how is worth it.

The new Grub addresses a lot of old problems (such as the size of the boot drive and the location of the boot files).

When I first upgraded to 9.10, I was disappointed to find that some things were changed and/or moved around.

But all in all, it's an improvement and the changes are worth learning and getting used to.

My humble opinion....


-- Roger

---

### Post by david-emm on 2009-12-17
> **david-emm said:**
> So I think I'll try replacing grub-install in the iso with the version in 9.04 and see if that works. I'll let you know.     

Well it didn't. I replaced grub-install with the version from the 64 bit Ubuntu server 8.04 LTS version and changed the MD5.txt file to reflect the correct MD5 and file name. However although the disk checked out OK before installation later in the installation phase it fails due to disk error. My guess is that an install script identifies the grub-install version and sees a mis-match. I'll hunt further but right now I'm staying with 8.04 as it works fine - no problem in getting grub to see my RAID1 setup. Luckily I'm not running a commercial server so the inability to get grub2 to see and use my RAID1 setup, even though all the other programs appear to have loaded OK, isn't a major stopper. (Why am I running a server? - I have a home network and just like playing around with the beasts.)

---

### Post by craigp84 on 2009-12-18
I guess it kinda sucks that the 9.10 upgrade hasn't been plain sailing.

If there's a silver lining it is the pain people are experiencing now with 9.10 will contribute to ensure the next LTS is much smoother.

So from folks like me (and companies i support), i guess we owe you guys a thank you for continuing to contribute to the comunity by exploring and trialing the new technologies and working out the bugs.

So while it can be a pain to hit these issues, it's worth highlighting that your service is valuable & appreciated!

Keep at it :-)

---

