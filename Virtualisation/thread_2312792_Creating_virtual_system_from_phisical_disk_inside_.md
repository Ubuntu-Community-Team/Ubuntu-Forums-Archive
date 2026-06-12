---
title: "Creating virtual system from phisical disk inside VirtualBox in Xubuntu"
date: 2016-02-07
forum: Virtualisation
---

### Post by mark253 on 2016-02-07
Hello,  
 I have 3 physical disk
 /dev/sdd      - disk were I have Xubuntu 14,04 installed and were MBT/Grub is

 /dev/sdc       - disk were Windows 7 is installed
 /dev/sdb       - disk used for Windows 7 data (user data)
 

 

 I am trying to create in Virtual-box run on Xubuntu a virtual system that will be my Windows 7 system from sdc disk.  
 As far as I know I have to first create a .vmdk file which will be link to my GRUB and than I will be able to boot a virtual machine from physical ssd.  
 As far as I know I need to create file using command  
 VBoxManage internalcommands createrawvmdk -filename
 but I have problem with making it. I read the forum, but usual people describe slightly different problems.

---

### Post by TheFu on 2016-02-07
What is the hostOS?
What is the OS to be virtualized?
What type of license is the Win7?  Some are tied to specific hardware and cannot run inside a VM.

---

### Post by MAFoElffen on 2016-02-07
Refer to [VirtualBox Manual]("http://www.virtualbox.org/manual/ch09.html#idp15871152"), Chapter 9 "Advanced Topics", Section 9.9 "Advanced storage configuration", Subsection 9.9.1 "Using a raw host hard disk from a guest" ... where is starts out that section with this warning:
> 
**Warning**
*Raw hard disk access is for expert users only. Incorrect use or use of an outdated configuration can lead to total loss of data on the physical disk. Most importantly, do not attempt to boot the partition with the currently running host operating system in a guest. This will lead to severe data corruption.*

Like TheFu hinted upon-- what is more common is to convert a hard-machine into a virtual guest.

---

### Post by mark253 on 2016-02-08
The Fu 
Host is Xubuntu 14.04, I want to virtualise a Windows 7, I have licence for Windows 7 pro 64bit.

MAFoElffen thank you for link. I as the question here because I think "the experts" are here. What exactly do you mean by "converting hard-machine into virtual guest" ?

---

### Post by TheFu on 2016-02-08
I've looked for notes on what I did. Cannot find them. Sorry.

Virtualizing Windows7 that came **with** the machine is often impossible because MSFT ties the Windows license to the hardware (OEM pre-installed versions). It checks for the specific BIOS + HW and refuses to boot/install onto any machine without that BIOS.  A virtualized environment will have a different BIOS than what a physical machine has. The best way to know is to take the installation media for that system and install it fresh into a VM. If that works and it doesn't complain about the license, then the effort to move a previously installed Windows into a VM will probably work. Do not activate the license until you are positive the setup/migration is working.

As MAFoElffen's link says, it is a non-trivial thing and someone without lots of experience in virtualization will almost always fail to accomplish the tasks necessary the first few times.  There are many choices for how to accomplish this goal. IMHO, using the previously installed Win7 OS as it is on the disk is the most dangerous and hardest.  I've never done that. Also, moving it from physical to virtual took me at least 5 attempts before it worked.

I have moved a "Retail License" of Windows7 from one VM environment to another. In my situation, the install is running Windows Media Center and had years of "already recorded" data that I didn't want to loose.  Doing a fresh installation was very possible, if I elected to loose that data.  There are a few key steps and many minor ones that I've forgotten, but were obvious to me at the time (I've been doing virtualization since the 1990s and Unix since the early 90s, but have stayed away from anything complicated on Windows since 2006).  It is unclear to me how obvious these extra things would be to other people. 

I'll try to explain the main parts that I vaguely recall - 3 yrs later (now).

Ok - so the key things are:
a) boot into Windows and tell it we're planning to move the license to another system. This preparation must be the last thing done inside the physical Windows OS. Never boot the machine again, since Microsoft counts the times each license does this and I think 3 is the limit. **SysPrep** is the name of the Microsoft tool that modifies the current install - basically, it tells Windows that at the next boot, it should reconfigure all the drivers for the new system like it was a new machine.  To my knowledge, only Retail licensed Window and bulk licensed Windows (used in corporate environments) can do this.  Pre-installed with PC licenses cannot.  At the first reboot on the new "system" (a VM in your case), a new Windows userid must be created. I was not allowed to use the existing userid during this driver-update-part, though it was still on the system and could be used later.  Any settings related to hardware were lost - video drivers, printers, networking, firewall rules stuff like that.  The drivers for the physical cards and chips inside the real PC mean absolutely nothing. All a VM sees is the virtualized HW created by the hypervisor, so removing the old drivers for the old hardware was necessary.

