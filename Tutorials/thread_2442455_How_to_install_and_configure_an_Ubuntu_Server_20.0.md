---
title: "How to install and configure an Ubuntu Server 20.04 LTS"
date: 2020-05-03
forum: Tutorials
---

### Post by LHammonds on 2020-05-03
[SIZE=4][COLOR=red]WARNING: This documentation will be based on the "legacy" version of 20.04.[/COLOR][/SIZE]

[SIZE=4][COLOR=red]NOTE: This documentation was developed using the "legacy" CD image for Ubuntu Server 20.04 which seems just like the 18.04 traditional installer but seems to be hidden from the download menus and being phased out.[/COLOR][/SIZE]

Greetings and salutations,

I hope this thread will be helpful to those who follow in my foot steps as well as getting any advice based on what I have done / documented.

Link to original post: [HammondsLegacy Forums]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=273")

[SIZE=4]High-level overview[/SIZE]
 
This document will cover installation of a dedicated Ubuntu server. This will be the "base" installation of the server as a prerequisite for other documents that will build upon it (e.g. MariaDB, Apache, MediaWiki, etc.). The server will be installed inside a virtual machine using vSphere running on ESXi servers. Notes will also be supplied for doing the same thing for Oracle's VirtualBox on a Windows 10 PC. Although there are some VMware-specific and VirtualBox-specific steps, they are very few and the majority of this documentation will work for other Virtual Machines or even directly installed onto a physical machine (e.g. bare-metal install).
 
This document will also cover some custom scripts to help automate tasks such as backing up, automatically growing the file system when free space is low, etc.
 
[SIZE=4]Tools utilized in this process[/SIZE]


[LIST]
[*][Ubuntu Server]("http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/") 20.04 LTS, 64-bit (legacy build) 
[*][Portable PuTTY]("http://portableapps.com/apps/internet/putty_portable") 0.73 
[*][VMware vSphere]("http://www.vmware.com/products/vsphere/overview.html") 6.0.0 
[*][VirtualBox]("http://www.virtualbox.org/") 6.0.20 
[*][SystemRestoreCD]("http://sourceforge.net/projects/systemrescuecd/") 6.1.3 
[/LIST]

[SIZE=4]Helpful links[/SIZE]
 
The list below are sources of information that helped me configure this system as well as some places that might be helpful to me later on as this process continues.


[LIST]
[*][Learning Linux]("http://blog.jdpfu.com/2014/12/28/learning-linux") 
[*][Ubuntu Documentation]("https://help.ubuntu.com") 
[*][Ubuntu Firewall Basics]("https://help.ubuntu.com/community/IptablesHowTo#Disabling%20the%20firewall") 
[*][Ubuntu AppArmor Basics]("https://help.ubuntu.com/community/AppArmor#Disable%20AppArmor%20framework") 
[/LIST]

[SIZE=4]Assumptions[/SIZE]

This documentation will need to make use of some very-specific information that will most-likely be different for each person / location. This variable data will be noted in this section and highlighted in red throughout the document as a reminder that you should plug-in your own value rather than actually using these "place-holder" values.

Under no circumstance should you use the actual values listed below. They are place-holders for the real thing. This is just a checklist template you need to have answered before you start the install process.

Wherever you see [COLOR=red]RED[/COLOR] in this document, you need to substitute it for what your company uses.


[LIST]
[*]Ubuntu Server name: [COLOR=red]srv-ubuntu[/COLOR] 
[*]Internet domain: [COLOR=red]mydomain.com[/COLOR] 
[*]Ubuntu Server IP address: [COLOR=red]192.168.107.2[/COLOR] 
[*]Ubuntu Server IP subnet mask: [COLOR=red]255.255.255.0[/COLOR] 
[*]Ubuntu Server IP gateway: [COLOR=red]192.168.107.1[/COLOR] 
[*]Internal DNS Server 1: [COLOR=red]192.168.107.212[/COLOR] 
[*]Internal DNS Server 2: [COLOR=red]192.168.107.213[/COLOR] 
[*]External DNS Server 1: [COLOR=red]1.1.1.1[/COLOR] (Cloudflare) 
[*]External DNS Server 2: [COLOR=red]8.8.8.8[/COLOR] (Google) 
[*]Ubuntu Admin ID: [COLOR=red]administrator[/COLOR] 
[*]Ubuntu Admin Password: [COLOR=red]myadminpass[/COLOR] 
[*]Email Server (remote): [COLOR=red]192.168.107.25[/COLOR] 
[*]Windows Share ID: [COLOR=red]myshare[/COLOR] 
[*]Windows Share Password: [COLOR=red]mysharepass[/COLOR] 
[/LIST]

It is also assumed that the reader knows how to use the VI editor. If not, you will need to [beef up your skill set]("http://www.washington.edu/computing/unix/vi.html") or use a different editor in place of it.  The vim-nox package that is installed later includes "vimtutor" which is also a good place to learn how to use the vi editor.

---

### Post by LHammonds on 2020-05-03
[SIZE=4]Analysis and Design[/SIZE]

The Ubuntu Server Long-Term Support (LTS) is great choice for companies because it is a solid operating system that happens to be free. If professional support is needed, there is an option to buy support for the Long-Term Support (LTS) versions of the operating system.

The large decision over the configuration of Ubuntu is how the hard drive space is sliced up (partitioned). This documentation will focus on partitioning the drives in such a way that it allows for growth depending on what is needed for the specific application.

This following design allows for dynamic growth and fine-tuning if need be. Being caught offguard with a scenario where space is filled up with no immediate option other than deleting files is never a good thing. Long-term life and growth of the system as well as budgeting concerns have to be taken into consideration.

Isolating the root volume to mainly just static data that will not grow much over time is the central concern. Pushing the other folders into their own volumes will be done so their dynamic growth will not affect the root partition. Filling up the root volume on a *nix system is a very bad thing and should be avoided at all costs. The file systems will also not take up 100% of the logical volume. This will allow the file systems (through automated scripts) to grow as needed and give the administrators some time to add more drives if necessary or shrink other volumes to get more space.

The volumes will initially be sliced up as follows:



[LIST]
[*]**boot** - This will remain static in size. It is also the only space residing outside the Logical Volume Manager (LVM) 
[*]**root volume** - Operating system and everything else which should remain fairly static. 
[*]**home volume** - This is where personal files will be stored but likely not be used in most server configurations. 
[*]**tmp volume** - This location will be used for temporary storage. Size should be adjusted to match however it is being used. 
[*]**var volume** - This is the app/database/log storage and will continue to grow over time. 
[*]**bak volume** - This will contain a local backup of the server/applications/data. So space needs to be about double the size of your application data (typically double the /var and /opt size). 
[*]**Offsite Storage** - This will be handled elsewhere but will be mounted on this server. 
[/LIST]

The partitions will be increased later as needed but will start off with a minimum size.
 
To get a good idea of the initial hard drive layout and to understand the process better, here is a graphical representation of the initial design for the server:

[IMG]https://images.hammondslegacy.com/linux/UbuntuHDPartitionDesign-Base20.png[/IMG]
 
These numbers will be used for the initial build of the system:
 
boot = 1 GB
root = 5 GB
home = 0.2 GB
tmp = 0.5 GB
var = 2.0 GB
bak = 0.5 GB

[SIZE=4]Important information[/SIZE] 


[LIST]
[*]When the logical volumes and file systems are initially created, they consume the maximum amount of space allocated which means the file system size will initially equal the logical volume size. These partition sizes above are artificially small for that reason. These will be later modified so that the logical volume will be larger than the file system so that the file system has room to expand when needed in a safe and automated manner. 
[*]If you want, you can initially allocate a larger disk such as a 50 GB drive rather than adding the 2nd and 3rd disk as noted in these steps.  These are just examples on how to manage and expand your storage when needed. 
[*]The /tmp folder is strictly temporary. By default, each time the server reboots, this folder is deleted and re-created. 
[*]The /bak folder will retain the most recent backup and is considered the "local" copy of the backup. 
[/LIST]

 
[SIZE=4]VMware Virtual Machine Settings[/SIZE]


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
[*]Create a Disk: 25 GB, No thin provisioning, No cluster features, Store with the virtual machine 
[*]Advanced Options: Virtual Device Node = SCSI (0:0) 
[*]Remove Floppy Drive 
[*]Mount CD/DVD Drive to Ubuntu ISO (**[COLOR=red]ubuntu-20.04-legacy-server-amd64.iso[/COLOR]**). Make sure CD/DVD is set to **Connect at power on** 
[*]Set boot options to Force BIOS Setup so you can set CDROM to boot before the Hard Disk 
[/LIST]

[SIZE=4]VirtualBox Virtual Machine Settings[/SIZE]


[LIST]
[*]Name: [COLOR=red]**srv-ubuntu**[/COLOR] 
[*]Operating System: Linux 
[*]Version: Ubuntu (64 bit) 
[*]Memory: 1024 MB 
[*]Check - Start-up Disk
- Create new hard disk
- VMDK
- Dynamically allocated
- Size: 25 GB 
[*]Select [COLOR=red]**srv-ubuntu**[/COLOR] and click Settings (**CTRL+S**)
- System, Processor, Enable PAE/NX
- Network, Attached to: Bridged Adapter, Advanced, Adapter Type: Intel PRO/1000 MT Server
- Storage, IDE Controller, Choose a virtual CD/DVD disk file, [COLOR=red]**ubuntu-20.04-legacy-server-amd64.iso**[/COLOR] 
[/LIST]

[SIZE=4]Install PuTTY[/SIZE]
 
When running inside a virtual machine, the response time for screen refreshes can be painfully slow to view man (manual) pages and navigating in VI (text editor). However, when using PuTTY via SSH, it is a far better solution for your Ubuntu console because it handles the screen draws much faster when scrolling and allows copying and pasting text between windows.
 
For example, selecting and copying a command in this document and then right-clicking in the PuTTY window will paste the command and have it ready to execute. Any text/lines highlighted with the mouse will be automatically copied into clipboard memory.
 
Download the portable edition and run the install...except it does not really "install" like a normal program, it simply extracts to a specified folder and will run from that folder even if you put it on a USB stick and carry over to a new computer (requires no install to run and thus leaves no footprint on your system)
 


[LIST=1]
[*]Start PuTTY 
[*]Under Window - Translation - Remote character set, select **UTF-8** 
[*]Type the following and click the Save button:
Host Name: [COLOR=red]**SRV-Ubuntu**[/COLOR] (or the IP such as [COLOR=red]192.168.107.2[/COLOR])
Port: **22**
Connection type: **SSH**
Saved Sessions: [COLOR=red]**SRV-Ubuntu**[/COLOR] 
[*]Now all you have to do is double-click on the session and it will connect to your server (when online). 
[/LIST]

---

### Post by LHammonds on 2020-05-03
[SIZE=4]Install Ubuntu Server[/SIZE]

NOTE: During the setup process throughout this entire document, most commands will require "sudo" as a prefix. However, this document will be using "sudo su" to temporarily gain root privileges so that subsequent commands will work without the need for the "sudo" prefix.



