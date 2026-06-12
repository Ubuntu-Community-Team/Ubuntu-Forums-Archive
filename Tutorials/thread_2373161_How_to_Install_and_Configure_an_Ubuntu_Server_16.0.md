---
title: "How to Install and Configure an Ubuntu Server 16.04 LTS"
date: 2017-10-03
forum: Tutorials
---

### Post by LHammonds on 2017-10-03
Greetings and salutations,
 
I hope this thread will be helpful to those who follow in my foot steps as well as getting any advice based on what I have done / documented.

Link to original post: [HammondsLegacy Forums]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220") (best when viewed at original location due to custom formatting)

[SIZE=5]High-level overview[/SIZE]
 
This document will cover installation of a dedicated Ubuntu server. This will be the "base" installation of the server as a prerequisite for other documents that will build upon it (e.g. MediaWiki and MySQL). The server will be installed inside a virtual machine using vSphere running on ESXi servers. Notes will also be supplied for doing the same thing for Oracle's VirtualBox on a Windows 10 PC. Although there are some VMware-specific and VirtualBox-specific steps, they are very few and the majority of this documentation will work for other Virtual Machines or even directly installed onto a physical machine (e.g. bare-metal install).
 
This document will also cover some custom scripts to help automate tasks such as backing up, automatically growing the file system when free space is low, etc.
 
[SIZE=5]Tools utilized in this process[/SIZE]
 


[LIST]
[*][Ubuntu Server]("http://www.ubuntu.com/download/ubuntu/download") 16.04.3 LTS, 64-bit 
[*][Portable PuTTY]("http://portableapps.com/apps/internet/putty_portable") 0.62 ([0.63 was too buggy]("http://ubuntuforums.org/showthread.php?t=2218674")) 
[*][VMware vSphere]("http://www.vmware.com/products/vsphere/overview.html") 6.0.0 
[*][VirtualBox]("http://www.virtualbox.org/") 5.1.22 
[*][SystemRestoreCD]("http://sourceforge.net/projects/systemrescuecd/") 4.9.4 
[/LIST]

[SIZE=5]Helpful links[/SIZE]
 
The list below are sources of information that helped me configure this system as well as some places that might be helpful to me later on as this process continues.


[LIST]
[*][Learning Linux]("http://blog.jdpfu.com/2014/12/28/learning-linux") 
[*][Ubuntu Documentation]("https://help.ubuntu.com") 
[*][Ubuntu Firewall Basics]("https://help.ubuntu.com/community/IptablesHowTo#Disabling%20the%20firewall") 
[*][A primer on Iptables]("http://bodhizazen.net/Tutorials/iptables") 
[*][Ubuntu AppArmor Basics]("https://help.ubuntu.com/community/AppArmor#Disable%20AppArmor%20framework") 
[/LIST]

[SIZE=5]Assumptions[/SIZE]
 
This documentation will need to make use of some very-specific information that will most-likely be different for each person / location. This variable data will be noted in this section and highlighted in red throughout the document as a reminder that you should plug-in your own value rather than actually using these "place-holder" values.
 
Under no circumstance should you use the actual values listed below. They are place-holders for the real thing. This is just a checklist template you need to have answered before you start the install process.
 
Wherever you see [COLOR=red]RED[/COLOR] in this document, you need to substitute it for what your company uses.  NOTE: Ubuntu Forums does not allow me to use color tags in code blocks like on my forums so be careful about missing these placeholders based on color. (do a search/find)
 


[LIST]
[*]Ubuntu Server name: [COLOR=red]srv-ubuntu[/COLOR] 
[*]Internet domain: [COLOR=red]mydomain.com[/COLOR] 
[*]Ubuntu Server IP address: [COLOR=red]192.168.107.2[/COLOR] 
[*]Ubuntu Server IP subnet mask: [COLOR=red]255.255.255.0[/COLOR] 
[*]Ubuntu Server IP gateway: [COLOR=red]192.168.107.1[/COLOR] 
[*]Internal DNS Server 1: [COLOR=red]192.168.107.212[/COLOR] 
[*]Internal DNS Server 2: [COLOR=red]192.168.107.213[/COLOR] 
[*]External DNS Server 1: [COLOR=red]8.8.8.4[/COLOR] 
[*]External DNS Server 2: [COLOR=red]8.8.8.5[/COLOR] 
[*]Ubuntu Admin ID: [COLOR=red]administrator[/COLOR] 
[*]Ubuntu Admin Password: [COLOR=red]myadminpass[/COLOR] 
[*]Email Server (remote): [COLOR=red]192.168.107.25[/COLOR] 
[*]Windows Share ID: [COLOR=red]myshare[/COLOR] 
[*]Windows Share Password: [COLOR=red]mysharepass[/COLOR] 
[/LIST]

It is also assumed that the reader knows how to use the VI editor. If not, you will need to [beef up your skill set]("http://www.washington.edu/computing/unix/vi.html") or use a different editor in place of it.

---

### Post by LHammonds on 2017-10-03
[SIZE=5]Analysis and Design[/SIZE]
 
The Ubuntu Server Long-Term Support (LTS) is great choice for companies because it is a solid operating system that happens to be free. If professional support is needed, there is an option to buy support for the Long-Term Support (LTS) versions of the operating system.
 
The large decision over the configuration of Ubuntu is how the hard drive space is sliced up (partitioned). This documentation will focus on partitioning the drives in such a way that it allows for growth depending on what is needed for the specific application.
 
This following design allows for dynamic growth and fine-tuning if need be. Being caught offguard with a scenario where space is filled up with no immediate option other than deleting files is never a good thing. Long-term life and growth of the system as well as budgeting concerns have to be taken into consideration.
 
Isolating the root volume to mainly just static data that will not grow much over time is the central concern. Pushing the other folders into their own volumes will be done so their dynamic growth will not affect the root partition. Filling up the root volume on a *nix system is a very bad thing and should be avoided at all costs. The file systems will also not take up 100% of the logical volume. This will allow the file systems (through automated scripts) to grow as needed and give the administrators some time to add more drives if necessary or shrink other volumes to get more space.
 
The volumes will initially be sliced up as follows:
 


[LIST]
[*]**boot** - This will remain static in size. It is also the only space residing outside the Logical Volume Manager (LVM) 
[*]**root volume** - Operating system and everything else which should remain fairly static. 
[*]**swap volume** - This will remain static in size. However, if the amount of RAM is adjusted, this might need to be adjusted as well. 
[*]**home volume** - This is where personal files will be stored but likely not be used in most server configurations. 
[*]**tmp volume** - This location will be used for temporary storage. Size should be adjusted to match however it is being used. 
[*]**usr volume** - This will contain mostly static data and should not grow unexpectedly. 
[*]**var volume** - This is the app/database/log storage and will continue to grow over time. 
[*]**srv volume** - This will contain the files stored in the Samba share. 
[*]**opt volume** - This will contain specific software you add but may not be utilized at all depending on configuration. 
[*]**bak volume** - This will contain a local backup of the application. So space needs to be about double the size of your app data (typically double the /var size). 
[*]**Offsite Storage** - This will be handled elsewhere but will be mounted on this server. 
[/LIST]

The partitions will be increased later as needed but will start off with a lower number.
 
To get a good idea of the initial hard drive layout and to understand the process better, here is a graphical representation of the initial design for the server:
 
[IMG]http://www.hammondslegacy.com/images/linux/UbuntuHDPartitionDesign-Base.png[/IMG]
 
These numbers will be used for the initial build of the system:
 
boot = 200 MB
root = 2 GB
swap = 2 GB
home = 0.2 GB
tmp = 0.5 GB
usr = 2.0 GB
var = 2.0 GB
srv = 0.2 GB
opt = 0.2 GB
bak = 0.5 GB
 
NOTE: When the logical volumes and file systems are initially created, they consume the maximum amount of space allocated so that the file system size will initially equal the logical volume size. These partition sizes above are artificially small for that reason. These will be later modified so that the logical volume will be larger than the file system so that the file system has room to expand when needed in a safe and automated manner.

Important info:
- The /tmp folder is strictly temporary. By default, each time the server reboots, this folder is deleted and re-created.
- The /bak folder will retain the most recent backup and is considered the "local" copy of the backup.
 
[SIZE=5]VMware Virtual Machine Settings[/SIZE]


[LIST]
[*]Configuration: Custom 
[*]Name: [COLOR=red]**srv-ubuntu**[/COLOR] 
[*]Datastore: DS3400-LUN0 
[*]Virtual Machine Version: 8 
[*]Guest Operating System: Linux, Version: Ubuntu Linux (64-bit) 
[*]Number of virtual processors: 1 
[*]Memory Size: 1024 MB 
[*]Number of NICs: 1 
[*]NIC 1: VM Network 
[*]Adapter: E1000, Connect at Power On: Checked 
[*]SCSI controller: LSI Logic Parallel 
[*]Select a Disk: Create a new virtual disk 
[*]Create a Disk: 10 GB, No thin provisioning, No cluster features, Store with the virtual machine 
[*]Advanced Options: Virtual Device Node = SCSI (0:0) 
[*]Remove Floppy Drive 
[*]Mount CD/DVD Drive to Ubuntu ISO (ubuntu-16.04-server-amd64.iso). Make sure CD/DVD is set to **Connect at power on** 
[*]Set boot options to Force BIOS Setup so you can set CDROM to boot before the Hard Disk 
[/LIST]

[SIZE=5]VirtualBox Virtual Machine Settings[/SIZE]


[LIST]
[*]Name: [COLOR=red]**srv-ubuntu**[/COLOR] 
[*]Operating System: Linux 
[*]Version: Ubuntu (64 bit) 
[*]Memory: 1024 MB 
[*]Check - Start-up Disk
- Create new hard disk
- VMDK
- Dynamically allocated
- Size: 10 GB 
[*]Select [COLOR=red]**srv-ubuntu**[/COLOR] and click Settings (**CTRL+S**)
- System, Processor, Enable PAE/NX
- Network, Attached to: Bridged Adapter, Advanced, Adapter Type: Intel PRO/1000 MT Server
- Storage, IDE Controller, Choose a virtual CD/DVD disk file, ubuntu-16.04-server-amd64.iso 
[/LIST]

[SIZE=5]Install PuTTY[/SIZE]
 
When running inside a virtual machine, the response time for screen refreshes can be painfully slow to view man (manual) pages and navigating in VI (text editor). However, when using PuTTY via SSH, it is a far better solution for your Ubuntu console because it handles the screen draws much faster when scrolling and allows copying and pasting text between windows.
 
For example, selecting and copying a command in this document and then right-clicking in the PuTTY window will paste the command and have it ready to execute. Any text/lines highlighted with the mouse will be automatically copied into clipboard memory.
 
Download the portable edition and run the install...except it does not really "install" like a normal program, it simply extracts to a specified folder and will run from that folder even if you put it on a USB stick and carry over to a new computer (requires no install to run and thus leaves no footprint on your system)
 


[LIST=1]
[*]Start PuTTY 
[*]Type the following and click the Save button:
Host Name: [COLOR=red]**SRV-Ubuntu**[/COLOR] (or the IP such as **[COLOR=red]192.168.107.2[/COLOR]**)
Port: **22**
Connection type: **SSH**
Saved Sessions: [COLOR=red]**SRV-Ubuntu**[/COLOR] 
[*]Now all you have to do is double-click on the session and it will connect to your server (when online). 
[/LIST]

---

### Post by LHammonds on 2017-10-03
[SIZE=5]Install Ubuntu Server[/SIZE]

NOTE: During the setup process throughout this entire document, most commands will require "sudo" as a prefix. However, this document will be using "sudo su" to temporarily gain root privileges so that subsequent commands will work without the need for the "sudo" prefix.



