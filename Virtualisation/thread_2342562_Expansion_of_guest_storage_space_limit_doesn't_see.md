---
title: "Expansion of guest storage space limit doesn't seem to be working, what now?"
date: 2016-11-07
forum: Virtualisation
---

### Post by caraj on 2016-11-07
My virtual OS had a 25GB storage capacity. I expanded it to 100GB. The Virtualbox storage settings have it listed as 100GB, but when I run the guest OS (Windows 7), it still says 25GB.

---

### Post by howefield on 2016-11-08
Can you explain how you expanded the capacity ?

---

### Post by &amp;KyT$0P# on 2016-11-08
[https://ubuntuforums.org/showthread.php?t=2340877](https://ubuntuforums.org/showthread.php?t=2340877)

---

### Post by caraj on 2016-11-08
> **howefield said:**
> Can you explain how you expanded the capacity ?

 I used [the following tutorial:]("https://www.linuxbabe.com/virtualbox/how-to-increase-virtualbox-disk-size-for-dynamically-allocated-disks")

In this tutorial, I’m going to show you how to increase Virtualbox  disk size for dynamically allocated storage. This method will only work  if your virtual disk is in .vdi or vhd format. I also assume that your  host OS is Linux. If you want to know how to increase the size of a  fixed size disk, then read the next article.

 **Find Out If Your Virtual Disk is Dinamically Allocated**

 Open you virtual machine settings and click **Storage**  on the left pane. Select your virtual disk under Storage Tree. You can  see the information about your virtual disk on the right. You can see  that my virtual disk is dynamically allocated.
 [IMG]https://www.linuxbabe.com/wp-content/uploads/2016/02/ubuntu-Settings_011.png[/IMG]
 **BackUp Your Virtual Hard Disk**

 Before we increase the size of our virtual hard disk, it’s always a good idea to make a backup of it in case something go wrong.
 First, right click on the location line and copy the location of your virtual hard disk.
 [IMG]https://www.linuxbabe.com/wp-content/uploads/2016/02/Selection_012.png[/IMG]
 Then click the minus icon to remove the virtual disk from virtual machine.
 [IMG]https://www.linuxbabe.com/wp-content/uploads/2016/02/Selection_013.png[/IMG]
 Next open up a terminal on your host OS and run the following command to backup the virtual hard disk.
 cp /location-of-virtual-disk /location-of-backup-of-virtual-disk Repalce the location with the real location of your virtual disk. For example, I executed this command:
 cp "/home/matrix/VirtualBox VMs/ubuntu/ubuntu.vdi" "/home/matrix/VirtualBox VMs/ubuntu/ubuntu-backup.vdi" Note that because the location of my virtual disk contains space, so I  added double quotes around the location. Make sure your backup disk  name is different from the origial disk name.
 **Increase Virtualbox Disk Size For Dynamically Allocated Disks**

 Now you can use the vboxmanage comand to enlarge your virtual disk. The syntax is as follows:
 vboxmanage modifyhd /location-of-your-virtual-disk --resize size-in-MB Specify the new size in Megabytes.  For instance, I entered the following command to increase my virtual disk to 10GB.
 vboxmanage modifyhd "/home/matrix/VirtualBox VMs/ubuntu/ubuntu.vdi" --resize 10240 You can’t make your virtual disk smaller using this command.
 Now open your virtualbox settings to attach the virtual disk back to  your virtual machine. Click the plus icon, and select Add Hard Disk.
 [IMG]https://www.linuxbabe.com/wp-content/uploads/2016/02/Selection_014.png[/IMG]
 Choose your enlarged virtual disk. Once your added your virtual disk  back, you can check out the new size of it. You can see that my virtual  disk is now 10GB in size.

[COLOR=#ff8c00][SIZE=5]*I FOLLOWED THE ABOVE STEPS, BUT THEN WAS UNABLE TO FOLLOW THE BELOW ONES.[/SIZE][/COLOR]

**Use Gparted to Expand the File System of Your Guest OS**

 Although your virtual disk size is increased, your guest OS can’t use  all of them right now. So you need to boot your virtual machine from a  Live CD/DVD that contains Gparted to enlarge the file system of your  guest OS.
 To boot your virtual machine from a Live CD/DVD, follow these steps.
 Open you virtual machine settings and click **Storage** on the left pane. Under storage tree, click **Controller: IDE** then click the optical drive icon to add a Live CD/DVD image file. I use the ubuntu live ISO file because it contains Gparted.
 [IMG]https://www.linuxbabe.com/wp-content/uploads/2016/02/Selection_016.png[/IMG]
 Now click System on the left pane, in Boot Order, make sure Optical  is first on the list. Save your settings and start your virtual machine.
 [IMG]https://www.linuxbabe.com/wp-content/uploads/2016/02/Selection_017.png[/IMG]
 Now you are in a Live OS. Open Gparted program.
 [IMG]https://www.linuxbabe.com/wp-content/uploads/2016/02/Selection_018.png[/IMG]
 As you can see there’re 2GB of unallocated space. To use this  unallocated space, first disable swap partition. Right click on the  linux-swap partition and select **swapoff**.
 [IMG]https://www.linuxbabe.com/wp-content/uploads/2016/02/Selection_019.png[/IMG]
 Then right click on linux-swap partion and select **delete**. Next right click on the extended partition and select **delete**. Apply your changes.
 Now you can enlarge your root file system. After you enlarged your  root file system, shut down your virtual machine and boot it for virtual  disk. You should be able to use the extra spaced added.

---