b) create a virtual HDD from the physical HDD partitions. I did that with KVM and the **qemu-img** tool and **ddrescue** to move the bits from the real HDD partition into the virtualHDD.  Ensure the virtual machine settings are all tuned as you want, since when Windows boots and begins re-re-installing drivers, it will see the new, virtualized, hardware provided by the hypervisor.  You can use VirtualBox, KVM, QEMU, VMware ESXi, Player, Workstation or Xen as the hypervisor. You cannot use LXC, Docker, openvz or any paravirtualization OR "container" type virtualization for Windows. Tuning the settings for Windows is an outside exercise. Definitely practice a few times before moving your "real" Windows install over. 90%+ of native performance should be possible. There are tuning guides for each hypervisor and Windows. The default settings from most of the hypervisors are not sufficient, IME.  [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) is mine.

c) Boot Windows on the vHDD inside the hypervisor, and go through the mini-setup to have it recognize the new virtualized hardware around it. You'll want to install any hypervisor-specific drivers.  Virtualbox has "guest additions", KVM has GXL video drivers, stuff like that.

Let me google a little to find the name of that MSFT tool .... [https://technet.microsoft.com/en-us/library/cc766514%28v=ws.10%29.aspx](https://technet.microsoft.com/en-us/library/cc766514%28v=ws.10%29.aspx) **SysPrep**. That's it. Added the name above.

15 yrs ago, VMware had a tool to migrate Windows VMs from physical to virtual environments. Last time I looked for it, it was a hassle to find and seemed really out-of-date.  I ended up using SysPrep and most things were fine.  My use of Windows is extremely limited - fewer than 20 programs are installed that aren't directly included with Win7 from MSFT. The more complex the Windows environment is, the harder this conversion is likely to be.  For example, I've always forced Windows to only have a single partition for the migration. The data partition(s) were removed before any migrations happened, then added back later, post-migration. Also, I avoid connecting hardware of any sort directly to Windows. No USB disks, no PCI cards - none of that stuff. Anything connected over the network is fine, since those aren't going anywhere. For example the HDHR TV tuners on my network and the drivers for those all had to be re-installed after the Windows migration. SysPrep removed them, sadly.

Since this is an expert-level task, hopefully, I won't get into trouble suggesting that the manpages for every command used be checked carefully to ensure any needed/wanted options are invoked.  The qemu-img tool is very impressive, so is vboxmanage. BTW, the resulting vHDD container format matters not if you just want to run the resulting VM.  VDI, VDMK, raw, qcow2, qcow - don't really matter, but you'll want to review the capabilities of each before you end up with one that isn't what you like. qcow2 has some very interesting compression and snapshot capabilities (similar to LVM) that are worth consideration.  OTOH, switching between these at a later time isn't too hard - qemu-img and vboxmanage can both do it. The main issue for me was finding an extra 60G of storage to move an entire Win7 install around. 

Good luck. Take notes, so when something doesn't work, you can post the exact steps (copy/paste the exact commands and errors somewhere to get help).

Hope this has been helpful.

---

### Post by MAFoElffen on 2016-02-08
As TheFu mentioned, it is a PITA. As he also mentioned, if you have the install media, migrating from old to new would then be easier, via a fresh install into a new image, reading the old disk as a host shared resource. As a data disk, instead of as a bootable system disk. NTFS is one of those file system formats that most any OS can read... and mount. It could then be left inside NTFS or migrated to another filesystem.

---

