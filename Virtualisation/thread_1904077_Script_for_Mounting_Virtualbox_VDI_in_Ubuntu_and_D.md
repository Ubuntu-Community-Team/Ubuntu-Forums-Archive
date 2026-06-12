---
title: "Script for Mounting Virtualbox VDI in Ubuntu and Debian"
date: 2012-01-04
forum: Virtualisation
---

### Post by japzone on 2012-01-04
I've made a Script for making the whole process of Mounting Virtualbox VDI disks in Ubuntu less of a pain. This script should work in any Debian OS but I can't garuntee it as I have yet to test it on anything but Ubuntu.

The Script has a lot of bells and whistles so let me know if you find a Bug or have other suggestions.

**Update:** VDIMount has a Permanent home! You can now follow any updates and Subscribe to the RSS feed via it's new page on FileTrip here: [http://filetrip.net/pc-downloads/other-files/latest-vdimount-mount-virtualbox-disk-f28663.html](http://filetrip.net/pc-downloads/other-files/latest-vdimount-mount-virtualbox-disk-f28663.html)

_Features:_
-Optional Install to /usr/bin to allow easy command use(ie: just type vdimount to use it)(If you say no but wish to install it later simply use th "rs" option in the script)
-AutoCheck if needed Dependencies are Installed
-Give Option to Install and Setup needed Dependencies if not Installed
-Mode Chooser
-[s]Drag'n'Drop abilities for selecting VDI file[/s]*(See ChangeLog)*
-Once Selected, Partition Table for VDI is Displayed 
-Choose which Partition in VDI to Mount
-Check if a VDI is mounted and give Details on Mount

_Features I'm Working On:_
-Multiple Partition Mounting
-Multiple VDI Mounting
-More Informative Display
-More Informative Error Checks and Displays
-... Whatever else I think of(or if you have an Idea post below)

