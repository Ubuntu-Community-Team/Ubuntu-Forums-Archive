---
title: "My Notes for Installing MySQL on Ubuntu Server 12.04 LTS"
date: 2012-05-20
forum: Server Platforms
---

### Post by LHammonds on 2012-05-20
Greetings and salutations,

I hope this thread will be helpful to those who follow in my foot steps as well as getting any advice based on what I have done / documented.

[SIZE=5]High-level overview[/SIZE]

This thread will cover installation of a dedicated Ubuntu server and MySQL database.  The server will be installed inside a virtual machine vSphere 4.1 running on ESXi 4.1 servers.  I will also supply notes for doing the same thing for VirtualBox 4.1.14 on a Windows 7 PC.  Toward the end, I will document how I migrate the data from an older MySQL server to the new one.  Although there are some VMware-specific and VirtualBox-specific steps, they are very few and the majority of this documentation will work for other Virtual Machines or even directly installed onto a physical machine (e.g. bare-metal install).  Please excuse any ignorance on my part since I am fairly new to Linux...if you have any advice on doing things better, please let me know.  I love feedback and learning better ways of doing things!

This thread will also cover some custom scripts to help automate tasks such as backing up, automatically growing the file system when free space is low, etc.

[SIZE=5]Tools utilized in this process[/SIZE]


[LIST]
[*][Ubuntu Server]("http://www.ubuntu.com/download/ubuntu/download") 12.04 LTS, 64-bit
[*]MySQL 5.5.22
[*][Portable PuTTY]("http://portableapps.com/apps/internet/putty_portable") 0.62
[*][VMware vSphere]("http://www.vmware.com/products/vsphere/overview.html") 4.1.0
[*][VirtualBox]("http://www.virtualbox.org/") 4.1.14
[/LIST]

[SIZE=5]Helpful links[/SIZE]

The list below are sources of information that helped me configure this system as well as some places that might be helpful to me later on as this process continues.

[LIST]
[*][Ubuntu Documentation]("https://help.ubuntu.com")
[*][Ubuntu Firewall Basics]("https://help.ubuntu.com/community/IptablesHowTo#Disabling%20the%20firewall")
[*][Ubuntu AppArmor Basics]("https://help.ubuntu.com/community/AppArmor#Disable%20AppArmor%20framework")
[/LIST]

[SIZE=5]Assumptions[/SIZE]

This documentation will need to make use of some very-specific information that will most-likely be different for each person / location.  And as such, I will note some of these in this section.  They will be highlighted in red throughout the document as a reminder that you should plug-in your own value rather than actually using my "place-holder" value.

Under no circumstance should you use the actual values I list below.  They are place-holders for the real thing.  This is just a checklist template you need to have answered before you start the install process.

Wherever you see [COLOR=red]RED[/COLOR] in this document, you need to substitute it for what your company uses.  Use the list below as a template you need to have answered before you continue.


[LIST]
[*]Ubuntu Server name: [COLOR=red]srv-mysql[/COLOR]
[*]Internet domain: [COLOR=red]mydomain.com[/COLOR]
[*]Ubuntu Server IP address: [COLOR=red]192.168.107.27[/COLOR]
[*]Ubuntu Server IP subnet mask: [COLOR=red]255.255.255.0[/COLOR]
[*]Ubuntu Server IP gateway: [COLOR=red]192.168.107.1[/COLOR]
[*]Internal DNS Server 1: [COLOR=red]192.168.107.212[/COLOR]
[*]Internal DNS Server 2: [COLOR=red]192.168.107.213[/COLOR]
[*]External DNS Server 1: [COLOR=red]8.8.8.4[/COLOR]
[*]External DNS Server 2: [COLOR=red]8.8.8.5[/COLOR]
[*]Ubuntu Admin ID: [COLOR=red]administrator[/COLOR]
[*]Ubuntu Admin Password: [COLOR=red]myadminpass[/COLOR]
[*]Email Server (remote): [COLOR=red]192.168.107.25[/COLOR]
[*]MySQL root Password: [COLOR=red]mysqlrootpass[/COLOR]
[*]Windows Share ID: [COLOR=red]mysqlshare[/COLOR]
[*]Windows Share Password: [COLOR=red]mysqlsharepass[/COLOR]
[/LIST]

I also assume the reader knows how to use the VI editor.  If not, you will need to [beef up your skill set]("http://www.eng.hawaii.edu/Tutor/vi.html") or use a different editor in place of it.

---

### Post by LHammonds on 2012-05-20
[SIZE=5]Analysis and Design[/SIZE]

The Ubuntu Server Long-Term Support (LTS) is free but we have the option of buy support and that is the main reason this server was selected.

The largest decision over the configuration of Ubuntu seems to be how the hard drive space is sliced up (partitioned).  I lot of my time was spent researching and learning the various options when it comes to the design layout of the storage.

I like to make use of a design that allows for dynamic growth and fine-tuning if need be.  I also do not like being caught offguard with a scenario where space is filled up with no immediate option other than deleting files.  Long-term life and growth of the system as well as budgeting concerns have to be taken into consideration.

I like to contain the root volume to mainly just static data that won't grow much and push the other folders that are dynamic into their own volumes.  In case you don't know, filling up the root volume on a *nix system is a very bad thing and should be avoided at all costs.  I also want to configure it where the file systems are not taking up 100% of the logical volume.  This will allow me (through automated scripts) to grow the file system as needed and give me some time to add more drives if necessary or shrink other volumes to get more space.

Here are my thoughts on how to slice up the space.


[LIST]
[*]**Boot** - This will remain static in size.  It is also the only space residing outside the Logical Volume Manager (LVM)
[*]**Root volume** - Operating system and everything else which should remain fairly static.
[*]**Swap volume** - This will remain static in size.  However, if amount of RAM is adjusted, this should be adjusted as well.
[*]**var volume** - This is the database/log storage and will continue to grow over time.
[*]**Backup volume** - This will contain a local backup of the databases.  So space needs to be around double /var.
[*]**Tmp volume** - This location will be used for temporary storage.  Size should be adjusted to match however it is being used.
[*]**Offsite Storage** - This will be handled elsewhere but will be mounted on this server.
[/LIST]

My estimated database store will be about 2 GB.  However, we will start this server off with a lower number.  We will then pretend some event happened such as a popular content site which causes quick growth of the database.  This will increase our storage needs and we will go through adjusting the entire system to accommodate a larger storage capacity.  This will be a good exercise / documentation for what will eventually need to be done later to handle growth.

To get a good idea of the initial hard drive layout and to understand the process better, here is a graphical representation of the initial design for the server:

[IMG]http://tinyurl.com/6r336ct[/IMG]

These numbers will be used for the initial build of the system:

boot = 200 MB
root = 4 GB
swap = 4 GB
var = 1 GB
tmp = 1 GB
backup = 2 GB

NOTE: When the logical volumes and file systems are initially created, they consume the maximum amount of space allocated so that the logical volume size = file system size.  These partition sizes are artificially small for that reason.  These will be later modified so that the logical volume will be larger than the file system so that the file system has room to expand when needed.

Important info:
 - The /tmp folder is strictly temporary.  Each time the server reboots, this folder is deleted and re-created.
 - The /backup folder will retain the most recent backup and is considered the "local" copy of the backup.

[SIZE=5]VMware Virtual Machine Settings[/SIZE]

Virtual Manager: VMware vSphere Client 4.1
Virtual Host: VMware ESXi Server 4.1


