---
title: "My Notes for Installing Nagios on Ubuntu Server 12.04 LTS"
date: 2012-05-25
forum: Server Platforms
---

### Post by LHammonds on 2012-05-25
Greetings and salutations,

I hope this thread will be helpful to those who follow in my foot steps as well as getting any advice based on what I have done / documented.

This is a Work-In-Progress topic so I will be updating this thread as I complete/update my notes.

[SIZE="5"]High-level overview[/SIZE]

This thread will cover installation of a dedicated Ubuntu server and Nagios monitoring system.  The server will be installed inside a virtual machine vSphere 4.1 running on ESXi 4.1 servers.  I will also supply notes for doing the same thing for Oracle's VirtualBox on a Windows 7 PC.  Although there are some VMware-specific and VirtualBox-specific steps, they are very few and the majority of this documentation will work for other Virtual Machines or even directly installed onto a physical machine (e.g. bare-metal install).  Please excuse any ignorance on my part since I am fairly new to Linux...if you have any advice on doing things better, please let me know.  I love feedback and learning better ways of doing things!

This thread will also cover some custom scripts to help automate tasks such as backing up, automatically growing the file system when free space is low, etc.

I choose to build Nagios from the source download rather than install from the repository with aptitude / apt-get.  The reason is that you get the newer version this way and you have full control over the installation options.

This documentation will only cover a very specific installation.  Nagios was designed to be able to handle just about anything you want to monitor so it will be different for each install and even with the same hardware needing to be monitored, two administrators may decide differently on what needs to be monitored.

[SIZE="5"]Tools utilized in this process[/SIZE]


[LIST]
[*][Ubuntu Server]("http://www.ubuntu.com/download/ubuntu/download") 12.04 LTS, 64-bit
[*]Nagios 3.4.1
[*][Portable PuTTY]("http://portableapps.com/apps/internet/putty_portable") 0.62
[*][VMware vSphere]("http://www.vmware.com/products/vsphere/overview.html") 4.1.0
[*][VirtualBox]("http://www.virtualbox.org/") 4.1.16
[/LIST]

[SIZE="5"]Helpful links[/SIZE]

The list below are sources of information that helped me configure this system as well as some places that might be helpful to me later on as this process continues.

[LIST]
[*][Ubuntu Documentation]("https://help.ubuntu.com")
[*][Ubuntu Firewall Basics]("https://help.ubuntu.com/community/IptablesHowTo#Disabling%20the%20firewall")
[*][A primer on Iptables]("http://bodhizazen.net/Tutorials/iptables")
[*][Ubuntu AppArmor Basics]("https://help.ubuntu.com/community/AppArmor#Disable%20AppArmor%20framework")
[*][InstallationWiki - Nagios]("http://www.installationwiki.org/Installing_Nagios")
[/LIST]

[SIZE="5"]Assumptions[/SIZE]

This documentation will need to make use of some very-specific information that will most-likely be different for each person / location.  And as such, I will note some of these in this section.  They will be highlighted in red throughout the document as a reminder that you should plug-in your own value rather than actually using my "place-holder" value.

Under no circumstance should you use the actual values I list below.  They are place-holders for the real thing.  This is just a checklist template you need to have answered before you start the install process.

Wherever you see [COLOR="red"]RED[/COLOR] in this document, you need to substitute it for what your company uses.  Use the list below as a template you need to have answered before you continue.


[LIST]
[*]Ubuntu Server name: [COLOR="red"]srv-nagios[/COLOR]
[*]Internet domain: [COLOR="red"]mydomain.com[/COLOR]
[*]Ubuntu Server IP address: [COLOR="red"]192.168.107.21[/COLOR]
[*]Ubuntu Server IP subnet mask: [COLOR="red"]255.255.255.0[/COLOR]
[*]Ubuntu Server IP gateway: [COLOR="red"]192.168.107.1[/COLOR]
[*]Internal DNS Server 1: [COLOR="red"]192.168.107.212[/COLOR]
[*]Internal DNS Server 2: [COLOR="red"]192.168.107.213[/COLOR]
[*]External DNS Server 1: [COLOR="red"]8.8.8.4[/COLOR]
[*]External DNS Server 2: [COLOR="red"]8.8.8.5[/COLOR]
[*]Ubuntu Admin ID: [COLOR="red"]administrator[/COLOR]
[*]Ubuntu Admin Password: [COLOR="red"]myadminpass[/COLOR]
[*]Nagios Admin Password: [COLOR="red"]mynagiospass[/COLOR]
[*]Nagios NSClient Port #: [COLOR="red"]12489[/COLOR]
[*]Nagios NRPE Port #: [COLOR="red"]5666[/COLOR]
[*]Nagios Service Password: [COLOR="red"]myservicepass[/COLOR]
[*]Email Server (remote): [COLOR="red"]192.168.107.25[/COLOR]
[*]Windows Share ID: [COLOR="red"]myshare[/COLOR]
[*]Windows Share Password: [COLOR="red"]mysharepass[/COLOR]
[/LIST]

I also assume the reader knows how to use the VI editor.  If not, you will need to [beef up your skill set]("http://www.eng.hawaii.edu/Tutor/vi.html") or use a different editor in place of it.

---

### Post by LHammonds on 2012-05-25
[SIZE="5"]Analysis and Design[/SIZE]

The Ubuntu Server Long-Term Support (LTS) is free but we have the option of buy support and that is the main reason this server was selected.

The largest decision over the configuration of Ubuntu seems to be how the hard drive space is sliced up (partitioned).  I lot of my time was spent researching and learning the various options when it comes to the design layout of the storage.

I like to make use of a design that allows for dynamic growth and fine-tuning if need be.  I also do not like being caught offguard with a scenario where space is filled up with no immediate option other than deleting files.  Long-term life and growth of the system as well as budgeting concerns have to be taken into consideration.

I like to contain the root volume to mainly just static data that won't grow much and push the other folders that are dynamic into their own volumes.  In case you don't know, filling up the root volume on a *nix system is a very bad thing and should be avoided at all costs.  I also want to configure it where the file systems are not taking up 100% of the logical volume.  This will allow me (through automated scripts) to grow the file system as needed and give me some time to add more drives if necessary or shrink other volumes to get more space.

Here are my thoughts on how to slice up the space.


[LIST]
[*]**boot** - This will remain static in size.  It is also the only space residing outside the Logical Volume Manager (LVM)
[*]**root volume** - Operating system and everything else which should remain fairly static.
[*]**swap volume** - This will remain static in size.  However, if amount of RAM is adjusted, this should be adjusted as well.
[*]**var volume** - This is the app/database/log storage and will continue to grow over time.
[*]**srv volume** - This will contain the files stored in the Samba share.
[*]**bak volume** - This will contain a local backup of the application.  So space needs to be around double /var.
[*]**tmp volume** - This location will be used for temporary storage.  Size should be adjusted to match however it is being used.
[*]**Offsite Storage** - This will be handled elsewhere but will be mounted on this server.
[/LIST]

My estimated database store will be about 2 GB.  However, we will start this server off with a lower number.  We will then pretend some event happened such as a popular content site which causes quick growth of the database.  This will increase our storage needs and we will go through adjusting the entire system to accommodate a larger storage capacity.  This will be a good exercise / documentation for what will eventually need to be done later to handle growth.

To get a good idea of the initial hard drive layout and to understand the process better, here is a graphical representation of the initial design for the server:

[IMG]http://tinyurl.com/6r336ct[/IMG]

These numbers will be used for the initial build of the system:

boot = 200 MB
root = 4 GB
swap = 2 GB
bak = 500 MB
tmp = 500 MB
srv = 500 MB
var = 500 MB

NOTE: When the logical volumes and file systems are initially created, they consume the maximum amount of space allocated so that the logical volume size = file system size.  These partition sizes are artificially small for that reason.  These will be later modified so that the logical volume will be larger than the file system so that the file system has room to expand when needed.

Important info:
 - The /tmp folder is strictly temporary.  Each time the server reboots, this folder is deleted and re-created.
 - The /bak folder will retain the most recent backup and is considered the "local" copy of the backup.

[SIZE="5"]VMware Virtual Machine Settings[/SIZE]

Virtual Manager: VMware vSphere Client 4.1
Virtual Host: VMware ESXi Server 4.1


[LIST]
[*]Configuration: Custom
[*]Name: srv-nagios
[*]Datastore: DS3400-LUN0
[*]Virtual Machine Version: 7
[*]Guest Operating System: Linux, Version: Ubuntu Linux (64-bit)
[*]Number of virtual processors: 1
[*]Memory Size: 1024 MB
[*]Number of NICs: 1
[*]NIC 1: VM Network
[*]Adapter: E1000, Connect at Power On: Checked
[*]SCSI controller: LSI Logic Parallel
[*]Select a Disk: Create a new virtual disk
[*]Create a Disk: 8 GB, No thin provisioning, No cluster features, Store with the virtual machine
[*]Advanced Options: Virtual Device Node = SCSI (0:0)
[*]Remove Floppy Drive
[*]Mount CD/DVD Drive to Ubuntu ISO (ubuntu-12.04-server-amd64.iso). Make sure CD/DVD is set to **Connect at power on**
[*]Set boot options to Force BIOS Setup so you can set CDROM to boot before the Hard Disk
[/LIST]

[SIZE="5"]VirtualBox Virtual Machine Settings[/SIZE]

Virtual Manager: Oracle VirtualBox 4.1.14
Virtual Host: Windows 7 Ultimate with SP1 (64-bit)


[LIST]
[*]Name: srv-nagios
[*]Operating System: Linux
[*]Version: Ubuntu (64 bit)
[*]Memory: 1024 MB
[*]Check - Start-up Disk
 - Create new hard disk
 - VMDK
 - Dynamically allocated
 - Size: 8 GB
[*]Select srv-nagios and click Settings (CTRL+S)
 - System, Processor, Enable PAE/NX
 - Network, Attached to: Bridged Adapter, Advanced, Adapter Type: Intel PRO/1000 MT Server
 - Storage, IDE Controller, Choose a virtual CD/DVD disk file, ubuntu-12.04-server-amd64.iso
[/LIST]

[SIZE="5"]Install PuTTY[/SIZE]

The 1st time I installed Ubuntu, I used the console for everything but it was painfully slow to view man (manual) pages and navigating in VI (text editor).  However, I found out that PuTTY is a far better solution for your Ubuntu console because it handles the screen draws much faster and allows for scrolling and copying text.

Download the portable edition and run the install...except it doesn't really "install" like a normal program, it simply extracts to a specified folder and will run from that folder even if you put it on a USB stick and carry over to a new computer (requires no install to run and thus leaves a very small footprint on your system)


[LIST=1]
[*]Start PuTTY
[*]Type the following and click the Save button:
Host Name: [COLOR="Red"]SRV-Nagios[/COLOR] (or the IP such as [COLOR="red"]192.168.107.21[/COLOR])
Port: **22**
Connection type: **SSH**
Saved Sessions: **SRV-Nagios**
[*]Now all you have to do is double-click on the session and it will connect to your server (when online).
[/LIST]

---

### Post by LHammonds on 2012-05-25
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
[*]Type **[COLOR=red]srv-nagios[/COLOR]** [COLOR=green]{ENTER}[/COLOR] (this is your hostname)
[*]Type **[COLOR=red]Administrator[/COLOR]**, [COLOR=green]{ENTER}[/COLOR] for the full name
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept the default of the lowercase name of **[COLOR=red]administrator[/COLOR]**
[*]Type **[COLOR=red]myadminpass[/COLOR]**, [COLOR=green]{ENTER}[/COLOR], **[COLOR=red]myadminpass[/COLOR]**, [COLOR=green]{ENTER}[/COLOR]
[*]Select *No*, [COLOR=green]{ENTER}[/COLOR] to not encrypt your home directory
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept detected time zone (*America/Chicago*)
[*]Select *Manual* [COLOR=green]{ENTER}[/COLOR]
[*]Select *SCSI3 (0,0,0) (sda) - 8.6 GB VMware Virtual disk* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Yes* to create new empty partition table, [COLOR=green]{ENTER}[/COLOR]
[*]Select *pri/log 8.6 GB FREE SPACE* [COLOR=green]{ENTER}[/COLOR]
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
[*]Select *LVG (8384MB)* [COLOR=green]{ENTER}[/COLOR]
[*]Type **swap** [COLOR=green]{ENTER}[/COLOR]
[*]Type **2G** [COLOR=green]{ENTER}[/COLOR] (NOTE: This is double the amount of RAM)
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR]
[*]Select *LVG (6387MB)* [COLOR=green]{ENTER}[/COLOR]
[*]Type **bak** [COLOR=green]{ENTER}[/COLOR]
[*]Type **500M** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR]
[*]Select *LVG (5888MB)* [COLOR=green]{ENTER}[/COLOR]
[*]Type **var** [COLOR=green]{ENTER}[/COLOR]
[*]Type **500M** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR]
[*]Select *LVG (5389MB)* [COLOR=green]{ENTER}[/COLOR]
[*]Type **tmp** [COLOR=green]{ENTER}[/COLOR]
[*]Type **500M** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR]
[*]Select *LVG (4890MB)* [COLOR=green]{ENTER}[/COLOR]
[*]Type **srv** [COLOR=green]{ENTER}[/COLOR]
[*]Type **500M** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Create logical volume* [COLOR=green]{ENTER}[/COLOR]
[*]Select *LVG (4391MB)* [COLOR=green]{ENTER}[/COLOR]
[*]Type **root** [COLOR=green]{ENTER}[/COLOR]
[*]Type **4G** [COLOR=green]{ENTER}[/COLOR] (we will have a small amount leftover in LVG)
[*]Select *Finish* [COLOR=green]{ENTER}[/COLOR]
[*]Select *#1 2.0 GB* directly under *LVM VG LVG, LV swap*, [COLOR=green]{ENTER}[/COLOR]
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR]
[*]Select *swap area* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR]
[*]Select *#1 4.0 GB* directly under *LVM VG LVG, LV root*, [COLOR=green]{ENTER}[/COLOR]
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR]
[*]Select */ - the root file system* [COLOR=green]{ENTER}[/COLOR]
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
[*]Select *#1 499.1 MB* directly under *LVM VG LVG, LV var*, [COLOR=green]{ENTER}[/COLOR]
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR]
[*]Select */var* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Label: none* [COLOR=green]{ENTER}[/COLOR]
[*]Type **var** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR]
[*]Select *#1 499.1 MB* directly under *LVM VG LVG, LV tmp*, [COLOR=green]{ENTER}[/COLOR]
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR]
[*]Select */tmp* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Label: **temp*** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR]
[*]Select *#1 499.1 MB* directly under *LVM VG LVG, LV srv*, [COLOR=green]{ENTER}[/COLOR]
[*]Select *Use as: do not use* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Ext4 journaling file system* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Mount point: none* [COLOR=green]{ENTER}[/COLOR]
[*]Select */srv* [COLOR=green]{ENTER}[/COLOR]
[*]Select *Label: **srv*** [COLOR=green]{ENTER}[/COLOR]
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR]
[*]Here is what the screen looks like at this point: [Partitions]("http://???????????????????????????")
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
[*]At the console login prompt, login with your administrator account (**[COLOR=red]administrator[/COLOR]** / **[COLOR=red]myadminpass[/COLOR]**)
[*]At the $ prompt, temporarily grant yourself super user privilages by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR=red]myadminpass[/COLOR]**).
[*]Type **vi /etc/network/interfaces** [COLOR=green]{ENTER}[/COLOR] and change the following: (We need to change the network interface card (NIC) from using DHCP to a static IP)
From:
```
iface eth0 inet dhcp
```To:
```
iface eth0 inet [B]static
address [COLOR=red]192.168.107.21[/COLOR]
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
[*]In VM menu, select VM --> Snapshot --> Take Snapshot.  Give it a name like **STEP 1** and description of **Ubuntu Server 12.04 LTS, clean install, Static IP: [COLOR=red]192.168.107.21[/COLOR]** and click **OK**
[/LIST]


[SIZE=5]Software Configurations[/SIZE]


[LIST=1]
[*]Start the Ubuntu server and connect using PuTTY.
[*]At the $ prompt, temporarily grant yourself super user privilages by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR=red]myadminpass[/COLOR]**).
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
ls /mnt/cdrom[/B]       ( make sure you see a file such as VMwareTools-8.3.2-257589.tar.gz)[B]
tar zxvf /mnt/cdrom/VMwareTools* -C /tmp/
cd /tmp/vmware-tools-distrib/
./vmware-install.pl -d
reboot
[/B]
```
[/LIST]


[SIZE=5]VirtualBox Guest Additions - Installation[/SIZE]

If you are installing under VirtualBox, be sure to install the Guest Additions to insure maximum performance in a virtual environmnet.


[LIST=1]
[*]Login with your administrator account.  At the $ prompt, temporarily grant yourself super user privilages by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR=red]myadminpass[/COLOR]**).
[*]You need to perform the following commands to fulfill the prerequisites:
```
[B]
aptitude update
aptitude safe-upgrade
aptitude install dkms
reboot
[/B]
```
[*]Login with your administrator account.  At the $ prompt, temporarily grant yourself super user privilages by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR=red]myadminpass[/COLOR]**).
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
[*]Login with your administrator account.  At the $ prompt, temporarily grant yourself super user privilages by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR=red]myadminpass[/COLOR]**).
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
[*]Login with your administrator account.  At the $ prompt, temporarily grant yourself super user privilages by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR=red]myadminpass[/COLOR]**).
[*]Type the following:
```
[B]
cd /opt/VBox*
./uninstall.sh
[/B]
```
[/LIST]

