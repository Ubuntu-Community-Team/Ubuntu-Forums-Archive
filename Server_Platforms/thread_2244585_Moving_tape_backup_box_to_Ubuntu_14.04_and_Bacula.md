---
title: "Moving tape backup box to Ubuntu 14.04 and Bacula"
date: 2014-09-17
forum: Server Platforms
---

### Post by Michael_McKenney on 2014-09-17
My current tape backup workstation has XP Pro x64 on it.   It is my old workstation

Backup workstation running Symantec Backup Exec 2010
XP x64 Pro SP2
Tyan Thunder K8WE server board
dual AMD Opteron 280
16GB RAM
On-board Gbps NIC 
SATA drives
Adaptec SCSI U320 controller
HP LTO3 tape drive
Two Exabyte VXA-2 tape drives
Runs over 300W total load with dual Opterons

Web Server
Ubuntu 14.04
Intel DG33TL board
Gbps NIC in slot
2GB RAM
Intel 775 dual core CPU
Runs at 96W total load


Workstation
Windows 7 x64 Ultimate
16GB RAM
Intel i7 2600K CPU
LSI Logic SAS RAID controller
two 15K SAS drives in RAID 1
two 10K SAS drives in RAID 1


I backup to tape because my web site at home has 130GB of pictures and videos on it.  I also have my Windows 7 x64 Ultimate workstation that is backed up along with the Backup workstation.  Since XP x64 is retired from Microsoft, I want to switch to another tape backup solution.  Tapes cannot get Cryptolocker or other viruses like my firewire 800 drives or cloud backups.  I can't do cloud backup because my ISP will not allow me to move 100+ GB of files.   

I have two options.  
1.) Get a SCSI controller for my web box and move the tape drives into it.   
2.) Reinstall my backup workstation with Ubuntu that has everything installed in it but runs at more wattage due to dual Opterons

Questions:
1.) Will Ubuntu run stable on the Tyan Thunder K8WE?  It was designed for enterprise Linux.  
2.) How is the SCSI and tape drive performance in Ubuntu on Bacula?
3.) Can I get Windows 7 drivers to backup my workstation?

---

### Post by matt_symes on 2014-09-17
Hi

Wow. That's some setup you have there.

You may struggle to get an answer here as your requirements, hardware and questions are very specific.

Here are my thoughts though - only thoughts and not answers :)

> Get a SCSI controller for my web box and move the tape drives into it.

Will this affect your webserver performance while the backup is occurring ? I assume you're streaming your videos. What is your traffic like, how often and how long does the backup take.

> Reinstall my backup workstation with Ubuntu that has everything installed in it but runs at more wattage due to dual Opterons

This is a real trade off. Is your backup PC on all the time or only when performing a backup ? What are your bills like. Personally i like to backup to a everything to a dedicated, separate PC.

> Will Ubuntu run stable on the Tyan Thunder K8WE?  It was designed for enterprise Linux.

I would suspect it would run Ubuntu fine but i would ask the board manufacturer; see what they have to say. 

You could also run Ubuntu from a Live CD/USB and have a play with it but this will only give an indication - all be it a good one - of what Ubuntu will be like when installed on bare metal.

Backup your backup PC. That way you can roll back to XP if required.

> How is the SCSI and tape drive performance in Ubuntu on Bacula?

I can't really offer any suggestions about this as i have no tape drives. Do you have a spare PC you can test on ?

> Can I get Windows 7 drivers to backup my workstation?

Backula is available for Windows 7 and as for any drivers you may need - apart from work, I have not used Windows in a long, long time.

Sorry i cannot be of more help but hopefully this reply will get the ball rolling.

Kind regards

---

### Post by Michael_McKenney on 2014-09-17
I am in charge of an entire data center running a HP C7000 Blade Center and VMware 5.5 U2 on 29 VMs.  At work we are 100% Microsoft.  At home, I switched to Ubuntu from XP IIS to Fedora Core 7.   Ubuntu was easy to work with.   So I want to switch my backup workstation to it.   

My home hardware is production grade for my CAD and A/V projects.  

XP x64 Backup workstation is only on for backups.  Problem is XP x64 Pro can't be reinstalled and activated, if it has issues.  I lose access to my four backup tape sets.   I don't have spare hardware left to build from.  My only SCSI controller is PCI-X server grade.   The Ubuntu box is PCI-E.  $250 for a PCI-E SCSI controller.   I thought about moving my web site to the Tyan workstation.  However, you do bring up a good point.  I could just use the backup box for the backups and leave the web site on the 96W box.   I did consider dual booting XP x64 and Ubuntu 14.04.  The last time I dual booted Linux and Windows caused both to fail.  The boot sector was corrupted.   I have a firewire 800 drive that can backup the web site and critical files from Windows 7 that can be disconnected.  