[LIST]
[*]Configuration: Custom
[*]Name: srv-mysql
[*]Datastore: DS3400-LUN0
[*]Virtual Machine Version: 7
[*]Guest Operating System: Linux, Version: Ubuntu Linux (64-bit)
[*]Number of virtual processors: 1
[*]Memory Size: 2048 MB
[*]Number of NICs: 1
[*]NIC 1: VM Network
[*]Adapter: E1000, Connect at Power On: Checked
[*]SCSI controller: LSI Logic Parallel
[*]Select a Disk: Create a new virtual disk
[*]Create a Disk: 12 GB, No thin provisioning, No cluster features, Store with the virtual machine
[*]Advanced Options: Virtual Device Node = SCSI (0:0)
[*]Remove Floppy Drive
[*]Mount CD/DVD Drive to Ubuntu ISO (ubuntu-12.04-server-amd64.iso). Make sure CD/DVD is set to **Connect at power on**
[*]Set boot options to Force BIOS Setup so you can set CDROM to boot before the Hard Disk
[/LIST]

[SIZE=5]VirtualBox Virtual Machine Settings[/SIZE]

Virtual Manager: Oracle VirtualBox 4.1.14
Virtual Host: Windows 7 Ultimate with SP1 (64-bit)


[LIST]
[*]Name: srv-mysql
[*]Operating System: Linux
[*]Version: Ubuntu (64 bit)
[*]Memory: 2048 MB
[*]Check - Start-up Disk
 - Create new hard disk
 - VMDK
 - Dynamically allocated
 - Size: 12 GB
[*]Select srv-mysql and click Settings (CTRL+S)
 - System, Processor, Enable PAE/NX
 - Network, Attached to: Bridged Adapter, Advanced, Adapter Type: Intel PRO/1000 MT Server
 - Storage, IDE Controller, Choose a virtual CD/DVD disk file, ubuntu-12.04-server-amd64.iso
[/LIST]

[SIZE=5]Install PuTTY[/SIZE]

The 1st time I installed Ubuntu, I used the console for everything but it was painfully slow to view man (manual) pages and navigating in VI (text editor).  However, I found out that PuTTY is a far better solution for your Ubuntu console because it handles the screen draws much faster and allows for scrolling and copying text.

Download the portable edition and run the install...except it doesn't really "install" like a normal program, it simply extracts to a specified folder and will run from that folder even if you put it on a USB stick and carry over to a new computer (requires no install to run and thus leaves a very small footprint on your system)


[LIST=1]
[*]Start PuTTY
[*]Type the following and click the Save button:
Host Name: [COLOR=Red]SRV-MySQL[/COLOR] (or the IP such as [COLOR=red]192.168.107.27[/COLOR])
Port: **22**
Connection type: **SSH**
Saved Sessions: **MySQL**
[*]Now all you have to do is double-click on the MySQL session and it will connect to your server (when online).
[/LIST]

---

### Post by LHammonds on 2012-05-20
[SIZE=5]Install Ubuntu Server[/SIZE]

NOTE: During the setup process throughout this entire document, most  commands will require "sudo" as a prefix. However, I will be using "sudo  su" to temporarily gain root privileges.

[LIST=1]
[*]Power on the Virtual Machine (VM)
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *English*
[*]Select *Install Ubuntu Server* [COLOR=green]{ENTER}[/COLOR]
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *English*
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *United States*
[*]Select **No** to not detect keyboard layout
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *English (US)*
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *English (US)*
[*]Type **[COLOR=red]srv-mysql[/COLOR]** [COLOR=green]{ENTER}[/COLOR] (this is your hostname)
[*]Type **[COLOR=red]Administrator[/COLOR]**, [COLOR=green]{ENTER}[/COLOR] for the full name
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept the default of the lowercase name of **[COLOR=red]administrator[/COLOR]**
[*]Type **[COLOR=red]myadminpass[/COLOR]**, [COLOR=green]{ENTER}[/COLOR], **[COLOR=red]myadminpass[/COLOR]**, [COLOR=green]{ENTER}[/COLOR]
[*]Select *No*, [COLOR=green]{ENTER}[/COLOR] to not encrypt your home directory
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept detected time zone (*America/Chicago*)
[*]Select *Manual* [COLOR=green]{ENTER}[/COLOR]
[*]Select *SCSI3 (0,0,0) (sda) - 12.9 GB VMware Virtual disk* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Yes* to create new empty partition table, [COLOR=green]{ENTER}[/COLOR]
[*]Select *pri/log 12.9 GB FREE SPACE* [COLOR=green]{ENTER}[/COLOR]
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
[*]Select */dev/sda free #1 (12684MB; FREE SPACE)*, [COLOR=green]{SPACEBAR}[/COLOR], [COLOR=green]{ENTER}[/COLOR]
[*]Select *Yes* to write change to disks and configure LVM, [COLOR=green]{ENTER}[/COLOR]
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR]
[*]Select *LVG (12679MB)* [COLOR=green]{ENTER}[/COLOR]
[*]Type **swap** [COLOR=green]{ENTER}[/COLOR]
[*]Type **4G** [COLOR=green]{ENTER}[/COLOR] (NOTE: This is double the amount of RAM)
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR]
[*]Select *LVG (8682MB)* [COLOR=green]{ENTER}[/COLOR]
[*]Type **bak** [COLOR=green]{ENTER}[/COLOR]
[*]Type **2G** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR]
[*]Select *LVG (6685MB)* [COLOR=green]{ENTER}[/COLOR]
[*]Type **var** [COLOR=green]{ENTER}[/COLOR]
[*]Type **1G** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR]
[*]Select *LVG (5687MB)* [COLOR=green]{ENTER}[/COLOR]
[*]Type **tmp** [COLOR=green]{ENTER}[/COLOR]
[*]Type **1G** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR]
[*]Select *LVG (4689MB)* [COLOR=green]{ENTER}[/COLOR]
[*]Type **root** [COLOR=green]{ENTER}[/COLOR]
[*]Type **4G** [COLOR=green]{ENTER}[/COLOR] (we will have a small amount leftover in LVG)
[*]Select *Finish* [COLOR=green]{ENTER}[/COLOR]
[*]Select *#1 4.0 GB* directly under *LVM VG LVG, LV swap*, [COLOR=green]{ENTER}[/COLOR]
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR]
[*]Select *swap area* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR]
[*]Select *#1 4.0 GB* directly under *LVM VG LVG, LV root*, [COLOR=green]{ENTER}[/COLOR]
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
[*]Select *#1 998.2 MB* directly under *LVM VG LVG, LV var*, [COLOR=green]{ENTER}[/COLOR]
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR]
[*]Select */var* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Label: none* [COLOR=green]{ENTER}[/COLOR]
[*]Type **mysql** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR]
[*]Select *#1 998.2 GB* directly under *LVM VG LVG, LV tmp*, [COLOR=green]{ENTER}[/COLOR]
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR]
[*]Select */tmp* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Label: **temp*** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR]
[*]Here is what the screen looks like at this point: [Partitions]("http://tinyurl.com/7c6rzgw")
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
[*]At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Type **vi /etc/network/interfaces** [COLOR=green]{ENTER}[/COLOR] and change the following: (We need to change the network interface card (NIC) from using DHCP to a static IP)
From:
```
iface eth0 inet dhcp
```To:
```
iface eth0 inet [B]static
address [COLOR=red]192.168.107.27[/COLOR]
netmask [COLOR=red]255.255.255.0[/COLOR]
gateway [COLOR=red]192.168.107.1[/COLOR]
network [COLOR=red]192.168.107[/COLOR].0
broadcast [COLOR=red]192.168.107[/COLOR].255
dns-nameservers [COLOR=red]192.168.107.212 192.168.107.213 8.8.8.4 8.8.8.5[/COLOR]
[/B]
```NOTE #1: You may need to manually remove the DHCP record (lease) associated to this Ubuntu server from your DHCP server so the correct IP can be found by other machines on the network.  This can be avoided by temporarily configuring the VM Network Adapter connection to be "Host Only Network" instead of "VM Network" so the server is isolated during setup...at least until you reach the testing of the static IP below.

