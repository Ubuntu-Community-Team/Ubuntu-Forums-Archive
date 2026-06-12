---
title: "Is There Anyone That Is Successfully Using Ubunto On A Dell PowerEdge 2300?"
date: 2006-10-24
forum: Server Platforms
---

### Post by ebozzz on 2006-10-24
Well? I would REALLY like to communicate with anbody who is. I need to know what steps you took to get it installed. Thanks.

---

### Post by Anapologetos on 2006-10-24
Ive got Ubuntu Server 6.06 installed on a Virtual Machine on our Poweredge 2650?
Anapologetos

---

### Post by ebozzz on 2006-10-24
> **Anapologetos said:**
> Ive got Ubuntu Server 6.06 installed on a Virtual Machine on our Poweredge 2650?
Anapologetos

Thanks for the reply! Is you RAID PERC 2, Perc 3 or other? How did the install go? Did you experience any unresponsiveness duirng any of the install steps that prevent you from completion? If so what was your work around? Again, thanks!

---

### Post by Anapologetos on 2006-10-24
Perc 3, and like I said, using a virutal machine, and MS Server 2003 as the host OS--When I installed ubuntu to the VM, I had no problems--but that is one of the major points of VM:--Hardware Indepedancy--Hope this helps.
Anapologetos

---

### Post by ebozzz on 2006-10-24
> **Anapologetos said:**
> Perc 3, and like I said, using a virutal machine, and MS Server 2003 as the host OS--When I installed ubuntu to the VM, I had no problems--but that is one of the major points of VM:--Hardware Indepedancy--Hope this helps.
Anapologetos