[LIST=1]
[*]Power on the Virtual Machine (VM) 
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *English* 
[*]Select *Install Ubuntu Server* [COLOR=green]{ENTER}[/COLOR] 
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *English* 
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *United States* 
[*]Select **No** to not detect keyboard layout 
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *English (US)* 
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *English (US)* 
[*]Type **[COLOR=red]srv-ubuntu[/COLOR]** [COLOR=green]{ENTER}[/COLOR] (this is your hostname) 
[*]Type **[COLOR=red]Administrator[/COLOR]**, [COLOR=green]{ENTER}[/COLOR] for the full name 
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept the default of the lowercase name of **[COLOR=red]administrator[/COLOR]** 
[*]Type **[COLOR=red]myadminpass[/COLOR]**, [COLOR=green]{ENTER}[/COLOR], **[COLOR=red]myadminpass[/COLOR]**, [COLOR=green]{ENTER}[/COLOR] 
[*]Select *No*, [COLOR=green]{ENTER}[/COLOR] to not encrypt your home directory 
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept detected time zone (*America/Chicago*) 
[*]Select *Manual* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *SCSI3 (0,0,0) (sda) - 10.7 GB VMware Virtual disk* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Yes* to create new empty partition table, [COLOR=green]{ENTER}[/COLOR] 
[*]Select *pri/log 10.7 GB FREE SPACE* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Create a new partition* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **500MB**, [COLOR=green]{ENTER}[/COLOR] (NOTE: This will be the /boot partition) 
[*]Select *Primary* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Beginning* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Use as: Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Ext2 file system* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Mount point: /* [COLOR=green]{ENTER}[/COLOR] 
[*]Select */boot - static files of the boot loader* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Label:* and type **boot** and press [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Bootable flag: off* [COLOR=green]{ENTER}[/COLOR] (NOTE: This toggles it on) 
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Configure the Logical Volume Manager* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Yes* to write change to disks and configure LVM, [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Create volume group* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **LVG** [COLOR=green]{ENTER}[/COLOR] 
[*]Select */dev/sda free #1 (10537MB; FREE SPACE)*, [COLOR=green]{SPACEBAR}[/COLOR], [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Yes* to write change to disks and configure LVM, [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *LVG (10531MB)* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **root** [COLOR=green]{ENTER}[/COLOR] 
[*]Type **2G** [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *LVG (8535MB)* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **swap** [COLOR=green]{ENTER}[/COLOR] 
[*]Type **2G** [COLOR=green]{ENTER}[/COLOR] (NOTE: This is double the amount of RAM) 
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *LVG (6538MB)* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **home** [COLOR=green]{ENTER}[/COLOR] 
[*]Type **0.2G** [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *LVG (6341MB)* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **tmp** [COLOR=green]{ENTER}[/COLOR] 
[*]Type **0.5G** [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *LVG (5842MB)* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **usr** [COLOR=green]{ENTER}[/COLOR] 
[*]Type **2G** [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *LVG (3846MB)* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **var** [COLOR=green]{ENTER}[/COLOR] 
[*]Type **2G** [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *LVG (1849MB)* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **srv** [COLOR=green]{ENTER}[/COLOR] 
[*]Type **0.2G** [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *LVG (1652MB)* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **opt** [COLOR=green]{ENTER}[/COLOR] 
[*]Type **0.2G** [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *LVG (1455MB)* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **bak** [COLOR=green]{ENTER}[/COLOR] 
[*]Type **0.5G** [COLOR=green]{ENTER}[/COLOR] (we will have a small amount leftover in LVG) 
[*]Select *Finish* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *#1 2.0 GB* directly under *LVM VG LVG, LV root*, [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR] 
[*]Select */ - the root file system* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Label: none* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **root** [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *#1 2.0 GB* directly under *LVM VG LVG, LV swap*, [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *swap area* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *#1 197.1 MB* directly under *LVM VG LVG, LV home*, [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR] 
[*]Select */home* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Label: none* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **home** [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *#1 499.1 MB* directly under *LVM VG LVG, LV tmp*, [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR] 
[*]Select */tmp* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Label: none* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **tmp** [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Label: **tmp*** [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *#1 2.0 GB* directly under *LVM VG LVG, LV usr*, [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR] 
[*]Select */usr* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Label: none* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **usr** [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *#1 2.0 GB* directly under *LVM VG LVG, LV var*, [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR] 
[*]Select */var* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Label: none* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **var** [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *#1 197.1 MB* directly under *LVM VG LVG, LV srv*, [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR] 
[*]Select */srv* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Label: none* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **srv** [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *#1 197.1 MB* directly under *LVM VG LVG, LV opt*, [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR] 
[*]Select */opt* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Label: none* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **opt** [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *#1 499.1 MB* directly under *LVM VG LVG, LV bak*, [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Enter manually* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **/bak** [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Label: none* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **bak** [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR] 
[*]Here is what the screen looks like at this point: [Partitions]("http://www.hammondslegacy.com/images/linux/Ubuntu-LVM-Partitions.png") 
[*]Select *Finish partitioning and write changes to disk* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Yes* to write changes to disk, [COLOR=green]{ENTER}[/COLOR] 
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept a blank line for the HTTP proxy 
[*]Select *No automatic updates*, [COLOR=green]{ENTER}[/COLOR]  (* We will schedule a script for this later *) 
[*]Set the following and press [COLOR=green]{ENTER}[/COLOR] to continue:
Uncheck - Manual package selection
Uncheck - DNS server
Uncheck - LAMP server
Uncheck - Mail server
Uncheck - PostgreSQL database
Uncheck - Samba file server
**Check** - standard system utilities (enabled by default)
Uncheck - Virtual Machine host
**Check** - OpenSSH server (allows us to use PuTTY after installation to connect to the server) 
[*]Select *Yes*, [COLOR=green]{ENTER}[/COLOR] to install GRUB boot loader to the master boot record 
[*]Installation Complete - from the VM menu, select VM --> Edit Settings and select *CD/DVD Drive 1* and change to "Client Device" which will effectively remove the ISO. Now press [COLOR=green]{ENTER}[/COLOR] to reboot. 
[/LIST]

 
[SIZE=5]Initial Configurations[/SIZE]
 


[LIST=1]
[*]At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR]) 
[*]At the $ prompt, temporarily grant yourself super user privileges by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR=red]myadminpass[/COLOR]**). 
[*]Type the following to give you a list of interfaces.  It will likely show you a loopback interface (lo) and an Ethernet interface (eth0, ens32, etc.)  Be sure to remember the Ethernet name.  The following steps will assume "eth0" was the name.
```
ip link
``` 
[*]Type **vi /etc/network/interfaces** [COLOR=green]{ENTER}[/COLOR] and change the Ethernet interface: (We need to change it from using DHCP to a static IP)
From:
[mycode]iface [COLOR=red]eth0[/COLOR] inet dhcp[/mycode]
To:
[mycode]iface [COLOR=red]eth0[/COLOR] inet **static**
**address [COLOR=red]192.168.107.2[/COLOR]**
**netmask [COLOR=red]255.255.255.0[/COLOR]**
**gateway [COLOR=red]192.168.107.1[/COLOR]**
**network [COLOR=red]192.168.107[/COLOR].0**
**broadcast [COLOR=red]192.168.107[/COLOR].255**
**dns-nameservers [COLOR=red]192.168.107.212 192.168.107.213 8.8.8.4 8.8.8.5[/COLOR]**[/mycode]
 
NOTE #1: You may need to manually remove the DHCP record (lease) associated to this Ubuntu server from your DHCP server so the correct IP can be found by other machines on the network. This can be avoided by temporarily configuring the VM Network Adapter connection to be "Host Only Network" instead of "VM Network" so the server is isolated during setup...at least until you reach the testing of the static IP below.
 
NOTE #2: You might also need to manually add a HOST(A) record to your Windows DNS server (for [COLOR=red]srv-ubuntu.mydomain.com[/COLOR] and [COLOR=red]srv-ubuntu.work.mydomain.com[/COLOR]) 
[*]Restart the network by typing the following:
[mycode]ip address flush [COLOR=#FF0000]eth0[/COLOR]
systemctl restart networking.service[/mycode] 
[*]Sanity check! Type **ifconfig** and make sure the settings are correct. Then type **ping [www.google.com]("http://www.google.com")** or similar and see if ping works. 
[*]Shutdown and power off the server by typing **shutdown -P now** 
[*]At this point forward, you can use PuTTY to access the console rather than the console itself for better performance, ability to scroll, etc. 
[*]In VM menu, select VM --> Snapshot --> Take Snapshot. Give it a name like **STEP 1** and description of **Ubuntu Server 16.04 LTS, clean install, Static IP: [COLOR=red]192.168.107.2[/COLOR]** and click **OK** 
[/LIST]


[SIZE=5]16.04.1 LTS Reboot/Shutdown Bug[/SIZE]

If you are experiencing a 10 minute delay when issuing a reboot or shutdown command, you might need to edit line 120 of the unattended upgrades script and change "False" to "false"

I have documented the [problem description here]("https://ubuntuforums.org/showthread.php?t=2351393") and others have pointed to the [bug fix here]("https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1661611").

The problem was fixed in version "0.90ubuntu0.5" which means you can do "**apt search unattended-upgrades**" and compare your installed version to see if you will be affected (by having an earlier version installed). In Ubuntu Server 16.04.3, we have version 0.90ubuntu0.8 which means this issue is not present in the current release of the operating system.

[SIZE=5]Operating System Patches[/SIZE]
 


[LIST=1]
[*]Start the Ubuntu server and connect using PuTTY. 
[*]At the $ prompt, temporarily grant yourself super user privileges by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR=red]myadminpass[/COLOR]**). 
[*]Install the patches by typing the following commands:
```
apt update
apt upgrade
apt dist-upgrade
``` 
[*]Shutdown and power off the server by typing **shutdown -P now** 
[*]In VM menu, select VM --> Snapshot --> Take Snapshot. Give it a name like **STEP 2** and description of **Ubuntu Server 16.04 LTS, Patches applied, Static IP: [COLOR=red]192.168.107.2[/COLOR]**. The Snapshot Manager should now have a nice hierarchy of snapshots (STEP 1 --> STEP 2 --> You are here) 
[/LIST]

---

### Post by LHammonds on 2017-10-03
[SIZE=5]Volume / Disk Management[/SIZE]

Earlier, it was mentioned that the partition design needed to have some breathing room in each volume so that the file system inside can grow as needed. When the volumes were created during setup, the file systems were automatically expanded to fill the entire volume. We will now correct this by adding more "drives" to the system and then extend each logical volume to gain some breathing space.
 
Most logical volumes will be increased in size and then the file systems contained in them will be increased but not to the maximum amount.
 
This design will allow growth when needed and ensure that there will be time to add additional hard drives BEFORE they are needed which will keep the administrators from being stuck between a rock and a hard place! Nobody wants to lose a job because somebody did not estimate growth correctly or the budget did not allow for large capacity when the system first rolled out.
 
Here are the planned adjustments for each **logical volume**:
 
root = 2 GB to 3 GB
swap = 2 GB (no change)
home = 0.2 GB to 1 GB
tmp = 0.5 GB to 2 GB
usr = 2.0 GB to 4 GB
var = 2.0 GB to 3 GB
srv = 0.2 GB to 2 GB
opt = 0.2 GB to 2 GB
bak = 0.5 GB to 4 GB
 
Here are the planned adjustments for each **file system**:
 
root = 2.0 GB (no change)
swap = 2.0 GB (no change)
home = 0.2 GB to 0.5 GB
tmp = 0.5 GB to 1.0 GB
usr = 2.0 GB to 3.0 GB
var = 2.0 GB (no change)
srv = 0.2 GB to 1.0 GB
opt = 0.2 GB to 1.0 GB
bak = 0.5 GB to 2.0 GB
 
We started off with a 10 GB drive to hold these volumes but now need 22 GB. For this exercise, we will add two 12 GB drives to cover the additional storage needs. (NOTE: This was an arbitrary number in order to demonstrate how to add additional hard drives to the system)
 
Here is a graphical representation of what needs to be accomplished:
 
[IMG]http://www.hammondslegacy.com/images/linux/UbuntuHDPartitionDesign-Mod.png[/IMG]
 
If we were to type **df -h** right now, we should see something like this:
 
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  1.9G  429M  1.4G  24% /
udev                  489M  4.0K  489M   1% /dev
tmpfs                 200M  244K  199M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  498M     0  498M   0% /run/shm
/dev/sda1             179M   47M  122M  28% /boot
/dev/mapper/LVG-home  187M  9.5M  168M   6% /home
/dev/mapper/LVG-tmp   473M   23M  427M   5% /tmp
/dev/mapper/LVG-usr   1.9G  460M  1.4G  26% /usr
/dev/mapper/LVG-var   1.9G  367M  1.5G  21% /var
/dev/mapper/LVG-srv   187M  9.5M  168M   6% /srv
/dev/mapper/LVG-opt   187M  9.5M  168M   6% /opt
/dev/mapper/LVG-bak   473M   23M  427M   5% /bak
```
 
Adding more space in VMware is easy. In this exercise, each drive will be added as a separate disk just as if we were to add a physical drive to a physical server.


[LIST=1]
[*]Shutdown and power off the server by typing **shutdown -P now** 
[*]In the vSphere client, right-click the Virtual Machine and choose *Edit Settings*. 
[*]On the hardware tab, click the *Add* button and select Hard Disk. Click Next, choose "Create a new virtual disk", click Next, set the size to **12** GB, click Next, Next, Finish. 
[*]Add another **12** GB disk using the same steps above and click OK to close the settings and allow VMware to process the changes. 
[/LIST]

Collect information about the newly added drives.


[LIST=1]
[*]Start the server and connect using PuTTY. 
[*]At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR]) and then temporarily grant yourself super user privilages by typing **sudo su** 
[*]Type **pvdisplay** which should show something similar to this:
```
--- Physical volume ---
  PV Name               /dev/sda5
  VG Name               LVG
  PV Size               9.81 GiB / not usable 3.00 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              2511
  Free PE               228
  Allocated PE          2283
  PV UUID               NkfC3i-ROqv-YuLZ-63VO-RTAU-l01p-suqi4O
```
The important bits of info here are the PV Name and VG Name for our existing configuration. 
[*]Type **fdisk -l** which should show something similar to this (however I abbreviated it to show just the important parts):
```
Disk /dev/sda: 10.7 GB, 10737418240 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      391167      194560   83  Linux
/dev/sda2          393214    20969471    10288129    5  Extended
/dev/sda5          393216    20969471    10288128   8e  Linux LVM
 
Disk /dev/sdb: 12.9 GB, 12884901888 bytes
Disk /dev/sdb doesn't contain a valid partition table
Disk /dev/sdc: 12.9 GB, 12884901888 bytes
Disk /dev/sdc doesn't contain a valid partition table
```
The important bits of info here are the device paths for the new drives which I highlighted in red. 
[/LIST]

Prepare the first drive (/dev/sdb) to be used by the LVM
 
Type the following:
```
fdisk /dev/sdb
n (Create New Partition)
p (Primary Partition)
1 (Partition Number)
{ENTER} (use default for first cylinder)
{ENTER} (use default for last cylinder)
t (Change partition type)
8e (Set to Linux LVM)
p (Preview how the drive will look)
w (Write changes)
```
 
Prepare the second drive (/dev/sdc) to be used by the LVM
 
Do the exact same steps as above but start with **fdisk /dev/sdc**
 
Create physical volumes using the new drives
 
If we type **fdisk -l**, we now see /dev/sdb1 and /dev/sdc1 which are Linux LVM partitions.
 
Type the following to create physical volumes:
```
pvcreate /dev/sdb1
pvcreate /dev/sdc1
```
 
Now add the physical volumes to the volume group (LVG) by typing the following:
```
vgextend LVG /dev/sdb1
vgextend LVG /dev/sdc1
```
 
Now that the space of both drives have been added to the logical volume group called LVG, we can now allocate that space to grow the logical volumes.
 
To get a list of volume paths to use in the next commands, type **lvscan** to show your current volumes and their sizes.
 
Type the following to set the exact size of the volume by specifying the end-result size you want:
 
```
lvextend -L3G /dev/LVG/root
lvextend -L1G /dev/LVG/home
lvextend -L2G /dev/LVG/tmp
lvextend -L4G /dev/LVG/usr
lvextend -L3G /dev/LVG/var
lvextend -L2G /dev/LVG/srv
lvextend -L2G /dev/LVG/opt
lvextend -L4G /dev/LVG/bak
```
 
or you can grow each volume by the specified amount (the number after the plus sign):
```
lvextend -L+1G /dev/LVG/root
lvextend -L+0.8G /dev/LVG/home
lvextend -L+1.5G /dev/LVG/tmp
lvextend -L+2G /dev/LVG/usr
lvextend -L+1G /dev/LVG/var
lvextend -L+1.8G /dev/LVG/srv
lvextend -L+1.8G /dev/LVG/opt
lvextend -L+3.5G /dev/LVG/bak
```
 
To see the new sizes, type **lvscan**
```
ACTIVE            '/dev/LVG/root' [3.00 GiB] inherit
  ACTIVE            '/dev/LVG/swap' [1.86 GiB] inherit
  ACTIVE            '/dev/LVG/home' [1.00 GiB] inherit
  ACTIVE            '/dev/LVG/tmp' [2.00 GiB] inherit
  ACTIVE            '/dev/LVG/usr' [4.00 GiB] inherit
  ACTIVE            '/dev/LVG/var' [3.00 GiB] inherit
  ACTIVE            '/dev/LVG/srv' [2.00 GiB] inherit
  ACTIVE            '/dev/LVG/opt' [2.00 GiB] inherit
  ACTIVE            '/dev/LVG/bak' [4.00 GiB] inherit
```
 
The last thing to do now is the actual growth of the file systems. We want to grow the existing file systems but only to a certain amount so we do not take up all the space in the volume. We want room for growth in the future so we have time to order and install new drives when needed.
```
resize2fs /dev/LVG/root 2G
resize2fs /dev/LVG/home 500M
resize2fs /dev/LVG/tmp 1G
resize2fs /dev/LVG/usr 3G
resize2fs /dev/LVG/var 2G
resize2fs /dev/LVG/srv 1G
resize2fs /dev/LVG/opt 1G
resize2fs /dev/LVG/bak 3G
```
 
If we need to increase space in **/var** at a later point, we can issue the following command without any downtime (we will automate this in a nifty script later):
 
```
resize2fs /dev/LVG/var 2560MB
```
 
We could continue to increase this particular file system all the way until we reach the limit of the volume which is 3 GB at the moment.
 
If we were to type **df -h** right now, we should see something like this:
 
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  1.9G  429M  1.4G  24% /
udev                  489M  4.0K  489M   1% /dev
tmpfs                 200M  260K  199M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  498M     0  498M   0% /run/shm
/dev/sda1             179M   47M  122M  28% /boot
/dev/mapper/LVG-home  488M  9.7M  454M   3% /home
/dev/mapper/LVG-tmp  1004M   23M  931M   3% /tmp
/dev/mapper/LVG-usr   3.0G  481M  2.3G  17% /usr
/dev/mapper/LVG-var   1.8G  267M  1.5G  16% /var
/dev/mapper/LVG-srv   989M  2.8M  940M   12% /srv
/dev/mapper/LVG-opt   996M  2.8M  940M   1% /opt
/dev/mapper/LVG-bak   2.0G   3.0M  1.9G   1% /bak
```

Remember, **df -h** will tell you the size of the file system and **lvscan** will tell you the size of the volumes where the file systems live in.

TIP: If you want to see everything in a specific block size, such as everything showing up in megabytes, you can use **df --block-size m**

Shutdown and power off the server by typing **shutdown -P now**

In VM menu, select VM --> Snapshot --> Take Snapshot. Give it a name like **STEP 3** and description of **Ubuntu Server 16.04 LTS, Storage space adjusted, Static IP: [COLOR=red]192.168.107.2[/COLOR]**. The Snapshot Manager should now have a nice hierarchy of snapshots (STEP 1 --> STEP 2 --> STEP 3 --> You are here)

---

### Post by LHammonds on 2017-10-03
[SIZE=5]Software Configurations[/SIZE]
 

[LIST=1]
[*]Turn on the server and connect using PuTTY. 
[*]At the login prompt, login with your administrator account (**[COLOR=red]administrator[/COLOR] **/ **[COLOR=red]myadminpass[/COLOR]**) 
[*]At the $ prompt, temporarily grant yourself super user privileges by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR=red]myadminpass[/COLOR]**). 
[*]At the $ prompt, type the following to install various utilities which are described below:
```
apt -y install vim-nox p7zip-full ntpdate htop fsarchiver sendemail
```
[LIST]
[*]vim-nox for use instead of the built-in VI editor. [more info]("http://en.wikipedia.org/wiki/Vim_%28text_editor%29") 
[*]p7zip-full is a 7-zip archive utility. 
[*]ntpdate is a time synchronization utility. 
[*]htop is a CPU/RAM monitoring utility. 
[*]fsarchiver is a backup utility. 
[*]sendemail is a command-line email utility. 
[/LIST]
  
[*]Change the default shell from dash to bash. Type **ls -l /bin/sh** to see that it points to /bin/dash. Type **dpkg-reconfigure dash** and answer **No**. Type **ls -l /bin/sh** and it should now be pointing to /bin/bash 
[*]It might be necessary to remove AppArmor to avoid problems by typing the following:
```
/etc/init.d/apparmor stop
/etc/init.d/apparmor teardown
update-rc.d -f apparmor remove
apt-get remove apparmor
``` 
[*]Type **vi /etc/hosts** and add your email server:
```
192.168.107.25    srv-mail
``` 
[*]Test the ability to send email by typing:
```
sendemail -f root@myserver -t MyTargetAddress@MyDomain.com -u "This is the Subject" -m "This is the body of the email" -s srv-mail:25
``` 
[/LIST]


[SIZE=5]SUDO Warning Message[/SIZE]


[LIST=1]
[*]Enable the default warning message whenever "sudo" is used.  Type **vi /etc/sudoers** and add the following line near the other defaults (instead of "always" you can use "once" too):
```
Defaults lecture=always
``` 
[*]To customize the message, you can create a custom message file.  Type **vi /etc/lecture** and add the following text or whatever you want:
```
We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.
``` 
[*]Now save the file and configure permissions to access that file.  Type **chmod 644 /etc/lecture** 
[*]Now point to the newly-created file in the sudoers config file.  Type **/vi /etc/sudoers**
```
Defaults lecture_file=/etc/lecture
``` 
[/LIST]


[SIZE=5]SSH Login Message
[/SIZE]

[LIST=1]
[*]To enable login banners that are displayed before entering a password, edit the following:
```
vi /etc/issue.net
``` 
[*]Add your message however you like to word it and save/close the file:
```

*********************************************************************
  ALERT! You are entering into a secured area!
  Your IP, Login Time, Username have been recorded.
  This service is restricted to authorized users only.
  All activities on this system are logged.
  Unauthorized access will be reported to the law enforcement agencies.
*********************************************************************

``` 
[*]Enable banners to be displayed by editing the SSH config file:
```
vi /etc/ssh/ssh_config
```
```
Banner /etc/issue.net
``` 
[*]Restart the SSH service:
```
service sshd restart
``` 
[/LIST]


Reboot the server by typing **reboot**
 
[SIZE=5]VMware Tools[/SIZE]
 
VMware Tools need to be installed if the VM is using a VMware host. This will insure maximum performance in a virtual environment and allow ESXi to interact with the operating system.

Starting with Ubuntu 16.04, open-vm-tools are installed automatically.  We should not need to perform any actions in this section.  It is kept for historical reasons.

Starting with Ubuntu 14.04, we now install drivers from the repository rather than using the "Guest" VMware Tools menu to attach the CD-ROM and install manually.


[LIST=1]
[*]Connect to the server using PuTTY 
[*]At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR]) 
[*]At the $ prompt, temporarily grant yourself super user privileges by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR=red]myadminpass[/COLOR]**). 
[*]Type the following:
```
apt install open-vm-tools
reboot
```
[/LIST]
  
[SIZE=5]VMware Tools Upgrade[/SIZE]
 
There is no need to manually update the drivers since they are now part of the software repository.  If you configure your system to get updates automatically, vmware drivers will get updated as well if there are any updates.

[SIZE=5]VirtualBox Guest Additions - Installation[/SIZE]
 
The Guest Additions need to be installed if the VM is using a VirtualBox host. This will insure maximum performance in a virtual environment.


[LIST=1]
[*]Connect to the server using PuTTY. 
[*]At the login prompt, login with your administrator account (**[COLOR=red]administrator[/COLOR] **/ **[COLOR=red]myadminpass[/COLOR]**) 
[*]At the $ prompt, temporarily grant yourself super user privileges by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR=red]myadminpass[/COLOR]**). 
[*]You need to perform the following commands to fulfill the prerequisites:
```
apt install dkms
reboot
``` 
[*]Connect to the server using PuTTY. 
[*]At the login prompt, login with your administrator account (**[COLOR=red]administrator[/COLOR] **/ **[COLOR=red]myadminpass[/COLOR]**) 
[*]At the $ prompt, temporarily grant yourself super user privileges by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR=red]myadminpass[/COLOR]**). 
[*]From the VirtualBox menu, click Devices, Install Guest Additions 
[*]At the console, type the following:
```
mkdir -p /mnt/cdrom
mount /dev/cdrom /mnt/cdrom
/mnt/cdrom/VBoxLinuxAdditions.run
``` 
[*]NOTE: The X Windows System drivers will fail to load because this is a headless server with no GUI (which is OK) 
[*]To see if the services are running, type **/etc/init.d/vboxadd-service status** or **service vboxadd-service status** 
[/LIST]

 
[SIZE=5]VirtualBox Guest Additions - Upgrading[/SIZE]
 
If VirtualBox is updated on the host machine, each VM also needs the upgraded Guest Additions.
 
Then mount the CDROM and run the installer just like the above. Reboot after it is upgraded.


[LIST=1]
[*]Connect to the server using PuTTY. 
[*]At the login prompt, login with your administrator account (**[COLOR=red]administrator[/COLOR] **/ **[COLOR=red]myadminpass[/COLOR]**) 
[*]At the $ prompt, temporarily grant yourself super user privileges by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR=red]myadminpass[/COLOR]**). 
[*]From the VirtualBox menu, click Devices, Install Guest Additions 
[*]At the console, type the following:
```
mount /dev/cdrom /mnt/cdrom
/mnt/cdrom/VBoxLinuxAdditions.run
reboot
``` 
[/LIST]

 
[SIZE=5]VirtualBox Guest Additions - Uninstallation[/SIZE]
 
