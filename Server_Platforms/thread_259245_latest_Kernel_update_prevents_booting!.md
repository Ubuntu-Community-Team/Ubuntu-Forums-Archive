---
title: "latest Kernel update prevents booting!"
date: 2006-09-17
forum: Server Platforms
---

### Post by Peturrr on 2006-09-17
I updated yesterday to the latest version of 2.6.15-26-server: 2.6.15-26.47 .
When I rebooted today the system didn't boot, but gave a kernel panic:

> 
RAMDISK: Compressed image found at block 0
crc error
VFS: cannot open root device "md0" or unknown-block(0,0)
Please append a correct "root=" boot option
kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)
 
root=/dev/md0
With the other kernel on my system:2-6-15-23 and the same parameters for root etc. The system does boot. So it is not a problem with the syntax in the grub menu entry. 

It looks like the system can't find the raid md0 drive, possibly doesn't initialize raid properly?

This is quite severe, since the only thing I did was sudo apt-get update && sudo apt-get dist-upgrade...
Fortunately I am running a non-production server.

I'll post a bug report, but I also post this here since I am interested if other people experienced the same problems.

---

### Post by richard_der on 2006-09-17
:frown: Yes I had the same problem and had to reformat my disk as a consequence. I did log this as a bug hopefully in the right place? The Ubuntu CD should have the option to replace a faulty kernel without having to reformat the disk.

---

### Post by Peturrr on 2006-09-19
Do you have a link to your bugreport? Than we can link these bugs.
I filed mine here:
[https://launchpad.net/bugs/60893](https://launchpad.net/bugs/60893)

---

### Post by divali on 2006-09-19
Dapper drake.
Exactamundo. This has just happened to me after I attempted to  downloaded updates yesterday and I'm having to use the earlier kernel at boot. Where do 
I go from here?:frown:

---

### Post by ChrisC on 2006-09-19
I'm having the same problem.  The #27 kernel on my k7 machine panics shortly after loading with something about running out of [un?]compressed space in the RAMdisk.  If I select the #26 kernel via grub then it boots fine (that's what I'm typing on now).

I would assume that we're not the first.  Hopefully someone will point us to the real thread where this is being discussed :)

---

### Post by ChrisC on 2006-09-19
Well, I take it back,  First, I came acorss this thread by searching, and I see now that it's in the "server talk" forum, and I'm not running the server version of Ubuntu.  Second, I don't think my errors have anything to do with disk mounting, but I'll take better notes of that tonight.  I still would like thread pointers if there are known problems with the kernel update that are being worked on.  Pretty bad ...

---

### Post by lifeempowered.com on 2006-09-19
It's a good idea to get ahold of [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page) (partimage) ISO and burn it to a CD, then boot from it and image your root system when it's working, to a backup location or DVD.  I did this before this fiasco of an update so if it's not working right I'll go back to my old image.

---

### Post by divali on 2006-09-20
Yes, but where do we go from here in order to solve this problem?
Is it caused by the new updates or a hardware problem?  I understand the 'CRC' relates to a disc problem. Anyone able to help with this ?

---

### Post by Peturrr on 2006-09-20
A response to my bug from Ben Collins was: 
> 
 Looks to me like the initramfs wasn't created correctly. Please boot from an older kernel, and run: sudo update-initramfs -u -k 2.6.15-26-server
 Make sure this runs without error. Note the message you see in dmesg confirms that the initramfs is not valid. If this appears to be a bug in the creation of this (e.g. not just a failure on the system like running out of disk space), open a target for this bug against initramfs-tools.

I did a sudo update-initramfs -u -k 2.6.15-26-server and a sudo update-initramfs -u -k 2.6.15-27-server. No errors, but still the same CRC error when booting.

I filed a new one for initramfs : [https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/61382](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/61382)

PIf you are having the same issues with the CRC error during boot and the kernel panic. Please add a comment at this bug. This way it will get noticed.

---

### Post by divali on 2006-09-20
Quote:
Please add a comment at this bug. This way it will get noticed.

Done.

---

### Post by Icereval on 2006-09-20
I would just like to note that I as well ran into this issue.

I applied the updates (apt-get upgrade) and cycled the system, when starting back up I then recieved the "crc error" system halted message.

I have a duplicate virtual box that I attempted to upgrade as well later today for testing, and found the linux-image upgrade has been restricted, so I assume this issue is being worked on...

From what I read about this "crc error" I would like to mention that my CD is an ISO thats being mounted from the Host OS, and has had the MD5 hash verified.

Also the Hard disk is virtual, which I have verified the RAID on the Host OS is working properly.

Virtual System Spec:
VMWare Server 1.0.1
Ubuntu 6.06.1 Server i386
512MB RAM
8GB SCSI

Host System Spec:
Windows 2003 Server
AMD 3000+ Barton
2GB RAM
RAID 1 - 2x 160GB SATA
RAID 1 - 2x 200GB SATA

---

### Post by Peturrr on 2006-09-21
Good to know I am not the only one. 

It definately looks to have to do with RAID. Since all people with this problem use RAID.


Would you please add a comment on the bug report?

---

### Post by NoWhereMan on 2006-09-21
no raid here and still kernel panic!

---

### Post by davidjneff on 2006-09-22
Definately not just Raid.  I have 2 different PCs, one an AMD desktop, the other a Pentium laptop, I get this same VFS kernel panic on both with the last 2 kernels.  -23 still boots, but -26 and -27 both panic.  I have re-installed grub, doesn't help.  I had been running Gentoo, but it got to be too much babysitting, now I switch to Ubuntu and run into this (still no comparison with the Gentoo maintenance though).  Just staying with -23 for now.

---