---

### Post by LHammonds on 2012-05-25
[SIZE="5"]Volume / Disk Management[/SIZE]

At this point, each volume is fairly small and the file systems contained in them are taking up all of the volume space.  This setup allows no room to expand our file system as needed!  We need to change this.

We are going to add an additional hard drive and give that space to the LVM.  Then space is going to be given to each volume we are going to grow.  However, we are not going to max-out the size of the file system.  We are going to leave some head room for expansion later which will give us the necessary time to acquire more storage but allow us to immediately grow the file system to accomodate our immediate needs.

bak volume = 4 GB, file system = 2 GB (2 GB available for growth)
srv volume = 1 GB, file system = 500 MB (500 MB available for growth)
tmp volume = 2 GB, file system = 1 GB (1 GB available for growth)
var volume = 2 GB, file system = 1 GB (1 GB available for growth)

We started off with 2 GB to hold these volumes but now need 9 GB.  We means we need at least 7 GB more. Adding a 10 GB hard drive will be enough with a little extra left over. (NOTE: This was an arbitrary number because I mainly want to show you how to add an additional hard drives to the system)

Here is a graphical representation of what needs to be accomplished:

[IMG]http://tinyurl.com/bm2km45[/IMG]

If we were to type **df -h** right now, we should see something like this:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  3.8G  912M  2.7G  26% /
udev                  489M  4.0K  489M   1% /dev
tmpfs                 200M  240K  199M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  498M     0  498M   0% /run/shm
/dev/sda1             179M   25M  145M  15% /boot
/dev/mapper/LVG-bak   473M   23M  427M   5% /bak
/dev/mapper/LVG-var   473M  261M  189M  59% /var
/dev/mapper/LVG-tmp   473M   23M  427M   5% /tmp
/dev/mapper/LVG-srv   473M   23M  427M   5% /srv

```

Since I am running VMware, adding additional space is a snap.  However, I will add it in such a way that Ubuntu will see 1 drive added to the system just as if we were to add a physical drive to a physical server.

[LIST=1]
[*]Shutdown and power off the server by typing **shutdown -P now**
[*]In the vSphere client, right-click the Virtual Machine and choose *Edit Settings*.
[*]On the hardware tab, click the *Add* button and select Hard Disk.  Click Next, choose "Create a new virtual disk", click Next, set the size to **10** GB, click Next, Next, Finish.  Click OK to close the settings and allow VMware to process the changes.
[/LIST]

Collect information about the newly added drive.

[LIST=1]
[*]Start the Ubuntu server and connect using PuTTY.
[*]Login with your administrator account.  At the $ prompt, temporarily grant yourself super user privilages by typing **sudo su** [COLOR="green"]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR="red"]myadminpass[/COLOR]**).
[*]Type **pvdisplay** which should show something similar to this:
```

  --- Physical volume ---
  [COLOR="red"]PV Name               /dev/sda5
  VG Name               LVG[/COLOR]
  PV Size               7.81 GiB / not usable 3.00 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              1999
  Free PE               94
  Allocated PE          1905
  PV UUID               HbQisN-2jhS-FGGG-t5aF-IuMZ-mEDQ-iQNfwx

```
The important bits of info here are the PV Name and VG Name for our existing configuration.
[*]Type **fdisk -l** which should show something similar to this (however I abbreviated it to show just the important parts):
```

Disk /dev/sda: 8589 MB, 8589934592 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      391167      194560   83  Linux
/dev/sda2          393214    16775167     8190977    5  Extended
/dev/sda5          393216    16775167     8190976   8e  Linux LVM


Disk [COLOR="red"]/dev/sdb[/COLOR]:  10.7 GB, 10737418240 bytes
Disk /dev/sdb doesn't contain a valid partition table

```
The important bits of info here is the device path for the new drive which I highlighted in red.
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

If we type **fdisk -l**, we now see /dev/sdb1 which is a Linux LVM partition.

Type the following to create physical volume:
```
**pvcreate /dev/sdb1**
```

Now add the physical volume to the volume group (LVG) by typing the following:
```
**vgextend LVG /dev/sdb1**
```

Now that the space has been added to the logical volume group called LVG, we can now allocate that space to grow the logical volumes.

To get a list of volume paths to use in the next commands, type **lvscan** to show your current volumes and their sizes.

Type the following to grow each volume by a specified amount (the number after the plus sign):
```
[B]
lvextend -L+3500M /dev/LVG/bak
lvextend -L+500M /dev/LVG/srv
lvextend -L+1500M /dev/LVG/tmp
lvextend -L+1500M /dev/LVG/var
[/B]
```

or you can specify the exact size by excluding the plus sign and specifying the end-result size you want:
```
[B]
lvextend -L4G /dev/LVG/bak
lvextend -L1G /dev/LVG/srv
lvextend -L2G /dev/LVG/tmp
lvextend -L2G /dev/LVG/var
[/B]
```

To see the new sizes, type **lvscan**

The last thing to do now is the actual growth of the file systems.  We want to grow the existing file systems but only to the size we mentioned earlier so we do not take up all the space in the volume...we want room to grow in the future so we have time to order and install new drives when needed.
```
[B]
resize2fs /dev/LVG/bak 2G
resize2fs /dev/LVG/tmp 1G
resize2fs /dev/LVG/var 1G
[/B]
```

NOTE: The srv file system is already at the desired 500 MB size so no resize was necessary.

If we need to increase space in **/var** at a later point, we can issue the following command without any downtime (we will automate this in a nifty script later):

```
**resize2fs /dev/LVG/var 1536MB**
```

We could continue to increase this particular file system all the way until we reach the limit of the volume which is 2 GB at the moment.

Remember, **df -h** will tell you the size of the file system and **lvscan** will tell you the size of the volumes where the file systems live in.

If we were to type **df -h** right now, we should see something like this:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  3.8G  912M  2.7G  26% /
udev                  489M  4.0K  489M   1% /dev
tmpfs                 200M  244K  199M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  498M     0  498M   0% /run/shm
/dev/sda1             179M   25M  145M  15% /boot
/dev/mapper/LVG-bak   2.0G   23M  1.9G   2% /bak
/dev/mapper/LVG-var  1004M  261M  692M  28% /var
/dev/mapper/LVG-tmp  1004M   23M  931M   3% /tmp
/dev/mapper/LVG-srv   473M   23M  427M   5% /srv

```

TIP: If you want to see everything in a specific block size, such as everything showing up in megabytes, you can use **df --block-size m**

---

### Post by LHammonds on 2012-05-25
[SIZE="5"]Configure Ubuntu for File Sharing[/SIZE]

This file sharing section is optional but can be handy if you need to swap files between the Linux server and a Windows machine.

This documentation will utilize this share for passing pre-configured files (configs, scripts, etc.) to make it faster/easier during installation.


[LIST=1]
[*]Start the Ubuntu server and connect using PuTTY.
[*]Login with your administrator account.  At the $ prompt, temporarily grant yourself super user privilages by typing **sudo su** [COLOR="green"]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR="red"]myadminpass[/COLOR]**).
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
[*]You should now be able to click Start --> Run and type **\\[COLOR="red"]srv-nagios[/COLOR]** or **\\[COLOR="red"]192.168.107.21[/COLOR]** [COLOR="green"]{ENTER}[/COLOR] and see an explorer window with a *Share* folder.  Drag-n-drop a file into the *Share* folder.  If it worked, it will not display an error message and you should be able to view it from the server by typing **ls -l /srv/samba/share/**
[*]Shutdown and power off the server by typing **shutdown -P now**
[*]In VM menu, select VM --> Snapshot --> Take Snapshot.  Give it a name like **STEP 2** and description of **Ubuntu Server 12.04 LTS, File share configured, Static IP: [COLOR="red"]192.168.107.21[/COLOR]**.  The Snapshot Manager should now have a nice hierarchy of snapshots (STEP 1 --> STEP 2 --> You are here)
[/LIST]

[SIZE="5"]Configure Windows Remote Mount Point[/SIZE]

The remote offsite location is a Windows 2008 server that has a vast amount of hard drive space and currently backs up other servers.

Part of the backup process will be to write files to a mounted folder to a Windows share.

First, let's document the variables for this solution below and highlight them in red throughout the document for easy identification.

The values below are merely samples which you need to change in order to match your environment:

Windows AD Domain Name: [COLOR="red"]work[/COLOR]
Windows Server Name: [COLOR="red"]SRV-Backup[/COLOR]
Windows Server IP: [COLOR="red"]192.168.107.218[/COLOR]
Windows Share Name: nagios
Windows Physical Share Location: [COLOR="red"]D:\Nagios\[/COLOR]
Windows Share ID: [COLOR="red"]myshare[/COLOR]
Windows Share Password: [COLOR="red"]mysharepass[/COLOR]

[SIZE=4]Create a share on a Windows 2008 server[/SIZE]


[LIST=1]
[*]In Windows Explorer, right-click on the [COLOR="red"]*D:\Nagios*[/COLOR] folder and select **Properties**
[*]Click the **Sharing** tab
[*]Click the **Advanced Sharing** button
[*]Place a checkmark beside **Share this folder**
[*]Change the Share name to **nagios**
[*]Set the Comment to **Nagios Backup**
[*]Click the **Permissions** button
[*]Select **Everyone** and click the **Remove** button
[*]Click the **Add** button
[*]Type in your share account: [COLOR="red"]**work\myshare**[/COLOR] and click the **Check Names** button, click **OK**
[*]Place a checkmark for **Allow Full Control** and click **OK**, click **OK**, click **OK**
[*]Create a text file in the root of the shared folder called "online.txt" and you might want to add some text inside saying to never delete this file because it is used (will be) by a backup script.  Probably a good idea to make it read-only as well.  Example: [B]D:\Nagios\online.txt[B]
[/LIST]

[SIZE=4]Create an NFS mount to the Windows 2008 server[/SIZE]

Connecting to a Windows share requires the **samba** and **smbfs** packages to be installed.  If you do not have them, type **aptitude -y install samba smbfs**


[LIST=1]
[*]Login with your administrator account.  At the $ prompt, temporarily grant yourself super user privilages by typing **sudo su** [COLOR="green"]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR="red"]myadminpass[/COLOR]**).
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
echo -e "username=[COLOR="red"]work\\myshare[/COLOR]\npassword=[COLOR="red"]mysharepass[/COLOR]" >> /etc/cifspw
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
mount -t cifs //srv-backup/nagios /mnt/backup --options nouser,rw,nofail,noatime,noexec,credentials=/etc/cifspw
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

### Post by LHammonds on 2012-05-25
[SIZE="5"]Nagios Prerequisites[/SIZE]


[LIST=1]
[*]Install the required programs:
```
[B]
aptitude -y install build-essential apache2 php5-gd wget wibgd2-xpm libgd2-xpm-dev libapache2-mod-php5
[/B]
```
[*]Type **vi /etc/apache2/apache2.conf** and add the following line:
```
[B]
DirectoryIndex index.html index.php index.cgi
[/B]
```
[*]Restart Apache by typing: **/etc/init.d/apache2 restart**
[*]Create users and groups:
```
[B]
mkdir -p /etc/nagios /var/nagios
groupadd --system --gid 9000 nagios
groupadd --system --gid 9001 nagcmd
adduser --system --gid 9000 --home /usr/local/nagios nagios
usermod --groups nagcmd nagios
usermod --append --groups nagcmd www-data
chown nagios:nagios /usr/local/nagios /etc/nagios /var/nagios
[/B]
```
[/LIST]


[SIZE="5"]Build and Install Nagios from Source[/SIZE]


[LIST]
[*]Download Nagios software (NOTE: You can use newer links once new versions become available):
```
[B]
cd /usr/local/src
wget http://prdownloads.sourceforge.net/sourceforge/nagios/nagios-3.4.1.tar.gz
[/B]
```
[*]Build and install Nagios Core:
```
[B]
tar -xzvf /usr/local/src/nagios-3.4.1.tar.gz
cd /usr/local/src/nagios
./configure --sysconfdir=/etc/nagios --localstatedir=/var/nagios --prefix=/usr/local/nagios --with-nagios-user=nagios --with-nagios-group=nagios --with-command-group=nagcmd --with-mail=/usr/bin/sendemail
make all
make install
make install-init
make install-config
make install-commandmode
[/B]
```
[*]Edit the commands by typing **vi /etc/nagios/objects/commands.cfg** to change both **sendemail** references to match the correct sendemail syntax:
```

define command{
 command_name    notify-host-by-email
 command_line    /usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\nHost: $HOSTNAME$\nState: $HOSTSTATE$\nAddress: $HOSTADDRESS$\nInfo: $HOSTOUTPUT$\n\nDate/Time: $LONGDATETIME$\n" | /usr/bin/sendemail **-s srv-mail:25 -f "admin <admin@nagios.server>" -t $CONTACTEMAIL$ -u "** $NOTIFICATIONTYPE$ Host Alert: $HOSTNAME$ is $HOSTSTATE$ ****"
}

define command{
command_name    notify-service-by-email
command_line    /usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\n\nService: $SERVICEDESC$\nHost: $HOSTALIAS$\nAddress: $HOSTADDRESS$\nState: $SERVICESTATE$\n\nDate/Time: $LONGDATETIME$\n\nAdditional Info:\n\n$SERVICEOUTPUT$" | /usr/bin/sendemail **-s srv-mail:25 -f "admin <admin@nagios.server>" -t $CONTACTEMAIL$ -u "** $NOTIFICATIONTYPE$ Service Alert: $HOSTALIAS$/$SERVICEDESC$ is $SERVICESTATE$ ****"
}

```
[*]Save and close commands.cfg
[*]Edit the contacts by typing **vi /etc/nagios/objects/contacts.cfg** and change the following:
```

define contact{
    contact_name     nagiosadmin             ; Short name of user
    use              generic-contact         ; Inherit default values from generic-contact template (defined above)
    alias            [COLOR="red"]**John Doe**[/COLOR]                ; Full name of user
    email            [COLOR="red"]**John.Doe@mydomain.com**[/COLOR]   ; <<***** CHANGE THIS TO YOUR EMAIL ADDRESS ******
}

```
[*]Save and close contacts.cfg
[*]Type the following:
```
[B]
cd /usr/local/src/nagios
make install-webconf
[/B]
```
[*]Set the nagiosadmin password to [COLOR="red"]mynagiospassword[/COLOR] by typing the following:
```
[B]
htpasswd -c /etc/nagios/htpasswd.users nagiosadmin
/etc/init.d/apache2 reload
[/B]
```
[*]Ensure Nagios can execute by typing **chmod +x /etc/init.d/nagios** (NOTE: On this version of Ubuntu and Nagios, it is already set correctly)
[*]Type the following to avoid startup problems: (NOTE: This is not documented anywhere, it is just my trial, error and observation)
```
[B]
mkdir -p /usr/local/nagios/var/spool/checkresults
chown nagios:nagios /var/nagios/spool/checkresults
chown nagios:nagios /var/nagios/spool
chown nagios:nagios /var/nagios
[/B]
```
[*]Ensure Nagios is started whenever the system boots up:
```
[B]
/usr/sbin/update-rc.d -f nagios defaults 99
ln -s /etc/init.d/nagios /etc/rcS.d/S99nagios
[/B]
```
[*]Check your Nagios configuration file for errors.  Look for errors in red.
```
**/usr/local/nagios/bin/nagios -v /etc/nagios/nagios.cfg**
```
[*]NOTE TO SELF: I need to generate (and document) an SSL certificate to enable SSL to protect the password during authentication.  [Self-Signed Certs]("http://library.linode.com/security/ssl-certificates/self-signed")
[*]Start Nagios for the 1st time.
```
**/etc/init.d/nagios start**
```
[*]Access the web-based administration utility at http://[COLOR="red"]192.168.107.21[/COLOR]/nagios/ (use nagiosadmin for the ID and [COLOR="red"]mynagiospassword[/COLOR] for the password)
[/LIST]

NOTE: The Nagios server is now up-and-running but doing absolutely nothing. ;)  We need plugins to actually make it do something so we will install a base plugin pack.  However, we will eventually need to get other plugins and maybe write our own in order to monitor everything we want.

---

### Post by LHammonds on 2012-05-25
[SIZE="5"]Nagios Plugin Prerequisites[/SIZE]

Nagios Plugin Requirements for check_snmp:
```
**perl -MCPAN -e 'install Net::SNMP'**
Configure as much as possible automatically? **yes**
**aptitude -y install snmp**
```
Requirements for check_mysql: (NOTE: For my site, this is not necessary because I will run it locally on MySQL server)
```
**aptitude -y install libmysqlclient-dev**
```
Requirements for check_nrpe:
```
**aptitude -y install libssl-dev**
```

[SIZE="5"]Nagios Plugins[/SIZE]

Download, build and install Nagios plugins (NOTE: You can use newer links once new versions become available):
```
[B]
cd /usr/local/src
wget http://prdownloads.sourceforge.net/sourceforge/nagiosplug/nagios-plugins-1.4.15.tar.gz
tar xzf /usr/local/src/nagios-plugins-1.4.15.tar.gz
cd /usr/local/src/nagios-plugins-1.4.15
./configure --sysconfdir=/etc/nagios --localstatedir=/var/nagios --with-nagios-user=nagios --with-nagios-group=nagios
make
make install
[/B]
```