If a VM will be migrated from VirtualBox to something like a VMware, the Guest Additions on the VM will need to be removed.


[LIST=1]
[*]Connect to the server using PuTTY. 
[*]At the login prompt, login with your administrator account (**[COLOR=red]administrator[/COLOR] **/ **[COLOR=red]myadminpass[/COLOR]**) 
[*]At the $ prompt, temporarily grant yourself super user privileges by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR=red]myadminpass[/COLOR]**). 
[*]Type the following:
```
cd /opt/VBox*
./uninstall.sh
``` 
[/LIST]


[SIZE=5]Configure Ubuntu for File Sharing[/SIZE]

This file sharing section is optional but can be handy if you need to swap files between the Linux server and a Windows machine.

This documentation will utilize this share for passing pre-configured files (configs, scripts, etc.) to make it faster/easier during installation.


[LIST=1]
[*]Start the Ubuntu server and connect using PuTTY. 
[*]At the login prompt, login with your administrator account (**[COLOR=red]administrator[/COLOR] **/ **[COLOR=red]myadminpass[/COLOR]**) 
[*]At the $ prompt, temporarily grant yourself super user privileges by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR=red]myadminpass[/COLOR]**). 
[*]Install Samba by typing **apt -y install samba cifs-utils** (NOTE: To share a folder with Windows, you just need the **samba** package, to connect to a Windows share, you need both **samba** and **cifs-utils**) 
[*]Type the following commands:
```
cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
mkdir -p /srv/samba/share
chown nobody:nogroup /srv/samba/share/
chmod 0777 /srv/samba/share
``` 
[*]Edit the configuration file by typing **vi /etc/samba/smb.conf** 
[*]Change:
```
workgroup = WORKGROUP
```
to:
```
workgroup = work
``` (you are using the domain alias) 
[*]Add the following section to the end of the file:
```
[share]
comment = Ubuntu File Server Share
path = /srv/samba/share
browsable = yes
guest ok = yes
read only = no
create mask = 0755
``` 
[*]Save and exit the file. 
[*]Restart the samba services to utilize the new configuration by typing:
```
service smbd restart
service nmbd restart
``` 
[*]You should now be able to click Start --> Run and type **\\[COLOR=red]srv-ubuntu[/COLOR]** or **\\[COLOR=red]192.168.107.2[/COLOR]** [COLOR=green]{ENTER}[/COLOR] and see an explorer window with a *Share* folder.  Drag-n-drop a file into the *Share* folder.  If it worked, it will not display an error message and you should be able to view it from the server by typing **ls -l /srv/samba/share/** 
[*]Shutdown and power off the server by typing **shutdown -P now** [COLOR=green]{ENTER}[/COLOR] 
[*]In VM menu, select VM --> Snapshot --> Take Snapshot.  Give it a name like **STEP 4** and description of **Ubuntu Server 16.04 LTS, File share configured, Static IP: [COLOR=red]192.168.107.2[/COLOR]**.  The Snapshot Manager should now have a nice hierarchy of snapshots (STEP 1 --> STEP 2 --> STEP 3 --> STEP 4 --> You are here) 
[/LIST]

---

### Post by LHammonds on 2017-10-03
[SIZE=5]Scripting[/SIZE]

Much of the solutions beyond this point involve scripts (programming snippets / automated commands).
 
In particular, they are Bash Scripts. I chose this due to its popularity and the fact it comes with Ubuntu. I try to make use of what comes with the system without requiring additional software / services unless they really add to the bottom line such as decreasing the time it takes for a process to run or to conserve storage and bandwidth usage.
 
When setting up a server and testing things out, there is typically very little concern for procedures / process since much of the activity is exploration and experimentation as well as not having an impact on production. However, once a server goes into production, processes and procedures need to be in place to ensure the availability of the services being provided.
 
In regards to these scripts, they will be treated like any other program and will require being tested, documented and go through a promotion process.
 
The ideal situation would involve 3 servers (for a single server setup). A test / development server, a quality assurance staging server and the production server itself. If 3 servers cannot be utilized, then it can still work well with 2 servers. Testing scripts / programs / restore on the production server is not advisable and many times impractical...how can you test your restore process / data periodically if you only have a production server?
 
The QA Staging server would resemble the production server as close as possible. The server should be setup in such a way that production backups are restored to this server which also tests and validates the backup / restore process as well as maintains a close representation of the production server to mitigate variable risk involved when testing new or modified programs and upgrades.
 
The test / development server can serve as the QA server if absolutely necessary.
 
The directory structure and how scripts can import other scripts will be configured to facilitate this process.
 
Example:
 
Directory path for scripts to import common variables, functions and server settings: **/var/scripts/common/**
 
Directory path for production scripts: **/var/scripts/prod/**
 
Directory path for QA staging area scripts: **/var/scripts/qa/**
 
Directory path for test / development scripts: **/var/scripts/test/**
 
Directory path for data for use by scripts: **/var/scripts/data/**
 
With a production and test servers on physically different machines, the "common" scripts folder can be custom-tailored for that environment and allow for minimal changes to a script when running on the test, QA or production server. This is similar to "normalizing" a database. If you have a variable, path or function that is duplicated in multiple scripts, consider pulling it out and placing it in the common folder. If ever you need to change who receives the email reports, you only need to update a single script and all programs will use the new reference from that point on.
 
Most of my scripts will import a file called "standard.conf" from the common script folder.
 
/var/scripts/common/standard.conf (contents of the file on the **production** server)
```
## Global Variables ##
Company="abc"
TempDir="/tmp"
LogDir="/var/log"
ShareDir="/srv/samba/share"
MyDomain="mydomain.com"
AdminEmail="admin@${MyDomain}"
ReportEmail="LHammonds <lhammonds@${MyDomain}>"
BackupDir="/bak"
OffsiteDir="/mnt/backup"
OffsiteTestFile="${OffsiteDir}/online.txt"
ArchiveMethod="tar.7z"    ## Choices are tar.7z or tgz
Hostname="$(hostname -s)"
ScriptName="$0"
ScriptDir="/var/scripts"
MailFile="${TempDir}/mailfile.$$"
 
## Global Functions ##
 
function f_sendmail()
{
  ## Purpose: Send administrative email message.
  ## Parameter #1 = Subject
  ## Parameter #2 = Body
  sendemail -f "${AdminEmail}" -t "${ReportEmail}" -u "${1}" -m "${2}\n\nServer: ${Hostname}\nProgram: ${ScriptName}\nLog: ${LogFile}" -s srv-mail:25 1>/dev/null 2>&1
}
 
function f_sendusermail()
{
  ## Purpose: Send end-user email message.
  ## Parameter #1 = To
  ## Parameter #2 = Subject
  ## Parameter #3 = Body
  sendemail -f "${AdminEmail}" -t "${1}" -u "${2}" -m "${3}" -s srv-mail:25 1>/dev/null 2>&1
}
 
function f_mount()
{
  ## Mount the pre-configured Windows share folder.
  ## NOTE: The Windows share should have a file called "online.txt"
  mount -t cifs //srv-backup/myshare ${OffsiteDir} --options nouser,rw,nofail,noatime,noexec,credentials=/etc/cifspw
}
 
function f_umount()
{
  ## Dismount the Windows share folder.
  ## NOTE: The unmounted folder should have a file called "offline.txt"
  umount ${OffsiteDir}
}
```


/var/scripts/common/standard.conf (contents of the file on the **test** server)
```
## Global Variables ##
Company="abc"
TempDir="/tmp"
LogDir="/var/log"
ShareDir="/srv/samba/share"
MyDomain="mytestdomain.com"
AdminEmail="test1@${MyDomain}"
ReportEmail="test2@${MyDomain}"
BackupDir="/bak"
OffsiteDir="/mnt/fakedir"
OffsiteTestFile="${OffsiteDir}/online.txt"
ArchiveMethod="tar.7z"    ## Choices are tar.7z or tgz
Hostname="$(hostname -s)"
ScriptName="$0"
ScriptDir="/var/scripts"
MailFile="${TempDir}/mailfile.$$"
 
## Global Functions ##
 
function f_sendmail()
{
  ## Purpose: Send administrative email message.
  ## Parameter #1 = Subject
  ## Parameter #2 = Body
  sendemail -f "${AdminEmail}" -t "${ReportEmail}" -u "${1}" -m "${2}\n\nServer: ${Hostname}\nProgram: ${ScriptName}\nLog: ${LogFile}" -s srv-mail:25 1>/dev/null 2>&1
}
 
function f_sendusermail()
{
  ## Purpose: Send end-user email message.
  ## Parameter #1 = To
  ## Parameter #2 = Subject
  ## Parameter #3 = Body
  sendemail -f "${AdminEmail}" -t "${1}" -u "${2}" -m "${3}" -s srv-mail:25 1>/dev/null 2>&1
}
 
function f_mount()
{
  ## Mount the pre-configured Windows share folder.
  ## NOTE: The Windows share should have a file called "online.txt"
  mount -t cifs //mypc/share ${OffsiteDir} --options nouser,rw,nofail,noexec,credentials=/etc/cifspw
}
 
function f_umount()
{
  ## Dismount the Windows share folder.
  ## NOTE: The unmounted folder should have a file called "offline.txt"
  umount ${OffsiteDir}
}
```
 
 
When receiving administrative email notifications, the server name, script name and path will be included at the bottom of the email every time. It will be readily apparent if the email was generated from the test, qa or production server simply because of the location (even if test, qa and production are all on the same server).
 
Here are the scripts to help automate the creation of this structure on the various servers (would run all of them if all are the same box)
 
setup-script-prod.sh
```
#!/bin/bash
if [ ! -d /var/scripts/prod ]; then
  mkdir -p /var/scripts/prod
fi
if [ ! -d /var/scripts/common ]; then
  mkdir -p /var/scripts/common
fi
if [ ! -d /var/scripts/data ]; then
  mkdir -p /var/scripts/data
fi
chown root:root -R /var/scripts
chmod 0755 -R /var/scripts
```
 
setup-script-qa.sh
```
#!/bin/bash
if [ ! -d /var/scripts/qa ]; then
  mkdir -p /var/scripts/qa
fi
if [ ! -d /var/scripts/common ]; then
  mkdir -p /var/scripts/common
fi
if [ ! -d /var/scripts/data ]; then
  mkdir -p /var/scripts/data
fi
chown root:root -R /var/scripts
chmod 0777 -R /var/scripts
```
 
setup-script-test.sh
```
#!/bin/bash
if [ ! -d /var/scripts/test ]; then
  mkdir -p /var/scripts/test
fi
if [ ! -d /var/scripts/common ]; then
  mkdir -p /var/scripts/common
fi
if [ ! -d /var/scripts/data ]; then
  mkdir -p /var/scripts/data
fi
chown root:root -R /var/scripts
chmod 0777 -R /var/scripts
```

---

### Post by LHammonds on 2017-10-03
[SIZE=5]Check Storage Space[/SIZE]
 
In favor of managing by exception, this script that can be scheduled to run daily to check the file systems to see if they are getting close to filling up and will automatically expand them a little bit and give you an email notice. Everything is done at the megabyte level. If you do not want the script to perform the increase, simply add a pound sign in front of the resize2fs command on line 62 to comment it out. Might also want to modify the log and email messages so it does not look like it actually "performed" the resize but instead is telling YOU how to perform the resize.
 
Here are the lines added to the root crontab schedule which will check each file system.
 
The script check the specified file system and see if the amount of space free is less than the threshold (e.g. 100 MB). If the file system has free space that is less than the threshold, it will attempt to add the specified amount (e.g. 50 MB).
 
crontab
```
0 1 * * * /var/scripts/prod/check-storage.sh root 500 100 > /dev/null 2>&1
15 1 * * * /var/scripts/prod/check-storage.sh home 100 50 > /dev/null 2>&1
30 1 * * * /var/scripts/prod/check-storage.sh tmp 100 50 > /dev/null 2>&1
45 1 * * * /var/scripts/prod/check-storage.sh usr 100 50 > /dev/null 2>&1
0 2 * * * /var/scripts/prod/check-storage.sh var 100 50 > /dev/null 2>&1
15 2 * * * /var/scripts/prod/check-storage.sh srv 100 50 > /dev/null 2>&1
30 2 * * * /var/scripts/prod/check-storage.sh opt 100 50 > /dev/null 2>&1
45 2 * * * /var/scripts/prod/check-storage.sh bak 100 50 > /dev/null 2>&1
```
/var/scripts/prod/check-storage.sh
```
#!/bin/bash
#############################################
## Name          : check-storage.sh
## Version       : 1.2
## Date          : 2017-03-17
## Author        : LHammonds
## Purpose       : Check available space for a file system and expand if necessary.
## Compatibility : Verified on Ubuntu Server 12.04 thru 16.04 LTS
## Requirements  : None
## Run Frequency : Recommend once per day for each FS to monitor.
## Parameters    :
##    1 = (Required) File System name (e.g. var)
##    2 = (Required) File System Threshold in MB (e.g. 50)
##    3 = (Required) Amount to increase File System in MB (e.g. 50)
## Exit Codes    :
##    0 = Success (either nothing was done or FS expanded without error)
##    1 = ERROR: Missing or incorrect parameter(s)
##    2 = ERROR: Invalid parameter value(s)
##    4 = ERROR: Lock file detected
##    8 = ERROR: Resize2fs error
##   16 = SEVERE: No room to expand
##   32 = ERROR: Script not run by root user
################ CHANGE LOG #################
## DATE       WHO WHAT WAS CHANGED
## ---------- --- ----------------------------
## 2012-05-11 LTH Created script.
## 2013-03-11 LTH Added company prefix to logs.
## 2017-03-17 LTH Adjusted variable casing.
#############################################

## Import standard variables and functions. ##
source /var/scripts/common/standard.conf

## Define local variables.
LogFile="${LogDir}/${Company}-check-storage.log"
LockFile="${TempDir}/${Company}-check-storage.lock"
ErrorFlag=0
ReturnCode=0

#######################################
##            FUNCTIONS              ##
#######################################

function f_cleanup()
{
  if [ -f ${LockFile} ];then
    ## Remove lock file so other check space jobs can run.
    rm ${LockFile} 1>/dev/null 2>&1
  fi
  exit ${ErrorFlag}
}

function f_showhelp()
{
  echo -e "\nUsage : ${ScriptName} FileSystemName ThresholdSizeInMB AmountToIncreaseByInMB\n"
  echo -e "\nExample: ${ScriptName} var 50 50\n"
}

function f_auto-increment()
{
  let RoomInLV=${LVSize}-${FSSize}
  if [[ ${RoomInLV} -gt ${FSIncreaseBy} ]]; then
    ## There is room in the LV to increase space to the FS.
    resize2fs ${FSVol} ${NewFSSize}M
    ReturnCode=$?
    echo "`date +%Y-%m-%d_%H:%M:%S` --- resize2fs ${FSVol} ${NewFSSize}M, ReturnCode=${ReturnCode}" | tee -a ${LogFile}
    if [[ ${ReturnCode} -ne 0 ]]; then
      ## There was an error in resize2fs.
      return ${ReturnCode}
    fi
  else
    ## There is not enough room in the LV to increase space in the FS.
    return 50
  fi
  return 0
}

#######################################
##           MAIN PROGRAM            ##
#######################################

if [ -f ${LockFile} ]; then
  # Lock file detected.  Abort script.
  echo "Check space script aborted"
  echo "This script tried to run but detected the lock file: ${LockFile}"
  echo "Please check to make sure the file does not remain when check space is not actually running."
  f_sendmail "ERROR: check storage script aborted" "This script tried to run but detected the lock file: ${LockFile}\n\nPlease check to make sure the file does not remain when check space is not actually running.\n\nIf you find that the script is not running/hung, you can remove it by typing 'rm ${LockFile}'"
  ErrorFlag=4
  f_cleanup
else
  echo "`date +%Y-%m-%d_%H:%M:%S` ${ScriptName}" > ${LockFile}
fi

## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo "ERROR: Root user required to run this script."
  echo ""
  ErrorFlag=32
  f_cleanup
fi

## Check existance of required command-line parameters.
case "$1" in
  "")
    f_showhelp
    ErrorFlag=1
    f_cleanup
    ;;
  --help|-h|-?)
    f_showhelp
    ErrorFlag=1
    f_cleanup
    ;;
  *)
    FSName=$1
    ;;
esac
case "$2" in
  "")
    f_showhelp
    ErrorFlag=1
    f_cleanup
    ;;
  --help|-h|-?)
    f_showhelp
    ErrorFlag=1
    f_cleanup
    ;;
  *)
    FSThreshold=$2
    ;;
esac
case "$3" in
  "")
    f_showhelp
    ErrorFlag=1
    f_cleanup
    ;;
  --help|-h|-?)
    f_showhelp
    ErrorFlag=1
    f_cleanup
    ;;
  *)
    FSIncreaseBy=$3
    ;;
esac

## Check validity of File System name.
case "${FSName}" in
  "root")
    FSVol="/dev/LVG/root"
    FSMap="/dev/mapper/LVG-root"
    ;;
  "home")
    FSVol="/dev/LVG/home"
    FSMap="/dev/mapper/LVG-home"
    ;;
  "tmp")
    FSVol="/dev/LVG/tmp"
    FSMap="/dev/mapper/LVG-tmp"
    ;;
  "opt")
    FSVol="/dev/LVG/opt"
    FSMap="/dev/mapper/LVG-opt"
    ;;
  "bak")
    FSVol="/dev/LVG/bak"
    FSMap="/dev/mapper/LVG-bak"
    ;;
  "usr")
    FSVol="/dev/LVG/usr"
    FSMap="/dev/mapper/LVG-usr"
    ;;
  "var")
    FSVol="/dev/LVG/var"
    FSMap="/dev/mapper/LVG-var"
    ;;
  "srv")
    FSVol="/dev/LVG/srv"
    FSMap="/dev/mapper/LVG-srv"
    ;;
  *)
    echo "ERROR: ${FSName} does not match a known file system defined in this script."
    f_showhelp
    ErrorFlag=2
    f_cleanup
    ;;
esac

## Check validity of threshold value.
test ${FSThreshold} -eq 0 1>/dev/null 2>&1
if [[ $? -eq 2 ]]; then
  ## Threshold parameter is not an integer.
  echo "ERROR: ${FSThreshold} is not an integer."
  f_showhelp
  ErrorFlag=2
  f_cleanup
fi

## Check validity of increment value.
test ${FSIncreaseBy} -eq 0 1>/dev/null 2>&1
if [[ $? -eq 2 ]]; then
  ## FSIncreaseBy parameter is not an integer.
  echo "ERROR: ${FSIncreaseBy} is not an integer."
  f_showhelp
  ErrorFlag=2
  f_cleanup
fi

## Get available space for the file system.
FSAvailable="`df --block-size=m ${FSMap} | awk '{ print $4 }' | tail -n 1 | sed 's/M//'`"

## Get the current size of the File System.
FSSize="`df --block-size=m ${FSMap} | awk '{ print $2 }' | tail -n 1 | sed 's/M//'`"

## Get the current size of the Logical Volume for the File System
LVSize="`lvs --noheadings --nosuffix --units=m ${FSMap} | awk '{ print $4}' | sed 's/[.].*//'`"