[LIST=1]
[*]Power on the Virtual Machine (VM) 
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *English* 
[*]Select *Install Ubuntu Server* [COLOR=green]{ENTER}[/COLOR] 
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *English* 
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *United States* 
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *do not detect keyboard layout* 
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *English (US)* 
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept *English (US)* 
[*]Type **[COLOR=red]srv-ubuntu[/COLOR]** [COLOR=green]{ENTER}[/COLOR] (this is your hostname) 
[*]Type **[COLOR=red]Administrator[/COLOR]**, [COLOR=green]{ENTER}[/COLOR] for the full name 
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept the default of the lowercase name of **[COLOR=red]administrator[/COLOR]** 
[*]Type **[COLOR=red]myadminpass[/COLOR]**, [COLOR=green]{ENTER}[/COLOR], **[COLOR=red]myadminpass[/COLOR]**, [COLOR=green]{ENTER}[/COLOR] 
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept detected time zone (*America/Chicago*) 
[*]Select *Manual* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *SCSI3 (0,0,0) (sda) - 26.8 GB VMware Virtual disk* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Yes* to create new empty partition table, [COLOR=green]{ENTER}[/COLOR] 
[*]Select *pri/log 26.8 GB FREE SPACE* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Create a new partition* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **1G**, [COLOR=green]{ENTER}[/COLOR] (NOTE: This will be the /boot partition) 
[*]Select *Primary* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Beginning* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Mount point: /* [COLOR=green]{ENTER}[/COLOR] 
[*]Select */boot - static files of the boot loader* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Label:* and type **boot** and press [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Bootable flag: off* [COLOR=green]{ENTER}[/COLOR] (NOTE: This toggles it on) 
[*]Select *Done setting up the partition* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Configure the Logical Volume Manager* [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Yes* to write change to disks and configure LVM, [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Create volume group* [COLOR=green]{ENTER}[/COLOR] 
[*]Type **LVG** [COLOR=green]{ENTER}[/COLOR] 
[*]Select */dev/sda free #1 (25843MB; FREE SPACE)*, [COLOR=green]{SPACEBAR}[/COLOR], [COLOR=green]{ENTER}[/COLOR] 
[*]Select *Yes* to write change to disks and configure LVM, [COLOR=green]{ENTER}[/COLOR] 
[*]At this point, you need to loop through this menu selecting the same options but different values, here is the short list of options/values:
[LIST]
[*]*Create logical volume*, select LVG, type **root**, type **5G** 
[*]*Create logical volume*, select LVG, type **var**, type **2G** 
[*]*Create logical volume*, select LVG, type **tmp**, type **0.5G** 
[*]*Create logical volume*, select LVG, type **bak**, type **0.5G** 
[*]*Create logical volume*, select LVG, type **home**, type **0.2G** 
[/LIST]
  
[*]Select *Finish* [COLOR=green]{ENTER}[/COLOR] 
[*]At this point, you need to loop through this menu selecting the same options but different values, here is the short list of options/values:
[LIST]
[*]Directly under *LVM VG LVG, LV root*, *Ext4 journaling file system*, Mount point: */ - the root file system*, Label: **root** 
[*]Directly under *LVM VG LVG, LV var*, *Ext4 journaling file system*, Mount point: */var - variable data*, Label: **var** 
[*]Directly under *LVM VG LVG, LV tmp*, *Ext4 journaling file system*, Mount point: */tmp - temporary files*, Label: **tmp** 
[*]Directly under *LVM VG LVG, LV bak*, *Ext4 journaling file system*, Mount point: */bak - Enter manually*, Label: **bak** 
[*]Directly under *LVM VG LVG, LV home*, *Ext4 journaling file system*, Mount point: */home - user home directories*, Label: **home** 
[/LIST]
  
[*]Here is what the screen looks like at this point: [Partitions]("https://images.hammondslegacy.com/linux/Ubuntu-LVM-Partitions20a.png") 
[*]Select *Finish partitioning and write changes to disk* [COLOR=green]{ENTER}[/COLOR] 
[*]Here is what the screen looks like at this point: [Partitions]("https://images.hammondslegacy.com/linux/Ubuntu-LVM-Partitions20b.png") 
[*]Select *Yes* to write changes to disk, [COLOR=green]{ENTER}[/COLOR] 
[*]Press [COLOR=green]{ENTER}[/COLOR] to accept a blank line for the HTTP proxy 
[*]Select *No automatic updates*, [COLOR=green]{ENTER}[/COLOR]  (* We will schedule a script for this later *) 
[*]Set the following and press [COLOR=green]{ENTER}[/COLOR] to continue:
Uncheck - DNS server
Uncheck - LAMP server
Uncheck - Mail server
Uncheck - PostgreSQL database
Uncheck - Print server
Uncheck - Samba file server
**Check** - OpenSSH server (allows us to use PuTTY after installation to connect to the server) 
[*]Select *Yes*, [COLOR=green]{ENTER}[/COLOR] to install GRUB boot loader to the master boot record 
[*]Installation Complete - from the VM menu, select VM --> Edit Settings and select *CD/DVD Drive 1* and change to "Client Device" which will effectively remove the ISO. Now press [COLOR=green]{ENTER}[/COLOR] to reboot. 
[/LIST]

---

### Post by LHammonds on 2020-05-03
[SIZE=4]Initial Configurations[/SIZE]


[LIST=1]
[*]At the login prompt, login with your administrator account ([COLOR=red]**administrator**[/COLOR] / [COLOR=red]**myadminpass**[/COLOR]) 
[*]If you made a mistake labeling any of the partitions, you can list them and make changes with the following example commands:
```
blkid | grep LABEL
sudo e2label /dev/sda1 boot
sudo e2label /dev/mapper/LVG-root root
sudo e2label /dev/mapper/LVG-var var
sudo e2label /dev/mapper/LVG-tmp tmp
sudo e2label /dev/mapper/LVG-bak bak
sudo e2label /dev/mapper/LVG-home home
``` 
[*]Edit the network configuration file:
```
sudo vi /etc/netplan/01-netcfg.yaml
``` 
[*]Change the Ethernet interface: (We need to change it from using DHCP to a static IP)
From:
```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      dhcp4: yes

```
To:
```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      dhcp4: false
      dhcp6: false
      addresses: [[COLOR=red]192.168.107.2/24[/COLOR]]
      gateway4: [COLOR=red]192.168.107.1[/COLOR]
      nameservers:
        addresses: [[COLOR=red]192.168.107.212,192.168.107.213,1.1.1.1,8.8.8.8[/COLOR]]

```
NOTE #1: The above YAML format is extremely sensitive to spaces.  Each indentation needs to be exactly 2 spaces.  Visit [NetPlan.io]("https://netplan.io/") for more information.

NOTE #2: The network card name (enp0s3) might be something different on your machine, be sure to use it instead of what I have.

NOTE #3: You may need to manually remove the DHCP record (lease) associated to this Ubuntu server from your DHCP server so the correct IP can be found by other machines on the network. This can be avoided by temporarily configuring the VM Network Adapter connection to be "Host Only Network" instead of "VM Network" so the server is isolated during setup...at least until you reach the testing of the static IP below.

NOTE #4: You might also need to manually add a HOST(A) record to your Windows DNS server (for [COLOR=red]srv-ubuntu.mydomain.com[/COLOR] and [COLOR=red]srv-ubuntu.work.mydomain.com[/COLOR]) 
[*]Verify that the configuration file syntax is good:
```
sudo netplan --debug generate
``` 
[*]If there were no errors, restart the network by typing the following:
```
sudo netplan --debug apply
``` 
[*]Sanity check! Type "**ip address**" and make sure the settings are correct. Then type **ping [www.google.com]("http://www.google.com")** or similar and see if ping works. 
[*]Make sure any file created by the root account is set to only be accessible to root by default:
```
echo 'umask 0077' >> ~/.bashrc
``` 
[*]Disable command history for the root user on production systems to prevent hackers from seeing the commands you have typed in the past which might expose passwords:
```
echo 'set +o history' >> ~/.bashrc
``` 
[*]Make sure menus will correctly draw lines instead of displaying ascii codes:
```
echo 'export NCURSES_NO_UTF8_ACS=1' >> ~/.bashrc
``` 
[*]Shutdown and power off the server:
```
sudo shutdown -P now
``` 
[*]At this point forward, you can use PuTTY to access the console rather than the console itself for better performance, ability to scroll, etc. 
[*]In VM menu, select VM --> Snapshot --> Take Snapshot. Give it a name like **STEP 1** and description of **Ubuntu Server 20.04 LTS, Clean install, Static IP: [COLOR=red]192.168.107.2[/COLOR]** and click **OK** 
[*]NOTE: Please remember to delete all snapshots when you are 100% done with the setup and happy with the results.  Not deleting snapshots can secretly consume all your storage space over time.  These snapshots are only there so you can revert back to a prior step quickly and easily without the need to completely re-install. 
[/LIST]


[SIZE=4]Add more SUDO users and lockdown SSH[/SIZE]

The root user is locked by default which is good.  When you installed the server, you created the [COLOR=red]administrator[/COLOR] account which can run sudo commands as root.  Let's add one more user that can use SUDO and ensure only these user accounts can login via SSH to the server.

Create a new user called "newadmin"
```
sudo adduser newadmin
```
Now add them to the SUDO group which will allow them to use the SUDO command.
```
sudo usermod -aG sudo newadmin
```

Now modify SSH service to only allow these 2 users to login via SSH.

```
sudo vi /etc/ssh/sshd_config
```

Add the following line anywhere in the file:
```
AllowUsers administrator newadmin
```

Reload the SSH config for the change to take affect:
```
sudo systemctl reload sshd
```

Now only administrator and newadmin can login to the server via SSH.  If you create another user, that user will not be able to login even with the correct password.  It will just say "Access denied."

The firewall and fail2ban sections later on will further increase SSH security.

You can also use SSH key-based authentication and disable user/password authentication.

[SIZE=4]Operating System Patches[/SIZE]
 


[LIST=1]
[*]Start the Ubuntu server and connect using PuTTY. 
[*]At the login prompt, login with your administrator account ([COLOR=red]**administrator**[/COLOR] / [COLOR=red]**myadminpass**[/COLOR]) 
[*]Install the patches by typing the following commands:
```
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
``` 
[*]Shutdown and power off the server by typing **shutdown -P now** 
[*]In VM menu, select VM --> Snapshot --> Take Snapshot. Give it a name like **STEP 2** and description of **Ubuntu Server 20.04 LTS, Patches applied, Static IP: [COLOR=red]192.168.107.2[/COLOR]**. The Snapshot Manager should now have a nice hierarchy of snapshots (STEP 1 --> STEP 2 --> You are here) 
[/LIST]

---

### Post by LHammonds on 2020-05-03
[SIZE=4]Volume / Disk Management[/SIZE]

Earlier, it was mentioned that the partition design needed to have some breathing room in each volume so that the file system inside can grow as needed. When the volumes were created during setup, the file systems were automatically expanded to fill the entire volume. We will now correct this by adding more "drives" to the system and then extend each logical volume to gain some breathing space.

Most logical volumes will be increased in size and then the file systems contained in them will be increased but not to the maximum amount.

This design will allow growth when needed and ensure that there will be time to add additional hard drives BEFORE they are needed which will keep the administrators from being stuck between a rock and a hard place! Nobody wants to lose a job because somebody did not estimate growth correctly or the budget did not allow for large capacity when the system first rolled out.

We started off with a 25 GB drive to hold these volumes and the changes below will use 22 GB.

Here are the planned adjustments for each **logical volume**:

root = 5 GB to 6 GB
home = 0.2 GB to 1 GB
tmp = 0.5 GB to 2 GB
var = 2.0 GB to 3 GB
bak = 0.5 GB to 4 GB

Here are the planned adjustments for each **file system**:

root = 5 GB [COLOR=red](no change)[/COLOR]
home = 0.2 GB to 0.5 GB
tmp = 0.5 GB to 1 GB
var = 2 GB [COLOR=red](no change)[/COLOR]
bak = 0.5 GB to 2 GB

Here is a graphical representation of what will be accomplished:

[IMG]https://images.hammondslegacy.com/linux/UbuntuHDPartitionDesign-Mod20.png[/IMG]

If we were to type **df -h** right now, we should see something like this:

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
udev                  448M     0  448M   0% /dev
tmpfs                  99M  772K   98M   1% /run
/dev/mapper/LVG-root  4.6G  2.3G  2.1G  52% /
tmpfs                 491M     0  491M   0% /dev/shm
tmpfs                 5.0M     0  5.0M   0% /run/lock
tmpfs                 491M     0  491M   0% /sys/fs/cgroup
/dev/mapper/LVG-tmp   446M  772K  411M   1% /tmp
/dev/mapper/LVG-bak   446M  732K  412M   1% /bak
/dev/sda1             922M  197M  662M  23% /boot
/dev/mapper/LVG-home  167M  232K  153M   1% /home
/dev/mapper/LVG-var   1.8G  268M  1.5G  16% /var
tmpfs                  99M     0   99M   0% /run/user/1000

```

To get a list of volume paths to use in the next commands, use **lvscan** to show your current volumes and their sizes.

```
sudo lvscan
  ACTIVE            '/dev/LVG/root' [<4.66 GiB] inherit
  ACTIVE            '/dev/LVG/var' [<1.86 GiB] inherit
  ACTIVE            '/dev/LVG/tmp' [476.00 MiB] inherit
  ACTIVE            '/dev/LVG/bak' [476.00 MiB] inherit
  ACTIVE            '/dev/LVG/home' [188.00 MiB] inherit
```

Type the following to set the exact size of the volume by specifying the end-result size you want:

```
sudo lvextend -L6G /dev/LVG/root
sudo lvextend -L1G /dev/LVG/home
sudo lvextend -L2G /dev/LVG/tmp
sudo lvextend -L3G /dev/LVG/var
sudo lvextend -L4G /dev/LVG/bak
```

or you can grow each volume by the specified amount (the number after the plus sign):
```
sudo lvextend -L+1G /dev/LVG/root
sudo lvextend -L+0.8G /dev/LVG/home
sudo lvextend -L+1.5G /dev/LVG/tmp
sudo lvextend -L+1G /dev/LVG/var
sudo lvextend -L+3.5G /dev/LVG/bak
```

To see the new sizes, use **lvscan**
```
sudo lvscan
  ACTIVE            '/dev/LVG/root' [6.00 GiB] inherit
  ACTIVE            '/dev/LVG/var' [3.00 GiB] inherit
  ACTIVE            '/dev/LVG/tmp' [2.00 GiB] inherit
  ACTIVE            '/dev/LVG/bak' [4.00 GiB] inherit
  ACTIVE            '/dev/LVG/home' [1.00 GiB] inherit
```

The last thing to do now is the actual growth of the file systems. We want to grow the existing file systems but only to a certain amount so we do not take up all the space in the volume. We want room for growth in the future so we have time to order and install new drives when needed.
```
sudo resize2fs /dev/LVG/home 500M
sudo resize2fs /dev/LVG/tmp 1G
sudo resize2fs /dev/LVG/bak 2G
```

If we need to increase space in **/var** at a later point, we can issue the following command without any downtime (we will automate this in a nifty script later):

```
sudo resize2fs /dev/LVG/var 2560MB
```

We could continue to increase this particular file system all the way until we reach the limit of the volume which is 3 GB at the moment.

If we were to type **df -h** right now, we should see something like this:

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
udev                  448M     0  448M   0% /dev
tmpfs                  99M  772K   98M   1% /run
/dev/mapper/LVG-root  4.6G  2.3G  2.1G  52% /
tmpfs                 491M     0  491M   0% /dev/shm
tmpfs                 5.0M     0  5.0M   0% /run/lock
tmpfs                 491M     0  491M   0% /sys/fs/cgroup
/dev/mapper/LVG-tmp   979M  1.3M  924M   1% /tmp
/dev/mapper/LVG-bak   2.0G  1.5M  1.9G   1% /bak
/dev/sda1             922M  197M  662M  23% /boot
/dev/mapper/LVG-home  473M  324K  452M   1% /home
/dev/mapper/LVG-var   1.8G  268M  1.5G  16% /var
tmpfs                  99M     0   99M   0% /run/user/1000
```

Remember, **df -h** will tell you the size of the file system and **lvscan** will tell you the size of the volumes where the file systems live in.

TIP: If you want to see everything in a specific block size, such as everything showing up in megabytes, you can use **df --block-size m**

[SIZE=4]Swap File Management[/SIZE]

If you do not specify a swap partition during the initial setup, a swap file system will be created automatically and point to a file called "swapfile" in the root filesystem.

Type **swapon --summary** to see the status of the swap system:

```

# swapon --summary
Filename                                Type            Size    Used    Priority
/swapfile                               file            88324   0       -2
```

Specific needs vary but the current rule of thumb for Linux servers is to have a swap file 1/2 the size of the amount of RAM in your system.

Let's assume we want a 1GB swap file and we want it on the /var partition. Keep in mind that it is normally recommended to keep the swapfile with the root partition for performance reasons.  Here are the steps to setup this scenario:


[LIST=1]
[*]Make sure you have space on /var by typing **df -h /var** 
[*]Run the following commands for the new swap file:
```
sudo fallocate --length 1G /var/swapfile1g
sudo chown root:root /var/swapfile1g
sudo chmod 600 /var/swapfile1g
sudo mkswap /var/swapfile1g --label swap
sudo swapon /var/swapfile1g
``` 
[*]Look at the current swap settings:
```
swapon --summary
Filename                                Type            Size    Used    Priority
/swapfile                               file            88324   0       -2
/var/swapfile1g                         file            1048572 0       -3
``` 
[*]Now disable the old swap file using these commands:
```
sudo swapoff /swapfile
sudo rm /swapfile
``` 
[*]Remove the old swapfile from /etc/fstab and add the new one.
```
sudo vi /etc/fstab
```
Remove:
```
/swapfile                                 none            swap    sw              0       0
```
Add:
```
/var/swapfile1g     none            swap    sw              0       0
``` 
[*]Look at the current swap settings again:
```
# swapon --summary
Filename                                Type            Size    Used    Priority
/var/swapfile1g                         file            1048500 0       -2
``` 
[*]Reboot the server and run the summary command again to verify that your /etc/fstab changes worked. 
[/LIST]


[SIZE=4]Adding More Hard Drives[/SIZE]

For this exercise, we will add two additional hard drives.  The addition of these drives are NOT necessary and this section can be skipped.  The extra drives are only to demonstrate how to add additional hard drives to the system.

Adding more space in VMware or VirtualBox is easy. In this exercise, each drive will be added as a separate disk just as if we were to add a physical drive to a physical server.

vSphere Steps

[LIST=1]
[*]Shutdown and power off the server by typing **sudo shutdown -P now** 
[*]In the vSphere client, right-click the Virtual Machine and choose *Edit Settings*. 
[*]On the hardware tab, click the *Add* button and select Hard Disk. Click Next, choose "Create a new virtual disk", click Next, set the size to **10** GB, click Next, Next, Finish. 
[*]Add another **15** GB disk using the same steps above and click OK to close the settings and allow VMware to process the changes. 
[/LIST]


VirtualBox Steps

[LIST=1]
[*]Shutdown and power off the server by typing **sudo shutdown -P now** 
[*]In the VirtualBox Manager, select the Virtual Machine and click *Settings*. 
[*]On the Storage tab, select *Controller: SATA* and click the *Add new storage attachment* button and select *Add Hard Disk*. Click *Create new disk*, *VDI*, Next, *Fixed size*, Next, give it a Name/Location/Size of **10** GB, click Create. 
[*]Add another **15** GB disk using the same steps above and click OK to close the settings and allow VirtualBox to process the changes. 
[/LIST]


Collect information about the newly added drives.


[LIST=1]
[*]Start the server and connect using PuTTY. 
[*]At the login prompt, login with your administrator account ([COLOR=red]**administrator**[/COLOR] / [COLOR=red]**myadminpass**[/COLOR]) 
[*]Make note of how much "Free PE / Size" you have in your logical volume group when using the **vgdisplay** command.  When done adding the new drives, the free space listed here will increase by the amount added. 
[*]Use **pvdisplay** which should show something similar to this:
```
sudo pvdisplay
  --- Physical volume ---
  PV Name               [COLOR=red]/dev/sda5[/COLOR]
  VG Name               [COLOR=red]LVG[/COLOR]
  PV Size               9.53 GiB / not usable 0
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              2440
  Free PE               157
  Allocated PE          2283
  PV UUID               g8IVWI-sF3A-aWAp-0KSJ-vmJE-SOkL-00R7DN

```
The important bits of info here are the PV Name and VG Name for our existing configuration. 
[*]Use **fdisk -l** which should show something similar to this (however I abbreviated it to show just the important parts):
```
sudo fdisk -l
Disk [COLOR=red]/dev/sda[/COLOR]: 10 GiB, 10737418240 bytes, 20971520 sectors
Device     Boot  Start      End  Sectors  Size Id Type
/dev/sda1  *      2048   976895   974848  476M 83 Linux
/dev/sda2       978942 20969471 19990530  9.5G  5 Extended
/dev/sda5       978944 20969471 19990528  9.5G 8e Linux LVM

Disk [COLOR=red]/dev/sdb[/COLOR]: 12 GiB, 12884901888 bytes, 25165824 sectors
Disk [COLOR=red]/dev/sdc[/COLOR]: 12 GiB, 12884901888 bytes, 25165824 sectors
```
The important bits of info here are the device paths for the new drives which I highlighted in red. 
[/LIST]

Prepare the first drive (/dev/sdb) to be used by the LVM

Type the following:
```
sudo fdisk /dev/sdb
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

Do the exact same steps as above but start with **sudo fdisk /dev/sdc**

Create physical volumes using the new drives

If we type **sudo fdisk -l**, we now see /dev/sdb1 and /dev/sdc1 which are Linux LVM partitions.

Type the following to create physical volumes:
```
sudo pvcreate /dev/sdb1
sudo pvcreate /dev/sdc1
```

Now add the physical volumes to the volume group (LVG) by typing the following:
```
sudo vgextend LVG /dev/sdb1
sudo vgextend LVG /dev/sdc1
```

You can run the **sudo vgdisplay** command to see that the "Free PE / Size" has increased.

Now that the space of both drives have been added to the logical volume group called LVG, we can now allocate that space to grow the logical volumes and then the file systems as needed.

Shutdown and power off the server by typing **sudo shutdown -P now**

In VM menu, select VM --> Snapshot --> Take Snapshot. Give it a name like **STEP 3** and description of **Ubuntu Server 20.04 LTS, Storage space adjusted, Static IP: [COLOR=red]192.168.107.2[/COLOR]**. The Snapshot Manager should now have a nice hierarchy of snapshots (STEP 1 --> STEP 2 --> STEP 3 --> You are here)

---

### Post by LHammonds on 2020-05-03
[SIZE=4]Software Configurations[/SIZE]
 

[LIST=1]
[*]Turn on the server and connect using PuTTY. 
[*]At the login prompt, login with your administrator account ([COLOR=red]**administrator**[/COLOR] / [COLOR=red]**myadminpass**[/COLOR]) 
[*]At the $ prompt, type the following to install various utilities which are described below:
```
sudo apt -y install vim-nox p7zip-full htop fsarchiver sendemail dialog ncdu
```
[LIST]
[*]vim-nox for use instead of the built-in VI editor. [more info]("http://en.wikipedia.org/wiki/Vim_%28text_editor%29") 
[*]p7zip-full is a 7-zip archive utility. 
[*]htop is a CPU/RAM monitoring utility. 
[*]fsarchiver is a backup utility. 
[*]sendemail is a command-line email utility. 
[*]dialog is used to build menu selections. 
[*]ncdu shows disk usage in menu format. 
[/LIST]
  
[*]Type **vi /etc/hosts** and add your email server:
```
[COLOR=red]192.168.107.25[/COLOR]    srv-mail
``` 
[*]Test the ability to send email by typing:
```
sendemail -f root@myserver -t MyTargetAddress@MyDomain.com -u "This is the Subject" -m "This is the body of the email" -s srv-mail:25
``` 
[*]If you are like me and like indents to be 2 spaces when you press TAB and not a tab character, then edit the vim-nox preference file:
```
vi ~/.vimrc
```
Add the following:
```
set tabstop=2
set shiftwidth=2
set expandtab
``` 
[*]If you want to disable automatic indents (especially when copy/paste ruins the format), then edit the vim-nox preference file:
```
 vi ~/.vimrc
```
Add the following:
```
filetype indent off
``` 
[/LIST]


[SIZE=4]VMware Tools[/SIZE]
 
Starting with Ubuntu 16.04, open-vm-tools are installed automatically.  We should not need to perform any actions in this section.
 
[SIZE=4]VirtualBox Guest Additions - Installation[/SIZE]
 
The Guest Additions need to be installed if the VM is using a VirtualBox host. This will insure maximum performance in a virtual environment.  The specific features this enables are: mouse pointer integration, shared clipboard, drag and drop, shared folders, better video support, seamless windows, generic host/guest communication channels, time synchronization and automated logins.


[LIST=1]
[*]Connect to the server using PuTTY. 
[*]At the login prompt, login with your administrator account ([COLOR=red]**administrator**[/COLOR] / [COLOR=red]**myadminpass**[/COLOR]) 
[*]You need to perform the following commands to fulfill the prerequisites:
```
sudo apt install dkms
sudo reboot
``` 
[*]Connect to the server using PuTTY. 
[*]At the login prompt, login with your administrator account ([COLOR=red]**administrator**[/COLOR] / [COLOR=red]**myadminpass**[/COLOR]) 
[*]From the VirtualBox menu, click Devices, Install Guest Additions 
[*]At the command line, type the following:
```
sudo mount /dev/cdrom /media/cdrom
sudo /media/cdrom/VBoxLinuxAdditions.run
sudo umount /media/cdrom
``` 
[*]To see the status, stop or start the service, you can use these commands:
```
systemctl status vboxadd-service
sudo systemctl stop vboxadd-service
sudo systemctl start vboxadd-service
``` 
[/LIST]

 
[SIZE=4]VirtualBox Guest Additions - Upgrading[/SIZE]
 
If VirtualBox is updated on the host machine, each VM also needs the upgraded Guest Additions.
 
Then mount the CDROM and run the installer just like the above. Reboot after it is upgraded.


[LIST=1]
[*]Connect to the server using PuTTY. 
[*]At the login prompt, login with your administrator account ([COLOR=red]**administrator**[/COLOR] / [COLOR=red]**myadminpass**[/COLOR]) 
[*]From the VirtualBox menu, click Devices, Install Guest Additions 
[*]At the console, type the following:
```
sudo mount /dev/cdrom /mnt/cdrom
sudo /mnt/cdrom/VBoxLinuxAdditions.run
sudo reboot
``` 
[/LIST]

 
[SIZE=4]VirtualBox Guest Additions - Uninstallation[/SIZE]
 
If a VM will be migrated from VirtualBox to something like a VMware, the Guest Additions on the VM will need to be removed.


[LIST=1]
[*]Connect to the server using PuTTY. 
[*]At the login prompt, login with your administrator account ([COLOR=red]**administrator**[/COLOR] / [COLOR=red]**myadminpass**[/COLOR]) 
[*]Type the following:
```
cd /opt/VBox*
sudo ./uninstall.sh
``` 
[/LIST]


[SIZE=4]AppArmor Profiles[/SIZE]

It might be necessary to disable specific AppArmor profiles for certain processes such as mysqld.


[LIST=1]
[*]Show the current status of AppArmor:
```
sudo apparmor_status
apparmor module is loaded.
13 profiles are loaded.
13 profiles are in enforce mode.
   /usr/bin/man
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/NetworkManager/nm-dhcp-helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/snapd/snap-confine
   /usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/sbin/tcpdump
   /{,usr/}sbin/dhclient
   lsb_release
   man_filter
   man_groff
   nvidia_modprobe
   nvidia_modprobe//kmod
0 profiles are in complain mode.
0 processes have profiles defined.
0 processes are in enforce mode.
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

``` 
[*]List the profiles:
```
ls -l /etc/apparmor.d
total 72
drwxr-xr-x 4 root root  4096 Apr 29 15:32 abstractions
drwxr-xr-x 2 root root  4096 Apr 29 11:53 disable
drwxr-xr-x 2 root root  4096 Feb 11 09:25 force-complain
drwxr-xr-x 2 root root  4096 Apr 29 15:33 local
-rw-r--r-- 1 root root  1313 Apr 12 11:11 lsb_release
-rw-r--r-- 1 root root  1108 Apr 12 11:11 nvidia_modprobe
-rw-r--r-- 1 root root  3222 Mar 11 08:15 sbin.dhclient
drwxr-xr-x 5 root root  4096 Apr 29 15:32 tunables
-rw-r--r-- 1 root root  3202 Feb 25 11:13 usr.bin.man
-rw-r--r-- 1 root root 26113 Apr 10 09:57 usr.lib.snapd.snap-confine.real
-rw-r--r-- 1 root root  1575 Feb 11 09:25 usr.sbin.rsyslogd
-rw-r--r-- 1 root root  1385 Dec  7 10:25 usr.sbin.tcpdump
-rw-r--r-- 1 root root  3210 Apr 29 10:00 usr.sbin.mysqld

``` 
[*]Let's disable the mysql profile:
```

sudo ln -s /etc/apparmor.d/usr.sbin.mysqld /etc/apparmor.d/disable/
apparmor_parser -R /etc/apparmor.d/disable/usr.sbin.mysqld

``` 
[*]Reboot the server and run the apparmor_status command again to verify that the profile is still disabled after a reboot. 
[*]To re-enable the profile we just disabled, type the following:
```

sudo rm /etc/apparmor.d/disable/usr.sbin.mysqld
sudo apparmor_parser -r /etc/apparmor.d/usr.sbin.mysqld

``` 
[*]To disable apparmor (and all profiles), type the following:
```
sudo systemctl disable apparmor
``` 
[*]To re-enable apparmor, type the following:
```
sudo systemctl enable apparmor
``` 
[/LIST]

---

### Post by LHammonds on 2020-05-03
[SIZE=4]Scripting[/SIZE]

Many of the sections below utilize BASH scripts as part of the solution/automation.

To speed up installation for myself and others, the commands below will download and extract the base set of scripts I use as a foundation for all my servers.  You can download all of them at once or skip this step and copy/paste the scripts one at a time throughout this tutorial.

```

cd /tmp
wget https://files.hammondslegacy.com/linux/init-scripts-2004.tar.gz
tar -xvf /tmp/init-scripts-2004.tar.gz -C /
rm /tmp/init-scripts-2004.tar.gz

```
NOTE: If you are leary about extracting the contents of the archive before seeing it, use the following command to peek inside before extracting:
```
tar -ztvf /tmp/init-scripts-2004.tar.gz
```

The directory structure will be as follows after extraction:

```

/var/scripts/common
/var/scripts/data
/var/scripts/prod
/var/scripts/test

```

The "common" directory contains code that is commonly used in other scripts.
The "data" directory contains stored information (currently, just backups of crontab schedule)
The "prod" directory contains all production-ready scripts
The "test" directory contains scripts that are under development or never need to be run in production-mode.

Most of my scripts will import a file called "standard.conf" from the common script folder.

/var/scripts/common/standard.conf
```
## Global Variables ##
Company="[COLOR=red]abc[/COLOR]"
TempDir="/tmp"
LogDir="/var/log"
ShareDir="/srv/samba/share"
MyDomain="[COLOR=red]mydomain.com[/COLOR]"
AdminEmail="admin@${MyDomain}"
ReportEmail="[COLOR=red]LHammonds[/COLOR] <[COLOR=red]lhammonds[/COLOR]@${MyDomain}>"
BackupDir="/bak"
OffsiteDir="/mnt/backup"
OffsiteTestFile="${OffsiteDir}/offline.txt"
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
  ## NOTE: The "offline.txt" file in the Linux mount folder should disappear while the mount is active.
  mount -t cifs //[COLOR=red]srv-backup/myshare[/COLOR] ${OffsiteDir} --options nouser,rw,nofail,noexec,credentials=/etc/cifspw
}
 
function f_umount()
{
  ## Dismount the Windows share folder.
  ## NOTE: The unmounted folder should have a file called "offline.txt"
  umount ${OffsiteDir}
}
```

Here is a script to help automate the creation of this structure on the various servers if you do not use the "init-scripts" archive:
 
setup-folders.sh
```
#!/bin/bash
if [ ! -d /var/scripts/prod ]; then
  mkdir -p /var/scripts/prod
fi
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
chmod 0755 -R /var/scripts
```

---

### Post by LHammonds on 2020-05-03
[SIZE=4]Crontab Schedule[/SIZE]

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
#       __________ Minute (0-59)
#      / _________ Hour (0-23)
#     / /  _______ Day Of Month (1-31)
#    / /  /   ____ MONth (1-12)
#   / /  /   /   _ Day Of Week (0-7) (Sun = 0 or 7)
#  / /  /   /   /  -------------------------------------------------------------
# m h dom mon dow  command <arguments> > /dev/null 2>&1
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
45 1 * * * /var/scripts/prod/check-storage.sh var 100 50 > /dev/null 2>&1
0 2 * * * /var/scripts/prod/check-storage.sh bak 100 50 > /dev/null 2>&1
#
# Daily software upgrade check
#
0 3 * * * /var/scripts/prod/apt-upgrade.sh > /dev/null 2>&1
30 3 * * * /var/scripts/prod/reboot-check.sh > /dev/null 2>&1

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

### Post by LHammonds on 2020-05-03
[SIZE=4]Operator Scripts[/SIZE]

I like scripts to be as generic as possible when copying among multiple servers.

I push the service start/stop specifics into their own scripts which can be unique to each server depending on what services need to be stopped/started.

On a MySQL/MariaDB server, the scripts that start and stop services would just contain the "mysql" line and the other service controls that do not apply are commented out.

NOTE: This script is custom-tailored to each server it is placed on to safely stop the services that are unique to it.
/var/scripts/prod/servicestop.sh
```

#############################################
## Name          : servicestop.sh
## Version       : 1.1
## Date          : 2018-04-19
## Author        : LHammonds
## Compatibility : Ubuntu Server 16.04 thru 20.04 LTS
## Requirements  : None
## Purpose       : Stop primary services.
## Run Frequency : As needed
## Exit Codes    : None
################ CHANGE LOG #################
## DATE       WHO  WHAT WAS CHANGED
## ---------- ---- ----------------------------
## 2013-01-08 LTH  Created script.
## 2018-04-19 LTH  Replaced service with systemctl
#############################################
## NOTE: Configure whatever services you need stopped here.
echo "Stopping services..."
#systemctl stop vsftpd
#systemctl stop nagios
#systemctl stop apache2
#systemctl stop mariadb
sleep 1

```

NOTE: This script is custom-tailored to each server it is placed on to start the services that are unique to it.  Although the services are likely to auto-start with the server, this is mainly used if only restarting the services and not the entire server.
/var/scripts/prod/servicestart.sh
```

#############################################
## Name          : servicestart.sh
## Version       : 1.1
## Date          : 2018-04-19
## Author        : LHammonds
## Compatibility : Ubuntu Server 16.04 thru 20.04 LTS
## Requirements  : None
## Purpose       : Start primary services.
## Run Frequency : As needed
## Exit Codes    : None
################ CHANGE LOG #################
## DATE       WHO  WHAT WAS CHANGED
## ---------- ---- ----------------------------
## 2018-04-19 LTH  Created script.
## 2018-04-19 LTH  Replaced service with systemctl
#############################################
## NOTE: Add whatever services you need started here.
echo "Starting services..."
#systemctl start mariadb
#systemctl start apache2
#systemctl start nagios
#systemctl start vsftpd
sleep 1

```

The service restart, reboot and shutdown scripts can simply call the service stop and start scripts and should never need to be modified from default.

NOTE: This script is generic enough that it should not need to be modified when deployed to any server.
/var/scripts/prod/servicerestart.sh
```

#!/bin/bash
#############################################
## Name          : servicerestart.sh
## Version       : 1.1
## Date          : 2018-04-19
## Author        : LHammonds
## Compatibility : Ubuntu Server 12.04 thru 20.04 LTS
## Requirements  : None
## Purpose       : Stop/Start primary services.
## Run Frequency : As needed
## Exit Codes    : None
################ CHANGE LOG #################
## DATE       WHO  WHAT WAS CHANGED
## ---------- ---- ----------------------------
## 2013-01-08 LTH  Created script.
## 2018-04-19 LTH  Spit stop/start code into individual scripts.
#############################################
## Import standard variables and functions. ##
source /var/scripts/common/standard.conf
clear
${ScriptDir}/prod/servicestop.sh
${ScriptDir}/prod/servicestart.sh

```

/var/scripts/prod/reboot.sh
```

#!/bin/bash
#############################################
## Name          : reboot.sh
## Version       : 1.2
## Date          : 2018-04-19
## Author        : LHammonds
## Compatibility : Ubuntu Server 12.04 thru 20.04 LTS
## Requirements  : Run as root
## Purpose       : Stop services and reboot server.
## Run Frequency : As needed
## Exit Codes    : None
################ CHANGE LOG #################
## DATE       WHO  WHAT WAS CHANGED
## ---------- ---- ----------------------------
## 2013-01-07 LTH  Created script.
## 2017-12-18 LTH  Added logging.
## 2018-04-19 LTH  Various minor changes.
#############################################

## Import standard variables and functions. ##
source /var/scripts/common/standard.conf

## Define local variables.
LogFile="${LogDir}/${Company}-reboot.log"

## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo -e "\nERROR: Root user required to run this script.\n"
  echo -e "Type 'sudo su' to temporarily become root user.\n"
  exit
fi

clear
echo "`date +%Y-%m-%d_%H:%M:%S` - Reboot initiated." | tee -a ${LogFile}
${ScriptDir}/prod/servicestop.sh
echo "Rebooting..."
echo "3"
sleep 1
echo "2"
sleep 1
echo "1"
sleep 1
shutdown -r now

```

/var/scripts/prod/shutdown.sh
```

#!/bin/bash
#############################################
## Name          : shutdown.sh
## Version       : 1.1
## Date          : 2018-05-08
## Author        : LHammonds
## Compatibility : Ubuntu Server 16.04 thru 20.04 LTS
## Requirements  : Run as root
## Purpose       : Notify logged in users, stop services and power off server.
## Run Frequency : As needed
## Parameters    :
##    1 = (Optional) Expected downtime in minutes.
## Exit Codes    : None
################ CHANGE LOG #################
## DATE       WHO  WHAT WAS CHANGED
## ---------- ---- ----------------------------
## 2018-04-19 LTH  Created script.
## 2018-05-08 LTH  Added broadcast message and loop function.
#############################################

## Import standard variables and functions. ##
source /var/scripts/common/standard.conf

## Define local variables.
LogFile="${LogDir}/${Company}-shutdown.log"
DefaultDowntime=5

#######################################
##            FUNCTIONS              ##
#######################################

function f_loop()
{
  LoopCount=$1
  for LoopIndex in $(seq ${LoopCount} -1 1)
  do
    echo ${LoopIndex}
    sleep 1
  done
} ## f_loop

function f_showhelp()
{
  echo -e "NOTE: Default expected downtime is ${DefaultDowntime} minutes and is optional.\n"
  echo -e "Usage : ${ScriptName} ExpectedDowntimeInMinutes\n"
  echo -e "Example: ${ScriptName} 5\n"
  exit
} ## f_showhelp

## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo -e "\nERROR: Root user required to run this script.\n"
  echo -e "Type 'sudo su' to temporarily become root user.\n"
  exit
fi

#######################################
##           MAIN PROGRAM            ##
#######################################

## Check existance of optional command-line parameter.
case "$1" in
  --help|-h|-?)
    f_showhelp
    ;;
  *[0-9]*)
    ## If parameter is a number, allow override.
    TimeOverride=$1
    ;;
  *)
    ## Invalid input supplied. Discard.
    ;;