Download, build and install NRPE plugin
```
[B]
cd /usr/local/src
wget http://prdownloads.sourceforge.net/sourceforge/nagios/nrpe-2.13.tar.gz
tar xzf /usr/local/src/nrpe-2.13.tar.gz
cd /usr/local/src/nrpe-2.13
./configure --sysconfdir=/etc/nagios --libexecdir=/usr/local/nagios/libexec --prefix=/usr/local/nagios --localstatedir=/var/nagios --with-nagios-user=nagios --with-nagios-group=nagios --with-nrpe-user=nagios --with-nrpe-group=nagios --enable-ssl=yes --with-ssl=/usr/bin/openssl --with-ssl-lib=/usr/lib/x86_64-linux-gnu
make all
make install-plugin
[/B]
```

[SIZE="5"]Verify that Plugins are Working![/SIZE]

For all the plugins we intend on using, we need to verify they are working before trying to integrate them into Nagios.  However, not all plugins will work without first configuring the target to be monitored.

Ping an IP address you know to be active:
```
[B]
/usr/local/nagios/libexec/check_icmp -H 192.168.107.20
[/B]
```

Check for an HTTP reply from a web server:
```
[B]
/usr/local/nagios/libexec/check_http -H 192.168.107.20
[/B]
```

Check for a response from an HP LaserJet printer:
```
[B]
/usr/local/nagios/libexec/check_hpjd -H 192.168.107.51 -C public
[/B]
```

Check the uptime of a router via SNMP:
```
[B]
/usr/local/nagios/libexec/check_snmp -H 192.168.107.1 -C public -o sysUpTime.0
[/B]
```
NOTE: For whatever reason, this command hangs on me.  Not sure what I did wrong this time but I'll track it down, fix it and update these dox.

Check a MySQL server (if on local host):
```
[B]
/usr/local/nagios/libexec/check_mysql -H 192.168.107.20 -P 3306 -u mysqlid -p mysqlpassword
[/B]
```
NOTE: This will fail if you do not configure the MySQL server 1st.  However, you might want to run the MySQL command remotely via NRPE instead.

---

### Post by spynappels on 2012-05-25
Howdy!

This is a great How-To. The only suggestion I would have is to make the default position to use sudo rather than "enabling" the root account.By all means explain there is a different way of doing things but as this will be a great resource to people with less understanding, it should stick as closely as possible to the established guidelines for this site.

Please see [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138) for a little more info, I think you may be venturing out on thin ice here and the rest of the How-To is excellent, I'd hate to see it get into bother for this.

Kindest regards,
Stefan

---

### Post by LHammonds on 2012-05-25
> **spynappels said:**
> Howdy!

This is a great How-To. The only suggestion I would have is to make the default position to use sudo rather than "enabling" the root account.By all means explain there is a different way of doing things but as this will be a great resource to people with less understanding, it should stick as closely as possible to the established guidelines for this site.

Please see [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138) for a little more info, I think you may be venturing out on thin ice here and the rest of the How-To is excellent, I'd hate to see it get into bother for this.

Kindest regards,
StefanI already stated as a NOTE before installing Ubuntu that using the root account was just for the initial setup and recommended to switch back to using sudo once setup is complete.  However, I did not document the command...which now has the command listed.  The article you linked me to is mainly pointed towards desktop / GUI interfaces and incorrectly using root to fix problems to run the GUI...thus making the normal use of the system as the root user.  This is NOT even close to what I am doing with this documentation.  

That article also mentions the concern of an "influx of new users" but I'd be willing to bet it is in regard to the desktop usage of Ubuntu.  The server crowd is significantly smaller.  And the documentation for what I am doing will be even smaller than that.  I would be interested to see a show of hands as to how many people are actually setting up their server and following what I have written.  Of the niche crowd that would actually read all of this, they would probably only use bits and pieces.  But I still don't see how I am using the root account as being a problem...even for production systems.  Again, these how-to's that I write are all about the initial setup of a server (which by definition means they are not in "production").  I see no problem with any of these setups eventually becoming production systems.

I seriously doubt the ice is that thin regarding that topic and this thread.

However, if these forums require me to re-write them using sudo for everything, I would simply request that the threads I have created to be deleted and I will post them elsewhere.  I have no intention of documenting how I will not be setting up a server.  If someone would like to make a copy and re-write it using sudo for everything, they can be my guest.  I'm just not interested in doing it that way and feel it would be a waste of my time.

LHammonds

---

### Post by spynappels on 2012-05-25
I'm sorry my (well meant)  comments seem to have upset you, I was saying that it is an excellent how-to, and was simply offering a suggestion as to how it could be done in a way that most matches the recommended setup according to the article I linked to.

A rewrite is not required, I was suggesting an alternative which did not require setting up a root password, ```
sudo su
``` instead of ```
su root
```

Anyway, enjoy using Linux, it is always good to have more than one way of doing things.

---

### Post by LHammonds on 2012-05-25
> **spynappels said:**
> I'm sorry my (well meant)  comments seem to have upset you, I was saying that it is an excellent how-to, and was simply offering a suggestion as to how it could be done in a way that most matches the recommended setup according to the article I linked to.

A rewrite is not required, I was suggesting an alternative which did not require setting up a root password, ```
sudo su
``` instead of ```
su root
```Anyway, enjoy using Linux, it is always good to have more than one way of doing things.
My apologies.  In my ignorance, I misunderstood what you were asking.  However, if I simply change the syntax which will accomplish the same thing, it may present a long-term problem for those looking at this thread.  Meaning, if I present this method without a warning, I can see how people would go about doing the sudo su on a regular basis rather than just for the initial setup.

I'll contemplate this and figure out how to arrange my words for this approach.

Thanks for the feedback and clarification.
LHammonds

---

### Post by spynappels on 2012-05-25
> **LHammonds said:**
> I'll contemplate this and figure out how to arrange my words for this approach.


In the Initial Configuration section, you could put in a note saying that the following commands need root privileges, this can be achieved by prefacing the command with sudo. Rather than doing this for every command, you can temporarily give yourself root privileges by using sudo su.

Good luck, I genuinely think this is a great how-to.

---

### Post by LHammonds on 2012-05-25
> **spynappels said:**
> Good luck, I genuinely think this is a great how-to.Thanks.  It is more of a "How I do" than a "How to" since I know just enough to make things work rather than knowing all the various ways of doing things or even knowing exactly what is going on under-the-hood.

Still not sure if I am doing things right or wrong other than just getting it to work...I don't typically get many responses on such things.  And after seeing my initial response to you, I probably won't get any other suggestions. hehehe.

Thanks,
LHammonds

---

### Post by LHammonds on 2012-05-28
[SIZE="5"]Configuration Framework[/SIZE]

The 1st thing I like to do is the creation of the folder structure I plan to use and then copy or rename all example configuration files to unused text files.  This ensures the originals are preserved as a reference.
```
[B]
mkdir -p /etc/nagios/servers
mkdir -p /etc/nagios/printers
mkdir -p /etc/nagios/switches
mkdir -p /etc/nagios/workstations
cp /etc/nagios/nagios.cfg /etc/nagios/example-nagios.txt
cp /etc/nagios/resource.cfg /etc/nagios/example-resource.txt
mv /etc/nagios/objects/windows.cfg /etc/nagios/servers/example-win.txt
mv /etc/nagios/objects/localhost.cfg /etc/nagios/servers/example-local.txt
mv /etc/nagios/objects/switch.cfg /etc/nagios/switches/example-sw.txt
mv /etc/nagios/objects/printer.cfg /etc/nagios/printers/example-ptr.txt
cp /etc/nagios/objects/commands.cfg /etc/nagios/objects/example-commands.txt
cp /etc/nagios/objects/contacts.cfg /etc/nagios/objects/example-contacts.txt
cp /etc/nagios/objects/templates.cfg /etc/nagios/objects/example-templates.txt
cp /etc/nagios/objects/timeperiods.cfg /etc/nagios/objects/example-timeperiods.txt
chown --recursive nagios:nagios /etc/nagios/*
chmod --recursive 0664 *.cfg
[/B]
```

Edit **/etc/nagios/nagios.cfg** and uncomment/add lines 52, 53 and 54 so it looks like this:
```
[B]
cfg_dir=/etc/nagios/servers
cfg_dir=/etc/nagios/printers
cfg_dir=/etc/nagios/switches
cfg_dir=/etc/nagios/workstations
[/B]
```
This allows you to place config files in those folders and they will be automatically picked up without having to edit the Nagios.cfg file.  I have a file for each object...or you could place all objects into a single file but it makes it harder to edit with the more you monitor.

[SIZE="5"]verify.sh[/SIZE]

Anytime you need to make a configuration change, you should always run a verification against your changes to ensure the Nagios service will be able to start up once you restart the service for the change to take effect.  This is called the pre-flight check and this script will make it easier to run.

The full command is this:

```
**/usr/local/nagios/bin/nagios -v /etc/nagios/nagios.cfg**
```

As you can see, it is a lot to type/remember.  I prefer to have a handy little script in the configuration folder to make it easier to run a verification.

/etc/nagios/verify.sh
```
[B]
#!/bin/bash
/usr/local/nagios/bin/nagios -v /etc/nagios/nagios.cfg
[/B]
```
Do not forget to make it executable after creating it.  **chmod 0755 /etc/nagios/verify.sh**

Now all that has to be done is to type **./verify.sh** if in the config folder.  If currently sitting in a sub-folder, just type **../verify.sh**

[SIZE="5"]Host Groups[/SIZE]

I group all of my objects according to how I like to see them separated.  This is done using "hostgroups" when defining a host.  I keep all of these hostgroups defined in a single configuration file.

The file is referenced in /etc/nagios/nagios.cfg with the following line:

```
**cfg_file=/etc/nagios/objects/hostgroups.cfg**
```

Here is a sample of what is contained in that file:

/etc/nagios/objects/hostgroups.cfg
```

###############################################################################
###############################################################################
#
# HOST GROUP DEFINITIONS
#
###############################################################################
###############################################################################

define hostgroup{
        hostgroup_name  ibm-servers
        alias           IBM Servers
        }

define hostgroup{
        hostgroup_name  aix-servers
        alias           IBM AIX Servers
        }

define hostgroup{
        hostgroup_name  ubuntu-servers
        alias           Ubuntu Servers
        }

define hostgroup{
        hostgroup_name  esx-servers
        alias           ESX Servers
        }

define hostgroup{
    hostgroup_name    windows2000-servers
    alias        Windows 2000 Servers
    }

define hostgroup{
    hostgroup_name    windows2003-servers
    alias        Windows 2003 Servers
    }

define hostgroup{
    hostgroup_name    windows2008-servers
    alias        Windows 2008 Servers
    }

define hostgroup{
    hostgroup_name    win7-pcs
    alias        Windows 7 PCs
    }

define hostgroup{
    hostgroup_name    winxp-pcs
    alias        Windows XP PCs
    }

define hostgroup{
    hostgroup_name    switches
    alias        Network Switches
    }

define hostgroup{
    hostgroup_name    wireless
    alias        Wireless Access Points
    }

define hostgroup{
    hostgroup_name    printers-hp
    alias        HP Printers
    }

define hostgroup{
    hostgroup_name    printers-brother
    alias        Brother Printers
    }

define hostgroup{
    hostgroup_name    copiers-toshiba
    alias        Toshiba Copiers
    }

```

[SIZE="5"]Sample Ubuntu Server Config File[/SIZE]

Here is my basic shell for an Ubuntu server:

/etc/nagios/servers/srv-wiki.cfg
```

###############################################################################
#
# HOST DEFINITION
#
###############################################################################

define host{
        use             ubuntu-server
        host_name       srv-wiki
        alias           SRV-Wiki
        address         192.168.107.23
        hostgroups      ubuntu-servers
        contacts        linux-admin-pager
        parents         srv-esxi1
        }

###############################################################################
#
# SERVICE DEFINITIONS
#
###############################################################################

define service{
    use                     generic-service
    host_name               srv-wiki
    service_description     PING
    check_command           check_icmp!100.0,20%!500.0,60%
    }

define service{
    use                     generic-service
    host_name               srv-wiki
    service_description     HTTP
    check_command           check_http
    }

define service{
    use                     generic-service
    host_name               srv-wiki
    service_description     APT Upgrade
    check_command           check_nrpe!check_apt
    }

define service{
    use                     generic-service
    host_name               srv-wiki
    service_description     APT Upgrade MotD
    check_command           check_nrpe!check_apt_motd
    }

define service{
    use                     generic-service
    host_name               srv-wiki
    service_description     All Disks
    check_command           check_nrpe!check_disk_all
    notifications_enabled   1
    }

define service{
    use                     generic-service
    host_name               srv-wiki
    service_description     Current Load
    check_command           check_nrpe!check_load
    notifications_enabled   1
    }

define service{
    use                     generic-service
    host_name               srv-wiki
    service_description     Total Processes
    check_command           check_nrpe!check_total_procs
    notifications_enabled   1
    }

define service{
    use                     generic-service
    host_name               srv-wiki
    service_description     Swap Usage
    check_command           check_nrpe!check_swap
    notifications_enabled   1
    }

define service{
    use                     generic-service
    host_name               srv-wiki
    service_description     Zombie Processes
    check_command           check_nrpe!check_zombie_procs
    notifications_enabled   1
    }

define service{
    use                     generic-service
    host_name               srv-wiki
    service_description     Users
    check_command           check_nrpe!check_users
    }

```


[SIZE="5"]Sample Windows Server Config File[/SIZE]

Here is my basic shell for a Windows server:

/etc/nagios/servers/srv-mssql.cfg
```

define host{
    use             windows-server
    host_name       srv-mssql
    alias           Win2008-SRV-GP
    address         192.168.107.69
    hostgroups      windows2008-servers
        contacts        windows-admin-email
    parents         srv-esxi2
    }

###############################################################################
#
# SERVICE DEFINITIONS
#
###############################################################################
define service{
        use                     generic-service
        host_name               srv-mssql
        service_description     NSClient++ Version
        check_command           check_nt!CLIENTVERSION -H $HOSTADDRESS$ -p 12489 -s $USER5$
        }

define service{
        use                     generic-service
        host_name               srv-mssql
        service_description     Uptime
        check_command           check_nt!UPTIME -H $HOSTADDRESS$ -p 12489 -s $USER5$
        }

define service{
        use                     generic-service
        host_name               srv-mssql
        service_description     CPU Load
        check_command           check_nt!CPULOAD!-l 5,80,90 -H $HOSTADDRESS$ -p 12489 -s $USER5$
        }

define service{
        use                     generic-service
        host_name               srv-mssql
        service_description     Memory Usage
        check_command           check_nt!MEMUSE!-w 80 -c 90 -H $HOSTADDRESS$ -p 12489 -s $USER5$
        }

define service{
        use                     hd-service
        host_name               srv-mssql
        service_description     Drive C:
        check_command           check_nt!USEDDISKSPACE!-l c -w 80 -c 90 -H $HOSTADDRESS$ -p 12489 -s $USER5$
        }

define service{
        use                     hd-service
        host_name               srv-mssql
        service_description     Drive D:
        check_command           check_nt!USEDDISKSPACE!-l d -w 80 -c 90 -H $HOSTADDRESS$ -p 12489 -s $USER5$
        }

define service{
        use                     generic-service
        host_name               srv-mssql
        service_description     MS SQL Server
        check_command           check_nt!SERVICESTATE!-d SHOWALL -l MSSQLSERVER -H $HOSTADDRESS$ -p 12489 -s $USER5$
        }

define service{
        use                     generic-service
        host_name               srv-mssql
        service_description     SQL Server Agent
        check_command           check_nt!SERVICESTATE!-d SHOWALL -l SQLSERVERAGENT -H $HOSTADDRESS$ -p 12489 -s $USER5$
        }

define service{
        use                     generic-service
        host_name               srv-mssql
        service_description     WindowsUpdates
        check_command           check_nrpe!check_updates!1
        }

## This can be used for servers that require the console to be logged in.
#define service{
#        use                     generic-service
#        host_name               srv-mssql
#        service_description     Explorer
#        check_command           check_nt!PROCSTATE!-d SHOWALL -l Explorer.exe -H $HOSTADDRESS$ -p 12489 -s $USER5$
#        }

```

---

### Post by LHammonds on 2012-05-28
[SIZE=5]Sample Network Switch Config File[/SIZE]

Here is my basic shell for a switch:

NOTE: The MIB codes are specific to the hardware, you probably will need to research the MIB that matches your hardware.

```

###############################################################################
# Switches.cfg
#
# Last Modified: 2012-05-25
###############################################################################

###############################################################################
#
# HOST DEFINITIONS
#
###############################################################################

define host{
        use             summit-switch
        host_name       SW-TX-IS
        alias           Texas IS Area
        address         192.168.107.230
        hostgroups      switches
        parents         SW-TX-Core
        }

define host{
        use             cisco-switch
        host_name       SW-TX-FD
        alias           Texas Front Desk
        address         192.168.107.231
        hostgroups      switches
        parents         SW-TX-FD
        }

###############################################################################
#
# SERVICE DEFINITIONS
#
###############################################################################

# Ping switch

define service{
        use                     switch-critical-service
        host_name               SW-TX-IS,SW-TX-FD
        service_description     PING
        check_command           check_ping!200.0,20%!600.0,60%
        }

# Monitor uptime via SNMP

define service{
        use                     switch-noncritical-service
        host_name               SW-TX-IS,SW-TX-FD
        service_description     Uptime
        check_command           check_snmp!-C public -o sysUpTime.0
        }

# Monitor Contact via SNMP

define service{
        use                     switch-noncritical-service
        host_name               SW-TX-IS,SW-TX-FD
        service_description     Contact
        check_command           check_snmp!-C public -o sysContact.0
        }

# Monitor Location via SNMP

define service{
        use                     switch-noncritical-service
        host_name               SW-TX-IS,SW-TX-FD
        service_description     Location
        check_command           check_snmp!-C public -o sysLocation.0
        }

# Monitor Over Temperature Alarm via SNMP

define service{
        use                     switch-noncritical-service
        host_name               SW-TX-IS,SW-TX-FD
        service_description     Temperature Over Alarm
        check_command           check_snmp!-C public -o .1.3.6.1.4.1.1916.1.1.1.7.0
        }

# Monitor Current Temperature via SNMP

define service{
        use                     switch-noncritical-service
        host_name               SW-TX-IS,SW-TX-FD
        service_description     Temperature Current
        check_command           check_snmp!-C public -o .1.3.6.1.4.1.1916.1.1.1.8.0
        }

# Monitor the Primary Software Revision Number via SNMP

define service{
        use                     switch-noncritical-service
        host_name               SW-TX-IS,SW-TX-FD
        service_description     Software Rev 1st
        check_command           check_snmp!-C public -o .1.3.6.1.4.1.1916.1.1.1.13.0
        }

# Monitor the Secondary Software Revision Number via SNMP

define service{
        use                     switch-noncritical-service
        host_name               SW-TX-IS,SW-TX-FD
        service_description     Software Rev 2nd
        check_command           check_snmp!-C public -o .1.3.6.1.4.1.1916.1.1.1.14.0
        }

```[SIZE=5]Sample HP Printer Config File[/SIZE]