## Calculate the new size of the FS in case we need it.
let NewFSSize=${FSSize}+${FSIncreaseBy}

if [[ ${FSAvailable} -lt ${FSThreshold} ]]; then
  echo "`date +%Y-%m-%d_%H:%M:%S` - Starting expansion of ${FSVol}" | tee -a ${LogFile}
  echo "`date +%Y-%m-%d_%H:%M:%S` --- LVSize=${LVSize}MB, FSSize=${FSSize}MB, FSAvail=${FSAvailable}MB, FSThreshold=${FSThreshold}MB, FSIncreaseBy=${FSIncreaseBy}MB" | tee -a ${LogFile}
  ## Run the auto-expansion function.
  f_auto-increment
  ReturnCode=$?
  case ${ReturnCode} in
  0)
    f_sendmail "NOTICE: File System Expanded" "${FSVol} was expanded because it was nearing max capacity.  Please review disk space usage and plan appropriately. LVSize=${LVSize}MB, FSSize=${FSSize}MB, FSAvailable=${FSAvailable}MB, FSThreshold=${FSThreshold}MB, FSIncreaseBy=${FSIncreaseBy}MB"
    ;;
  50)
    echo "`date +%Y-%m-%d_%H:%M:%S` - SEVERE: No room to expand ${FSVol}" | tee -a ${LogFile}
    ErrorFlag=16
    f_sendmail "SEVERE: No room to expand ${FSVol}" "There is not enough room in the Logical Volume to expand the ${FSVol} File System.  Immediate action is required.  Make sure there is free space in the Volume Group 'LVG' and then expand the Logical Volume...then expand the File System.\n\nLVSize=${LVSize}MB, FSSize=${FSSize}MB, FSAvailable=${FSAvailable}MB, FSThreshold=${FSThreshold}MB, FSIncreaseBy=${FSIncreaseBy}MB.\n\nType 'vgs' to see if there is any free space in the Volume Group which can be given to the Logical Volume.\n\nType 'lvs' to see the current sizes of the LVs.\n\nType 'lvdisplay' to see a list of Logical Volumes so you can get the LV Name which is used in the lvextend and resize2fs commands.\n\nType 'lvextend -L+50M /dev/LVG/var' if you want to extend the var Logical Volume by 50 megabytes (assuming there is 50MB available in the Volume Group).\n\nType 'df --block-size=m' to see a list of file systems and their associated size and available space.\n\nType 'resize2fs /dev/LVG/var ${NewFSSize}M' to set the size of var to ${NewFSSize} megabytes. Make sure you set the size to the desired end-result which should be LARGER than the current FS size so you do not lose data."
    ;;
  *)
    echo "`date +%Y-%m-%d_%H:%M:%S` - ERROR: Expansion failure for ${FSVol}" | tee -a ${LogFile}
    ErrorFlag=8
    f_sendmail "ERROR: File System Expansion Failed" "${FSVol} Expansion failed with return code of ${ReturnCode}.  LVSize=${LVSize}MB, FSSize=${FSSize}MB, FSAvailable=${FSAvailable}MB, FSThreshold=${FSThreshold}MB, FSIncreaseBy=${FSIncreaseBy}MB"
    ;;
  esac
  echo "`date +%Y-%m-%d_%H:%M:%S` - Finished expansion of ${FSVol}" | tee -a ${LogFile}
else
  echo "`date +%Y-%m-%d_%H:%M:%S` - ${FSVol} ${FSAvailable}M>${FSThreshold}M No action required." | tee -a ${LogFile}
fi

## Perform cleanup routine.
f_cleanup
```
Here is the typical output when it does not have to increase the FS:
 
/var/log/check-storage.log
```
2017-02-01_01:00:00 - /dev/LVG/root 1377M>500M No action required.
2017-02-01_01:15:00 - /dev/LVG/home 454M>100M No action required.
2017-02-01_01:30:00 - /dev/LVG/tmp 776M>100M No action required.
2017-02-01_01:45:00 - /dev/LVG/usr 1126M>100M No action required.
2017-02-01_02:00:00 - /dev/LVG/var 1417M>100M No action required.
2017-02-01_02:15:00 - /dev/LVG/srv 935M>100M No action required.
2017-02-01_02:30:00 - /dev/LVG/opt 935M>100M No action required.
2017-02-01_02:45:00 - /dev/LVG/bak 1871M>100M No action required.
2017-02-02_01:00:00 - /dev/LVG/root 1377M>500M No action required.
2017-02-02_01:15:00 - /dev/LVG/home 454M>100M No action required.
2017-02-02_01:30:00 - /dev/LVG/tmp 776M>100M No action required.
2017-02-02_01:45:00 - /dev/LVG/usr 1126M>100M No action required.
2017-02-02_02:00:00 - /dev/LVG/var 1417M>100M No action required.
2017-02-02_02:15:00 - /dev/LVG/srv 935M>100M No action required.
2017-02-02_02:30:00 - /dev/LVG/opt 935M>100M No action required.
2017-02-02_02:45:00 - /dev/LVG/bak 1871M>100M No action required.
```
Here is a sample of what the log will look like when it performs increases:
 
/var/log/check-storage.log
```
2017-02-02_01:30:00 - Starting expansion of /dev/LVG/tmp
2017-02-02_01:30:00 --- LVSize=2048MB, FSSize=1004MB, FSAvail=93MB, FSThreshold=100MB, IncreaseBy=50MB
2017-02-02_01:30:00 --- resize2fs /dev/LVG/temp 1054, ReturnCode=0
2017-02-02_01:30:00 - Finished expansion of /dev/LVG/tmp
2017-02-02_02:00:00 - Starting expansion of /dev/LVG/var
2017-02-02_02:00:00 --- LVSize=3072MB, FSSize=1901MB, FSAvail=95MB, FSThreshold=100MB, IncreaseBy=50MB
2017-02-02_02:00:00 --- resize2fs /dev/LVG/var 1951, ReturnCode=0
2017-02-02_02:00:00 - Finished expansion of /dev/LVG/var
2017-02-02_02:45:00 - Starting expansion of /dev/LVG/bak
2017-02-02_02:45:00 --- LVSize=4096MB, FSSize=1996MB, FSAvail=91MB, FSThreshold=100MB, IncreaseBy=50MB
2017-02-02_02:45:00 --- resize2fs /dev/LVG/bak 2044, ReturnCode=0
2017-02-02_02:45:00 - Finished expansion of /dev/LVG/bak
```

---

### Post by LHammonds on 2017-10-03
[SIZE=5]APT Upgrade[/SIZE]
 
This script that can be scheduled to run daily to check for updates and then install them if available.
 
The following is an example of a crontab entry to schedule the script to run once per day @ 3am.
 
/var/scripts/data/crontab.root
```
0 3 * * * /var/scripts/prod/apt-upgrade.sh > /dev/null 2>&1
```
/var/scripts/prod/apt-upgrade.sh
```
#!/bin/bash
#############################################
## Name          : apt-upgrade.sh
## Version       : 1.3
## Date          : 2017-03-16
## Author        : LHammonds
## Purpose       : Keep system updated (rather than use unattended-upgrades)
## Compatibility : Verified on Ubuntu Server 16.04 LTS
## Requirements  : Sendemail, run as root
## Run Frequency : Recommend once per day.
## Parameters    : None
## Exit Codes    :
##    0 = Success
##    1 = ERROR: Lock file detected.
##    2 = ERROR: Not run as root user.
##    4 = ERROR: APT update Error.
##    8 = ERROR: APT upgrade Error.
##   16 = ERROR: APT autoremove Error.
##   32 = ERROR: APT autoclean Error.
##   64 = ERROR: APT clean Error.
################ CHANGE LOG #################
## DATE       WHO WHAT WAS CHANGED
## ---------- --- ----------------------------
## 2012-06-01 LTH Created script.
## 2013-01-08 LTH Allow visible status output if run manually.
## 2013-03-11 LTH Added company prefix to log files.
## 2017-03-16 LTH Made compatible with 16.04 LTS
#############################################

## Import standard variables and functions. ##
source /var/scripts/common/standard.conf

## Define local variables.
LogFile="${LogDir}/${Company}-apt-upgrade.log"
LockFile="${TempDir}/${Company}-apt-upgrade.lock"
ErrorFlag=0
ErrorMsg=""
ReturnCode=0
AptCmd="$(which apt)"
AptGetCmd="$(which apt-get)"

#######################################
##            FUNCTIONS              ##
#######################################
function f_cleanup()
{
  if [ -f ${LockFile} ]; then
    ## Remove lock file so subsequent jobs can run.
    rm ${LockFile} 1>/dev/null 2>&1
  fi
  ## Temporarily pause script in case user is watching output.
  sleep 2
  if [ ${ErrorFlag} -gt 0 ]; then
    ## Display error message to user in case being run manually.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: ${ErrorMsg}" | tee -a ${LogFile}
    ## Email error notice.
    f_sendmail "ERROR ${ErrorFlag}: Script aborted" "${ErrorMsg}"
  fi
  exit ${ErrorFlag}
}

#######################################
##           MAIN PROGRAM            ##
#######################################
clear
if [ -f ${LockFile} ]; then
  # Lock file detected.  Abort script.
  echo "** Script aborted **"
  echo "This script tried to run but detected the lock file: ${LockFile}"
  echo "Please check to make sure the file does not remain when check space is not actually running."
  ErrorMsg="This script tried to run but detected the lock file: ${LockFile}\n\nPlease check to make sure the file does not remain when check space is not actually running.\n\nIf you find that the script is not running/hung, you can remove it by typing 'rm ${LockFile}'"
  ErrorFlag=1
  f_cleanup
else
  echo "`date +%Y-%m-%d_%H:%M:%S` ${ScriptName}" > ${LockFile}
fi
## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo -e "ERROR: Root user required to run this script.\n"
  ErrorMsg="Root user required to run this script."
  ErrorFlag=2
  f_cleanup
fi
echo "`date +%Y-%m-%d_%H:%M:%S` - Begin script." | tee -a ${LogFile}
echo "`date +%Y-%m-%d_%H:%M:%S` --- Apt-Get Update" | tee -a ${LogFile}
${AptGetCmd} update > /dev/null 2>&1
ReturnCode=$?
if [[ "${ReturnCode}" -gt 0 ]]; then
  ErrorMsg="Apt-Get Update return code of ${ReturnCode}"
  ErrorFlag=4
  f_cleanup
fi
echo "`date +%Y-%m-%d_%H:%M:%S` --- Apt-Get Upgrade" | tee -a ${LogFile}
echo "--------------------------------------------------" >> ${LogFile}
${AptGetCmd} --assume-yes upgrade >> ${LogFile} 2>&1
ReturnCode=$?
if [[ "${ReturnCode}" -gt 0 ]]; then
  ErrorMsg="Apt-Get Upgrade return code of ${ReturnCode}"
  ErrorFlag=8
  f_cleanup
fi
echo "--------------------------------------------------" >> ${LogFile}
echo "`date +%Y-%m-%d_%H:%M:%S` --- Apt-Get Autoremove" | tee -a ${LogFile}
echo "--------------------------------------------------" >> ${LogFile}
${AptGetCmd} --assume-yes autoremove >> ${LogFile} 2>&1
ReturnCode=$?
if [[ "${ReturnCode}" -gt 0 ]]; then
  ErrorMsg="Apt-Get Autoremove return code of ${ReturnCode}"
  ErrorFlag=16
  f_cleanup
fi
echo "--------------------------------------------------" >> ${LogFile}
echo "`date +%Y-%m-%d_%H:%M:%S` --- Apt-get Autoclean" | tee -a ${LogFile}
echo "--------------------------------------------------" >> ${LogFile}
${AptGetCmd} autoclean >> ${LogFile} 2>&1
ReturnCode=$?
if [[ "${ReturnCode}" -gt 0 ]]; then
  ErrorMsg="Apt-Get Autoclean return code of ${ReturnCode}"
  ErrorFlag=32
  f_cleanup
fi
echo "--------------------------------------------------" >> ${LogFile}
echo "`date +%Y-%m-%d_%H:%M:%S` --- Apt-get Clean" | tee -a ${LogFile}
echo "--------------------------------------------------" >> ${LogFile}
${AptGetCmd} clean >> ${LogFile} 2>&1
ReturnCode=$?
if [[ "${ReturnCode}" -gt 0 ]]; then
  ErrorMsg="Apt-Get Clean return code of ${ReturnCode}"
  ErrorFlag=64
  f_cleanup
fi
echo "--------------------------------------------------" >> ${LogFile}
echo "`date +%Y-%m-%d_%H:%M:%S` - End script." | tee -a ${LogFile}