NOTE #2: You might also need to manually add a HOST(A) record to your Windows DNS server (for [COLOR=red]srv-mysql.mydomain.com[/COLOR] and [COLOR=red]srv-mysql.work.mydomain.com[/COLOR])
[*]Restart the network by typing **/etc/init.d/networking restart**
[*]Sanity check!  Type **ifconfig** and make sure the settings are correct.  Then type **ping [www.google.com]("http://www.google.com")** or similar and see if ping works.
[*]Shutdown and power off the server by typing **shutdown -P now**
[*]At this point forward, you can use PuTTY to access the console rather than the console itself for better performance, ability to scroll, etc.
[*]In VM menu, select VM --> Snapshot --> Take Snapshot.  Give it a name like **STEP 1** and description of **Ubuntu Server 12.04 LTS, clean install, Static IP: [COLOR=red]192.168.107.27[/COLOR]** and click **OK**
[/LIST]


[SIZE=5]Software Configurations[/SIZE]


[LIST=1]
[*]Start the Ubuntu server and connect using PuTTY.
[*]At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]At the $ prompt, type **aptitude -y install vim-nox** for use instead of the built-in VI editor. [more info]("http://en.wikipedia.org/wiki/Vim_%28text_editor%29")
[*]At the $ prompt, type **aptitude -y install p7zip-full** to install 7-zip archive utility.
[*]At the $ prompt, type **aptitude -y install sendemail** to install a command-line email utility.
[*]Change the default shell from dash to bash.  Type **ls -l /bin/sh** to see that it points to /bin/dash.  Type **dpkg-reconfigure dash** and answer **No**.  Type **ls -l /bin/sh** and it should now be pointing to /bin/bash
[*]Remove AppArmor to avoid problems by typing the following:
```
[B]/etc/init.d/apparmor stop
/etc/init.d/apparmor teardown
update-rc.d -f apparmor remove
aptitude remove apparmor apparmor-utils[/B]
```
[*]Type **vi /etc/hosts** and add your email server:
```
**[COLOR=red]192.168.107.25[/COLOR]    srv-mail**
```
[*]Test the ability to send email by typing:
```
**sendemail -f root@myserver -t MyTargetAddress@MyDomain.com -u "This is the Subject" -m "This is the body of the email" -s srv-mail:25**
```
[*]TIP: Over time, upgrades to the kernel can start taking up space in /usr/src.  I found this out because my root partition started to get full.  When I typed this command: **du -sh /usr/src/*** I found out there was over a gigabyte of old files.  To cleanly clear out old an unused headers, type the following commands:
```
[B]
apt-get -f install
apt-get autoremove
[/B]
```
[*]Reboot the server by typing **reboot**
[/LIST]


[SIZE=5]VMware Tools Installation[/SIZE]

If you are installing under VMware like me, be sure to install the tools to insure maximum performance in a virtual environment.


[LIST=1]
[*]In the VM toolbar for the VM, click Guest, Install VMware Tools
[*]At the Ubuntu prompt, type the following:
```
[B]
mkdir /mnt/cdrom
mount /dev/cdrom /mnt/cdrom
ls /mnt/cdrom[/B]       ( make sure you see a file such as VMwareTools-8.3.2-257589.tar.gz)[B]
tar zxvf /mnt/cdrom/VMwareTools* -C /tmp/
cd /tmp/vmware-tools-distrib/
./vmware-install.pl -d
reboot
[/B]
```
[/LIST]


[SIZE=5]VMware Tools Upgrade[/SIZE]

Before you can install the updated version, you must 1st remove the currently installed version.

To determine which version is installed, run this command:
```
[B]
grep buildNr /usr/bin/vmware-config-tools.pl
[/B]
```
[LIST=1]
[*]Connect to the server using PuTTY.
[*]At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Type the following to remove VMware Tools:
```
[B]
vmware-uninstall-tools.pl
[/B]
```
[*]Now install the new VMware Tools as described in the install section above.
[/LIST]



[SIZE=5]VirtualBox Guest Additions - Installation[/SIZE]

If you are installing under VirtualBox, be sure to install the Guest Additions to insure maximum performance in a virtual environmnet.


[LIST=1]
[*]At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]You need to perform the following commands to fulfill the prerequisites:
```
[B]
aptitude update
aptitude safe-upgrade
aptitude install dkms
reboot
[/B]
```
[*]At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]From the VirtualBox menu, click Devices, Install Guest Additions
[*]At the console, type the following:
```
[B]
mkdir -p /mnt/cdrom
mount /dev/cdrom /mnt/cdrom
/mnt/cdrom/VBoxLinuxAdditions.run
[/B]
```
[*]NOTE: The X Windows System drivers will fail to load because this is a headless server with no GUI (which is OK)
[*]To see if the services are running, type **/etc/init.d/vboxadd-service status** or **service vboxadd-service status**
[/LIST]


[SIZE=5]VirtualBox Guest Additions - Upgrading[/SIZE]

If you upgraded VirtualBox on your host machine, you also need to upgrade the Guest Additions on all your guest operating systems.

Then mount the CDROM and run the installer just like the above.  Reboot after it is upgraded.


[LIST=1]
[*]At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR]) and then type **su** and the root password ([COLOR=red]myrootpass[/COLOR])
[*]From the VirtualBox menu, click Devices, Install Guest Additions
[*]At the console, type the following:
```
[B]
mount /dev/cdrom /mnt/cdrom
/mnt/cdrom/VBoxLinuxAdditions.run
reboot
[/B]
```
[/LIST]


[SIZE=5]VirtualBox Guest Additions - Uninstallation[/SIZE]

If you are about to migrate from a VirtualBox host to something like a VMware host, you will need to uninstall VirtualBox's Guest Additions.


[LIST=1]
[*]At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR]) and then type **su** and the root password ([COLOR=red]myrootpass[/COLOR])
[*]Type the following:
```
[B]
cd /opt/VBox*
./uninstall.sh
[/B]
```
[/LIST]

---

### Post by LHammonds on 2012-05-20
[SIZE="5"]Volume / Disk Management[/SIZE]

At this point, let's assume something has changed and we need additional storage (e.g. insanely popular site with more people adding content).  The initial setup left us with no room to expand our file system!  We need to change this.

For this scenario, we are expecting storage space to require 1 GB.  If they need 1 GB for storage, let's double that amount for the actual size.  Here is the planned adjustments for each file system:

var = 2 GB (double the expected storage)
tmp = 2 GB ("should" be plenty of room for temp usage)
backup = 4 GB (double the var size)

In the analysis and design section, we wanted to have some file systems smaller than the logical volume on which they sit.  This will allow us to allocate additional space when needed.  However, when we created the volumes, Ubuntu automatically expanded the file systems to the maximum size of the volume.  Normally, this is OK...but we want a system that will allow growth when needed and ensure that we will have time to add additional hard drives BEFORE they are needed which will keep us from being stuck between a rock and a hard place!  You do not want to lose a job because somebody did not estimate growth correctly or the budget did not allow for large capacity when the system first rolled out.

This design calls for **/backup**, **/var** and **/tmp** file systems to be smaller than the maximum space available for the logical volume in which they reside in.

So, let's make the logical volumes double the file systems.  This means that we will need an additional 12 GB of storage {(8 + 4 + 4 ) - (2 + 1 + 1}.  If we add two drives that are 6 GB each, that will be just enough to cover our needs. (NOTE: This was an arbitrary number because I wanted to show you how to add 2 drives to the system)

Here is a graphical representation of what needs to be accomplished:

[IMG]http://tinyurl.com/bm2km45[/IMG]

If we were to type **df -h** right now, we should see something like this:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  3.8G  912M  2.7G  26% /
udev                  237M  4.0K  237M   1% /dev
tmpfs                  99M  232K   99M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  246M     0  246M   0% /run/shm
/dev/sda1             179M   25M  145M  15% /boot
/dev/mapper/LVG-bak   1.9G   61M  1.8G   4% /backup
/dev/mapper/LVG-var   950M  274M  629M  31% /var
/dev/mapper/LVG-tmp   950M   30M  873M   4% /tmp