Here is my basic shell for an HP printer:

```

###############################################################################
# Printer-HP.cfg
#
# Last Modified: 2012-05-25
###############################################################################

###############################################################################
#
# HOST DEFINITIONS
#
###############################################################################

define host{
        use             generic-printer
        host_name       PTR-TX-ADMIN
        alias           Texas Admin
        address         192.168.107.254
        hostgroups      printers-hp
        parents         SW-TX-Core
}

define host{
        use             generic-printer
        host_name       PTR-TX-ADMIN-COLOR
        alias           Texas Admin - HPColor
        address         192.168.107.253
        hostgroups      printers-hp
        parents         SW-TX-Core
        }

###############################################################################
#
# SERVICE DEFINITIONS
#
###############################################################################

define service{
        use                     hp-noncritical-service
        host_name               PTR-TX-ADMIN,PTR-TX-ADMIN-COLOR
        service_description     PING
        check_command           check_ping!3000.0,80%!5000.0,100%
        }

define service{
        use                     hp-noncritical-service
        host_name               PTR-TX-ADMIN,PTR-TX-ADMIN-COLOR
        service_description     Printer Status
        check_command           check_hpjd!-C public
        }

```[SIZE=5]Sample Brother Printer Config File[/SIZE]

Here is my basic shell for an Brother printer:

```

###############################################################################
# Printer-Brother.cfg
#
# Last Modified: 2010-05-25
###############################################################################

###############################################################################
#
# HOST DEFINITIONS
#
###############################################################################

define host{
        use             generic-printer
        host_name       PTR-TX-IS
        alias           Texas IS - ISHP
        address         192.168.107.252
        hostgroups      printers-brother
        parents         SW-TX-Core
        }

define host{
        use             generic-printer
        host_name       PTR-TX-FD
        alias           Texas Front Desk
        address         192.168.107.251
        hostgroups      printers-brother
        parents         SW-TX-Core
        }

###############################################################################
#
# SERVICE DEFINITIONS
#
###############################################################################

# Create a service for "pinging" the printer occassionally.  Useful for monitoring RTA, packet loss, etc.

define service{
        use                     brother-noncritical-service
        host_name               PTR-TX-IS,PTR-TX-FD
        service_description     PING
        check_command           check_ping!3000.0,80%!5000.0,100%
        normal_check_interval   10
        retry_check_interval    1
        }

```[SIZE=5]Sample Toshiba Copier Config File[/SIZE]

Here is my basic shell for a Toshiba Copier:

```

###############################################################################
# Copier-Toshiba.cfg
#
# Last Modified: 2012-05-25
###############################################################################

###############################################################################
#
# HOST DEFINITIONS
#
###############################################################################

define host{
        use             toshiba-copier
        host_name       TE-COPIER-01
        alias           Toshiba e-Studio255
        address         192.168.107.250
        hostgroups      copiers-toshiba
        parents         SW-TX-Core
        }

define host{
        use             toshiba-copier
        host_name       TE-COPIER-02
        alias           Toshiba e-Studio255
        address         192.168.107.249
        hostgroups      copiers-toshiba
        parents         SW-TX-Core
        }

###############################################################################
#
# SERVICE DEFINITIONS
#
###############################################################################

# Create a service for "pinging" the printer occassionally.  Useful for monitoring RTA, packet loss, etc.

define service{
        use                     copier-service
        host_name               TE-COPIER-01,TE-COPIER-02
        service_description     PING
        check_command           check_ping!3000.0,80%!5000.0,100%
        }

define service{
        use                     copier-service
        host_name               TE-COPIER-01,TE-COPIER-02
        service_description     Contact
        check_command           check_snmp!-C public -o sysContact.0
        }

define service{
        use                     copier-service
        host_name               TE-COPIER-01,TE-COPIER-02
        service_description     Location
        check_command           check_snmp!-C public -o sysLocation.0
        }

```

---

### Post by LHammonds on 2012-05-28
[SIZE=5]Monitoring Remote Linux Servers[/SIZE]

Since there are other Linux boxes that need to be monitored, the NRPE plugin and NRPE service will be installed on each Linux box.

Setup the remote Linux server to be monitored:

Create the Nagios user and group:
```
[B]
groupadd --system --gid 9000 nagios
adduser --system --gid 9000 --home /usr/local/nagios nagios
chown nagios:nagios /usr/local/nagios
chmod 0755 /usr/local/nagios
[/B]
```Install Nagios standard and NRPE plugins.  Rather and compiling from source, we will just use what comes with the repository.
```
[B]
aptitude -y install nagios-plugins nagios-nrpe-server
[/B]
```Make a backup of the NRPE configuration files before modifying them:
```
[B]
cp /etc/nagios/nrpe.cfg /etc/nagios/nrpe.cfg.bak
cp /etc/nagios/nrpe_local.cfg /etc/nagios/nrpe_local.cfg.bak
[/B]
```Edit the local configuration:
```
[B]
vi /etc/nagios/nrpe_local.cfg
[/B]
```Add the IP of your Nagios server to the "allowed_hosts" line and list only the plugins that be used:
```
[B]
allowed_hosts=192.168.107.21,127.0.0.1
command[check_users]=/usr/lib/nagios/plugins/check_users -w 5 -c 10
command[check_load]=/usr/lib/nagios/plugins/check_load -w 15,10,5 -c 30,25,20
command[check_disk_app]=/usr/lib/nagios/plugins/check_disk -p /var -w 20% -c 10%
command[check_disk_root]=/usr/lib/nagios/plugins/check_disk -p / -w 20% -c 10%
command[check_disk_all]=/usr/lib/nagios/plugins/check_disk -w 15% -c 10%
command[check_zombie_procs]=/usr/lib/nagios/plugins/check_procs -w 5 -c 10 -s Z
command[check_total_procs]=/usr/lib/nagios/plugins/check_procs -w 150 -c 200
command[check_swap]=/usr/lib/nagios/plugins/check_swap -w 15% -c 10%
command[check_apt]=/usr/lib/nagios/plugins/check_apt
[/B]
```TIP: if you define separate disk checks like the above, you can assign different notifications.  For example, you could have the Linux administrator get email notification when the root partition reaches the warning threshold (during business hours) and send an alert to his pager (at any time of the day) if the root partition reaches critical.  The application manager could get a different notice for /var notices such as both warnings and criticals going to through SMS to his phone at any time of the day.

Check the status of the NRPE server:
```
**/etc/init.d/nagios-nrpe-server status**
```If the NRPE server is not running, this is how you can start it:
```
**/etc/init.d/nagios-nrpe-server start**
```If the NRPE server was already running and you made configuration changes, use this command to load the new changes:
```
**/etc/init.d/nagios-nrpe-server reload**
```Now see if your configured commands will run on your server (before trying to test them remotely on the Nagios server)

```
[B]
/usr/lib/nagios/plugins/check_users -w 5 -c 10
/usr/lib/nagios/plugins/check_load -w 15,10,5 -c 30,25,20
/usr/lib/nagios/plugins/check_disk -w 15% -c 10%
/usr/lib/nagios/plugins/check_procs -w 5 -c 10 -s Z
/usr/lib/nagios/plugins/check_procs -w 150 -c 200
/usr/lib/nagios/plugins/check_swap -w 15% -c 10%
/usr/lib/nagios/plugins/check_apt
[/B]
```[SIZE=5]Test Connectivity of NRPE Plugin[/SIZE]

Test the connectivity of the NRPE service on your server to be monitored by trying to access the server via telnet using the NRPE port number.

If we installed the NRPE server on a machine with the address of 192.168.107.20, type the following at the console of your Nagios server:

```
**telnet 192.168.107.20 5666**
```If you get a response of **Escape character is '^]'.**, then you have a good connection.  Type **exit** to close the connection.

If the command fails with a timeout, you might need to add rules to your firewall:
```
[B]
iptables -A INPUT -p tcp  --dport 5666 -j ACCEPT
iptables -A OUTPUT -p tcp  --dport 5666 -j ACCEPT
service iptables save
[/B]
```Now try executing some of the commands you have configured on your remote Linux server (that stuff in the nrpe_local.cfg file)

```
[B]
/usr/local/nagios/libexec/check_nrpe -H 192.168.107.20 -p 5666 -c check_users
/usr/local/nagios/libexec/check_nrpe -H 192.168.107.20 -p 5666 -c check_load
/usr/local/nagios/libexec/check_nrpe -H 192.168.107.20 -p 5666 -c check_disk_all
/usr/local/nagios/libexec/check_nrpe -H 192.168.107.20 -p 5666 -c check_zombie_procs
/usr/local/nagios/libexec/check_nrpe -H 192.168.107.20 -p 5666 -c check_total_procs
/usr/local/nagios/libexec/check_nrpe -H 192.168.107.20 -p 5666 -c check_apt
[/B]
```If it all looks good, you can then use commands in a server configuration file.  See the sample configurations posted earlier.

---

### Post by LHammonds on 2012-05-28
[SIZE="5"]Custom Plugin - Check HTTPS[/SIZE]

On one of my Linux servers, I have a web mail service that I wanted to keep an eye on. However, the check_http did not work because the server only uses SSL (HTTPS) on port 443. I did not see a check_https command so I tried my hand at making one and it works like a champ.

Here is how I made and implemented custom HTTPS checking function.

The first thing was to create a script that would communicate to the server. We already have WGET installed as one of the prerequisite programs so I used that program. Here is what the script looks like:

/usr/local/nagios/libexec/check_https
```

#!/bin/bash
###########################################
## Name         : check_https
## Version      : 1.0
## Date         : 2012-01-03
## Author       : LHammonds
## Purpose      : Check for response from HTTPS server
## Requirements : WGET
## Parameters   :
##    1 = Server IP Address (Required)
##    2 = Port Number (Optional)
## Exit Codes   :
##    0 = Success
##    1 = Failure
##    2 = Error, missing required parameter
###########################################
OUTFILE="/tmp/check_https_out.$$"
ERRFILE="/tmp/check_https_err.$$"
WGETCMD="$(which wget)"

## Do basic check on arguments passed to the script.
if [ "$1" = "" ]; then
  echo "Missing required parameter"
  exit 2
fi
if [ "$2" = "" ]; then
  ## Assume default port.
  SSLPORT="443"
else
  SSLPORT=$2
fi
${WGETCMD} --no-check-certificate --output-document=${OUTFILE} -S https://$1:${SSLPORT} 2> ${ERRFILE}
RETURNVALUE=$?
if [ ${RETURNVALUE} -eq 0 ];  then
  echo "HTTPS OK"
  EXITCODE=0
else
  echo "Connection refused. Code=${RETURNVALUE}"
  EXITCODE=1
fi
if [ -f ${OUTFILE} ]; then
  rm ${OUTFILE}
fi
if [ -f ${ERRFILE} ]; then
  rm ${ERRFILE}
fi
exit ${EXITCODE}

```

After creating the file, you need to set the correct ownership and permissions as follows:
```
[B]
chown nagios:nagios /usr/local/nagios/libexec/check_https
chmod 0755 /usr/local/nagios/libexec/check_https
[/B]
```

To test it out, run the command against a server running HTTPS and then against a server not running HTTPS. Example:

```
[B]
/usr/local/nagios/libexec/check_https 192.168.107.25 443
[/B]
```

Next, we add this script to the commands file. Type **vi /etc/local/nagios/etc/objects/commands.cfg**

Find the existing "check_http" command and you basically just copy the definition and add "s" to the end of http and remove the "-I" option. Example:
```

define command{
        command_name     check_http
        command_line     $USER1$/check_http -I $HOSTADDRESS $ARG1$
        }

[B]define command{
        command_name     check_https
        command_line     $USER1$/check_https $HOSTADDRESS 443
        }[/B]

```

Now we can add a service to monitor HTTPS by adding the following to the server configuration file:

```
[B]
define service{
        use                     generic-service
        host_name               srv-securewebserver
        service_description     web mail server
        check_command           check_https
        }
[/B]
```


[SIZE="5"]Custom Plugin - Check APT MotD[/SIZE]

Reference: [Original source]("http://www.sandfordit.com/vwiki/Nagios")

This plugin is a bit different from the built-in APT check for Linux servers.  This plugin was designed to give the same kind of messages that you get when you login to an Ubuntu console.

One thing this script will catch that the built-in APT will not is the "reboot required" state of the server.

The script will be executed on the remote Linux server so we will be making use of NRPE.

On the remote Linux server, create the script:

```
[B]
touch /usr/lib/nagios/plugins/check_apt_motd.sh
chown root:root /usr/lib/nagios/plugins/check_apt_motd.sh
chmod 0755 /usr/lib/nagios/plugins/check_apt_motd.sh
vi /usr/lib/nagios/plugins/check_apt_motd.sh
[/B]
```

/usr/lib/nagios/plugins/check_apt_motd.sh
```

#!/bin/sh
#
# check_apt_packages - nagios plugin
#
# Checks for any packages to be applied
# Built for Ubuntu 10 (LTS), see following URL for further info
# - http://www.sandfordit.com/vwiki/index.php/Nagios#Ubuntu_Software_Updates_Monitor
#
# By Simon Strutt
# Version 1 - Jan 2012

# Include standard Nagios library
. /usr/lib/nagios/plugins/utils.sh || exit 3


if [ ! -f /usr/lib/update-notifier/apt-check ]; then
        exit $STATE_UNKNOWN
fi

APTRES=$(/usr/lib/update-notifier/apt-check 2>&1)
PKGS=$(echo $APTRES | cut -f1 -d';')
SEC=$(echo $APTRES | cut -f2 -d';')

if [ -f /var/run/reboot-required ]; then
        REBOOT=1
        TOAPPLY=`cat /var/run/reboot-required.pkgs`
else
        REBOOT=0
fi

if [ "${PKGS}" -eq 0 ]; then
        if [ "${REBOOT}" -eq 1 ]; then
                RET=$STATE_WARNING
                RESULT="Reboot required to apply ${TOAPPLY}"
        else
                RET=$STATE_OK
                RESULT="No packages to be updated"
        fi
elif [ "${SEC}" -eq 0 ]; then
        RET=$STATE_WARNING
        RESULT="${PKGS} packages to update (no security updates)"
else
        RET=$STATE_CRITICAL
        RESULT="${PKGS} packages (including ${SEC} security) packages to update"
fi

echo $RESULT
exit $RET

```

Test the script to see if it is working: **/usr/lib/nagios/plugins/check_apt_motd.sh**

The output should look something like one of these:
```

Reboot required to apply libssl0.9.8

```
or
```

1 packages to update (no security updates)

```
or
```

No packages to be updated

```

Add the script to the trusted NRPE commands to be executed.  Edit **/etc/nagios/nrpe_local.cfg**

```
[B]
command[check_apt_motd]=/usr/lib/nagios/plugins/check_apt_motd.sh
[/B]
```

The NRPE Server now needs to reload the configuration for the changes to take affect.
```
**/etc/init.d/nagios-nrpe-server reload**
```

On the Nagios server, add the following command to the remote Linux server's configuration file:

/etc/nagios/servers/srv-wiki.cfg
```
[B]
define service{
        use                             generic-service
        host_name                       [COLOR="red"]srv-wiki[/COLOR]
        service_description             APT Upgrade MotD
        check_command                   check_apt_motd
        }
[/B]
```

The final step is to verify that nothing is broken in the configuration:
```
[B]
/etc/nagios/verify.sh
[/B]
```

If there were no errors or warnings, restart Nagios to load the new configuration:
```
[B]
/etc/init.d/nagios stop
/etc/init.d/nagios start
[/B]
```

---

### Post by LHammonds on 2012-05-28
[SIZE=5]Custom Plugin - Check ESXi Hardware[/SIZE]

Reference: [Original source]("http://www.claudiokuenzler.com/nagios-plugins/check_esxi_hardware.php")

I use this custom script to check the health of my ESXi servers.  It is run directly from the Nagios server.

This script requires the PyWBEM Python library.  Here is how to install it:

```
**aptitude -y install python-pywbem**
```You then need to add a command to call the script.  Edit **/etc/nagios/objects/commands.cfg** and add the following:

```
[B]
# 'check_esxi_hardware' command definition

define command{
        command_name    check_esxi_hardware
        command_line    $USER1$/check_esxi_hardware.py -H $HOSTADDRESS$ -U $ARG1$ -P $ARG2$ -V $ARG3$ $ARG4$
        }
[/B]
```To access the ESXi data, you will need to supply and ID/password.  The password can be placed in the "resources.cfg" file but let's make sure it is secured first.