I leave the current Ubuntu box alone with the web site.  I convert the Tyan Thunder K8WE box to Ubuntu.  I could remove the Windows hard drive to keep it safe and install a new drive.   Tyan only supports certain OS and will not answer questions from non-supported stuff.  You are on your own.  

Tyan box has issues booting USB drives.  It was a quirk in the BIOS of the board.  It was my last Tyan board ever.  They removed the hardware monitoring from all their server boards.  It was $600+ for the board.   I remove the XP hard drive and install a new clean hardware for Ubuntu.  No dual booting.   I will not use software RAID from Tyan.  Single drives only.   I found how to install the SCSI and tape drivers in Google.  

How can I resize the /boot partition.   It is 8GB on my current web site box.   Upgrades fill it at 4-5 revisions.  I have to manually delete the files.  I keep the first and last revisions only.  Everything in the middle gets deleted.  I wish upgrades would clean up like Windows.

---

### Post by matt_symes on 2014-09-17
Hi

> **Michael_McKenney said:**
> I am in charge of an entire data center running a HP C7000 Blade Center and VMware 5.5 U2 on 29 VMs.  At work we are 100% Microsoft.  At home, I switched to Ubuntu from XP IIS to Fedora Core 7.   Ubuntu was easy to work with.   So I want to switch my backup workstation to it.   

My home hardware is production grade for my CAD and A/V projects.  

That explains your hardware. I was wondering where you got that kit from.

> XP x64 Backup workstation is only on for backups.  Problem is XP x64 Pro can't be reinstalled and activated, if it has issues.  I lose access to my four backup tape sets.   I don't have spare hardware left to build from.  My only SCSI controller is PCI-X server grade.   The Ubuntu box is PCI-E.  $250 for a PCI-E SCSI controller.   I thought about moving my web site to the Tyan workstation.  However, you do bring up a good point.  I could just use the backup box for the backups and leave the web site on the 96W box.   I did consider dual booting XP x64 and Ubuntu 14.04.  The last time I dual booted Linux and Windows caused both to fail.  The boot sector was corrupted.   I have a firewire 800 drive that can backup the web site and critical files from Windows 7 that can be disconnected.  

I leave the current Ubuntu box alone with the web site.  I convert the Tyan Thunder K8WE box to Ubuntu.  I could remove the Windows hard drive to keep it safe and install a new drive.   Tyan only supports certain OS and will not answer questions from non-supported stuff.  You are on your own.

Tyan box has issues booting USB drives.  It was a quirk in the BIOS of the board.  It was my last Tyan board ever.  They removed the hardware monitoring from all their server boards.  It was $600+ for the board.   I remove the XP hard drive and install a new clean hardware for Ubuntu.  No dual booting.   I will not use software RAID from Tyan.  Single drives only.   I found how to install the SCSI and tape drivers in Google.  

That sounds like a good plan. As i said, i prefer a dedicated backup PC and keeping the existing hard drive will expidiate any rollback you have to perform as well as allowing you to test the new system.

> How can I resize the /boot partition.   It is 8GB on my current web site box.   Upgrades fill it at 4-5 revisions.  I have to manually delete the files.  I keep the first and last revisions only.  Everything in the middle gets deleted.  I wish upgrades would clean up like Windows.

When you say ugrades i assume you mean kernel updates ?

You can resize your boot partition using a LiveCD/USB and gparted. You will need to shrink the partition next to the boot partition and then expand the boot partition into the space created by shrinking the other partition.

Of course, it goes without saying, backup before attempting this.

Ubuntu should offer to delete any old kernels for you though. Have you been running 

```
sudo apt-get autoremove
```

This should remove any old packages including old kernels (IIRC).

BTW: How were you deleting the old kernels ?

Kind regards

---

### Post by Michael_McKenney on 2014-09-17
All my home hardware was built from the ground up.  My workstation power supplies were custom wired from PC Power and Cooling.  My main workstation has its own 20A dual 120V circuits and Tripp Lite line conditioners.  I am an Electrical Engineer and senior network engineer.  I have been building hardware since 1982.  I started in DOS.  I switched to SAS RAID because I would destroy a SATA drive monthly.   LSI Logic 8708EM2 128MB battery cache controller in RAID 1 gives me 1.097 GB/s cached reads and 850MB/s cached write.   SAS drives are server room drives that are designed for 24x7x365x5 year use.  They usually don't fail.  I also have 11 Panflo fans in my main workstation for maximum 30dB air flow.  

