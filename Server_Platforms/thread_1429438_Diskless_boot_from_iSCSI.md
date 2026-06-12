---
title: "Diskless boot from iSCSI"
date: 2010-03-14
forum: Server Platforms
---

### Post by TheR on 2010-03-14
I am using diskless servers for my KVM servers. I actualy boot servers from USB keys which is enough because everything else is on iSCSI SAN.

Than I heard for iSCSI boot which is still not mature enough for ubuntu at the time (as I read).

So I wonder. Would it be possible and if how to make some kind simple initial boot from USB key, configure network adapters and than boot actual OS from iSCSI's target LUN like I boot all my virtual machines.


by TheR

---

### Post by stevemarfisi on 2010-03-14
iSCSI boot will work fairly smooth for Ubuntu servers - and desktops. Trick is to use PXE to bootstrap first, then chainboot to iSCSI. Here's how I did it with Double-Take's Flex software. You can use their target, or other iSCSI target. The Flex server can be Windows or Linux.
 
[COLOR=#1f497d][FONT=Calibri][FONT=Calibri][SIZE=3]1.[/SIZE][/FONT]       [/FONT][/COLOR][COLOR=#1f497d][SIZE=3][FONT=Calibri]Grab a **_SERVER_**-class variant of the Ubuntu installer. This is required, because only v9.10 Ubuntu installer allows direct access to iSCSI at the installation phase.[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][FONT=Calibri][FONT=Calibri][SIZE=3]2.[/SIZE][/FONT]       [/FONT][/COLOR][COLOR=#1f497d][SIZE=3][FONT=Calibri]Insert the CD / DVD into the workstation. Boot from it (we are not booting using Flex at this point because Ubuntu will not read in the iBFT parameters from Flex).[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][FONT=Calibri][FONT=Calibri][SIZE=3]3.[/SIZE][/FONT]       [/FONT][/COLOR][COLOR=#1f497d][SIZE=3][FONT=Calibri]Run the Ubuntu installer. At the  point of preparing the disks, there is a selection there that allows you to connect to iSCSI disks for partitioning and installation.[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][FONT=Calibri][FONT=Calibri][SIZE=3]4.[/SIZE][/FONT]       [/FONT][/COLOR][COLOR=#1f497d][SIZE=3][FONT=Calibri]Enter the IP address of the Flex Storage Server (FSS) or other iSCSI target . A list of available targets will be shown. Obviously, an FSS target disk will have to be created ahead of time. A disk of 5 -6 gb will be sufficient in size to hold a standard ubuntu-desktop installation. If using FSS, create this in EXCLUSIVE mode.[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][FONT=Calibri][FONT=Calibri][SIZE=3]5.[/SIZE][/FONT]       [/FONT][/COLOR][COLOR=#1f497d][SIZE=3][FONT=Calibri]Select the FSS disk you would like to install to, and proceed with partitioning. I had issues post-install with preparing partitions using LVM, so accept the default “guided disk” unless you really know what you are doing here. [/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][FONT=Calibri][FONT=Calibri][SIZE=3]6.[/SIZE][/FONT]       [/FONT][/COLOR][COLOR=#1f497d][SIZE=3][FONT=Calibri]Proceed with installation. Depending on  your installation source (CD or DVD), you may need to have your setup environment exposed to the internet, as the standard CD installation does not have local sources to the required packages for desktops. The *apt-get* that runs later will try to access the internet to grab packages, but will fail if not connected to it (it will not show errors if it fails to connect!).[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][FONT=Calibri][FONT=Calibri][SIZE=3]7.[/SIZE][/FONT]       [/FONT][/COLOR][COLOR=#1f497d][SIZE=3][FONT=Calibri]When done, do **_not_** reboot as instructed. Note that the Ubuntu server install will kick out the CD / DVD (or if in VMware, will disconnect it) at this point. You may need it reconnected / inserted for next boot in order to be able to read package lists.[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][FONT=Calibri][FONT=Calibri][SIZE=3]8.[/SIZE][/FONT]       [/FONT][/COLOR][COLOR=#1f497d][SIZE=3][FONT=Calibri]Prepare a Flex client for this target. Note from the FSS logs (or other iSCSI target logs) the name of the **_initiator_** IQN (not target IQN), and add this name to the Flex target configuration (first tab, properties). Assign the target disk to the client.[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][FONT=Calibri][FONT=Calibri][SIZE=3]9.[/SIZE][/FONT]       [/FONT][/COLOR][COLOR=#1f497d][SIZE=3][FONT=Calibri]Boot the client using Flex. You may see several iSCSI timeouts (shown as 03/02) before you connect to the target disk. You can ignore these errors. Ubuntu server will start.[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][FONT=Calibri][FONT=Calibri][SIZE=3]10.[/SIZE][/FONT]   [/FONT][/COLOR][COLOR=#1f497d][SIZE=3][FONT=Calibri]The Ubuntu server will drop to a minimal logon prompt. Logon using the username / password provided during installation. ‘Root’ user has no password, nor console access at this point [/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][/COLOR][COLOR=#1f497d][FONT=Calibri][FONT=Calibri][SIZE=3]11.[/SIZE][/FONT]   [/FONT][/COLOR][COLOR=#1f497d][SIZE=3][FONT=Calibri]Run the following command to get a list of packages to install:
**sudo tasksel**[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][FONT=Calibri][FONT=Calibri][SIZE=3]12.[/SIZE][/FONT]   [/FONT][/COLOR][COLOR=#1f497d][SIZE=3][FONT=Calibri]Select and install the **ubuntu-desktop** (or other desired desktop environment, such as kubuntu-dektop for KDE). Again, depending on your installation media,  you may need access to the internet in order to pull the required packages down.[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][FONT=Calibri][FONT=Calibri][SIZE=3]13.[/SIZE][/FONT]   [/FONT][/COLOR][COLOR=#1f497d][SIZE=3][FONT=Calibri]When done, you should be able to start into the GNOME desktop environment with this command:
**sudo startx**[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][FONT=Calibri][FONT=Calibri][SIZE=3]14.[/SIZE][/FONT]   [/FONT][/COLOR][COLOR=#1f497d][SIZE=3][FONT=Calibri]Once in the GUI, you can further configure options as you desire. A reboot from there should then reboot into the GNOME graphical environment at next start-up.[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][FONT=Calibri][SIZE=3] [/SIZE][/FONT][/COLOR]
 
> **TheR said:**
> I am using diskless servers for my KVM servers. I actualy boot servers from USB keys which is enough because everything else is on iSCSI SAN.
 
Than I heard for iSCSI boot which is still not mature enough for ubuntu at the time (as I read).
 
So I wonder. Would it be possible and if how to make some kind simple initial boot from USB key, configure network adapters and than boot actual OS from iSCSI's target LUN like I boot all my virtual machines.
 
 
by TheR

---

### Post by TheR on 2010-03-14
Thank you for your thorough reply. It looks like flex client has to be booted from CD or USB key every time, which then starts ubuntu. I will try this tomorrow.

I am using my own made  iSCSI HW of course with Ubuntu and brief look on the Internet shows me that this flex client is not for free. 

Is there any opensource solution for this functionality?

by
TheR

---

### Post by stevemarfisi on 2010-03-15
> **TheR said:**
> Thank you for your thorough reply. It looks like flex client has to be booted from CD or USB key every time, which then starts ubuntu. I will try this tomorrow.
 
I am using my own made iSCSI HW of course with Ubuntu and brief look on the Internet shows me that this flex client is not for free. 
 
Is there any opensource solution for this functionality?
 
by
TheR
 
The Flex client does not have to be booted from CD or USB - it is boostrapped via PXE. Actually, there is no Flex client per se here - just using Flex to obtain the iSCSI boot parameters at PXE boot time.
 
gPXE will work as well. I believe Ubuntu boot from iSCSI is documented on their web site. 
 
Steve

---

### Post by TheR on 2010-03-15
Let me explain what i think is my problem. I have storage server with double 1Gb NIC and double 10Gb NIC.

The first problem is that I don't want to expose storage server to client through 1G NIC-s but only through 10G NIC-s. 

Second problem is that 10G NIC-s don't have PXE boot option.

So basicly I am scru*** ;-(

On the positive site installing Ubuntu 9.10 on iSCSI storage works like a charm (I had manually enabled 1G network and Installed through 1G NIC. 10G NIC doesn't get detected on instalation).

I don't understand the mechanism of PXE booting but it looks like something which could be done by booting from CD or USB key. You ask DHCP server to get local ip address and address of tftp server (this could be easly configured in a file). Then you download and run some files from tftp server (they can as well be loaded from CD or USB key too) and after that I haven't quite understand what is happening. Just that guest OS boots.

Anybody here that has done this before or has idea how can it be done?

by
TheR

---

### Post by Xipher on 2010-03-15
You could certainly have grub, the kernel, and initrd on a flash drive to boot from so long as it has the drivers for the 10-GigE interface and iSCSI in initrd it should be possible. I don't have any hints on how to pull it off though.

---