```
[B]
chmod 0600 /etc/nagios/resources.cfg
chown nagios:nagios /etc/nagios/resources.cfg
[/B]
```Edit **/etc/nagios/resources.cfg** and add the following:

```
[B]
# Password to access ESXi servers.
$USER6$=your-esxi-password-here
[/B]
```To add this command to an ESXi configuration file, add the following to its config file:

/etc/nagios/servers/srv-esxi1.cfg
```
[B]
define service{
        use                             generic-service
        host_name                       [COLOR=red]srv-esxi1[/COLOR]
        service_description             Server Health
        check_command                   check_esxi_hardware![COLOR=red]your-esxi-userid-here[/COLOR]!$USER6$!ibm
        }
[/B]
```Now it is time to create the script:

```
[B]
touch /usr/local/nagios/libexec/check_esxi_hardware.py
chown nagios:nagios /usr/local/nagios/libexec/check_esxi_hardware.py
chmod 0755 /usr/local/nagios/libexec/check_esxi_hardware.py
vi /usr/local/nagios/libexec/check_esxi_hardware.py
[/B]
```/usr/local/nagios/libexec/check_esxi_hardware.py
```

#!/usr/bin/python
# -*- coding: UTF-8 -*-
#
# Script for checking global health of host running VMware ESX/ESXi
#
# Licence : GNU General Public Licence (GPL) http://www.gnu.org/
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA
# 02110-1301, USA.
#
# Pre-req : pywbem
#
# Copyright (c) 2008 David Ligeret
# Copyright (c) 2009 Joshua Daniel Franklin
# Copyright (c) 2010 Branden Schneider
# Copyright (c) 2010-2012 Claudio Kuenzler
# Copyright (c) 2010 Samir Ibradzic
# Copyright (c) 2010 Aaron Rogers
# Copyright (c) 2011 Ludovic Hutin
# Copyright (c) 2011 Carsten Schoene
# Copyright (c) 2011-2012 Phil Randal
# Copyright (c) 2011 Fredrik Aslund
# Copyright (c) 2011 Bertrand Jomin
# Copyright (c) 2011 Ian Chard
# Copyright (c) 2012 Craig Hart
#
# The VMware 4.1 CIM API is documented here:
#
#   http://www.vmware.com/support/developer/cim-sdk/4.1/smash/cim_smash_410_prog.pdf
#
#   http://www.vmware.com/support/developer/cim-sdk/smash/u2/ga/apirefdoc/
#
# This Nagios plugin is maintained here:
# http://www.claudiokuenzler.com/nagios-plugins/check_esxi_hardware.php
#
#@---------------------------------------------------
#@ History
#@---------------------------------------------------
#@ Date   : 20080820
#@ Author : David Ligeret
#@ Reason : Initial release
#@---------------------------------------------------
#@ Date   : 20080821
#@ Author : David Ligeret
#@ Reason : Add verbose mode
#@---------------------------------------------------
#@ Date   : 20090219
#@ Author : Joshua Daniel Franklin
#@ Reason : Add try/except to catch AuthError and CIMError
#@---------------------------------------------------
#@ Date   : 20100202
#@ Author : Branden Schneider
#@ Reason : Added HP Support (HealthState)
#@---------------------------------------------------
#@ Date   : 20100512
#@ Author : Claudio Kuenzler www.claudiokuenzler.com
#@ Reason : Combined different versions (Joshua and Branden)
#@ Reason : Added hardware type switch (dell or hp)
#@---------------------------------------------------
#@ Date   : 20100626/28
#@ Author : Samir Ibradzic www.brastel.com
#@ Reason : Added basic server info
#@ Reason : Wanted to have server name, serial number & bios version at output
#@ Reason : Set default return status to Unknown
#@---------------------------------------------------
#@ Date   : 20100702
#@ Author : Aaron Rogers www.cloudmark.com
#@ Reason : GlobalStatus was incorrectly getting (re)set to OK with every CIM element check
#@---------------------------------------------------
#@ Date   : 20100705
#@ Author : Claudio Kuenzler www.claudiokuenzler.com
#@ Reason : Due to change 20100702 all Dell servers would return UNKNOWN instead of OK...
#@ Reason : ... so added Aaron's logic at the end of the Dell checks as well
#@---------------------------------------------------
#@ Date   : 20101028
#@ Author : Claudio Kuenzler www.claudiokuenzler.com
#@ Reason : Changed text in Usage and Example so people dont forget to use https://
#@---------------------------------------------------
#@ Date   : 20110110
#@ Author : Ludovic Hutin (Idea and Coding) / Claudio Kuenzler (Bugfix)
#@ Reason : If Dell Blade Servers are used, Serial Number of Chassis was returned
#@---------------------------------------------------
#@ Date   : 20110207
#@ Author : Carsten Schoene carsten.schoene.cc
#@ Reason : Bugfix for Intel systems (in this case Intel SE7520) - use 'intel' as system type
#@---------------------------------------------------
#@ Date   : 20110215
#@ Author : Ludovic Hutin
#@ Reason : Plugin now catches Socket Error (Timeout Error) and added a timeout parameter
#@---------------------------------------------------
#@ Date   : 20110217/18
#@ Author : Ludovic Hutin / Tom Murphy
#@ Reason : Bugfix in Socket Error if clause
#@---------------------------------------------------
#@ Date   : 20110221
#@ Author : Claudio Kuenzler www.claudiokuenzler.com
#@ Reason : Remove recently added Timeout due to incompabatility on Windows
#@ Reason : and changed name of plugin to check_esxi_hardware
#@---------------------------------------------------
#@ Date   : 20110426
#@ Author : Claudio Kuenzler www.claudiokuenzler.com
#@ Reason : Added 'ibm' hardware type (compatible to Dell output). Tested by Keith Erekson.
#@---------------------------------------------------
#@ Date   : 20110426
#@ Author : Phil Randal
#@ Reason : URLise Dell model and tag numbers (as in check_openmanage)
#@ Reason : Return performance data (as in check_openmanage, using similar names where possible)
#@ Reason : Minor code tidyup - use elementName instead of instance['ElementName']
#@---------------------------------------------------
#@ Date   : 20110428
#@ Author : Phil Randal (phil.randal@gmail.com)
#@ Reason : If hardware type is specified as 'auto' try to autodetect vendor
#@ Reason : Return performance data for some HP models
#@ Reason : Indent 'verbose' output to make it easier to read
#@ Reason : Use OptionParser to give better parameter parsing (retaining compatability with original)
#@---------------------------------------------------
#@ Date   : 20110503
#@ Author : Phil Randal (phil.randal@gmail.com)
#@ Reason : Fix bug in HP Virtual Fan percentage output
#@ Reason : Slight code reorganisation
#@ Reason : Sort performance data
#@ Reason : Fix formatting of current output
#@---------------------------------------------------
#@ Date   : 20110504
#@ Author : Phil Randal (phil.randal@gmail.com)
#@ Reason : Minor code changes and documentation improvements
#@ Reason : Remove redundant mismatched ' character in performance data output
#@ Reason : Output non-integral values for all sensors to fix problem seen with system board voltage sensors
#@          on an IBM server (thanks to Attilio Drei for the sample output)
#@---------------------------------------------------
#@ Date   : 20110505
#@ Author : Fredrik Aslund
#@ Reason : Added possibility to use first line of a file as password (file:)
#@---------------------------------------------------
#@ Date   : 20110505
#@ Author : Phil Randal (phil.randal@gmail.com)
#@ Reason : Simplfy 'verboseoutput' to use 'verbose' as global variable instead of as parameter
#@ Reason : Don't look at performance data from CIM_NumericSensor if we're not using it
#@ Reason : Add --no-power, --no-volts, --no-current, --no-temp, and --no-fan options
#@---------------------------------------------------
#@ Date   : 20110506
#@ Author : Phil Randal (phil.randal@gmail.com)
#@ Reason : Reinstate timeouts with --timeout parameter (but not on Windows)
#@ Reason : Allow file:passwordfile in old-style arguments too
#@---------------------------------------------------
#@ Date   : 20110507
#@ Author : Phil Randal (phil.randal@gmail.com)
#@ Reason : On error, include numeric sensor value in output
#@---------------------------------------------------
#@ Date   : 20110520
#@ Author : Bertrand Jomin
#@ Reason : Plugin had problems to handle some S/N from IBM Blade Servers
#@---------------------------------------------------
#@ Date   : 20110614
#@ Author : Claudio Kuenzler (www.claudiokuenzler.com)
#@ Reason : Rewrote file handling and file can now be used for user AND password
#@---------------------------------------------------
#@ Date   : 20111003
#@ Author : Ian Chard (ian@chard.org)
#@ Reason : Allow a list of unwanted elements to be specified, which is useful
#@          in cases where hardware isn't well supported by ESXi
#@---------------------------------------------------
#@ Date   : 20120402
#@ Author : Claudio Kuenzler (www.claudiokuenzler.com)
#@ Reason : Making plugin GPL compatible (Copyright) and preparing for OpenBSD port
#@---------------------------------------------------
#@ Date   : 20120405
#@ Author : Phil Randal (phil.randal@gmail.com)
#@ Reason : Fix lookup of warranty info for Dell
#@---------------------------------------------------
#@ Date   : 20120501
#@ Author : Craig Hart
#@ Reason : Bugfix in manufacturer discovery when cim entry not found or empty
#@---------------------------------------------------


import sys
import time
import pywbem
import re
import string
from optparse import OptionParser,OptionGroup

version = '20120501'

NS = 'root/cimv2'

# define classes to check 'OperationStatus' instance
ClassesToCheck = [
  'OMC_SMASHFirmwareIdentity',
  'CIM_Chassis',
  'CIM_Card',
  'CIM_ComputerSystem',
  'CIM_NumericSensor',
  'CIM_Memory',
  'CIM_Processor',
  'CIM_RecordLog',
  'OMC_DiscreteSensor',
  'OMC_Fan',
  'OMC_PowerSupply',
  'VMware_StorageExtent',
  'VMware_Controller',
  'VMware_StorageVolume',
  'VMware_Battery',
  'VMware_SASSATAPort'
]

sensor_Type = {
  0:'unknown',
  1:'Other',
  2:'Temperature',
  3:'Voltage',
  4:'Current',
  5:'Tachometer',
  6:'Counter',
  7:'Switch',
  8:'Lock',
  9:'Humidity',
  10:'Smoke Detection',
  11:'Presence',
  12:'Air Flow',
  13:'Power Consumption',
  14:'Power Production',
  15:'Pressure',
  16:'Intrusion',
  32768:'DMTF Reserved',
  65535:'Vendor Reserved'
}

data = []

perf_Prefix = {
  1:'Pow',
  2:'Vol',
  3:'Cur',
  4:'Tem',
  5:'Fan',
  6:'FanP'
}


# parameters

# host name
hostname=''

# user
user=''

# password
password=''

# vendor - possible values are 'unknown', 'auto', 'dell', 'hp', 'ibm', 'intel'
vendor='unknown'

# verbose
verbose=False

# Produce performance data output for nagios
perfdata=False

# timeout
timeout = 0

# elements to ignore (full SEL, broken BIOS, etc)
ignore_list=[]

# urlise model and tag numbers (currently only Dell supported, but the code does the right thing for other vendors)
urlise_country=''

# collect perfdata for each category
get_power   = True
get_volts   = True
get_current = True
get_temp    = True
get_fan     = True

# define exit codes
ExitOK = 0
ExitWarning = 1
ExitCritical = 2
ExitUnknown = 3

def urlised_server_info(vendor, country, server_info):
  #server_inf = server_info
  if vendor == 'dell' :
    # Dell support URLs (idea and tables borrowed from check_openmanage)
    du = 'http://support.dell.com/support/edocs/systems/pe'
    if (server_info is not None) :
      p=re.match('(.*)PowerEdge (.*) (.*)',server_info)
      if (p is not None) :
        md=p.group(2)
        if (re.match('M',md)) :
          md = 'm'
        server_info = p.group(1) + '<a href="' + du + md + '/">PowerEdge ' + p.group(2)+'</a> ' + p.group(3)
  elif vendor == 'hp':
    return server_info
  elif vendor == 'ibm':
    return server_info
  elif vendor == 'intel':
    return server_info

  return server_info

# ----------------------------------------------------------------------

def system_tag_url(vendor,country):
  url = {'xx':''}
  if vendor == 'dell':
    # Dell support sites
    supportsite = 'http://www.dell.com/support/troubleshooting/'
    dellsuffix = 'nodhs1/Index?t=warranty&servicetag='

    # warranty URLs for different country codes
    # EMEA
    url['at'] = supportsite + 'at/de/' + dellsuffix  # Austria
    url['be'] = supportsite + 'be/nl/' + dellsuffix  # Belgium
    url['cz'] = supportsite + 'cz/cs/' + dellsuffix  # Czech Republic
    url['de'] = supportsite + 'de/de/' + dellsuffix  # Germany
    url['dk'] = supportsite + 'dk/da/' + dellsuffix  # Denmark
    url['es'] = supportsite + 'es/es/' + dellsuffix  # Spain
    url['fi'] = supportsite + 'fi/fi/' + dellsuffix  # Finland
    url['fr'] = supportsite + 'fr/fr/' + dellsuffix  # France
    url['gr'] = supportsite + 'gr/en/' + dellsuffix  # Greece
    url['it'] = supportsite + 'it/it/' + dellsuffix  # Italy
    url['il'] = supportsite + 'il/en/' + dellsuffix  # Israel
    url['me'] = supportsite + 'me/en/' + dellsuffix  # Middle East
    url['no'] = supportsite + 'no/no/' + dellsuffix  # Norway
    url['nl'] = supportsite + 'nl/nl/' + dellsuffix  # The Netherlands
    url['pl'] = supportsite + 'pl/pl/' + dellsuffix  # Poland
    url['pt'] = supportsite + 'pt/en/' + dellsuffix  # Portugal
    url['ru'] = supportsite + 'ru/ru/' + dellsuffix  # Russia
    url['se'] = supportsite + 'se/sv/' + dellsuffix  # Sweden
    url['uk'] = supportsite + 'uk/en/' + dellsuffix  # United Kingdom
    url['za'] = supportsite + 'za/en/' + dellsuffix  # South Africa
    # America
    url['br'] = supportsite + 'br/pt/' + dellsuffix  # Brazil
    url['ca'] = supportsite + 'ca/en/' + dellsuffix  # Canada
    url['mx'] = supportsite + 'mx/es/' + dellsuffix  # Mexico
    url['us'] = supportsite + 'us/en/' + dellsuffix  # USA
    # Asia/Pacific
    url['au'] = supportsite + 'au/en/' + dellsuffix  # Australia
    url['cn'] = supportsite + 'cn/zh/' + dellsuffix  # China
    url['in'] = supportsite + 'in/en/' + dellsuffix  # India
    # default fallback
    url['xx'] = supportsite + 'us/en/' + dellsuffix  # default
  # elif vendor == 'hp':
  # elif vendor == 'ibm':
  # elif vendor == 'intel':

  return url.get(country,url['xx'])

# ----------------------------------------------------------------------

def urlised_serialnumber(vendor,country,SerialNumber):
  if SerialNumber is not None :
    tu = system_tag_url(vendor,country)
    if tu != '' :
      SerialNumber = '<a href="' + tu + SerialNumber + '">' + SerialNumber + '</a>'
  return SerialNumber

# ----------------------------------------------------------------------

def verboseoutput(message) :
  if verbose:
    print "%s %s" % (time.strftime("%Y%m%d %H:%M:%S"), message)

# ----------------------------------------------------------------------

def getopts() :
  global hosturl,user,password,vendor,verbose,perfdata,urlise_country,timeout,ignore_list,get_power,get_volts,get_current,get_temp,get_fan
  usage = "usage: %prog  https://hostname user password system [verbose]\n" \
    "example: %prog https://my-shiny-new-vmware-server root fakepassword dell\n\n" \
    "or, using new style options:\n\n" \
    "usage: %prog -H hostname -U username -P password [-V system -v -p -I XX]\n" \
    "example: %prog -H my-shiny-new-vmware-server -U root -P fakepassword -V auto -I uk\n\n" \
    "or, verbosely:\n\n" \
    "usage: %prog --host=hostname --user=username --pass=password [--vendor=system --verbose --perfdata --html=XX]\n"

  parser = OptionParser(usage=usage, version="%prog "+version)
  group1 = OptionGroup(parser, 'Mandatory parameters')
  group2 = OptionGroup(parser, 'Optional parameters')

  group1.add_option("-H", "--host", dest="host", help="report on HOST", metavar="HOST")
  group1.add_option("-U", "--user", dest="user", help="user to connect as", metavar="USER")
  group1.add_option("-P", "--pass", dest="password", \
      help="password, if password matches file:<path>, first line of given file will be used as password", metavar="PASS")

  group2.add_option("-V", "--vendor", dest="vendor", help="Vendor code: auto, dell, hp, ibm, intel, or unknown (default)", \
      metavar="VENDOR", type='choice', choices=['auto','dell','hp','ibm','intel','unknown'],default="unknown")
  group2.add_option("-v", "--verbose", action="store_true", dest="verbose", default=False, \
      help="print status messages to stdout (default is to be quiet)")
  group2.add_option("-p", "--perfdata", action="store_true", dest="perfdata", default=False, \
      help="collect performance data for pnp4nagios (default is not to)")
  group2.add_option("-I", "--html", dest="urlise_country", default="", \
      help="generate html links for country XX (default is not to)", metavar="XX")
  group2.add_option("-t", "--timeout", action="store", type="int", dest="timeout", default=0, \
      help="timeout in seconds - no effect on Windows (default = no timeout)")
  group2.add_option("-i", "--ignore", action="store", type="string", dest="ignore", default="", \
      help="comma-separated list of elements to ignore")
  group2.add_option("--no-power", action="store_false", dest="get_power", default=True, \
      help="don't collect power performance data")
  group2.add_option("--no-volts", action="store_false", dest="get_volts", default=True, \
      help="don't collect voltage performance data")
  group2.add_option("--no-current", action="store_false", dest="get_current", default=True, \
      help="don't collect current performance data")
  group2.add_option("--no-temp", action="store_false", dest="get_temp", default=True, \
      help="don't collect temperature performance data")
  group2.add_option("--no-fan", action="store_false", dest="get_fan", default=True, \
      help="don't collect fan performance data")

  parser.add_option_group(group1)
  parser.add_option_group(group2)

  # check input arguments
  if len(sys.argv) < 2:
    print "no parameters specified\n"
    parser.print_help()
    sys.exit(-1)
  # if first argument starts with 'https://' we have old-style parameters, so handle in old way
  if re.match("https://",sys.argv[1]):
    # check input arguments
    if len(sys.argv) < 5:
      print "too few parameters\n"
      parser.print_help()
      sys.exit(-1)
    if len(sys.argv) > 5 :
      if sys.argv[5] == "verbose" :
        verbose = True
    hosturl = sys.argv[1]
    user = sys.argv[2]
    password = sys.argv[3]
    vendor = sys.argv[4]
  else:
    # we're dealing with new-style parameters, so go get them!
    (options, args) = parser.parse_args()

    # Making sure all mandatory options appeared.
    mandatories = ['host', 'user', 'password']
    for m in mandatories:
      if not options.__dict__[m]:
        print "mandatory parameter '--" + m + "' is missing\n"
        parser.print_help()
        sys.exit(-1)

    hostname=options.host.lower()
    # if user has put "https://" in front of hostname out of habit, do the right thing
    # hosturl will end up as https://hostname
    if re.match('^https://',hostname):
      hosturl = hostname
    else:
      hosturl = 'https://' + hostname

    user=options.user
    password=options.password
    vendor=options.vendor.lower()
    verbose=options.verbose
    perfdata=options.perfdata
    urlise_country=options.urlise_country.lower()
    timeout=options.timeout
    ignore_list=options.ignore.split(',')
    get_power=options.get_power
    get_volts=options.get_volts
    get_current=options.get_current
    get_temp=options.get_temp
    get_fan=options.get_fan

  # if user or password starts with 'file:', use the first string in file as user, second as password
  if (re.match('^file:', user) or re.match('^file:', password)):
        if re.match('^file:', user):
          filextract = re.sub('^file:', '', user)
          filename = open(filextract, 'r')
          filetext = filename.readline().split()
          user = filetext[0]
          password = filetext[1]
          filename.close()
        elif re.match('^file:', password):
          filextract = re.sub('^file:', '', password)
          filename = open(filextract, 'r')
          filetext = filename.readline().split()
          password = filetext[0]
          filename.close()

# ----------------------------------------------------------------------

getopts()

# if running on Windows, don't use timeouts and signal.alarm
on_windows = True
os_platform = sys.platform
if os_platform != "win32":
  on_windows = False
  import signal
  def handler(signum, frame):
    print 'CRITICAL: Execution time too long!'
    sys.exit(ExitCritical)

# connection to host
verboseoutput("Connection to "+hosturl)
wbemclient = pywbem.WBEMConnection(hosturl, (user,password), NS)

# Add a timeout for the script. When using with Nagios, the Nagios timeout cannot be < than plugin timeout.
if on_windows == False and timeout > 0:
  signal.signal(signal.SIGALRM, handler)
  signal.alarm(timeout)

# run the check for each defined class
GlobalStatus = ExitUnknown
server_info = ""
bios_info = ""
SerialNumber = ""
ExitMsg = ""

# if vendor is specified as 'auto', try to get vendor from CIM
# note: the default vendor is 'unknown'
if vendor=='auto':
  c=wbemclient.EnumerateInstances('CIM_Chassis')
  man=c[0][u'Manufacturer']
  if re.match("Dell",man):
    vendor="dell"
  elif re.match("HP",man):
    vendor="hp"
  elif re.match("IBM",man):
    vendor="ibm"
  elif re.match("Intel",man):
    vendor="intel"
  else:
    vendor='unknown'

for classe in ClassesToCheck :
  verboseoutput("Check classe "+classe)
  try:
    instance_list = wbemclient.EnumerateInstances(classe)
  except pywbem.cim_operations.CIMError,args:
    if ( args[1].find('Socket error') >= 0 ):
      print "CRITICAL: %s" %args
      sys.exit (ExitCritical)
    else:
      verboseoutput("Unknown CIM Error: %s" % args)
  except pywbem.cim_http.AuthError,arg:
    verboseoutput("Global exit set to CRITICAL")
    GlobalStatus = ExitCritical
    ExitMsg = " : Authentication Error! "
  else:
    # GlobalStatus = ExitOK #ARR
    for instance in instance_list :
      sensor_value = ""
      elementName = instance['ElementName']
      elementNameValue = elementName
      verboseoutput("  Element Name = "+elementName)

      # Ignore element if we don't want it
      if elementName in ignore_list :
        verboseoutput("    (ignored)")
        continue

      # BIOS & Server info
      if elementName == 'System BIOS' :
        bios_info =     instance[u'Name'] + ': ' \
            + instance[u'VersionString'] + ' ' \
            + str(instance[u'ReleaseDate'].datetime.date())
        verboseoutput("    VersionString = "+instance[u'VersionString'])

      elif elementName == 'Chassis' :
        man = instance[u'Manufacturer']
    if man is None :
      man = 'Unknown Manufacturer'
        verboseoutput("    Manufacturer = "+man)
        SerialNumber = instance[u'SerialNumber']
        if SerialNumber:
          verboseoutput("    SerialNumber = "+SerialNumber)
        server_info = man + ' '
        if vendor != 'intel':
          model = instance[u'Model']
          if model:
            verboseoutput("    Model = "+model)
            server_info +=  model + ' s/n:'

      elif elementName == 'Server Blade' :
        SerialNumber = instance[u'SerialNumber']
        if SerialNumber:
          verboseoutput("    SerialNumber = "+SerialNumber)

      # Report detail of Numeric Sensors and generate nagios perfdata

      if classe == "CIM_NumericSensor" :
        sensorType = instance[u'sensorType']
        sensStr = sensor_Type.get(sensorType,"Unknown")
        if sensorType:
          verboseoutput("    sensorType = %d - %s" % (sensorType,sensStr))
        units = instance[u'BaseUnits']
        if units:
          verboseoutput("    BaseUnits = %d" % units)
        # grab some of these values for Nagios performance data
        scale = 10**instance[u'UnitModifier']
        verboseoutput("    Scaled by = %f " % scale)
        cr = int(instance[u'CurrentReading'])*scale
        verboseoutput("    Current Reading = %f" % cr)
        elementNameValue = "%s: %g" % (elementName,cr)
        ltnc = 0
        utnc = 0
        ltc  = 0
        utc  = 0
        if instance[u'LowerThresholdNonCritical'] is not None:
          ltnc = instance[u'LowerThresholdNonCritical']*scale
          verboseoutput("    Lower Threshold Non Critical = %f" % ltnc)
        if instance[u'UpperThresholdNonCritical'] is not None:
          utnc = instance[u'UpperThresholdNonCritical']*scale
          verboseoutput("    Upper Threshold Non Critical = %f" % utnc)
        if instance[u'LowerThresholdCritical'] is not None:
          ltc = instance[u'LowerThresholdCritical']*scale
          verboseoutput("    Lower Threshold Critical = %f" % ltc)
        if instance[u'UpperThresholdCritical'] is not None:
          utc = instance[u'UpperThresholdCritical']*scale
          verboseoutput("    Upper Threshold Critical = %f" % utc)
        #
        if perfdata:
          perf_el = elementName.replace(' ','_')

          # Power and Current
          if sensorType == 4:               # Current or Power Consumption
            if units == 7:            # Watts
              if get_power:
                data.append( ("%s=%g;%g;%g " % (perf_el, cr, utnc, utc),1) )
            elif units == 6:          # Current
              if get_current:
                data.append( ("%s=%g;%g;%g " % (perf_el, cr, utnc, utc),3) )

          # PSU Voltage
          elif sensorType == 3:               # Voltage
            if get_volts:
              data.append( ("%s=%g;%g;%g " % (perf_el, cr, utnc, utc),2) )

          # Temperatures
          elif sensorType == 2:               # Temperature
            if get_temp:
              data.append( ("%s=%g;%g;%g " % (perf_el, cr, utnc, utc),4) )

          # Fan speeds
          elif sensorType == 5:               # Tachometer
            if get_fan:
              if units == 65:           # percentage
                data.append( ("%s=%g%%;%g;%g " % (perf_el, cr, utnc, utc),6) )
              else:
                data.append( ("%s=%g;%g;%g " % (perf_el, cr, utnc, utc),5) )

      elif classe == "CIM_Processor" :
        verboseoutput("    Family = %d" % instance['Family'])
        verboseoutput("    CurrentClockSpeed = %dMHz" % instance['CurrentClockSpeed'])


      # HP Check
      if vendor == "hp" :
        if instance['HealthState'] is not None :
          elementStatus = instance['HealthState']
          verboseoutput("    Element HealthState = %d" % elementStatus)
          interpretStatus = {
            0  : ExitOK,    # Unknown
            5  : ExitOK,    # OK
            10 : ExitWarning,  # Degraded
            15 : ExitWarning,  # Minor
            20 : ExitCritical,  # Major
            25 : ExitCritical,  # Critical
            30 : ExitCritical,  # Non-recoverable Error
          }[elementStatus]
          if (interpretStatus == ExitCritical) :
            verboseoutput("GLobal exit set to CRITICAL")
            GlobalStatus = ExitCritical
            ExitMsg += " CRITICAL : %s " % elementNameValue
          if (interpretStatus == ExitWarning and GlobalStatus != ExitCritical) :
            verboseoutput("GLobal exit set to WARNING")
            GlobalStatus = ExitWarning
            ExitMsg += " WARNING : %s " % elementNameValue
          # Added the following for when GlobalStatus is ExitCritical and a warning is detected
          # This way the ExitMsg gets added but GlobalStatus isn't changed
          if (interpretStatus == ExitWarning and GlobalStatus == ExitCritical) : # ARR
            ExitMsg += " WARNING : %s " % elementNameValue #ARR
          # Added the following so that GlobalStatus gets set to OK if there's no warning or critical
          if (interpretStatus == ExitOK and GlobalStatus != ExitWarning and GlobalStatus != ExitCritical) : #ARR
            GlobalStatus = ExitOK #ARR



      # Dell, Intel, IBM and unknown hardware check
      elif (vendor == "dell" or vendor == "intel" or vendor == "ibm" or vendor=="unknown") :
        if instance['OperationalStatus'] is not None :
          elementStatus = instance['OperationalStatus'][0]
          verboseoutput("    Element Op Status = %d" % elementStatus)
          interpretStatus = {
            0  : ExitOK,            # Unknown
            1  : ExitCritical,      # Other
            2  : ExitOK,            # OK
            3  : ExitWarning,       # Degraded
            4  : ExitWarning,       # Stressed
            5  : ExitWarning,       # Predictive Failure
            6  : ExitCritical,      # Error
            7  : ExitCritical,      # Non-Recoverable Error
            8  : ExitWarning,       # Starting
            9  : ExitWarning,       # Stopping
            10 : ExitCritical,      # Stopped
            11 : ExitOK,            # In Service
            12 : ExitWarning,       # No Contact
            13 : ExitCritical,      # Lost Communication
            14 : ExitCritical,      # Aborted
            15 : ExitOK,            # Dormant
            16 : ExitCritical,      # Supporting Entity in Error
            17 : ExitOK,            # Completed
            18 : ExitOK,            # Power Mode
            19 : ExitOK,            # DMTF Reserved
            20 : ExitOK             # Vendor Reserved
          }[elementStatus]
          if (interpretStatus == ExitCritical) :
            verboseoutput("Global exit set to CRITICAL")
            GlobalStatus = ExitCritical
            ExitMsg += " CRITICAL : %s " % elementNameValue
          if (interpretStatus == ExitWarning and GlobalStatus != ExitCritical) :
            verboseoutput("GLobal exit set to WARNING")
            GlobalStatus = ExitWarning
            ExitMsg += " WARNING : %s " % elementNameValue
          # Added same logic as in 20100702 here, otherwise Dell servers would return UNKNOWN instead of OK
          if (interpretStatus == ExitWarning and GlobalStatus == ExitCritical) : # ARR
            ExitMsg += " WARNING : %s " % elementNameValue #ARR
          if (interpretStatus == ExitOK and GlobalStatus != ExitWarning and GlobalStatus != ExitCritical) : #ARR
            GlobalStatus = ExitOK #ARR
        if elementName == 'Server Blade' :
                if SerialNumber :
                        if SerialNumber.find(".") != -1 :
                                SerialNumber = SerialNumber.split('.')[1]


# Munge the ouptput to give links to documentation and warranty info
if (urlise_country != '') :
  SerialNumber = urlised_serialnumber(vendor,urlise_country,SerialNumber)
  server_info = urlised_server_info(vendor,urlise_country,server_info)

# Output performance data
perf = '|'
if perfdata:
  sdata=[]
  ctr=[0,0,0,0,0,0,0]
  # sort the data so we always get perfdata in the right order
  # we make no assumptions about the order in which CIM returns data
  # first sort by element name (effectively) and insert sequence numbers
  for p in sorted(data):
    p1 = p[1]
    sdata.append( ("P%d%s_%d_%s") % (p1,perf_Prefix[p1], ctr[p1], p[0]) )
    ctr[p1] += 1
  # then sort perfdata into groups and output perfdata string
  for p in sorted(sdata):
    perf += p

# sanitise perfdata - don't output "|" if nothing to report
if perf == '|':
  perf = ''

if GlobalStatus == ExitOK :
  print "OK - Server: %s %s %s%s" % (server_info, SerialNumber, bios_info, perf)

elif GlobalStatus == ExitUnknown :
  print "UNKNOWN: %s" % (ExitMsg) #ARR

else:
  print "%s- Server: %s %s %s%s" % (ExitMsg, server_info, SerialNumber, bios_info, perf)

sys.exit (GlobalStatus)

```Now test the script to make sure it works.