_Download:_
**vdimount_1.6.sh** (4 KB)
[FileTrip Page]("http://filetrip.net/pc-downloads/other-files/download-vdimount-mount-virtualbox-disk-16-f28663.html")
[http://www.multiupload.com/AJ965PAOSJ](http://www.multiupload.com/AJ965PAOSJ)
[http://mir.cr/0HCNBJCQ](http://mir.cr/0HCNBJCQ)

[s]**vdimount_1.5.sh** (4 KB)
[FileTrip Page]("http://filetrip.net/pc-downloads/other-files/download-vdimount-mount-virtualbox-disk-15-f28664.html")
[http://www.multiupload.com/0IAHU9J3P8](http://www.multiupload.com/0IAHU9J3P8)[/s]

[s]**vdimount_1.0.sh** (2 KB)
[FileTrip Page]("http://filetrip.net/pc-downloads/other-files/download-vdimount-mount-virtualbox-disk-10-f28665.html")
[http://www.multiupload.com/W85ZBJUHBT](http://www.multiupload.com/W85ZBJUHBT)[/s]

```

#!/bin/bash
if [ "$(id -u)" != "0" ]; then
echo 'This script must be run as root'
exit 1
fi
SETTINGS=~/vdimount.txt
CANONPATH=`readlink -f "$0"`
FOLDERPATH=`dirname "$CANONPATH"`
if [ -e "/media" ]; then
	mountdir=/media/vdi
	else
	mountdir=/mnt/vdi
fi
binskip=`grep -o "binskip" $SETTINGS`
if [ "$binskip" != binskip ]; then
	if [ "$FOLDERPATH" != /usr/bin ]; then
		echo "-----------------------------------------------"
		echo "Install Script as Command(/usr/bin)? [Y/n]"
		read bininstall
		echo "-----------------------------------------------"
		if [ "$bininstall" = Y ]; then
			echo binskip >> $SETTINGS
			cp "$CANONPATH" /usr/bin/vdimount
			chmod +rx /usr/bin/vdimount
			echo "Script Installed to /usr/bin as 'vdimount'"
			echo "Restart Terminal for Changes to Take Effect"
			read -p "press any key to exit..." presss
			exit 1
		fi
	fi
	echo binskip >> $SETTINGS
fi
checknbd=`dpkg-query -W -f='${Status}' qemu-kvm`
if [ "$checknbd" != "install ok installed" ]; then
	echo "Missing Deppendencies!"
	read -p "Install them?[Y/n]" installnbd
	if [ $installnbd = Y ]; then
		apt-get install qemu-kvm
		rmmod nbd
		modprobe nbd max_part=9
		echo "Dependencies Setup and Installed!!"
		read -p "press any key to continue..."
	else
		echo "Script can't run without them!"
		exit 1
	fi
fi
nbdmount=`ls /dev | grep "nbd"`
if [ -z "$nbdmount" ]; then
	modprobe nbd max_part=9
fi
clear
echo "VDI MOUNTER v1.6"
echo "-----------------------------------"
echo "What to do?"
echo "1: Mount VDI"
echo "2: Unmount VDI (2-f: Force Unmount)"
echo "3: Check VDI Mount"
echo "rs: Clear Settings File"
read userselect

if [ "$userselect" = 1 ]; then
	if mountpoint -q "$mountdir"; then
		echo "**********************************************"
		echo "VDI Already Mounted! Unmount it First before Mounting Again!"
		exit 1
	fi
		echo "-----------------------------------------------"
		echo "Enter VDI Location:(Full Path without Quotes)";
		read VDI
		echo "-----------------------------------------------"
		echo "You have selected: $VDI"
		qemu-nbd -c /dev/nbd0 $VDI
		echo "--VDI Mounted--"
		read -p "press any key to continue" press
		clear
		echo "-----------------------------------------------"
		echo "VDI $VDI"
		sfdisk -luM /dev/nbd0
		echo "-----------------------------------------------"
		echo "Enter Partition to be Mounted [ex:/dev/nbd0p1]"
		read device
		if [ $device =  ]; then
			qemu-nbd -d /dev/nbd0
			echo "****************************"; echo "Quitting Because of Error!"; exit 1
		fi
		if [ ! -e "$mountdir" ]; then
			mkdir $mountdir
		fi
		mount $device $mountdir
		clear
		echo "-----------------------------------------------"
		echo "$device"
		echo "of"
		echo "$VDI"
		echo "Mounted to $mountdir"
		echo "-----------------------------------------------"
fi
if [ "$userselect" = 2 ]; then
	if mountpoint -q "$mountdir"; then
		umount $mountdir
		qemu-nbd -d /dev/nbd0
		echo "-----------------------------------------------"
		echo "VDI Unmounted"
		exit 1
	else
		echo "**********************************************"
		echo "No VDI Mounted!"
		echo "****************************"; echo "Quitting Because of Error!"; exit 1
	fi
fi
if [ "$userselect" = "2-f" ]; then
		umount $mountdir
		qemu-nbd -d /dev/nbd0
		echo "-----------------------------------------------"
		echo "VDI Unmounted"
		exit 1
fi
if [ "$userselect" = 3 ]; then
	if mount | grep -q "/dev/nbd0"; then
		echo "-----------------------------------------------"
		echo "A VDI is Mounted!"
		highlight=`mount | grep "/dev/nbd0"`
		echo "$highlight"
		exit 1
	else
		echo "**********************************************"
		echo "No VDI Mounted!"
		echo "****************************"; echo "Quitting Because of Error!"; exit 1
	fi
fi
if [ "$userselect" = rs ]; then
	rm ~/vdimount.txt
	echo "-----------------------------------------------"
	echo "Settings File Cleared!"
fi

```

---

### Post by japzone on 2012-01-04
**_Changelog_**
_v1.6_*(Jan 13, 2012)*
-Fixed Bug where nbd devices weren't created after Reboot
-Reduces number of created nbd devices from 16 to 9(Otherwise Disk Utility gets full of unused devices)

_v1.5_*(Jan 4, 2012)*
-Removed Drag'n'Drop support because of Fatal Glitch(Quotes are not accepted by the tool, so until I can automate removal of the quotes the path has to be Manually Entered)
-Fixed several other Severe Glitches
-Added Some Elements to Clean up the Output
-Added some commands so Dependencies are properly configured after Install

---

### Post by japzone on 2012-01-13
If having trouble try a reboot

---

### Post by japzone on 2012-01-22
Having odd problem where commands will just fail in the script for no reason.
Example: I have a piece of script that works fine and then I use the read command to insert a "Press any key to Continue" but then the commands after it fail for some reason. I tried sh -x but all I can tell is that the commands just simply fail when executed. Very Odd.

---

### Post by japzone on 2012-05-14
VDIMount has a Permanent home! You can now follow any updates and Subscribe to the RSS feed via it's new page on FileTrip here: [http://filetrip.net/pc-downloads/other-files/latest-vdimount-mount-virtualbox-disk-f28663.html](http://filetrip.net/pc-downloads/other-files/latest-vdimount-mount-virtualbox-disk-f28663.html)

PS:I have reached the limit to the number of commands in the script. If you have any ideas how to get around this, _Please_, let me know

---