## Perform cleanup routine.
f_cleanup
```
Here is the typical output:
 
/var/log/apt-upgrade.log
```
2017-03-16_16:15:08 - Begin script.
2017-03-16_16:15:08 --- Apt-Get Update
2017-03-16_16:15:11 --- Apt-Get Upgrade
--------------------------------------------------
Reading package lists...
Building dependency tree...
Reading state information...
Calculating upgrade...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--------------------------------------------------
2017-03-16_16:15:12 --- Apt-Get Autoremove
--------------------------------------------------
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--------------------------------------------------
2017-03-16_16:15:13 --- Apt-get Autoclean
--------------------------------------------------
Reading package lists...
Building dependency tree...
Reading state information...
--------------------------------------------------
2017-03-16_16:15:13 --- Apt-get Clean
--------------------------------------------------
```

---

### Post by LHammonds on 2017-10-03
[SIZE=5]Backup Partitions Using LVM Snapshots and FSArchiver[/SIZE]

This method will allow online backup of the server at the partition level. It is designed to run via crontab schedule but can also be run manually.
 
This should be considered a full backup which means you will probably need to rely on other methods for granular backups and restores such as using rsync at the file level.
 
This method is great for backing up a system just prior to and just after a major upgrade of the OS or application. It is not very helpful for retrieving individual files although it could be done but would require a bit of work by temporarily restoring to an unused area, retrieving the file(s) and then destroying the temporary partition.
 
The /bak partition is skipped because that is where the archives are being stored.
 
The /tmp partition is skipped because there should not be anything in there that needs to be restored...but feel free to include it if you like.
 
The script below was built around a few very basic commands that do the bulk of the work but most of the code is for error handling.
 
Here are examples of the commands:
```
## Create the snapshot volume of the partition to be backed up.
lvcreate --size=5G --snapshot --name="tempsnap" /dev/LVG/root
 
## Create the compressed and encrypted archive of the snapshot.
fsarchiver savefs --compress=7 --jobs=1 --cryptpass="abc123" --label="insert comment here" /bak/root.fsa /dev/LVG/tempsnap
 
## Create an informational text file about the archive.
fsarchiver archinfo --cryptpass="abc123" /bak/root.fsa > /bak/root.txt 2>&1
 
## Remove the snapshot.
lvremove --force /dev/LVG/tempsnap
 
## Create a checksum file about the archive.
md5sum /bak/root.fsa > /bak/root.md5
 
## Verify that the checksum file can validate against the archive.
md5sum --check /bak/root.md5
```
 
Here is an example of a crontab entry to run the script once a day.
 
/var/scripts/data/crontab.root
```
0 4 * * * /var/scripts/prod/back-parts.sh > /dev/null 2>&1
```
 
Here is the script.
 
/var/scripts/prod/back-parts.sh
```
#!/bin/bash
#############################################################
## Name : back-parts.sh (Backup Partitions)
## Version : 1.3
## Date : 2017-10-04
## Author : LHammonds
## Purpose : Backup partitions
## Compatibility : Verified on Ubuntu Server 12.04 thru 16.04 LTS (fsarchiver 0.6.12)
## Requirements : Fsarchiver, Sendemail, run as root
## Run Frequency : Once per day or as often as desired.
## Parameters : None
## Exit Codes :
## 0  = Success
## 1  = ERROR: Lock file detected
## 2  = ERROR: Must be root user
## 4  = ERROR: Missing software
## 8  = ERROR: LVM problems
## 16 = ERROR: File creation problems
## 32 = ERROR: Mount/Unmount problems
###################### CHANGE LOG ###########################
## DATE       VER WHO WHAT WAS CHANGED
## ---------- --- --- ---------------------------------------
## 2013-01-09 1.0 LTH Created script.
## 2017-03-16 1.1 LTH Updated variable standards.
## 2017-08-31 1.2 LTH Added create folder if not exist.
## 2017-10-04 1.3 LTH Set file permissions.
#############################################################

## Import standard variables and functions. ##
source /var/scripts/common/standard.conf

## Define local variables.
LogFile="${LogDir}/${Company}-back-parts.log"
LockFile="${TempDir}/${Company}-back-parts.lock"
LVG="/dev/LVG"
TempLV="${LVG}/tempsnap"
MaxTempVolSize=1G
ErrorFlag=0
ReturnCode=0
CryptPass="abc123"

#######################################
##            FUNCTIONS              ##
#######################################

function f_cleanup()
{
  if [ -f ${LockFile} ];then
    ## Remove lock file so other check space jobs can run.
    rm ${LockFile} 1>/dev/null 2>&1
  fi
  if [ ${ErrorFlag} != 0 ]; then
    f_sendmail "ERROR: Script Failure" "Please review the log file on ${Hostname}${LogFile}"
    echo "`date +%Y-%m-%d_%H:%M:%S` - Backup aborted." >> ${LogFile}
  fi
  exit ${ErrorFlag}
}

function f_archive_fs()
{
  FSName=$1
  FSPath=$2

  ## Purge old backup files.
  if [ -f ${BackupDir}/${Hostname}-${FSName}.fsa ]; then
    rm ${BackupDir}/${Hostname}-${FSName}.fsa
  fi
  if [ -f ${BackupDir}/${Hostname}-${FSName}.txt ]; then
    rm ${BackupDir}/${Hostname}-${FSName}.txt
  fi
  if [ -f ${BackupDir}/${Hostname}-${FSName}.md5 ]; then
    rm ${BackupDir}/${Hostname}-${FSName}.md5
  fi

  ## Unmount FileSystem.
  umount /${FSName}

  LVLabel="${Hostname}:${FSPath}->/${FSName}"
  ## Create the compressed and encrypted archive of the snapshot.
  fsarchiver savefs --compress=7 --jobs=1 --cryptpass="${CryptPass}" --label="${LVLabel}" ${BackupDir}/${Hostname}-${FSName}.fsa ${FSPath} > /dev/null 2>&1
  ReturnCode=$?
  if [ ${ReturnCode} != 0 ]; then
    ## Creation of the archive failed.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: Creation of ${BackupDir}/${FSName}.fsa failed, Return Code = ${ReturnCode}" >> ${LogFile}
    ErrorFlag=16
    f_cleanup
  fi

  ## Create an informational text file about the archive.
  fsarchiver archinfo --cryptpass="${CryptPass}" ${BackupDir}/${Hostname}-${FSName}.fsa > ${BackupDir}/${Hostname}-${FSName}.txt 2>&1
  ReturnCode=$?
  if [ ${ReturnCode} != 0 ]; then
    ## Creation of info text failed.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: Creation of info file failed for ${BackupDir}/${FSName}.txt, Return Code = ${ReturnCode}" >> ${LogFile}
    ErrorFlag=16
    f_cleanup
  fi

  ## Create a checksum file about the archive.
  md5sum ${BackupDir}/${Hostname}-${FSName}.fsa > ${BackupDir}/${Hostname}-${FSName}.md5
  ReturnCode=$?
  if [ ${ReturnCode} != 0 ]; then
    ## Creation of md5 checksum failed.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: Creation of checksum failed for ${BackupDir}/${FSName}.md5, Return Code = ${ReturnCode}" >> ${LogFile}
    ErrorFlag=16
    f_cleanup
  fi

  ## Verify that the checksum file can validate against the archive.
  md5sum --check --status ${BackupDir}/${Hostname}-${FSName}.md5
  ReturnCode=$?
  if [ ${ReturnCode} != 0 ]; then
    ## Verification failed.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: md5 validation check failed for ${BackupDir}/${FSName}.md5. Return Code = ${ReturnCode}" >> ${LogFile}
    ErrorFlag=16
    f_cleanup
  fi

  ## Set file permissions.
  chmod 0600 ${BackupDir}/${Hostname}-${FSName}.*

  BackupSize=`ls -lak --block-size=m "${BackupDir}/${Hostname}-${FSName}.fsa" | awk '{ print $5 }'`

  echo "`date +%Y-%m-%d_%H:%M:%S` --- Created: ${BackupDir}/${Hostname}-${FSName}.fsa, ${BackupSize}" >> ${LogFile}

  ## Make sure target folder exists.
  if [ ! -d ${OffsiteDir}/${Hostname} ]; then
    ## Create folder.  This is typical of 1st time use.
    mkdir -p ${OffsiteDir}/${Hostname}
  fi
  ## Copy the backup to an offsite storage location.
  echo "`date +%Y-%m-%d_%H:%M:%S` --- Copying archive file to offsite location." >> ${LogFile}
  cp ${BackupDir}/${Hostname}-${FSName}.* ${OffsiteDir}/${Hostname}/. 1>/dev/null 2>&1
  if [ ! -f ${OffsiteDir}/${Hostname}/${Hostname}-${FSName}.fsa ]; then
    ## NON-FATAL ERROR: Copy command did not work.  Send email notification.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- WARNING: Remote copy failed. ${OffsiteDir}/${Hostname}/${Hostname}-${FSName}.fsa does not exist!" >> ${LogFile}
    f_sendmail "Backup Failure - Remote Copy" "Remote copy failed. ${OffsiteDir}/${Hostname}/${Hostname}-${FSName}.fsa does not exist\n\nBackup file still remains in this location: ${Hostname}:${BackupDir}/${Hostname}-${FSName}.fsa"
  fi

  ## Remount FileSystem.
  mount /${FSName}
}

function f_archive_vol()
{
  LVName=$1
  LVPath=${LVG}/${LVName}

  ## Purge old backup files.
  if [ -f ${BackupDir}/${Hostname}-${LVName}.fsa ]; then
    rm ${BackupDir}/${Hostname}-${LVName}.fsa
  fi
  if [ -f ${BackupDir}/${Hostname}-${LVName}.txt ]; then
    rm ${BackupDir}/${Hostname}-${LVName}.txt
  fi
  if [ -f ${BackupDir}/${Hostname}-${LVName}.md5 ]; then
    rm ${BackupDir}/${Hostname}-${LVName}.md5
  fi

  ## Create the snapshot volume of the partition to be backed up.
  lvcreate --size=${MaxTempVolSize} --snapshot --name="tempsnap" ${LVPath} > /dev/null 2>&1
  ReturnCode=$?
  if [ ${ReturnCode} != 0 ]; then
    ## Creation of temporary volume failed.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: Creation of temp volume failed for ${LVPath}, size=${MaxTempVolSize}, Return Code = ${ReturnCode}" >> ${LogFile}
    ErrorFlag=8
    f_cleanup
  fi

  ## Give the OS a moment to let the LV create command do its thing.
  sleep 2

  LVLabel="${Hostname}:${LVPath}"
  ## Create the compressed and encrypted archive of the snapshot.
  fsarchiver savefs --compress=7 --jobs=1 --cryptpass="${CryptPass}" --label="${LVLabel}" ${BackupDir}/${Hostname}-${LVName}.fsa ${TempLV} > /dev/null 2>&1
  ReturnCode=$?
  if [ ${ReturnCode} != 0 ]; then
    ## Creation of the archive failed.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: Creation of ${BackupDir}/${Hostname}-${LVName}.fsa failed, Return Code = ${ReturnCode}" >> ${LogFile}
    ErrorFlag=16
    f_cleanup
  fi

  ## Create an informational text file about the archive.
  fsarchiver archinfo --cryptpass="${CryptPass}" ${BackupDir}/${Hostname}-${LVName}.fsa > ${BackupDir}/${Hostname}-${LVName}.txt 2>&1
  ReturnCode=$?
  if [ ${ReturnCode} != 0 ]; then
    ## Creation of info text failed.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: Creation of info file failed for ${BackupDir}/${Hostname}-${LVName}.txt, Return Code = ${ReturnCode}" >> ${LogFile}
    ErrorFlag=16
    f_cleanup
  fi

  ## Create a checksum file about the archive.
  md5sum ${BackupDir}/${Hostname}-${LVName}.fsa > ${BackupDir}/${Hostname}-${LVName}.md5
  ReturnCode=$?
  if [ ${ReturnCode} != 0 ]; then
    ## Creation of md5 checksum failed.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: Creation of checksum failed for ${BackupDir}/${Hostname}-${LVName}.md5, Return Code = ${ReturnCode}" >> ${LogFile}
    ErrorFlag=16
    f_cleanup
  fi

  ## Set file permissions.
  chmod 0600 ${BackupDir}/${Hostname}-${LVName}.*

  ## Remove the snapshot.
  lvremove --force ${TempLV} > /dev/null 2>&1
  ReturnCode=$?
  if [ ${ReturnCode} != 0 ]; then
    ## Removal of temporary volume failed.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: Removal of temp volume failed. ${TempLV}. Return Code = ${ReturnCode}" >> ${LogFile}
    ErrorFlag=8
    f_cleanup
  fi

  ## Give the OS a moment to let the LV remove command do its thing.
  sleep 2

  ## Verify that the checksum file can validate against the archive.
  md5sum --check --status ${BackupDir}/${Hostname}-${LVName}.md5
  ReturnCode=$?
  if [ ${ReturnCode} != 0 ]; then
    ## Verification failed.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: md5 validation check failed for ${BackupDir}/${Hostname}-${LVName}.md5. Return Code = ${ReturnCode}" >> ${LogFile}
    ErrorFlag=16
    f_cleanup
  fi

  BackupSize=`ls -lak --block-size=m "${BackupDir}/${Hostname}-${LVName}.fsa" | awk '{ print $5 }'`

  echo "`date +%Y-%m-%d_%H:%M:%S` --- Created: ${BackupDir}/${Hostname}-${LVName}.fsa, ${BackupSize}" >> ${LogFile}

  ## Make sure target folder exists.
  if [ ! -d ${OffsiteDir}/${Hostname} ]; then
    ## Create folder.  This is typical of 1st time use.
    mkdir -p ${OffsiteDir}/${Hostname}
  fi
  ## Copy the backup to an offsite storage location.
  echo "`date +%Y-%m-%d_%H:%M:%S` --- Copying archive file to offsite location." >> ${LogFile}
  cp ${BackupDir}/${Hostname}-${LVName}.* ${OffsiteDir}/${Hostname}/. 1>/dev/null 2>&1
  if [ ! -f ${OffsiteDir}/${Hostname}/${Hostname}-${LVName}.fsa ]; then
    ## NON-FATAL ERROR: Copy command did not work.  Send email notification.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- WARNING: Remote copy failed. ${OffsiteDir}/${Hostname}/${Hostname}-${LVName}.fsa does not exist!" >> ${LogFile}
    f_sendmail "Backup Failure - Remote Copy" "Remote copy failed. ${OffsiteDir}/${Hostname}/${Hostname}-${LVName}.fsa does not exist\n\nBackup file still remains in this location: ${Hostname}:${BackupDir}/${Hostname}-${LVName}.fsa"
  fi
}

#######################################
##           MAIN PROGRAM            ##
#######################################

if [ -f ${LockFile} ]; then
  # Lock file detected.  Abort script.
  echo "Backup partitions script aborted"
  echo "This script tried to run but detected the lock file: ${LockFile}"
  echo "Please check to make sure the file does not remain when backup partitions is not actually running."
  f_sendmail "ERROR: Backup partitions script aborted" "This script tried to run but detected the lock file: ${LockFile}\n\nPlease check to make sure the file does not remain when backup partitions is not actually running.\n\nIf you find that the script is not running/hung, you can remove it by typing 'rm ${LockFile}'"
  ErrorFlag=1
  exit ${ErrorFlag}
else
  echo "`date +%Y-%m-%d_%H:%M:%S` ${ScriptName}" > ${LockFile}
fi

## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo "`date +%Y-%m-%d_%H:%M:%S` ERROR: Root user required to run this script." >> ${LogFile}
  ErrorFlag=2
  f_cleanup
fi

## Requirement Check: Software
command -v fsarchiver > /dev/null 2>&1 && ReturnCode=0 || ReturnCode=1
if [ ${ReturnCode} = 1 ]; then
  ## Required program not installed.
  echo "`date +%Y-%m-%d_%H:%M:%S` ERROR: fsarchiver not installed." >> ${LogFile}
  ErrorFlag=4
  f_cleanup
fi

## Mount the remote folder. ##
f_mount

if [ -f ${OffsiteTestFile} ]; then
  ## Found local file.  Assuming failed mount.
  echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: Cannot detect remote location: ${OffsiteTestFile}" >> ${LogFile}
  ErrorFlag=32
  f_cleanup
fi

StartTime="$(date +%s)"
echo "`date +%Y-%m-%d_%H:%M:%S` - Backup started." >> ${LogFile}

f_archive_fs boot /dev/sda1
f_archive_vol root
f_archive_vol var
f_archive_vol tmp
f_archive_vol home
f_archive_vol usr
f_archive_vol srv
f_archive_vol opt
#f_archive_vol swap

## Unmount the Windows shared folder.
f_umount

## Calculate total time for backup.
FinishTime="$(date +%s)"
ElapsedTime="$(expr ${FinishTime} - ${StartTime})"
Hours=$((${ElapsedTime} / 3600))
ElapsedTime=$((${ElapsedTime} - ${Hours} * 3600))
Minutes=$((${ElapsedTime} / 60))
Seconds=$((${ElapsedTime} - ${Minutes} * 60))

echo "`date +%Y-%m-%d_%H:%M:%S` --- Total backup time: ${Hours} hour(s) ${Minutes} minute(s) ${Seconds} second(s)" >> ${LogFile}

