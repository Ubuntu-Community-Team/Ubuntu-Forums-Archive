---
title: "Reinstall Solaris to drive after Ubuntu installation"
date: 2007-01-08
forum: Sun Sparc Users
---

### Post by levinep on 2007-01-08
I was trying to set up a SunBlade 1000 to dual boot to Solaris 10 on one scsi drive and Ubuntu 6.06 sparc on the other drive. The Blade is OBP 4.16.4. Now I need to use the Blade for other tasks so I'll move my Ubuntu experiment to another box. My problem is that when I try to install Solaris 10 on the drive that had Ubuntu installed to it, the Solaris installation program tells me that no drives were found. I tried booting from the Ubuntu install CD again, but I don't see all the partition/file system options that I saw on the install CD for a PC. I was hoping I could mark or format the drive so Solaris would recognize it again (it had Solaris installed to it originally). Has anyone been down this road? Does anyone know how to return that drive to a state where I can use it for Solaris once again? It's not a matter of the drive being bad. I can boot Ubuntu from it and I can reinstall Ubuntu to it, so the drive is working and visible to Ubuntu.

---

### Post by netztier on 2007-01-08
> **levinep said:**
> I was hoping I could mark or format the drive so Solaris would recognize it again (it had Solaris installed to it originally). Has anyone been down this road? 


It's not the formatting, it's the partitioning. I remember this from my Gentoo days:

[Gentoo Linux Handbook, 4. Preparing the Disks]("http://www.gentoo.org/doc/en/handbook/handbook-sparc.xml?part=1&chap=4")

Boot the System from live CD and run fdisk on the disk you want to use in Solaris. Make sure that the 3rd partition covers the entire disk and has a Sun disk label (Id 5).  (see the Gentoo Document).

I can't remember if I actually did this once with success, but I remember vaguely reverting to Solaris from Linux once.

best regards

Marc

---

### Post by levinep on 2007-01-10
Well, your response looked so promising...........

I boot from the sparc install CD and I don't find fdisk anywhere. I boot from the 
CD and go to "rescue" and open a shell and there's no fdisk there, either. The
partition options from the installer don't include anything related to Solaris. So,
I guess I need a CD that:
1) Can be booted on sparc hardware
2) Has fdisk or a similar utility
3) Recognizes a disk with Ubuntu's partitioning

I hate to give up on a 72G scsi drive that is (was) perfectly good. If installing 
Ubuntu to sparc hardware is such a one-way street, it certainly makes 
experimenting a lot less appealing. Any other thoughts on the subject?

---

### Post by netztier on 2007-01-10
> **levinep said:**
> Well, your response looked so promising...........

I boot from the sparc install CD and I don't find fdisk anywhere. I boot from the 
CD and go to "rescue" and open a shell and there's no fdisk there, either. 

Nah, can't really be. The partitioner has to use some form of fdisk, too. So its gotta be there. Did you open a shell from the installed Ubuntu on the drive or one from the livecd environment?

ah.. seems it's  done with **[FONT="Courier New"]/sbin/parted[/FONT]** from the livecd environment.

give it a try!

best regards

Marc

---

### Post by Delta_Farce on 2007-01-11
I tried to revert from 6.06 to Solaris 10 once (to upgrade the OBP) on a Blade 150. It seems Solaris doesn't like the way linux partitions the disks and it didn't work for me (with an IDE disk).

Only having a Sun label might work, but in my case I had to zero my disk and start from scratch before Solaris could see it. Let us know how you go with it though.

Cheers,

Mark

---

### Post by netztier on 2007-01-12
> **Delta_Farce said:**
> Only having a Sun label might work, but in my case I had to zero my disk and start from scratch before Solaris could see it. Let us know how you go with it though.


That of course might work also: blank the entire partition table and let Solaris do the partitioning and setting of the disk label itself.

Probably also worth reading: [The "format" Utility in the Solaris Operating System]("http://www.sun.com/bigadmin/content/submitted/format_utility.html") on [www.sun.com/BigAdmin](www.sun.com/BigAdmin) 

best regards

Marc

---

### Post by sovs on 2007-01-12
I'd take a stab the ubuntu has put EFI labels on your disk.

solaris only works with SMI labels.

if you run "format -e" on your disk the first thing it will ask you is to switch to an SMI label.

you need to do this manually - the solaris install program won't do it automatically.

---

### Post by levinep on 2007-01-18
Well, it seems that the key to the problem was the SMI vs. EFI label.

I played with /sbin/parted on the Ubuntu CD, but it never would allow 
me to make a third partition that used the entire disk. It showed a disk 
label of sun, but no matter what I tried, the Solaris installer still complained, 
"No disks found". Finally I removed all partitions and rebooted with the Solaris
install CD. It still couldn't see the drive, so I exited the install program,
went to the terminal window that was open and entered the format
command. The disk was visible, but when I entered "label", I got this
message:
Error occurred with device in use checking: Permission denied

I quit format and tried "format -e" as was suggested in the posting.
Now I got two choices when I typed "label":
[0] SMI
[1] EFI
When I chose SMI, I got a message telling me that the disk had an EFI 
label and changing to SMI would erase all current partitions. After that,
I was prompted two more times:
Auto configuration via format.dat [no]?
Auto configuration vi generic SCSI-Z [no]?
I chose the default "no" for both, exited format, rebooted from the 
Solaris install CD, and, lo and behold, the installer saw the drive.
I let a default install occur just to make sure everything was working.

Thanks to all who posted and led me to the solution! I've partitioned
Sun boxes quite a bit, but never dealt with SMI vs. EFI before.

---