I never knew about sudo apt-get autoremove.  I will run it tonight.   I was only cleaning up /boot.  

My current method is go into /boot and manually delete the files that were in the middle revisions.  I kept the lowest and highest build of each file.

---

### Post by Michael_McKenney on 2014-09-17
burning a live DVD disk to test tonight.

---

### Post by Michael_McKenney on 2014-09-17
I tested the Live Boot DVD on a workstation with an LSI Logic SCSI controller.   It was able to see the controller with no problems.  Tonight, I will test it on the Tyan workstation.

---

### Post by Michael_McKenney on 2014-09-17
Live CD 14.04.1 looks like it found the SCSI controller, all NVidia drivers, all hard drive partitions.  I am still looking for the tape drives.   I did get an Cannot Reserve MMIO region.  I read it is nothing to worry about.

---

### Post by Michael_McKenney on 2014-09-17
cat /proc/scsi/scsi shows all the three tape drives and firmware correctly.  I can see all three SATA hard drives.  I could boot to Windows XP x64 and clear some partition space to dual boot Ubuntu 14.04.1.   Do I need partition space on drive 0 for the boot drive like in older versions?

---

### Post by Michael_McKenney on 2014-09-17
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ cat /proc/scsi/scsi
Attached devices:
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: TSSTcorp Model: CDDVDW SH-S223Q  Rev: SB00
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi3 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3750640AS      Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3500320AS      Rev: SD15
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi5 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3500320AS      Rev: SD15
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi6 Channel: 00 Id: 10 Lun: 00
  Vendor: EXABYTE  Model: VXA-3            Rev: 3233
  Type:   Sequential-Access                ANSI  SCSI revision: 03
Host: scsi6 Channel: 00 Id: 12 Lun: 00
  Vendor: EXABYTE  Model: VXA-3            Rev: 3233
  Type:   Sequential-Access                ANSI  SCSI revision: 03
Host: scsi7 Channel: 00 Id: 13 Lun: 00
  Vendor: HP       Model: Ultrium 3-SCSI   Rev: D22D
  Type:   Sequential-Access                ANSI  SCSI revision: 03
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$

---

### Post by Michael_McKenney on 2014-09-17
ubuntu@ubuntu:~$ lspci
00:00.0 Memory controller: NVIDIA Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: NVIDIA Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: NVIDIA Corporation CK804 SMBus (rev a2)
00:02.0 USB controller: NVIDIA Corporation CK804 USB Controller (rev a2)
00:02.1 USB controller: NVIDIA Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: NVIDIA Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: NVIDIA Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: NVIDIA Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: NVIDIA Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: NVIDIA Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: NVIDIA Corporation CK804 Ethernet Controller (rev a3)
00:0e.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:19.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:19.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:19.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:19.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: NVIDIA Corporation NV43 [GeForce 6600 LE] (rev a2)
10:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] AMD-8131 PCI-X Bridge (rev 12)
10:0a.1 PIC: Advanced Micro Devices, Inc. [AMD] AMD-8131 PCI-X IOAPIC (rev 01)
10:0b.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] AMD-8131 PCI-X Bridge (rev 12)
10:0b.1 PIC: Advanced Micro Devices, Inc. [AMD] AMD-8131 PCI-X IOAPIC (rev 01)
11:04.0 SCSI storage controller: Adaptec ASC-39320A U320 (rev 10)
11:04.1 SCSI storage controller: Adaptec ASC-39320A U320 (rev 10)
80:00.0 Memory controller: NVIDIA Corporation CK804 Memory Controller (rev a3)
80:01.0 Memory controller: NVIDIA Corporation CK804 Memory Controller (rev a3)
80:0a.0 Bridge: NVIDIA Corporation CK804 Ethernet Controller (rev a3)
80:0e.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev a3)
ubuntu@ubuntu:~$

---

### Post by matt_symes on 2014-09-18
> **Michael_McKenney said:**
> All my home hardware was built from the ground up.  My workstation power supplies were custom wired from PC Power and Cooling.  My main workstation has its own 20A dual 120V circuits and Tripp Lite line conditioners.  I am an Electrical Engineer and senior network engineer.  I have been building hardware since 1982.  I started in DOS.  I switched to SAS RAID because I would destroy a SATA drive monthly.   LSI Logic 8708EM2 128MB battery cache controller in RAID 1 gives me 1.097 GB/s cached reads and 850MB/s cached write.   SAS drives are server room drives that are designed for 24x7x365x5 year use.  They usually don't fail.  I also have 11 Panflo fans in my main workstation for maximum 30dB air flow.  

Impressive.

> I never knew about sudo apt-get autoremove.  I will run it tonight.   I was only cleaning up /boot.  