```
[B]
/usr/local/nagios/libexec/check_esxi_hardware.py -H 192.168.107.44 -U esxiuser -P esxipassword -V ibm
[/B]
```The final step is to verify that nothing is broken in the configuration:
```
[B]
/etc/nagios/verify.sh
[/B]
```If there were no errors or warnings, restart Nagios to load the new configuration:
```
[B]
/etc/init.d/nagios stop
/etc/init.d/nagios start
[/B]
```

---

### Post by LHammonds on 2012-05-28
[SIZE="5"]Monitoring MySQL Server[/SIZE]

The script will be executed on the remote Linux server so we will be making use of NRPE.

On the remote MySQL server, install the Nagios plugins, NRPE server and NRPE plugin as mentioned earlier for remote Linux servers.

An extra step to allow the check_mysql plugin to work is to grant the nagios user access to a database.  Rather than granting access to an existing database, let's create an empty database just for Nagios.

Type the following commands to create a nagios database, nagios user and read-only access to just the empty Nagios database:

```
[B]
mysql
CREATE DATABASE nagiosdb;
CREATE USER nagios;
SET PASSWORD FOR 'nagios'@'%'=PASSWORD('[COLOR="red"]nagios-password[/COLOR]');
GRANT SELECT ON nagiosdb.* TO nagios IDENTIFIED BY '[COLOR="red"]nagios-password[/COLOR]';
FLUSH PRIVILEGES;
exit
[/B]
```

Now see if the command will run on your server (before trying to test them remotely on the Nagios server)

```
[B]
/usr/lib/nagios/plugins/check_mysql -w 20 -c 10 -d nagiosdb -u nagios -p [COLOR="red"]nagios-password[/COLOR]
[/B]
```

Add the plugin to the trusted NRPE commands to be executed.  Edit **/etc/nagios/nrpe_local.cfg**

```
[B]
command[check_mysql]=/usr/lib/nagios/plugins/check_mysql -w 20 -c 10 -d nagiosdb -u nagios -p [COLOR="red"]nagios-password[/COLOR]
[/B]
```
Even though we are using a low-acces and read-only ID, the password is exposed in the config file so make sure the file ownership and permissions are set accordingly:
```
[B]
chown root:nagios /etc/nagios/nrpe_local.cfg
chmod 0640 /etc/nagios/nrpe_local.cfg
[/B]
```

The NRPE Server now needs to reload the configuration for the changes to take affect.
```
**/etc/init.d/nagios-nrpe-server reload**
```

On the Nagios server, add the following command to the remote MySQL Linux server's configuration file:

/etc/nagios/servers/srv-mysql.cfg
```
[B]
define service{
        use                             generic-service
        host_name                       [COLOR="red"]srv-mysql[/COLOR]
        service_description             Server Health
        check_command                   check_mysql
        }
[/B]
```

The final step is to verify that nothing is broken in the configuration:
```
[B]
/etc/nagios/verify.sh
[/B]
```

If there were no errors or warnings, restart Nagios to load the new configuration:
```
[B]
/etc/init.d/nagios stop
/etc/init.d/nagios start
[/B]
```

