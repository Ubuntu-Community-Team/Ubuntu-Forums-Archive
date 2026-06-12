---
title: "Help: Install Ubuntu Desktop 16 on VBox 5 hosted on CentOS 7.2?"
date: 2016-05-04
forum: Virtualisation
---

### Post by louarnold on 2016-05-04
I wanted to try Ubuntu Desktop - currently at V16...
Oracle Virtual Box was suggested as a way forward. I installed VBox 5.0 on my CentOS 7.2 (64bit) system. There is lots of disk space, but only 4 GB of memory.

I tried creating a guest system, but read some things that I didn't understand, and wanted some help getting started, at the very least.

So far I can start VBox to bring up its first GUI screen, but that's about it. I must add that I know very little about virtualization software.

Regards,
Lou.

---

### Post by QIII on 2016-05-04
[https://www.virtualbox.org/](https://www.virtualbox.org/) should have everything to do with your problems, if you look at the column on the left and click "End-user docs"

Most of it will be very confusing.  Don't expect any of it to be crystal clear.  But if you read through it you will probably start to put together a series of more direct questions to ask.

Trying to recreate the entire documentation here would be beyond the scope of this sort of Forum.

We'll be here to answer.

---

### Post by ajgreeny on 2016-05-04
I accept QIII's comments above, but as I **do** use VBox a lot for many VMs, not all at the same time, here is what I do.

1 - Download the ISO image file of the OS, but do not burn to DVD or USB.
2 - In the VBox manager window click on New, name the OS and group it as 32 or 64 bit Ubuntu. Click "Next"
3 - Create a new Virtual disk.  The defaults for ram and disk size will probably be too small; I always use up to half my machine ram for each VM, make it fixed size at 18GB, and have always made a vdi filetype.
4 - Now with the new disk created click Start, and in the screen that appears click the dropdown-box and point to the ISO file on your hard disk.
5 - The normal bootup procedure for a live disk will now start and from that you can install the virtual OS to the virtual disk you created. Let it do the default install to the whole disk.
6 - Once installed you can restart in the usual way.  As there is no disk to eject as there would be with a DVD, the shutdown/restart will come to a halt and you will need to hit Enter to continue to the final boot to the new VM.

Simple, quick, and in many ways a lot less difficult that many believe.
I hope this helps you start, but come back again for more help if needed.

---

### Post by louarnold on 2016-05-04
Ah, thats the info I needed.  Thank you. There were many questions from the online tutorials, and there are different versions than those named. I will try these steps and will get back to you. I am completely ignorant on this topic.

---

### Post by louarnold on 2016-05-05
Hate to admit it, but I'm stuck on step 1. I've been through several pages on the Ubuntu.com website. But I haven't seen a way to actually download an ISO. I do see downloads of installers for network installation and comments about buying a Ubuntu DVD and then booting the system from that, but there isn't actually a download file either. (I understand that the bootable Ubuntu DVD is an alternative to installing Ubuntu on VBox.)

---

### Post by howefield on 2016-05-05
Try

[http://releases.ubuntu.com/xenial/](http://releases.ubuntu.com/xenial/)

---

### Post by louarnold on 2016-05-05
Well, I'm not sure how you got to that page, but that's past now. I downloaded the torrent file and the Desktop 16.04 amd64 image. Download time via torrent was 20 minutes.

For step 2, my total RAM is 3.75 GB, so I should use about half of that (1.8 GB)  for the VM RAM?
For the virtual disk, It recommends 8 GB, and offers no way to change that. So what then?

The Hard disk set-up screens seem to have changed, but seem easy enough. I will try for the 18 GB / VDI image/ and get back to you if I get stuck.

I've gotten to the VM CD/DVD drive settings, where the tutorial (docs,oracle.com --- Creating a new virtual machine in Virtual Box) it tells me to pick Storage> IDE Controller...
I note there is also a SATA Controller option. The actual machine has no IDE devices. So should I pick only the SATA controller?

---

### Post by howefield on 2016-05-05
> **louarnold said:**
> For step 2, my total RAM is 3.75 GB, so I should use about half of that (1.8 GB)  for the VM RAM?

I don't think it will allow more than half the ram to the guest, but with the total that you have host and guest having half each sounds about right.

> For the virtual disk, It recommends 8 GB, and offers no way to change that. So what then?

The Hard disk set-up screens seem to have changed, but seem easy enough. I will try for the 18 GB / VDI image/ and get back to you if I get stuck.

18GB will be fine, you probably need at least 8GB but depends on what you want to do with the installation. You have the choice of fixed or dynamic disk creation, using a dynamic disk will mean that your guest will start small and "grow" up to that amount of space but not exceed it, with a small speed trade off.

> I've gotten to the VM CD/DVD drive settings, where the tutorial (docs,oracle.com --- Creating a new virtual machine in Virtual Box) it tells me to pick Storage> IDE Controller...
I note there is also a SATA Controller option. The actual machine has no IDE devices. So should I pick only the SATA controller?

I'd take the default knowing that the settings can be changed after the fact.#

PS. Thread moved to the "*Virtualisation*" forum.

---

### Post by louarnold on 2016-05-05
OK, picked the IDE controller, no IDE device on this machine. IDE Controller set to the downloaded Ubuntu ISO file on the hard drive. SATA controller defaults to name of the VM UbuntuDT16. O)n Now I get the following errors and attempt a few things:
-------------------
VB Manager > Start 
Produces:
------------------------
```

VirtualBox Error
Failed to open a session for the virtual machine UbuntuDT16.
The virtual machine 'UbuntuDT16' has terminated unexpectedly during startup with exit code 1 (0x1).
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: MachineWrap
Interface: IMachine {f30138d4-e5ea-4b3a-8858-a059de4c93fd}
-------------------------
Also:
VBox Error in suplibOsInit
Kernel driver not installed (rc=-1908)
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing
'/sbin/rcvboxdrv setup'
as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT. 
-----------------------------
[root@shoe ~]# /sbin/rcvboxdrv setup
Stopping VirtualBox kernel modules                         [  OK  ]
Recompiling VirtualBox kernel modules                      [  OK  ]
Starting VirtualBox kernel modules                         [  OK  ]
[root@shoe ~]# 
-------------------------------
Next try: Closed VBox
Restarted VBox from Centos menu. Software went straight to VBox manager. I clicked Start button. Got another error:
Failed to open a session for the virtual machine UbuntuDT16.
AMD-V is disabled in the BIOS (or by the host OS) (VERR_SVM_DISABLED).
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: ConsoleWrap
Interface: IConsole {872da645-4a9b-1727-bee2-5585105b9eed}

```
----
Stumped at this point.
Back in a few hours. 3 pm my time (GMT-5).

---

### Post by louarnold on 2016-05-05
Back again...
I was thinking that these errors might be caused by the IDE controller being pointed to the Ubuntu ISO file rather than a DVD drive.
Otherwise, there seems to be a BIOS problem (in VERR_SVM_DISABLED).
Any better guesses, :D?

---

### Post by ajgreeny on 2016-05-06
In all my VMs except for WinXP the main disk with the attached vdi is a SATA disk; for some reason the WinXP is an IDE disk.

I have no idea why that is the case unless XP was unable to use SATA disks.  I know so little about Windows any more, and use it so infrequently that I can not help further in that way, but I do know that I never made the choice of SATA for my various Linux virtual machines; it was the default when I installed in the manner I showed you in post #3.

Also regrettably I am not conversant with the VBox error codes, so I have no idea about those that you are seeing.

---

### Post by louarnold on 2016-05-06
The AMD-V problem has to do with the HP BIOS. Enable Virtual Technology in the BIOS (under OS Security). Or in the VM Settings > System > Acceleration > Hardware Virtualization: Select Disable VT-x/AMD-V. The VM then started, but somehow I have a problem with capture of the keyboard and mouse.

---

### Post by louarnold on 2016-05-06
Some progress: The AMD-V error solved by a BIOS setting change.
Ubuntu is booting, but still gives two problems:
1) A "piix4 smbus..." error that I assume I can ignore - from other posts on the problem.
2) The Ubuntu screen turns to vertical lines of all colours. This doesn't seem to change with Nested paging, etc. changed. Not sure if its a Ubuntu problem or VirtualBox problem.
Anyone have answers.