esac

#clear
echo ""
if [ -z ${TimeOverride+8} ]; then
  ## No override given.  Display user input prompt.
  echo -e "How many minutes do you expect the server to be offline? (default=${DefaultDowntime})"
  read -t 30 TimeInput
  ReturnCode=$?
  if [[ ${ReturnCode} -gt 128 ]]; then
    ## User input timed out. Use default.
    let OfflineTime=${DefaultDowntime}
  else
    ## Evaluate the user-supplied input.
    case ${TimeInput} in
      *[0-9]*)
        ## User-supplied input is a number.  Use it instead of default.
        let OfflineTime="${TimeInput}" ;;
      *)
        ## User-supplied input is invalid.  Use default.
        let OfflineTime=${DefaultDowntime} ;;
    esac
  fi
else
  ## Use commandline override.
  OfflineTime=${TimeOverride}
fi
## Broadcasting message to any other users logged in via SSH.
clear
echo "WARNING: Shutting down server. Should be back online in ${OfflineTime} minutes" | wall

echo "`date +%Y-%m-%d_%H:%M:%S` - Shutdown initiated." | tee -a ${LogFile}
${ScriptDir}/prod/servicestop.sh
echo "Shutting down..."
f_loop 10
shutdown -P now

```

---

### Post by LHammonds on 2020-05-03
[SIZE=4]APT Upgrade[/SIZE]
 
This script that can be scheduled to run daily to check for OS/software updates in the repositories and then install them if available.

NOTE: This script will assume the answer is yes to any question the package manager asks with exception to modified configuration files.  If you modify a configuration file, the package manager will want to overwrite your changes with the packages template.  You typically do NOT want to do this because you will lose your customized changes.  There is at least one scenario you need to be careful about...major changes in the config file.  If breaking changes were made in the latest version, you will have to rename your existing config file, find/copy the package's template config file and manually merge your custom changes into the new config file.
 
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
## Version       : 1.4
## Date          : 2019-09-23
## Author        : LHammonds
## Purpose       : Keep system updated (rather than use unattended-upgrades)
## Compatibility : Verified on Ubuntu Server 18.04 thru 20.04 LTS
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
## 2017-03-16 LTH Made compatible with 16.04 LTS.
## 2019-09-23 LTH Set to not overwrite existing config file.
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

## Make sure the cleanup function is called from this point forward.
trap f_cleanup EXIT

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
${AptGetCmd} --assume-yes --option Dpkg::Options::="--force-confdef" --option Dpkg::Options::="--force-confold" upgrade >> ${LogFile} 2>&1
ReturnCode=$?
if [[ "${ReturnCode}" -gt 0 ]]; then
  ErrorMsg="Apt-Get Upgrade return code of ${ReturnCode}"
  ErrorFlag=8
  f_cleanup
fi
echo "`date +%Y-%m-%d_%H:%M:%S` --- Apt-Get Dist-Upgrade" | tee -a ${LogFile}
echo "--------------------------------------------------" >> ${LogFile}
${AptGetCmd} --assume-yes --option Dpkg::Options::="--force-confdef" --option Dpkg::Options::="--force-confold" dist-upgrade >> ${LogFile} 2>&1
ReturnCode=$?
if [[ "${ReturnCode}" -gt 0 ]]; then
  ErrorMsg="Apt-Get Dist-Upgrade return code of ${ReturnCode}"
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

2019-09-23_17:29:15 - Begin script.
2019-09-23_17:29:15 --- Apt-Get Update
2019-09-23_17:29:18 --- Apt-Get Upgrade
--------------------------------------------------
Reading package lists...
Building dependency tree...
Reading state information...
Calculating upgrade...
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2019-09-23_17:29:19 --- Apt-Get Dist-Upgrade
--------------------------------------------------
Reading package lists...
Building dependency tree...
Reading state information...
Calculating upgrade...
The following NEW packages will be installed:
  linux-headers-4.15.0-64 linux-headers-4.15.0-64-generic
  linux-image-4.15.0-64-generic linux-modules-4.15.0-64-generic
  linux-modules-extra-4.15.0-64-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 66.2 MB of archives.
After this operation, 332 MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-modules-4.15.0-64-generic amd64 4.15.0-64.73 [13.1 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-image-4.15.0-64-generic amd64 4.15.0-64.73 [7,965 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-modules-extra-4.15.0-64-generic amd64 4.15.0-64.73 [32.9 MB]
Get:4 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-generic amd64 4.15.0.64.66 [1,868 B]
Get:5 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-image-generic amd64 4.15.0.64.66 [2,392 B]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-headers-4.15.0-64 all 4.15.0-64.73 [11.1 MB]
Get:7 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-headers-4.15.0-64-generic amd64 4.15.0-64.73 [1,231 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-headers-generic amd64 4.15.0.64.66 [2,352 B]
Fetched 66.2 MB in 5s (13.1 MB/s)
Selecting previously unselected package linux-modules-4.15.0-64-generic.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 111865 files and directories currently installed.)
Preparing to unpack .../0-linux-modules-4.15.0-64-generic_4.15.0-64.73_amd64.deb ...
Unpacking linux-modules-4.15.0-64-generic (4.15.0-64.73) ...
Selecting previously unselected package linux-image-4.15.0-64-generic.
Preparing to unpack .../1-linux-image-4.15.0-64-generic_4.15.0-64.73_amd64.deb ...
Unpacking linux-image-4.15.0-64-generic (4.15.0-64.73) ...
Selecting previously unselected package linux-modules-extra-4.15.0-64-generic.
Preparing to unpack .../2-linux-modules-extra-4.15.0-64-generic_4.15.0-64.73_amd64.deb ...
Unpacking linux-modules-extra-4.15.0-64-generic (4.15.0-64.73) ...
Preparing to unpack .../3-linux-generic_4.15.0.64.66_amd64.deb ...
Unpacking linux-generic (4.15.0.64.66) over (4.15.0.60.62) ...
Preparing to unpack .../4-linux-image-generic_4.15.0.64.66_amd64.deb ...
Unpacking linux-image-generic (4.15.0.64.66) over (4.15.0.60.62) ...
Selecting previously unselected package linux-headers-4.15.0-64.
Preparing to unpack .../5-linux-headers-4.15.0-64_4.15.0-64.73_all.deb ...
Unpacking linux-headers-4.15.0-64 (4.15.0-64.73) ...
Selecting previously unselected package linux-headers-4.15.0-64-generic.
Preparing to unpack .../6-linux-headers-4.15.0-64-generic_4.15.0-64.73_amd64.deb ...
Unpacking linux-headers-4.15.0-64-generic (4.15.0-64.73) ...
Preparing to unpack .../7-linux-headers-generic_4.15.0.64.66_amd64.deb ...
Unpacking linux-headers-generic (4.15.0.64.66) over (4.15.0.60.62) ...
Setting up linux-modules-4.15.0-64-generic (4.15.0-64.73) ...
Setting up linux-headers-4.15.0-64 (4.15.0-64.73) ...
Setting up linux-image-4.15.0-64-generic (4.15.0-64.73) ...
I: /vmlinuz.old is now a symlink to boot/vmlinuz-4.15.0-60-generic
I: /initrd.img.old is now a symlink to boot/initrd.img-4.15.0-60-generic
I: /vmlinuz is now a symlink to boot/vmlinuz-4.15.0-64-generic
I: /initrd.img is now a symlink to boot/initrd.img-4.15.0-64-generic
Setting up linux-headers-4.15.0-64-generic (4.15.0-64.73) ...
Setting up linux-headers-generic (4.15.0.64.66) ...
Setting up linux-modules-extra-4.15.0-64-generic (4.15.0-64.73) ...
Setting up linux-image-generic (4.15.0.64.66) ...
Setting up linux-generic (4.15.0.64.66) ...
Processing triggers for linux-image-4.15.0-64-generic (4.15.0-64.73) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.15.0-64-generic
/etc/kernel/postinst.d/x-grub-legacy-ec2:
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-4.15.0-60-generic
Found kernel: /vmlinuz-4.15.0-58-generic
Found kernel: /vmlinuz-4.15.0-64-generic
Found kernel: /vmlinuz-4.15.0-60-generic
Found kernel: /vmlinuz-4.15.0-58-generic
Replacing config file /run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-64-generic
Found initrd image: /boot/initrd.img-4.15.0-64-generic
Found linux image: /boot/vmlinuz-4.15.0-60-generic
Found initrd image: /boot/initrd.img-4.15.0-60-generic
Found linux image: /boot/vmlinuz-4.15.0-58-generic
Found initrd image: /boot/initrd.img-4.15.0-58-generic
done
--------------------------------------------------
2019-09-23_17:30:31 --- Apt-Get Autoremove
--------------------------------------------------
Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be REMOVED:
  linux-headers-4.15.0-58 linux-headers-4.15.0-58-generic
  linux-image-4.15.0-58-generic linux-modules-4.15.0-58-generic
  linux-modules-extra-4.15.0-58-generic
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 333 MB disk space will be freed.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 147371 files and directories currently installed.)
Removing linux-headers-4.15.0-58-generic (4.15.0-58.64) ...
Removing linux-headers-4.15.0-58 (4.15.0-58.64) ...
Removing linux-modules-extra-4.15.0-58-generic (4.15.0-58.64) ...
Removing linux-image-4.15.0-58-generic (4.15.0-58.64) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.15.0-58-generic
/etc/kernel/postrm.d/x-grub-legacy-ec2:
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-4.15.0-64-generic
Found kernel: /vmlinuz-4.15.0-60-generic
Found kernel: /vmlinuz-4.15.0-58-generic
Replacing config file /run/grub/menu.lst with new version
Found kernel: /vmlinuz-4.15.0-64-generic
Found kernel: /vmlinuz-4.15.0-60-generic
Replacing config file /run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-64-generic
Found initrd image: /boot/initrd.img-4.15.0-64-generic
Found linux image: /boot/vmlinuz-4.15.0-60-generic
Found initrd image: /boot/initrd.img-4.15.0-60-generic
done
Removing linux-modules-4.15.0-58-generic (4.15.0-58.64) ...
--------------------------------------------------
2019-09-23_17:30:48 --- Apt-get Autoclean
--------------------------------------------------
Reading package lists...
Building dependency tree...
Reading state information...
--------------------------------------------------
2019-09-23_17:30:48 --- Apt-get Clean
--------------------------------------------------
--------------------------------------------------
2019-09-23_17:30:48 - End script.

```