---

### Post by LHammonds on 2012-05-28
[SIZE="5"]Monitoring Remote Windows Servers[/SIZE]

Monitoring Windows Servers and Workstations will requiring installing a service if you need data better than a simple ping.

For this, we will be using [NSClient++]("http://www.nsclient.org/nscp/downloads").  In particular, we will be downloading the [Win32]("http://files.nsclient.org/x-0.3.x_STABLE/NSClient%2B%2B-0.3.9-Win32.zip") and [x64]("") "zip" files for version 0.3.9.

The reason why I chose ZIP files instead of the MSI files is that it is much more simple to configure and rollout.

Extract the Win32 ZIP file to C:\NSClient\ and edit **C:\NSClient\nsc.ini**

Uncomment the DLL files you will be using between lines 10 and 22.  For example:
```

FileLogger.dll
CheckSystem.dll
CheckDisk.dll
NSClientListener.dll
NRPEListener.dll
SysTray.dll
CheckEventLog.dll
CheckHelpers.dll
;CheckWMI.dll
CheckNSCP.dll

; Script to check external scripts and/or internal aliases.
CheckExternalScripts.dll

```

On line 56, set the password that will be required to access the remote functions.  For example:

```

password=[COLOR="red"]my-nsclient-password[/COLOR]

```

On the Nagios server, you will need to match this password in your resource file which will then be referenced in your server config file.
/etc/nagios/resources.cfg
```

$USER5$=[COLOR="red"]my-nsclient-password[/COLOR]

```

On line 62, set the IP of the Nagios server to limit access to just that host.  For example:

```

allowed_hosts=[COLOR="red"]192.168.107.21[/COLOR]

```

On line 67, tell it to use this file to obtain settings rather than the registry.

```

use_file=1

```

On line 100, set the IP of the Nagios server to limit access to just that host.  For example:

```

allowed_hosts=[COLOR="red"]192.168.107.21[/COLOR]

```

On line 104, set the port number that will be used for communication with Nagios via check_nt.  It would be wise to use a port other than the default.  This example is using the default port:

```

port=[COLOR="red"]12489[/COLOR]

```

On line 118, set the port number that will be used for communication with Nagios via check_nrpe.  It would be wise to use a port other than the default.  This example is using the default port:

```

port=[COLOR="red"]5666[/COLOR]

```

On line 134, enable SSL.  For example:

```

use_ssl=1

```

On line 144, set the IP of the Nagios server to limit access to just that host.  For example:

```

allowed_hosts=[COLOR="red"]192.168.107.21[/COLOR]

```

On line 244, enable the check for Windows Update script.  For example:

```

check_updates=check_updates.vbs

```

Now, to make rolling this out a snap, create a couple of batch files to install / remove the NSClient service:

C:\NSClient\service-install.bat
```
[B]
@ECHO OFF
NSClient++.exe -install
START NET START NSClientpp /WAIT
pause
[/B]
```

C:\NSClient\service-uninstall.bat
```
[B]
@ECHO OFF
START NET STOP NSClientpp /WAIT
NSClient++.exe -uninstall
pause
[/B]
```

Copy the C:\NSClient folder to a network share and then go to each Windows host you want to monitor and copy the folder to C:\NSClient and double-click the "Service-Install.bat" file.

You will also need to add rules to your firewall to allow communication from the Nagios server.

Inbound Rule Name: Nagios [COLOR="red"]12489[/COLOR] TCP
 - Check: Enabled
 - Action: Allow the connection
 - Protocol Type: TCP
 - Local Port: [COLOR="red"]12489[/COLOR]
 - Remote Port: All Ports
 - Profile: Domain
 - Local IP address: Any IP address
 - Remote IP address: These IP addresses: [COLOR="red"]192.168.107.21[/COLOR]

Inbound Rule Name: Nagios [COLOR="red"]5666[/COLOR] TCP
 - Check: Enabled
 - Action: Allow the connection
 - Protocol Type: TCP
 - Local Port: [COLOR="red"]5666[/COLOR]
 - Remote Port: All Ports
 - Profile: Domain
 - Local IP address: Any IP address
 - Remote IP address: These IP addresses: [COLOR="red"]192.168.107.21[/COLOR]

On the Nagios server, create or copy a Windows config file and make appropriate changes such as server name and IP.  See the Sample Windows config file posted earlier in the thread.

The final step is to verify that nothing is broken in the configuration:
```
[B]
/etc/nagios/verify.sh
[/B]
```

If there were no errors or warnings, restart Nagios to load the new configuration:
```
[B]
/etc/init.d/nagios stop
/etc/init.d/nagios start
[/B]
```

Rinse, lather repeat for the x64 version if you have 64-bit servers.

NOTE: The Win32 version will work on 64-bit servers.   The only problem is if you need to check for the existence of running processes such as Explorer.exe or Notepad.exe which are 64-bit. The Win32 client cannot properly detect 64-bit programs.

---

### Post by LHammonds on 2012-05-28
[SIZE="5"]Contacts[/SIZE]

It would be a good idea to define contact groups and associate services to them.  Further down, define your contacts and what contact groups they belong to.  This will make it easier to maintain, even if you have a small shop or grow to a large shop, maintenance is primarily handled at the contact level.

Here is an example of what I mean:

/etc/nagios/objects/contacts.cfg
```


###############################################################################
# CONTACTS.CFG - CONTACT/CONTACTGROUP DEFINITIONS
#
# Last Modified: 2012-05-25
###############################################################################

###############################################################################
#
# CONTACT GROUPS
#
###############################################################################

define contactgroup{
        contactgroup_name       windows-server-admins
        alias                   Windows Server Administrators
        }

define contactgroup{
        contactgroup_name       linux-server-admins
        alias                   Linux Server Administrators
        }

define contactgroup{
        contactgroup_name       windows-pc-admins
        alias                   Windows PC Administrators
        }

define contactgroup{
        contactgroup_name       ibm-bladecenter-admins
        alias                   IBM BladeCenter Administrators
        }

define contactgroup{
        contactgroup_name       network-admins
        alias                   Network Administrators
        }

define contactgroup{
        contactgroup_name       phone-admins
        alias                   Phone Administrators
        }

define contactgroup{
        contactgroup_name       printer-admins
        alias                   Printer Administrators
        }

define contactgroup{
        contactgroup_name       copier-admins
        alias                   Copier/Fax/Scanner Administrators
        }

###############################################################################
#
# CONTACTS
#
###############################################################################

define contact{
        contact_name    dirkdiggler-email
        use             generic-contact
        alias           Dirk Diggler
        email           dirk.diggler@mydomain.com
        contactgroups   windows-server-admins,windows-pc-admins,linux-server-admins,ibm-bladecenter-admins,network-admins,phone-admins,printer-admins,copier-admins
        }

define contact{
        contact_name    johndoe-email
        use             generic-contact
        alias           John Doe
        email           john.doe@mydomain.com
        contactgroups   windows-server-admins,windows-pc-admins,ibm-bladecenter-admins,network-admins,printer-admins,copier-admins
        }

define contact{
        contact_name    maryjane-email
        use             generic-contact
        alias           Mary Jane
        email           mary.jane@mydomain.com
        contactgroups   windows-server-admins,windows-pc-admins,network-admins,phone-admins,printer-admins,copier-admins
        }

define contact{
        contact_name    dirkdiggler-pager
        use             generic-pager
        alias           Dirk Diggler Pager
        pager           8005551234@txt.att.net
        }

define contact{
        contact_name    johndoe-pager
        use             generic-pager
        alias           John Doe Pager
        pager           8005555678@txt.att.net
        }

define contact{
        contact_name    maryjane-pager
        use             generic-pager
        alias           Mary Jane Pager
        pager           8005559876@txt.att.net
        }

```

[SIZE="5"]Timeperiods[/SIZE]

The /etc/nagios/objects/timeperiods.cfg file is fairly straight-forward.  You can make adjustments to what is defined as "work hours" and leave it at that or add in some custom settings depending on your situation.

[SIZE="5"]Templates[/SIZE]

The file is also fairly straight-forward.  You can use what is defined in there or make changes to them or add new templates as I have done.  In case you spotted references to them in earlier examples, I will share some of the custom ones here (this is only part of the entire file)

/etc/nagios/objects/templates.cfg
```

define host{
        name                            template-server-critical
        notifications_enabled           1
        check_period                    24x7
        check_interval                  5
        retry_interval                  1
        check_command                   check-host-alive
        max_check_attempts              10
        event_handler_enabled           1
        flap_detection_enabled          1
        failure_prediction_enabled      1
        process_perf_data               1
        retain_status_information       1
        retain_nonstatus_information    1
        notification_period             24x7
        notification_interval           120
        notification_options            d,u,r
        register                        0
        }

        name                            template-server-non-critical
        notifications_enabled           1
        check_period                    workhours
        check_interval                  5
        retry_interval                  1
        check_command                   check-host-alive
        max_check_attempts              10
        event_handler_enabled           1
        flap_detection_enabled          1
        failure_prediction_enabled      1
        process_perf_data               1
        retain_status_information       1
        retain_nonstatus_information    1
        notification_period             workhours
        notification_interval           120
        notification_options            d,u,r
        register                        0
        }

define host{
        name                    linux-server
        use                     template-server-critical
        contact_groups          linux-server-admins
        register                0
        }

define host{
        name                    esx-server
        use                     template-server-critical
        contact_groups          ibm-bladecenter-admins
        register                0
        }

define host{
        name                    toshiba-copier
        use                     template-server-non-critical
        notification_options    n
        contact_groups          copier-admins
        register                0
        }

define host{
        name                    wirelessap
        use                     template-server-non-critical
        notification_options    n
        contact_groups          network-admins
        register                0
        }

```

---

### Post by LHammonds on 2012-05-31
NOTICE: There appears to be some kind of bug with check_snmp on Ubuntu 12.04.  I have detailed notes in [this thread @ Nagios forums]("http://support.nagios.com/forum/viewtopic.php?f=7&t=5973").