My current method is go into /boot and manually delete the files that were in the middle revisions.  I kept the lowest and highest build of each file.

You don't want to manually delete the files as the entries are still left in the package manager database.

To manually delete, you want to use 

```
sudo apt-get purge <kernel_name>
```

Where <kernel_name> is the name of the kernel. You may also want to delete the headers this way.

However, as i stated, sudo apt-get autoremove should remove old kernels for you. It keeps the last 2 kernel installed only.

Kind regards

---

### Post by Michael_McKenney on 2014-09-18
I still see 4-5 revisions in /boot.  I will try sudo apt-get purge <kernel_name>.   How do I determine what part is the kernel name?  sudo apt-get autoremove removed about 3GB of files.

---

### Post by matt_symes on 2014-09-18
Hi

> **Michael_McKenney said:**
> burning a live DVD disk to test tonight.

Excellent. That will give you a feel for the hardware uder ubuntu.

Kind regards

---

### Post by matt_symes on 2014-09-18
Hi

> **Michael_McKenney said:**
> I tested the Live Boot DVD on a workstation with an LSI Logic SCSI controller.   It was able to see the controller with no problems.  Tonight, I will test it on the Tyan workstation.

I don't expect there will be any problems. It's good that it see the controllers.

As it should run enterprise Linux then it should run Ubuntu without problems - hopefully.

Kind regards

---

### Post by matt_symes on 2014-09-18
Hi

> **Michael_McKenney said:**
> cat /proc/scsi/scsi shows all the three tape drives and firmware correctly.  I can see all three SATA hard drives.  I could boot to Windows XP x64 and clear some partition space to dual boot Ubuntu 14.04.1.   Do I need partition space on drive 0 for the boot drive like in older versions?

No. You do not need a seperate boot partition. I don't use them.

Kind regards

---

### Post by matt_symes on 2014-09-18
Hi

Your last two posts look good.

BTW: Sorry for the late reply. Was away from keyboard.

Kind regards

---

### Post by Michael_McKenney on 2014-09-18
So to dual boot for now, I just remove existing Windows partitions on the 3 hard drives and let Ubuntu configure itself.  Will it update the Windows XP x64 boot launcher files?  Once Ubuntu and Bacula are working, I no longer need Windows XP x64.  I just don't want to lose access to the Symantec backups until two backups are completed and restores are tested on both Ubuntu and Windows 7.

---

### Post by matt_symes on 2014-09-18
Hi

> **Michael_McKenney said:**
> So to dual boot for now, I just remove existing Windows partitions on the 3 hard drives and let Ubuntu configure itself.  Will it update the Windows XP x64 boot launcher files?  Once Ubuntu and Bacula are working, I no longer need Windows XP x64.  I just don't want to lose access to the Symantec backups until two backups are completed and restores are tested on both Ubuntu and Windows 7.

Can we clarify first. 

Are the hard drive in a raid array ?

Is Windows just installed on one drive and the drives are just data drives ?

Kind regards

---

### Post by matt_symes on 2014-09-18
Hi

> **Michael_McKenney said:**
> I still see 4-5 revisions in /boot.  I will try sudo apt-get purge <kernel_name>.   How do I determine what part is the kernel name?  sudo apt-get autoremove removed about 3GB of files.

To get a list of the kernels you can use the dpkg command.

Here's an example from the kernel on my notebook.

```

matthew-laptop:/home/matthew/storage/my_isos/xubuntu_daily_build:1 % dpkg -l | grep linux-image
rc  linux-image-3.13.0-32-generic                               3.13.0-32.57                          amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                               3.13.0-34.60                          amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                               3.13.0-35.62                          amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic                         3.13.0-32.57                          amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                         3.13.0-34.60                          amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                         3.13.0-35.62                          amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                         3.13.0.35.42                          amd64        Generic Linux kernel image
matthew-laptop:/home/matthew/storage/my_isos/xubuntu_daily_build:1 %
```

You want to remove both the linux-image and the matching linux-image-extra packages for each kernel you don't need.

I surprised apt-get autoremove did not remove the old kernels. 

Have you pinned any kernels ?
Did you install them manually ?

Kind regards

---

### Post by Michael_McKenney on 2014-09-18
I installed Ubuntu 12.x from a DVD on the web server box.  I upgraded using the sudo apt-get dist-upgrade command or whatever sudo apt-get command did the distribution upgrades and told it to clean up after.   I don't know enough about Ubuntu to pin anything.  I mainly use Microsoft at work and home.  Ubuntu is just because I needed a easy web site my ISP would not care I had.   My main workstation will be Windows because of the CAD and Adobe products I run.  I also need Cisco Anyconnect to access the data center.  