[SIZE=4]Reboot Check[/SIZE]

You can schedule the server to run your custom reboot script right after an upgrade to see if it needs to be rebooted automatically.  Use at your own discretion since many admins do not like having a server reboot without them being present just to make extra sure the service comes back up without any issues or at least be ready to handle them immediately.

You can run this reboot check every time the upgrade script but it will only initiate the reboot sequence if the upgrade placed a notification file saying it needs a reboot to complete the upgrade.

The following is an example of a crontab entry to schedule the script to run shortly after the upgrade script:
 
/var/scripts/data/crontab.root
```
0 3 * * * /var/scripts/prod/apt-upgrade.sh > /dev/null 2>&1
30 3 * * * /var/scripts/prod/reboot-check.sh > /dev/null 2>&1
```

```

#!/bin/bash
#############################################
## Name          : reboot-check.sh
## Version       : 1.2
## Date          : 2019-10-01
## Author        : LHammonds
## Compatibility : Ubuntu Server 16.04.3 - 20.04 LTS
## Requirements  : Run as root
## Purpose       : Stop services and reboot server but only if necessary.
## Run Frequency : Daily after update.
## Exit Codes    : None
################ CHANGE LOG #################
## DATE       WHO  WHAT WAS CHANGED
## ---------- ---- ----------------------------
## 2017-12-13 LTH  Created script.
## 2019-09-24 LTH  Added email notification.
## 2019-10-01 LTH  Added better event logging.
#############################################

## Import standard variables and functions. ##
source /var/scripts/common/standard.conf

## Define local variables.
LogFile="${LogDir}/${Company}-reboot-check.log"

## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo -e "\nERROR: Root user required to run this script.\n"
  echo -e "Type 'sudo su' to temporarily become root user.\n"
  exit
fi

echo "`date +%Y-%m-%d_%H:%M:%S` Current Kernel: `/bin/uname -nr`" | tee -a ${LogFile}
if [ -f /var/run/reboot-required ]; then
  echo "`date +%Y-%m-%d_%H:%M:%S` - Reboot required." | tee -a ${LogFile}
  cat /var/run/reboot-required.pkgs >> ${LogFile}
  f_sendmail "[INFO] ${Hostname} Reboot Notice" "${Hostname} rebooted at `date +%Y-%m-%d_%H:%M:%S`"
  ${ScriptDir}/prod/reboot.sh
else
  echo "`date +%Y-%m-%d_%H:%M:%S` - No reboot required." | tee -a ${LogFile}
fi

```

