---
title: "Backup Suggestions for XFS/LVM/KVM server."
date: 2010-01-20
forum: Server Platforms
---

### Post by batonac on 2010-01-20
My company has recently acquired a very nice server from dell.  I convinced them to give Ubuntu server a try, which we did, and everyone here is very happy with how it is working.

I installed Ubuntu server 9.10 on the machine using LVM to handle the filesystem, XFS as the default filesystem type, and the "virtual machine host" option selected during the install, which installed KVM.  I then used KVM to install virtual machines.  

Currently I have three virtual machines running on the host.  One is Windows Server 2008 R2, which hosts Quickbooks, and the other two are Ubuntu Jeos 9.10, one acting as a MySql database server, and the other as a ResourceSpace image server.

For administration, I installed the x-window-system-core, xdm, and lxde-core packages, with a few other graphical administration programs that can be accessed from the lxde desktop.

The server specs are as follows:
[LIST]
[*]E5520 Xeon Processor, 2.26GHz 8M Cache, Turbo, HT
[*]8 GB Memory (4x2GB), 1333MHz Dual Ranked RDIMMs
[*]Four 250GB 7.2K RPM SATA 3.5" Hot Plug Hard Drives
[*]RAID 10 for PERC 6/I SAS RAID Controller (500 GB total storage available)
[/LIST]

The filesystem is set up as follows:
[LIST]
[*]sda1 given 200MB, formated as ext3, assigned to /boot
[*]sda5 given 20GB, formated as Linux LVM, assigned to LVM PV "LinuxFS"
[*]sda6 given 480GB, formated as Linux LVM, assigned to LVM PV "VirtualMachines"
[/LIST]

LVM is setup as follows:
LinuxFS:
[LIST]
[*]root given 2GB, formated as xfs, assigned to /
[*]usr given 3GB, formated as xfs, assigned to /usr
[*]var given 1GB, formated as xfs, assigned to /var
[*]tmp given 500MB, formated as xfs, assigned to /tmp
[*]home given 1GB, formated as xfs, assigned to /home
[*]swap given 4GB, formated as swap
[/LIST]
VirtualMachines:
[LIST]
[*]QuickBooksServer given 20GB, assigned to KVM virtual machine (running Windows Server 2008 R2)
[*]DatabaseServer given 20GB, assigned to KVM virtual machine (running Ubuntu Jeos 9.10 & MySQL)
[*]ImageServer given 200GB, assigned to KVM virtual machine (running Ubuntu Jeos 9.10 & Apache)
[/LIST]

Now, all that just goes to say, I love the setup, it's working great (actually awesome), but the folks here are concerned about backing up the system.  I understand that LVM Snapshots are a very reliable way to go, but I can't seem to find any GUI program that will take care of the process for me.

The current preferred method here is to take the 1 TB portable hard drive out of the safe, plug it into the server, perform a backup, and return the hard drive to the fire safe.  We want this backup to be performed about once a week.

I am quite comfortable in the Linux console, but the employees who will be in charge of the backup are not.  Even a script that they can click on the desktop that will perform the task and then notify them when it has completed would be fine, but what is the best way to do this?

Your suggestions are very appreciated.

---

### Post by Xianath on 2010-01-21
LVM snapshots are not backup. A snapshot volume only stores the delta (changes) since it was created. This is convenient for a point-in-time, well, snapshot, but if your original data is lost, you can't restore from a snapshot. A mirror volume is more like a backup, but given that you use XFS, you can just xfsdump to tape or other media. It is easily scriptable and has enough visual feedback to keep support folks at ease.

Another very cool option which will probably work very well in your case is to auto-trigger the backup script on plugging in the portable drive. Just make sure you DON'T do that when your server dies :) Here are some tips:

[http://ubuntuforums.org/showthread.php?t=989780](http://ubuntuforums.org/showthread.php?t=989780)
[http://andri.dk/tech/linux/usb-backup](http://andri.dk/tech/linux/usb-backup)
[http://www.virtfoundry.com/blog/?p=61](http://www.virtfoundry.com/blog/?p=61)

Google for "udev backup usb drive" or something similar to get more goodies. I'm sure one of them will work out great. Please let us know which one :)

Cheers,
Peter

---

