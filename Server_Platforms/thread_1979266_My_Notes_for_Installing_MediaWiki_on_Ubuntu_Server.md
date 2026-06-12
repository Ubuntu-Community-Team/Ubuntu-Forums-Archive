---
title: "My Notes for Installing MediaWiki on Ubuntu Server 12.04 LTS"
date: 2012-05-13
forum: Server Platforms
---

### Post by LHammonds on 2012-05-13
Greetings and salutations,

I hope this thread will be helpful to those who follow in my foot steps as well as getting any advice based on what I have done / documented.

This is a Work-In-Progress topic so I will be updating this thread as I learn more about Ubuntu and MediaWiki.

[SIZE="5"]High-level overview[/SIZE]

This thread will cover installation of a dedicated Ubuntu server, Apache Web service and MediaWiki web site.  The server will be installed inside a virtual machine vSphere 4.1 running on ESXi 4.1 servers.  Although there are some VMware-specific steps, they are very few and the majority of this documentation will work for other VMs such as VirtualBox or even directly installed onto a physical machine.  Please excuse any ignorance on my part since I am fairly new to Linux and MediaWiki...if you have any advice on doing things better, please let me know.  I love feedback and learning better ways of doing things!

After Ubuntu is installed and configured, Apache web server will be installed and configured.  Next will be the installation and configuration of MediaWiki which will utilize an existing remote MySQL server.  Some extensions will then be installed and tested.

The last step will cover some custom scripts to help automate tasks such as backing up, automatically growing the file system when free space is low, etc.

[SIZE="5"]Tools utilized in this process[/SIZE]


[LIST]
[*][Ubuntu Server]("http://www.ubuntu.com/download/ubuntu/download") 12.04 LTS, 64-bit
[*]Apache 2.2.22
[*]PHP 5.3.10
[*]MySQL 5.1.62
[*]MediaWiki 1.19
[*]Microsoft Active Directory 2003
[*][Portable PuTTY]("http://portableapps.com/apps/internet/putty_portable") 0.62
[*][VMware vSphere]("http://www.vmware.com/products/vsphere/overview.html") 4.1.0
[/LIST]


[SIZE="5"]Helpful links[/SIZE]

The list below are sources of information that helped me configure this system as well as some places that might be helpful to me later on as this process continues.

[LIST]
[*][Ubuntu Documentation]("https://help.ubuntu.com")
[*][Ubuntu MediaWiki package]("https://help.ubuntu.com/community/MediaWiki")
[*][Ubuntu Firewall Basics]("https://help.ubuntu.com/community/IptablesHowTo#Disabling%20the%20firewall")
[*][Ubuntu AppArmor Basics]("https://help.ubuntu.com/community/AppArmor#Disable%20AppArmor%20framework")
[*][MediaWiki downloads]("http://www.mediawiki.org/wiki/Download")
[*][MediaWiki Extension Distributor]("http://www.mediawiki.org/wiki/Special:ExtensionDistributor")
[/LIST]


[SIZE="5"]Assumptions[/SIZE]

This documentation will need to make use of some very-specific information that will most-likely be different for each person / location.  And as such, I will note some of these in this section.  They will be highlighted in red throughout the document as a reminder that you should plug-in your own value rather than actually using my "place-holder" value.

Under no circumstance should you use the actual values I list below.  They are place-holders for the real thing.  This is just a checklist template you need to have answered before you start the install process.

Wherever you see [COLOR="red"]RED[/COLOR] in this document, you need to substitute it for what your company uses.  Use the list below as a template you need to have answered before you continue.



[LIST]
[*]Ubuntu Server name: [COLOR="red"]srv-wiki[/COLOR]
[*]Internet domain: [COLOR="red"]mydomain.com[/COLOR]
[*]Ubuntu Server IP address: [COLOR="red"]192.168.107.30[/COLOR]
[*]Ubuntu Server IP subnet mask: [COLOR="red"]255.255.255.0[/COLOR]
[*]Ubuntu Server IP gateway: [COLOR="red"]192.168.107.1[/COLOR]
[*]Internal DNS Server 1: [COLOR="red"]192.168.107.212[/COLOR]
[*]Internal DNS Server 2: [COLOR="red"]192.168.107.213[/COLOR]
[*]External DNS Server 1: [COLOR="red"]8.8.8.4[/COLOR]
[*]External DNS Server 2: [COLOR="red"]8.8.8.5[/COLOR]
[*]Ubuntu Admin ID: [COLOR="red"]administrator[/COLOR]
[*]Ubuntu Admin Password: [COLOR="red"]myadminpass[/COLOR]
[*]Email Server (remote): [COLOR="red"]192.168.107.25[/COLOR]
[*]MySQL Server (remote): [COLOR="red"]192.168.107.20[/COLOR]
[*]MySQL root Password: [COLOR="red"]mysqlrootpass[/COLOR]
[*]MySQL wiki user: [COLOR="red"]mediawikiuser[/COLOR]
[*]MySQL wiki Password: [COLOR="red"]mysqlwikipass[/COLOR]
[*]Windows Share ID: [COLOR="red"]mediawikishare[/COLOR]
[*]Windows Share Password: [COLOR="red"]mywikisharepass[/COLOR]
[/LIST]

I also assume the reader knows how to use the VI editor.  If not, you will need to [beef up your skill set]("http://www.eng.hawaii.edu/Tutor/vi.html") or use a different editor in place of it.

---

### Post by LHammonds on 2012-05-13
[SIZE="5"]Analysis and Design[/SIZE]

The Ubuntu Server Long-Term Support (LTS) is free but we have the option of buy support and that is the main reason this server was selected.

The largest decision over the configuration of Ubuntu seems to be how the hard drive space is sliced up (partitioned).  I lot of my time was spent researching and learning the various options when it comes to the design layout of the storage.

I like to make use of a design that allows for dynamic growth and fine-tuning if need be.  I also do not like being caught offguard with a scenario where space is filled up with no immediate option other than deleting files.  Long-term life and growth of the system as well as budgeting concerns have to be taken into consideration.

I like to contain the root volume to mainly just static data that won't grow much and push the other folders that are dynamic into their own volumes.  In case you don't know, filling up the root volume on a *nix system is a very bad thing and should be avoided at all costs.  I also want to configure it where the file systems are not taking up 100% of the logical volume.  This will allow me (through automated scripts) to grow the file system as needed and give me some time to add more drives if necessary or shrink other volumes to get more space.

Here are my thoughts on how to slice up the space.


[LIST]
[*]**Boot** - This will remain static in size.  It is also the only space residing outside the Logical Volume Manager (LVM)
[*]**Root volume** - Operating system and everything else which should remain fairly static.
[*]**Swap volume** - This will remain static in size.  However, if amount of RAM is adjusted, this should be adjusted as well.
[*]**var volume** - This is the application storage and will continue to grow over time.
[*]**Backup volume** - This will contain a local backup of the Opt volume.  So space needs to be around double /opt/mediawiki.
[*]**Temp volume** - This location will be used to hold data during backups, archives and restores and should be about double the size of opt/mediawiki.
[*]**Offsite Storage** - This will be handled elsewhere but will be mounted on this server.
[/LIST]

My estimated wiki store will be about 6 GB.  However, we will start this server off with a much lower number.  We will then pretend some event happened such as many people starting to document all their processes (with images).  This will increase our storage needs and we will go through adjusting the entire system to accommodate a larger storage capacity.  This will be a good exercise / documentation for what will eventually need to be done later to handle growth.

To get a good idea of the hard drive layout and to understand the process better, here is a graphical representation of the initial design for the server:

[IMG]http://tinyurl.com/7vtjgp7[/IMG]

These numbers will be used for the initial build of the system:

boot = 200 MB
root = 4 GB
swap = 4 GB
var = 2 GB
temp = 4 GB
backup = 4 GB

NOTE: When the logical volumes and file systems are initially created, they consume the maximum amount of space allocated so that the logical volume size = file system size.  This will be later modified so that the logical volume will be larger than the file system so that the file system has room to expand when needed.

Important info:
 - The /tmp folder is strictly temporary.  Each time the server reboots, this folder is deleted and re-created.
 - The /temp folder is for semi-permanent temporary files.  Files placed here will not go away after a reboot.
 - The /backup folder will retain the most recent backup and is considered the "local" copy of the backup.

[SIZE="5"]Virtual Machine Settings[/SIZE]

Virtual Manager: VMware vSphere Client 4.1
Virtual Host: VMware ESXi Server 4.1


[LIST]
[*]Configuration: Custom
[*]Name: SRV-Wiki
[*]Datastore: MainOffice-LUN0
[*]Virtual Machine Version: 7
[*]Guest Operating System: Linux, Version: Ubuntu Linux (64-bit)
[*]Number of virtual processors: 1
[*]Memory Size: 2048 MB
[*]Number of NICs: 1
[*]NIC 1: VM Network
[*]Adapter: E1000, Connect at Power On: Checked
[*]SCSI controller: LSI Logic Parallel
[*]Select a Disk: Create a new virtual disk
[*]Create a Disk: 20 GB, No thin provisioning, No cluster features, Store with the virtual machine
[*]Advanced Options: Virtual Device Node = SCSI (0:0)
[*]Remove Floppy Drive
[*]Mount CD/DVD Drive to Ubuntu ISO (ubuntu-12.04-server-amd64.iso). Make sure CD/DVD is set to **Connect at power on**
[*]Set boot options to Force BIOS Setup so you can set CDROM to boot before the Hard Disk
[/LIST]

[SIZE="5"]Install PuTTY[/SIZE]

The 1st time I installed Ubuntu, I used the console for everything but it was painfully slow to view man (manual) pages and navigating in VI (text editor).  However, I found out that PuTTY is a far better solution for your Ubuntu console because it handles the screen draws much faster and allows for scrolling and copying text.

Download the portable edition and run the install...except it doesn't really "install" like a normal program, it simply extracts to a specified folder and will run from that folder even if you put it on a USB stick and carry over to a new computer (requires no install to run and thus leaves a very small footprint on your system)


[LIST=1]
[*]Start PuTTY
[*]Type the following and click the Save button:
Host Name: [COLOR="Red"]srv-wiki[/COLOR] (or the IP such as [COLOR="red"]192.168.107.23[/COLOR])
Port: **22**
Connection type: **SSH**
Saved Sessions: **SRV-Wiki**
[*]Now all you have to do is double-click on the mediawiki session and it will connect to your server (when online).
[/LIST]

---

### Post by LHammonds on 2012-05-13
[SIZE=5]Install Ubuntu Server[/SIZE]

NOTE: During the setup process throughout this entire document, most commands will require "sudo" as a prefix. However, I will be using "sudo su" to temporarily gain root privileges.

[LIST=1]
[*]Power on the Virtual Machine (VM)
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *English*
[*]Select *Install Ubuntu Server* [COLOR=green]{ENTER}[/COLOR]
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *English*
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *United States*
[*]Select **No** to not detect keyboard layout
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *English (US)*
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *English (US)*
[*]Type **[COLOR=red]srv-wiki[/COLOR]** [COLOR=green]{ENTER}[/COLOR] (this is your hostname)
[*]Type **[COLOR=red]Administrator[/COLOR]**, [COLOR=green]{ENTER}[/COLOR] for the full name
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept the default of the lowercase name of **[COLOR=red]administrator[/COLOR]**
[*]Type **[COLOR=red]myadminpass[/COLOR]**, [COLOR=green]{ENTER}[/COLOR], **[COLOR=red]myadminpass[/COLOR]**, [COLOR=green]{ENTER}[/COLOR]
[*]Select *No*, [COLOR=green]{ENTER}[/COLOR] to not encrypt your home directory
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept detected time zone (*America/Chicago*)
[*]Select *Manual* [COLOR=green]{ENTER}[/COLOR]
[*]Select *SCSI3 (0,0,0) (sda) - 21.5 GB VMware Virtual disk* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Yes* to create new empty partition table, [COLOR=green]{ENTER}[/COLOR]
[*]Select *pri/log 21.5 GB FREE SPACE* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Create a new partition* [COLOR=green]{ENTER}[/COLOR]
[*]Type **200 MB**, [COLOR=green]{ENTER}[/COLOR] (NOTE: This will be the /boot partition)
[*]Select *Primary* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Beginning* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Use as: Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Ext2 file system* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Mount point: /* [COLOR=green]{ENTER}[/COLOR]
[*]Select */boot - static files of the boot loader* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Bootable flag: off* [COLOR=green]{ENTER}[/COLOR] (NOTE: This toggles it on)
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Configure the Logical Volume Manager* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Yes* to write change to disks and configure LVM, [COLOR=green]{ENTER}[/COLOR]
[*]Select *Create volume group* [COLOR=green]{ENTER}[/COLOR]
[*]Type **LVG** [COLOR=green]{ENTER}[/COLOR]
[*]Select */dev/sda free #1 (21274MB; FREE SPACE)*, [COLOR=green]{SPACEBAR}[/COLOR], [COLOR=green]{ENTER}[/COLOR]
[*]Select *Yes* to write change to disks and configure LVM, [COLOR=green]{ENTER}[/COLOR]
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR]
[*]Select *LVG (21269MB)* [COLOR=green]{ENTER}[/COLOR]
[*]Type **swap** [COLOR=green]{ENTER}[/COLOR]
[*]Type **4G** [COLOR=green]{ENTER}[/COLOR] (NOTE: This is double the amount of RAM)
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR]
[*]Select *LVG (17272MB)* [COLOR=green]{ENTER}[/COLOR]
[*]Type **bak** [COLOR=green]{ENTER}[/COLOR]
[*]Type **4G** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR]
[*]Select *LVG (13274MB)* [COLOR=green]{ENTER}[/COLOR]
[*]Type **var** [COLOR=green]{ENTER}[/COLOR]
[*]Type **2G** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR]
[*]Select *LVG (11278MB)* [COLOR=green]{ENTER}[/COLOR]
[*]Type **temp** [COLOR=green]{ENTER}[/COLOR]
[*]Type **4G** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR]
[*]Select *LVG (7281MB)* [COLOR=green]{ENTER}[/COLOR]
[*]Type **root** [COLOR=green]{ENTER}[/COLOR]
[*]Type **4G** [COLOR=green]{ENTER}[/COLOR] (we will have a small amount leftover in LVG)
[*]Select *Finish* [COLOR=green]{ENTER}[/COLOR]
[*]Select *#1 4.0 GB* directly under *LVM VG LVG, LV swap*, [COLOR=green]{ENTER}[/COLOR]
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR]
[*]Select *swap area* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR]
[*]Select *#1 4.1 GB* directly under *LVM VG LVG, LV root*, [COLOR=green]{ENTER}[/COLOR]
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR]
[*]Select */ - the root file system* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR]
[*]Select *#1 4.0 GB* directly under *LVM VG LVG, LV bak*, [COLOR=green]{ENTER}[/COLOR]
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Enter manually* [COLOR=green]{ENTER}[/COLOR]
[*]Type **/backup** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Label: none* [COLOR=green]{ENTER}[/COLOR]
[*]Type **backup** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR]
[*]Select *#1 4.0 GB* directly under *LVM VG LVG, LV var*, [COLOR=green]{ENTER}[/COLOR]
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR]
[*]Select */var* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Label: none* [COLOR=green]{ENTER}[/COLOR]
[*]Type **mediawiki** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR]
[*]Select *#1 4.0 GB* directly under *LVM VG LVG, LV temp*, [COLOR=green]{ENTER}[/COLOR]
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Enter manually* [COLOR=green]{ENTER}[/COLOR]
[*]Type **/temp** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Label: **temp*** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR]
[*]Here is what the screen looks like at this point: [Partitions]("http://tinyurl.com/83lhku3")
[*]Select *Finish partitioning and write changes to disk* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Yes* to write changes to disk, [COLOR=green]{ENTER}[/COLOR]
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept a blank line for the HTTP proxy
[*]Select *Install security updates automatically*, [COLOR=green]{ENTER}[/COLOR]
[*]Highlight only *OpenSSH server* and press [COLOR=green]{SPACEBAR}[/COLOR] to enable, [COLOR=green]{ENTER}[/COLOR] to continue.  NOTE: This allows us to use PuTTY after installation to connect to the server.
[*]Select *Yes*, [COLOR=green]{ENTER}[/COLOR] to install GRUB boot loader to the master boot record
[*]Installation Complete - from the VM menu, select VM --> Edit Settings and select *CD/DVD Drive 1* and change to "Client Device" which will effectively remove the ISO.  Now press [COLOR=green]{ENTER}[/COLOR] to reboot.
[/LIST]