I did consider using the command I found on one site to remove all but the newest revision

sudo apt-get remove --purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d')

I found sites with other commands to purge all kernels except the current one.  Once I backup everything a few times, I would do a destructive cleanup to remove all the old kernels.   The web site is over 130 GB of pictures and videos from all my trips around the world and other stuff.

 dpkg -l | grep linux-image, I will run this tonight and see what comes up.

---

### Post by Michael_McKenney on 2014-09-18
The problem with server grade hardware is the design is for enterprise OS.  XP x64 runs on it because it was Windows 2003 x64 stripped down.  They tell you no 32-bit OS will run on it.   This level of hardware has quirks that consumer grade hardware does not have.  It is made for data center engineers to use and run only specific OS on it.   I still don't know how stable Ubuntu 14.04 will be on it running Bacula.  I was wondering if I could use some of the Enterprise drivers in Ubuntu standard?

---

### Post by Michael_McKenney on 2014-09-18
[http://www.tyan.com/tech/driver_linux.aspx](http://www.tyan.com/tech/driver_linux.aspx) is the list of general Linux drivers for the archived boards.

---

### Post by matt_symes on 2014-09-18
Hi

> **Michael_McKenney said:**
> I installed Ubuntu 12.x from a DVD on the web server box.  I upgraded using the sudo apt-get dist-upgrade command or whatever sudo apt-get command did the distribution upgrades and told it to clean up after.   I don't know enough about Ubuntu to pin anything.  I mainly use Microsoft at work and home.  Ubuntu is just because I needed a easy web site my ISP would not care I had.   My main workstation will be Windows because of the CAD and Adobe products I run.  I also need Cisco Anyconnect to access the data center.  

I have always said that there is room in this world for more than just Linux although i do find some of the properiety OS makers practices questionable at best.

> I did consider using the command I found on one site to remove all but the newest revision

I would strongly advise keeping a minimum of 2 kernels.

> sudo apt-get remove --purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d')

I found sites with other commands to purge all kernels except the current one.  Once I backup everything a few times, I would do a destructive cleanup to remove all the old kernels.   The web site is over 130 GB of pictures and videos from all my trips around the world and other stuff.

That looks like it will remove kernels for you. Be careful running random commands from the Internet though ;)

 > dpkg -l | grep linux-image, I will run this tonight and see what comes up.

Post back the results if you need help removing them. I may not be around until tomorrow though; UK time.

Kind regards

---

### Post by Michael_McKenney on 2014-09-18
UK Time, which part?  Been to Ireland, Northern Ireland, London, and Dover.  We were married last year and spend 2 weeks on our honeymoon in Ireland and Northern Ireland in October.  

I would probably wait till my backups are working before doing anything like that.  Symantec Backup Exec only does the var/www files.  Bacula should backup everything in Ubuntu.  It will be nice to get a full backup of Ubuntu instead of just my Microsoft stuff.  Symantec only supports enterprise agents and they will not install on non-enterprise Linux.  

HP, Tyan, Supermicro, and IBM design hardware OS revisions for stability.  HP VMware ISOs are designed for our HP C7000 Blade Center and blades.  When dealing with server hardware you stick to the OS that it is designed for.   If it is not listed for that hardware, you buy new hardware.  Otherwise, no support.

---

### Post by matt_symes on 2014-09-18
Hi

> **Michael_McKenney said:**
> UK Time, which part?  Been to Ireland, Northern Ireland, London, and Dover.  We were married last year and spend 2 weeks on our honeymoon in Ireland and Northern Ireland in October.  

I'm based in Bristol in the south west of the UK.

[https://en.wikipedia.org/wiki/Bristol](https://en.wikipedia.org/wiki/Bristol)

I've been to both Northern and Southern Ireland on a number of occasions. It's a beautiful place.

BTW: London is not really representative of England. It's rather a microcosm all of it's own.

> I would probably wait till my backups are working before doing anything like that.  Symantec Backup Exec only does the var/www files.  Bacula should backup everything in Ubuntu.  It will be nice to get a full backup of Ubuntu instead of just my Microsoft stuff.  Symantec only supports enterprise agents and they will not install on non-enterprise Linux.

I here Backula is a world class backup system. Alan on TechSNAP has mentioned it a number of times.

I have never used it myself preferring to use rsync and clonezilla.

> HP, Tyan, Supermicro, and IBM design hardware OS revisions for stability.  HP VMware ISOs are designed for our HP C7000 Blade Center and blades.  When dealing with server hardware you stick to the OS that it is designed for.   If it is not listed for that hardware, you buy new hardware.  Otherwise, no support.

Agreed :)

