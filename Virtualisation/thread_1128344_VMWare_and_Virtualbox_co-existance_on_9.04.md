---
title: "VMWare and Virtualbox co-existance on 9.04"
date: 2009-04-17
forum: Virtualisation
---

### Post by bond-o on 2009-04-17
Recently installed 64-bit 9.04 on new Dell.  I was previously running 32-bit 8.04 with VMWare and Virtualbox co-existing and had no issues (HP).  I run both because I demo products that only install on VMWare and like the flexibility of Virtualbox for my XP applications (i.e. Outlook, Visio, etc).

Installed both VMWare 2.0.1 and Virtualbox 2.2.0.  Both applications launch without issue and both launch Guest's individually.  However, if a Guest in VMWare is running and a Guest in VirtualBox is launched, the Guest in VMWare will power off.

In the reverse, a Guest in VirtualBox is running and a Guest in VMware is launched, the VMWare Guest will power up to 95% prior to stalling and terminating.  The error given is "Failed to initialize monitor device."

I reverted back to VMWare 1.6 and VirtualBox 2.1.4 for testing.  As soon as one Guest was running and the other application's Guest was launched, the entire system froze.

I continued with a combination of different versions of VMWare and VirtualBox until the system stopped freezing.

Would appreciate any assistance.

---

### Post by Shazaam on 2009-04-17
Check your memory allocation to each vm. If you have for example 1gig of physical memory installed on your pc and you allocate 512megs ram to each one you will run out quickly.

---

### Post by jdrodrig on 2009-04-18
Just curious,

if you export the machine used under VMware and import it back in VBox, what happens if you run that machine and the originally run under VBox both under VBox?

I guess that could help if it is the specifications of the VMs or the virtualization engines that are conflicting...

---

### Post by bond-o on 2009-04-19
Shazaam: my host has 4GB of RAM and both Guests combined for 1.2GB of RAM.

jdrodrig: I may try this in the future.

To update my progress, I started seeing strange behavior in VirtualBox (i.e. mouse disapearing and freezing, and shared folder copying folder structure, but no files from SFTP, etc.) when running in a production environment.  And yes, I did have the Guest Additions installed.

I installed 9.04 32-bit on my HP laptop with the server kernel headers.  I had the same results with VMware 2.0.1 and VirtualBox 2.2.0.  I then downgraded VMware to 1.0.7 and I was able to utilize both guests.  However, I did have one crash instance with VMware.  I plan on testing for a few more days.

As to my Dell, I installed 8.10 32-bit with the server kernel headers, VMware 1.0.7, and VirtualBox 2.0.2.  The only issue that I have seen is in the way the guests are launched.  As long as the VirtualBox guest is launched first, then there are no issues (so far).  However, if the VMWare guest is launched first, the VirtualBox guest will crash the VMWare guest.

As much as I wish to move to the 9.04 environment, I believe I need to stay in the 8.x world for now.

Again, any input is appreciated.

---

### Post by vbundi on 2009-09-17
Sorry to post on an old topic...

This happened to me today, after searching it looks like it may have to do with some sort of conflict between the modules used for each virtualization tool.

[http://ubuntuforums.org/showthread.php?t=616358](http://ubuntuforums.org/showthread.php?t=616358)

---