My temporary solution to this will be to utilize NRPE and have a remote 10.04 server make all the SNMP checks for the switches.  Kind of an ugly solution at the moment but I do not want to downgrade my Nagios server to 10.04.  However, if my only remaining 10.04 server can get upgraded to 12.04 (because the app is what's holding it back right now), then I may be forced to re-configure this on a 10.04 server or forgo the sysUpTime, sysName, sysContact and sysLocation checks.

LHammonds

---

### Post by LHammonds on 2012-06-08
[SIZE="5"]Managing User Accounts[/SIZE]

It is recommended to replace the nagiosadmin with a different account and here is how you do it.

We are going to add 3 administrators with the same level of access as the nagiosadmin.

ID / Password: lhammonds / [COLOR="red"]abc123[/COLOR]
ID / Password: ddiggler / [COLOR="red"]jigglier69[/COLOR]
ID / Password: jdoe / [COLOR="red"]jlow9876[/COLOR]


[LIST=1]
[*]Login with your administrator account.  At the $ prompt, temporarily grant yourself super user privilages by typing **sudo su** [COLOR="green"]{ENTER}[/COLOR] and then provide the administrator password (**[COLOR="red"]myadminpass[/COLOR]**).
[*]Type the following commands to add the users to the web interface:
```
[B]
htpasswd /etc/nagios/htpasswd.users lhammonds
[COLOR="red"]abc123[/COLOR]
htpasswd /etc/nagios/htpasswd.users ddiggler
[COLOR="red"]jiggler69[/COLOR]
htpasswd /etc/nagios/htpasswd.users jdoe
[COLOR="red"]jlow9876[/COLOR]
[/B]
```
[*]Edit **/etc/nagios/cgi.cfg** and search/replace "nagiosadmin" with "lhammonds,ddiggler,jdoe"
For example, in VI, you type **:%s/nagiosadmin/lhammonds,ddiggler,jdoe/g"**
[*]Restart the apache service: **/etc/init.d/apache2 restart**
[*]Now open a web browser and go to **http://[COLOR="red"]192.168.107.21[/COLOR]/nagios** and see if you can login with your new accounts.  NOTE: There is no logout option, you will need to close the browser and re-open it to test different accounts.
[*]Once you have verified your accounts work, you can safely delete the nagiosadmin account by typing the following:
```
[B]
htpasswd -D /etc/nagios/htpasswd.users nagiosadmin
[/B]
```
[/LIST]


To fine-tune user accounts, you can add or remove them from the following permission branches in **/etc/nagios/cgi.cfg**

authorized_for_system_information
authorized_for_configuration_information
authorized_for_system_commands
authorized_for_all_services
authorized_for_all_hosts
authorized_for_all_service_commands
authorized_for_all_host_commands


[SIZE="5"]Custom Sounds[/SIZE]

Nagios allows custom WAV sounds to be played as alerts on the web page but does not come with any (that I could tell).  So I went through my audio collection and pulled out a few clips I thought would work good for the various event types.

Each audio clip was converted to WAV format and stereo turned into mono.

[Sound Pack #1]("http://www.4shared.com/archive/Cr5UBS_W/Nagios-Sound-Pack1.html") (37 files, 4.3 MB)
[Sound Pack #2]("http://www.4shared.com/archive/pJsbVw0v/Nagios-Sound-Pack2.html") (43 files, 7.6 MB)

To enable this, here is what you can do.

Edit **/etc/nagios/cgi.cfg**
Around line #313, you will find the following section commented out:
```

#host_unreachable_sound=host-unreachable.wav
#host_down_sound=host-down.wav
#service_critical_sound=critical.wav
#service_warning_sound=warning.wav
#service_unknown_sound=warning.wav
#normal_sound=noproblem.wav

```
I don't know about you but I tend to have services in the red all the time (WindowsUpdate) which tend to stay that way more often than not...so I would not be interested at all in service alert sounds.  However, I would like to have audible alerts for host issues and this is how I modified mine:
```

host_unreachable_sound=host-unreachable.wav
host_down_sound=host-down.wav
#service_critical_sound=critical.wav
#service_warning_sound=warning.wav
#service_unknown_sound=warning.wav
normal_sound=noproblem.wav

```
I then used the following files from my audio collection and copied them to my Samba share and moved/renamed them to the proper location.

Star Trek\command-path-discontinuity.wav
Star Trek\losing-power.wav
Star Trek\i-hate-prototypes.wav

On the server, I then typed these commands:
```
[B]
mv /srv/samba/share/command-path-discontinuity.wav /usr/local/nagios/share/media/host-unreachable.wav
mv /srv/samba/share/losing-power.wav /usr/local/nagios/share/media/host-down.wav
mv /srv/samba/share/i-hate-prototypes.wav /usr/local/nagios/share/media/noproblem.wav
chown nagios:nagios /usr/local/nagios/share/media/*.wav
chmod 0444 /usr/local/nagios/share/media/*.wav
[/B]
```
As long as your browser can play wav files, you will be able to hear any changes in host status while you leave your web browser on the nagios monitoring page.  I typically have mine on the tactical overview page.

---

### Post by Luc Comtois on 2012-07-04
LHammonds I followed you instruction to install Nagios on Ubuntu server 12.04 in vmware and I had the same problem with snmp.

I was able to get it working this is what have done:
```
cd /usr/share/mibs/netsnmp
wget ftp://ftp.cisco.com/pub/mibs/v2/SNMPv2-MIB.my
wget ftp://ftp.cisco.com/pub/mibs/v1/RFC1213-MIB.my
wget ftp://ftp.cisco.com/pub/mibs/v2/IANAifType-MIB.my
wget ftp://ftp.cisco.com/pub/mibs/v2/SNMPv2-TC.my
wget ftp://ftp.cisco.com/pub/mibs/v2/SNMPv2-SMI.my
echo "mibs +sysUpTime" >> /etc/snmp/snmp.conf

```

I hope this will help as much as you instruction helped me.

---

### Post by LHammonds on 2012-07-05
> **Luc Comtois said:**
> I was able to get it working this is what have done:
```
cd /usr/share/mibs/netsnmp
wget ftp://ftp.cisco.com/pub/mibs/v2/SNMPv2-MIB.my
wget ftp://ftp.cisco.com/pub/mibs/v1/RFC1213-MIB.my
wget ftp://ftp.cisco.com/pub/mibs/v2/IANAifType-MIB.my
wget ftp://ftp.cisco.com/pub/mibs/v2/SNMPv2-TC.my
wget ftp://ftp.cisco.com/pub/mibs/v2/SNMPv2-SMI.my
echo "mibs +sysUpTime" >> /etc/snmp/snmp.conf

```
Awesome!  These Cisco files did the trick.  I did not need to change anything in snmp.conf for the sysUpTime, sysLocation, sysName and sysContact to start working.

**EDIT:** It seems I can no longer edit my prior posts...thus it is pointless using these forums to build works-in-progress such as this.  I will have to use a different solution to hold my notes.

Thanks!
LHammonds

---

### Post by boatman on 2012-07-11
Your notes are rare, concise and accurate.

FYI on the NRPE plugin for i386 virtual machines.  The ssl lib is located.

--with-ssl-lib=/usr/lib/i386-linux-gnu

Instead of x86_64-linux-gnu

Thanks for you time.

---

### Post by LHammonds on 2012-07-11
> **boatman said:**
> Your notes are rare, concise and accurate.
 
FYI on the NRPE plugin for i386 virtual machines. The ssl lib is located.
 
--with-ssl-lib=/usr/lib/i386-linux-gnu
 
Instead of x86_64-linux-gnu
Thanks. I'll be sure to check this out and update my notes for the next place I put them. (Will be a little while...my company shipped me off to Georgia for a couple of weeks of training)
 
LHammonds

---

### Post by cg28oh on 2012-07-11
Hi,

Came across some trouble after following this process. Upon reboot, the /var/nagios/rw/nagios.cmd file in not present. If I do a stop/start, it shows up. I have tried a few solutions found through Google search and haven't found the problem. Has anyone seen this?

EDIT:
Looks like the nagios process is starting twice:

Jul 11 16:31:12 nagios: Nagios 3.4.1 starting... (PID=730)
Jul 11 16:31:12 nagios: Local time is Wed Jul 11 16:31:12 EDT 2012
Jul 11 16:31:12 nagios: LOG VERSION: 2.0
Jul 11 16:31:12 nagios: Finished daemonizing... (New PID=735)
Jul 11 16:31:14 nagios: Nagios 3.4.1 starting... (PID=993)
Jul 11 16:31:14 nagios: Local time is Wed Jul 11 16:31:14 EDT 2012
Jul 11 16:31:14 nagios: LOG VERSION: 2.0
Jul 11 16:31:14 nagios: Lockfile '/var/nagios/nagios.lock' looks like its already held by another instance of Nagios (PID 735).  Bailing out...

---

### Post by LHammonds on 2012-07-11
> **cg28oh said:**
> Hi,
 
Came across some trouble after following this process. Upon reboot, the /var/nagios/rw/nagios.cmd file in not present. If I do a stop/start, it shows up. I have tried a few solutions found through Google search and haven't found the problem. Has anyone seen this?
 
EDIT:
Looks like the nagios process is starting twice:
 
Jul 11 16:31:12 nagios: Nagios 3.4.1 starting... (PID=730)
Jul 11 16:31:12 nagios: Local time is Wed Jul 11 16:31:12 EDT 2012
Jul 11 16:31:12 nagios: LOG VERSION: 2.0
Jul 11 16:31:12 nagios: Finished daemonizing... (New PID=735)
Jul 11 16:31:14 nagios: Nagios 3.4.1 starting... (PID=993)
Jul 11 16:31:14 nagios: Local time is Wed Jul 11 16:31:14 EDT 2012
Jul 11 16:31:14 nagios: LOG VERSION: 2.0
Jul 11 16:31:14 nagios: Lockfile '/var/nagios/nagios.lock' looks like its already held by another instance of Nagios (PID 735). Bailing out...
I've installed Nagios several times and not seen this problem. Is this the 1st time you've installed Nagios or have you tried this multiple times and continue to get the same problem?
 
**EDIT:** You might want to look through your command history and see if you ran a setup command more than once...such as the install command (just a guess)

---

### Post by cg28oh on 2012-07-11
I think I found it. Went back to the Nagios Ubuntu quickstart guide. I first did 
```
update-rc.d -f nagios remove
```Then only: ```
ln -s /etc/init.d/nagios /etc/rcS.d/S99nagios
``` I did not use command: ```
/usr/sbin/update-rc.d -f nagios defaults 99
```> **LHammonds said:**
> I've installed Nagios several times and not seen this problem. Is this the 1st time you've installed Nagios or have you tried this multiple times and continue to get the same problem?
 
**EDIT:** You might want to look through your command history and see if you ran a setup command more than once...such as the install command (just a guess)

---

### Post by bpb_21 on 2012-07-14
> **LHammonds said:**
> It seems I can no longer edit my prior posts...thus it is pointless using these forums to build works-in-progress such as this.  I will have to use a different solution to hold my notes.

Thanks!
LHammonds

Let us know where you go to host your notes.  They are an invaluable resource and I'd love to see updates.

---

### Post by LHammonds on 2012-07-16
> **bpb_21 said:**
> Let us know where you go to host your notes.  They are an invaluable resource and I'd love to see updates.
They will most-likely be maintained on [my forums]("http://www.hammondslegacy.com/forum/viewforum.php?f=40") and when they have reached a mature state, will probably be copied to the Ubuntu wiki.

It may take a while to get them moved over to my forum since I'm currently out-of-state at a training camp. Once I get back, there will be about a month-solid of converting our electronic medical records (EMR) system to a different EMR system.

I have separated the base install of the Ubuntu server and will be re-vamping the other tutorials to simply reference the base install and make notes on what to modify from that installation to fit the needs for each application server that is setup...thus making each document a bit smaller by removing the redundant Ubuntu install steps.

LHammonds

---

### Post by LHammonds on 2012-07-17
I can no longer edit this thread...therefor, I have moved the thread (and all updates mentioned up to this point {thanks everyone} and future updates) to my own forum. Once I have all my documents settled down, I will see about getting help converting it to the wiki.

[My Notes for Installing Nagios on Ubuntu Server 12.04 LTS]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=194") @ HammondsLegacy.com

LHammonds

---

### Post by minja on 2012-08-17
Hi! Thank you very much for this guide. It's very good, precise and comprehensive. I took about two hours to install Nagios and all went perfect.

---

### Post by richardsith on 2012-08-20
thanks a lot to have realized a guide as perfect as that, it's been really useful for my job, thank you again

---

### Post by LHammonds on 2012-08-21
minja and richardsith, I'm glad it was helpful to you.

I'm almost through the rough part of my companies transition from several major systems to a completely new system.  I'll be taking off the rest of the week and hopefully will have some time to start working on cleaning up my tutorials to reference the generic Ubuntu server setup and focus on just the application notes (MySQL, Nagios, MediaWiki, etc.).

I'm also researching a solution for a low-energy device which will run Ubuntu Server 12.04 and XBMC and serve as media centers for each of my rooms...which will then connect to a central MySQL server.  This will serve movies, songs and pictures throughout my house.  Should have a really nice how-to document once that project is done!  Now if I can just convince my company they need a similar project (2 birds, 1 stone!)

LHammonds

---

### Post by richardsith on 2012-08-28
Hi LHammonds,

I was reviewing your notes, where you've reported the basic file shell for the switch you use two lines to indicate the templates:

define host{
        use             [COLOR="Red"]cisco-switch[/COLOR]
        host_name       SW-TX-FD
        alias           Texas Front Desk
        address         192.168.107.231
        hostgroups      switches
        parents         SW-TX-FD
        }

and its definition service:

define service{
        use                     [COLOR="Red"]switch-critical-service[/COLOR]
        host_name               SW-TX-IS,SW-TX-FD
        service_description     PING
        check_command           check_ping!200.0,20%!600.0,60%
        }

I'd would like to know if you had modified the templates.cfg file and added that 2 new definitions using those already present on the file coping generic-switch and generic-service? 
And then I'm using VirtualBox with GNS3 but the SNMP service set on a cisco switch Nagios reports always error.

---

### Post by LHammonds on 2012-08-29
Yes, I added those.  The hosts are mainly just organizational placeholders so I could go back and make tweaks just for those types of devices.  But for now, it is purely organizational.

Example:
```

define host{
        name                    wirelessap
        use                     generic-switch
        register                0
        }

define host{
        name                    summit-switch
        use                     generic-switch
        register                0
        }

define host{
        name                    cisco-switch
        use                     generic-switch
        register                0
        }

```For the services, I wanted to make a distinction in who gets notified based on the types of service and even have them broken out in critical and non-critical so we don't get notified after hours on non-critical equipment such as a wireless which nobody is using at night.

Example:
```

define service{
        name                            switch-critical-service
        use                             generic-service
        contact_groups                  network-admins
        notification_options            c
        notification_interval           60
        notification_period             24x7
        register                        0
        }

define service{
        name                            switch-noncritical-service
        use                             generic-service
        normal_check_interval           1440
#       contact_groups                  nocontact-admins
        notification_options            n
        notification_interval           1440
        notification_period             workhours
        register                        0
        }

```

---

### Post by richardsith on 2012-08-29
thanks a lot for the fast reply, now it's a bit clear.
see y at next question!!!!!

---

### Post by LHammonds on 2012-08-29
> **richardsith said:**
> thanks a lot for the fast replyYou're welcome.  It was just luck that I saw your reply.  I have way too many posts in threads on these forums to be able to keep up with them all.  The fastest way to get my attention would be to send me a PM with a link back to the thread/question.  The PM system sends me an email notification which then gets sent to my phone so I won't miss those.

LHammonds

---

### Post by inventsekar on 2012-09-04
Thanks a ton, LHammonds...
Nagios install gave me lot of troubles, a lot, really. 
your notes only saved me big time. very very appreciating your help on this...

---

### Post by chinnappan on 2012-09-06
[B]Hi team,

Please help me any one for to monitor the Fortigate Firewalls model in nagios server. I am realy new one for this tools .

Please posted one sample cfg file , or guide me 


appreciating your help 

Thanks
chinnappan[/B]

---

### Post by chinnappan on 2012-09-06
Hi team one more request for email notifications

I am able to send email from treminal but nagios notifications not working please guide me any one..

i am using sendmail using below commands

echo test |mail [email]jvanathu@xxx.com[/email] its working find but if any server is down i am not reciving email notifications 

please find my error logs

[1346961085] EXTERNAL COMMAND: SEND_CUSTOM_HOST_NOTIFICATION;CHN-Fortigate;3;Nagios Admin;need to down
[1346961085] HOST NOTIFICATION: nagiosadmin;CHN-Fortigate;CUSTOM (UP);notify-host-by-email;PING OK - Packet loss = 0%, RTA = 2.10 ms;Nagios Admin;need to down
[1346961085] Warning: Attempting to execute the command "/usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: CUSTOM\nHost: CHN-Fortigate\nState: UP\nAddress: 10.5.66.49\nInfo: PING OK - Packet loss = 0%, RTA = 2.10 ms\n\nDate/Time: Fri Sept 7 01:21:25 IST 2012\n" | /bin/mail -s "** CUSTOM Host Alert: CHN-Fortigate is UP **" nagios@localhost" resulted in a return code of 127.  Make sure the script or binary you are trying to execute actually exists...

---

### Post by LHammonds on 2012-09-06
That does not look like a Nagios problem and should really be in its own thread in order to get the right people to see it.

Make sure /bin/mail exists or is a link to a program that exists.

LHammonds

---

### Post by chinnappan on 2012-09-07
Thanks LHammonds for your hint,

issues with path we need to add /usr/bin/mail


greate guidence.:KS

---

### Post by indunair on 2012-09-09
Sir, I've performed the installation process as you've said but still when I run the verification command, I am getting an error saying "Executable file /usr/local/nagios/bin/nagios not found. ". Yes the bin folder hasn't been created in /usr/local/nagios..what should i do? Kindly reply..thankyou.

---

### Post by LHammonds on 2012-09-10
> **indunair said:**
> Sir, I've performed the installation process as you've said but still when I run the verification command, I am getting an error saying "Executable file /usr/local/nagios/bin/nagios not found. ". Yes the bin folder hasn't been created in /usr/local/nagios..what should i do? Kindly reply..thankyou.
You compiled this program from source...you tell it exactly where to go with the "configure" options.  On the 6th post of this thread, there is a line that reads as follows:

> Build and install Nagios Core:
```
[B]
./configure --sysconfdir=/etc/nagios --localstatedir=/var/nagios --prefix=/usr/local/nagios --with-nagios-user=nagios --with-nagios-group=nagios --with-command-group=nagcmd --with-mail=/usr/bin/sendemail
[/B]
```The **prefix=/usr/local/nagios** is where you told Nagios to install the binary files.  If they are not there, then that means it did not compile or you did not specify that path.

Look at your command history to see what you typed during install.  You can do this by typing:

```
vi ~/.bash_history
```Then type the following to search/find the key phrase:

```
/configure
```LHammonds

---

### Post by IvanMP on 2012-11-28
Hi all,

I have one question ... im trying to monitor Network equipment (routers and switches) but the check_snmp file does not exist in "/usr/local/nagios/libexec" ... i follow like you have write 

> "perl -MCPAN -e 'install Net::SNMP'
Configure as much as possible automatically? yes
aptitude -y install snmp"

and then i installing the plugins like 

> cd /tmp/nagios-plugins-1.4.16 
./configure --with-nagios-user=nagios --with-nagios-group=nagios 
make 
make install 

so what should do or where i get wrong how can i fix this and have snmp installed. Should i repeat the process perl -MCPAN -e install net::SNMP and reconfigure the plugins ./configure --...... ???

well i solved the problem tnx in advance 
i repeat the process and there it is :)

---

### Post by IvanMP on 2012-12-05
Hi,
in the /usr/local/nagios/libexec there is check_xxxx files or plugins but what about the plugins on [http://exchange.nagios.org/](http://exchange.nagios.org/) do i need to download them and if i do how to do that and install them ... i try downloading the [http://exchange.nagios.org/directory/Plugins/Hardware/Network-Gear/Cisco/check_snmp_cisco/details]check_snmp_cisco](http://exchange.nagios.org/directory/Plugins/Hardware/Network-Gear/Cisco/check_snmp_cisco/details]check_snmp_cisco) with wget but i get nothing ... i was using the document description of how to install nagios core and nagios plugins from source (quickstart quide) and i wonder if i miss somthing or not ... 

tnx in advance ....

---

### Post by Wasca on 2013-03-22
Hi  LHammonds

I have a simple question for you. 

In your srv-wiki.cfg file you have the following...

> ###############################################################################
#
# HOST DEFINITION
#
###############################################################################

define host{
        use             ubuntu-server
        host_name       srv-wiki
        alias           SRV-Wiki
        address         192.168.107.23
        hostgroups      ubuntu-servers
        contacts        linux-admin-pager
        parents         srv-esxi1
        }

What i can't figure out about this part is what is the "use   ubuntu-server" part pointing to? Is it some host template file? When I try to verify my config using the same setup as your example I get the following.

> Error: Template 'ubuntu-server' specified in host definition could not be not found (config file '/etc/nagios/servers/srv-masdev.cfg', starting on line 7)
   Error processing object config files!


Where is the template "ubuntu-server" and what does it look like?

Thanks

---

### Post by ally_uk on 2013-03-22
I am a Linux Noob but after reading this thread I have confused myself even more quick question regarding chmod 0775 why are there four characters I am reading a UNIX reference book and the command would be chmod 775 

I thought permissions were for Owner, Group and Others? 

Confused :P

---

### Post by maab2413 on 2013-04-09
Hello
I installed the plugins nagios, etc and it works ok.
Now try istalar SNMP4NAGIOS and when I run the command. / Configure gives error checking for snmp_sess_init ... no
Can anyone help?


Thanks to all

---

### Post by AmbiguousOutlier on 2013-04-09
> **ally_uk said:**
> I am a Linux Noob but after reading this thread I have confused myself even more quick question regarding chmod 0775 why are there four characters I am reading a UNIX reference book and the command would be chmod 775 

I thought permissions were for Owner, Group and Others? 

Confused :P

None, they are the same, the 0 just means there are no special modes.

---

### Post by ally_uk on 2013-04-22
I just would like to say major propz to Lhammonds very good website :) very insightful actually understand LVM now :)

---

### Post by LHammonds on 2013-05-22
> **Wasca said:**
> Hi  LHammonds

I have a simple question for you. 

In your srv-wiki.cfg file you have the following...
** SNIP **

What i can't figure out about this part is what is the "use    ubuntu-server" part pointing to? Is it some host template file? When I  try to verify my config using the same setup as your example I get the  following.
** SNIP **

Where is the template "ubuntu-server" and what does it look like?
Sorry for the late reply.  I apparently lost all my thread subscriptions (now corrected and will be notified in the future)

Yes, that is a template.  It is practically the same as the default host template.  I simply made a copy of it and gave it that name for the purpose of grouping Ubuntu servers together and keeping them separate from Windows servers.  I even have Windows servers grouped by version number such as Windows-2000, Windows-2003, Windows-2008, etc.  I don't have an Ubuntu-10 / Ubuntu 12 distinction because I try to keep the servers up-to-date and not let any lag behind.  It is fairly impossible to do with Windows servers since I have little control over the apps installed on them which are typically specific to the version number.

Having them separated in logical divisions allows me to run interesting reports to compare things such as what kinds of servers typically have the best uptime and such.

LHammonds

---

### Post by jason35 on 2013-09-11
Thanks Lhammonds for taking your time to share your notes on this.

---

### Post by jebenastranka on 2013-11-26
hi,

Is there any way that you could implement nsca in to your notes? Because every notes that you do they just work perfectly :)

regards

---

### Post by abizmo on 2013-11-27
> **LHammonds said:**
> 
...
[*]To mount this system for backups, type the following command:
```
[B]
mount -t cifs //srv-backup/nagios /mnt/backup --options nouser,rw,nofail,noatime,noexec,credentials=/etc/cifspw
[/B]
```
....


Hi, first of all nice guide! It's so complete.

I'm having some problems with my samba server. I have done all your steps and when i send the mount command, it returns "mount error(5): Input/output error". I have checked the server (Windows 7) and there are a successful login and automatic logout. Do you know why? How can i fixed? 
I have to remove "noatime" because of invalid argument message.

Thank you,

---

### Post by LHammonds on 2014-01-10
> **jebenastranka said:**
> Is there any way that you could implement nsca in to your notes? Because every notes that you do they just work perfectly
Thanks.  I only have time to document what I implement.  If I ever use nsca, I'll be sure to include it in an update.

> **abizmo said:**
> Hi, first of all nice guide! It's so complete.

I'm having some problems with my samba server. I have done all your steps and when i send the mount command, it returns "mount error(5): Input/output error". I have checked the server (Windows 7) and there are a successful login and automatic logout. Do you know why? How can i fixed? 
I have to remove "noatime" because of invalid argument message.
Thanks.  Yes, the latest version of Samba no longer recognizes noatime so that would be good to remove.  Not sure what else would need to be modified other than that based on my notes though.

LHammonds

---