---

### Post by LHammonds on 2020-05-03
[SIZE=4]Check Storage Space[/SIZE]

In favor of managing by exception, this script that can be scheduled to run daily to check the file systems to see if they are getting close to filling up and will automatically expand them a little bit and give you an email notice. Everything is done at the megabyte level. If you do not want the script to perform the increase, simply add a pound sign in front of the resize2fs command on line 62 to comment it out. Might also want to modify the log and email messages so it does not look like it actually "performed" the resize but instead is telling YOU how to perform the resize.

Here are the lines added to the root crontab schedule which will check each file system.

The script check the specified file system and see if the amount of space free is less than the threshold (e.g. 100 MB). If the file system has free space that is less than the threshold, it will attempt to add the specified amount (e.g. 50 MB).

crontab
```
0 1 * * * /var/scripts/prod/check-storage.sh root 500 100 > /dev/null 2>&1
15 1 * * * /var/scripts/prod/check-storage.sh home 100 50 > /dev/null 2>&1
30 1 * * * /var/scripts/prod/check-storage.sh tmp 100 50 > /dev/null 2>&1
45 1 * * * /var/scripts/prod/check-storage.sh var 100 50 > /dev/null 2>&1
0 2 * * * /var/scripts/prod/check-storage.sh bak 100 50 > /dev/null 2>&1
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
## Compatibility : Verified on Ubuntu Server 12.04 thru 20.04 LTS
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

## Check existence of required command-line parameters.
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

2020-05-03_01:00:00 - /dev/LVG/root 2088M>100M No action required.
2020-05-03_01:15:00 - /dev/LVG/var 507M>100M No action required.
2020-05-03_01:30:00 - /dev/LVG/tmp 917M>100M No action required.
2020-05-03_01:45:00 - /dev/LVG/bak 1870M>100M No action required.
2020-05-03_02:00:00 - /dev/LVG/home 446M>100M No action required.

```
Here is a sample of what the log will look like when it performs increases:
 
/var/log/check-storage.log
```
2020-05-03_09:40:10 - Starting expansion of /dev/LVG/var
2020-05-03_09:40:10 --- LVSize=3072MB, FSSize=1843MB, FSAvail=507MB, FSThreshold=600MB, FSIncreaseBy=100MB
2020-05-03_09:40:10 --- resize2fs /dev/LVG/var 1943M, ReturnCode=0
2020-05-03_09:40:11 - Finished expansion of /dev/LVG/var
2020-05-03_09:40:37 - Starting expansion of /dev/LVG/tmp
2020-05-03_09:40:37 --- LVSize=2048MB, FSSize=979MB, FSAvail=917MB, FSThreshold=2000MB, FSIncreaseBy=100MB
2020-05-03_09:40:37 --- resize2fs /dev/LVG/tmp 1079M, ReturnCode=0
2020-05-03_09:40:37 - Finished expansion of /dev/LVG/tmp
2020-05-03_09:40:56 - Starting expansion of /dev/LVG/tmp
2020-05-03_09:40:56 --- LVSize=2048MB, FSSize=1030MB, FSAvail=966MB, FSThreshold=2000MB, FSIncreaseBy=100MB
2020-05-03_09:40:56 --- resize2fs /dev/LVG/tmp 1130M, ReturnCode=0
2020-05-03_09:40:56 - Finished expansion of /dev/LVG/tmp

```

---

### Post by LHammonds on 2020-05-03
[SIZE=4]Operator Menu[/SIZE]

To make my servers easier to administer within my group (who are not all *NIX guys), I made an operator script that can be used to manipulate the server.

The main features I wanted to make easier for other members of the IT group are:

1. Update the operating system (manually)
2. Disk Status
3. Memory Status
4. Stop/Restart primary services
5. Cleanly shutdown services and reboot server
6. Cleanly shutdown services and power off server

I accomplished this by creating a script and making a shortcut to it so the only thing they need to type on each server is "opm" which is short for "Operator Menu"

Here is how to do something similar for your servers.

Create the script file and set the permissions so that only the root user can run the script and make a shortcut for it:

```

touch /var/scripts/prod/opm.sh
chmod 0700 /var/scripts/prod/opm.sh
ln -s /var/scripts/prod/opm.sh /usr/sbin/opm

```

