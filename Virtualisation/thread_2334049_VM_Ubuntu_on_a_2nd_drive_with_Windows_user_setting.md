---
title: "VM Ubuntu on a 2nd drive with Windows user settings"
date: 2016-08-15
forum: Virtualisation
---

### Post by mfrp9 on 2016-08-15
Hello, this is what I'm trying to do.

I have 1 SSD that is for my main Windows installation and a game here or there. This is only 128 GB so space is precious.

I have a 2nd drive, 500 GB, that I moved my User settings and other applications. I'd like to run Ubuntu in a virtual machine (not dual-boot) and install it on this hard drive.

I have created the virtual machine for Ubuntu, allocated around 50 GB for the installation and fired it up. I'm presented to try Ubuntu or install Ubuntu.

OK, I want to install, then I am presented with two more options. Erase disk and install Ubuntu or Something else. Now I don't want to format my 2nd drive as I have Windows User data on it and other application data.

When I try to create partitions myself and Install Now, a message "No root file system is defined" is displayed.

How can I install Ubuntu on the 2nd drive (not dual-boot) and keep the Windows data on it?

Now that I think about it, it came to me just as I was typing this, the option "Erase disk and install Ubuntu" only refers to the virtual disk since I am running it via the Virtual Machine, so this option would still keep my Windows and other data on this hard drive safe, correct?

---

### Post by &amp;KyT$0P# on 2016-08-15
Yes, if you created the virtual hard disk the normal way it's just another file on your physical drive.

If you're still concerned that you may have done something **very wrong and out-of-the-way** and actually given the VM your physical drive, check the size of the disk it's seeing and look at whether it matches the virtual hard disk size you gave it or your physical drive's size.  But, again, it would take a pretty severe and very convoluted mistake, so it's extremely unlikely to have happened to you.

---

### Post by deadflowr on 2016-08-16
> Now that I think about it, it came to me just as I was typing this, the option "Erase disk and install Ubuntu" only refers to the virtual disk since I am running it via the Virtual Machine, so this option would still keep my Windows and other data on this hard drive safe, correct?
Correct.
The virtual machine is just another file within Windows, a rather large file, but a file nonetheless.
As stated above already.

But for what it's worth, when you tried manually creating the partitions, you did not set the mount points.
When you use Ubuntu's *something else* option in the installation phase, you set the size and the file system type 
(Ubuntu's default is ext4, but the *something else* option lets you choose different if you want...)
then after setting the size and the file system type, you have to set the mountpoint. 
The mountpoint option is blank so you have to toggle a dropdown to set it.
(The first option is root, or /)
This will clear that no root file system defined set error.

Again, though, that's a for what it's worth.
If using the Main installer option; Erase and Install Ubuntu, then no need to worry about that.

---

### Post by howefield on 2016-08-16
Moved to the "*Virtualisation*" forum for a better fit.

---

### Post by MAFoElffen on 2016-08-17
The point not mentioned, to ensure ask that would be for me to ask if you have installed some kind of vierualization software yet-- such as Hyper-v, VMWare Pkarer or Workstation, or VirtualBox. The next questions would be to ask how or what steps you took in creating your new VM Guest.

The thing is with a VM Guest install, common to most, you choose an option to create a new VM Guest > You can that guest a name > You might tell it what kind of OS you will be installing > You tell it from where and what form the install media is > you tell it how big a virtual hard disk image file you wanted to use > you tell it how much memory to use > you might review and change some of the virtual hardware... and create the virtual machine to install to.

Then you start it for the first time and do the install... in that window of the VM Guest, running within your Host OS... That is virtualization, one OS being able to run witin your host OS.

If instead, you created a partition on your host...instead of within the virtualization hypervisor, within your virtual image file that you created... then you are doing something physical, instead of virtual. You mentioning that you "started out" by creating a partition, before telling us anything about the virtualization software you are using... makes me a bit nervous.

Because the question that would have brought up would have been on ensuring the storage of the virtual machine guest image file on your second drive, in your VM image user directory, right?

So please answer in your own words what you have done so far...

---

### Post by mfrp9 on 2016-08-17
I am using Virtual Box. I did what you described in your second paragraph with the VM Guest Install. All is well now!\\:D/

---