Kind regards

---

### Post by Michael_McKenney on 2014-09-18
We are looking at going to Wales, England and Scotland in 2 years.  I want to get to Cardiff to see where Dr. Who and Torchwood are filmed.  I read a lot of good things about Bacula.  Too bad enterprise version was $2600 a year.

---

### Post by matt_symes on 2014-09-18
Hi

> **Michael_McKenney said:**
> We are looking at going to Wales, England and Scotland in 2 years.  I want to get to Cardiff to see where Dr. Who and Torchwood are filmed.  I read a lot of good things about Bacula.  Too bad enterprise version was $2600 a year.

I used to live and work in Cardiff and it is a great city.

You'll be looking to get to the millennium center and down by Roald Dall Plass. Take a wonder down castle street and see the castle and go shopping in the mall.

If you can get out of cardiff and take a trip to the Brecon Beacons or along the Pembrokeshire coast line.

You'll love it.

Blimey. I'm beginning to sound like a tour guide :)

Kind regards

---

### Post by Michael_McKenney on 2014-09-18
I will talk to you when we plan it.  A lot to see in Wales.  My friend said to go to the Tattoo in Edinburgh, Scotland.  I wonder how tomorrow's Yes vote will change things in Scotland for my trip?  Most England based tour sites that do Wales and Scotland skip a lot of Wales and Scotland to and keep you in England.

---

### Post by matt_symes on 2014-09-18
Hi

> **Michael_McKenney said:**
> I will talk to you when we plan it.  A lot to see in Wales.  My friend said to go to the Tattoo in Edinburgh, Scotland.  I wonder how tomorrow's Yes vote will change things in Scotland for my trip?  Most England based tour sites that do Wales and Scotland skip a lot of Wales and Scotland to and keep you in England.

PM me on the forums when you do plan it. I'll change my settings to e-mail notifications.

Your friends advise to go and see the tattoo sounds solid although i have never seen it myself so i can't comment too much.

To be honest i have seen more of Europe, Asia and South America than i have of Scotland. That is something i will rectify one day.

Kind regards

---

### Post by Michael_McKenney on 2014-09-18
I never met a bottle of whiskey or scotch I did not like.

Any tips on dual booting setup with Ubuntu?  XP x64 SP2 is configured.  I was going to boot into Windows and remove partitions first.

---

### Post by matt_symes on 2014-09-18
Hi

> **Michael_McKenney said:**
> I never met a bottle of whiskey or scotch I did not like.

You're in for a treat on your holiday then. Both Scotland and Ireland.

Have you considered...

