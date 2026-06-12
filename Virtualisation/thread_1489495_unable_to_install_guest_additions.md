---
title: "unable to install guest additions"
date: 2010-05-21
forum: Virtualisation
---

### Post by klemencic on 2010-05-21
I am running a Ubuntu host and have installed a a Xubuntu as a guest in VB
I had no problems in loading the system but I am unable to access the DVD or install the guest additions
I click on Devices>Install Guest Additions and nothing happens
I click on Devices CD/DVD Devices>VboxGuestAdditions.iso and receive and error 'Unable to mount /usr/share/virtualbox/VBoxGuestadditions.iso'
If I click on unmount I receive 'Unable to unmount the CD/DVD Host Drive IOMEGA DVDRW8440E2D-B (sr0) from the machine Xubuntu. Would you like to force unmounting of this medium?

I believe the problem could have something to do with the DVD as being device sr0
I also have Windows installed as a VB guest with no problems
Any help appreciated

---

### Post by Objekt on 2010-06-30
I have had a similar problem for the last few versions of the Guest Additions.  While my Virtualbox PUEL install is current (3.2.6), I can't get the latest Guest Additions installed.  For now, I am stuck with Windows Guest Additions 3.2.0r61806.

As in your case, nothing happens when I try the standard method.  My first DVD/CD-RW drive opens, for some reason, but I get no Guest Additions update, and nothing further happens.

I got the last version of the Windows Guest Additions (3.2.0r61806) installed by downloading the CD image (*.iso file) from a webpage, mounting it in a virtual CD-ROM drive, then installing in the Windows XP guest.  However, I can't remember where/how I downloaded that image, and I can't find any place to download the new one.  It seems that Oracle is "sure" there is no way for the "Install Guest Additions..." menu item cannot fail, so they have not provided any way to get the image directly.  How irritating.

This has been broken at least since Virtualbox 3.2.0.  It's high time it were fixed.

Again, I am running the Personal Use and Evaluation License (PUEL) version of Virtualbox, not the OSE version.  Not sure if it matters, but there you are.

Also note I am using regular Ubuntu, not Xubuntu, but that shouldn't matter either.

---

### Post by howefield on 2010-06-30
Have you tried following the steps in the Virtualbox manual (downloadable from virtualbox.org)., ?


> 1. Before installing the Guest Additions, you will have to prepare your guest system
for building external kernel modules. This works similarly as described in chap-
ter 2.3.2, The VirtualBox kernel module, page 36, except that this step must now
be performed in your Linux guest instead of on a Linux host system, as described
there.
Again, as with Linux hosts, we recommend using DKMS for Linux guests as well.
If it is not installed, use this command for Ubuntu/Debian systems:
sudo apt-get install dkms
or for Fedora systems:
yum install dkms
Make sure to nstall DKMS before installing the Linux Guest Additions.
2. Mount the VBoxGuestAdditions.iso file as your Linux guest’s virtual CD-ROM
drive, exactly the same way as described for a Windows guest in chapter 4.2.1.1,
Installation, page 65.
3. Change to the directory where your CD-ROM drive is mounted and execute as
root:
sh ./VBoxLinuxAdditions-x86.run
In a 64-bit Linux guest, use VBoxLinuxAdditions-amd64.run instead.

---

### Post by Objekt on 2010-06-30
None of that is applicable.  As I stated above, I am running a Windows XP guest, not any version of Linux.  Must be time to start a new thread.

---

### Post by howefield on 2010-06-30
> **Objekt said:**
> None of that is applicable.

Of course it is, the OP to whom I am responding has a Linux guest. I missed the fact that you had resurrected a dead(ish) thread.


:lolflag::lolflag:

Incidentally, it is a triviality to find the iso that you are looking for.

---

### Post by Objekt on 2010-06-30
I finally found the page to download CD images directly.  I'm going to post it here and bookmark it so this never happens again!

[http://download.virtualbox.org/virtualbox/]("http://download.virtualbox.org/virtualbox/")

---