Now open the script in your favorite editor and add the following:
/var/scripts/prod/opm.sh
```
#!/bin/bash
#############################################
## Name          : opm.sh
## Version       : 1.2
## Date          : 2018-04-19
## Author        : LHammonds
## Compatibility : Ubuntu Server 12.04 thru 20.04 LTS
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
## 2018-04-19 LTH  Various minor changes.
#############################################
## Store menu options selected by the user.
TempDir="/tmp"
ScriptDir="/var/scripts/prod"
InputFile="${TempDir}/opm-input.$$"

## Storage file for displaying cal and date command output.
OutputFile="${TempDir}/opm-output.$$"

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
trap "rm $OutputFile; rm $InputFile; exit" SIGHUP SIGINT SIGTERM

function f_display_output(){
  ## Purpose - display output using msgbox
  ##  $1 -> set msgbox height
  ##  $2 -> set msgbox width
  ##  $3 -> set msgbox title
  local h=${1-10}     ## box height default 10
  local w=${2-41}     ## box width default 41
  local t=${3-Output} ## box title
  dialog --backtitle "Operator Menu for $(hostname -f)" --title "${t}" --clear --msgbox "$(<$OutputFile)" ${h} ${w}
} ## f_display_output

function f_showdate(){
  ## Purpose - display current system date & time
  echo "Today is $(date) @ $(hostname -f)." >$OutputFile
  f_display_output 6 60 "Date and Time"
} ## f_showdate

function f_checkdisk(){
  ## Purpose: Display disk status.
  clear
  echo -e "df --block-size=M\n"
  df --block-size=M
  echo ""
  read -p "Press [Enter] key to continue..."
} ## f_checkdisk

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
  RebootServer "Cleanly reboot server" \
  PoweroffServer "Cleanly Power-off server" \
  Date/time "Displays date and time" 2>"${InputFile}"

  menuitem=$(<"${InputFile}")

  ## Make decision.
  case $menuitem in
    OSUpdate) ${ScriptDir}/apt-upgrade.sh;;
    CheckDisk) f_checkdisk;;
    MEMCheck) htop;;
    ServiceRestart) ${ScriptDir}/servicerestart.sh;;
    RebootServer) ${ScriptDir}/reboot.sh;;
    PoweroffServer) ${ScriptDir}/shutdown.sh;;
    Date/time) f_showdate;;
    Exit) clear; echo "Clean menu exit."; break;;
  esac
done

## Delete temp files.
[ -f $OutputFile ] && rm $OutputFile
[ -f $InputFile ] && rm $InputFile

```

[HR][/HR]

[SIZE=4]Customizing Operator Menu[/SIZE]

Let's say you have "mytop" installed on your MySQL/MariaDB server and you want that added to your menu.  This is how you would do that.

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

Now when you run opm, you will see the MySQL/MariaDB entry which will run mytop when you select it.

With this menu example, I have given you 3 example types of how you can do something.  You can call the program directly, like mytop or htop, or you can call a function to process several lines of script like f_checkdisk or f_showdate or you can call an external script like reboot.sh or servicerestart.sh which can further isolate individual server needs in other scripts.

---

### Post by LHammonds on 2020-05-03
[SIZE=4]Firewall[/SIZE]

Linux uses IPTables as its firewall but learning the ins and outs of the syntax can be daunting. Luckily for us, Ubuntu has a front-end for it called Uncomplicated Firewall (UFW for short).

If you are not using IPv6 (most networks are still just using IPv4), you can comment out the IPv6 setting so you don't get doubles of each rule (one for IPv4 and one for IPv6).

To disable IPv6 rules:
```
sudo vi /etc/default/ufw
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

You can copy this script and use it for your own purposes and tweak it for your environment.  Enough commands are used/documented in it that you should be able to modify it to fit your particular server.  For example, if running a Minecraft server, you could add a command to allow TCP port 25565.  If you are running a web server, you could remove the comment from the TCP ports 80, 8080 and 443.

I NEVER simply copy this script and run it.  Each and every server requires a custom variation of this script tailored for it.  The application section has examples for commonly used services such as web, database, etc.  Feel free to uncomment lines you can use and modify to suit your needs.

/var/scripts/prod/en-firewall.sh
```
#!/bin/bash
#############################################
## Name          : enable-firewall.sh
## Version       : 1.1
## Date          : 2017-04-13
## Author        : LHammonds
## Compatibility : Ubuntu Server 14.04 thru 20.04 LTS
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
ufw allow from 192.168.107.0/24 to any port 22 comment 'SSH via LAN' 1>/dev/null 2>&1
ufw allow from 192.168.108.0/24 to any port 22 comment 'SSH via LAN' 1>/dev/null 2>&1
echo "Allowing Samba file sharing connections"
#ufw allow proto tcp to any port 135,139,445 comment 'Samba Share' 1>/dev/null 2>&1
#ufw allow proto udp to any port 137,138 comment 'Samba Share' 1>/dev/null 2>&1
echo "Allowing Nagios connections"
#ufw allow from 192.168.107.21 to any port 12489 comment 'Nagios' 1>/dev/null 2>&1
#ufw allow from 192.168.107.21 proto tcp to any port 5666 comment 'Nagios' 1>/dev/null 2>&1
echo "Adding Application-specific rules"
echo "Adding MySQL/MariaDB rules"
#ufw allow from 192.168.107.0/24 proto tcp to any port 3306 comment 'MariaDB via LAN' 1>/dev/null 2>&1
#ufw allow from 192.168.108.0/24 proto tcp to any port 3306 comment 'MariaDB via LAN' 1>/dev/null 2>&1
echo "Adding FTP/FTPS rules"
#ufw allow proto tcp to any port 990 comment 'FTPS' 1>/dev/null 2>&1
#ufw allow proto tcp to any port 21 comment 'FTP' 1>/dev/null 2>&1
#ufw allow proto tcp to any port 2000:2020 comment 'FTP Passive' 1>/dev/null 2>&1
echo "Adding Web Server rules"
#ufw allow proto tcp to any port 80 comment 'HTTP Service' 1>/dev/null 2>&1
#ufw allow proto tcp to any port 8080 comment 'HTTP Alt Service' 1>/dev/null 2>&1
#ufw allow proto tcp to any port 443 comment 'HTTPS Service' 1>/dev/null 2>&1
echo "Enabling firewall"
echo y | ufw enable 1>/dev/null 2>&1
echo "Firewall enabled and all rules have been configured."

```

---

### Post by LHammonds on 2020-05-03
[SIZE=4]Fail2Ban[/SIZE]

Fail2Ban is an intrusion prevention system that can be used to protect servers from different kinds of attacks.

Fail2ban scans log files for various services, such as SSH, FTP, SMTP, Apache and block the IP address that makes too many password failures.

[SIZE=4]Install Fail2Ban[/SIZE]
```
sudo apt install fail2ban
```

[SIZE=4]Configure Fail2Ban[/SIZE]
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
#ignoreself = true
#ignoreip = 127.0.0.1/8 ::1
ignorecommand =
bantime  = 10m
findtime  = 10m
maxretry = 5
filter = %(__name__)s[mode=%(mode)s]
destemail = root@localhost
sender = root@<fq-hostname>
mta = sendmail
action = %(action_)s
[sshd]
port    = ssh
logpath = %(sshd_log)s
backend = %(sshd_backend)s

```

Now create a local jail file that will be used to override any settings in the default that we want changed or added.

For this example, we will ignore all failed login attempts from our local server subnet (192.168.107.xxx) and a specific admin workstation (192.168.1.69)

```
sudo touch /etc/fail2ban/jail.local
sudo chown root:root /etc/fail2ban/jail.local
sudo chmod 644 /etc/fail2ban/jail.local
sudo vi /etc/fail2ban/jail.local
```

Let's make some changes that fit our server as it stands right now:

```

[DEFAULT]
## 127.0.0.1/8 = ignore login failures on the local machine
## 192.168.107.0/24 = ignore login failures on an entire subnet
## 192.168.1.69 = ignore login failures for this specific IP
ignoreip = 127.0.0.1/8 192.168.107.0/24 192.168.1.69
bantime = 30m
## "findtime" is the length of time between login attempts before a ban is set.
findtime = 10m
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
sudo touch /etc/fail2ban/action.d/sendemail-whois-lines.conf
sudo chown root:root /etc/fail2ban/action.d/sendemail-whois-lines.conf
sudo chmod 644 /etc/fail2ban/action.d/sendemail-whois-lines.conf
sudo vi /etc/fail2ban/action.d/sendemail-whois-lines.conf
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

[SIZE=4]Useful commands[/SIZE]

Here are a few of the most-used commands.  Reference: [Fail2Ban commands]("https://www.fail2ban.org/wiki/index.php/Commands").
Stop, start or restart the fail2ban service:
```
sudo systemctl stop fail2ban
sudo systemctl start fail2ban
sudo systemctl restart fail2ban
```

This command will show which services are being watched (sshd in this example):
```
sudo fail2ban-client status
```
Example output:
```

Status
|- Number of jail:      1
`- Jail list:   sshd

```

This command gets the status on the sshd service being watched:
```
sudo fail2ban-client status sshd
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

[SIZE=4]Firewall Rules[/SIZE]

Installing Fail2Ban will create the following firewall rules which can be seen with the following command:

```
sudo iptables -S
```

```

-N f2b-sshd
-A INPUT -p tcp -m multiport --dports 22 -j f2b-sshd
-A f2b-sshd -j RETURN

```

If you have already enabled Uncomplicated Firewall (UFW), you will see several ufw-prefixed rules as well.

[SIZE=4]Test Fail2Ban[/SIZE]

To manually ban an IP:
```
sudo fail2ban-client set sshd banip 192.168.1.69
```

To manually unban an IP:
```
sudo fail2ban-client set sshd unbanip 192.168.1.69
```

On the server, run the following command to watch the Fail2Ban log file:
```
tail -f /var/log/fail2ban.log
```

On a different machine (that is not on your ignoreip list), try to ssh into your server with the incorrect ID or password multiple times until you have reached the "maxretry" attempts and you get locked out...thus causing an entry in the log.

[SIZE=4]References[/SIZE]

[Fail2Ban Manual]("http://www.fail2ban.org/wiki/index.php/MANUAL_0_8")

---

### Post by LHammonds on 2020-05-03
[SIZE=4]SSH Public and Private Keys[/SIZE]
 
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
[*]Just below that line, add the following:
```
PermitRootLogin yes
``` 
[*]You might also need to add root to the AllowUsers line:
```
AllowUsers administrator root
``` 
[*]Restart SSH:
```
systemctl restart ssh
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
ssh-copy-id root@[COLOR=red]srv-database[/COLOR]
ssh-copy-id root@[COLOR=red]srv-wiki[/COLOR]
ssh-copy-id root@[COLOR=red]srv-ftp[/COLOR]
ssh-copy-id root@[COLOR=red]srv-nagios[/COLOR]
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
[*]Just below that line, delete the following:
```
PermitRootLogin yes
``` 
[*]Restart SSH:
```
systemctl restart ssh
``` 
[*]Do the same for each of your servers 
[/LIST]


If you have other accounts you want to use across the servers (such as a low-rights account), you can do the same thing as the above except you probably won't need to do the unlock/lock steps for the account if you can already login with that account.

Now you should be able to securely copy files back and forth between servers without having to type a password.

Example:
```
scp /etc/hosts root@[COLOR=red]srv-database[/COLOR]:/tmp/hosts.txt
```

---

### Post by LHammonds on 2020-05-03
[SIZE=4]SUDO Warning Message[/SIZE]


[LIST=1]
[*]Enable the default warning message whenever "sudo" is used.  Edit sudoers file by typing:
```
sudo EDITOR=vim visudo
```
Add the following line near the other defaults (instead of "always" you can use "once" too):
```
Defaults lecture=always
``` 
[*]To make sure the syntax of the edited file is not incorrect, check it with the following command and look for "parsed: OK"
NOTE: If you mess up the syntax in this file, it can cause you problems using the "sudo" command.
```
sudo visudo -c
``` 
[*]To customize the message, you can create a custom message file.  Edit the lecture file by typing:
```
sudo touch /etc/lecture
sudo chown root:root /etc/lecture
sudo chmod 644 /etc/lecture
sudo vi /etc/lecture
```
Add the following text (which is default) or whatever you want:
```
We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.
``` 
[*]Now point to the newly-created file in the sudoers config file.
```
sudo EDITOR=vim visudo
```
```
Defaults lecture_file=/etc/lecture
``` 
[/LIST]


[SIZE=4]SSH Login Message[/SIZE]

[LIST=1]
[*]To enable login banners that are displayed before entering a password, edit the following:
```
sudo vi /etc/issue.net
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
sudo vi /etc/ssh/sshd_config
```
```
Banner /etc/issue.net
``` 
[*]Restart the SSH service:
```
sudo systemctl restart sshd
``` 
[/LIST]


[SIZE=4]Custom Login Logo[/SIZE]

If you want an Ubuntu Logo and additional info added to your login, visit [this thread]("http://viewtopic.php?f=40&t=259").

[IMG]https://images.hammondslegacy.com/linux/Ubuntu_2004_Logo_ASCII.png[/IMG]

---

### Post by LHammonds on 2020-05-03
[SIZE=4]Configure Ubuntu for File Sharing[/SIZE]

This file sharing section is optional but can be handy if you need to swap files between the Linux server and a Windows machine.

This documentation will utilize this share for passing pre-configured files (configs, scripts, etc.) to make it faster/easier during installation.