[http://www.jamesonwhiskey.com/uk/tours/oldjamesondistillery](http://www.jamesonwhiskey.com/uk/tours/oldjamesondistillery)

There are similar tours in Scotland as well i believe.

> Any tips on dual booting setup with Ubuntu?  XP x64 SP2 is configured.  I was going to boot into Windows and remove partitions first.

Personally, i would be tempted to boot into windows and use the windows tools to shrink the main windows partition creating some space after the partition and before the end of the disk.

I would then install Ubuntu into that vacated space. I think that may minimise any risk.

Kind regards

---

### Post by Michael_McKenney on 2014-09-18
I will look at the partitions tonight in Windows.  I know drive 0 has XP x64 drive C: on it.  I think it also has Drive E: with Symantec.  The other two drives were copies of the Firewall 800 drives to improve backup performance of them.  The firewire 800 drives are for Photoshop to render faster.  I used one as source and one as target.  I could process 60+ pictures per minute from RAW to Jpg with 3 auto filters applied.

---

### Post by Michael_McKenney on 2014-09-19
Drive 0 is a basic partition with C: and E: completely filling it.  I can't change it to Dynamic to shrink it because of Symantec.   So I have Drive 1 and 2 each 500GB that are not used.  I can install Ubuntu on them.

---

### Post by matt_symes on 2014-09-19
Hi

> **Michael_McKenney said:**
> Drive 0 is a basic partition with C: and E: completely filling it.  I can't change it to Dynamic to shrink it because of Symantec.   So I have Drive 1 and 2 each 500GB that are not used.  I can install Ubuntu on them.

That sounds like a good plan. As you mentioned earlier, remove the XP drive from the chassis just to be safe.

Kind regards

---

### Post by Michael_McKenney on 2014-09-19
I used Synaptic to remove all old Linux-Images up to 3.11.xxxx.  So I have 6-8 of 3.11 and 3.13 each.  Can I get rid of 3.11 and most of 3.13.

---

### Post by oldfred on 2014-09-19
I normally keep just a couple of kernels and when it builds to 3 or 4 delete back to just 2. 

If kernels are still in dpkg and recognized as installed, I prefer to use synaptic. If from previous installs they may not be recognized and then you need to just delete. If you use rm (very carefully) they will be gone, but if you Nautilus then they are moved to root's trash and that can be difficult to house clean.

       Determine your current kernel:
uname -a
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

Command line:

 cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.8.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.8.0-{17,18,19,21,22,23,24}-generic

---

### Post by Michael_McKenney on 2014-09-19
Synaptic made it easy to clear out 30+ Linux-images.  I might get rid of 3.11 and leave all the 3.13 versions for now.   I am debating on dual booting XP Pro and Ubuntu or removing the XP Pro hard drive connection and installing Ubuntu on the other two drives.  Every time I did dual booting with Linux and Windows in the past, it eventually broke the boot loader on Windows updates or Linux updates.

---

### Post by oldfred on 2014-09-19
I built my system in 2006 with two drives. I installed XP on one drive and intended to install Ubuntu on the same drive and use second as backup. But I made the best mistake ever and installed Ubuntu on the second drive.

Never had any issues as each was separate and could boot without the other. Had to shut XP down when I added a SSD and needed AHCI in BIOS to be able to run trim. Windows drive is still installed, os-prober still finds it until I turn off os-prober.

---

### Post by Michael_McKenney on 2014-09-19
Eventually XP Pro x64 and Symantec Backup Exec will go away.  How does the boot loader get affected.  It used to be the oldest OS boot loader was used.  Did you dual boot or just use F12 boot loader in CMOS to point to the drive to boot?

---

### Post by oldfred on 2014-09-19
I normally set default boot in BIOS to hard drive with grub for the Ubuntu install on that drive.
But since I have several drives and now have turned off XP, some of my test installs on sdc will default to installing grub to sda (my old XP) and I just let it. Then I can boot my working install by default or use one time boot key to choose sda to boot a test install. After a sudo-update grub in working install, I can boot test install from grub menu, but I have to turn off os-prober as I have too many old test installs and os-prober takes forever. I do add boot stanza manually into 40_custom to boot some test installs from my working install.

---

### Post by Michael_McKenney on 2014-09-19
XP Pro will never activate again, if it breaks as of April 2014.  I need it long enough to get Bacula working and tested.  I can't modify drive 0 to open up a partition on it because of Symantec.  Backup Exec will not run in a Dynamic drive configuration.   My six backup tape sets work with Symantec only.   I did backup my web site to my Firewire 800 drive.  I am also backing up My Documents to it to protect them.  My BIOS is set to boot Drive 0 with XP x64.  Once I get Bacula working, I will take my oldest tape set and use it with Bacula.   

Unplug drive 0.  I install Grub with Ubuntu on drive 1.  Once completed use BIOS to change boot drives.  So XP Pro and Ubuntu are distinct. 

How are the SSD benchmarks in Ubuntu.  I had mixed results in Linux with performance over Windows.  The Windows drivers are better optimized.

---

### Post by Michael_McKenney on 2014-09-21
I unplugged the Windows XP hard drive and installed Ubuntu 14.04 on the first 500 GB drive.  Ubuntu and Bacula 5 are installed.  I have not tried Bacula 7.0.5 yet.  Still working through the configuration of it.   The three tape drives were found and I did a tar test and all three erased.   I am looking for the Ubuntu GUI files.  bconsole does not see the tape drives.   I removed the file storage backup.  I only want the three tape drives.  
Storage jobs created for each tape drive.  Each drive does one box.

HPLTO3: Web Site Ubuntu
VXA12:  Windows 7 x64 workstation
VXA10: Tape Ubuntu box

Each tape drive is dedicated to one box.  Which forum would have more on Bacula?  I need to create the full backup jobs.

---

### Post by Michael_McKenney on 2014-09-21
bacula-dir.conf

---

### Post by Michael_McKenney on 2014-09-21
aaa

---

### Post by oldfred on 2014-09-21
Please use code tags on longer text output. Easy to add if in advanced editor with the # icon.

I can move thread to server sub-forum as tape drives are not often in any other forum.

---

### Post by Michael_McKenney on 2014-09-21
Thanks, move it to the correct forum.

---

### Post by oldfred on 2014-09-21
Moved to server sub-forum.

---

### Post by Michael_McKenney on 2014-09-22
Thank you for moving it and the code tagging suggestion.  I really appreciate it.

---

### Post by Michael_McKenney on 2014-09-22
anyone get Bacula working even with a hard drive based backup.  I would like to see the bacula-sd.conf and bacula-dir.conf.

---

### Post by Michael_McKenney on 2014-09-23
I removed all the extra stuff from bacula-sd.conf and bacula-dir.conf and only put in my settings.  I can now see the three tape drives.  Tonight, I setup the jobs.  I had to add my worksgroup to samba and configure the hosts file for the three workstations.  Bacula uses FDQN names instead of IP addresses.  So you need hosts or dns.

---

### Post by Michael_McKenney on 2014-09-24
The first job is setup.  I am now getting password errors.  What is strange is it tells me the password that is be reported and one it is looking for.  Not a great security thing.  I also saw the install password in simple text in a debug file.

---

### Post by Michael_McKenney on 2014-09-24
Important commands to configure Bacula

---

### Post by Michael_McKenney on 2014-09-24
What is not currently working is connecting to the three tape drive storage daemons.  I will work on it tomorrow.

---

### Post by Michael_McKenney on 2014-09-24
Here is the list of the devices.  Eventually I will see if I can get other devices working with Bacula

---

### Post by Michael_McKenney on 2014-10-04
I am ready to upgrade to 5.2.13 before going to 7.x.x.   With Matt's help, we did a test compile and installation of 5.2.13 yesterday.   Today, I will upgrade 5.2.6.

1.) Created all my individual tape jobs to allow tapes to overwrite each time.  
2.) Cleared out the old jobs not needed
3.) Removed all test volumes for the overwrites to happen
4.) New Intel NIC helped performance over the Nvidia on board NICs.   My Nvidia NIC Windows Symantec backup speed was 1630 MB/min.  The Intel NIC on Ubuntu Bacula was 2200 MB/min.  
     a.) Looking at increasing the buffers so I can run three concurrent jobs faster.   I have 3 GB+ of RAM available.