---

### Post by louarnold on 2016-05-11
Thnaks to howefield and ajgreeny for your help. I'm moving to the VBox forum, since this seems like a VBox problem more than Ubuntu. There are older tutorials and posts there that are quite relevant, but don't seem to be solutions, but someone may have them solved by now.
Good virtualizing to you all.

---

### Post by MAFoElffen on 2016-05-12
Note: If you go to EDIT on post #9, you will see how I added code tags to your output. Please use code tags to wrap all output and commands in posts...

If you look at your error, it complains of a missing kernel module for VirtualBox.in your CENTOS host system.
```

# substittue dnf for yum if appropriate by CENTOS version
su -c "yum search dkms"

```
If not installed:
```

su -c "yum install dkms" && su -c "yum install virtualbox-dkms"
# next is the path for CENTOS 7
su -c "/usr/lib/virtualbox/vboxdrv.sh setup"

```
In RHEL Branches: The dkms package is a dependency of virtualbox. But the rhel virtualbox package does not mark it as such during it's install, so does not include it's installation. It assumes you already have that package installed previously.

If you would have added switches to auto-resolve the dependencies on the original vbox install, it would have resolved the prerequisite dependent packages:
```

yum -y PackageName
rpm -q PackageName
dnf libsolve PackageName

```
One other note, in VirtualBox, a step left out of Al's post... when you create a new VM, select an OS type and version (Linux, Ubuntu, 14.04). This installs the hypervisor's VM Guest "software virtio files" for the OS type... Since 16.04 is too new your vb 5.0, use whatever is the highest for Ubuntu (14.04).