echo "`date +%Y-%m-%d_%H:%M:%S` - Backup Finished." >> ${LogFile}
f_cleanup
```
 
Here is an example of the log file:
 
/var/log/back-parts.log
```
2017-02-28_18:19:36 - Backup started.
2017-02-28_18:19:46 --- Created: /bak/srv-ubuntu-boot.fsa, 40M
2017-02-28_18:19:46 --- Created: /bak/srv-ubuntu-home.fsa, 1M
2017-02-28_18:20:33 --- Created: /bak/srv-ubuntu-root.fsa, 96M
2017-02-28_18:20:44 --- Created: /bak/srv-ubuntu-opt.fsa, 1M
2017-02-28_18:20:55 --- Created: /bak/srv-ubuntu-srv.fsa, 1M
2017-02-28_18:22:21 --- Created: /bak/srv-ubuntu-usr.fsa, 162M
2017-02-28_18:23:28 --- Created: /bak/srv-ubuntu-var.fsa, 189M
2017-02-28_18:23:40 --- Backup time: 0 hour(s) 4 minute(s) 4 second(s)
2017-02-28_18:23:40 - Backup Finished.
```
 
An example email notification when a fatal error occurred:
```
From: admin@mydomain.com
Sent: Tuesday, February 28, 2017 6:23:45 PM
To: lhammonds@mydomain.com
Subject: ERROR: Backup partitions script aborted
 
This script tried to run but detected the lock file: /tmp/abc-back-parts.lock

Please check to make sure the file does not remain when backup partitions is not actually running.

If you find that the script is not running/hung, you can remove it by typing 'rm /tmp/abc-back-parts.lock'

Server: srv-ubuntu
Program: /var/scripts/prod/abc-back-parts.sh
Log: /var/log/abc-back-parts.log
```
 
An example email notification when no errors occur and email notifications turned on:
```
From: admin@mydomain.com
To: lhammonds@mydomain.com
Sent: Tuesday, February 28, 2017 6:23:45 PM
Subject: Backup Completed
 
INFO: The partition backup job has completed without any errors.
 
Server: srv-ubuntu
Program: /var/scripts/prod/abc-back-parts.sh
Log: /var/log/abc-back-parts.log
```
 
 
NOTE: If the snapshot volume could not be automatically removed, here is how you do it:
 
```
dmsetup ls
```
```
LVG-srv (252, 6)
LVG-tempsnap    (252, 9)
LVG-opt (252, 7)
LVG-swap        (252, 1)
LVG-root        (252, 0)
LVG-opt-real    (252, 10)
LVG-bak (252, 8)
LVG-tmp (252, 3)
LVG-tempsnap-cow        (252, 11)
LVG-usr (252, 4)
LVG-var (252, 5)
LVG-home        (252, 2)
```
 
```
dmsetup remove LVG-tempsnap
dmsetup remove LVG-tempsnap-cow
```
 
[SIZE=5]Backup Test[/SIZE]
 
Before the partitions are backed on your server, create a couple of empty test files to verify that the restore in the next section will work.
 
Type the following commands:
 
```
touch /important.txt
touch /srv/samba/share/important.txt
```
 
Make sure the above files are included in your backup before testing the restore in the next section.

---

### Post by LHammonds on 2017-10-03
[SIZE=5]Restore Partitions Using SystemRescueCD and FSArchiver[/SIZE]

Partitions cannot be mounted when restoring to them. If services can be stopped that use files on a specific partition, it can be unmounted and restored. However, the root partition can never be restore while the server is online so these instructions will cover the common denominator which requires taking the server offline.
 
The server needs to be booted up with a CD but not just any CD will do because it needs to have FSArchiver on it. For this document, the ISO image from [www.sysresccd.org]("http://www.sysresccd.org") will be used.
 
Once downloaded, the ISO can be burned to a CD-ROM disc or uploaded to your ISO repository such as a LUN. VMware and VirtualBox can attach an ISO image and mount it in the CD-ROM device to allow the virtual machine to boot the ISO image.
 
For this example, the root and srv partitions will be restored.
 
Be sure the partitions have been backed up and the files are sitting in the /bak volume.
 
```
ls -l /bak
```
 
```
-rw-r--r-- 1 root root  41515916 Jun 28 18:19 srv-ubuntu-boot.fsa
-rw-r--r-- 1 root root        59 Jun 28 18:19 srv-ubuntu-boot.md5
-rw-r--r-- 1 root root       732 Jun 28 18:19 srv-ubuntu-boot.txt
-rw-r--r-- 1 root root      8467 Jun 28 18:19 srv-ubuntu-home.fsa
-rw-r--r-- 1 root root        59 Jun 28 18:19 srv-ubuntu-home.md5
-rw-r--r-- 1 root root       730 Jun 28 18:19 srv-ubuntu-home.txt
-rw-r--r-- 1 root root      5045 Jun 28 18:20 srv-ubuntu-opt.fsa
-rw-r--r-- 1 root root        58 Jun 28 18:20 srv-ubuntu-opt.md5
-rw-r--r-- 1 root root       729 Jun 28 18:20 srv-ubuntu-opt.txt
-rw-r--r-- 1 root root  99626058 Jun 28 18:20 srv-ubuntu-root.fsa
-rw-r--r-- 1 root root        59 Jun 28 18:20 srv-ubuntu-root.md5
-rw-r--r-- 1 root root       732 Jun 28 18:20 srv-ubuntu-root.txt
-rw-r--r-- 1 root root      5458 Jun 28 18:20 srv-ubuntu-srv.fsa
-rw-r--r-- 1 root root        58 Jun 28 18:21 srv-ubuntu-srv.md5
-rw-r--r-- 1 root root       728 Jun 28 18:20 srv-ubuntu-srv.txt
-rw-r--r-- 1 root root 169110383 Jun 28 18:22 srv-ubuntu-usr.fsa
-rw-r--r-- 1 root root        58 Jun 28 18:22 srv-ubuntu-usr.md5
-rw-r--r-- 1 root root       730 Jun 28 18:22 srv-ubuntu-usr.txt
-rw-r--r-- 1 root root 198015579 Jun 28 18:23 srv-ubuntu-var.fsa
-rw-r--r-- 1 root root        58 Jun 28 18:23 srv-ubuntu-var.md5
-rw-r--r-- 1 root root       730 Jun 28 18:23 srv-ubuntu-var.txt
```
 
As a little test of the restore, let's delete the two text files created in the previous section:
 
```
rm /important.txt
rm /srv/samba/share/important.txt
```
 
These files should have been included in the backup image. When the restore is complete, these files should return.
 
Insert the CDROM (or mount the ISO image) and boot the server with it.
 
Here is the 1st screen:
[IMG]http://www.hammondslegacy.com/images/linux/SystemRescueCD-menu1.png[/IMG]
 
The server in this document is a 64-bit server so option #6 was chosen.
 
The next screen takes you to the command prompt:
 
[IMG]http://www.hammondslegacy.com/images/linux/SystemRescueCD-menu2.png[/IMG]
 
 
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **mkdir /mnt/test**
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **fsarchiver probe simple**
```
[======DISK======] [=============NAME==============] [====SIZE====] [MAJ] [MIN]
[sda             ] [Virtual disk                   ] [    10.00 GB] [  8] [  0]
[sdb             ] [Virtual disk                   ] [    12.00 GB] [  8] [ 16]
[sdc             ] [Virtual disk                   ] [    12.00 GB] [  8] [ 32]
[sr0             ] [VMware IDE CDR10               ] [   378.96 MB] [ 11] [  0]
 
[=====DEVICE=====] [==FILESYS==] [======LABEL======] [====SIZE====] [MAJ] [MIN]
[loop0           ] [squashfs   ] [<unknown>        ] [   297.63 MB] [  7] [  0]
[sda1            ] [ext2       ] [boot             ] [   190.00 MB] [  8] [  1]
[sda5            ] [LVM2_member] [<unknown>        ] [     9.81 GB] [  8] [  5]
[sdb1            ] [LVM2_member] [<unknown>        ] [    12.00 GB] [  8] [ 17]
[sdc1            ] [LVM2_member] [<unknown>        ] [    12.00 GB] [  8] [ 33]
[dm-0            ] [ext4       ] [root             ] [     3.00 GB] [253] [  0]
[dm-1            ] [swap       ] [<unknown>        ] [     1.86 GB] [253] [  1]
[dm-2            ] [ext4       ] [home             ] [     1.00 GB] [253] [  2]
[dm-3            ] [ext4       ] [tmp              ] [     2.00 GB] [253] [  3]
[dm-4            ] [ext4       ] [usr              ] [     3.00 GB] [253] [  4]
[dm-5            ] [ext4       ] [var              ] [     3.00 GB] [253] [  5]
[dm-6            ] [ext4       ] [srv              ] [     2.00 GB] [253] [  6]
[dm-7            ] [ext4       ] [opt              ] [     2.00 GB] [253] [  7]
[dm-8            ] [ext4       ] [bak              ] [     4.00 GB] [253] [  8]
```
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **mkdir /bak**
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **mount --read-only [COLOR=red]/dev/dm-8[/COLOR] /bak**
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **ls -l /bak**
```
-rw-r--r-- 1 root root  41515916 Jun 28 18:19 srv-ubuntu-boot.fsa
-rw-r--r-- 1 root root        59 Jun 28 18:19 srv-ubuntu-boot.md5
-rw-r--r-- 1 root root       732 Jun 28 18:19 srv-ubuntu-boot.txt
-rw-r--r-- 1 root root      8467 Jun 28 18:19 srv-ubuntu-home.fsa
-rw-r--r-- 1 root root        59 Jun 28 18:19 srv-ubuntu-home.md5
-rw-r--r-- 1 root root       730 Jun 28 18:19 srv-ubuntu-home.txt
-rw-r--r-- 1 root root      5045 Jun 28 18:20 srv-ubuntu-opt.fsa
-rw-r--r-- 1 root root        58 Jun 28 18:20 srv-ubuntu-opt.md5
-rw-r--r-- 1 root root       729 Jun 28 18:20 srv-ubuntu-opt.txt
-rw-r--r-- 1 root root  99626058 Jun 28 18:20 srv-ubuntu-root.fsa
-rw-r--r-- 1 root root        59 Jun 28 18:20 srv-ubuntu-root.md5
-rw-r--r-- 1 root root       732 Jun 28 18:20 srv-ubuntu-root.txt
-rw-r--r-- 1 root root      5458 Jun 28 18:20 srv-ubuntu-srv.fsa
-rw-r--r-- 1 root root        58 Jun 28 18:21 srv-ubuntu-srv.md5
-rw-r--r-- 1 root root       728 Jun 28 18:20 srv-ubuntu-srv.txt
-rw-r--r-- 1 root root 169110383 Jun 28 18:22 srv-ubuntu-usr.fsa
-rw-r--r-- 1 root root        58 Jun 28 18:22 srv-ubuntu-usr.md5
-rw-r--r-- 1 root root       730 Jun 28 18:22 srv-ubuntu-usr.txt
-rw-r--r-- 1 root root 198015579 Jun 28 18:23 srv-ubuntu-var.fsa
-rw-r--r-- 1 root root        58 Jun 28 18:23 srv-ubuntu-var.md5
-rw-r--r-- 1 root root       730 Jun 28 18:23 srv-ubuntu-var.txt
```
 
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **md5sum --check /bak/srv-ubuntu-srv.md5**
```
/bak/srv-ubuntu-srv.fsa: OK
```
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **fsarchiver restfs --cryptpass="[COLOR=red]abc123[/COLOR]" /bak/srv-ubuntu-srv.fsa id=0,dest=[COLOR=red]/dev/dm-6[/COLOR]**
```
Statistics for filesystem 0
* files successfully processed:....regfiles=1, directories=4, symlinks=0, hardlinks=0, specials=0
* files with errors:...............regfiles=0, directories=0, symlinks=0, hardlinks=0, specials=0
```
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **mount --read-only [COLOR=red]/dev/dm-6[/COLOR] /mnt/test**
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **ls -l /mnt/test/samba/share**
```
-rw-r--r-- 1 root root 0 Jun 28 09:21 important.txt
```
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **umount /mnt/test**
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **md5sum --check /bak/srv-ubuntu-root.md5**
```
/bak/srv-ubuntu-root.fsa: OK
```
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **fsarchiver restfs --cryptpass="[COLOR=red]abc123[/COLOR]" /bak/srv-ubuntu-root.fsa id=0,dest=[COLOR=red]/dev/dm-0[/COLOR]**
```
Statistics for filesystem 0
* files successfully processed:....regfiles=8938, directories=1693, symlinks=855, hardlinks=11, specials=80
* files with errors:...............regfiles=0, directories=0, symlinks=0, hardlinks=0, specials=0
```
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **mount --read-only [COLOR=red]/dev/dm-0[/COLOR] /mnt/test**
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **ls -l /mnt/test**
```
drwxr-xr-x   3 root root  1024 Jun 27 12:25 bak
drwxr-xr-x   2 root root  4096 Jun 26 12:37 bin
drwxr-xr-x   4 root root  1024 Jun 26 12:36 boot
drwxr-xr-x  14 root root  4400 Jun 28 09:17 dev
drwxr-xr-x  90 root root  4096 Jun 28 09:17 etc
drwxr-xr-x   4 root root  1024 Jun 26 10:20 home
-rw-r--r--   1 root root     0 Jun 28 09:20 important.txt
lrwxrwxrwx   1 root root    33 Jun 26 10:33 initrd.img -> /boot/initrd.img-3.2.0-25-generic
lrwxrwxrwx   1 root root    33 Jun 26 10:16 initrd.img.old -> /boot/initrd.img-3.2.0-23-generic
drwxr-xr-x  17 root root  4096 Jun 26 12:34 lib
drwxr-xr-x   2 root root  4096 Jun 26 10:16 lib64
drwx------   2 root root 16384 Jun 26 10:15 lost+found
drwxr-xr-x   4 root root  4096 Jun 26 10:16 media
drwxr-xr-x   3 root root  4096 Jun 26 12:35 mnt
drwxr-xr-x   3 root root  1024 Jun 26 10:15 opt
dr-xr-xr-x 111 root root     0 Jun 28 09:17 proc
drwx------   3 root root  4096 Jun 26 19:57 root
drwxr-xr-x  15 root root   500 Jun 28 09:18 run
drwxr-xr-x   2 root root  4096 Jun 26 12:37 sbin
drwxr-xr-x   2 root root  4096 Mar  5 11:54 selinux
drwxr-xr-x   4 root root  1024 Jun 28 08:34 srv
drwxr-xr-x  13 root root     0 Jun 28 09:17 sys
drwxrwxrwt   4 root root  1024 Jun 28 09:18 tmp
drwxr-xr-x  11 root root  4096 Jun 26 10:16 usr
drwxr-xr-x  14 root root  4096 Jun 26 13:08 var
lrwxrwxrwx   1 root root    29 Jun 26 10:33 vmlinuz -> boot/vmlinuz-3.2.0-25-generic
lrwxrwxrwx   1 root root    29 Jun 26 10:16 vmlinuz.old -> boot/vmlinuz-3.2.0-23-generic
```
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **umount /mnt/test**
 
Eject the CDROM/ISO and reboot the server.
 
If it worked right, the server will boot up (we restored the root file system) and the test files should have been restored.
 
NOTE: If you noticed any ext file systems that had <unknown> labels, you can update them using the tune2fs command.
Example 1:
```
tune2fs /dev/sda1 -L boot
```

Example 2:
```
tune2fs /dev/dm-0 root
```

---

### Post by LHammonds on 2017-10-03
[SIZE=5]Crontab Schedule[/SIZE]

The crontab schedule can be edited directly by typing "crontab -e" but that can be a bit dangerous. It would be safer to edit a file and then load that file into the schedule. This will allow backups of the schedule to be made. If there is ever a problem with the schedule, it can be re-loaded with a known-good schedule or at least back to the way it was before the last change. This requires the person doing the editing to always work with a copy of the schedule 1st.

Here is an example crontab scheduling file for the root user:

/var/scripts/data/crontab.root
```
########################################
# Name: Crontab Schedule for root user
# Author: LHammonds
############# Update Log ###############
# 2012-05-20 - LTH - Created schedule
########################################

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# Crontab SYNTAX:
# minute(0-59) hour(0-23) day-of-month(1-31) month(1-12) day-of-week(0-6) command-to-execute
#
# Adjust the time clock
#
0 1-23 * * * /usr/sbin/ntpdate ntp.ubuntu.com > /dev/null 2>&1
#
# Backup MySQL Server
#
0 23 * * * /var/scripts/prod/mysql-backup.sh > /dev/null 2>&1
#
# Backup MySQL Database On Demand
#
0-59 * * * * /var/scripts/prod/mysql-db-backup.sh > /dev/null 2>&1
#
# Daily checks for available space
#
0 1 * * * /var/scripts/prod/check-storage.sh root 500 100 > /dev/null 2>&1
15 1 * * * /var/scripts/prod/check-storage.sh home 100 50 > /dev/null 2>&1
30 1 * * * /var/scripts/prod/check-storage.sh tmp 100 50 > /dev/null 2>&1
45 1 * * * /var/scripts/prod/check-storage.sh usr 100 50 > /dev/null 2>&1
0 2 * * * /var/scripts/prod/check-storage.sh var 100 50 > /dev/null 2>&1
15 2 * * * /var/scripts/prod/check-storage.sh srv 100 50 > /dev/null 2>&1
30 2 * * * /var/scripts/prod/check-storage.sh opt 100 50 > /dev/null 2>&1
45 2 * * * /var/scripts/prod/check-storage.sh bak 100 50 > /dev/null 2>&1
#
# Daily software upgrade check
#
0 3 * * * /var/scripts/prod/apt-upgrade.sh > /dev/null 2>&1
```
Once the file is created, make sure appropriate permissions are set by typing the following:
```
chown root:root /var/scripts/data/crontab.root
chmod 0600 /var/scripts/data/crontab.root
```
To enable the root schedule using this file, type the following:

```
crontab -u root /var/scripts/data/crontab.root
```
To disable the root schedule, type the following:
```
touch /tmp/deleteme
crontab -u root /tmp/deleteme
rm /tmp/deleteme
```
If you need to modify the schedule, make a backup copy 1st. For example:

```
cp /var/scripts/data/crontab.root /var/scripts/data/2012-11-28-crontab.root
vi /var/scripts/data/crontab.root
(make your changes)
crontab -u root /var/scripts/data/crontab.root
```

---

### Post by LHammonds on 2017-10-03
[SIZE=5]Configure Windows Server as a Remote Mount Point[/SIZE]
 
If you have a Windows 2008 server that serves as your offsite backup repository, this section describes how to configure and mount the remote server for storage use.

Part of the backup process involves copying the backup files to an offsite storage server.

First, let's document the variables for this solution below and highlight them in red throughout the document for easy identification.

The values below are merely samples which you need to change in order to match your environment:

Windows AD Domain Name: [COLOR=red]work[/COLOR]
Windows AD Share ID: [COLOR=red]ubuntushare[/COLOR]
Windows AD Share Password: [COLOR=red]ubuntupassword[/COLOR]
Windows Server Name: [COLOR=red]SRV-Backup[/COLOR]
Windows Server IP: [COLOR=red]192.168.107.218[/COLOR]
Windows Share Name: ubuntu
Windows Physical Share Location: [COLOR=red]D:\Ubuntu\[/COLOR]

[SIZE=5]Create a share on a Windows 2008 server[/SIZE]


[LIST=1]
[*]In Windows Explorer, right-click on the [COLOR=red]*D:\Ubuntu*[/COLOR] folder and select **Properties** 
[*]Click the **Sharing** tab 
[*]Click the **Advanced Sharing** button 
[*]Place a checkmark beside **Share this folder** 
[*]Change the Share name to **ubuntu** 
[*]Set the Comment to **Ubuntu Backup** 
[*]Click the **Permissions** button 
[*]Select **Everyone** and click the **Remove** button 
[*]Click the **Add** button 
[*]Type in your Ubuntu share account: [COLOR=red]**work\ubuntushare**[/COLOR] and click the **Check Names** button, click **OK** 
[*]Place a checkmark for **Allow Full Control** and click **OK**, click **OK**, click **OK** 
[*]Create a text file in the root of the shared folder called "online.txt" and you might want to add some text inside saying to never delete this file because it is used (will be) by a backup script.  Probably a good idea to make it read-only as well.  Example: **D:\Ubuntu\online.txt** 
[/LIST]

[SIZE=5]Create an NFS mount to the Windows 2008 server[/SIZE]

Connecting to a Windows share requires the **samba** and **cifs-utils** packages to be installed.  If you did not install them (from a prior section), type **apt -y install samba cifs-utils**


[LIST=1]
[*]At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR]) 
[*]At the $ prompt, temporarily grant yourself super user privileges by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR=red]myadminpass[/COLOR]**). 
[*]Type the following commands:
```
mkdir -p /mnt/backup
chown root:root /mnt/backup
chmod 0755 /mnt/backup
echo "This file is used to tell if the mount is active or not" > /mnt/backup/offline.txt
chown root:root /mnt/backup/offline.txt
chmod 0444 /mnt/backup/offline.txt
touch /etc/cifspw
chmod 0600 /etc/cifspw