I will post my configuration once everything is working properly on 5.2.13.

---

### Post by Michael_McKenney on 2014-10-06
Installed the Windows 7 client and setup the jobs to back it up.  Performance is slow.  I am tweaking the Maximum Block Size and Maximum Network Buffer Size to increase performance on the drives.  I changed the NIC buffer settings.   

In order to get Bacula to do concurrent jobs, I need to configure SSL TLS support.  Created my first SSL Cert.  Still reading the section on reinstalling with SSL TLS support.

---

### Post by Michael_McKenney on 2014-10-06
I set the NIC buffers to 512 and 128.   Maximum Network Buffer Size of Bacula client and storage to 32768, A note said Windows does not handle more than 32768.   I am trying to remember what I set Symantec to 32 high water level and something else.

---

### Post by Michael_McKenney on 2014-10-07
First Windows 7 backup 200 MB/min+.  It was over 640 MB/min in Symantec.  I am going to get the latest Realtek driver for the motherboard NIC and see if that helps.  I am using the Microsoft driver.  If that does not work, another $40 Intel PCIe NIC for my Windows 7 workstation.  I did a iperf test,  441 Mbps.  I know it is not the hard drives.   My workstation has SAS RAID.  LSI Logic 8708EM2 128 MB battery cached controller and 15K SAS drives.  I use the LSI Logic drivers and firmware.  Benchmarks are 1.097 GB/s cached reads and 850 MB/s cached writes.  It is definitely the NIC causing this issue.   I found a user that said the new Realtek drivers really improved performance.   The Intel NIC on my Ubuntu web site workstation really helped performance.  So it is an option for $40.

---

### Post by Michael_McKenney on 2014-10-07
Working on tray monitor.  Getting unable to authenticate console.  Must be password

Error in Authentication.c:415 Unable to authenticate console "ubuntu-mon" 192.168.0.xx 36131.

---

### Post by Michael_McKenney on 2014-10-09
I found a posting from years ago on my VXA-2 that I made.  That was what Exabyte recommended.  I might play with it this week.  Last night's backup of Windows 7 took 7.5 hours.  It was 2.5 hours before.  

block size: 64K
buffer size: 1024K
buffer count: 10
high water count: 0

---

### Post by Michael_McKenney on 2014-10-17
At a standstill on backing up my Windows 7 workstation.   Performance is bad.  7+ hours to backup.  I tried setting up spooling the data to the tape server drives first.  Getting fatal errors and permission errors.   I added my 2nd hard drive to the Ubuntu Tape server.  Created a 456GB partition for the 400GB spool.   I took ownership of the Backup partition and can get to /media/Michael/backup on 2nd drive.  I can create a file and directory.  I added my group Michael to the permissions.  I might see if bacula group is needed.   Exabyte drive performance is bad.   I have been looking for a way to backup two computers to the HP LTO 3 drive on the same tape job.

---

### Post by Michael_McKenney on 2014-10-20
Upgraded to 7.0.5 and still working on it.

---