```

Since I am running VMware, adding additional space is a snap.  However, I will add it in such a way that Ubuntu will see 2 drives added to the system just as if we were to add 2 physical drives to a physical server.

[LIST=1]
[*]Shutdown and power off the server by typing **shutdown -P now**
[*]In the vSphere client, right-click the Virtual Machine and choose *Edit Settings*.
[*]On the hardware tab, click the *Add* button and select Hard Disk.  Click Next, choose "Create a new virtual disk", click Next, set the size to **6** GB, click Next, Next, Finish.
[*]Add another **6** GB disk using the same steps above and click OK to close the settings and allow VMware to process the changes.
[/LIST]

Collect information about the newly added drives.

[LIST=1]
[*]Start the Ubuntu server and connect using PuTTY.
[*]At the login prompt, login with your administrator account ([COLOR="red"]administrator[/COLOR] / [COLOR="red"]myadminpass[/color]) and then type **su** and the root password ([COLOR="red"]myrootpass[/COLOR])
[*]Type **pvdisplay** which should show something similar to this:
```

  --- Physical volume ---
  [COLOR="red"]PV Name               /dev/sda5
  VG Name               LVG[/COLOR]
  PV Size               11.81 GiB / not usable 3.00 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              3023
  Free PE               165
  Allocated PE          2858
  PV UUID               s967ty-gx1A-HLfE-0SMq-0Y8t-WbGT-SOaftd

```
The important bits of info here are the PV Name and VG Name for our existing configuration.
[*]Type **fdisk -l** which should show something similar to this (however I abbreviated it to show just the important parts):
```

Disk /dev/sda: 12.9 GB, 12884901888 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      391167      194560   83  Linux
/dev/sda2          393214    25163775    12385281    5  Extended
/dev/sda5          393216    25163775    12385280   8e  Linux LVM

Disk [COLOR="red"]/dev/sdb[/COLOR]: 6442 MB, 6442450944 bytes
Disk /dev/sdb doesn't contain a valid partition table
Disk [COLOR="red"]/dev/sdc[/COLOR]: 6442 MB, 6442450944 bytes
Disk /dev/sdc doesn't contain a valid partition table

```
The important bits of info here are the device paths for the new drives which I highlighted in red.
[/LIST]

Prepare the first drive (/dev/sdb) to be used by the LVM

Type the following:
```
**fdisk /dev/sdb**
**n** (Create New Partition)
**p** (Primary Partition)
**1** (Partition Number)
[COLOR="green"]{ENTER}[/COLOR] (use default for first cylinder)
[COLOR="green"]{ENTER}[/COLOR] (use default for last cylinder)
**t** (Change partition type)
**8e** (Set to Linux LVM)
**p** (Preview how the drive will look)
**w** (Write changes)
```

Prepare the second drive (/dev/sdc) to be used by the LVM

Do the exact same steps as above but start with **fdisk /dev/sdc**

Create physical volumes using the new drives

If we type **fdisk -l**, we now see /dev/sdb1 and /dev/sdc1 which are Linux LVM partitions.

Type the following to create physical volumes:
```
[B]pvcreate /dev/sdb1
pvcreate /dev/sdc1[/B]
```

Now add the physical volumes to the volume group (LVG) by typing the following:
```
[B]vgextend LVG /dev/sdb1
vgextend LVG /dev/sdc1[/B]
```

Now that the space of both drives have been added to the logical volume group called LVG, we can now allocate that space to grow the logical volumes.

To get a list of volume paths to use in the next commands, type **lvscan** to show your current volumes and their sizes.

Type the following to grow each volume by a specified amount (the number after the plus sign):
```
[B]lvextend -L+3G /dev/LVG/var
lvextend -L+3G /dev/LVG/tmp
lvextend -L+6G /dev/LVG/bak[/B]
```

or you can specify the exact size by excluding the plus sign and specifying the end-result size you want:
```
[B]lvextend -L4G /dev/LVG/var
lvextend -L4G /dev/LVG/tmp
lvextend -L8G /dev/LVG/bak[/B]
```

To see the new sizes, type **lvscan**

The last thing to do now is the actual growth of the file systems.  We want to grow the existing file systems but only to a certain amount so we do not take up all the space in the volume...we want room to grow in the future so we have time to order and install new drives when needed.
```
[B]resize2fs /dev/LVG/var 2G
resize2fs /dev/LVG/tmp 2G
resize2fs /dev/LVG/bak 4G[/B]
```

If we need to increase space in **/var** at a later point, we can issue the following command without any downtime (we will automate this in a nifty script later):

```
**resize2fs /dev/LVG/var 2560MB**
```

We could continue to increase this particular file system all the way until we reach the limit of the volume which is 4 GB at the moment.

Remember, **df -h** will tell you the size of the file system and **lvscan** will tell you the size of the volumes where the file systems live in.

If we were to type **df -h** right now, we should see something like this:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  3.8G  912M  2.7G  26% /
udev                  237M  4.0K  237M   1% /dev
tmpfs                  99M  248K   99M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  246M     0  246M   0% /run/shm
/dev/sda1             179M   25M  145M  15% /boot
/dev/mapper/LVG-bak   4.0G   64M  3.8G   2% /backup
/dev/mapper/LVG-var   2.0G  275M  1.7G  15% /var
/dev/mapper/LVG-tmp   2.0G   31M  1.9G   2% /tmp

```

TIP: If you want to see everything in a specific block size, such as everything showing up in megabytes, you can use **df --block-size m**

---

### Post by LHammonds on 2012-05-20
[SIZE="5"]Configure Ubuntu for File Sharing[/SIZE]

This file sharing section is optional but can be handy if you need to swap files between the Linux server and a Windows machine.

This documentation will utilize this share for passing pre-configured files (configs, scripts, etc.) to make it faster/easier during installation.