[SIZE=5]Initial Configurations[/SIZE]


[LIST=1]
[*]At the console login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Type **vi /etc/network/interfaces** [COLOR=green]{ENTER}[/COLOR] and change the following: (We need to change the network interface card (NIC) from using DHCP to a static IP)

From:
```
iface eth0 inet dhcp
```To:
```
iface eth0 inet [B]static
address [COLOR=red]192.168.107.23[/COLOR]
netmask [COLOR=red]255.255.255.0[/COLOR]
gateway [COLOR=red]192.168.107.1[/COLOR]
network [COLOR=red]192.168.107[/COLOR].0
broadcast [COLOR=red]192.168.107[/COLOR].255
dns-nameservers [COLOR=red]192.168.107.212 192.168.107.213 8.8.8.4 8.8.8.5[/COLOR][/B]
```NOTE #1: You may need to manually remove the DHCP record (lease) associated to this Ubuntu server from your DHCP server so the correct IP can be found by other machines on the network.  This can be avoided by temporarily configuring the VM Network Adapter connection to be "Host Only Network" instead of "VM Network" so the server is isolated during setup...at least until you reach the testing of the static IP below.

NOTE #2: You might also need to manually add a HOST(A) record to your Windows DNS server (for [COLOR=red]srv-wiki.mydomain.com[/COLOR] and [COLOR=red]srv-wiki.work.mydomain.com[/COLOR])
[*]Restart the network by typing **/etc/init.d/networking restart**
[*]Sanity check!  Type **ifconfig** and make sure the settings are correct.  Then type **ping [www.google.com]("http://www.google.com")** or similar and see if ping works.
[*]Shutdown and power off the server by typing **shutdown -P now** [COLOR=green]{ENTER}[/COLOR]
[*]At this point forward, you can use PuTTY to access the console rather than the console itself for better performance, ability to scroll, etc.
[*]In VM menu, select VM --> Snapshot --> Take Snapshot.  Give it a name like **STEP 1** and description of **Ubuntu Server 12.04 LTS, clean install, Static IP: [COLOR=red]192.168.107.23[/COLOR]** and click **OK**
[/LIST]


[SIZE=5]Software Configurations[/SIZE]


[LIST=1]
[*]Start the Ubuntu server and connect using PuTTY.
[*]At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]At the $ prompt, type **aptitude -y install vim-nox** for use instead of the built-in VI editor. [more info]("http://en.wikipedia.org/wiki/Vim_%28text_editor%29")
[*]At the $ prompt, type **aptitude -y install p7zip-full** to install 7-zip archive utility.
[*]At the $ prompt, type **aptitude -y install sendemail** to install an email utility.
[*]Change the default shell from dash to bash.  Type **ls -l /bin/sh** to see that it points to /bin/dash.  Type **dpkg-reconfigure dash** and answer **No**.  Type **ls -l /bin/sh** and it should now be pointing to /bin/bash
[*]Remove AppArmor to avoid problems by typing the following:
```
[B]/etc/init.d/apparmor stop
/etc/init.d/apparmor teardown
update-rc.d -f apparmor remove
aptitude remove apparmor apparmor-utils[/B]
```
[*]Reboot the server by typing **reboot**
[/LIST]


[SIZE=5]VMware Tools[/SIZE]

If you are installing under VMware like me, be sure to install the tools to insure maximum performance in a virtual environment.


[LIST=1]
[*]In the VM toolbar for the VM, click Guest, Install VMware Tools
[*]At the Ubuntu prompt, type the following:
```
[B]
mkdir /mnt/cdrom
mount /dev/cdrom /mnt/cdrom
ls /mnt/cdrom       ( make sure you see a file such as VMwareTools-8.3.2-257589.tar.gz)
tar zxvf /mnt/cdrom/VMwareTools* -C /tmp/
cd /tmp/vmware-tools-distrib/
./vmware-install.pl -d
reboot
[/B]
```
[/LIST]

---

### Post by LHammonds on 2012-05-13
[SIZE=5]Volume / Disk Management[/SIZE]

At this point, let's assume something has changed and we need additional storage (e.g. insanely popular with more people adding content).  The initial setup left us with no room to expand our file system!  We need to change this.

For this scenario, we are expecting storage space to require 3 GB.  If they need 3 GB for storage, let's double that amount for the actual size.  Here is the planned adjustments for each file system:

var = 6 GB (double the expected storage)
temp = 12 GB (double the www size)
backup = 12 GB (double the www size)

In the analysis and design section, we wanted to have some file systems smaller than the logical volume on which they sit.  This will allow us to allocate additional space when needed.  However, when we created the volumes, Ubuntu automatically expanded the file systems to the maximum size of the volume.  Normally, this is OK...but we want a system that will allow growth when needed and ensure that we will have time to add additional hard drives BEFORE they are needed which will keep us from being stuck between a rock and a hard place!  You do not want to lose a job because somebody did not estimate growth correctly or the budget did not allow for large capacity when the system first rolled out.

This design calls for the backup, var and temp file systems to be slightly smaller than the maximum space available for the logical volume in which they reside in.

So, let's make the logical volumes an extra 1 GB larger.  This means that we will need an additional 23 GB of storage {(7 + 13 + 13 ) - (2 + 4 + 4}.  If we add two drives that are 12 GB each, that will be just enough to cover our needs. (NOTE: This was an arbitrary number because I wanted to show you how to add 2 drives to the system)

Here is a graphical representation of what needs to be accomplished:

[IMG]http://tinyurl.com/7rfzz5c[/IMG]

If we were to type **df -h** right now, we should see something like this:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  3.9G  976M  2.7G  27% /
udev                  993M  4.0K  993M   1% /dev
tmpfs                 401M  232K  401M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                 1002M     0 1002M   0% /run/shm
/dev/sda1             179M   25M  145M  15% /boot
/dev/mapper/LVG-bak   3.8G  121M  3.5G   4% /backup
/dev/mapper/LVG-temp  3.8G  121M  3.5G   4% /temp
/dev/mapper/LVG-var   1.9G  298M  1.5G  17% /var

```Since I am running VMware, adding additional space is a snap.  However, I will add it in such a way that Ubuntu will see 2 drives added to the system just as if we were to add 2 physical drives to a physical server.

[LIST=1]
[*]Shutdown and power off the server by typing **shutdown -P now** [COLOR=green]{ENTER}[/COLOR]
[*]In the vSphere client, right-click the Virtual Machine and choose *Edit Settings*.
[*]On the hardware tab, click the *Add* button and select Hard Disk.  Click Next, choose "Create a new virtual disk", click Next, set the size to **12** GB, click Next, Next, Finish.
[*]Add another **12** GB disk using the same steps above and click OK to close the settings and allow VMware to process the changes.
[/LIST]

Collect information about the newly added drives.

[LIST=1]
[*]Start the Ubuntu server and connect using PuTTY.
[*]At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR]) and then type **su** and the root password ([COLOR=red]myrootpass[/COLOR])
[*]Type **pvdisplay** which should show something similar to this:
```

  --- Physical volume ---
  [COLOR=red]PV Name               /dev/sda5
  VG Name               LVG[/COLOR]
  PV Size               19.81 GiB / not usable 3.00 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              5071
  Free PE               760
  Allocated PE          4311
  PV UUID               CJOZ2d-rhek-Dy95-UVuN-hAoR-Ao9q-nrScUv

```The important bits of info here are the PV Name and VG Name for our existing configuration.
[*]Type **fdisk -l** which should show something similar to this (however I abbreviated it to show just the important parts):
```

Disk /dev/sda: 21.5 GB, 21474836480 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      391167      194560   83  Linux
/dev/sda2          393214    41940991    20773889    5  Extended
/dev/sda5          393216    41940991    20773888   8e  Linux LVM
Disk [COLOR=red]/dev/sdb[/COLOR]: 12.9 GB, 12884901888 bytes
Disk /dev/sdb doesn't contain a valid partition table
Disk [COLOR=red]/dev/sdc[/COLOR]: 12.9 GB, 12884901888 bytes
Disk /dev/sdc doesn't contain a valid partition table

```The important bits of info here are the device paths for the new drives which are highlighted in red.
[/LIST]

Prepare the first drive (/dev/sdb) to be used by the LVM

Type the following:
```
**fdisk /dev/sdb**
**n** (Create New Partition)
**p** (Primary Partition)
**1** (Partition Number)
[COLOR=green]{ENTER}[/COLOR] (use default for first cylinder)
[COLOR=green]{ENTER}[/COLOR] (use default for last cylinder)
**t** (Change partition type)
**8e** (Set to Linux LVM)
**p** (Preview how the drive will look)
**w** (Write changes)
```Prepare the second drive (/dev/sdc) to be used by the LVM

Do the exact same steps as above but start with **fdisk /dev/sdc**

Create physical volumes using the new drives

If we type **fdisk -l**, we now see /dev/sdb1 and /dev/sdc1 which are Linux LVM partitions.

Type the following to create physical volumes:
```
[B]pvcreate /dev/sdb1
pvcreate /dev/sdc1[/B]
```Now add the physical volumes to the volume group (LVG) by typing the following:
```
[B]vgextend LVG /dev/sdb1
vgextend LVG /dev/sdc1[/B]
```Now that the space of both drives have been added to the logical volume group called LVG, we can now allocate that space to grow the logical volume.

To get a list of volume paths to use in the next commands, type **lvscan** to show your current volumes and their sizes.

Type the following to grow each volume by a specified amount (the number after the plus sign):
```
[B]lvextend -L+5G /dev/LVG/var
lvextend -L+9G /dev/LVG/bak
lvextend -L+9G /dev/LVG/temp[/B]
```or you can specify the exact size by excluding the plus sign and specifying the end-result size you want:
```
[B]lvextend -L7G /dev/LVG/var
lvextend -L13G /dev/LVG/bak
lvextend -L13G /dev/LVG/temp[/B]
```To see the new sizes, type **lvscan**

The last thing to do now is the actual growth of the file systems.  We want to grow the existing file systems but only to a certain amount so we do not take up all the space in the volume...we want room to grow in the future so we have time to order and install new drives when needed.
```
[B]resize2fs /dev/LVG/var 6G
resize2fs /dev/LVG/bak 12G
resize2fs /dev/LVG/temp 12G[/B]
```If we need to increase space in /var at a later point, we can issue the following command (without any downtime):

```
**resize2fs /dev/LVG/var 6100MB**
```We could continue to increase this particular file system all the way until we reach the limit of the volume which is 13 GB at the moment.

Remember, **df -h** will tell you the size of the file system and **lvscan** will tell you the size of the volumes where the file systems live in.

If we were to type **df -h** right now, we should see something like this:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  3.8G  904M  2.7G  26% /
udev                  993M  4.0K  993M   1% /dev
tmpfs                 401M  248K  401M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                 1002M     0 1002M   0% /run/shm
/dev/sda1             179M   25M  145M  15% /boot
/dev/mapper/LVG-bak    12G  125M   12G   2% /var/backup
/dev/mapper/LVG-temp   12G  125M   12G   2% /var/temp
/dev/mapper/LVG-var   6.0G  301M  5.4G   6% /var

```TIP: If you want to see everything in a specific block size, such as everything showing up in megabytes, you can use **df --block-size m**

---

### Post by LHammonds on 2012-05-13
[SIZE="5"]Configure Ubuntu for Windows File Sharing[/SIZE]

This file sharing section is optional but can be handy if you need to swap files between the Linux server and a Windows machine.

This documentation will utilize this share for passing pre-configured files (configs, scripts, etc.) to make it faster/easier during installation.