[LIST=1]
[*]Start the Ubuntu server and connect using PuTTY. 
[*]At the login prompt, login with your administrator account ([COLOR=red]**administrator**[/COLOR] / [COLOR=red]**myadminpass**[/COLOR]) 
[*]Install Samba by typing the following:
```
sudo apt -y install samba cifs-utils
```
NOTE: To share a folder with Windows, you just need the **samba** package, to connect to a Windows share, you need both **samba** and **cifs-utils** 
[*]Type the following commands:
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
sudo mkdir -p /srv/samba/share
sudo chown nobody:nogroup /srv/samba/share/
sudo chmod 0777 /srv/samba
sudo chmod 0777 /srv/samba/share
``` 
[*]Edit the configuration file:
```
sudo vi /etc/samba/smb.conf
``` 
[*]Change:
```
workgroup = WORKGROUP
```
to:
```
workgroup = [COLOR=red]work[/COLOR]
``` (you are using the domain alias) 
[*]Add the following section to the end of the file:
```
[share]
comment = Ubuntu File Server Share
path = /srv/samba/share
browsable = yes
guest ok = yes
read only = no
create mask = 0660
directory mask = 0755
``` 
[*]Save and exit the file. 
[*]Restart the samba services to utilize the new configuration by typing:
```
sudo systemctl restart smbd
sudo systemctl restart nmbd
``` 
[*]Update your firewall rules to allow Samba file sharing:
```

sudo ufw allow proto tcp to any port 135,139,445 comment 'Samba Share'
sudo ufw allow proto udp to any port 137,138 comment 'Samba Share'

``` 
[*]You should now be able to click Start --> Run and type **\\[COLOR=red]srv-ubuntu[/COLOR]** or **\\[COLOR=red]192.168.107.2[/COLOR]** [COLOR=green]{ENTER}[/COLOR] and see an explorer window with a *Share* folder.  Drag-n-drop a file into the *Share* folder.  If it worked, it will not display an error message and you should be able to view it from the server by typing **ls -l /srv/samba/share/** 
[*]Shutdown and power off the server by typing **shutdown -P now** [COLOR=green]{ENTER}[/COLOR] 
[*]In VM menu, select VM --> Snapshot --> Take Snapshot.  Give it a name like **STEP 4** and description of **Ubuntu Server 20.04 LTS, File share configured, Static IP: [COLOR=red]192.168.107.2[/COLOR]**.  The Snapshot Manager should now have a nice hierarchy of snapshots (STEP 1 --> STEP 2 --> STEP 3 --> STEP 4 --> You are here) 
[/LIST]

---

### Post by LHammonds on 2020-05-03
[SIZE=4]NFS Mount (Sharing among Linux)[/SIZE]

If you want to share files between Linux servers, you can use NFS.  Here is how you can do that.

On the machine that will host the files to be shared:


[LIST=1]
[*]Install the required software:
```
sudo apt install nfs-kernel-server
``` 
[*]Configure a folder to be shared:
```
sudo touch /etc/exports
sudo chown root:root /etc/exports
sudo chmod 644 /etc/exports
sudo vi /etc/exports
``` 
[*]Add the following line, adjust as necessary and then save and close the file:
```
/srv/samba/share        *(rw,sync,no_root_squash,no_subtree_check)
``` 
[*]Make the folder and configure ownership and permissions:
```
sudo mkdir -p /srv/samba/share
sudo chown nobody:nogroup /srv/samba/share
sudo chmod 777 /srv/samba/share
``` 
[*]Restart services for changes to take effect:
```
sudo systemctl restart nfs-kernel-server
``` 
[*]If your UFW firewall is enabled, you will need to open port 2049 TCP and UDP.  Example:
```
sudo ufw allow proto tcp to any port 2049 comment 'NFS Share'
sudo ufw allow proto udp to any port 2049 comment 'NFS Share'
``` 
[/LIST]


On the machine that will connect to the other remotely:

[LIST=1]
[*]Install the required software:
```
sudo apt install nfs-common
``` 
[*]Create the mount point folder:
```
sudo mkdir -p /mnt/nfs
sudo touch /mnt/nfs/offline.txt
``` 
[*]Now connect to the server. We will assume the server's IP doing the sharing is [COLOR=red]192.168.107.100[/COLOR] in this example.
```
sudo mount 192.168.107.100:/srv/samba/share /mnt/nfs
``` 
[*]If the mount was successful, you will not see the "offline.txt" file we created at the mount point. 
[*]To disconnect from the server, type the following:
```
sudo umount /mnt/nfs
``` 
[*]If the unmount was successful, you will see the "offline.txt" file. 
[/LIST]

---

### Post by LHammonds on 2020-05-03
[SIZE=4]Configure Windows Server as a Remote Mount Point[/SIZE]

If you have a Windows 2008/2012 server that serves as your offsite backup repository, this section describes how to configure and mount the remote server for storage use.

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

[SIZE=4]Create a share on a Windows 2008/2012 server[/SIZE]


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
[/LIST]

[SIZE=4]Create an NFS mount to the Windows 2008/2012 server[/SIZE]

Connecting to a Windows share requires the **samba** and **cifs-utils** packages to be installed.  If you did not install them (from a prior section), type **apt -y install samba cifs-utils**


[LIST=1]
[*]At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR]) 
[*]Type the following commands:
```
sudo mkdir -p /mnt/backup
sudo chown root:root /mnt/backup
sudo chmod 0755 /mnt/backup
sudo echo "This file is used to tell if the mount is active or not" > /mnt/backup/offline.txt
sudo chown root:root /mnt/backup/offline.txt
sudo chmod 0444 /mnt/backup/offline.txt
sudo touch /etc/cifspw
sudo chown root:root /etc/cifspw
sudo chmod 0600 /etc/cifspw
sudo vi /etc/cifspw

```
Add the following text, save and exit the file:
```
username=[COLOR=red]ubuntushare[/COLOR]
domain=[COLOR=red]work[/COLOR]
password=[COLOR=red]ubuntupassword[/COLOR]
``` 
[*]Type **sudo vi /etc/hosts** and add the following line anywhere in the file:
```
[COLOR=red]192.168.107.218    srv-backup[/COLOR]
``` 
[*]At this point, you might want to type **ping [COLOR=red]srv-backup[/COLOR]** to make sure you typed the right IP address as well as seeing a good response. 
[*]To mount this system for backups, type the following command:
```
sudo mount -t cifs //srv-backup/ubuntu /mnt/backup --options vers=2.0,nouser,rw,nofail,noexec,credentials=/etc/cifspw
``` 
[*]To test it, type **cp /etc/hosts /mnt/backup/hosts.txt** and look on the Windows server and see if the file shows up.  Then type **rm /mnt/backup/hosts.txt** and verify that the file was deleted on the windows server. 
[*]This would also be a good time to verify that you cannot see the "offline.txt" file that will be used by the backup script. Type **ls -l /mnt/backup/*.txt** 
[*]To dismount the windows share, type the following command:
```
sudo umount /mnt/backup
``` 
[/LIST]

The scripts will call a common mount and unmount function to connect to this share only when needed.

However, if you would rather have it mounted all the time (even after a reboot), do the following (but remember to not use the mount/umount functions in the scripts later):


[LIST=1]
[*]Type **sudo vi /etc/fstab** and add the following line at the bottom of the file:
```
//[COLOR=red]srv-backup/ubuntu[/COLOR]    /mnt/backup    cifs vers=2.0,nouser,rw,nofail,noexec,credentials=/etc/cifspw    0    0
``` 
[*]Type **sudo mount -a** and if it does not spew out any error messages, it will quietly mount the share. 
[*]To test it, type **cp /etc/hosts /mnt/backup/hosts.txt** and look on the Windows server and see if the file shows up.  Then type **rm /mnt/backup/hosts.txt** and verify that the file was deleted on the windows server. 
[*]If you need to unmount it, type **sudo umount /mnt/backup** and it will remain unmounted until you reboot.  To make it permanent, you need to remove the line you added in the /etc/fstab file. 
[/LIST]

Sometimes it is helpful during tests to manually toggle the mount on or off so here is a script you might find helpful.  You can find the contents of "standard.conf" file in the scripting section.

togglemount.sh
```
#!/bin/bash
#############################################
## Name          : togglemount.sh
## Version       : 1.3
## Date          : 2020-05-01
## Author        : LHammonds
## Compatibility : Ubuntu Server 10.04 thru 20.04 LTS
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
## 2019-07-18 LTH Updated reference file online.txt to offline.txt
## 2020-05-01 LTH Test file now uses the common variable name.
#############################################

## Import common variables and functions. ##
source /var/scripts/common/standard.conf
ErrorFlag=0

if [ -f ${OffsiteTestFile} ]; then
  echo "Remote share is not mounted.  Mounting share now..."
  f_mount
  sleep 2
  if [ -f ${OffsiteTestFile} ]; then
    echo "Mount failed.  Listing contents:"
    ErrorFlag=1
  else
    echo "Mount successful.  Listing contents:"
  fi
else
  echo "Remote share is mounted.  Dismounting share now..."
  f_umount
  sleep 2
  if [ -f ${OffsiteTestFile} ]; then
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

### Post by LHammonds on 2020-05-03
[SIZE=4]Backup Partitions Using LVM Snapshots and FSArchiver[/SIZE]

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
## Version : 1.4
## Date : 2020-01-01
## Author : LHammonds
## Purpose : Backup partitions
## Compatibility : Verified on Ubuntu Server 12.04 thru 20.04 LTS
##                 Verified with fsarchiver 0.8.4)
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
## 2020-01-01 1.4 LTH Remove any prior temp snapshots before starting.
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

## Remove old snapshot from a prior run if it exists.
lvremove --force ${TempLV} > /dev/null 2>&1

StartTime="$(date +%s)"
echo "`date +%Y-%m-%d_%H:%M:%S` - Backup started." >> ${LogFile}

f_archive_fs boot /dev/sda1
f_archive_vol root
f_archive_vol var
f_archive_vol tmp
f_archive_vol home
#f_archive_vol usr
#f_archive_vol srv
#f_archive_vol opt
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

/var/log/abc-back-parts.log
```
2018-04-20_17:11:14 - Backup started.
2018-04-20_17:11:25 --- Created: /bak/srv-ubuntu-boot.fsa, 63M
2018-04-20_17:11:25 --- Copying archive file to offsite location.
2018-04-20_17:12:29 --- Created: /bak/srv-ubuntu-root.fsa, 254M
2018-04-20_17:12:29 --- Copying archive file to offsite location.
2018-04-20_17:13:20 --- Created: /bak/srv-ubuntu-var.fsa, 74M
2018-04-20_17:13:20 --- Copying archive file to offsite location.
2018-04-20_17:13:32 --- Created: /bak/srv-ubuntu-tmp.fsa, 1M
2018-04-20_17:13:32 --- Copying archive file to offsite location.
2018-04-20_17:13:37 --- Created: /bak/srv-ubuntu-home.fsa, 1M
2018-04-20_17:13:37 --- Copying archive file to offsite location.
2018-04-20_17:15:47 --- Total backup time: 0 hour(s) 4 minute(s) 33 second(s)
2018-04-20_17:15:47 - Backup Finished.

```

An example email notification when a fatal error occurred:
```
From: admin@mydomain.com
Sent: Friday, April 20, 2018 5:20:45 PM
To: lhammonds@mydomain.com
Subject: ERROR: Backup partitions script aborted

This script tried to run but detected the lock file: /tmp/abc-back-parts.lock

Please check to make sure the file does not remain when backup partitions is not actually running.

If you find that the script is not running/hung, you can remove it by typing 'rm /tmp/abc-back-parts.lock'

Server: srv-ubuntu
Program: /var/scripts/prod/back-parts.sh
Log: /var/log/abc-back-parts.log
```

An example email notification when no errors occur and email notifications turned on:
```
From: admin@mydomain.com
To: lhammonds@mydomain.com
Sent: Friday, April 20, 2018 5:20:45 PM
Subject: Backup Completed

INFO: The partition backup job has completed without any errors.

Server: srv-ubuntu
Program: /var/scripts/prod/back-parts.sh
Log: /var/log/abc-back-parts.log
```

[SIZE=4]Troubleshooting Snapshot Failures[/SIZE]

If the snapshot volume could not be automatically removed, here is how you do it:

```
sudo dmsetup ls
```
```

[COLOR=red]LVG-tempsnap[/COLOR]    (253:7)
LVG-root        (253:0)
LVG-bak (253:3)
LVG-tmp (253:2)
LVG-root-real   (253:5)
[COLOR=red]LVG-tempsnap-cow[/COLOR]        (253:6)
LVG-var (253:1)
LVG-home        (253:4)

```

```

sudo dmsetup remove LVG-tempsnap
sudo dmsetup remove LVG-tempsnap-cow
sudo lvremove LVG-tempsnapshot

```

The script can fail for multiple reasons...mostly due to lack of space.

Use "vgdisplay" to make sure you have enough free/unallocated space in the volume group.  Your max tempsnap size cannot exceed the amount of unallocated/unused space in the volume group.

Make sure you have enough room in /bak to hold the partitions as well as your remote location.  A new server without any software/data installed will take up at least 652 MB of space when archived.

[SIZE=4]Backup Test[/SIZE]

Before the partitions are backed on your server, create a couple of empty test files to verify that the restore in the next section will work.

Type the following commands:

```
touch /important.txt
touch /home/administrator/important.txt
```

Make sure the above files are included in your backup before testing the restore in the next section.

---

### Post by LHammonds on 2020-05-03
[SIZE=4]Restore Partitions Using SystemRescueCD and FSArchiver[/SIZE]

Partitions cannot be mounted when restoring to them. If services can be stopped that use files on a specific partition, it can be unmounted and restored. However, the root partition can never be restored while the server is online so these instructions will cover the common denominator which requires taking the server offline.

The server needs to be booted up with a CD but not just any CD will do because it needs to have FSArchiver on it. For this document, the ISO image from [www.sysresccd.org]("http://www.sysresccd.org") will be used.