[LIST=1]
[*]Start the Ubuntu server and connect using PuTTY.
[*]At the login prompt, login with your administrator account ([COLOR="red"]administrator[/COLOR] / [COLOR="red"]myadminpass[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Install Samba by typing **aptitude -y install samba smbfs** (NOTE: To share a folder with Windows, you just need the **samba** package, to connect to a Windows share, you need both **samba** and **smbfs**)
[*]Type the following commands:
```
[B]
cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
mkdir -p /srv/samba/share
chown nobody:nogroup /srv/samba/share/
chmod 0777 /srv/samba/share
[/B]
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
[*]You should now be able to click Start --> Run and type **\\[COLOR="red"]srv-mysql[/COLOR]** or **\\[COLOR="red"]192.168.107.27[/COLOR]** [COLOR="green"]{ENTER}[/COLOR] and see an explorer window with a *Share* folder.  Drag-n-drop a file into the *Share* folder.  If it worked, it will not display an error message and you should be able to view it from the server by typing **ls -l /srv/samba/share/**
[*]Shutdown and power off the server by typing **shutdown -P now**
[*]In VM menu, select VM --> Snapshot --> Take Snapshot.  Give it a name like **STEP 2** and description of **Ubuntu Server 12.04 LTS, File share configured, Static IP: [COLOR="red"]192.168.107.27[/COLOR]**.  The Snapshot Manager should now have a nice hierarchy of snapshots (STEP 1 --> STEP 2 --> You are here)
[/LIST]

[SIZE="5"]Configure Windows Remote Mount Point[/SIZE]

The remote offsite location is a Windows 2008 server that has a vast amount of hard drive space and currently backs up other servers.

Part of the backup process will be to write files to a mounted folder to a Windows share.

First, let's document the variables for this solution below and highlight them in red throughout the document for easy identification.

The values below are merely samples which you need to change in order to match your environment:

Windows AD Domain Name: [COLOR="red"]work[/COLOR]
Windows Server Name: [COLOR="red"]SRV-Backup[/COLOR]
Windows Server IP: [COLOR="red"]192.168.107.218[/COLOR]
Windows Share Name: mysql
Windows Physical Share Location: [COLOR="red"]D:\MySQL\[/COLOR]
Windows Share ID: [COLOR="red"]mysqlshare[/COLOR]
Windows Share Password: [COLOR="red"]mysqlpassword[/COLOR]

[SIZE=4]Create a share on a Windows 2008 server[/SIZE]


[LIST=1]
[*]In Windows Explorer, right-click on the [COLOR="red"]*D:\MySQL*[/COLOR] folder and select **Properties**
[*]Click the **Sharing** tab
[*]Click the **Advanced Sharing** button
[*]Place a checkmark beside **Share this folder**
[*]Change the Share name to **mysql**
[*]Set the Comment to **MySQL Backup**
[*]Click the **Permissions** button
[*]Select **Everyone** and click the **Remove** button
[*]Click the **Add** button
[*]Type in your MySQL share account: [COLOR="red"]**work\mysqlshare**[/COLOR] and click the **Check Names** button, click **OK**
[*]Place a checkmark for **Allow Full Control** and click **OK**, click **OK**, click **OK**
[*]Create a text file in the root of the shared folder called "online.txt" and you might want to add some text inside saying to never delete this file because it is used (will be) by a MySQL backup script.  Probably a good idea to make it read-only as well.  Example: [B]D:\MySQL\online.txt[B]
[/LIST]

[SIZE=4]Create an NFS mount to the Windows 2008 server[/SIZE]

Connecting to a Windows share requires the **samba** and **smbfs** packages to be installed.  If you do not have them, type **aptitude -y install samba smbfs**


[LIST=1]
[*]At the login prompt, login with your administrator account ([COLOR="red"]administrator[/COLOR] / [COLOR="red"]myadminpass[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Type the following commands:
```
[B]
mkdir -p /mnt/backup
chown root:root /mnt/backup
chmod 0755 /mnt/backup
echo "This file is used to tell if the mount is active or not" > /mnt/backup/offline.txt
chown root:root /mnt/backup/offline.txt
chmod 0444 /mnt/backup/offline.txt
touch /etc/cifspw
chmod 0600 /etc/cifspw
echo -e "username=[COLOR="red"]work\\mysqlshare[/COLOR]\npassword=[COLOR="red"]mysqlpassword[/COLOR]" >> /etc/cifspw
[/B]
```
[*]Type **vi /etc/hosts** and add the following line anywhere in the file:
```
[B]
[COLOR="red"]192.168.107.218    srv-backup[/COLOR]
[/B]
```
[*]At this point, you might want to type **ping [COLOR="red"]srv-backup[/COLOR]** to make sure you typed the right IP address as well as seeing a good response.
[*]To mount this system for backups, type the following command:
```
[B]
mount -t cifs //srv-backup/mysql /mnt/backup --options nouser,rw,nofail,noatime,noexec,credentials=/etc/cifspw
[/B]
```
[*]To test it, type **cp /etc/hosts /mnt/backup/hosts.txt** and look on the Windows server and see if the file shows up.  Then type **rm /mnt/backup/hosts.txt** and verify that the file was deleted on the windows server.
[*]This would also be a good time to verify that you can see the "online.txt" file that will be used by the backup script. Type **ls -l /mnt/backup/*.txt**
[*]To dismount the windows share, type the following command:
```
[B]
umount /mnt/backup
[/B]
```
[/LIST]

The scripts will call a common mount and unmount function to connect to this share only when needed.

However, if you would rather have it mounted all the time (even after a reboot), do the following (but remember to not use the mount/umount functions in the scripts later):


[LIST=1]
[*]Type **vi /etc/fstab** and add the following line at the bottom of the file:
```

**//[COLOR="red"]srv-backup/mysql[/COLOR]    /mnt/backup    cifs nouser,rw,nofail,noatime,noexec,credentials=/etc/cifspw    0    0**

```
[*]Type **mount -a** and if it does not spew out any error messages, it will quietly mount the share.
[*]To test it, type **cp /etc/hosts /mnt/backup/hosts.txt** and look on the Windows server and see if the file shows up.  Then type **rm /mnt/backup/hosts.txt** and verify that the file was deleted on the windows server.
[*]If you need to unmount it, simply type **umount /mnt/backup** and it will remain unmounted until you reboot.  To make it permanent, you need to remove the line you added in the /etc/fstab file.
[/LIST]

---

### Post by LHammonds on 2012-05-20
[SIZE="5"]Install MySQL[/SIZE]


[LIST=1]
[*]Start the Ubuntu server and connect using PuTTY.
[*]At the login prompt, login with your administrator account ([COLOR="red"]administrator[/COLOR] / [COLOR="red"]myadminpass[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Install MySQL by typing **aptitude -y install mysql-server**
[*]Type your password for the MySQL "root" user account [COLOR="red"]**mysqlrootpass**[/COLOR][COLOR="green"]{ENTER}[/COLOR]
[*]Re-type the password again [COLOR="red"]**mysqlrootpass**[/COLOR][COLOR="green"]{ENTER}[/COLOR]
[*]When installation is completed, the MySQL service should automatically start
[*]Verify the service is running by typing either of the following two commands:
```
**service mysql status**
```
or
```
**netstat -tap | grep mysql**
```
[/LIST]

[SIZE="5"]Configure MySQL[/SIZE]


[LIST=1]
[*]Make a personal MySQL config file for the root user so the password is not required when running MySQL commands
```
[B]touch ~/my.cnf
chmod 0600 ~/my.cnf
vi ~/my.cnf[/B]
```
[*]Add the following lines to ~/my.cnf
```
[B][client]
password=[COLOR="red"]mysqlrootpass[/COLOR][/B]
```
[*]Edit the global mysql config file by typing **vi /etc/mysql/my.cnf**
[*]Comment-out the bind-address by adding a pound sign (#) at the beginning of the line:
```
**#bind-address = 127.0.0.1**
```
[*]Add the following line to the very bottom:
```
**!include ~/my.cnf**
```
[*]Restart the mysql service by typing **service mysql restart**
[*]See if the following command will work without prompting for a password: **mysqladmin status**
[*]If this did not work, it is possible you did not uninstall apparmor in an earlier step
[/LIST]


[SIZE="5"]Tighten Security[/SIZE]

MySQL comes with a script to tighten-down security for a production server.


[LIST=1]
[*]Connect to the server using PuTTY and at the login prompt, login with your administrator account ([COLOR="red"]administrator[/COLOR] / [COLOR="red"]myadminpass[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Type **mysql_secure_installation**
[*]Type the MySQL "root" password: [COLOR="red"]**mysqlrootpass**[/COLOR]
[*]Type **N** to skip changing the password
[*]Type **Y** to remove the anonymous user account
[*]Type **Y** to disallow remote root login
[*]Type **Y** to remove the test database
[*]Type **Y** to reload privilege tables
[/LIST]


[SIZE="5"]Relocate the Databases[/SIZE]

If you do not want to leave your databases in the default location (/var/lib/mysql), then you can following these steps to move them somewhere else.  In this example, we will move them to /opt/mysql


[LIST=1]
[*]At the login prompt, login with your administrator account ([COLOR="red"]administrator[/COLOR] / [COLOR="red"]myadminpass[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]At the console, type the following:
```
[B]mkdir -p /opt/mysql
chown mysql:mysql /opt/mysql
vi /etc/mysql/my.cnf[/B]
```
[*]Change the location where the databases by changing datadir from /var/lib/mysql to:
```
**datadir = opt/mysql**
```
[*]Type the following commands to move the database(s)
```
[B]service mysql stop
mv /var/lib/mysql/* /opt/mysql/.
service mysql start[/B]
```
[*]Verify the service is running by typing either of the following two commands:
```
**service mysql status**
```
or
```
**netstat -tap | grep mysql**
```
[/LIST]



[SIZE="5"]Reset lost root password[/SIZE]

If you ever find yourself in the position of not being able to login to your database with your root password, you will need to reset the password.  For example, phpmyadmin fails to change the password correctly and neither the old nor the new password works.

This procedure will require taking the database offline for a short time to schedule it appropriately.

In this example, we are going to set the password to [COLOR="red"]**mysqlrootpass**[/COLOR] but please do not actually use this exact password for your server.


[LIST=1]
[*]Connect to the server using PuTTY.
[*]Login with your administrator account.  At the $ prompt, temporarily grant yourself super user privilages by typing **sudo su**
[*]Shutdown the database service:
```
[B]
service mysql stop
[/B]
```
[*]Start MySQL in safe mode so that it does not try to authenticate users:
```
[B]
mysqld_safe --skip-grant-tables &
[/B]
```
[*]Connect to the MySQL server via the command-line utility (which should not ask for a password):
```
[B]
mysql -u root
[/B]
```
[*]Select the primary database and reset the password:
```
[B]
use mysql;
update user set password=PASSWORD("[COLOR="red"]**mysqlrootpass**[/COLOR]") where User='root';
flush privileges;
quit
[/B]
```
[*]Stop the MySQL service and restart it in the normal mode:
```
[B]
service mysql stop
service mysql start
[/B]
```
[*]Test out the new password by connecting with the command-line utility:
```
[B]
mysql -u root -p
quit
[/B]
```
[*]Update your **~/my.cnf** file with the current password.
[/LIST]

---

### Post by LHammonds on 2012-05-20
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

With a production and test servers on physically different machines, the "common" scripts folder can be custom-tailored for that environment and allow for minimal changes to a script when running on the test, QA or production server.  This is similar to "normalizing" a database.  If you have a variable, path or function that is duplicated in multiple scripts, consider pulling it out and placing it in the common folder.  If ever you need to change who receives the email reports, you only need to update a single script and all programs will use the new reference from that point on.

Most of my scripts will import a file called "standard.conf" from the common script folder.

/var/scripts/common/standard.conf (contents of the file on the **production** server)
```

## Global Variables ##
TEMPDIR="/tmp"
SHAREDIR="/srv/samba/share"
MYDOMAIN="[COLOR=red]mydomain.com[/COLOR]"
ADMINEMAIL="admin@${MYDOMAIN}"
REPORTEMAIL="[COLOR=red]lhammonds[/COLOR]@${MYDOMAIN}"
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
  mount -t cifs //srv-backup/mysql ${OFFSITEDIR} --options nouser,rw,nofail,noatime,noexec,credentials=/etc/cifspw
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
SHAREDIR="/srv/samba/share"
MYDOMAIN="[COLOR=red]mytestdomain.com[/COLOR]"
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

```setup-script-qa.sh
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

```setup-script-test.sh
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

### Post by LHammonds on 2012-05-20
[SIZE=5]Toggle Mount Script[/SIZE]

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
[SIZE=5]MySQL Backup Script[/SIZE]

This script is designed to perform a full backup of all databases while the server is online.  It actually does three kinds of backups.  First, it pulls all the databases into a single file which is good for restoring everything on new servers.  It then pulls by database to create database files and then it pulls each individual table into its own file which is easier to isolate individual items to restore if necessary.

My needs are not that great at the moment so I backup one time per day...which is handled by a crontab schedule covered later in this thread.

/var/scripts/prod/mysql-backup.sh
```

#!/bin/bash
#############################################
## Name          : mysql-backup.sh
## Version       : 1.1
## Date          : 2012-01-09
## Author        : LHammonds
## Purpose       : Complete backup of MySQL database.
## Compatibility : Verified on to work on:
##                  - Ubuntu Server 10.04 LTS - 12.04 LTS
##                  - MySQL 5.1.41 - 5.5.22
## Requirements  : p7zip-full (if ARCHIVEMETHOD=tar.7z), sendemail
## Run Frequency : Once per day after hours or as needed (will not shutdown service)
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
## 2011-12-19 LTH Created script.
## 2012-01-09 LTH Bugfix - f_PurgeOldestArchive
#############################################

## Import common variables and functions. ##
source /var/scripts/common/standard.conf

LOGFILE="${LOGDIR}/mysql-backup.log"
LOCKFILE="${TEMPDIR}/mysql-backup.lock"
TARGETDIR="${BACKUPDIR}/mysql"
OFFSITEBACKDIR="${OFFSITEDIR}/mysql"
ARCHIVEFILE="`date +%Y-%m-%d-%H-%M`_mysql-backup.${ARCHIVEMETHOD}"
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
  echo "`date +%Y-%m-%d_%H:%M:%S` - MySQL backup exit code: ${ERRORFLAG}" >> ${LOGFILE}

  if [ -f ${LOCKFILE} ];then
    ## Remove lock file so other backup jobs can run.
    rm ${LOCKFILE} 1>/dev/null 2>&1
  fi
  ## Email the result to the administrator.
  if [ ${ERRORFLAG} -eq 0 ]; then
    f_sendmail "MySQL Backup Success" "MySQL backup completed with no errors."
  else
    f_sendmail "MySQL Backup ERROR" "MySQL backup failed.  ERRORFLAG = ${ERRORFLAG}"
  fi
}

function f_emergencyexit()
{
  ## Purpose: Exit script as cleanly as possible.
  ## Parameter #1 = Error Code
  f_cleanup
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
  f_sendmail "MySQL Backup aborted - Lock File" "This script tried to run but detected the lock file: ${LOCKFILE}\n\nPlease check to make sure the file does not remain when this script is not actually running."
  exit 1
else
  ## Create the lock file to ensure only one script is running at a time.
  echo "`date +%Y-%m-%d_%H:%M:%S` ${SCRIPTNAME}" > ${LOCKFILE}
fi

echo "`date +%Y-%m-%d_%H:%M:%S` - MySQL Backup started." >> ${LOGFILE}

## If the 7-Zip archive method is specified, make sure the package is installed.
if [ "${ARCHIVEMETHOD}" = "tar.7z" ]; then
  if [ ! -f "/usr/bin/7za" ]; then
    ## Required package (7-Zip) not installed.
    echo "`date +%Y-%m-%d_%H:%M:%S` - CRITICAL ERROR: 7-Zip package not installed.  Please install by typing 'aptitude -y install p7zip-full'" >> ${LOGFILE}
    ERRORFLAG=1
    f_emergencyexit ${ERRORFLAG}
  fi
fi

echo "`date +%Y-%m-%d_%H:%M:%S` --- Partition status:" >> ${LOGFILE}
df -h >> ${LOGFILE}

## Document the current uptime.
${MYSQL} -e status | grep -i uptime >> ${LOGFILE}

StartTime="$(date +%s)"

echo "`date +%Y-%m-%d_%H:%M:%S` --- Space consumed in ${MYSQLDIR} = `du -sh ${MYSQLDIR} | awk '{ print $1 }'`" >> ${LOGFILE}

## Backup all databases.
${MYSQLDUMP} --skip-lock-tables --all-databases > ${TARGETDIR}/mysql-all.sql

## Loop through every database.
DATABASES=$(echo "show databases;"|mysql --skip-column-names)
for DATABASE in ${DATABASES}
do
  if (( "${DATABASE}" != "information_schema" )) && (( "${DATABASE}" != "performance_schema" )); then
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
  fi
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

echo "`date +%Y-%m-%d_%H:%M:%S` - MySQL backup completed." >> ${LOGFILE}

## Perform cleanup routine.
f_cleanup
## Exit with the combined return code value.
exit ${ERRORFLAG}

```Here is a sample of the log output:

/var/log/mysql-backup.log
```

2012-05-16_23:00:01 - MySQL backup started.
2012-05-16_23:00:01 --- Partition status:
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  3.8G  1.1G  2.6G  29% /
udev                  237M  4.0K  237M   1% /dev
tmpfs                  99M  540K   98M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  246M     0  246M   0% /run/shm
/dev/sda1             179M   25M  145M  15% /boot
/dev/mapper/LVG-bak   4.0G   65M  3.8G   2% /backup
/dev/mapper/LVG-var   2.0G  347M  1.6G  18% /var
/dev/mapper/LVG-tmp   2.0G   31M  1.9G   2% /tmp
Uptime:            13 days 8 hours 50 min 14 sec
2012-05-16_23:00:01 --- Space consumed in  = 104K
2012-05-16_23:00:07 --- Compressing archive: /tmp/2012-05-16-23-00_mysql-backup.tar.7z
2012-05-16_23:00:18 --- Copying archive file to offsite location.
2012-05-16_23:00:19 --- Total backup time: 0 hour(s) 0 minute(s) 18 second(s)
2012-05-16_23:00:19 - MySQL backup completed.
2012-05-16_23:00:19 - MySQL backup exit code: 0
2012-05-17_23:00:02 - MySQL backup started.
2012-05-17_23:00:02 --- Partition status:
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  3.8G  1.1G  2.6G  29% /
udev                  237M  4.0K  237M   1% /dev
tmpfs                  99M  540K   98M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  246M     0  246M   0% /run/shm
/dev/sda1             179M   25M  145M  15% /boot
/dev/mapper/LVG-bak   4.0G   65M  3.8G   2% /backup
/dev/mapper/LVG-var   2.0G  347M  1.6G  18% /var
/dev/mapper/LVG-tmp   2.0G   31M  1.9G   2% /tmp
Uptime:            8 hours 38 min 26 sec
2012-05-17_23:00:02 --- Space consumed in  = 104K
2012-05-17_23:00:07 --- Compressing archive: /tmp/2012-05-17-23-00_mysql-backup.tar.7z
2012-05-17_23:00:19 --- Copying archive file to offsite location.
2012-05-17_23:00:25 --- Total backup time: 0 hour(s) 0 minute(s) 23 second(s)
2012-05-17_23:00:25 - MySQL backup completed.
2012-05-17_23:00:25 - MySQL backup exit code: 0
2012-05-18_23:00:01 - MySQL backup started.
2012-05-18_23:00:01 --- Partition status:
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  3.8G  1.1G  2.6G  29% /
udev                  237M  4.0K  237M   1% /dev
tmpfs                  99M  540K   98M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  246M     0  246M   0% /run/shm
/dev/sda1             179M   25M  145M  15% /boot
/dev/mapper/LVG-bak   4.0G   65M  3.8G   2% /backup
/dev/mapper/LVG-var   2.0G  347M  1.6G  18% /var
/dev/mapper/LVG-tmp   2.0G   31M  1.9G   2% /tmp
Uptime:            1 day 8 hours 38 min 25 sec
2012-05-18_23:00:01 --- Space consumed in  = 108K
2012-05-18_23:00:05 --- Compressing archive: /tmp/2012-05-18-23-00_mysql-backup.tar.7z
2012-05-18_23:00:16 --- Copying archive file to offsite location.
2012-05-18_23:00:17 --- Total backup time: 0 hour(s) 0 minute(s) 16 second(s)
2012-05-18_23:00:17 - MySQL backup completed.
2012-05-18_23:00:17 - MySQL backup exit code: 0
2012-05-19_23:00:01 - MySQL backup started.
2012-05-19_23:00:01 --- Partition status:
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  3.8G  1.1G  2.6G  29% /
udev                  237M  4.0K  237M   1% /dev
tmpfs                  99M  540K   98M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  246M     0  246M   0% /run/shm
/dev/sda1             179M   25M  145M  15% /boot
/dev/mapper/LVG-bak   4.0G   65M  3.8G   2% /backup
/dev/mapper/LVG-var   2.0G  347M  1.6G  18% /var
/dev/mapper/LVG-tmp   2.0G   31M  1.9G   2% /tmp
Uptime:            2 days 8 hours 38 min 25 sec
2012-05-19_23:00:01 --- Space consumed in  = 108K
2012-05-19_23:00:04 --- Compressing archive: /tmp/2012-05-19-23-00_mysql-backup.tar.7z
2012-05-19_23:00:16 --- Copying archive file to offsite location.
2012-05-19_23:00:17 --- Total backup time: 0 hour(s) 0 minute(s) 16 second(s)
2012-05-19_23:00:17 - MySQL backup completed.
2012-05-19_23:00:17 - MySQL backup exit code: 0

```Here is a sample of the files stored on the offsite server:

D:\MySQL\MySQL
```

2012-05-09-23-00_mysql-backup.tar.7z
2012-05-10-23-00_mysql-backup.tar.7z
2012-05-11-23-00_mysql-backup.tar.7z
2012-05-12-23-00_mysql-backup.tar.7z
2012-05-13-23-00_mysql-backup.tar.7z
2012-05-14-23-00_mysql-backup.tar.7z
2012-05-15-23-00_mysql-backup.tar.7z
2012-05-16-23-00_mysql-backup.tar.7z
2012-05-17-23-00_mysql-backup.tar.7z
2012-05-18-23-00_mysql-backup.tar.7z
2012-05-19-23-00_mysql-backup.tar.7z

```

---

### Post by LHammonds on 2012-05-20
[SIZE=5]Database Backup On Demand[/SIZE]

This script is designed to run every minute looking for key files.  If a specific file shows up on the samba share, it will trigger an immediate backup of the specified database.  This is helpful when scheduling the backup of an app server and coordinating the backup of the database at the same time.  The remote app backup script can trigger the database backup anytime it runs no matter if it is schedule via crontab or manually run.

For an example of a app server configured to make use of the script, take a look at [my MediaWiki thread]("http://ubuntuforums.org/showpost.php?p=11938217&postcount=13").

If a file such as /srv/samba/share/mediawiki shows up, this script will delete that file and perform a backup of the mediawiki database.

To configure this script for your own needs, modify the IF statements between lines 116 and 130.

/var/scripts/prod/mysql-db-backup.sh
```

#!/bin/bash
#############################################
## Name          : mysql-db-backup.sh
## Version       : 1.0
## Date          : 2012-05-14
## Author        : LHammonds
## Purpose       : Backup of a single database
## Compatibility : Verified on Ubuntu Server 10.04 - 12.04 LTS, MySQL 5.1.62 - 5.5.22
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

LOGFILE="${LOGDIR}/mysql-db-backup.log"
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

```Here is a sample of the log output:

/var/log/mysql-db-backup.log
```

2012-05-16_20:00:01 - MySQL mediawiki backup started.
2012-05-16_20:00:02 --- Compressing archive: /var/temp/2012-05-16-20-00_mysql-db-mediawiki.tar.7z
2012-05-16_20:00:05 --- Copying archive file to offsite location.
2012-05-16_20:00:06 --- Total backup time: 0 hour(s) 0 minute(s) 5 second(s)
2012-05-16_20:00:06 - MySQL mediawiki backup completed.
2012-05-17_20:00:02 - MySQL mediawiki backup started.
2012-05-17_20:00:02 --- Compressing archive: /var/temp/2012-05-17-20-00_mysql-db-mediawiki.tar.7z
2012-05-17_20:00:07 --- Copying archive file to offsite location.
2012-05-17_20:00:11 --- Total backup time: 0 hour(s) 0 minute(s) 9 second(s)
2012-05-17_20:00:11 - MySQL mediawiki backup completed.
2012-05-18_20:01:01 - MySQL mediawiki backup started.
2012-05-18_20:01:02 --- Compressing archive: /var/temp/2012-05-18-20-01_mysql-db-mediawiki.tar.7z
2012-05-18_20:01:03 --- Copying archive file to offsite location.
2012-05-18_20:01:04 --- Total backup time: 0 hour(s) 0 minute(s) 3 second(s)
2012-05-18_20:01:04 - MySQL mediawiki backup completed.
2012-05-19_20:01:01 - MySQL mediawiki backup started.
2012-05-19_20:01:02 --- Compressing archive: /var/temp/2012-05-19-20-01_mysql-db-mediawiki.tar.7z
2012-05-19_20:01:03 --- Copying archive file to offsite location.
2012-05-19_20:01:03 --- Total backup time: 0 hour(s) 0 minute(s) 2 second(s)
2012-05-19_20:01:03 - MySQL mediawiki backup completed.

```Here is a sample of the files stored on the offsite server:

D:\MySQL\MySQL-DB
```

2012-05-16-20-00_mysql-db-mediawiki.tar.7z
2012-05-17-20-00_mysql-db-mediawiki.tar.7z
2012-05-18-20-01_mysql-db-mediawiki.tar.7z
2012-05-19-20-01_mysql-db-mediawiki.tar.7z

```

---

### Post by LHammonds on 2012-05-20
[SIZE=5]Check Storage Space[/SIZE]

In favor of manage by exception, I wrote a script that can be scheduled to run daily to check the file systems to see if they are getting close to filling up and will automatically expand them a little bit and give you an email notice.  Everything is done at the megabyte level.  If you do not want the script to perform the increase, simply add a pound sign in front of the resize2fs command on line 64 to comment it out.  Might also want to modify the log and email messages so it does not look like it actually "performed" the resize but instead is telling YOU how to perform the resize.

Here are the lines I added to my crontab schedule which will check each file system I expect will grow on a daily basis @ 1am, 2am and 3am.  I have them checking to see if we have less than 50 MB available and if so, it will try to increase by 50 MB.

crontab
```

0 1 * * * /var/scripts/prod/check-storage.sh var 50 50 > /dev/null 2>&1
0 2 * * * /var/scripts/prod/check-storage.sh bak 50 50 > /dev/null 2>&1
0 3 * * * /var/scripts/prod/check-storage.sh tmp 50 50 > /dev/null 2>&1

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
LOGFILE="${LOGDIR}/check-storage.log"
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
  "tmp")
    FSVol="/dev/LVG/tmp"
    FSMap="/dev/mapper/LVG-tmp"
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

/var/log/check-storage.log
```

2012-05-01_01:00:00 - /dev/LVG/var 44M>5M No action required.
2012-05-01_02:00:00 - /dev/LVG/bak 91M>5M No action required.
2012-05-01_03:00:00 - /dev/LVG/tmp 93M>5M No action required.
2012-05-02_01:00:00 - /dev/LVG/var 44M>5M No action required.
2012-05-02_02:00:00 - /dev/LVG/bak 91M>5M No action required.
2012-05-02_03:00:00 - /dev/LVG/tmp 93M>5M No action required.
2012-05-03_01:00:00 - /dev/LVG/var 44M>5M No action required.
2012-05-03_02:00:00 - /dev/LVG/bak 91M>5M No action required.
2012-05-03_03:00:00 - /dev/LVG/tmp 93M>5M No action required.

```Here is a sample of what the log will look like when it perform increases...notice how I had to increase the threshold in order for it to fire off the increase (but it still just issued a single megabyte increase):

/var/log/check-storage.log
```

2012-05-02_01:00:00 - Starting expansion of /dev/LVG/var
2012-05-02_01:00:00 --- LVSize=75MB, FSSize=50MB, FSAvail=44MB, FSThreshold=55MB, IncreaseBy=1MB
2012-05-02_01:00:00 --- resize2fs /dev/LVG/var 51, ReturnCode=0
2012-05-02_01:00:00 - Finished expansion of /dev/LVG/var
2012-05-02_02:00:00 - Starting expansion of /dev/LVG/bak
2012-05-02_02:00:00 --- LVSize=125MB, FSSize=99MB, FSAvail=91MB, FSThreshold=100MB, IncreaseBy=1MB
2012-05-02_02:00:00 --- resize2fs /dev/LVG/bak 100, ReturnCode=0
2012-05-02_02:00:00 - Finished expansion of /dev/LVG/bak
2012-05-02_03:00:00 - Starting expansion of /dev/LVG/tmp
2012-05-02_03:00:00 --- LVSize=125MB, FSSize=99MB, FSAvail=93MB, FSThreshold=100MB, IncreaseBy=1MB
2012-05-02_03:00:00 --- resize2fs /dev/LVG/temp 100, ReturnCode=0
2012-05-02_03:00:00 - Finished expansion of /dev/LVG/tmp
```

---

### Post by LHammonds on 2012-05-20
[SIZE=5]Migrate Database from Old Server[/SIZE]

Since I am upgrading my database server by installing an entirely new server, I will be using the backup archives created by the same "mysql-backup.sh" script that the new server is using.

Here are the steps to import the databases from the old server into the new server from the latest backup archive on the remote server to /tmp


[LIST=1]
[*]Make a full backup of the current database by typing: **mysqldump --all-databases > /tmp/all-db-before.sql**
[*]Make a restore folder by typing: **mkdir /tmp/restore**
[*]Extract the archive by typing: **7za x -so -w/tmp /tmp/*.7z | tar -C /tmp/restore --strip-components=3 -xf -**
[*]Import the all-database file by typing: **mysql < /tmp/restore/mysql-all.sql**
[*]Make a full backup of the current database by typing: **mysqldump --all-databases > /tmp/all-db-after.sql**
[*]Verify that your databases, tables, rows and users are now on the new server
[*]Cleanup by removing the restore folder: **rm -rf /tmp/restore**
[*]Now would be a good time to run your backup script: **/var/scripts/prod/mysql-backup.sh**
[/LIST]

Now you can point your apps to the new database server or shutdown the old server and then change the IP of this server to match the old server.


[SIZE=5]Crontab Schedule[/SIZE]

I would not advise anyone to ever "edit" a live crontab schedule by typing "crontab -e" but rather edit a saved schedule file and then load the schedule file. This will allow you to make backups of the schedule so you can always go back to a known-good schedule or at least back to the way it was before you made a change...assuming you always work with a copy of the schedule 1st.

Here is my root crontab scheduling file:

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

# m h dom mon dow command

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
0 3 * * * /var/scripts/prod/check-storage.sh tmp 50 50 > /dev/null 2>&1

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

```This concludes my documentation on how I setup a dedicated MySQL server.

If you notice any problems, please reply here and let me know.

Thanks,
LHammonds

---

### Post by LHammonds on 2012-05-23
[SIZE="5"]Web Front-end[/SIZE]

Someone asked if there was a graphical way to manage the server.  After a long sigh, I mentioned that phpmyadmin is a popular front-end.

Here is how you install it:
```
aptitude install phpmyadmin
```

I would recommend uninstalling it after your initial setup since having an Apache web service tends to eat away at your CPU/RAM.  My corporate DB server runs happily on 512 MB of RAM.

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

### Post by LHammonds on 2012-06-18
Document revised using the **sudo su** method to temporarily gain root-level access rather than setting a password on the root account.

The next change will be the setup of the operating system to be generalized a bit and pulled into a different document and then referred to rather than trying to update OS-specific changes in all my different threads.  :)

LHammonds

---

### Post by LHammonds on 2012-07-19
I can no longer edit this thread...therefor, I have moved the thread (and updates) to my own forum. Once I have all my documents settled down, I will see about getting help converting it to the wiki.

[My Notes for Installing MySQL on Ubuntu Server 12.04 LTS]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=193") @ HammondsLegacy.com
 
LHammonds

---

