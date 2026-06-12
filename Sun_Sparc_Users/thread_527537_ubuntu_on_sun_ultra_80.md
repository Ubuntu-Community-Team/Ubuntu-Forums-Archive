---
title: "ubuntu on sun ultra 80?"
date: 2007-08-16
forum: Sun Sparc Users
---

### Post by afinley on 2007-08-16
Hi I just was given a sun ultra 80 expert 3D. I know nothing about sun other than I want linux on it. I see there is sparc install disc, but does ubuntu (linux in general) really run well on these machines? Or will I be hacking away several days? Thanks!!!

---

### Post by bodycoach2 on 2007-08-18
I have that machine too. I had tried the free Solaris 10 on it, but it was too slow. I installed the Ubuntu Server SunSpark edition, and it went on with no problems. After it was on, I did: sudo apt-get install xubuntu-desktop. It installed well too. Xubuntu runs very well on that machine.

It's a REALLY heavy machine for it's size too, huh?

---

### Post by afinley on 2007-08-18
Hey bodycoach2, 
Thanks for the reply. They are heavy machines :-)  The server install went just dandy, but couldn't figure out which video card to choose when installing the ubuntu-desktop. Do you recall what video card you chose when installing X? I can't figure it out.
Thanks again!

---

### Post by hartz on 2007-08-20
Hi afinley.

Did you get the information you needed on the Ultra-80 Graphics?  Many of these machines have ATI workstation cards.  If you can give me the Sun Model number I can tell you what card it it.

Some of the common card models used in the Ultra-80 workstations are:
540-3902 - Elite3D-m6
501-5484 - Elite3D-m3
540-5476 - XVR100 (FFB3) Graphics
540-4313 - Elite3D-m6 series 2
370-4362 - PGX64 8/24-Bit Color Frame Buffer

You can search for the model nr on the web or I can give you some info on it if you post here.

---

### Post by afinley on 2007-08-20
Thank for your help Hartz,
Where is the model number? I see a PN and SN number on the back of the machine but that's it.

---

### Post by hartz on 2007-08-21
The PN (Part Number).

There may be more than one.

These look like 370-1234-04

The final -xx is the revision.

---

### Post by toupeiro on 2007-11-14
I just tried installing ubuntu server 7.10 on an Ultra 80, but my system config is a bit non-standard.  I have 7 SCSI hard disks attached to this system via 2 controllers, and a version of Solaris 5.6 on the first disk of the first SCSI controller.

I issued a boot cdrom and was able to install ubuntu on one of the open disks, but Linux naturally see's this disk differently than openboot sees the hardware.  I did a probe-scsi-all and I can see all the disks, but Linux sees the disk as /dev/sdc on SCSI@2 0,1,0  

How does this translate to Openboot on a Sparc box, and is there a specific minimum version of openboot I should be at before attempting to boot linux on this machine?  I could just set the boot-device to the drive with linux installed on it (do I have to specify the partition?) if I knew how to translate what ubuntu reports into an address available in openboot.  I can't blow away the 5.6 partition, as it has some important data on it that I can't migrate just yet.

---