:( I was hoping to have a solution. Thanks for sharing anyway. The search continues!

---

### Post by peanut butter on 2006-10-24
i DONT own a dell but i can give you some helpful ubuntu info.
I find raid tobe a hassel. You might use LVM groups during Setup with the Alternate install CD. If you are trying to set up mirror disks please disregard.

---

### Post by ebozzz on 2006-10-24
> **peanut butter said:**
> i DONT own a dell but i can give you some helpful ubuntu info.
I find raid tobe a hassel. You might use LVM groups during Setup with the Alternate install CD. If you are trying to set up mirror disks please disregard.

I'm all ears! Can you elaborate please? I am new to Linux and Ubuntu. I'm also not the most computer savy person but I am learing. 

Raid is also new to me and I like the idea of the redundancy but if I can't get it to work on this box with a Linux OS it means nothing to me. If you don't mind sharing, I am willing consider any options. Thanks.

---

### Post by peanut butter on 2006-10-24
ok. i dont know anything about redundency. What i was trying to say is, if you want to use RAID0 for disk spanning (using multiple disks to act as one) you can use LVM Groups. Lvm groups are set up at installation of ubuntu with the alternate install CD. This will allow you to use 2 250GB drives as 1 500GB drive. I have never used RAID, because of lack of time, but have heard it is hard to set up. I am in no way a person who knows a lot about this.

---

### Post by ebozzz on 2006-10-25
> **peanut butter said:**
> ok. i dont know anything about redundency. What i was trying to say is, if you want to use RAID0 for disk spanning (using multiple disks to act as one) you can use LVM Groups. Lvm groups are set up at installation of ubuntu with the alternate install CD. This will allow you to use 2 250GB drives as 1 500GB drive. I have never used RAID, because of lack of time, but have heard it is hard to set up. I am in no way a person who knows a lot about this.

Redundancy is just a fancy way of referring to the ability to back up info IMO with the primary data being mirrored on additional drives in RAID. You probably already know this but RAID is also supposed to provide faster data access. 

My RAID is already configured but for some reason is not being recognized during the install process with Ubuntu. I get to the step where the partitioner scans the drives and from that point on nothing happens. The system doesn't freeze or become unresponsive. It just doesn't progress past that stage. I eventually have to cancel/quit the process. I need to find more information on LVM Groups. Thanks!

---

### Post by ebozzz on 2006-10-25
> **peanut butter said:**
> Lvm groups are set up at installation of ubuntu with the alternate install CD.

Let me get some clarification here. Do you mean that when installing Ubuntu from an Ubuntu disc, NOT a burned disc, it will give me the option to set up LVM Groups? Is that the correct interpretation? I probably should have asked this im my last post.

---

### Post by dimeotane on 2007-03-08
Very soon I'm going to be playing with a our Poweredge 2300 donated to our department.  I plan on using some form of ubuntu on it, if I can get it to work.  Hopefully you've had some luck installing on this machine since October?

---

### Post by rennen01 on 2007-03-08
This may help you.

[http://ubuntuforums.org/showthread.php?p=259437](http://ubuntuforums.org/showthread.php?p=259437)

---

### Post by ebozzz on 2007-03-09
> **dimeotane said:**
> Very soon I'm going to be playing with a our Poweredge 2300 donated to our department.  I plan on using some form of ubuntu on it, if I can get it to work.  Hopefully you've had some luck installing on this machine since October?

I was never able to get Ubuntu installed on my 2300s. It is my understanding that the Perc 2 & Perc 3 support was dropped all releases with the 2.4 kernel or above. After doing some research and discussing it a few mentors, I decided to go with FreeBSD. The Perc architecture is supported in that OS. Good luck!

---

### Post by Tye on 2007-05-17
I got ubuntu 7.04 installed on my Poweredge 2300/500 

I had a few probs with the scsi controller card
but i just used the onboard one instead

i dont use raid though

---

### Post by ebozzz on 2007-05-18
> **Tye said:**
> I got ubuntu 7.04 installed on my Poweredge 2300/500 

I had a few probs with the scsi controller card
but i just used the onboard one instead

i dont use raid though

Would you mind documenting your steps, *please*? :)

---

### Post by Tye on 2007-07-10
ubuntu server 6.04 installed fine using the onboard scsi controller but not with the pci controller card, so i just used it with the onboard controller



but recently i have reinstalled ubuntu 7.04 ( not server version )
and tried it WITH the pci controller card and it works fine as long as i turn off the onboard controller in the BIOS

since its only a P III 500 i had to install xubuntu-desktop aswell

but everything is good here


once again I am not using RAID

---

### Post by bwells on 2007-08-22
I was successful in installing Kubuntu 7.04 on a Dell PowerEdge 2300 but it wasn't easy.  I have a Perc 3.10 controller installed in mine with 3 73gb hd.  A SCSI cdrom attached to the secondary Adaptec SCSI controller that is on the motherboard.  Nothing is attached to the primary SCSI controller.  Here is the steps I took.

1.  Disable the Primary SCSI controller in the BIOS - For some reason if this is enabled during the boot of the CD, you will receive and error.
2.  Allow Ubuntu, or Kubuntu in my install, to load.
3.  Click Install Button
4.  Follow on screen guide and select default settings until you reach the Hard Drive configuration.  Here do not allow Ubuntu to auto partition your drive even if you are going todo it the same way.  In my installation, I have a /swap and /, that is it.  
5.  Allow Ubuntu to install with above hard drive settings
6.  After installation is complete, reboot
7.  Before system can load anything, enter the BIOS again, this time enable the Primary SCSI controller and disable the Secondary.  I know this will disable the CDROM, but for some reason Ubuntu will boot up only when the Primary is enabled and the Secondary is disabled.
8.  Boot Ubuntu and enjoy.

This is how I installed my system and it works fine.  I know that I am missing a CD drive, but that is what apt-get is for, lol.  Hope this helps!

Brent

---

### Post by ifconfig on 2007-09-07
> **bwells said:**
> I was successful in installing Kubuntu 7.04 on a Dell PowerEdge 2300 but it wasn't easy.  I have a Perc 3.10 controller installed in mine with 3 73gb hd.  A SCSI cdrom attached to the secondary Adaptec SCSI controller that is on the motherboard.  Nothing is attached to the primary SCSI controller.  Here is the steps I took.

1.  Disable the Primary SCSI controller in the BIOS - For some reason if this is enabled during the boot of the CD, you will receive and error.
2.  Allow Ubuntu, or Kubuntu in my install, to load.
3.  Click Install Button
4.  Follow on screen guide and select default settings until you reach the Hard Drive configuration.  Here do not allow Ubuntu to auto partition your drive even if you are going todo it the same way.  In my installation, I have a /swap and /, that is it.  
5.  Allow Ubuntu to install with above hard drive settings
6.  After installation is complete, reboot
7.  Before system can load anything, enter the BIOS again, this time enable the Primary SCSI controller and disable the Secondary.  I know this will disable the CDROM, but for some reason Ubuntu will boot up only when the Primary is enabled and the Secondary is disabled.
8.  Boot Ubuntu and enjoy.

This is how I installed my system and it works fine.  I know that I am missing a CD drive, but that is what apt-get is for, lol.  Hope this helps!

Brent

This didn't work for me, didn't want to format. I'm trying again but formating the disks from the scsi bios first. So hopefully. :)

But there must be some kind of solution for this when the system is installed. I've got my backup on the same scsi as the cdrom.

Magnus

---

### Post by phantasm on 2007-09-07
I am running Ubuntu 7.04 on my 2300 with a PERC 3 DC card. The problem i encountered was that for some reason they dropped support for the card. So what needed to be done was ot boot into the controller setup and change its mode from IO2 to Mass Storage. This works. However i have my own problems with any Linux distro and this system right now. See here: [http://ubuntuforums.org/showthread.php?t=545237]("http://ubuntuforums.org/showthread.php?t=545237")

---

### Post by ifconfig on 2007-09-21
> **ifconfig said:**
> This didn't work for me, didn't want to format. I'm trying again but formating the disks from the scsi bios first. So hopefully. :)

But there must be some kind of solution for this when the system is installed. I've got my backup on the same scsi as the cdrom.

Magnus

I didn't change the bios settings after the installation and it runs perfectly. With working cdrom and tapedrive. =)

---

### Post by earcaraxe on 2008-02-10
Sorry for resurrecting an old dead thread, but how were you able to install? I can't seem to get my poweredge 2300 to boot from CDROM.

---

### Post by Kadin2048 on 2008-06-02
This thread seems to have been going on for a while, but I just thought I'd chime in to say that I successfully installed 6.06 LTS on a PowerEdge 2300 a few months ago, and it's been ticking along nicely ever since.

I have it set up with the factory RAID card (called a "PERC 2/SC") with a bunch of 74GB SCSI drives in RAID-5 as one logical volume, and then managing that logical volume with LVM to produce various partitions to my liking.  Anyway, my first real attempt at a RAIDed system, and seems to be pretty nice.

I had a few odd things during the install ... the '2300 seems to be picky about *keyboards*, of all things.  No joke, but it just would not go into any of the BIOS or RAID configuration screens when I had one keyboard attached; it just didn't seem to recognize the Ctrl-M combination.  Switching to a Dell-branded keyboard from about the same vintage as the '2300 did the trick.  (The offending keyboard was a trusty old IBM Model M.)  I thought that was pretty weird.

Other than that, nothing really different.  All the hardware seemed to be recognized automatically in the latest release of 6.06, including the PERC 2/SC.  (I can monitor the status of it by looking at some files in /proc/megaraid, which is nice.)

Anyway, sorry I can't give any insight into the issues folks were having with the machine refusing to boot from the install media...mine didn't have an issue there.  That sounds like a BIOS or SCSI-related problem; because of the two onboard SCSI channels plus the SCSI RAID PCI card, there are a lot of boot menus for configuring everything ... lots of opportunities for misconfiguration that I suspect could be the issue there.

EDIT:  Just a few more pieces of info that others might find useful.  First, my machine did not have a tape-drive installed, and there was nothing connected to the internal Wide-SCSI bus.  The internal Narrow-SCSI had just the CD-Rom attached.  I didn't need to do anything funny in the BIOS about disabling the internal adapter or anything to get the install to work.  However, I did configure the RAID card (the PERC 2/SC) completely and create the logical volume that I wanted Ubuntu installed on, before putting the CD in and booting from it.

Also, I used the **Server** install CD, *not* the Desktop/LiveCD.  And this was for 6.06.02 LTS.  I don't know what's behind the claims that the 'PERC is not supported' ... it seems totally supported on my machine, including, as I said above, the entries in /proc/megaraid for status and health.

The only thing I had to do post-install was manually force installation of the i686 kernel instead of the 386 one.  For some reason the installer defaulted to the 386 kernel and this doesn't support SMP, so only one of the machines processors was in use; using apt-get to install the same kernel version but in the 686 flavor fixed this.  Now both processors are in operation.  (There's really no excuse not to have 2 procs if you have a 2300 ... you can get surplus P3s on eBay for literally a few dollars these days.  Just make sure to either buy two of the same or match your existing processor exactly.)

---