---

### Post by louarnold on 2016-05-12
To MAFoElffen:
Code tags: Understood.
Versions: VBox vs Ubuntu releases understood..

Missing kernel module for VirtualBox: I understand, but your suggestions don't work. The search for dkms and VirtualBox-dkms fails.
I have The rpmforge, and OracleVirtualBox repos.

Both those repos are enabled.
```
[root@shoe ~]# yum install dkms
Loaded plugins: fastestmirror, langpacks, refresh-packagekit, remove-with-leaves
Loading mirror speeds from cached hostfile
 * base: centos.mirror.rafal.ca
 * extras: centos.mirror.rafal.ca
 * fasttrack: mirror.netflash.net
 * nux-dextop: mirror.li.nux.ro
 * nux-misc: mirror.li.nux.ro
 * rpmforge: mirror.us.leaseweb.net
 * rpmforge-extras: mirror.us.leaseweb.net
 * updates: less.cogeco.net
No package dkms available.
Error: Nothing to do
[root@shoe ~]# yum install virtualbox-dkms
Loaded plugins: fastestmirror, langpacks, refresh-packagekit, remove-with-leaves
Loading mirror speeds from cached hostfile
 * base: centos.mirror.rafal.ca
 * extras: centos.mirror.rafal.ca
 * fasttrack: mirror.netflash.net
 * nux-dextop: mirror.li.nux.ro
 * nux-misc: mirror.li.nux.ro
 * rpmforge: mirror.us.leaseweb.net
 * rpmforge-extras: mirror.us.leaseweb.net
 * updates: less.cogeco.net
No package virtualbox-dkms available.
Error: Nothing to do
[root@shoe ~]# yum --enablerepo rpmforge install dkms
Loaded plugins: fastestmirror, langpacks, refresh-packagekit, remove-with-leaves
Loading mirror speeds from cached hostfile
 * base: centos.mirror.rafal.ca
 * extras: centos.mirror.rafal.ca
 * fasttrack: mirror.netflash.net
 * nux-dextop: mirror.li.nux.ro
 * nux-misc: mirror.li.nux.ro
 * rpmforge: mirror.us.leaseweb.net
 * rpmforge-extras: mirror.us.leaseweb.net
 * updates: less.cogeco.net
No package dkms available.

```

---

### Post by louarnold on 2016-05-13
Changed to the Ubuntu 14.04 Desktop and all worked. See the VBox forum at ([https://forums.virtualbox.org/viewtopic.php?f=3&t=77656](https://forums.virtualbox.org/viewtopic.php?f=3&t=77656)).
Still have a bit of tuning to do on VBox.

---

