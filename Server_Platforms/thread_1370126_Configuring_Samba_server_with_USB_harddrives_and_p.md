---
title: "Configuring Samba server with USB harddrives and printer"
date: 2010-01-01
forum: Server Platforms
---

### Post by Clark3934 on 2010-01-01
I'm running Ubuntu 9.10 Server Edition with the 2.6.31-16-generic-pae kernel.  I am attempting to share three harddrives and a printer to my LAN using samba.  Two of the harddives (formatted ntfs and FAT32) and the printer (HP Officejet 5610) are attached via usb.  The third harddive, formatted ext4, is attached  via SATA.

I have installed the ubuntu-desktop, and have it set to log-in automatically with an administrator account.  I intend to manage the computer remotely via SSH, and the physical security of the LAN shouldn't be a problem.

I am hoping to share all of the harddrives and printer as fully read/write resources to the local network, but I keep running into trouble.  I wish to do this as simply as possible--allowing multiple users to access the drives and printer from computers running Ubuntu and Windows XP/Vista/7, all while allowing complete guest access of the HDDs and printer to any new computer/user who might join the network.

I am having a terrible time getting all of the client operating systems to have full access, getting the drives to automount to the server on boot, and allowing guest printing... all while allowing an administrative account to be logged in to the server.

What I have so far in my Samba configuration (/etc/samba/smb.conf):
```
[global]
	load printers = yes
	allow hosts = 127.0.0. 192.168.1.
	netbios name = SERVER
	printing = cups
	remote announce = 192.168.1.255
	workgroup = WORKGROUP
	printcap name = cups
	security = share
	create mask = 664
	directory mask = 775

[printers]
	comment = All Printers
	browseable = yes
	printable = yes
	path = /var/spool/samba

[1TbBlack]
	comment = 1 TB Black External Harddrive
	path = /media/1TbBlack
	force user = sambashare
	force group = sambashare
	read only = No
	guest ok = Yes

[300GBGRAY]
	comment = 300 GB Gray Seagate Harddrive
	path = /media/300GBGRAY
	force user = sambashare
	force group = sambashare
	read only = No
	guest ok = Yes
```

I have tried having the USB drives automount by adding them to fstab (/etc/fstab):
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/server-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=381a2473-2c19-4f6d-9370-a4debfb68d90 /boot           ext2    defaults        0       2
/dev/mapper/server-swap_1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#External HDDs
#/dev/sdc1 (1TbBlack)
UUID=C0307DFA307DF82C	/media/1TbBlack	ntfs-3g	defaults,locale=en_US.utf8	0	0
#/dev/sde1 (300GBGRAY)
UUID=1DD9-1023	/media	vfat	user,rw,umask=111,dmask=000	0	0
```

I have tried installing the 'usbmount' package, but this still doesn't work.  At one point, before fstabing, I was able to get printing to work from a couple of separate machines, but I have never been able to get full HDD read/write access.  I figured it was because they were only mounted when the server admin account logged in, thus making it the owner of the file, and overriding samba settings for guest access.  I thought I might fix this by fstab automounting.

I figured I would make some type of sharing group, so I created the user "sambashare" as a normal user account, and put it in the "sambashare" group, along with my admin user.  I then made "sambashare" the owner user and group of all the mount points (/media/1TbBlack, etc.) with 0775 permissions.  I followed the directions here: [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html) and ran the command "smbpasswd -a sambashare" with a password.

I am now unable to access / see anything from any of my network computers, and I'm really stuck about what to do next.  I might of gone about doing this wrong, as I followed tons of different guides from all over the place.  

Does anyone have any advice on where I should go from here?  Or, even better, is there a good step-by-step guide on how to do this with the 9.10 fstab issues in mind?  

Thanks!

---

