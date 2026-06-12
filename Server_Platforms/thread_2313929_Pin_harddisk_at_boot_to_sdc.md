---
title: "Pin harddisk at boot to sdc"
date: 2016-02-17
forum: Server Platforms
---

### Post by Seb_Boffen on 2016-02-17
I have 3 disks in my server 2 in raid 1 and a raid 5 rocketraid, I'd like the rocketraid array to load at boot as sdc. I've tried the udev rules.d but this is not consistent.

KERNEL=="sdc", ATTRS{model}!="DISK_10_0", NAME="sdc"
KERNEL=="sdc?", ATTRS{model}!="DISK_10_0", NAME="sdc%n"

Could it be I need to redefine sda and sdb in a similar way in the udev rules.d for them to work consistent?
The reason is I'd like to monitor the disks smart status using Historic System Statistics from webmin and there I need to redefine what to monitor on a sda, sdb, sdc level.
And the sdc as it is a rocketraid does not allow the same monitoring features as a standard disk.

---

### Post by MAFoElffen on 2016-02-17
Is this for personal preference or do you have a specific program that is hardcode to look for a specific device assignment? The only reason I ask, is that Linux now, since a device name can change, uses the in your case logical RAID Volume, to keep track of those changes. Changing from that is not something to take lightly. Just make backups before your changes...

You said you already tried udev/rules.d, so you may or may not know that there's a few pieces that fit together besides just that. Just in case you didn't, here the doc's from Red Hat:
[https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/5/html/Virtualization/sect-Virtualization-Virtualized_block_devices-Configuring_persistent_storage_in_Red_Hat_Enterprise_Linux_5.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/5/html/Virtualization/sect-Virtualization-Virtualized_block_devices-Configuring_persistent_storage_in_Red_Hat_Enterprise_Linux_5.html)

---

### Post by Seb_Boffen on 2016-02-18
I've changed to command to: 

KERNEL=="sdc", BUS=="scsi", ATTRS{model}!="DISK_10_0", PROGRAM="/lib/udev/scsi_id -g /dev/sdc", RESULT="200193c0000000000", NAME="sdc"
KERNEL=="sdc?", BUS=="scsi", ATTRS{model}!="DISK_10_0", PROGRAM="/lib/udev/scsi_id -g /dev/sdc", RESULT="200193c0000000000", NAME="sdc%n"

and append this line to /etc/rc.local: /sbin/start_udev

I'll monitor to see if the configuration stays consistent.

I like to load the device as sdc as:  I'd like to monitor the disks smart status using Historic System Statistics from webmin and there I need to redefine what to monitor on a sda, sdb, sdc level.
 And the sdc as it is a rocketraid does not allow the same monitoring features as a standard disk. As with the Raid 1 I don't care if 1 loads up as sda or next time sdb as they both contain the same data and are bootable.

After 2 boots it loads up as sdc, but I'll report later if this works consistent.

I do not use the file: [FONT=Courier New]/etc/scsi_id.config[/FONT]

---

### Post by MAFoElffen on 2016-02-19
Crossing my fingers for you!

---

### Post by Seb_Boffen on 2016-03-03
No fix so far I turned off the smart recording statistics as the disks keep loading random.

---