``` 
[*]Type **vi /etc/cifspw** and add the following text, save and exit the file:
```
username=ubuntushare
domain=work
password=ubuntupassword
``` 
[*]Type **vi /etc/hosts** and add the following line anywhere in the file:
```
192.168.107.218    srv-backup
``` 
[*]At this point, you might want to type **ping [COLOR=red]srv-backup[/COLOR]** to make sure you typed the right IP address as well as seeing a good response. 
[*]To mount this system for backups, type the following command:
```
mount -t cifs //srv-backup/ubuntu /mnt/backup --options nouser,rw,nofail,noexec,credentials=/etc/cifspw
``` 
[*]To test it, type **cp /etc/hosts /mnt/backup/hosts.txt** and look on the Windows server and see if the file shows up.  Then type **rm /mnt/backup/hosts.txt** and verify that the file was deleted on the windows server. 
[*]This would also be a good time to verify that you can see the "online.txt" file that will be used by the backup script. Type **ls -l /mnt/backup/*.txt** 
[*]To dismount the windows share, type the following command:
```
umount /mnt/backup
``` 
[/LIST]

The scripts will call a common mount and unmount function to connect to this share only when needed.

However, if you would rather have it mounted all the time (even after a reboot), do the following (but remember to not use the mount/umount functions in the scripts later):


[LIST=1]
[*]Type **vi /etc/fstab** and add the following line at the bottom of the file:
```
//srv-backup/ubuntu    /mnt/backup    cifs nouser,rw,nofail,noexec,credentials=/etc/cifspw    0    0
``` 
[*]Type **mount -a** and if it does not spew out any error messages, it will quietly mount the share. 
[*]To test it, type **cp /etc/hosts /mnt/backup/hosts.txt** and look on the Windows server and see if the file shows up.  Then type **rm /mnt/backup/hosts.txt** and verify that the file was deleted on the windows server. 
[*]If you need to unmount it, simply type **umount /mnt/backup** and it will remain unmounted until you reboot.  To make it permanent, you need to remove the line you added in the /etc/fstab file. 
[/LIST]

Sometimes it is helpful during tests to manually toggle the mount on or off so here is a script you might find helpful.  You can find the contents of "standard.conf" file in the scripting section.

togglemount.sh
```
#!/bin/bash
#############################################
## Name          : togglemount.sh
## Version       : 1.1
## Date          : 2017-03-17
## Author        : LHammonds
## Compatibility : Ubuntu Server 10.04 - 16.04 LTS
## Purpose       : Toggle the mount status of a pre-configured backup mount.
## Run Frequency : Manual as needed.
## Exit Codes    :
##   0 = success
##   1 = failure
################ CHANGE LOG #################
## DATE       WHO WHAT WAS CHANGED
## ---------- --- ----------------------------
## 2011-11-05 LTH Created script.
## 2017-03-17 LTH Updated variable standards.
#############################################

## Import common variables and functions. ##
source /var/scripts/common/standard.conf
ErrorFlag=0

if [ -f ${OffsiteDir}/offline.txt ]; then
  echo "Windows share is not mounted.  Mounting share now..."
  f_mount
  sleep 2
  if [ -f ${OffsiteDir}/online.txt ]; then
    echo "Mount successful.  Listing contents:"
  else
    echo "Mount failed.  Listing contents:"
    ErrorFlag=1
  fi
else
  echo "Windows share is mounted.  Dismounting share now..."
  f_umount
  sleep 2
  if [ -f ${OffsiteDir}/offline.txt ]; then
    echo "Dismount successful.  Listing contents:"
  else
    echo "Dismount failed.  Listing contents:"
    ErrorFlag=1
  fi
fi
ls -l ${OffsiteDir}
exit ${ErrorFlag}
```

---

### Post by LHammonds on 2017-10-03
[SIZE=5]SSH Public and Private Keys[/SIZE]
 
If you have more than one Ubuntu server, you probably will want to setup a trusted SSH authentication between the two servers so you can securely and automatically transfer files between them with commands such as scp or sftp.

NOTE: You probably have the root account locked (by default) so you cannot login with root directly.  In order to initially copy the public key, you will need to enable the root account temporarily on all servers.

Temporarily enable login with the root account on each server:

[LIST=1]
[*]Connect to a server using PuTTY. 
[*]At the login prompt, login with your administrator account ([COLOR=red]**administrator**[/COLOR] / [COLOR=red]**myadminpass**[/COLOR]) 
[*]At the $ prompt, temporarily grant yourself super user privileges by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR=red]myadminpass[/COLOR]**). 
[*]Type the following and set the password to the same as your administrator account (**[COLOR=red]myadminpass[/COLOR]**):
```
passwd root
``` 
[*]Edit **/etc/ssh/sshd_config**, and comment out the following from:
```
PermitRootLogin prohibit-password
```
to:
```
#PermitRootLogin prohibit-password
``` 
[*]Just below that line, add the following and then save/exit:
```
PermitRootLogin yes
``` 
[*]Restart SSH:
```
service ssh restart
``` 
[*]Do the same for each of your servers 
[/LIST]


Generate the private/public key on each server:

[LIST=1]
[*]Generate a key by typing the following and accept the default values on everything (even the blank passphrase):
```
mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa -b 4096
``` 
[*]Do the same thing on all your other servers. 
[/LIST]


Transfer the public key to your trusted servers:

[LIST=1]
[*]Type the following command for each server you have (use your own server name or IP instead of my example names):
```
ssh-copy-id root@srv-mysql
ssh-copy-id root@srv-wiki
ssh-copy-id root@srv-ftp
ssh-copy-id root@srv-nagios
``` 
[*]Do the same thing on all your other servers. 
[/LIST]


Lock the root account on each server:

[LIST=1]
[*]Type the following:
```
passwd -l root
``` 
[*]Do the same for each of your servers 
[/LIST]


Set root login to SSH only on each server:

[LIST=1]
[*]Edit **/etc/ssh/sshd_config**, and uncomment the following from:
```
#PermitRootLogin prohibit-password
```
to:
```
PermitRootLogin prohibit-password
``` 
[*]Just below that line, delete the following and then save/exit:
```
PermitRootLogin yes
``` 
[*]Restart SSH:
```
service ssh restart
``` 
[*]Do the same for each of your servers 
[/LIST]


If you have other accounts you want to use across the servers (such as a low-rights account), you can do the same thing as the above except you probably won't need to do the unlock/lock steps for the account if you can already login with that account.

Now you should be able to securely copy files back and forth between servers without having to type a password.

Example:
```
scp /etc/hosts root@srv-mysql:/tmp/hosts.txt
```

---

### Post by LHammonds on 2017-10-03
[SIZE=5]Operator Menu[/SIZE]

To make my servers easier to administer within my group (who are not all *NIX guys), I made an operator script that can be used to manipulate the server.

The main features I wanted to make easier for other members of the IT group are:

1. Update the operating system (manually)
2. Disk Status
3. Memory Status
4. Stop/Restart primary services
5. Cleanly shutdown services and reboot server

I accomplished this by creating a script and making a shortcut to it so the only thing they need to type on each server is "opm" which is short for "Operator Menu"

Here is how to do something similar for your servers.

Create the script file and set the permissions so that only the root user can run the script and make a shortcut for it:

```

touch /var/scripts/prod/opm.sh
chmod 0700 /var/scripts/prod/opm.sh
ln -s /var/scripts/prod/opm.sh /usr/sbin/opm

```

You will need a program called "dialog" installed for this menu to work.

```

apt install dialog

```

Now open the script in your favorite editor and add the following:
/var/scripts/prod/opm.sh
```
#!/bin/bash
#############################################
## Name          : opm.sh
## Version       : 1.1
## Date          : 2017-03-17
## Author        : LHammonds
## Compatibility : Ubuntu Server 12.04-16.04 LTS
## Requirements  : dialog (apt-get dialog) and root privileges
## Purpose       : Display menu to control the server
## Run Frequency : As needed
## Exit Codes    : None
## SymLink Cmd   : ln -s /var/scripts/prod/opm.sh /usr/sbin/opm
################ CHANGE LOG #################
## DATE       WHO  WHAT WAS CHANGED
## ---------- ---- ----------------------------
## 2013-01-07 LTH  Created script.
## 2017-03-17 LTH  Updated variable standards.
#############################################

## Store menu options selected by the user.
TempDir="/tmp"
ScriptDir="/var/scripts/prod"
Input="${TempDir}/opm-input.$$"

## Storage file for displaying cal and date command output.
Output="${TempDir}/opm-output.$$"

## Get text editor or fall back to vi_editor.
vi_editor=${EDITOR-vi}

## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo -e "\nERROR: Root user required to run this script.\n"
  echo -e "Type 'sudo su' to temporarily become root user.\n"
  exit
fi

## Trap and delete temp files.
trap "rm $Output; rm $Input; exit" SIGHUP SIGINT SIGTERM

function f_display_output(){
  ## Purpose - display output using msgbox
  ##  $1 -> set msgbox height
  ##  $2 -> set msgbox width
  ##  $3 -> set msgbox title
  local h=${1-10}     ## box height default 10
  local w=${2-41}     ## box width default 41
  local t=${3-Output} ## box title
  dialog --backtitle "KDC Operator Menu for $(hostname -f)" --title "${t}" --clear --msgbox "$(<$Output)" ${h} ${w}
}

function f_showdate(){
  ## Purpose - display current system date & time
  echo "Today is $(date) @ $(hostname -f)." >$Output
  f_display_output 6 60 "Date and Time"
}

function f_checkdisk(){
  ## Purpose: Display disk status.
  clear
  echo -e "df --block-size=M\n"
  df --block-size=M
  echo ""
  read -p "Press [Enter] key to continue..."
}

## Loop the menu display.
while true
do
  ## Display main menu.
  dialog --clear  --no-cancel --backtitle "Operator Menu for $(hostname -f)" \
  --title "[ M A I N - M E N U ]" \
  --menu "You can use the UP/DOWN arrow keys, the first \n\
  letter of the choice as a hot key, or the \n\
  number keys 1-9 to choose an option.\n\
  Choose the TASK" 19 50 7 \
  Exit "Exit menu" \
  OSUpdate "Update Operating System" \
  CheckDisk "Check Disk Status" \
  MEMCheck "Look at running processes" \
  ServiceRestart "Stop/Start Main Services" \
  Reboot "Cleanly reboot server" \
  Date/time "Displays date and time" 2>"${Input}"

  menuitem=$(<"${Input}")

  ## Make decision.
  case $menuitem in
    OSUpdate) ${ScriptDir}/abc-apt-upgrade.sh;;
    CheckDisk) f_checkdisk;;
    MEMCheck) htop;;
    Reboot) ${ScriptDir}/reboot.sh;;
    ServiceRestart) ${ScriptDir}/servicerestart.sh;;
    Date/time) f_showdate;;
    Exit) clear; echo "Clean menu exit."; break;;
  esac
done

## Delete temp files.
[ -f $Output ] && rm $Output
[ -f $Input ] && rm $Input
```

I like the opm script to as static as possible when copying among the many servers I have so I push the reboot and service restart "logic" into their own scripts which can be unique to each server.

On a MySQL server, the service restart script would look something like this:

/var/scripts/prod/servicerestart.sh
```
#!/bin/bash
#############################################
## Name          : servicerestart.sh
## Version       : 1.0
## Date          : 2013-01-08
## Author        : LHammonds
## Compatibility : Ubuntu Server 12.04-16.04 LTS
## Requirements  : None
## Purpose       : Stop/Start primary services.
## Run Frequency : As needed
## Exit Codes    : None
################ CHANGE LOG #################
## DATE       WHO  WHAT WAS CHANGED
## ---------- ---- ----------------------------
## 2013-01-08 LTH  Created script.
#############################################

clear
echo ""
echo "Stopping services..."
service mysql stop
sleep 1
echo "Starting services..."
service mysql start
sleep 1
```

On a MySQL server, the reboot script would look something like this:

/var/scripts/prod/reboot.sh
```
#!/bin/bash
#############################################
## Name          : reboot.sh
## Version       : 1.0
## Date          : 2013-01-08
## Author        : LHammonds
## Compatibility : Ubuntu Server 12.04-16.04 LTS
## Requirements  : Run as root
## Purpose       : Stop services and reboot server.
## Run Frequency : As needed
## Exit Codes    : None
################ CHANGE LOG #################
## DATE       WHO  WHAT WAS CHANGED
## ---------- ---- ----------------------------
## 2013-01-07 LTH  Created script.
#############################################

## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo -e "\nERROR: Root user required to run this script.\n"
  echo -e "Type 'sudo su' to temporarily become root user.\n"
  exit
fi

clear
echo ""
echo "Stopping MySQL service..."
service mysql stop
echo "Rebooting..."
echo "3"
sleep 1
echo "2"
sleep 1
echo "1"
sleep 1
shutdown -r now
```

[HR][/HR]

[SIZE=5]Customizing Operator Menu[/SIZE]

Let's say you have "mytop" installed on your MySQL server and you want that added to your menu.  This is how you would do that.

Edit the opm.sh file and find this section:

```

  OSUpdate "Update Operating System" \
  CheckDisk "Check Disk Status" \
  MEMCheck "Look at running processes" \
  ServiceRestart "Stop/Start Main Services" \
  Reboot "Cleanly reboot server" \
  Date/time "Displays date and time" 2>"${Input}"

```

Now add the following line so it shows up in your menu:

```

  MySQLCheck "Look at MySQL processes" \

```

End result looking like this:

```

  OSUpdate "Update Operating System" \
  CheckDisk "Check Disk Status" \
  MEMCheck "Look at running processes" \
  MySQLCheck "Look at MySQL processes" \
  ServiceRestart "Stop/Start Main Services" \
  Reboot "Cleanly reboot server" \
  Date/time "Displays date and time" 2>"${Input}"

```

Now that the menu entry is there, we need the menu item to actually do something so find this section below:

```

    OSUpdate) ${ScriptDir}/abc-apt-upgrade.sh;;
    CheckDisk) f_checkdisk;;
    MEMCheck) htop;;
    Reboot) ${ScriptDir}/reboot.sh;;
    ServiceRestart) ${ScriptDir}/servicerestart.sh;;
    Date/time) f_showdate;;
    Exit) clear; echo "Clean menu exit."; break;;

```

Add the following line:

```

    MySQLCheck) mytop;;

