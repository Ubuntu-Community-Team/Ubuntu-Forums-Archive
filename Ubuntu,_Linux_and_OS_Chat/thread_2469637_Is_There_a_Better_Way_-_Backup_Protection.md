---
title: "Is There a Better Way - Backup Protection"
date: 2021-12-04
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2021-12-04
Is a ransomware attack likely on ubuntu/linux?  Assuming it is a possibility I've been looking at ways of securing myself on my stand-alone pc.  I have a 'working' HD and a second HD I use for backup; and use rdiff-backup as my means of performing the actual backup.  I have a custom icon that I *use/click on* when I want to shutdown the pc.  This icon runs a script that runs rdiff-backup and then shuts down the pc when the backup is finished.  Over the past months I've read, every now again, the model where a backup machine 'pulls' the data off a live machine using all sorts of tools including cron.  This seems to me a very good model to protect against ransomware like attacks (the backup up *device/machine* is not connected to the live machine) but not that practical for a stand alone Desktop that is switched on and off at random times.  In order to try and simulate the 'pull' model as closely as I can this is what I have done.

[LIST]
[*]Left my existing fstab 'as is' with the two HDs configured as normal
[*]Created a script that is run as part of the boot process (put an entry in Startup Applications - running Ubuntu Mate) that runs a command that unmounts the backup HD*
[*]Amended my rdiff-backup script so that the first thing it does is mount the backup HD and then runs the backup**
[/LIST]


*  when my Desktop boots the backup HD is unmounted but I've put a 3 secs delay before the umount script is run.
** Not sure whether this is necessary but the script runs the mount command, waits 3 secs, then runs the rdiff-backup command, then waits 2 secs to runs the shutdown command.

At the moment this model works but I'm not sure if it is the best way of achieving a Desktop/pull way of working. Also, for reasons I cannot explain I've put 3 sec and 2 sec delays between mount,rdiff-backup,shutdown in my script.

---

### Post by grahammechanical on 2021-12-04
I do not know anything about ransomware except the little I have read since first viewing your post. It seems that ransomware works by 1) locking the OS. I assume that means changing the password Or, 2) encrypting the hard drive which would require a password to unlock the hard drive.

I also assume that the ransomware would encrypt all drives connected to the machine even those drives that are not mounted and even powered down. I also suspect that the ransomware would have a component that would allow it to infect all machines connected to the network. The way to remove ransomware is to wipe the hard drive and reinstall. That also wipes out all the data. So, backups are important.

In your case the situation is more simple. I suggest you think about backing up to removable storage that is ejected once the backup is complete.

Regards

---

### Post by lammert-nijhof on 2021-12-04
I had a ransomware attack, they asked for 4000 Euros, but they were amateurs (no encryption), but they used a claim, that they found compromising stuff (liars) and had all my email addresses. I had Ubuntu installed on OpenZFS as supported by the Ubuntu-installer. OpenZFS supports snapshots. So I rolled back Ubuntu to a date 2 weeks before the threatening email, changed my passwords and reapplied all changes from the last 3-4 weeks and that was the end of the ransomware attack. They came into my machine through the browser! Since that time I use a master password to protect e.g the passwords stored by the browser. A more general snapshot tool is TimeShift. 

It is difficult to enter my computers directly from the Internet, I have the ISP WiFi Router and for my computers in the back of our house I have an own old WiFi router. I changed username and password and that old TP-WRxxxx limits access to my desktop and laptop checking their physical MAC addresses. After that old router I use a cheap 5 port 1Gpbs switch to speed up my backups to laptop (Ubuntu) or backup-server (FreeBSD).

I use the laptop only during travel, so basically my 2 backups are powered off always with the exception of say 1 to 3 hours/week. I do an incremental backup once per week. If they would encrypt my desktop drives, I can reformat all my drives and restore my stuff from one of the backups. I expect, they would have troubles getting hold of my backups, since they are powered off and beside one of them is another 32-bits BSD OS.

I have moved all my work to 5 VMs and those have limited access, only to the parts of the data they need. I should have moved my browsing also to a VM and nowadays I also browse from a VM and worse case I delete the complete VM :)  Re-installation and setting up the VM again would take 0.5 to 3 hours. Currently I use Xubuntu 20.04 LTS for all external communication and I could also fall back on the previous version for that communication; VM Xubuntu 18.04 LTS or the next version Xubuntu 22.04.  I already use Xubunti 22.04 for hours as a kind of alpha test for my communication without any issues.

[LIST]
[*]I think I made direct entry really difficult,  also because all VMs; the desktop host and the TP WiFi router are closed for inbound traffic, only the communication VM has a few open ports for the local network. So I don't worry about that type of attack. 
[*]Entry through browser and email have more risks, that is why I use a VM for communication. I could restore from older snapshots of the VM or from the backup and worse case I could deleted it completely and use another VM; or reinstall it from scratch. 
[/LIST]
 I use Ubuntu 21.10; OpenZFS 2.0.6 and Virtualbox 6.1.30. The hardware is relatively modern but modest: a Ryzen 3 2200G; 16GB; 512GB nvme-SSD and 2 leftover HDDs (1.5TB). 
The laptop is 2011 Sandy-Bridge i5 with a new 2TB HDD and the backup server a 2003 Pentium 4 HT (1C2T; 3.0GHz; 2GB DDR) and 4 leftover HDDs (2 IDE 3.5" and 2 SATA 2.5") in total 1.21TB.

ZFS now supports built-in encryption, so I consider encrypting my data, but it would not help against attacks through browser or email.

I your case I would move the backup to an USB disk (either a new one or move the existing disk to an USB 3.1 HDD enclosure) and keep that HDD powered-off say 99% of the time. At least I would remove the disk from fstab, it is too easy to mount disks, if they are in fstab.

---

### Post by TheFu on 2021-12-05
I've gotten hundreds of emails claiming that they have embarrassing data from my computers asking for money/coins.  They said I had good taste in porn too.
I've ignored all of them, since there wasn't any other "proof" they'd actually done anything or entered any of my systems.

I have been hacked a few times, over the decades.  The last 2 times I was saved by backups.  The last time, I expected to be hacked (was at a security/hacker conference), so the system was a fresh install with no personal data on it. I planned to perform a wipe and restore from backups when I got home.  Little did I know that I'd be doing that the 2nd evening there. At the time, I think I was using Lubuntu, so I had an Lubuntu ISO/flash drive with me. Installs were slower then - 30 min while I watched TV in the hotel.

If you have only 1 computer, the best answer for backups besides having them automatic, versioned, and put onto encrypted storage, is to have them off-line.  A USB3 "dock" that can be powered down when not in use is very flexible and cheap.  Maybe start the backup+shutdown and brush your teeth, then come back and push the dock power button?

---