[LIST=1]
[*]Start the Ubuntu server and connect using PuTTY.
[*]At the login prompt, login with your administrator account ([COLOR="red"]administrator[/COLOR] / [COLOR="red"]myadminpass[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Install Samba by typing **aptitude -y install samba smbfs** (NOTE: To share a folder with Windows, you just need the **samba** package, to connect to a Windows share, you need both **samba** and **smbfs**)
[*]Type the following commands:
```
[B]cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
mkdir -p /srv/samba/share
chown nobody:nogroup /srv/samba/share/
chmod 0777 /srv/samba/share[/B]
```
[*]Edit the configuration file by typing **vi /etc/samba/smb.conf**
[*]Change **workgroup = WORKGROUP** to **workgroup = [COLOR="red"]work[/COLOR]** (you are using the domain alias)
[*]Change:
```
#   security = user
```
to:
```
   security = user
```
[*]Add the following section to the end of the file:
```
[B][share]
comment = Ubuntu File Server Share
path = /srv/samba/share
browsable = yes
guest ok = yes
read only = no
create mask = 0755[/B]
```
[*]Save and exit the file.
[*]Restart the samba services to utilize the new configuration by typing:
```
[B]restart smbd
restart nmbd[/B]
```
[*]You should now be able to click Start --> Run and type **\\[COLOR="red"]srv-wiki[/COLOR]** or **\\[COLOR="red"]192.168.107.23[/COLOR]** [COLOR="green"]{ENTER}[/COLOR] and see an explorer window with a *Share* folder.  Drag-n-drop a file into the *Share* folder.  If it worked, it will not display an error message and you should be able to view it from the server by typing **ls -l /srv/samba/share/**
[*]Shutdown and power off the server by typing **shutdown -P now** [COLOR="green"]{ENTER}[/COLOR]
[*]In VM menu, select VM --> Snapshot --> Take Snapshot.  Give it a name like **STEP 2** and description of **Ubuntu Server 12.04 LTS, File share configured, Static IP: [COLOR="red"]192.168.107.23[/COLOR]**.  The Snapshot Manager should now have a nice hierarchy of snapshots (STEP 1 --> STEP 2 --> You are here)
[/LIST]

[SIZE="5"]Configure Windows Remote Mount Point[/SIZE]

The remote offsite location is a Windows 2008 server that has a vast amount of hard drive space and currently backs up other servers.

Part of the backup process will be to write files to a mounted folder to a Windows share.

First, let's document the variables for this solution below and highlight them in red throughout the document for easy identification.

The values below are merely samples which you need to change in order to match your environment:

Windows AD Domain Name: [COLOR="red"]work[/COLOR]
Windows Server Name: [COLOR="red"]SRV-Backup[/COLOR]
Windows Server IP: [COLOR="red"]192.168.107.218[/COLOR]
Windows Share Name: mediawikishare
Windows Physical Share Location: [COLOR="red"]D:\MediaWiki\[/COLOR]
Windows Share ID: [COLOR="red"]mediawikishare[/COLOR]
Windows Share Password: [COLOR="red"]mywikisharepass[/COLOR]

[SIZE=4]Create a share on a Windows 2008 server[/SIZE]


[LIST=1]
[*]In Windows Explorer, right-click on the [COLOR="red"]*D:\MediaWiki*[/COLOR] folder and select **Properties**
[*]Click the **Sharing** tab
[*]Click the **Advanced Sharing** button
[*]Place a checkmark beside **Share this folder**
[*]Change the Share name to **mediawikishare**
[*]Set the Comment to **MediaWiki Backup**
[*]Click the **Permissions** button
[*]Select **Everyone** and click the **Remove** button
[*]Click the **Add** button
[*]Type in your MediaWiki share account: [COLOR="red"]**work\mediawikishare**[/COLOR] and click the **Check Names** button, click **OK**
[*]Place a checkmark for **Allow Full Control** and click **OK**, click **OK**, click **OK**
[*]Create a text file in the root of the shared folder called "online.txt" and you might want to add some text inside saying to never delete this file because it is used (will be) by a MediaWiki backup script.  Probably a good idea to make it read-only as well.  Example: [B]D:\MediaWiki\online.txt[B]
[/LIST]

[SIZE=4]Create an NFS mount to the Windows 2008 server[/SIZE]

Connecting to a Windows share requires the **samba** and **smbfs** packages to be installed.  If you did not install them (from a prior section), type **aptitude -y install samba smbfs**


[LIST=1]
[*]At the login prompt, login with your administrator account ([COLOR="red"]administrator[/COLOR] / [COLOR="red"]myadminpass[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Type the following commands:
```
[B]mkdir -p /mnt/backup
chown root:root /mnt/backup
chmod 0755 /mnt/backup
echo "This file is used to tell if the mount is active or not" > /mnt/backup/offline.txt
chown root:root /mnt/backup/offline.txt
chmod 0444 /mnt/backup/offline.txt
touch /etc/cifspw
chmod 0600 /etc/cifspw[/B]
```
[*]Type **vi /etc/cifspw** and add the following text, save and exit the file:
```
[B]username=[COLOR="red"]work\mediawikishare[/COLOR]
password=[COLOR="red"]mywikisharepassword[/COLOR][/B]
```
[*]Type **vi /etc/hosts** and add the following line anywhere in the file:
```
[B][COLOR="red"]192.168.107.218    srv-backup
192.168.107.20    srv-sql
192.168.107.25    srv-mail[/COLOR][/B]
```
[*]At this point, you might want to type **ping [COLOR="red"]srv-backup[/COLOR]** to make sure you typed the right IP address as well as seeing a good response.
[*]To mount this system for backups, type the following command:
```
**mount -t cifs //srv-backup/mediawikishare /mnt/backup --options nouser,rw,nofail,noatime,noexec,credentials=/etc/cifspw**
```
[*]To test it, type **cp /etc/hosts /mnt/backup/hosts.txt** and look on the Windows server and see if the file shows up.  Then type **rm /mnt/backup/hosts.txt** and verify that the file was deleted on the windows server.
[*]This would also be a good time to verify that you can see the "online.txt" file that will be used by the backup script. Type **ls -l /mnt/backup/*.txt**
[*]To dismount the windows share, type the following command:
```
**umount /mnt/backup**
```
[/LIST]

The scripts will call a common mount and unmount function to connect to this share only when needed.

However, if you would rather have it mounted all the time (even after a reboot), do the following (but remember to not use the mount/umount functions in the scripts later):


[LIST=1]
[*]Type **vi /etc/fstab** and add the following line at the bottom of the file:
```
**//[COLOR="red"]srv-backup/mediawikishare[/COLOR]    /mnt/backup    cifs nouser,rw,nofail,noatime,noexec,credentials=/etc/cifspw    0    0**
```
[*]Type **mount -a** and if it does not spew out any error messages, it will quietly mount the share.
[*]To test it, type **cp /etc/hosts /mnt/backup/hosts.txt** and look on the Windows server and see if the file shows up.  Then type **rm /mnt/backup/hosts.txt** and verify that the file was deleted on the windows server.
[*]If you need to unmount it, simply type **umount /mnt/backup** and it will remain unmounted until you reboot.  To make it permanent, you need to remove the line you added in the /etc/fstab file.
[/LIST]


[SIZE="5"]Configure Ubuntu for Linux File Sharing[/SIZE]

This file sharing section is optional but can be handy if you need to swap files between Linux servers.

This documentation will utilize this share for writing files to remote Linux servers using the same share point as the Windows samba folder.

Install NFS server files

[LIST=1]
[*]Connect to your server using PuTTY.
[*]At the login prompt, login with your administrator account ([COLOR="red"]administrator[/COLOR] / [COLOR="red"]myadminpass[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Install NFS server files by typing **aptitude -y install nfs-kernel-server nfs-common**)
[*]Edit **/etc/exports** and add the following line:
```
**/srv/samba/share    *(rw,sync,no_subtree_check)**
```
[*]Refresh NFS folders by typing **exportfs -a**
[/LIST]


Connecting to a remote Ubuntu server that has an NFS mount configured ("srv-mysql" in this example)

[LIST=1]
[*]Connect to your server using PuTTY.
[*]At the login prompt, login with your administrator account ([COLOR="red"]administrator[/COLOR] / [COLOR="red"]myadminpass[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Type the following commands:
```
[B]mkdir -p /mnt/srv-mysql
echo "This file is used to tell if the mount is active or not" > /mnt/srv-mysql/offline.txt
mount srv-mysql:/srv/samba/share /mnt/srv-mysql
ls -l /mnt/srv-mysql[/B]
```
[*]If it worked, the list command will show you the files on the remote server instead of the "offline.txt" file.
[*]To unmount the NFS, type **umount /mnt/srv-mysql**
[/LIST]

---

### Post by LHammonds on 2012-05-13
[SIZE="5"]Final Ubuntu Changes[/SIZE]

[LIST=1]
[*]Start the Ubuntu server and connect using PuTTY.
[*]At the login prompt, login with your administrator account ([COLOR="red"]administrator[/COLOR] / [COLOR="red"]myadminpass[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Update the package database by typing **aptitude update**
[*]Install the latest updates by typing **aptitude -y safe-upgrade**
[*]Shutdown and power off the server by typing **shutdown -P now** [COLOR="green"]{ENTER}[/COLOR]
[*]In VM menu, select VM --> Snapshot --> Take Snapshot.  Give it a name like **STEP 3** and description of **Ubuntu Server 12.04 LTS, all patches applied, Static IP: [COLOR="red"]192.168.107.23[/COLOR]**.  The Snapshot Manager should now have a nice hierarchy of snapshots (STEP 1 --> STEP 2 --> STEP 3 --> You are here)
[/LIST]


TIP: Over time, upgrades to the kernel can start taking up space in /usr/src.  I found this out because my root partition started to get full.  When I typed this command: **du -sh /usr/src/*** I found out there was over a gigabyte of old files.  To cleanly clear out old an unused headers, type the following commands:
```
[B]
apt-get -f install
apt-get autoremove
[/B]
```

[SIZE="5"]Configure MySQL[/SIZE]

In this scenario, a dedicated and general-purpose MySQL server already exists and it will be used to hold the MediaWiki database.


[LIST=1]
[*]Connect to the MySQL server using PuTTY.
[*]At the login prompt, login with your administrator account ([COLOR="red"]administrator[/COLOR] / [COLOR="red"]myadminpass[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Type **mysql -u root -p**
[*]Type the following commands:
```
[B]
CREATE DATABASE mediawiki;
CREATE USER [COLOR="red"]mediawikiuser[/COLOR];
SET PASSWORD FOR '[COLOR="red"]mediawikiuser[/COLOR]'@'%'=PASSWORD('[COLOR="red"]mediawikiuserpassword[/COLOR]');
GRANT ALL PRIVILEGES ON mediawiki.* TO [COLOR="red"]mediawikiuser[/COLOR] IDENTIFIED BY '[COLOR="red"]mediawikiuserpassword[/COLOR]';
FLUSH PRIVILEGES;
exit
[/B]
```
[/LIST]


NOTE: Here is the thread for [my notes on how I install MySQL on Ubuntu 12.04 LTS]("http://ubuntuforums.org/showthread.php?t=1983344")

[SIZE="5"]Install Apache Web Server[/SIZE]


[LIST=1]
[*]Connect to the SRV-Wiki server using PuTTY.
[*]At the login prompt, login with your administrator account ([COLOR="red"]administrator[/COLOR] / [COLOR="red"]myadminpass[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Type the following commands:
```
[B]
aptitude -y install apache2
[/B]
```
[*]If you plan on utilizing email functions (and who doesn't!!!), type the following commands:
```
[B]
aptitude -y install php-pear
pear install mail
pear install Net_SMTP
[/B]
```
[*]Once that is done, open a web browser and go to **[http://192.168.107.23](http://192.168.107.23)** and you should see a web page that says "It works!"
[/LIST]


[SIZE="5"]Add Web Site Icon[/SIZE]

If you want a custom icon to show up to the left of URL in the address bar, you need to follow these steps.


[LIST=1]
[*]Create a 16x16 image that is 16 colors (4-bit) with dimensions of 16x16 pixels and save it as a .BMP file called favicon.bmp
[*]Use your favorite icon editor to convert the BMP image to an ICO file. (e.g. IrfanView)
[*]Copy favicon.ico to **\\192.168.107.23\share**
[*]Connect to the SRV-Wiki server using PuTTY.
[*]At the login prompt, login with your administrator account ([COLOR="red"]administrator[/COLOR] / [COLOR="red"]myadminpass[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Type the following commands:
```
[B]
mv /srv/samba/share/favicon.ico /var/www/.
chown www-data:root /var/www/favicon.ico
chmod 0755 /var/www/favicon.ico
[/B]
```
[*]Edit **/etc/apache2/httpd.conf** and add the following line:
```
[B]
AddType image/x-icon .ico
[/B]
```
[*]Restart the Apache web server by typing **service apache2 restart**
[*]Once that is done, open a web browser and go to **[http://192.168.107.23](http://192.168.107.23)** and refresh the page.  You should see your icon to the left of the URL in the address bar.
[/LIST]


[SIZE="5"]Install MediaWiki Prerequisites[/SIZE]


[LIST=1]
[*]At the server console, type **aptitude -y install php5 php5-mysql php5-gd imagemagick**
[*]Now restart the web service, type **service apache2 restart**
[/LIST]

---

### Post by LHammonds on 2012-05-13
[SIZE="5"]Install MediaWiki[/SIZE]

At the time of this writing, MediaWiki's current version is 1.19.0 so we will be downloading and installing that archive.


[LIST=1]
[*]Connect to the MediaWiki server using PuTTY.
[*]At the login prompt, login with your administrator account ([COLOR="red"]administrator[/COLOR] / [COLOR="red"]myadminpass[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Type the following:
```
[B]
rm /var/www/index.html
cd /tmp
wget http://download.wikimedia.org/mediawiki/1.19/mediawiki-1.19.0.tar.gz
tar -xzvf /tmp/media*.gz -C /var/www/ --strip-components=1
chown www-data:root --recursive /var/www/*
find /var/www/. -type d -exec chmod 755 '{}' \+
find /var/www/. -type f -exec chmod 644 '{}' \+
rm /tmp/media*.gz
[/B]
```
[*]Open a browser and go to **http://[COLOR="red"]192.168.107.23[/COLOR]**, click on the "set up the wiki" link when the page loads.
[*]Installation Language - Click **Continue** to accept en-English
[*]Envirnomental Checks - Click **Continue**
[*]Connect to database - Set the following and click **Continue**:
Database type: **MySQL**
Database host: **[COLOR="red"]192.168.107.20[/COLOR]**
Database name: **mediawiki**
Database table prefix:
Database username: **[COLOR="red"]mediawikiuser[/COLOR]**
Database password: **[COLOR="red"]mediawikiuserpassword[/COLOR]**
[*]Database settings - Set the following and click **Continue**:
**Check** - Use the same account as for installation
Storage engine: **InnoDB**
Database character set: **Binary**
[*]Name - Set the following and click **Continue**:
Name of wiki: **[COLOR="red"]MyWiki[/COLOR]**
Project namespace: **Same as the wiki name**
Your Name: **[COLOR="red"]JohnDoe[/COLOR]**
Password: **[COLOR="red"]Hobo123![/COLOR]**
Password again: **[COLOR="red"]Hobo123![/COLOR]**
E-mail address: **[COLOR="red"]JohnDoe@mydomain.com[/COLOR]**
**Uncheck**: Subscribe to the release announcements mailing list
**Check**: Ask me more questions
[*]Options - Set the following and click **Continue**:
User rights profile: **Account creation required**
Copyright and license: **No license footer**
**Check**: Enable outbound e-mail
Return e-mail address: **no-reply@mydomain.com**
**Check**: Enable user-to-user e-mail
**Check**: Enable user talk page notification
**Check**: Enable watchlist notification
**Check**: Enable e-mail authentication
**Check**: ConfirmEdit
**Check**: Gadgets
**Uncheck**: Nuke
**Check**: ParserFunctions
**Check**: Renameuser    (* NOTE: Do not enable if you plan to use external LDAP authentication *)
**Check**: Vector
**Check**: WikiEditor
**Check**: Enable file uploads
Directory for deleted files: **/var/www/images/deleted**
Logo URL: **/wiki/skins/common/images/mylogo.png**
**Uncheck**: Enable Instant Commons
**Uncheck**: No caching
[*]Install Confirmation - Click **Continue**
[*]Install Done - Click **Continue**
[*]Save the **LocalSettings.php** to your PC and then transfer to **\\[COLOR="red"]192.168.107.23[/COLOR]\share**
[*]On the server console, type the following:
```
[B]
mv /srv/samba/share/LocalSettings.php /var/www/.
chown www-data:root /var/www/LocalSettings.php
chmod 0600 /var/www/LocalSettings.php
[/B]
```
[*]Increase the php filesize limit of uploaded files by editing **/etc/php5/apache2/php.ini** and find **upload_max_filesize** and change it from 2M to **50M**, then find **post_max_size** and change it from 8M to **51M**
[*]Increase the wiki filesize limit of uploaded files by editing **/var/www/LocalSettings.php** and add the following line: **$wgMaxUploadSize = '52428800';** ([Reference]("http://www.mediawiki.org/wiki/Manual:$wgMaxUploadSize"))
[*]Allow various file types to be uploaded and certain file types to be blocked by editing **/var/www/LocalSettings.php** and add the following lines:
```
[B]
# Allow the files to be uploaded with the following extensions:
$wgFileExtensions[] = 'bmp';
$wgFileExtensions[] = 'doc';
$wgFileExtensions[] = 'docx';
$wgFileExtensions[] = 'gif';
$wgFileExtensions[] = 'jpg';
$wgFileExtensions[] = 'jpeg';
$wgFileExtensions[] = 'mp3';
$wgFileExtensions[] = 'mpp';
$wgFileExtensions[] = 'odt';
$wgFileExtensions[] = 'ods';
$wgFileExtensions[] = 'odp';
$wgFileExtensions[] = 'odg';
$wgFileExtensions[] = 'pdf';
$wgFileExtensions[] = 'ppt';
$wgFileExtensions[] = 'pptx';
$wgFileExtensions[] = 'ps';
$wgFileExtensions[] = 'png';
$wgFileExtensions[] = 'tiff';
$wgFileExtensions[] = 'xls';
$wgFileExtensions[] = 'xlsx';

# Block files from being uploaded with the following extensions:
$wgFileBlacklist[] = 'exe';
$wgFileBlacklist[] = 'php';
$wgFileBlacklist[] = 'sh';
$wgFileBlacklist[] = 'com';
$wgFileBlacklist[] = 'vbs';
$wgFileBlacklist[] = 'bat';
$wgFileBlacklist[] = 'htm';
$wgFileBlacklist[] = 'html';
$wgFileBlacklist[] = 'js';
[/B]
```
[*]Edit **/var/www/LocalSettings.php** and add the following line:
```
[B]
$wgFavicon = "$wgScriptPath/favicon.ico";
[/B]
```
[*]Edit **/var/www/LocalSettings.php** and make sure the path for $wgLogo points to your custom logo:
```

$wgLogo             = "$wgStylePath/common/images/[COLOR="red"]mylogo.png[/COLOR]";

```
[*]Create a logo image in PNG format that has the dimensions of 135 x 133 pixels.  Save it to **\\[COLOR="red"]192.168.107.23[/COLOR]\share\mylogo.png**
[*]On the server console, type the following:
```
[B]
chown www-data:root /srv/samba/share/mylogo.png
chmod 0644 /srv/samba/share/mylogo.png
mv /srv/samba/share/mylogo.png /var/www/skins/common/images/.
[/B]
```
[*]Edit **/var/www/LocalSettings.php** and add the following lines (preferably after the existing email variables):
```
[B]
$wgSMTP = array(
 'host'     => "[COLOR="red"]mail.mydomain.com[/COLOR]", //could also be an IP address
 'IDHost'   => "[COLOR="red"]mydomain.com[/COLOR]",
 'port'     => 25,
 'auth'     => true,
 'username' => "[COLOR="red"]my_smtp_username[/COLOR]",
 'password' => "[COLOR="red"]my_smtp_password[/COLOR]"
);
[/B]
```
[*]To enable the WikiEditor by default, edit **/var/www/LocalSettings.php** and add the following lines (preferably right after WikiEditor extension line):
```
[B]
$wgDefaultUserOptions['usebetatoolbar'] = 1;
$wgDefaultUserOptions['usebetatoolbar-cgd'] = 1;
$wgDefaultUserOptions['wikieditor-preview'] = 1;
$wgDefaultUserOptions['forceeditsummary'] = 1;
[/B]
```
[*]NOTE: To see a list of other preferences you can set by default, look at [this page]("http://www.mediawiki.org/wiki/Manual:$wgDefaultUserOptions") or run the following command: **php /var/www/maintenance/userOptions.php --list**
[*]To set configure some settings for the ConfirmEdit extension, edit **/var/www/LocalSettings.php** and add the following lines (preferably after the ConfirmEdit extension line):
```
[B]
$wgCaptchaTriggers['edit']          = true;
$wgCaptchaTriggers['create']        = true;
$wgCaptchaTriggers['addurl']        = true;
$wgCaptchaTriggers['createaccount'] = true;
$wgCaptchaTriggers['badlogin']      = true;
$wgGroupPermissions['emailconfirmed']['skipcaptcha'] = true;
$ceAllowConfirmedEmail = true;
[/B]
```
[*]Restart the Apache web server by typing **service apache2 restart**
[*]Visit **http://[COLOR="red"]192.168.107.23[/COLOR]/**
[*]You should see your wiki page with your custom logo.  Test your login ID that you created earlier.
[/LIST]

---

### Post by LHammonds on 2012-05-13
[SIZE="5"]Install More Extensions for MediaWiki[/SIZE]

Normally, you will go to the [Extension Distributor]("http://www.mediawiki.org/wiki/Special:ExtensionDistributor") page to select your desired extension.  Then you will pick which version of MediaWiki you are running (1.19.x in this case) and then obtain the snapshot that works with the specific MediaWiki site you are running.  Download and copy the archive to **\\[COLOR="red"]192.168.107.23[/COLOR]\share**

Anytime you create new files on your website, you need to make sure the files and folders have the correct ownership and permission settings.

Run these commands each time you need to reset ownership/permissions:

```
[B]
chown www-data:root --recursive /var/www/*
find /var/www/. -type d -exec chmod 755 '{}' \+
find /var/www/. -type f -exec chmod 644 '{}' \+
chmod 0600 /var/www/LocalSettings.php
chmod 0755 /var/www/favicon.ico
[/B]
```

[SIZE="4"][FlashMP3]("http://www.mediawiki.org/wiki/Extension:FlashMP3")[/SIZE]


[LIST=1]
[*]Copy the php code on the web page to a file called **FlashMP3.php** and copy it to **\\[COLOR="red"]192.168.107.23[/COLOR]\share**
[*]Download the [standalone player]("http://wpaudioplayer.com/download/") archive.  Extract **audio-player.js** and **player.swf** and copy them to **\\[COLOR="red"]192.168.107.23[/COLOR]\share**
[*]At the server console, type the following commands:
```
[B]
mkdir /var/www/extensions/FlashMP3
mv /srv/samba/share/FlashMP3.php /var/www/extensions/FlashMP3/.
mv /srv/samba/share/audio-player.js /var/www/extensions/FlashMP3/.
mv /srv/samba/share/player.swf /var/www/extensions/FlashMP3/.
[/B]
```
[*]Reset ownership/permissions (see code at beginning of this section).
[*]Edit **/var/www/LocalSettings.php** and add the following to the bottom:
```
[B]
require_once( "$IP/extensions/FlashMP3/FlashMP3.php" );
[/B]
```
[*]Visit the version page to verify that the extension was installed and loaded: **http://[COLOR="red"]192.168.107.23[/COLOR]/index.php/Special:Version**
[/LIST]


[SIZE="4"][VideoFlash]("http://www.mediawiki.org/wiki/Extension:VideoFlash")[/SIZE]


[LIST=1]
[*]Copy the php code on the web page to a file called **VideoFlash.php** and copy it to **\\[COLOR="red"]192.168.107.23[/COLOR]\share**
[*]At the server console, type the following commands:
```
[B]
mkdir /var/www/extensions/VideoFlash
mv /srv/samba/share/VideoFlash.php /var/www/extensions/VideoFlash/.
[/B]
```
[*]Reset ownership/permissions (see code at beginning of this section).
[*]Edit **/var/www/LocalSettings.php** and add the following to the bottom:
```
[B]
require_once( "$IP/extensions/VideoFlash/VideoFlash.php" );
[/B]
```
[*]Visit the version page to verify that the extension was installed and loaded: **http://[COLOR="red"]192.168.107.23[/COLOR]/index.php/Special:Version**
[/LIST]


NOTE: The authors of this particular plugin did not include a version number and thus, none is displayed on the version page.  You can correct this by editing the php file.

Change this:
```
[B]
        'url' => 'http://www.mediawiki.org/wiki/Extension:VideoFlash'
);
[/B]
```
To this:
```
[B]
        'url' => 'http://www.mediawiki.org/wiki/Extension:VideoFlash',
        'version' => '1.0'
);
[/B]
```

[SIZE="4"][ContactPage]("http://www.mediawiki.org/wiki/Extension:ContactPage")[/SIZE]


[LIST=1]
[*]Download ConfirmPage from the [Extension Distributor]("http://www.mediawiki.org/wiki/Special:ExtensionDistributor") and copy to the Ubuntu share
[*]On the server console, type the following:
```
[B]
mv /srv/samba/share/ContactPage* /tmp/.
tar -xzf /tmp/ContactPage* -C /var/www/extensions
[/B]
```
[*]Reset ownership/permissions.
[*]Edit **/var/www/LocalSettings.php** and add the following to the bottom:
```
[B]
require_once( "$IP/extensions/ContactPage/ContactPage.php" );
$wgContactUser = 'Admin';
$wgContactSender = $wgPasswordSender;
$wgContactSenderName = 'Contact Form on ' . $wgSitename;
$wgCaptchaTriggers['contactpage'] = true;
[/B]
```
[*]Visit the version page to verify that the extension was installed and loaded: **http://[COLOR="red"]192.168.107.23[/COLOR]/index.php/Special:Version**
[/LIST]


NOTE #1: The wgContactUser must reference a valid email-enabled wiki user in order to display the form properly.

NOTE #2: The authors of this particular plugin did not include a version number and thus, none is displayed on the version page.  You can correct this by editing the php file.

Change this:
```
[B]
        'url' => 'http://www.mediawiki.org/wiki/Extension:ContactPage',
        'descriptionmsg' => 'contactpage-desc',
[/B]
```
To this:
```
[B]
        'url' => 'http://www.mediawiki.org/wiki/Extension:ContactPage',
        'version' => '1.0.76660',
        'descriptionmsg' => 'contactpage-desc',
);
[/B]
```

[SIZE="4"][SyntaxHighlight GeSHi]("http://www.mediawiki.org/wiki/Extension:SyntaxHighlight_GeSHi")[/SIZE]


[LIST=1]
[*]Download SyntaxHighlight GeSHi from the [Extension Distributor]("http://www.mediawiki.org/wiki/Special:ExtensionDistributor") and copy to the Ubuntu share
[*]On the server console, type the following:
```
[B]
mv /srv/samba/share/Syntax* /tmp/.
tar -xzf /tmp/Syntax* -C /var/www/extensions
mv /var/www/extensions/SyntaxHighlight_GeSHi-master-f7617c9 /var/www/extensions/SyntaxHighlight_GeSHi
[/B]
```
[*]Reset ownership/permissions.
[*]Edit **/var/www/LocalSettings.php** and add the following to the bottom:
```
[B]
require_once( "$IP/extensions/SyntaxHighlight_GeSHi/SyntaxHighlight_GeSHi.php" );
[/B]
```
[*]Visit the version page to verify that the extension was installed and loaded: **http://[COLOR="red"]192.168.107.23[/COLOR]/index.php/Special:Version**
[/LIST]


[SIZE="4"][Contribution Scores]("http://www.mediawiki.org/wiki/Extension:Contribution_Scores")[/SIZE]


[LIST=1]
[*]Download Contribution Scores from the [Extension Distributor]("http://www.mediawiki.org/wiki/Special:ExtensionDistributor") and copy to the Ubuntu share
[*]On the Ubuntu console, type the following:
```
[B]
mv /srv/samba/share/Contrib* /tmp/.
tar -xzf /tmp/Contrib* -C /var/www/extensions
[/B]
```
[*]Reset ownership/permissions.
[*]Edit **/var/www/LocalSettings.php** and add the following to the bottom:
```
[B]
require_once( "$IP/extensions/ContributionScores/ContributionScores.php" );
$wgContribScoreIgnoreBots = true;          // Exclude Bots from the reporting - Can be omitted.
$wgContribScoreIgnoreBlockedUsers = true;  // Exclude Blocked Users from the reporting - Can be omitted.
$wgContribScoresUseRealName = true;        // Use real user names when available - Can be omitted. Only for MediaWiki 1.19 and later.
$wgContribScoreDisableCache = false;       // Set to true to disable cache for parser function and inclusion of table.
//Each array defines a report - 7,50 is "past 7 days" and "LIMIT 50" - Can be omitted.
$wgContribScoreReports = array(
    array(7,50),
    array(30,50),
    array(0,50));
[/B]
```
[*]CSS classes are used but not defined (this is optional but recommended).  Edit **/var/www/skins/common/commonElements.css** and add the following lines:
```
[B]
.contributionscores-wrapper    {  }
.contributionscores-title      { background-color: #aaaaaa; margin-bottom: 0px; padding-left: .4em; }
.contributionscores .header    { background-color: #cccccc; border-bottom: 1px solid #999999; font-weight: bold; }
.contributionscores .odd       { background-color: #eeeeee; }
.contributionscores .header td { padding-left: .2em; padding-right: .2em; }
.contributionscores .content   { padding-left: .2em; padding-right: .2em; }
[/B]
```
[*]Visit the version page to verify that the extension was installed and loaded: **http://[COLOR="red"]192.168.107.23[/COLOR]/index.php/Special:Version**
[/LIST]



[SIZE="4"][LDAP Authentication]("http://www.mediawiki.org/wiki/Extension:LDAP_Authentication")[/SIZE]

All of our users are in a Microsoft Active Directory 2003 domain.  These steps will allow MediaWiki to authenticate against the AD and auto-create a wiki account in the process of logging in.

References:
 - [LDAP Authentication Requirements]("http://www.mediawiki.org/wiki/Extension:LDAP_Authentication/Requirements")
 - [LDAP Authentication Options]("www.mediawiki.org/wiki/Extension:LDAP_Authentication/Options")
 - [How to enable LDAP over SSL with a third-party certification authority]("http://support.microsoft.com/kb/321051")

Configure MediaWiki:

[LIST=1]
[*]Download LDAP Authentication from the [Extension Distributor]("http://www.mediawiki.org/wiki/Special:ExtensionDistributor") and copy to the Ubuntu share.  NOTE: The current version is 1.2e and designed for MediaWiki 1.18.x but works in 1.19.0
[*]On the Ubuntu console, type the following:
```
[B]
mv /srv/samba/share/LdapAuth* /tmp/.
tar -xzf /tmp/LdapAuth* -C /var/www/extensions
[/B]
```
[*]Reset ownership/permissions.
[*]Edit **/var/www/LocalSettings.php** and add the following to the bottom:
```
[B]
require_once( "$IP/extensions/LdapAuthentication/LdapAuthentication.php" );
$wgAuth = new LdapAuthenticationPlugin();
$wgLDAPDomainNames = array("[COLOR="red"]mydomain.com[/COLOR]");
$wgLDAPServerNames = array("[COLOR="red"]mydomain.com[/COLOR]"=>"[COLOR="red"]work.mydomain.com[/COLOR]");
$wgLDAPUseLocal = false;
$wgLDAPEncryptionType = array("[COLOR="red"]mydomain.com[/COLOR]"=>"ssl","[COLOR="red"]mydomain.com[/COLOR]"=>"tls");
$wgLDAPSearchStrings = array("[COLOR="red"]mydomain.com[/COLOR]"=>"[COLOR="red"]work[/COLOR]\\USER-NAME");
$wgLDAPDisableAutoCreate = array("[COLOR="red"]mydomain.com[/COLOR]"=>false);
#LDAPDebug will show debug info
# 0 (default) = disabled (best for production systems)
# 1 = Will display non-sensitive info
# 2 = Will display possibly sensitive info
# 3 = Will display sensitive system info
$wgLDAPDebug = 0;
[/B]
```
[*]Visit the version page to verify that the extension was installed and loaded: **http://[COLOR="red"]192.168.107.23[/COLOR]/index.php/Special:Version**
[/LIST]


Configure Ubuntu:

[LIST=1]
[*]Connect to the SRV-Wiki server using PuTTY.
[*]At the login prompt, login with your administrator account ([COLOR="red"]administrator[/COLOR] / [COLOR="red"]myadminpass[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Install the LDAP library for PHP by typing **install php5-ldap**
[*]If your Active Directory domain has a certificate, type the following:
```
[B]
openssl s_client -showcerts -connect [COLOR="red"]work.mydomain.com[/COLOR]:636 > /usr/local/share/ca-certificates/cert.crt
quit
[/B]
```
[*]If your Active Directory domain does not have a certificate, use your web server:
```
[B]
openssl s_client -showcerts -connect [COLOR="red"]www.mydomain.com[/COLOR]:443 > /usr/local/share/ca-certificates/cert.crt
quit
[/B]
```
[*]If you do not have a web server that has an SSL certificate, try **google.com:443** instead.
[*]Edit **/usr/local/share/cs-certificates/cert.crt**
[*]Find the 1st certificate and delete everything above **-----BEGIN CERTIFICATE-----**
[*]Find the bottom of the 1st certificate and delete everything after **-----END CERTIFICATE-----**
[*]You should have something that looks like this:
```

-----BEGIN CERTIFICATE-----
MIIF0DCCBTmgAwIBAgIKFUj0TwAAAABS8DANBgkqhkiG9w0BAQUFADBGMQswCQYD
VQQGEwJVUzETMBEGA1UEChMKR29vZ2xlIEluYzEiMCAGA1UEAxMZR29vZ2xlIElu
dGVybmV0IEF1dGhvcml0eTAeFw0xMjA1MDIxMTA2NTdaFw0xMzA1MDIxMTE2NTda
MGYxCzAJBgNVBAYTAlVTMRMwEQYDVQQIEwpDYWxpZm9ybmlhMRYwFAYDVQQHEw1N
b3VudGFpbiBWaWV3MRMwEQYDVQQKEwpHb29nbGUgSW5jMRUwEwYDVQQDFAwqLmdv
b2dsZS5jb20wgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBAMGHpxE/UIg9t1Zs
RcdR3PJ72quccUCxHzBLRrkBjexBL89+L+m9P/XFDDrXozTxoZlga2Hy0qkIdUv7
vcaE16rl4vHhkOnvPLG683LFFOdRwWMuZeGUMXsqB3/GK7o2Ay3bzCrXmabv952f
CzDa/vRuB5zBxlAtQl7UPfJfgy6lAgMBAAGjggOjMIIDnzAdBgNVHSUEFjAUBggr
BgEFBQcDAQYIKwYBBQUHAwIwHQYDVR0OBBYEFDYKKSKamB4E8BXEAscAmzoM/9cS
MB8GA1UdIwQYMBaAFL/AMOv1QxE+Z7qekfv8atrjaxIkMFsGA1UdHwRUMFIwUKBO
oEyGSmh0dHA6Ly93d3cuZ3N0YXRpYy5jb20vR29vZ2xlSW50ZXJuZXRBdXRob3Jp
dHkvR29vZ2xlSW50ZXJuZXRBdXRob3JpdHkuY3JsMGYGCCsGAQUFBwEBBFowWDBW
BggrBgEFBQcwAoZKaHR0cDovL3d3dy5nc3RhdGljLmNvbS9Hb29nbGVJbnRlcm5l
dEF1dGhvcml0eS9Hb29nbGVJbnRlcm5ldEF1dGhvcml0eS5jcnQwggJ3BgNVHREE
ggJuMIICaoIMKi5nb29nbGUuY29tggpnb29nbGUuY29tgg0qLnlvdXR1YmUuY29t
ggt5b3V0dWJlLmNvbYIWKi55b3V0dWJlLW5vY29va2llLmNvbYIIeW91dHUuYmWC
CyoueXRpbWcuY29tgg8qLmdvb2dsZS5jb20uYnKCDiouZ29vZ2xlLmNvLmluggsq
Lmdvb2dsZS5lc4IOKi5nb29nbGUuY28udWuCCyouZ29vZ2xlLmNhggsqLmdvb2ds
ZS5mcoILKi5nb29nbGUucHSCCyouZ29vZ2xlLml0ggsqLmdvb2dsZS5kZYILKi5n
b29nbGUuY2yCCyouZ29vZ2xlLnBsggsqLmdvb2dsZS5ubIIPKi5nb29nbGUuY29t
LmF1gg4qLmdvb2dsZS5jby5qcIILKi5nb29nbGUuaHWCDyouZ29vZ2xlLmNvbS5t
eIIPKi5nb29nbGUuY29tLmFygg8qLmdvb2dsZS5jb20uY2+CDyouZ29vZ2xlLmNv
bS52boIPKi5nb29nbGUuY29tLnRygg0qLmFuZHJvaWQuY29tggthbmRyb2lkLmNv
bYIUKi5nb29nbGVjb21tZXJjZS5jb22CECoudXJsLmdvb2dsZS5jb22CFiouZ29v
Z2xldGFnbWFuYWdlci5jb22CFGdvb2dsZXRhZ21hbmFnZXIuY29tggwqLnVyY2hp
bi5jb22CCnVyY2hpbi5jb22CFiouZ29vZ2xlLWFuYWx5dGljcy5jb22CFGdvb2ds
ZS1hbmFseXRpY3MuY29tghIqLmNsb3VkLmdvb2dsZS5jb22CBmdvby5nbIIEZy5j
bzANBgkqhkiG9w0BAQUFAAOBgQCyBzOsXXz5FhOxVcLeplWWss6sgJCvmAlzvhY/
5YpdFsdKhzEmh13aogii7FGG3i+LH0i7dSlWy+QZ8v23lDbE6SGySQN2fusSThC8
Wz1i/6D/kpJw90tGInJL/yvW9z60Hw1TUG6/heyYBHe2JhHa6CgqTyowRoaii1rA
iQBF8w==
-----END CERTIFICATE-----

```
[*]Save and close the file
[*]Verify that the certificate is valid by typing **openssl x509 -noout -text -in /usr/local/share/cs-certificates/cert.crt**
[*]Now update the certificates by typing **update-ca-certificates**
[*]Edit **/etc/ldap/ldap.conf** and make sure it contains the following lines:
```
[B]
TLS_CACERTDIR   /etc/ssl/certs
TLS_CACERT      /etc/ssl/certs/ca-certificates.crt
[/B]
```
[*]Visit the login page and verify that a domain user can login (that does not have a mediawiki account): **http://[COLOR="red"]192.168.107.23[/COLOR]/index.php?title=Special:UserLogin**
[/LIST]

---

### Post by LHammonds on 2012-05-13
[SIZE="5"]Scripting[/SIZE]


Much of the solutions beyond this point involve scripts (programming snippets / automated commands).

In particular, they are Bash Scripts. I chose this due to its popularity and the fact it comes with Ubuntu. I try to make use of what comes with the system without requiring additional software / services unless they really add to the bottom line such as decreasing the time it takes for a process to run or to conserve storage and bandwidth usage.

When setting up a server and testing things out, there is typically very little concern for procedures / process since much of the activity is exploration and experimentation as well as not having an impact on production. However, once a server goes into production, processes and procedures need to be in place to ensure the availability of the services being provided.

In regards to these scripts, they will be treated like any other program and will require being tested, documented and go through a promotion process.

The ideal situation would involve 3 servers (for a single server setup). A test / development server, a quality assurance staging server and the production server itself. If 3 servers cannot be utilized, then it can still work well with 2 servers. Testing scripts / programs / restore on the production server is not advisable and many times impractical...how can you test your restore process / data periodically if you only have a production server?

The QA Staging server would resemble the production server as much as possible. The server should be setup in such a way that production backups are restored to this server which also tests and validates the backup / restore process as well as maintains a close representation of the production server to mitigate variable risk involved when testing new or modified programs and upgrades.

The test / development server can serve as the QA server if absolutely necessary.

The directory structure and how scripts can import other scripts will be configured to facilitate this process.

Example:

Directory path for scripts to import common variables, functions and server settings: **/var/scripts/common/**

Directory path for production scripts: **/var/scripts/prod/**

Directory path for QA staging area scripts: **/var/scripts/qa/**

Directory path for test / development scripts: **/var/scripts/test/**

Directory path for data for use by scripts: **/var/scripts/data/**

With a production and test servers on physically different machines, the "common" scripts folder can be custom-tailored for that environment and allow for minimal changes to a script when running on the test, QA or production server.  This is similar to "normalizing" a database.  If you have a variable, path or function that is duplicated in multiple scripts, consider pulling it out and placing it in the common folder.  If ever you need to change who receives the email reports, you only need to update a single script and all programs will use the new reference from that point on.

Most of my scripts will import a file called "standard.conf" from the common script folder.

/var/scripts/common/standard.conf (contents of the file on the **production** server)
```

## Global Variables ##
TEMPDIR="/temp"
LOGDIR="/var/log"
APPDIR="/var/www"
SHAREDIR="/srv/samba/share"
MYDOMAIN="[COLOR="red"]mydomain.com[/COLOR]"
ADMINEMAIL="admin@${MYDOMAIN}"
REPORTEMAIL="[COLOR="red"]lhammonds[/COLOR]@${MYDOMAIN}"
BACKUPDIR="/backup"
OFFSITEDIR="/mnt/backup"
OFFSITETESTFILE="${OFFSITEDIR}/online.txt"
ARCHIVEMETHOD="tar.7z"    ## Choices are tar.7z or tgz
HOSTNAME="$(hostname -s)"
SCRIPTNAME="$0"
SCRIPTDIR="/var/scripts"
MAILFILE="${TEMPDIR}/mailfile.$$"

## Global Functions ##

function f_sendmail()
{
  ## Purpose: Send administrative email message.
  ## Parameter #1 = Subject
  ## Parameter #2 = Body
  sendemail -f "${ADMINEMAIL}" -t "${REPORTEMAIL}" -u "${1}" -m "${2}\n\nServer: ${HOSTNAME}\nProgram: ${SCRIPTNAME}\nLog: ${LOGFILE}" -s srv-mail:25 1>/dev/null 2>&1
}

function f_sendusermail()
{
  ## Purpose: Send end-user email message.
  ## Parameter #1 = To
  ## Parameter #2 = Subject
  ## Parameter #3 = Body
  sendemail -f "${ADMINEMAIL}" -t "${1}" -u "${2}" -m "${3}" -s srv-mail:25 1>/dev/null 2>&1
}

function f_mount()
{
  ## Mount the pre-configured Windows share folder.
  ## NOTE: The Windows share should have a file called "online.txt"
  mount -t cifs //srv-backup/mediawikishare ${OFFSITEDIR} --options nouser,rw,nofail,noatime,noexec,credentials=/etc/cifspw
}

function f_umount()
{
  ## Dismount the Windows share folder.
  ## NOTE: The unmounted folder should have a file called "offline.txt"
  umount ${OFFSITEDIR}
}

```


/var/scripts/common/standard.conf (contents of the file on the **test** server)
```

## Global Variables ##
TEMPDIR="/tmp"
LOGDIR="/var/log"
APPDIR="/var/www"
SHAREDIR="/srv/samba/share"
MYDOMAIN="[COLOR="red"]mytestdomain.com[/COLOR]"
ADMINEMAIL="test1@${MYDOMAIN}"
REPORTEMAIL="test2@${MYDOMAIN}"
BACKUPDIR="/backup"
OFFSITEDIR="/mnt/fakedir"
OFFSITETESTFILE="${OFFSITEDIR}/online.txt"
ARCHIVEMETHOD="tar.7z"    ## Choices are tar.7z or tgz
HOSTNAME="$(hostname -s)"
SCRIPTNAME="$0"
SCRIPTDIR="/var/scripts"
MAILFILE="${TEMPDIR}/mailfile.$$"

## Global Functions ##

function f_sendmail()
{
  ## Purpose: Send administrative email message.
  ## Parameter #1 = Subject
  ## Parameter #2 = Body
  sendemail -f "${ADMINEMAIL}" -t "${REPORTEMAIL}" -u "${1}" -m "${2}\n\nServer: ${HOSTNAME}\nProgram: ${SCRIPTNAME}\nLog: ${LOGFILE}" -s srv-mail:25 1>/dev/null 2>&1
}

function f_sendusermail()
{
  ## Purpose: Send end-user email message.
  ## Parameter #1 = To
  ## Parameter #2 = Subject
  ## Parameter #3 = Body
  sendemail -f "${ADMINEMAIL}" -t "${1}" -u "${2}" -m "${3}" -s srv-mail:25 1>/dev/null 2>&1
}

function f_mount()
{
  ## Mount the pre-configured Windows share folder.
  ## NOTE: The Windows share should have a file called "online.txt"
  mount -t cifs //mypc/share ${OFFSITEDIR} --options nouser,rw,nofail,noatime,noexec,credentials=/etc/cifspw
}

function f_umount()
{
  ## Dismount the Windows share folder.
  ## NOTE: The unmounted folder should have a file called "offline.txt"
  umount ${OFFSITEDIR}
}

```


When receiving administrative email notifications, the server name, script name and path will be included at the bottom of the email every time.  It will be readily apparent if the email was generated from the test, qa or production server simply because of the location (even if test, qa and production are all on the same server).

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

### Post by LHammonds on 2012-05-14
[SIZE="5"]Toggle Mount[/SIZE]

Sometimes it is helpful to toggle the mount on or off so here is a script you might find helpful.

/var/scripts/prod/togglemount.sh
```

#!/bin/bash
#############################################
## Name          : togglemount.sh
## Version       : 1.0
## Date          : 2012-05-11
## Author        : LHammonds
## Compatibility : Ubuntu Server 12.04 LTS
## Purpose       : Toggle the mount status of a pre-configured backup mount.
## Run Frequency : Manual as needed.
## Exit Codes    :
##   0 = success
##   1 = failure
################ CHANGE LOG #################
## DATE       WHO WHAT WAS CHANGED
## ---------- --- ----------------------------
## 2012-05-11 LTH Created script.
#############################################

## Import common variables and functions. ##
source /var/scripts/common/standard.conf
ERRORFLAG=0

if [ -f ${OFFSITEDIR}/offline.txt ]; then
  echo "Windows share is not mounted.  Mounting share now..."
  f_mount
  sleep 2
  if [ -f ${OFFSITEDIR}/online.txt ]; then
    echo "Mount successful.  Listing contents:"
  else
    echo "Mount failed.  Listing contents:"
    ERRORFLAG=1
  fi
else
  echo "Windows share is mounted.  Dismounting share now..."
  f_umount
  sleep 2
  if [ -f ${OFFSITEDIR}/offline.txt ]; then
    echo "Dismount successful.  Listing contents:"
  else
    echo "Dismount failed.  Listing contents:"
    ERRORFLAG=1
  fi
fi
ls -l ${OFFSITEDIR}
exit ${ERRORFLAG}

```


[SIZE="5"]MySQL Backup[/SIZE]

My database server exports all databases and archives them on a normal schedule so any database I add to it such as the mediawiki database will get included automatically.

However, I created another script designed to run every minute looking for key files.  If a specific file shows up on the samba share, it will trigger an immediate backup of the specified database.  This will be helpful when scheduling the backup of the MediaWiki web files.  When the web backup script run, it will place the database-specific file on the remote database server's samba share which will trigger the database backup to run immediately.  The web backup script can trigger the remote database backup anytime it runs no matter if it is schedule via crontab or manually run.

Here is the script that runs every minute on the database server:

/var/scripts/prod/mysql-db-backup.sh
```

#!/bin/bash
#############################################
## Name          : mysql-db-backup.sh
## Version       : 1.0
## Date          : 2012-05-14
## Author        : LHammonds
## Purpose       : Backup of a single database
## Compatibility : Verified on Ubuntu Server 10.04.3 LTS, MySQL 5.1.62
## Requirements  : p7zip-full (if ARCHIVEMETHOD=tar.7z), sendemail
## Run Frequency : As needed
## Exit Codes    : (if multiple errors, value is the addition of codes)
##    0 = success
##    1 = 7zip not installed
##    2 = archive failure
##    4 = archive purge failure
##    8 = configuration error
##   16 = mount warning
################ CHANGE LOG #################
## DATE       WHO WHAT WAS CHANGED
## ---------- --- ----------------------------
## 2012-05-14 LTH Created script.
#############################################

## Import common variables and functions. ##
source /var/scripts/common/standard.conf

LOGFILE="${TEMPDIR}/mysql-db-backup.log"
LOCKFILE="${TEMPDIR}/mysql-db-backup.lock"
TARGETDIR="${BACKUPDIR}/mysql-db"
OFFSITEBACKDIR="${OFFSITEDIR}/mysql-db"
ERRORFLAG=0

#######################################
##            FUNCTIONS              ##
#######################################
function f_PurgeOldestArchive()
{
  ## Purpose: Delete the oldest archive on the remote site.
  ## Return values:
  ##    0 = Success
  ##    1 = Cannot delete file
  ##    9 = Configuration error, path empty

  ## Variable Error Check. *
  if [ ${OFFSITEBACKDIR} = "" ]; then
    ## Make darn sure the path is not empty since we do NOT
    ## want to start purging files from a random location.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- Purge error: OFFSITEBACKDIR site variable is empty!" >> ${LOGFILE}
    return 9
  fi
  ## Get the name of the oldest file.
  OLDESTFILE=`ls -1t ${OFFSITEBACKDIR} | tail -1`
  if [ "${OLDESTFILE}" = "" ]; then
    ## Error. Filename variable empty.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- Purge error: OLDESTFILE variable is empty." >> ${LOGFILE}
    return 9
  else   
    FILESIZE=`ls -lak "${OFFSITEBACKDIR}/${OLDESTFILE}" | awk '{ print $5 }' | sed -e :a -e 's/\(.*[0-9]\)\([0-9]\{3\}\)/\1,\2/;ta'`
    echo "`date +%Y-%m-%d_%H:%M:%S` --- Purging old file: ${OFFSITEBACKDIR}/${OLDESTFILE}, Size = ${FILESIZE} kb" >> ${LOGFILE}
    rm "${OFFSITEBACKDIR}/${OLDESTFILE}"
    if [ -f "${OFFSITEBACKDIR}/${OLDESTFILE}" ]; then
      ## File still exists.  Return error.
      return 1
    else
      return 0
    fi
  fi
}

function f_cleanup()
{
  if [ -f ${LOCKFILE} ];then
    ## Remove lock file so other rsync jobs can run.
    rm ${LOCKFILE} 1>/dev/null 2>&1
  fi
  if [[ "${TARGETDIR}" != "" && "{TARGETDIR}" != "/" ]]; then
    ## Remove local backup files.
    rm -rf ${TARGETDIR}/*
  fi
  ## Email the result to the administrator.
  if [ ${ERRORFLAG} -eq 0 ]; then
    f_sendmail "MySQL DB Backup Success" "MySQL backup completed with no errors."
  else
    f_sendmail "MySQL DB Backup ERROR" "MySQL backup failed.  ERRORFLAG = ${ERRORFLAG}"
  fi
}

function f_emergencyexit()
{
  ## Purpose: Exit script as cleanly as possible.
  ## Parameter #1 = Error Code
  f_cleanup
  echo "`date +%Y-%m-%d_%H:%M:%S` - MySQL backup exit code: ${ERRORFLAG}" >> ${LOGFILE}
  exit $1
}

#######################################
##           MAIN PROGRAM            ##
#######################################

## Binaries ##
TAR="$(which tar)"
MY7ZIP="$(which 7za)"
MYSQL="$(which mysql)"
MYSQLDUMP="$(which mysqldump)"

if [ -f ${LOCKFILE} ]; then
  ## Program lock file detected.  Abort script.
  f_sendmail "MySQL DB Backup Aborted - Lock File" "This script tried to run but detected the lock file: ${LOCKFILE}\n\nPlease check to make sure the file does not remain when this script is not actually running."
  exit 1
else
  ## Create the lock file to ensure only one script is running at a time.
  echo "`date +%Y-%m-%d_%H:%M:%S` ${SCRIPTNAME}" > ${LOCKFILE}
fi

## Figure out which database will be backed up. Only one per run.
if [ -f "${SHAREDIR}/mediawiki" ]; then
  DATABASE="mediawiki"
  rm "${SHAREDIR}/mediawiki"
elif [ -f "${SHAREDIR}/phpbb" ]; then
  DATABASE="phpbb"
  rm "${SHAREDIR}/phpbb"
elif [ -f "${SHAREDIR}/wordpress" ]; then
  DATABASE="wordpress"
  rm "${SHAREDIR}/wordpress"
fi
if [[ "${DATABASE}" = "" ]]; then
  f_cleanup 0
  exit 0
fi

ARCHIVEFILE="`date +%Y-%m-%d-%H-%M`_mysql-db-${DATABASE}.${ARCHIVEMETHOD}"

echo "`date +%Y-%m-%d_%H:%M:%S` - MySQL ${DATABASE} backup started." >> ${LOGFILE}

## If the 7-Zip archive method is specified, make sure the package is installed.
if [ "${ARCHIVEMETHOD}" = "tar.7z" ]; then
  if [ ! -f "/usr/bin/7za" ]; then
    ## Required package (7-Zip) not installed.
    echo "`date +%Y-%m-%d_%H:%M:%S` - CRITICAL ERROR: 7-Zip package not installed.  Please install by typing 'aptitude -y install p7zip-full'" >> ${LOGFILE}
    ERRORFLAG=1
    f_emergencyexit ${ERRORFLAG}
  fi
fi

StartTime="$(date +%s)"

## Backup individual database.
${MYSQLDUMP} ${DATABASE} > ${TARGETDIR}/${DATABASE}.sql
## Create database sub-folder.
mkdir -p ${TARGETDIR}/${DATABASE}
## Export each table in the database individually.
for TABLE in `echo "show tables" | $MYSQL ${DATABASE}|grep -v Tables_in_`;
do
  FILE=${TARGETDIR}/${DATABASE}/${TABLE}.sql
  case "${TABLE}" in
    general_log)
      ${MYSQLDUMP} ${DATABASE} ${TABLE} --skip-lock-tables > ${FILE}
      ;;
    slow_log)
      ${MYSQLDUMP} ${DATABASE} ${TABLE} --skip-lock-tables > ${FILE}
      ;;
    *)
      ${MYSQLDUMP} ${DATABASE} ${TABLE} > ${FILE}
      ;;
  esac
done

## Compress the backup into a single file based on archive method specified.
echo "`date +%Y-%m-%d_%H:%M:%S` --- Compressing archive: ${TEMPDIR}/${ARCHIVEFILE}" >> ${LOGFILE}
case "${ARCHIVEMETHOD}" in
tar.7z)
  ${TAR} -cpf - ${TARGETDIR} | ${MY7ZIP} a -si -mx=9 -w${TEMPDIR} ${TEMPDIR}/${ARCHIVEFILE} 1>/dev/null 2>&1
  RETURNVALUE=$?
  ## Restore using one of the following commands (do not uncomment, only for notation):
  ## 7za x -so -w/tmp ${TEMPDIR}/${ARCHIVEFILE} | tar -C / -xf -
  ## 7za x -so -w/tmp ${TEMPDIR}/${ARCHIVEFILE} | tar -C ${TEMPDIR}/restore --strip-components=1 -xf -
  ;;
tgz)
  ${TAR} -cpzf ${TEMPDIR}/${ARCHIVEFILE} ${TARGETDIR} 1>/dev/null 2>&1
  RETURNVALUE=$?
  ## Restore using one of the following commands (do not uncomment, only for notation):
  ## tar -C / -xzf ${TEMPDIR}/${ARCHIVEFILE}
  ## tar -C ${TEMPDIR}/restore --strip-components=1 -xzf ${TEMPDIR}/${ARCHIVEFILE}
  ;;
*)
  ${TAR} -cpzf ${TEMPDIR}/${ARCHIVEFILE} ${TARGETDIR} 1>/dev/null 2>&1
  RETURNVALUE=$?
  ;;
esac

if [ ${RETURNVALUE} -ne 0 ]; then
  ## tar command failed.  Send warning email.
  f_sendmail "MySQL Backup Failure - tar" "tar failed with return value of ${RETURNVALUE}"
  ERRORFLAG=$((${ERRORFLAG} + 2))
fi

## Mount the remote folder. ##
f_mount

if [ ! -f ${OFFSITETESTFILE} ]; then
  ## Could not find expected file on remote site.  Assuming failed mount.
  ERRORFLAG=$((${ERRORFLAG} + 16))
  echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: Cannot detect remote location: ${OFFSITETESTFILE}" >> ${LOGFILE}
  f_emergencyexit ${ERRORFLAG}
fi

FREESPACE=`df -k ${OFFSITEDIR} | grep ${OFFSITEDIR} | awk '{ print $3 }'`
BACKUPSIZE=`ls -lak "${TEMPDIR}/${ARCHIVEFILE}" | awk '{ print $5 }'`

## Make sure space is available on the remote server to copy the file.
if [ ${FREESPACE} -lt ${BACKUPSIZE} ]; then
  ## Not enough free space available.  Purge existing backups until there is room.
  ENOUGHSPACE=0
  while [ ${ENOUGHSPACE} -eq 0 ]
  do
    f_PurgeOldestArchive
    RETURNVALUE=$?
    case ${RETURNVALUE} in
    1)
      ## Cannot purge archives to free up space.  End program gracefully.
      echo "`date +%Y-%m-%d_%H:%M:%S` - ERROR: Not enough free space on ${OFFSITEBACKDIR} and cannot purge old archives.  Script aborted." >> ${LOGFILE}
      ## Stop and exit the script with an error code.
      ERRORFLAG=$((${ERRORFLAG} + 4))
      f_emergencyexit ${ERRORFLAG}
      ;;
    9)
      ## Configuration error, end program gracefully.
      echo "`date +%Y-%m-%d_%H:%M:%S` - ERROR: Configuration problem. Script aborted." >> ${LOGFILE}
      ## Stop and exit the script with an error code.
      ERRORFLAG=$((${ERRORFLAG} + 8))
      f_emergencyexit ${ERRORFLAG}
      ;;
    esac
    FREESPACE=`df -k ${OFFSITEDIR} | grep ${OFFSITEDIR} | awk '{ print $3 }'`
    if [ ${FREESPACE} -gt ${BACKUPSIZE} ]; then
      ## Enough space is now available.
      ENOUGHSPACE=1
    else
      ## Not enough space is available yet.
      ENOUGHSPACE=0
    fi
  done
fi

## Copy the backup to an offsite storage location.
echo "`date +%Y-%m-%d_%H:%M:%S` --- Copying archive file to offsite location." >> ${LOGFILE}
cp ${TEMPDIR}/${ARCHIVEFILE} ${OFFSITEBACKDIR}/${ARCHIVEFILE} 1>/dev/null 2>&1
if [ ! -f ${OFFSITEBACKDIR}/${ARCHIVEFILE} ]; then
  ## NON-FATAL ERROR: Copy command did not work.  Send email notification.
  echo "`date +%Y-%m-%d_%H:%M:%S` --- WARNING: Remote copy failed. ${OFFSITEBACKDIR}/${ARCHIVEFILE} does not exist!" >> ${LOGFILE}
  f_sendmail "MySQL Backup Failure - Remote Copy" "Remote copy failed. ${OFFSITEBACKDIR}/${ARCHIVEFILE} does not exist\n\nBackup file still remains in this location: ${HOSTNAME}:${TEMPDIR}/${ARCHIVEFILE}"
else
  ## Remove local copy of the compressed backup file
  rm ${TEMPDIR}/${ARCHIVEFILE}
fi

## Unmount the Windows shared folder.
f_umount

## Calculate total time for backup.
FinishTime="$(date +%s)"
ElapsedTime="$(expr ${FinishTime} - ${StartTime})"
Hours=$((${ElapsedTime} / 3600))
ElapsedTime=$((${ElapsedTime} - ${Hours} * 3600))
Minutes=$((${ElapsedTime} / 60))
Seconds=$((${ElapsedTime} - ${Minutes} * 60))

echo "`date +%Y-%m-%d_%H:%M:%S` --- Total backup time: ${Hours} hour(s) ${Minutes} minute(s) ${Seconds} second(s)" >> ${LOGFILE}

echo "`date +%Y-%m-%d_%H:%M:%S` - MySQL ${DATABASE} backup completed." >> ${LOGFILE}

## Perform cleanup routine.
f_cleanup
## Exit with the combined return code value.
exit ${ERRORFLAG}

```

Here is a sample of the log file:

/temp/mysql-db-backup.log
```

2012-05-14_13:10:13 - MySQL backup exit code: 0
2012-05-14_13:10:33 - MySQL mediawiki backup started.
2012-05-14_13:10:34 --- Compressing archive: /var/temp/2012-05-14-13-10_mysql-db-mediawiki.tar.7z
2012-05-14_13:10:35 --- Copying archive file to offsite location.
2012-05-14_13:10:35 --- WARNING: Remote copy failed. /mnt/backup/mysql-db/2012-05-14-13-10_mysql-db-mediawiki.tar.7z does not exist!
2012-05-14_13:10:35 --- Total backup time: 0 hour(s) 0 minute(s) 2 second(s)
2012-05-14_13:10:35 - MySQL mediawiki backup completed.
2012-05-14_13:10:35 - MySQL backup exit code: 0
2012-05-14_13:12:37 - MySQL backup exit code: 0
2012-05-14_13:14:50 - MySQL mediawiki backup started.
2012-05-14_13:14:51 --- Compressing archive: /var/temp/2012-05-14-13-14_mysql-db-mediawiki.tar.7z
2012-05-14_13:14:55 --- Copying archive file to offsite location.
2012-05-14_13:14:56 --- Total backup time: 0 hour(s) 0 minute(s) 6 second(s)
2012-05-14_13:14:56 - MySQL mediawiki backup completed.
2012-05-14_13:15:13 - MySQL backup exit code: 0
2012-05-14_13:16:38 - MySQL mediawiki backup started.
2012-05-14_13:16:39 --- Compressing archive: /var/temp/2012-05-14-13-16_mysql-db-mediawiki.tar.7z
2012-05-14_13:16:40 --- Copying archive file to offsite location.
2012-05-14_13:16:41 --- Total backup time: 0 hour(s) 0 minute(s) 3 second(s)
2012-05-14_13:16:41 - MySQL mediawiki backup completed.
2012-05-14_13:16:47 - MySQL phpbb backup started.
2012-05-14_13:16:49 --- Compressing archive: /var/temp/2012-05-14-13-16_mysql-db-phpbb.tar.7z
2012-05-14_13:16:55 --- Copying archive file to offsite location.
2012-05-14_13:16:56 --- Total backup time: 0 hour(s) 0 minute(s) 9 second(s)
2012-05-14_13:16:56 - MySQL phpbb backup completed.
2012-05-14_13:16:59 - MySQL wordpress backup started.
2012-05-14_13:16:59 --- Compressing archive: /var/temp/2012-05-14-13-16_mysql-db-wordpress.tar.7z
2012-05-14_13:17:05 --- Copying archive file to offsite location.
2012-05-14_13:17:06 --- Total backup time: 0 hour(s) 0 minute(s) 7 second(s)
2012-05-14_13:17:06 - MySQL wordpress backup completed.

```

---

### Post by lisati on 2012-05-14
tl;dr :D

---

### Post by LHammonds on 2012-05-14
> **lisati said:**
> tl;dr :D
That's OK.  Some people like to read such ramblings. It is mainly for my own documentation and future projects.

[SIZE=5]Check Storage Space[/SIZE]

In favor of manage by exception, I wrote a script that can be scheduled to run daily to check the file systems to see if they are getting close to filling up and will automatically expand them a little bit and give you an email notice.  Everything is done at the megabyte level.  If you do not want the script to perform the increase, simply add a pound sign in front of the resize2fs command on line 64 to comment it out.  Might also want to modify the log and email messages so it does not look like it actually "performed" the resize but instead is telling YOU how to perform the resize.

Here are the lines I added to my crontab schedule which will check each file system I expect will grow on a daily basis @ 1am, 2am and 3am.  I have them checking to see if we have less than 50 MB available and if so, it will try to increase by 50 MB.

crontab
```

0 1 * * * /var/scripts/prod/check-storage.sh var 50 50 > /dev/null 2>&1
0 2 * * * /var/scripts/prod/check-storage.sh bak 50 50 > /dev/null 2>&1
0 3 * * * /var/scripts/prod/check-storage.sh temp 50 50 > /dev/null 2>&1

```/var/scripts/prod/check-storage.sh
```

#!/bin/bash
#############################################
## Name          : check-storage.sh
## Version       : 1.0
## Date          : 2012-05-11
## Author        : LHammonds
## Purpose       : Check available space for a file system and expand if necessary.
## Compatibility : Verified on Ubuntu Server 12.04 LTS
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
#############################################

## Import standard variables and functions. ##
source /var/scripts/common/standard.conf

## Define local variables.
LOGFILE="${TEMPDIR}/check-storage.log"
LOCKFILE="${TEMPDIR}/check-storage.lock"
ErrorFlag=0
ReturnCode=0

#######################################
##            FUNCTIONS              ##
#######################################

function f_cleanup()
{
  if [ -f ${LOCKFILE} ];then
    ## Remove lock file so other check space jobs can run.
    rm ${LOCKFILE} 1>/dev/null 2>&1
  fi
  exit ${ErrorFlag}
}

function f_showhelp()
{
  echo -e "\nUsage : ${SCRIPTNAME} FileSystemName ThresholdSizeInMB AmountToIncreaseByInMB\n"
  echo -e "\nExample: ${SCRIPTNAME} var 50 50\n"
}

function f_auto-increment()
{
  let RoomInLV=${LVSize}-${FSSize}
  if [[ ${RoomInLV} -gt ${FSIncreaseBy} ]]; then
    ## There is room in the LV to increase space to the FS.
    resize2fs ${FSVol} ${NewFSSize}M
    ReturnCode=$?
    echo "`date +%Y-%m-%d_%H:%M:%S` --- resize2fs ${FSVol} ${NewFSSize}M, ReturnCode=${ReturnCode}" | tee -a ${LOGFILE}
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

if [ -f ${LOCKFILE} ]; then
  # Lock file detected.  Abort script.
  echo "Check space script aborted"
  echo "This script tried to run but detected the lock file: ${LOCKFILE}"
  echo "Please check to make sure the file does not remain when check space is not actually running."
  f_sendmail "ERROR: check storage script aborted" "This script tried to run but detected the lock file: ${LOCKFILE}\n\nPlease check to make sure the file does not remain when check space is not actually running.\n\nIf you find that the script is not running/hung, you can remove it by typing 'rm ${LOCKFILE}'"
  ErrorFlag=4
  f_cleanup
else
  echo "`date +%Y-%m-%d_%H:%M:%S` ${SCRIPTNAME}" > ${LOCKFILE}
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
  "var")
    FSVol="/dev/LVG/var"
    FSMap="/dev/mapper/LVG-var"
    ;;
  "bak")
    FSVol="/dev/LVG/bak"
    FSMap="/dev/mapper/LVG-bak"
    ;;
  "temp")
    FSVol="/dev/LVG/temp"
    FSMap="/dev/mapper/LVG-temp"
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
  echo "`date +%Y-%m-%d_%H:%M:%S` - Starting expansion of ${FSVol}" | tee -a ${LOGFILE}
  echo "`date +%Y-%m-%d_%H:%M:%S` --- LVSize=${LVSize}MB, FSSize=${FSSize}MB, FSAvail=${FSAvailable}MB, FSThreshold=${FSThreshold}MB, FSIncreaseBy=${FSIncreaseBy}MB" | tee -a ${LOGFILE}
  ## Run the auto-expansion function.
  f_auto-increment
  ReturnCode=$?
  case ${ReturnCode} in
  0)
    f_sendmail "NOTICE: File System Expanded" "${FSVol} was expanded because it was nearing max capacity.  Please review disk space usage and plan appropriately. LVSize=${LVSize}MB, FSSize=${FSSize}MB, FSAvailable=${FSAvailable}MB, FSThreshold=${FSThreshold}MB, FSIncreaseBy=${FSIncreaseBy}MB"
    ;;
  50)
    echo "`date +%Y-%m-%d_%H:%M:%S` - SEVERE: No room to expand ${FSVol}" | tee -a ${LOGFILE}
    ErrorFlag=16
    f_sendmail "SEVERE: No room to expand ${FSVol}" "There is not enough room in the Logical Volume to expand the ${FSVol} File System.  Immediate action is required.  Make sure there is free space in the Volume Group 'LVG' and then expand the Logical Volume...then expand the File System.\n\nLVSize=${LVSize}MB, FSSize=${FSSize}MB, FSAvailable=${FSAvailable}MB, FSThreshold=${FSThreshold}MB, FSIncreaseBy=${FSIncreaseBy}MB.\n\nType 'vgs' to see if there is any free space in the Volume Group which can be given to the Logical Volume.\n\nType 'lvs' to see the current sizes of the LVs.\n\nType 'lvdisplay' to see a list of Logical Volumes so you can get the LV Name which is used in the lvextend and resize2fs commands.\n\nType 'lvextend -L+50M /dev/LVG/var' if you want to extend the var Logical Volume by 50 megabytes (assuming there is 50MB available in the Volume Group).\n\nType 'df --block-size=m' to see a list of file systems and their associated size and available space.\n\nType 'resize2fs /dev/LVG/var ${NewFSSize}M' to set the size of var to ${NewFSSize} megabytes. Make sure you set the size to the desired end-result which should be LARGER than the current FS size so you do not lose data."
    ;;
  *)
    echo "`date +%Y-%m-%d_%H:%M:%S` - ERROR: Expansion failure for ${FSVol}" | tee -a ${LOGFILE}
    ErrorFlag=8
    f_sendmail "ERROR: File System Expansion Failed" "${FSVol} Expansion failed with return code of ${ReturnCode}.  LVSize=${LVSize}MB, FSSize=${FSSize}MB, FSAvailable=${FSAvailable}MB, FSThreshold=${FSThreshold}MB, FSIncreaseBy=${FSIncreaseBy}MB"
    ;;
  esac
  echo "`date +%Y-%m-%d_%H:%M:%S` - Finished expansion of ${FSVol}" | tee -a ${LOGFILE}
else
  echo "`date +%Y-%m-%d_%H:%M:%S` - ${FSVol} ${FSAvailable}M>${FSThreshold}M No action required." | tee -a ${LOGFILE}
fi

## Perform cleanup routine.
f_cleanup

```Here is the typical output when it does not have to increase the FS:

/var/temp/check-storage.log
```

2012-05-01_01:00:00 - /dev/LVG/var 44M>5M No action required.
2012-05-01_02:00:00 - /dev/LVG/bak 91M>5M No action required.
2012-05-01_03:00:00 - /dev/LVG/temp 93M>5M No action required.
2012-05-02_01:00:00 - /dev/LVG/var 44M>5M No action required.
2012-05-02_02:00:00 - /dev/LVG/bak 91M>5M No action required.
2012-05-02_03:00:00 - /dev/LVG/temp 93M>5M No action required.
2012-05-03_01:00:00 - /dev/LVG/var 44M>5M No action required.
2012-05-03_02:00:00 - /dev/LVG/bak 91M>5M No action required.
2012-05-03_03:00:00 - /dev/LVG/temp 93M>5M No action required.

```Here is a sample of what the log will look like when it perform increases...notice how I had to increase the threshold in order for it to fire off the increase (but it still just issued a single megabyte increase):

/var/temp/check-storage.log
```

2012-05-02_01:00:00 - Starting expansion of /dev/LVG/var
2012-05-02_01:00:00 --- LVSize=75MB, FSSize=50MB, FSAvail=44MB, FSThreshold=55MB, IncreaseBy=1MB
2012-05-02_01:00:00 --- resize2fs /dev/LVG/var 51, ReturnCode=0
2012-05-02_01:00:00 - Finished expansion of /dev/LVG/var
2012-05-02_02:00:00 - Starting expansion of /dev/LVG/bak
2012-05-02_02:00:00 --- LVSize=125MB, FSSize=99MB, FSAvail=91MB, FSThreshold=100MB, IncreaseBy=1MB
2012-05-02_02:00:00 --- resize2fs /dev/LVG/bak 100, ReturnCode=0
2012-05-02_02:00:00 - Finished expansion of /dev/LVG/bak
2012-05-02_03:00:00 - Starting expansion of /dev/LVG/temp
2012-05-02_03:00:00 --- LVSize=125MB, FSSize=99MB, FSAvail=93MB, FSThreshold=100MB, IncreaseBy=1MB
2012-05-02_03:00:00 --- resize2fs /dev/LVG/temp 100, ReturnCode=0
2012-05-02_03:00:00 - Finished expansion of /dev/LVG/temp
```

---

### Post by LHammonds on 2012-05-15
[SIZE="5"]MediaWiki Backup[/SIZE]

There are various methods of backup that can be utilized but for this server, I will simply use RSync and tar.

RSync will mirror the files in the production folder to a local backup folder.  The archive will be created from this backup folder.

Here are the folders I consider important that will be included in the backup:

Data Folders:
SRV-Wiki: /backup (which contains a mirror of /var/www)

Config Folders and files:
SRV-Wiki: /var/log/apache2/
SRV-Wiki: /etc/apache2/
SRV-Wiki: /etc/php5/
SRV-Wiki: /etc/network/interfaces
SRV-Wiki: /etc/hosts

Remote Data:
SRV-MYSQL: MediaWiki Database

The backup of the web site will be fairly simplistic.  However, since there are multiple servers involved, the backup will need to be synchronized for the web files, uploads and the remote database.

A crontab schedule will be used to schedule the local backups and when the backup is initiated on the local server, a special file will be sent to the remote database server so it will trigger a backup on the database that corresponds to this server (mediawiki).

The bulk of the data will be in /var/www and rsync will be used to copy any files from that folder to the backup folder.  The benefit and beauty of using rsync in this way is that it will only copy what has changed since the last backup/sync.  That means it will run VERY quickly even if your www folder has gigs of data in it.  The other miscellaneous folders will be archived directly from their source location which will not be much in terms of size.

/var/scripts/prod/mediawiki-backup.sh
```

#!/bin/bash
#############################################
## Name          : mediawiki-backup.sh
## Version       : 1.0
## Date          : 2012-05-15
## Author        : LHammonds
## Compatibility : Ubuntu Server 12.04 LTS
## Purpose       : Backup web server while online.
## Run Frequency : One or multiple times per day.
## Exit Codes    : (if multiple errors, value is the addition of codes)
##   0 = Success
##   1 = rsync failure
##   2 = Archive creation failure
##   4 = Remote copy failure
##   8 = Cannot connect to MySQL NFS mount
################ CHANGE LOG #################
## DATE       WHO WHAT WAS CHANGED
## ---------- --- ----------------------------
## 2012-05-15 LTH Created script.
#############################################

## Import common variables and functions. ##
source /var/scripts/common/standard.conf

LOGFILE="${TEMPDIR}/mediawiki-backup.log"
TARGET="${BACKUPDIR}/mediawiki"
LOCKFILE="${TEMPDIR}/mediawiki-backup.lock"
ARCHIVEFILE="`date +%Y-%m-%d-%H-%M`_mediawiki-backup.${ARCHIVEMETHOD}"
SOURCES="/backup /var/log/apache2/ /etc/apache2/ /etc/php5/ /etc/network/interfaces /etc/hosts"
ERRORFLAG=0
RETURNVALUE=0

#######################################
##            FUNCTIONS              ##
#######################################
function f_PurgeOldestArchive()
{
  ## Purpose: Delete the oldest archive on the remote site.
  ## Return values:
  ##    0 = Success
  ##    1 = Cannot delete file
  ##    9 = Configuration error, path empty

  ## Variable Error Check. *
  if [ ${OFFSITEBACKDIR} = "" ]; then
    ## Make darn sure the path is not empty since we do NOT
    ## want to start purging files from a random location.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- Purge error: OFFSITEBACKDIR site variable is empty!" >> ${LOGFILE}
    return 9
  fi
  ## Get the name of the oldest file.
  OLDESTFILE=`ls -1t ${OFFSITEBACKDIR} | tail -1`
  if [ "${OLDESTFILE}" = "" ]; then
    ## Error. Filename variable empty.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- Purge error: OLDESTFILE variable is empty." >> ${LOGFILE}
    return 9
  else   
    FILESIZE=`ls -lak "${OFFSITEBACKDIR}/${OLDESTFILE}" | awk '{ print $5 }' | sed -e :a -e 's/\(.*[0-9]\)\([0-9]\{3\}\)/\1,\2/;ta'`
    echo "`date +%Y-%m-%d_%H:%M:%S` --- Purging old file: ${OFFSITEBACKDIR}/${OLDESTFILE}, Size = ${FILESIZE} kb" >> ${LOGFILE}
    rm "${OFFSITEBACKDIR}/${OLDESTFILE}"
    if [ -f "${OFFSITEBACKDIR}/${OLDESTFILE}" ]; then
      ## File still exists.  Return error.
      return 1
    else
      return 0
    fi
  fi
}

function f_cleanup()
{
  if [ -f ${LOCKFILE} ];then
    ## Remove lock file so other backup jobs can run.
    rm "${LOCKFILE}" 1>/dev/null 2>&1
  fi
  echo "`date +%Y-%m-%d_%H:%M:%S` - MediaWiki backup exit code: ${ERRORFLAG}" >> ${LOGFILE}
}

#######################################
##           MAIN PROGRAM            ##
#######################################

## Binaries ##
TAR="$(which tar)"
MY7ZIP="$(which 7za)"
RSYNC="$(which rsync)"

if [ -f ${LOCKFILE} ]; then
  ## Script lock file detected.  Abort script.
  f_sendmail "MediaWiki Backup Aborted - Lock File" "This script tried to run but detected the lock file: ${LOCKFILE}\n\nPlease check to make sure the file does not remain when backup is not actually running."
  exit 1
else
  echo "`date +%Y-%m-%d_%H:%M:%S` ${SCRIPTNAME}" > ${LOCKFILE}
fi

StartTime="$(date +%s)"
echo "`date +%Y-%m-%d_%H:%M:%S` - Backup started." >> ${LOGFILE}

## Connect to the MySQL server to kick-off a remote database backup.
mount srv-mysql:/srv/samba/share /mnt/srv-mysql
if [ -f /mnt/srv-mysql/offline.txt ];then
  ## The mount command did not work.
  ERRORFLAG=${ERRORFLAG} + 8
else
  ## Create the key file to trigger a backup of the database.
  echo "Time to backup MediaWiki!" > /mnt/srv-mysql/mediawiki
  umount /mnt/srv-mysql
fi

## Output the version information to a text file which will be included in the backup.
if [ -f "${APPDIR}/version-info.txt" ]; then
  rm "${APPDIR}/version-info.txt"
fi
lsb_release -cd >> ${APPDIR}/version-info.txt
apache2 -v >> ${APPDIR}/version-info.txt
php -i >> ${APPDIR}/version-info.txt

## Check destination folder.  Create folder structure if not present.
if [ ! -d "${TARGET}" ]; then
  mkdir -p ${TARGET}
fi

## Synchronize files to backup folder.
${RSYNC} -apogHK --delete --exclude=*.pid ${APPDIR} ${TARGET} 1>/dev/null 2>&1
RETURNVALUE=$?
if [ ${RETURNVALUE} -ne 0 ]; then
  ## ERROR: Send email notification.
  echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: Backup failed. ${APPDIR} -> ${TARGET}" >> ${LOGFILE}
  f_sendmail "Backup Failure - rsync" "ERROR: Backup failed. ${APPDIR} -> ${TARGET}, RETURN VALUE = ${RETURNVALUE}"
  ERRORFLAG=${ERRORFLAG} + 1
fi

## Compress the backup into a single file based on archive method specified.
echo "`date +%Y-%m-%d_%H:%M:%S` --- Compressing archive: ${TEMPDIR}/${ARCHIVEFILE}" >> ${LOGFILE}
case "${ARCHIVEMETHOD}" in
tar.7z)
  ${TAR} -cpf - ${SOURCES} | ${MY7ZIP} a -si -mx=9 -w${TEMPDIR} ${TEMPDIR}/${ARCHIVEFILE} 1>/dev/null 2>&1
  RETURNVALUE=$?
  ## Restore using one of the following commands (do not uncomment, only for notation):
  ## 7za x -so -w/tmp ${TEMPDIR}/${ARCHIVEFILE} | tar -C / -xf -
  ## 7za x -so -w/tmp ${TEMPDIR}/${ARCHIVEFILE} | tar -C ${TEMPDIR}/restore --strip-components=1 -xf -
  ;;
tgz)
  ${TAR} -cpzf ${TEMPDIR}/${ARCHIVEFILE} ${SOURCES} 1>/dev/null 2>&1
  RETURNVALUE=$?
  ## Restore using one of the following commands (do not uncomment, only for notation):
  ## tar -C / -xzf ${TEMPDIR}/${ARCHIVEFILE}
  ## tar -C ${TEMPDIR}/restore --strip-components=1 -xzf ${TEMPDIR}/${ARCHIVEFILE}
  ;;
*)
  ${TAR} -cpzf ${TEMPDIR}/${ARCHIVEFILE} ${SOURCES} 1>/dev/null 2>&1
  RETURNVALUE=$?
  ;;
esac

if [ ${RETURNVALUE} -ne 0 ]; then
  ## tar command failed.  Send warning email.
  f_sendmail "MediaWiki Backup Failure - tar" "tar failed with return value of ${RETURNVALUE}"
  ERRORFLAG=$((${ERRORFLAG} + 2))
fi

## Mount the remote folder. ##
f_mount

if [ ! -f ${OFFSITETESTFILE} ]; then
  ## Could not find expected file on remote site.  Assuming failed mount.
  ERRORFLAG=$((${ERRORFLAG} + 16))
  echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: Cannot detect remote location: ${OFFSITETESTFILE}" >> ${LOGFILE}
  f_emergencyexit ${ERRORFLAG}
fi

FREESPACE=`df -k ${OFFSITEDIR} | grep ${OFFSITEDIR} | awk '{ print $3 }'`
BACKUPSIZE=`ls -lak "${TEMPDIR}/${ARCHIVEFILE}" | awk '{ print $5 }'`

## Make sure space is available on the remote server to copy the file.
if [ ${FREESPACE} -lt ${BACKUPSIZE} ]; then
  ## Not enough free space available.  Purge existing backups until there is room.
  ENOUGHSPACE=0
  while [ ${ENOUGHSPACE} -eq 0 ]
  do
    f_PurgeOldestArchive
    RETURNVALUE=$?
    case ${RETURNVALUE} in
    1)
      ## Cannot purge archives to free up space.  End program gracefully.
      echo "`date +%Y-%m-%d_%H:%M:%S` - ERROR: Not enough free space on ${OFFSITEBACKDIR} and cannot purge old archives.  Script aborted." >> ${LOGFILE}
      ## Stop and exit the script with an error code.
      ERRORFLAG=$((${ERRORFLAG} + 4))
      f_emergencyexit ${ERRORFLAG}
      ;;
    9)
      ## Configuration error, end program gracefully.
      echo "`date +%Y-%m-%d_%H:%M:%S` - ERROR: Configuration problem. Script aborted." >> ${LOGFILE}
      ## Stop and exit the script with an error code.
      ERRORFLAG=$((${ERRORFLAG} + 8))
      f_emergencyexit ${ERRORFLAG}
      ;;
    esac
    FREESPACE=`df -k ${OFFSITEDIR} | grep ${OFFSITEDIR} | awk '{ print $3 }'`
    if [ ${FREESPACE} -gt ${BACKUPSIZE} ]; then
      ## Enough space is now available.
      ENOUGHSPACE=1
    else
      ## Not enough space is available yet.
      ENOUGHSPACE=0
    fi
  done
fi

## Copy the backup to an offsite storage location.
echo "`date +%Y-%m-%d_%H:%M:%S` --- Copying archive file to offsite location." >> ${LOGFILE}
cp ${TEMPDIR}/${ARCHIVEFILE} ${OFFSITEDIR}/${ARCHIVEFILE} 1>/dev/null 2>&1
if [ ! -f ${OFFSITEDIR}/${ARCHIVEFILE} ]; then
  ## NON-FATAL ERROR: Copy command did not work.  Send email notification.
  echo "`date +%Y-%m-%d_%H:%M:%S` --- WARNING: Remote copy failed. ${OFFSITEDIR}/${ARCHIVEFILE} does not exist!" >> ${LOGFILE}
  f_sendmail "MediaWiki Backup Failure - Remote Copy" "Remote copy failed. ${OFFSITEDIR}/${ARCHIVEFILE} does not exist\n\nBackup file still remains in this location: ${HOSTNAME}:${TEMPDIR}/${ARCHIVEFILE}"
else
  ## Remove local copy of the compressed backup file
  rm "${TEMPDIR}/${ARCHIVEFILE}"
fi

## Unmount the Windows shared folder.
f_umount

## Calculate total time for backup.
FinishTime="$(date +%s)"
ElapsedTime="$(expr ${FinishTime} - ${StartTime})"
Hours=$((${ElapsedTime} / 3600))
ElapsedTime=$((${ElapsedTime} - ${Hours} * 3600))
Minutes=$((${ElapsedTime} / 60))
Seconds=$((${ElapsedTime} - ${Minutes} * 60))

echo "`date +%Y-%m-%d_%H:%M:%S` --- Total backup time: ${Hours} hour(s) ${Minutes} minute(s) ${Seconds} second(s)" >> ${LOGFILE}

echo "`date +%Y-%m-%d_%H:%M:%S` - MediaWiki backup completed." >> ${LOGFILE}

## Perform cleanup routine.
f_cleanup
## Exit with the combined return code value.
exit ${ERRORFLAG}

```

Here is some sample output from the log file.

/temp/mediawiki-backup.log
```

2012-05-15_10:17:57 - Backup started.
2012-05-15_10:17:58 --- Compressing archive: /temp/2012-05-15-10-17_mediawiki-backup.tar.7z
2012-05-15_10:18:49 --- Copying archive file to offsite location.
2012-05-15_10:18:49 --- Total backup time: 0 hour(s) 0 minute(s) 52 second(s)
2012-05-15_10:18:49 - MediaWiki backup completed.
2012-05-15_10:18:49 - MediaWiki backup exit code: 0
2012-05-15_10:23:16 - Backup started.
2012-05-15_10:23:16 --- Compressing archive: /temp/2012-05-15-10-23_mediawiki-backup.tar.7z
2012-05-15_10:24:05 --- Copying archive file to offsite location.
2012-05-15_10:24:26 --- Total backup time: 0 hour(s) 1 minute(s) 10 second(s)
2012-05-15_10:24:26 - MediaWiki backup completed.
2012-05-15_10:24:26 - MediaWiki backup exit code: 0
2012-05-15_10:38:41 - Backup started.
2012-05-15_10:38:41 --- Compressing archive: /temp/2012-05-15-10-38_mediawiki-backup.tar.7z
2012-05-15_10:39:31 --- Copying archive file to offsite location.
2012-05-15_10:39:57 --- Total backup time: 0 hour(s) 1 minute(s) 16 second(s)
2012-05-15_10:39:57 - MediaWiki backup completed.
2012-05-15_10:39:57 - MediaWiki backup exit code: 0
2012-05-15_10:44:37 - Backup started.
2012-05-15_10:44:39 --- Compressing archive: /temp/2012-05-15-10-44_mediawiki-backup.tar.7z
2012-05-15_10:45:28 --- Copying archive file to offsite location.
2012-05-15_10:45:59 --- Total backup time: 0 hour(s) 1 minute(s) 22 second(s)
2012-05-15_10:45:59 - MediaWiki backup completed.
2012-05-15_10:45:59 - MediaWiki backup exit code: 0

```

Here is the top part of the version info file included in each backup.

/var/www/version-info.txt
```

Description:    Ubuntu 12.04 LTS
Codename:    precise
Server version: Apache/2.2.22 (Ubuntu)
Server built:   Feb 13 2012 01:51:50
phpinfo()
PHP Version => 5.3.10-1ubuntu3.1

System => Linux srv-wiki 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64
Build Date => May  4 2012 02:18:29

```

---

### Post by LHammonds on 2012-05-15
[SIZE=5]Crontab[/SIZE]

I would not advise anyone to ever "edit" a live crontab schedule by typing "crontab -e" but rather edit a saved schedule file and then load the schedule file. This will allow you to make backups of the schedule so you can always go back to a known-good schedule or at least back to the way it was before you made a change...assuming you always work with a copy of the schedule 1st.

Here is my root crontab scheduling file:

/var/scripts/data/crontab.root

```

########################################
# Name: Crontab Schedule for root user
# Author: LHammonds
############# Update Log ###############
# 2012-05-15 - LTH - Created schedule
########################################

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow command

#
# Adjust the time clock
#
0 1-23 * * * /usr/sbin/ntpdate ntp.ubuntu.com > /dev/null 2>&1
#
# Backup MediaWiki
#
0 22 * * * /var/scripts/prod/mediawiki-backup.sh > /dev/null 2>&1
#
# Daily check for available space on /var
#
0 1 * * * /var/scripts/prod/check-storage.sh opt 50 50 > /dev/null 2>&1
#
# Daily check for available space on /backup
#
0 2 * * * /var/scripts/prod/check-storage.sh bak 50 50 > /dev/null 2>&1
#
# Daily check for available space on /temp
#
0 3 * * * /var/scripts/prod/check-storage.sh temp 50 50 > /dev/null 2>&1

```Once you have created the file, make sure appropriate permissions are set by typing the following:
```

chown root:root /var/scripts/data/crontab.root
chmod 0600 /var/scripts/data/crontab.root

```To enable the root schedule using this file, type the following:

```
crontab -u root /var/scripts/data/crontab.root
```To disable the root schedule, type the following:
```

touch /tmp/deleteme
crontab -u root /tmp/deleteme
rm /tmp/deleteme

```If you need to modify the schedule, make a backup copy 1st.   For example:

```

cp /var/scripts/data/crontab.root /var/scripts/data/2011-11-28-crontab.root
vi /var/scripts/data/crontab.root (make your changes)
crontab -u root /var/scripts/data/crontab.root

```

This concludes my documentation on how I setup a MediaWiki server.

If you notice any problems, please reply here and let me know.

Thanks,
LHammonds

---

### Post by d4m1r on 2012-05-15
Very well written! Great work. I vote to sticky ;)

---

### Post by LHammonds on 2012-06-01
[SIZE="5"]APT Upgrade[/SIZE]

Here is a script that can be scheduled to run daily to check for updates and then install them if available.

This is the line you put in crontab to have the script once per day @ 3am.

/var/scripts/data/crontab.root
```

0 3 * * * /var/scripts/prod/apt-upgrade.sh > /dev/null 2>&1

```

/var/scripts/prod/apt-upgrade.sh
```

#!/bin/bash
#############################################
## Name          : apt-upgrade.sh
## Version       : 1.0
## Date          : 2012-06-01
## Author        : LHammonds
## Purpose       : Keep system updated (rather than use unattended-upgrades)
## Compatibility : Verified on Ubuntu Server 12.04 LTS
## Requirements  : Sendemail, run as root
## Run Frequency : Recommend once per day.
## Parameters    : None
## Exit Codes    :
##    0 = Success
##    1 = ERROR: Lock file detected.
##    2 = ERROR: Not run as root user.
##    4 = ERROR: Aptitude update Error.
##    8 = ERROR: Aptitude safe-upgrade Error.
##   16 = ERROR: Aptitude autoclean Error.
################ CHANGE LOG #################
## DATE       WHO WHAT WAS CHANGED
## ---------- --- ----------------------------
## 2012-06-01 LTH Created script.
#############################################

## Import standard variables and functions. ##
source /var/scripts/common/standard.conf

## Define local variables.
LOGFILE="${LOGDIR}/apt-upgrade.log"
LOCKFILE="${TEMPDIR}/apt-upgrade.lock"
ErrorFlag=0
ReturnCode=0
APTCMD="$(which aptitude)"

#######################################
##            FUNCTIONS              ##
#######################################

function f_cleanup()
{
  if [ -f ${LOCKFILE} ];then
    ## Remove lock file so subsequent jobs can run.
    rm ${LOCKFILE} 1>/dev/null 2>&1
  fi
  exit ${ErrorFlag}
}

#######################################
##           MAIN PROGRAM            ##
#######################################

if [ -f ${LOCKFILE} ]; then
  # Lock file detected.  Abort script.
  echo "** Script aborted **"
  echo "This script tried to run but detected the lock file: ${LOCKFILE}"
  echo "Please check to make sure the file does not remain when check space is not actually running."
  f_sendmail "ERROR: Script aborted" "This script tried to run but detected the lock file: ${LOCKFILE}\n\nPlease check to make sure the file does not remain when check space is not actually running.\n\nIf you find that the script is not running/hung, you can remove it by typing 'rm ${LOCKFILE}'"
  ErrorFlag=1
  f_cleanup
else
  echo "`date +%Y-%m-%d_%H:%M:%S` ${SCRIPTNAME}" > ${LOCKFILE}
fi

## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo -e "ERROR: Root user required to run this script.\n"
  ErrorFlag=2
  f_cleanup
fi

echo "`date +%Y-%m-%d_%H:%M:%S` - Begin script." >> ${LOGFILE}
echo "`date +%Y-%m-%d_%H:%M:%S` --- Aptitude Update" >> ${LOGFILE}
${APTCMD} update > /dev/null 2>&1
ReturnCode=$?
if [[ "${ReturnCode}" -gt 0 ]]; then
  ErrorFlag=4
  f_cleanup
fi
echo "`date +%Y-%m-%d_%H:%M:%S` --- Aptitude Safe-Upgrade" >> ${LOGFILE}
echo "--------------------------------------------------" >> ${LOGFILE}
${APTCMD} safe-upgrade --assume-yes --target-release `lsb_release -cs`-security >> ${LOGFILE} 2>&1
ReturnCode=$?
if [[ "${ReturnCode}" -gt 0 ]]; then
  ErrorFlag=8
  f_cleanup
fi
echo "--------------------------------------------------" >> ${LOGFILE}
echo "`date +%Y-%m-%d_%H:%M:%S` --- Aptitude Autoclean" >> ${LOGFILE}
echo "--------------------------------------------------" >> ${LOGFILE}
${APTCMD} autoclean >> ${LOGFILE} 2>&1
ReturnCode=$?
if [[ "${ReturnCode}" -gt 0 ]]; then
  ErrorFlag=16
  f_cleanup
fi
echo "--------------------------------------------------" >> ${LOGFILE}
echo "`date +%Y-%m-%d_%H:%M:%S` - End script." >> ${LOGFILE}

## Perform cleanup routine.
f_cleanup

```

Here is the typical output:

/var/log/apt-upgrade.log
```

2012-06-01_09:31:19 - Begin script.
2012-06-01_09:31:19 --- Aptitude Update
2012-06-01_09:32:01 --- Aptitude Safe-Upgrade
--------------------------------------------------
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
--------------------------------------------------
2012-06-01_09:32:03 --- Aptitude Autoclean
--------------------------------------------------
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Freed 0 B of disk space
--------------------------------------------------
2012-06-01_09:32:04 - End script.
2012-06-02_03:00:01 - Begin script.
2012-06-02_03:00:01 --- Aptitude Update
2012-06-02_03:00:26 --- Aptitude Safe-Upgrade
--------------------------------------------------
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
The following packages will be upgraded:
  grub-common grub-pc grub-pc-bin grub2-common libcups2 libgcrypt11
6 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,611 kB of archives. After unpacking 59.4 kB will be freed.
Writing extended state information...
Get: 1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgcrypt11 amd64 1.5.0-3ubuntu0.1 [280 kB]
Get: 2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libcups2 amd64 1.5.3-0ubuntu1 [171 kB]
Get: 3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-pc amd64 1.99-21ubuntu3.1 [140 kB]
Get: 4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-pc-bin amd64 1.99-21ubuntu3.1 [861 kB]
Get: 5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub2-common amd64 1.99-21ubuntu3.1 [94.3 kB]
Get: 6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Fetched 3,611 kB in 3s (941 kB/s)
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin:
(Reading database ... 61584 files and directories currently installed.)
Preparing to replace libgcrypt11 1.5.0-3 (using .../libgcrypt11_1.5.0-3ubuntu0.1_amd64.deb) ...
Unpacking replacement libgcrypt11 ...
Preparing to replace libcups2 1.5.2-9ubuntu1 (using .../libcups2_1.5.3-0ubuntu1_amd64.deb) ...
Unpacking replacement libcups2 ...
Preparing to replace grub-pc 1.99-21ubuntu3 (using .../grub-pc_1.99-21ubuntu3.1_amd64.deb) ...
Unpacking replacement grub-pc ...
Preparing to replace grub-pc-bin 1.99-21ubuntu3 (using .../grub-pc-bin_1.99-21ubuntu3.1_amd64.deb) ...
Unpacking replacement grub-pc-bin ...
Preparing to replace grub2-common 1.99-21ubuntu3 (using .../grub2-common_1.99-21ubuntu3.1_amd64.deb) ...
Unpacking replacement grub2-common ...
Preparing to replace grub-common 1.99-21ubuntu3 (using .../grub-common_1.99-21ubuntu3.1_amd64.deb) ...
Unpacking replacement grub-common ...
Processing triggers for man-db ...
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Setting up libgcrypt11 (1.5.0-3ubuntu0.1) ...
Setting up libcups2 (1.5.3-0ubuntu1) ...
Setting up grub-common (1.99-21ubuntu3.1) ...
Installing new version of config file /etc/grub.d/10_linux ...
Setting up grub2-common (1.99-21ubuntu3.1) ...
Setting up grub-pc-bin (1.99-21ubuntu3.1) ...
Setting up grub-pc (1.99-21ubuntu3.1) ...
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /memtest86+.bin
done
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
ldconfig deferred processing now taking place
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
--------------------------------------------------
2012-06-02_03:00:43 --- Aptitude Autoclean
--------------------------------------------------
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Freed 0 B of disk space
--------------------------------------------------
2012-06-02_03:00:44 - End script.

```

---

### Post by fubofo on 2012-06-08
Wow, just wow!

Thanks very much for covering all this.
I have learned quite a bit from reading this thread alone.

Do you have list type of information saved on your own site anywhere or any more fully-informative type guides?

---

### Post by Skyflyer4life on 2012-06-08
Just incredible!  So much information here... I could spend just a week reading through everything here and trying to soak it all in!

THANK YOU FOR ALL YOU HARD WORK!

---

### Post by LHammonds on 2012-06-18
> **fubofo said:**
> Do you have list type of information saved on your own site anywhere or any more fully-informative type guides?
I do have a site where I have a ton of tutorials, but they are not related to Linux. ;)  The ones related to Linux are in my sig.

--------------

Document revised using the **sudo su** method to temporarily gain root-level access rather than setting a password on the root account.

The next change will be the setup of the operating system to be  generalized a bit and pulled into a different document and then referred  to rather than trying to update OS-specific changes in all my different  threads.  :smile:

**EDIT:** Here is [my website]("http://hammondslegacy.com/forum/index.php").  You can find the tutorial section under Miscellaneous.

LHammonds

---

### Post by fubofo on 2012-06-18
Cheers LHammonds, this is indeed invaluable info. Also, I NEVER heard of Nagios before....seems like a fantastic monitoring tool.

What is your site (Linux or not)?
*maybe you should consider making some Linux tutorials*

---

### Post by lightxx on 2012-07-13
awesome write-up!!!

thank you so much!

---

### Post by LHammonds on 2012-07-17
I can no longer edit this thread...therefor, I have moved the thread (and updates) to my own forum. Once I have all my documents settled down, I will see about getting help converting it to the wiki.

[My Notes for Installing MediaWiki on Ubuntu Server 12.04 LTS](http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=192) @ HammondsLegacy.com

 
> **fubofo said:**
> Cheers LHammonds, this is indeed invaluable info. Also, I NEVER heard of Nagios before....seems like a fantastic monitoring tool.

What is your site (Linux or not)?
*maybe you should consider making some Linux tutorials*That's what I'm doing. hehehe.

 
> **lightxx said:**
> awesome write-up!!!
 
thank you so much!
Thanks.

---

