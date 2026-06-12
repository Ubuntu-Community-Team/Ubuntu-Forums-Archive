---
title: "Ubuntu 11.04 Server Fresh Install - Won't boot"
date: 2011-09-08
forum: Server Platforms
---

### Post by n8af on 2011-09-08
Hey all,

I just put together a server box with two brand new WD 500 GB hard drives and a brand new server Mo-Bo. I established a mirror raid between the two drives as "Intel Raid1 Volume0". I booted ubuntu server from a USB stick and ran through the setup process. The installation finished without any issues. The system restarted, i removed the usb device and reentered the BIOS. Changed the boot priority to the Raid volume0 and hit save & exit. The system restarts and BIOS completes the POST screen, the raid utility menu pops up briefly, then....nothing. All i get is a blinking cursur in the upper left hand corner of the screen. I waited 10 min and nothing happens, no error message, no "unable to detect operating system" message, nothing at all. The only thing I can do is hit ctrl-alt-del to restart the system.[IMG]http://www.techsupportforum.com/images/smilies/4-dontknow.gif[/IMG]

System Specs:
Mo-Bo: [[COLOR=#014a8f]SUPERMICRO MBD-X7SBL-LN2 LGA 775 Intel 3200 Micro ATX[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813182145") 
CPU: Intel Core 2 Quad 2.5 Ghz 
RAM: 2 PNY 1GB DDR2 on channel0 667 Mhz, 2 [[COLOR=#014a8f]Crucial 1GB DDR2 [/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820148204")on channel1 800MHz (BIOS clocked at 667Mhz).
HDD: 2 [[COLOR=#014a8f]WD 500 GB Hard Disks[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136697") in RAID 1 (mirror)

Any ideas as to why the system won't boot?[IMG]http://www.techsupportforum.com/images/smilies/4-dontknow.gif[/IMG]

Thanks in advance!

---

### Post by Entilza on 2011-09-08
When it installed did it detect the raid correctly and was it infact installed on the raid drives, It could have installed on your USB stick if you didn't pick the correct location.

Also on the question with grub at the end, make sure you install on the Master boot record of the hard disk.

Finally, I would hold down the shift key after bios to see if you get the grub menu.

---

### Post by n8af on 2011-09-08
> **Entilza said:**
> When it installed did it detect the raid correctly and was it infact installed on the raid drives, It could have installed on your USB stick if you didn't pick the correct location.
 
Also on the question with grub at the end, make sure you install on the Master boot record of the hard disk.
 
Finally, I would hold down the shift key after bios to see if you get the grub menu.
 
I believe it did detect the raid.  It listed Intel Volume0 as the disk name during the install, although i'm wondering if i goofed that part up, i'll double check.  When the grub question came up it asked if I wanted to write to the master boot record - I selected yes.
 
I'm at work at the moment, I will double check to make sure it did in fact install to the RAID and try holding shift after bios.
 
Thanks - I'll get back to ya this evening.

---

### Post by n8af on 2011-09-09
I figured out why it wouldn't boot. Apparently Ubuntu server has a hard time booting from a hardware RAID configuration. What I did was disable the raid controller in bios and booted back into Ubuntu server installation (via USB thumbdrive) and started the installation. When the setup reached the disk setup/partition section, I had to setup a root and swap partion (achieved by choosing "configure free space automatically"). 
 
I noted that once I did this twice for both disks, the first disk changed to "do not use". I had to go back and ensure it was set back to '/' (root) and 'swap' and that root was bootable.
 
Once i had identical partitions on both drives, I had to configure a software RAID between the identical partitions on each drive (i.e. sda root and sdb root, sda2 and sdb2). Once I did this the rest of the setup went smoothly.
 
I tried searching the online community for a way to setup this with hardware raid via mo-board (i know some believe this isnt truely hardware raid, unless its a PCI SCISI) but the only support information I could find that fit my senario talked about using software RAID. Some information mentioned it isn't possible to do Mo-Bo SATA hardware RAID in Ubuntu, and that you had to use software RAID. 
 
Oh well, i'll keep this setup for now since it works.

---

### Post by Entilza on 2011-09-09
Hmm, ok so you are trying to use the motherboard's raid controller as a hardware raid controller.  I've always used an actual raid controller card for my servers so I am not too familiar how well ubuntu recognizes onboard motherboard raid controllers.  I've never had a problem with linux booting off one of these setup correctly.

It would be nice to use your raid controller on the board if possible.  I still want to ask again whether or not Ubuntu detected your raid drives with the controller enabled.  This is at the "Detect Disks" section of the install.  You will see a /dev/xxxx device with your terabyte raid space.  If you are only seeing the USB stick that means it cannot detect it.  You need to see both the USB drive and the terabyte raid.  So please let me know the answer to at least this if you aren't going further with this as I am curious.

I don't even believe you are using mdadm which is the real software raid.  I think you may be using dmraid which is completely fake.

Also it may be important to make a small /boot partition of maybe 200 MB as ext2.

Anyway since you are still at the setup stage I would try a bit more and not settle for the dmraid solution.  I am not sure why Ubuntu doesn't default to mdadm instead of dmraid.

---

### Post by Entilza on 2011-09-09
I think motherboard raid controllers are still considered software so I am not sure if Ubuntu has drivers in the kernel which support this.  The answer is at the detect disks section, let me know.  After the detect disk section it loads any modules necessary to control the drives.  You can press ALT-F2 and login as root.  Do a "fdisk -l"  to see what disks are being detected without installing anything to just test.  If you see it in fdisk then you should be able to get it working.

---

### Post by n8af on 2011-09-09
> **Entilza said:**
>  
It would be nice to use your raid controller on the board if possible. I still want to ask again whether or not Ubuntu detected your raid drives with the controller enabled. This is at the "Detect Disks" section of the install. You will see a /dev/xxxx device with your terabyte raid space. If you are only seeing the USB stick that means it cannot detect it. You need to see both the USB drive and the terabyte raid. So please let me know the answer to at least this if you aren't going further with this as I am curious.

 
I believe it did detect the RAID. When the Mo-bo RAID was still activated and configured using the Intel utility the Ubuntu server setup would ask if I wanted to "activate" the SATA Raid volume0. If I select yes, then it shows up on the partition screen as RAID (0,0,0,0) SATA volume0 1.0TB (stripe)....blah blah. I then setup two partitions, one root ('/') and one swap. The issue came when it was time to install the GRUB boot loader. GRUB would ask if I wanted to install it to the master boot record (/dev/sda). I would say yes, then it would give me a fatal error saying it could not install. I tried changing the command to sda1, sda2, etc. Nothing worked. I ended up selecting "finish installation without GRUB". Once the setup finished and rebooted, thats where I was getting the "no boot" problem with the blinking cursur in the upper left hand corner.

---

### Post by Entilza on 2011-09-09
I would create a /boot partition as "ext2" with 200 mb at the install.  You will have to mess around with the partition utility to get this right.

This partition will store your kernels and grub.  Give it a try if you are still up for getting this right.

---

### Post by n8af on 2011-09-09
> **Entilza said:**
> I would create a /boot partition as "ext2" with 200 mb at the install. You will have to mess around with the partition utility to get this right.
 
This partition will store your kernels and grub. Give it a try if you are still up for getting this right.
 
 
Sure, I would rather use the mo-bo raid config rather than a software (fake) raid.
 
So let me summarize what i should do.
 
- Enable mo-bo raid and setup volume0 with the BIOS Intel raid utility
 
- Boot into the Ubuntu Server Setup via USB Thumbdrive
 
- Select 'Yes' to activate the RAID (when asked)
 
- Partition as follows:
     - /boot      ext2     1GB (bootable)
     - swap                  (whatever size it needs)
     - / (root)    ext4    100GB
     -/home      ext4     (remaining size)
 
When GRUB installtion comes up, do i need to select /dev/sda? or enter a different path to direct it to the /boot partion?

---

### Post by Entilza on 2011-09-09
That's about right.  You don't need 1 gig for the /boot make it smaller 200mb is fine.

Ubuntu should be smart enough to detect /boot is separate and try to install grub there.

Good summary you are set to try again :)

---

### Post by n8af on 2011-09-09
> **Entilza said:**
> That's about right. You don't need 1 gig for the /boot make it smaller 200mb is fine.
 
Ubuntu should be smart enough to detect /boot is separate and try to install grub there.
 
Good summary you are set to try again :)
 
Awesome, Thanks for the quick response!  I'll give it a try and let you know :)

---

### Post by Entilza on 2011-09-09
If you haven't already started is your system running mdadm you can check by typing cat /proc/mdstat

You may have actually installed the mdadm correctly previously so you can fall back to that if needed.  I thought maybe you had done the fake raid solution (dmraid) instead of mdadm.

Apparently with software raid (mdadm) a separate /boot is only needed for RAID 5 but grub can read a RAID 1 for software.

---

### Post by n8af on 2011-09-09
> **Entilza said:**
> If you haven't already started is your system running mdadm you can check by typing cat /proc/mdstat
 
You may have actually installed the mdadm correctly previously so you can fall back to that if needed. I thought maybe you had done the fake raid solution (dmraid) instead of mdadm.
 
Apparently with software raid (mdadm) a separate /boot is only needed for RAID 5 but grub can read a RAID 1 for software.
 
I haven't started yet, i'm still at work at the moment.
 
When I selected software RAID it set it up as dmraid.  dmraid0, dmraid1 were the volume names after I combined the different drive partitions.

---

### Post by Entilza on 2011-09-09
ok, so regardless you are up for a reinstall whether we get the controller to boot the planned way or re-install with the proper software raid mdadm.

Just to plan ahead if the other method doesn't work is to disable the bios raid controller then, manually setup the patition structure.

Then similar to how you did the dmraid stuff you have to manually partition both drives as "Use as:  Physical volume for RAID"  you do this for both drives.  Then afterwards you have to "Configure software RAID" - create the multidisk (md) for the devices for example / /boot /home  very similar but this will create it with mdadm the proper software raid.  Make /boot separate anyway even though not necessary for raid 1, it's safer.  Hopefully the first method works though.

---

### Post by n8af on 2011-09-10
> **Entilza said:**
> ok, so regardless you are up for a reinstall whether we get the controller to boot the planned way or re-install with the proper software raid mdadm.

Just to plan ahead if the other method doesn't work is to disable the bios raid controller then, manually setup the patition structure.

Then similar to how you did the dmraid stuff you have to manually partition both drives as "Use as:  Physical volume for RAID"  you do this for both drives.  Then afterwards you have to "Configure software RAID" - create the multidisk (md) for the devices for example / /boot /home  very similar but this will create it with mdadm the proper software raid.  Make /boot separate anyway even though not necessary for raid 1, it's safer.  Hopefully the first method works though.

Alright, I tried the original configuration again with the mo-bo raid and partitioned out a root, boot, and home directory.  However, once I got to the GRUB installation, it gave me a fatal error again.  I tried typing in the path for the master boot record, the boot section of the Raid.  Nothing seemed to work.  I read in the debugging log (alt-f4 screen) that GRUB didn't like being split up between two devices (paraphrased).  

So anyways, I tried the second thing you mentioned.  Setting each partition to "use in RAID" and sectioned each disk using the example I provided earlyer.  Then RAID'd them together using the software raid.  I then left a 200MB section on one of the disks open (non-raid) as the boot section.  GRUB detected it right away and installed without any issues.  \\:D/

So all in all, I guess I have the RAID functionality as far as I can get it.  Now its time to dive into network configurations.](*,)

---

### Post by Entilza on 2011-09-10
Hey it's too bad the grub didn't work in the first case I would have liked to see the error messages but that's ok.  As I said I am not familiar with the motherboard raid so I would be interested if others have experience with this.

The /boot should have been part of the raid though even though it's a separate partition I would really re-do it one final time now that you've got it down pact.  Otherwise your boot won't be raided which is probably the most important part :)

Check out this thread I am not sure if it's similar to your orignal problem:  [http://ubuntuforums.org/showthread.php?t=1559762](http://ubuntuforums.org/showthread.php?t=1559762)

---

### Post by n8af on 2011-09-11
Thanks for that link, it helped to explain things more in-depth and give me hope for a solution.  I'll give it a try. Although, i was worried when no one responded back confirming or verifying their similar setup worked.

I guess it is worth a try - its not like Ubuntu takes as long to install as Windows does

---

### Post by YesWeCan on 2011-09-11
> **Entilza said:**
> ok, so regardless you are up for a reinstall whether we get the controller to boot the planned way or re-install with the proper software raid mdadm.
+1

@n8af: I have some experience of this. Just to clarify, mobo RAID is Fake RAID and it is a system aimed at Windows to enable it to do software RAID. So linux doesn't need it at all and it is advisable not to use it unless you intend to install Windows on this RAID in the future.

I'd not bother with a separate boot partition. I don't personally see any need for it.
4GB swap
16GB ext4 for /
480GB ext4 for /home
Is my guess at what you will want (in the absence of more info about what you will use the server for)

You can either make 3 separate RAID1s for each of the three partitions or you can make one 500GB RAID1 partition and add an LVM layer to it to make separate volumes (partitions). I chose the latter as it gives a little more flexibility if you want to add new volumes in the future or resize them.

Having swap in a RAID is not strictly necessary. It just means that if a drive fails and your system just happens to be using swap space at the time then it might crash a running application or something. Cause a glitch. For guaranteed continuation of service put the swap in RAID.

---

### Post by n8af on 2011-09-11
> **YesWeCan said:**
> +1

@n8af: I have some experience of this. Just to clarify, mobo RAID is Fake RAID and it is a system aimed at Windows to enable it to do software RAID. So linux doesn't need it at all and it is advisable not to use it unless you intend to install Windows on this RAID in the future.



So what your saying is if I want a true hardware raid, then I need to add a PCI raid controller that supports SATA hard drives?

Edit: Or is it even worth the effort using a PCI raid controller? I just heard some people downing software RAID in general.  I guess for what i'm wanting it for its probably just fine with Ubuntu's software raid (not fake-raid).

---

### Post by YesWeCan on 2011-09-11
> **n8af said:**
> So what your saying is if I want a true hardware raid, then I need to add a PCI raid controller that supports SATA hard drives?
Yep, one of these: [http://www.newegg.com/Product/Product.aspx?Item=N82E16816103221](http://www.newegg.com/Product/Product.aspx?Item=N82E16816103221)
If you read the spec sheet for your $180 mobo it says "RAID X support". The operative word being "support". It supports Windows to do software RAID. Pretty ambiguous, isn't it?

> Edit: Or is it even worth the effort using a PCI raid controller? I just heard some people downing software RAID in general.  I guess for what i'm wanting it for its probably just fine with Ubuntu's software raid (not fake-raid).
I have never used a proper h/w RAID controller so I can only speculate. Look at the performance specs. for the Adaptec controller.
Some advantages of mdadm are flexibility - you can make raid devices out of individual partitions. You aren't tied to the PCI hardware - your disks can be put into another linux PC and the raid will work. Easier to debug. And a lot, lot cheaper, of course.
Having said that, I wouldn't be surprised if the Adaptec controller has some pretty slick and robust error recovery algorithms.

You have to be very careful with PCI cards. There are a lot that are Fake RAID but look like hardware RAID! The crude way to tell is by price and then by the size of the heatsinking on the card!

---

### Post by Entilza on 2011-09-11
> **YesWeCan said:**
> Yep, one of these: [http://www.newegg.com/Product/Product.aspx?Item=N82E16816103221](http://www.newegg.com/Product/Product.aspx?Item=N82E16816103221)


Lol that's the raid controller we use.

Yeah if you look at the big picture how can a motherboard have a real hardware raid if what is necessary for real raid hardware is a huge card like this with dedicated processor, ram etc.

For multi user systems a hardware controller is the way to go or heavy IO applications.

I think the signal that it's fake raid is the time Ubuntu asks if you want to activate the intel raid.  It should not have to ask, if it's a real hardware raid it should just detect the entire array as a single /dev/sda (for example) and not show separate drives with fdisk -l when installing.  Mind you you will need the module drivers or hope ubuntu has it already as part of the base kernel.

Anyway what is this server for if its not that high demand I bet mdadm will be fine, yer almost there let us know how it goes :)

---

### Post by YesWeCan on 2011-09-11
@Entiliza: you have one if those cards...nice. :)

@n8af: Ubuntu will detect both dmraid and mdraid, by default, and you really only want mdraid. I'd be inclined to be over-cautious and disable all raid options in bios and remove any dmraid superblocks that may have been written to the disks,
sudo dmraid -E -r /dev/sdx
choose appropriate value of x for your drives.

---

### Post by n8af on 2011-09-11
Awesome, thanks for that bit of information!  I think for what I'm trying to do right now (which is a home file/print server - for starters) that the software raid setup will do just fine.  

I build this server box out of some old PC hardware I had laying around and a new mo-bo and hard drives.  I'm not in the market for a PCI device that costs twice as much as what I already invested into this box, lol. Maybe later on I will be, but for now, i'll stick with what I got.

Thanks very much for the information guys, I have learned a lot about Ubuntu from this experience (which was my goal in the beginning).

---