```

The end result looking like this:

```

    OSUpdate) ${ScriptDir}/abc-apt-upgrade.sh;;
    CheckDisk) f_checkdisk;;
    MEMCheck) htop;;
    MySQLCheck) mytop;;
    Reboot) ${ScriptDir}/reboot.sh;;
    ServiceRestart) ${ScriptDir}/servicerestart.sh;;
    Date/time) f_showdate;;
    Exit) clear; echo "Clean menu exit."; break;;

```

Save and close the script.

Now when you run opm, you will see the MySQL entry which will run mytop when you select it.

With this menu example, I have given you 3 example types of how you can do something.  You can call the program directly, like mytop or htop, or you can call a function to process several lines of script like f_checkdisk or f_showdate or you can call an external script like reboot.sh or servicerestart.sh which can further isolate individual server needs in other scripts.

---

### Post by LHammonds on 2017-10-03
[SIZE=5]Firewall[/SIZE]

Linux uses IPTables as its firewall but learning the ins and outs of the syntax can be daunting. Luckily for us, Ubuntu has a front-end for it called Uncomplicated Firewall (UFW for short).

If you are not using IPv6 (most networks are still just using IPv4), you can comment out the IPv6 setting so you don't get doubles of each rule (one for IPv4 and one for IPv6).

To disable IPv6 rules:
```
vi /etc/default/ufw
```

Find:
```
IPV6=yes
```
Change to:
```
#IPV6=yes
```

Here is a script I use to configure the firewall rules and turn it on...which will remain on even during a reboot.

You can copy this script and use it for your own purposes and tweak it for your environment.  Enough commands are used/documented in it that you should be able to modify it to fit your particular server.  For example, if running a Minecraft server, you could add a command to allow TCP port 25565.  If you are not running a web server, you could remove the TCP ports 80, 8080 and 443 from the application-specific section.

I "NEVER" simply copy this script and run it.  Each and every server requires a custom variation of this script tailored for it.  The application section is much larger than needed because its much faster to simply remove or edit what is not needed than adding.

enable-firewall.sh
```
#!/bin/bash
#############################################
## Name          : enable-firewall.sh
## Version       : 1.1
## Date          : 2017-04-13
## Author        : LHammonds
## Compatibility : Ubuntu Server 14.04-16.04 LTS
## Requirements  : Run as root
## Purpose       : Restore and enable firewall.
## Run Frequency : As needed
## Exit Codes    : None
################ CHANGE LOG #################
## DATE       WHO  WHAT WAS CHANGED
## ---------- ---- ----------------------------
## 2015-08-28 LTH  Created script.
## 2017-04-13 LTH  Added comments in rules.
#############################################

## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo -e "\nERROR: Root user required to run this script.\n"
  echo -e "Type 'sudo su' to temporarily become root user.\n"
  exit
fi

clear
echo ""
echo "Resetting Firewall to factory default"
echo y | ufw reset 1>/dev/null 2>&1
ufw default deny incoming 1>/dev/null 2>&1
ufw default allow outgoing 1>/dev/null 2>&1
echo "Allowing SSH from only LAN connections"
ufw allow from 192.168.1.0/24 to any port 22 comment 'SSH via LAN' 1>/dev/null 2>&1
echo "Allowing Samba file sharing connections"
ufw allow proto tcp to any port 135,139,445 comment 'Samba Share' 1>/dev/null 2>&1
ufw allow proto udp to any port 137,138 comment 'Samba Share' 1>/dev/null 2>&1
echo "Allowing Nagios connections"
ufw allow from 192.168.107.21 to any port 12489 comment 'Nagios' 1>/dev/null 2>&1
ufw allow from 192.168.107.21 proto tcp to any port 5666 comment 'Nagios' 1>/dev/null 2>&1
echo "Adding Application-specific rules"
echo "Adding MySQL/MariaDB rules"
ufw allow from 192.168.107.0/24 proto tcp to any port 3306 comment 'MariaDB via LAN' 1>/dev/null 2>&1
ufw allow from 192.168.2.0/24 proto tcp to any port 3306 comment 'MariaDB via LAN' 1>/dev/null 2>&1
echo "Adding FTP/FTPS rules"
ufw allow proto tcp to any port 990 comment 'FTPS' 1>/dev/null 2>&1
ufw allow proto tcp to any port 21 comment 'FTP' 1>/dev/null 2>&1
ufw allow proto tcp to any port 2000:2020 comment 'FTP Passive' 1>/dev/null 2>&1
echo "Adding Web Server rules"
ufw allow proto tcp to any port 80 comment 'Web Service' 1>/dev/null 2>&1
ufw allow proto tcp to any port 8080 comment 'Web Service' 1>/dev/null 2>&1
ufw allow proto tcp to any port 443 comment 'Web Service' 1>/dev/null 2>&1
echo "Enabling firewall"
echo y | ufw enable 1>/dev/null 2>&1
echo "Firewall enabled and all rules have been configured."

```

---

### Post by LHammonds on 2017-10-03
[SIZE=5]Boot Issues[/SIZE]

```
systemd-analyze plot > /srv/samba/share/boot.xml
```
Open boot.xml in a web browser to examine the boot process to see if anything is taking longer than it should.

```
systemd-analyze blame
```
This shows a list of all running processes ordered by the time it took to initialize.  Be careful not to judge a process too harshly at 1st sight...it may have been waiting on another process to initialize 1st.

```
dmesg > /tmp/boot.txt
```
Open boot.txt and observe the order of events from the moment it starts its boot all the way to the end.  The events are ordered by time and it shows how much time has passed since the machine was turned on for that particular event to occur.

---

### Post by LHammonds on 2017-10-03
[SIZE=5]NFS Mount (Linux to Linux)[/SIZE]

If you want to share files between Linux servers, you can use NFS.  Here is how you can do that.

On the machine that will host the files to be shared:


[LIST=1]
[*]Install the required software:
```
apt install nfs-kernel-server
``` 
[*]Configure a folder to be shared:
```
vi /etc/exports
``` 
[*]Add the following line, adjust as necessary and then save and close the file:
```
/srv/samba/share        *(rw,sync,no_root_squash,no_subtree_check)
``` 
[*]Make the folder and configure ownership and permissions:
```
mkdir -p /srv/samba/share
chown nobody:nogroup /srv/samba/share
chmod 777 /srv/samba/share
``` 
[*]Restart services for changes to take effect:
```
systemctl restart nfs-kernel-server
``` 
[*]If your UFW firewall is enabled, you will need to open port 2049 TCP and UDP.  Example:
```
ufw allow proto tcp to any port 2049
ufw allow proto udp to any port 2049
``` 
[/LIST]


On the machine that will connect to the other remotely:

[LIST=1]
[*]Install the required software:
```
apt install nfs-common
``` 
[*]Create the mount point folder:
```
mkdir -p /mnt/nfs
touch /mnt/nfs/offline.txt
``` 
[*]Now connect to the server. We will assume the server's IP doing the sharing is [COLOR=red]192.168.107.100[/COLOR] in this example.
```
mount 192.168.107.100:/srv/samba/share /mnt/nfs
``` 
[*]If the mount was successful, you will not see the "offline.txt" file we created at the mount point. 
[*]To disconnect from the server, type the following:
```
umount /mnt/nfs
``` 
[*]If the unmount was successful, you will see the "offline.txt" file. 
[/LIST]

---

### Post by LHammonds on 2017-10-03
[SIZE=5]Migrating users/groups from one server to another[/SIZE]

**[COLOR=#FF0000]WARNING:[/COLOR]** These migration commands are completely untested by me...just jotting down these research notes for future testing.

_Commands to run on old server_

Copy accounts to passwd.mig using awk to filter out system accounts (i.e. only copy user accounts)
```
awk -v LIMIT=1000 -F: '($3>=LIMIT) && ($3!=65534)' /etc/passwd > /tmp/passwd.mig
```

Copy groups to group.mig
```
awk -v LIMIT=1000 -F: '($3>=LIMIT) && ($3!=65534)' /etc/group > /tmp/group.mig
```

Copy shadow to shadow.mig
```
awk -v LIMIT=1000 -F: '($3>=LIMIT) && ($3!=65534) {print $1}' /etc/passwd | tee - |egrep -f - /etc/shadow > /tmp/shadow.mig
```

Copy gshadow to gshadow.mig (rarely used):
```
cp /etc/gshadow /tmp/gshadow.mig
```

Backup the home directories.
```
tar -zcvpf /tmp/home.tar.gz /home
```

If you have Samba users...
```
cp /etc/samba/smb.conf /tmp/smb.mig
cp /etc/samba/smbusers /tmp/smbusers.mig
cp /etc/samba/smbpasswd /tmp/smbpasswd.mig
```

Transfer the migration files to new server.
```
scp /tmp/*.mig administrator@newserver:/tmp/.
scp /tmp/home.tar.gz administrator@newserver:/tmp/.
```

_Commands to run on new server_

Backup current files (and their backups).
```
mkdir /root/save
cp /etc/passwd /etc/passwd- /etc/shadow /etc/shadow- /etc/group /etc/group- /etc/gshadow /etc/gshadow- /root/save
```

If you have Samba users, backup your current files.
```
cp /etc/samba/smb.conf /etc/samba/smbusers /etc/samba/smbpasswd /root/save
```

Merge/Overwrite files.
```
cat /tmp/passwd.mig >> /etc/passwd
cat /tmp/group.mig >> /etc/group
cat /tmp/shadow.mig >> /etc/shadow
cp /tmp/gshadow.mig /etc/gshadow
```

Ensure file ownership and permissions are correct.
```

chown root:shadow /etc/shadow /etc/gshadow
chmod 640 /etc/shadow /etc/gshadow
chown root:root /etc/passwd /etc/group
chmod 644 /etc/passwd /etc/group

```

If you have Samba users...
```
cp /tmp/smb.mig /etc/samba/smb.conf
cp /tmp/smbusers.mig /etc/samba/smbusers
cp /tmp/smbpasswd.mig /etc/samba/smbpasswd
```

Extract home directories.
```
cd /
tar -zxvf /tmp/home.tar.gz
```

Reboot system for new user accounts to take effect.
```
reboot
```

[SIZE=5]Replacing a server with a new one[/SIZE]

If you want to keep SSH keys and the fingerprint from changing when swapping out an old server for a new one (e.g. old FTPS server to new FTPS), these are the steps needed to keep the system looking the same. (I think...but will know when I upgrade my FTPS server)

The old server name and the new server name must batch.  Example: srv-ftps

Make sure the sshd configuration files on both servers are pointing to the same files (filenames and paths)

```
vi /etc/ssh/sshd_config
```

Look for section like this:
```

# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key

```
If there are differences, figure out if they matter and if so, make sure the transferred files on the new server are being referenced correctly in the config file on the new server.

_Commands to run on old server_

Transfer files to new server
```
scp /etc/ssh/ssh_host* administrator@newserver:/tmp/.
```

_Commands to run on new server_

Backup existing files
```

mkdir /root/ssh-backup
cp /etc/ssh/ssh_host* /root/ssh-backup/.
```

Set correct file ownership and permissions
```
chown root:root /tmp/ssh_host*
chmod 600 /tmp/ssh_host*
chmod 644 /tmp/ssh_host*.pub

```

Move and overwrite files to correct location
```
mv /tmp/ssh_host* /etc/ssh/.
```

Restart SSH daemon
```
service ssh restart
```

You will also want to copy over individual user's public keys in their ~/.ssh/authorized_keys but if you transferred the contents of the /home folder, this was already done.

---

### Post by LHammonds on 2017-10-03
[SIZE=5]Fail2Ban[/SIZE]

Fail2Ban is an intrusion prevention system that can be used to protect servers from different kinds of attacks.

Fail2ban scans log files for various services, such as SSH, FTP, SMTP, Apache and block the IP address that makes too many password failures.

[SIZE=5]Install Fail2Ban[/SIZE]
```
apt-get install fail2ban
```

[SIZE=5]Configure Fail2Ban[/SIZE]
The default configuration file should not be altered since upgrades tend to overwrite this file with new settings.

Instead, use a custom configuration file that will simply override or append various settings to the default.

Fail2Ban reads .conf files first and then .local files last which can override any settings initially set in .conf files.

First, look at the default file:
```
vi /etc/fail2ban/jail.conf
```

Notice the following partial list of default values. These are based on the OS and version at the time of this writing:
```

[DEFAULT]
ignoreip = 127.0.0.1/8
bantime  = 600
findtime  = 600
maxretry = 5
filter = %(__name__)s
destemail = root@localhost
sender = root@localhost
mta = sendmail
action = %(action_)s
[sshd]
port    = ssh
logpath = %(sshd_log)s

```

Now create a local jail file that will be used to override any settings in the default that we want changed or added.

For this example, we will ignore all failed login attempts from our local server subnet (192.168.107.xxx) and a specific admin workstation (192.168.1.69)

```
vi /etc/fail2ban/jail.local
```

Let's make some changes that fit our server as it stands right now:

```

[DEFAULT]
## 127.0.0.1/8 = ignore login failures on the local machine
## 192.168.107.0/24 = ignore login failures on an entire subnet
## 192.168.1.69 = ignore login failures for this specific IP
ignoreip = 127.0.0.1/8 192.168.107.0/24 192.168.1.69

## "bantime" is the number of seconds that a host is banned. 600=10 minutes, 1800=30 minutes.
bantime = 1800
## "findtime" is the length of time between login attempts before a ban is set.
findtime = 600
## "maxretry" is how many attempts can be made to access the server from a single IP before a ban is imposed.
maxretry = 7

## "destemail" is the email address where you would like to receive the emails.
destemail = webmaster@mydomain.com
## "sender" is the FROM: address when it arrives in your mailbox.
sender = myserver@mydomain.com
## Use the lightweight sendemail instead of sendmail
mta = sendemail
## Email notify with whois report and relevant log lines when a ban occurs
action = %(action_mwl)s

```

We are using sendemail for our scripts so we will also use it for fail2ban.  We will need to make a configuration file that tells fail2ban how to make use of it though.

```
vi /etc/fail2ban/action.d/sendemail-whois-lines.conf
```

```

[Definition]
actionstart =  /usr/bin/sendemail -f <sender> -t <dest> -s <smtp> -xu <sender> -xp <password> -u "[Fail2Ban] <servername> <name>: started" -m "The jail <name> has been started successfully.\n\nFail2Ban"
actionstop =  /usr/bin/sendemail -f <sender> -t <dest> -s <smtp> -xu <sender> -xp <password> -u "[Fail2Ban] <servername> <name>: stopped" -m "The jail <name> has been stopped.\n\nFail2Ban"
actioncheck =
actionban =  /usr/bin/sendemail -f <sender> -t <dest> -s <smtp> -xu <sender> -xp <password> -u "[Fail2Ban] <servername> <name>: banned <ip>" -m "The IP <ip> has just been banned by Fail2Ban after <failures> attempts against <name>.\n\nHere is more information about <ip>:\n `/usr/bin/whois <ip>`\n\n Lines containing IP:<ip> in <logpath>\n`/bin/grep '\<<ip>\>' <logpath>`\n\n\n\nFail2Ban"
actionunban =

[Init]
## Amended to be the same as the SMTP user
sender = fail2ban@mydomain.com
## SMTP password for user
#password = XXXXXXX
## SMTP server - use port 587 for Google rather than 25 (times out too often) or 465 (crashes sendemail)
#smtp = smtp.googlemail.com:587
smtp = srv-mail

## Name for this server - handy when there are lots of servers sending emails to the destemail
servername = srv-ubuntu

```

[SIZE=5]Useful commands[/SIZE]

Here are a few of the most-used commands.  Reference: [Fail2Ban commands]("https://www.fail2ban.org/wiki/index.php/Commands").
Stop, start or restart the fail2ban service:
```
service fail2ban stop
service fail2ban start
service fail2ban restart
```

This command will show which services are being watched (sshd in this example):
```
fail2ban-client status
```
Example output:
```

Status
|- Number of jail:      1
`- Jail list:   sshd

```

This command gets the status on the sshd service being watched:
```
fail2ban-client status sshd
```
Example output:
```

Status for the jail: sshd
|- Filter
|  |- Currently failed: 0
|  |- Total failed:     0
|  `- File list:        /var/log/auth.log
`- Actions
   |- Currently banned: 0
   |- Total banned:     0
   `- Banned IP list:

```

[SIZE=5]Firewall Rules[/SIZE]

Installing Fail2Ban will create the following firewall rules which can be seen with the following command:

```
iptables -S
```

```

-N f2b-sshd
-A INPUT -p tcp -m multiport --dports 22 -j f2b-sshd
-A f2b-sshd -j RETURN

```

If you have already enabled Uncomplicated Firewall (UFW), you will see several ufw-prefixed rules as well.

[SIZE=5]Test Fail2Ban[/SIZE]

To manually ban an IP:
```
fail2ban-client set sshd banip 192.168.1.69
```

To manually unban an IP:
```
fail2ban-client set sshd unbanip 192.168.1.69
```

On the server, run the following command to watch the Fail2Ban log file:
```
tail -f /var/log/fail2ban.log
```

On a different machine (that is not on your ignoreip list), try to ssh into your server with the incorrect ID or password multiple times until you have reached the "maxretry" attempts and you get locked out...thus causing an entry in the log.

[SIZE=5]References[/SIZE]

[Fail2Ban Manual]("http://www.fail2ban.org/wiki/index.php/MANUAL_0_8")

---

### Post by mörgæs on 2017-10-03
Whoa, impressive thread. Thanks for posting.

Feel free to ask for this post to be deleted when you have read it. Just wanted to thank you in public.

---