Once downloaded, the ISO can be burned to a CD-ROM disc or uploaded to your ISO repository such as a LUN. VMware and VirtualBox can attach an ISO image and mount it in the CD-ROM device to allow the virtual machine to boot the ISO image.

For this example, files on the root and home partitions will be restored using this summarized procedure:

[LIST=1]
[*]Boot the system using the RescueCD. 
[*]Mount the bak partition which contains the backup archives. 
[*]Verify that the backup archives are in good condition. 
[*]Restore the partitions. 
[*]Mount the root and home partitions. 
[*]Verify the restore worked. 
[*]Unmount the partitions. 
[*]Reboot the system. 
[/LIST]


Be sure the partitions have been backed up and the files are sitting in the /bak volume.

```
ls -l /bak
```

```

total 1035280
drwx------ 2 root root     16384 Apr 30 13:31 lost+found
-rw------- 1 root root 156167681 May  3 15:33 srv-ubuntu-boot.fsa
-rw------- 1 root root        59 May  3 15:33 srv-ubuntu-boot.md5
-rw------- 1 root root       747 May  3 15:33 srv-ubuntu-boot.txt
-rw------- 1 root root     11113 May  3 15:40 [COLOR=red]srv-ubuntu-home.fsa[/COLOR]
-rw------- 1 root root        59 May  3 15:40 srv-ubuntu-home.md5
-rw------- 1 root root       749 May  3 15:40 srv-ubuntu-home.txt
-rw------- 1 root root 837941885 May  3 15:38 [COLOR=red]srv-ubuntu-root.fsa[/COLOR]
-rw------- 1 root root        59 May  3 15:38 srv-ubuntu-root.md5
-rw------- 1 root root       750 May  3 15:38 srv-ubuntu-root.txt
-rw------- 1 root root      7142 May  3 15:40 srv-ubuntu-tmp.fsa
-rw------- 1 root root        58 May  3 15:40 srv-ubuntu-tmp.md5
-rw------- 1 root root       745 May  3 15:40 srv-ubuntu-tmp.txt
-rw------- 1 root root  65930756 May  3 15:40 srv-ubuntu-var.fsa
-rw------- 1 root root        58 May  3 15:40 srv-ubuntu-var.md5
-rw------- 1 root root       748 May  3 15:40 srv-ubuntu-var.txt
```

As a test of the restore, let's delete the two text files created in the previous section:

```
rm /important.txt
rm /home/administrator/important.txt
```

These files should have been included in the backup image. When the restore is complete, these files should return.

Insert the SystemRescueCD CDROM (or mount the ISO image) and boot the server with it.

Here is the 1st screen:
[IMG]https://images.hammondslegacy.com/linux/SystemRescueCD613-menu1.png[/IMG]

Option #1 was chosen (SystemRescueCd: default boot options)

The next screen takes you to the command prompt:

[IMG]https://images.hammondslegacy.com/linux/SystemRescueCD613-menu2.png[/IMG]

Show what partitions the system has by using fsarchiver.

[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **fsarchiver probe simple**
```

[======DISK======] [=============NAME==============] [====SIZE====] [MAJ] [MIN]
[sda             ] [VBOX HARDDISK                  ] [    25.00 GB] [  8] [  0]
[sr0             ] [CD-ROM                         ] [   675.00 MB] [ 11] [  0]

[=====DEVICE=====] [==FILESYS==] [======LABEL======] [====SIZE====] [MAJ] [MIN]
[loop0           ] [squashfs   ] [<unknown>        ] [   620.12 MB] [  7] [  0]
[sda1            ] [ext4       ] [boot             ] [   953.00 MB] [  8] [  1]
[sda5            ] [LVM2_member] [<unknown>        ] [    24.87 GB] [  8] [  5]
[[COLOR=red]dm-0[/COLOR]            ] [ext4       ] [[COLOR=red]root[/COLOR]             ] [     6.00 GB] [254] [  0]
[dm-1            ] [ext4       ] [var              ] [     3.00 GB] [254] [  1]
[dm-2            ] [ext4       ] [tmp              ] [     1.00 GB] [254] [  2]
[[COLOR=red]dm-3[/COLOR]            ] [ext4       ] [[COLOR=red]bak[/COLOR]              ] [     4.00 GB] [254] [  3]
[[COLOR=red]dm-4[/COLOR]            ] [ext4       ] [[COLOR=red]home[/COLOR]             ] [     1.00 GB] [254] [  4]

```

Mount the bak partition which contains the backup archives.

[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **mkdir /bak**
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **mount --read-only [COLOR=red]/dev/dm-3[/COLOR] /bak**
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **ls -l /bak**
```

total 1035280
drwx------ 2 root root     16384 Apr 30 13:31 lost+found
-rw------- 1 root root 156167681 May  3 15:33 srv-ubuntu-boot.fsa
-rw------- 1 root root        59 May  3 15:33 srv-ubuntu-boot.md5
-rw------- 1 root root       747 May  3 15:33 srv-ubuntu-boot.txt
-rw------- 1 root root     11113 May  3 15:40 [COLOR=red]srv-ubuntu-home.fsa[/COLOR]
-rw------- 1 root root        59 May  3 15:40 srv-ubuntu-home.md5
-rw------- 1 root root       749 May  3 15:40 srv-ubuntu-home.txt
-rw------- 1 root root 837941885 May  3 15:38 [COLOR=red]srv-ubuntu-root.fsa[/COLOR]
-rw------- 1 root root        59 May  3 15:38 srv-ubuntu-root.md5
-rw------- 1 root root       750 May  3 15:38 srv-ubuntu-root.txt
-rw------- 1 root root      7142 May  3 15:40 srv-ubuntu-tmp.fsa
-rw------- 1 root root        58 May  3 15:40 srv-ubuntu-tmp.md5
-rw------- 1 root root       745 May  3 15:40 srv-ubuntu-tmp.txt
-rw------- 1 root root  65930756 May  3 15:40 srv-ubuntu-var.fsa
-rw------- 1 root root        58 May  3 15:40 srv-ubuntu-var.md5
-rw------- 1 root root       748 May  3 15:40 srv-ubuntu-var.txt
```

Verify that the backup archives are in good condition:

[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **md5sum --check /bak/srv-ubuntu-root.md5**
```
/bak/srv-ubuntu-root.fsa: [COLOR=red]OK[/COLOR]
```
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **md5sum --check /bak/srv-ubuntu-home.md5**
```
/bak/srv-ubuntu-home.fsa: [COLOR=red]OK[/COLOR]
```

Restore the root partition:

[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **fsarchiver restfs --cryptpass="[COLOR=red]abc123[/COLOR]" /bak/srv-ubuntu-root.fsa id=0,dest=[COLOR=red]/dev/dm-0[/COLOR]**
```
Statistics for filesystem 0
* files successfully processed:....regfiles=96032, directories=19993, symlinks=7266, hardlinks=9, specials=8
* files with errors:...............regfiles=0, directories=0, symlinks=0, hardlinks=0, specials=0
```

Restore the home partition:

[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **fsarchiver restfs --cryptpass="[COLOR=red]abc123[/COLOR]" /bak/srv-ubuntu-home.fsa id=0,dest=[COLOR=red]/dev/dm-4[/COLOR]**
```
Statistics for filesystem 0
* files successfully processed:....regfiles=11, directories=5, symlinks=0, hardlinks=0, specials=0
* files with errors:...............regfiles=0, directories=0, symlinks=0, hardlinks=0, specials=0
```

Mount the root and home partitions:

[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **mkdir /mnt/root**
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **mkdir /mnt/home**
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **mount --read-only [COLOR=red]/dev/dm-0[/COLOR] /mnt/root**
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **mount --read-only [COLOR=red]/dev/dm-4[/COLOR] /mnt/home**

Verify the restore worked:

[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **ls -l /mnt/root/import***
```
-rw-r--r-- 1 root root 0 May  3 17:00 [COLOR=red]important.txt[/COLOR]
```
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **ls -l /mnt/home/administrator/import***
```
-rw-r--r-- 1 root root 0 May  3 17:00 [COLOR=red]important.txt[/COLOR]
```

Unmount the partitions:

[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **umount /mnt/root**
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **umount /mnt/home**
[COLOR=lime]root@sysresccd[/COLOR] [COLOR=blue]/root[/COLOR] % **umount /bak**
 
Eject the CDROM/ISO and reboot the server.

If it worked right, the server will boot up (we restored the root file system) and the test files should have been restored.

NOTE: If you noticed any ext file systems that had <unknown> labels, you can update them using the tune2fs command which makes identification easier when restoring.

Example 1:
```
sudo tune2fs /dev/sda1 -L boot
```

Example 2:
```
sudo tune2fs /dev/dm-0 root
```

---

### Post by LHammonds on 2020-05-03
[SIZE=4]Migrating users/groups from one server to another[/SIZE]

**[COLOR=red]WARNING:[/COLOR]** These migration commands are thoroughly tested by me...just jotting down these research notes for future testing.

_Commands to run on old server_

Copy accounts to passwd.mig using awk to filter out system accounts (i.e. only copy user accounts)
```
sudo awk -v LIMIT=1000 -F: '($3>=LIMIT) && ($3!=65534)' /etc/passwd > /tmp/passwd.mig
```

Copy groups to group.mig
```
sudo awk -v LIMIT=1000 -F: '($3>=LIMIT) && ($3!=65534)' /etc/group > /tmp/group.mig
```

Copy shadow to shadow.mig
```
sudo awk -v LIMIT=1000 -F: '($3>=LIMIT) && ($3!=65534) {print $1}' /etc/passwd | tee - |egrep -f - /etc/shadow > /tmp/shadow.mig
```

Copy gshadow to gshadow.mig (rarely used):
```
sudo cp /etc/gshadow /tmp/gshadow.mig
```

Backup the home directories.
```
sudo tar -zcvpf /tmp/home.tar.gz /home
```

If you have Samba users...
```
sudo cp /etc/samba/smb.conf /tmp/smb.mig
sudo cp /etc/samba/smbusers /tmp/smbusers.mig
sudo cp /etc/samba/smbpasswd /tmp/smbpasswd.mig
```

Transfer the migration files to new server.
```
sudo scp /tmp/*.mig administrator@newserver:/tmp/.
sudo scp /tmp/home.tar.gz administrator@newserver:/tmp/.
```

_Commands to run on new server_

Backup current files (and their backups).
```
sudo mkdir /root/save
sudo cp /etc/passwd /etc/passwd- /etc/shadow /etc/shadow- /etc/group /etc/group- /etc/gshadow /etc/gshadow- /root/save
```

If you have Samba users, backup your current files.
```
sudo cp /etc/samba/smb.conf /etc/samba/smbusers /etc/samba/smbpasswd /root/save
```

Merge/Overwrite files.
```
sudo cat /tmp/passwd.mig >> /etc/passwd
sudo cat /tmp/group.mig >> /etc/group
sudo cat /tmp/shadow.mig >> /etc/shadow
sudo cp /tmp/gshadow.mig /etc/gshadow
```

Ensure file ownership and permissions are correct.
```

sudo chown root:shadow /etc/shadow /etc/gshadow
sudo chmod 640 /etc/shadow /etc/gshadow
sudo chown root:root /etc/passwd /etc/group
sudo chmod 644 /etc/passwd /etc/group

```

If you have Samba users...
```

sudo cp /tmp/smb.mig /etc/samba/smb.conf
sudo cp /tmp/smbusers.mig /etc/samba/smbusers
sudo cp /tmp/smbpasswd.mig /etc/samba/smbpasswd
```

Extract home directories.
```
cd /
sudo tar -zxvf /tmp/home.tar.gz
```

Reboot system for new user accounts to take effect.
```
sudo reboot
```

---

### Post by LHammonds on 2020-05-03
[SIZE=4]Replacing a server with a new one[/SIZE]

If you want to keep SSH keys and the fingerprint from changing when swapping out an old server for a new one (e.g. old FTPS server to new FTPS which interfaces with many 3rd-party vendors), these are the steps needed to keep the system looking the same.

The old server name and the new server name must match.  Example: srv-ftps

Make sure the sshd configuration files on both servers are pointing to the same files (filenames and paths)

```
sudo vi /etc/ssh/sshd_config
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
sudo scp /etc/ssh/ssh_host* administrator@newserver:/tmp/.
```

_Commands to run on new server_

Backup existing files
```

sudo mkdir /root/ssh-backup
sudo cp /etc/ssh/ssh_host* /root/ssh-backup/.
```

Set correct file ownership and permissions
```

sudo chown root:root /tmp/ssh_host*
sudo chmod 600 /tmp/ssh_host*
sudo chmod 644 /tmp/ssh_host*.pub

```

Move and overwrite files to correct location
```
sudo mv /tmp/ssh_host* /etc/ssh/.
```

Restart SSH daemon
```
sudo systemctl restart ssh
```

You will also want to copy over individual user's public keys in their ~/.ssh/authorized_keys but if you transferred the contents of the /home folder, this was already done.

---

### Post by LHammonds on 2020-05-03
[SIZE=4]Boot Issues[/SIZE]

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

[SIZE=4]Disk Space Issues[/SIZE]

To quickly find out status on partition sizes, use this command:
```
df -h
```

To help find out what is eating up your space in a particular folder, you can use this command:
```
du -sh /path/to/folder
```

To make faster use of du, use the ncdu utility I recommended to install in an earlier section.  If you start at the root like the example below, you can use your arrow keys to select the problematic folders and keep drilling down until you find the culprit you are looking for.  It automatically sorts the results so you are typically already on the biggest folder and just need to press ENTER to drill down to the next folder.
```
ncdu /
```

---

