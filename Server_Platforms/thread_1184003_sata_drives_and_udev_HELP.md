---
title: "sata drives and udev???? HELP"
date: 2009-06-10
forum: Server Platforms
---

### Post by cenwesi on 2009-06-10
I need help figuring out why udev is not working correctly. It keeps changing the drive assignment each time i reboot and this messes up my raid1 setup and LVM. Basically what i am trying to do is make sure sdf stays as sdf and sdg the same every time i reboot.. The two hard drive are Barracuda 1.5Tb.

Drive #1: [sdf]
  Serial#: **9VS21DHL** 
Drive #2: [sdg]
  Serial#: **9VS21D9C**

Now here is what i have on my udev file (71-sata-drives.rules).
> #--2 x 1.5TB
KERNEL=="sd?", ENV{ID_SERIAL}=="SATA_ST31500341AS_9VS21DHL", NAME="sdf" ,SYMLINK+="SATA_1.5TB#1"
KERNEL=="sd?[0-9]", ENV{ID_SERIAL}=="SATA_ST31500341AS_9VS21DHL", NAME="sdf%n" ,SYMLINK+="SATA_1.5TB#1_P%n"

KERNEL=="sd?", ENV{ID_SERIAL}=="SATA_ST31500341AS_9VS21D9C", NAME="sdg" ,SYMLINK+="SATA_1.5TB#2"
KERNEL=="sd?[0-9]", ENV{ID_SERIAL}=="SATA_ST31500341AS_9VS21D9C", NAME="sdg%n" ,SYMLINK+="SATA_1.5TB#2_P%n"

Here is the output of "udevadm info -a -p `udevadm info -a -q path -n /dev/sdf`"

>   looking at device '/devices/pci0000:00/0000:00:08.0/host6/target6:0:0/6:0:0:0/block/sdf':
    KERNEL=="sdf"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{ext_range}=="256"
    ATTR{removable}=="0"
    ATTR{ro}=="0"
    ATTR{size}=="2930277168"
    ATTR{capability}=="52"
    ATTR{stat}=="      78      320     1234       99        0        0        0        0        0       98       99"

  looking at parent device '/devices/pci0000:00/0000:00:08.0/host6/target6:0:0/6:0:0:0':
    KERNELS=="6:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="6"
    ATTRS{vendor}=="ATA     "
    ATTRS{model}=="ST31500341AS    "
    ATTRS{rev}=="CC1H"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x63"
    ATTRS{iodone_cnt}=="0x63"
    ATTRS{ioerr_cnt}=="0x0"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"


Here the output for sdg

  looking at device '/devices/pci0000:00/0000:00:08.0/host7/target7:0:0/7:0:0:0/block/sdg':
    KERNEL=="sdg"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{ext_range}=="256"
    ATTR{removable}=="0"
    ATTR{ro}=="0"
    ATTR{size}=="2930277168"
    ATTR{capability}=="52"
    ATTR{stat}=="     113      157     1204      152        0        0        0        0        0      151      152"

  looking at parent device '/devices/pci0000:00/0000:00:08.0/host7/target7:0:0/7:0:0:0':
    KERNELS=="7:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="6"
    ATTRS{vendor}=="ATA     "
    ATTRS{model}=="ST31500341AS    "
    ATTRS{rev}=="CC1H"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x86"
    ATTRS{iodone_cnt}=="0x86"
    ATTRS{ioerr_cnt}=="0x0"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"


AS you can see, this is how i want those two drives to show up and if i was to reboot now it will probably remap sdg->sde. Seems like udev is not doing what i told it to do. Any help will be appreciated before i loose my mind.

ps, i have tried different # for the file name and the current one is 71-sata-drives.rules

---

### Post by cariboo on 2009-06-10
This has been a problem, especially if you have a mix of ide and sata drives. The way I get around the problem is to use uuid instead of device labels. This is an example of /etc/fstab on the computer I'm using right now:

```
# / was on /dev/sdb1 during installation
UUID=29994917-63c7-4980-ae46-212ca6ad29cb /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=7c109a7f-b7fd-402d-aec5-0ee7dd30d37a /home           ext4    relatime        0       2
# swap was on /dev/sdb3 during installation
UUID=bc7912f5-a427-429d-98cd-7b97312c294d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# storage was on /dev/sda1
UUID=7451e251-cb09-4cda-b433-a2768d81affe /home/storage ext4	relatime	02
``` 

To find the uuid of your drives, at the prompt type:

```
sudo blkid
```

You should see something like this:

```
sudo blkid
[sudo] password for jim: 
/dev/sda1: UUID="7451e251-cb09-4cda-b433-a2768d81affe" TYPE="ext4" 
/dev/sdb1: UUID="29994917-63c7-4980-ae46-212ca6ad29cb" TYPE="ext4" 
/dev/sdb2: UUID="7c109a7f-b7fd-402d-aec5-0ee7dd30d37a" TYPE="ext4" 
/dev/sdb3: TYPE="swap" UUID="bc7912f5-a427-429d-98cd-7b97312c294d" 
/dev/sdb5: UUID="e80a1b7b-5113-491f-8f7b-473aeeefa34b" TYPE="ext4" 
/dev/sdb6: UUID="d4240bbc-6108-4a70-bb52-92ca66d86daf" TYPE="ext4"
```

---

### Post by cenwesi on 2009-06-10
My fstab is OK and works fine, its udev/ubuntu that keeps switching the OS IDE drive (sde) with one of the location of the SATA drive. I will really appriciate it if someone knows how to solve this problem. I will really want sdg to stay sdg.... i have 7 drives including the IDE 40gigs for Ubuntu.

---

### Post by redmk2 on 2009-06-11
> **cenwesi said:**
> My fstab is OK and works fine, its udev/ubuntu that keeps switching the OS IDE drive (sde) with one of the location of the SATA drive. I will really appriciate it if someone knows how to solve this problem. I will really want sdg to stay sdg.... i have 7 drives including the IDE 40gigs for Ubuntu.

I assume everything is mounted via fstab then.  

What cariboo907 has stated is correct.To carry it further when the OS is booted it assigns the /dev/<drivename> in the order they are discovered. There is no permanent /dev/<drivename>.  This name can change for any reason, e.g., slow response, interruptions, media removed (pen drive), etc..


The UUID is a an identifier for a [COLOR="Blue"]_specific block device_[/COLOR] i.e., partition or removable media.  This makes it a more reliable means of identifying the specific partition.

What is your situation that you need to refer to the /dev/<drivename> moniker?  I use UUID's in my scripts and it is fine.  To be clear about this; once the UUID is assigned it does not change. Unless you reformat the drive itself.

---

### Post by cenwesi on 2009-06-11
Ok, let me see if i can explain... All my drives excluding the OS are all used for software Raid1. On top of the Raid1 resides the LVM. So there is NO reference of these drives in the fstab file, only the OS is referenced there. Here is a sample of my fstab.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c173418f-cbee-45da-9758-8faf2d07e292 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c3506670-0026-40a9-bcdc-ca216451908c none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
## --- mount LVM
/dev/FileSystem/Recordings /mnt/Recordings xfs noatime,nodiratime 0 0
/dev/FileSystem/Movies /mnt/Movies xfs noatime,nodiratime 0 0
/dev/FileSystem/Data /mnt/Data xfs noatime,nodiratime 0 0
/dev/FileSystem/Vmwares /mnt/Vmwares xfs noatime,nodiratime 0 0
/dev/FileSystem/Pictures /mnt/Pictures ext4 noatime,nodiratime,relatime 0 0
/dev/FileSystem/Documents /mnt/Documents ext4 noatime,nodiratime,relatime 0 0
/dev/FileSystem/Mp3s /mnt/Mp3s ext4 noatime,nodiratime,relatime 0 0
/dev/FileSystem/Backups /mnt/Backups reiserfs noatime,nodiratime 0 0

As you can see there is NO reference of sda...sdh, only sde which is the OS and has that UUID. Problem is each time i reboot, sde gets swaped with sdg which in turns messes up my software raid1 using mdadm. So when i look at **cat /proc/mdstat** it shows inactive or somethings active with only one drive....

---

### Post by glliho on 2011-01-18
> **cenwesi said:**
> Ok, let me see if i can explain... All my drives excluding the OS are all used for software Raid1. On top of the Raid1 resides the LVM. So there is NO reference of these drives in the fstab file, only the OS is referenced there. Here is a sample of my fstab.



As you can see there is NO reference of sda...sdh, only sde which is the OS and has that UUID. Problem is each time i reboot, sde gets swaped with sdg which in turns messes up my software raid1 using mdadm. So when i look at **cat /proc/mdstat** it shows inactive or somethings active with only one drive....

Hi cenwesi,

Sorry to bother you again with this issue, but have you solved the problem? I have almost the same problem, and I can,t solve it.

Thanks,
glliho

---

### Post by glliho on 2011-01-18
> **cenwesi said:**
> Ok, let me see if i can explain... All my drives excluding the OS are all used for software Raid1. On top of the Raid1 resides the LVM. So there is NO reference of these drives in the fstab file, only the OS is referenced there. Here is a sample of my fstab.



As you can see there is NO reference of sda...sdh, only sde which is the OS and has that UUID. Problem is each time i reboot, sde gets swaped with sdg which in turns messes up my software raid1 using mdadm. So when i look at **cat /proc/mdstat** it shows inactive or somethings active with only one drive....

Hi cenwesi,

Sorry to bother you again with this issue, but have you solved the problem? I have almost the same problem, and I can't solve it.

Thanks,
glliho

---

### Post by nero32 on 2011-07-13
hi,

i have the same problem. i am using a raid5 with 4 sata drives for data storage. every time i start the server the drives are different because there is a usb mf-printer with integrated cardreader. and by booting the system the cardreader will be recognized different.
my configuration when i use hddtemp
WDC is my system hd
Hitachi drives are my raid 5
sdc-e is my usb printer

[CODE]/dev/sda: WDC WD3200BEVT-22A0RT0: 34°C
/dev/sdb: Hitachi HDS722020ALA330: 41°C
/dev/sdc: Generic-SD/MMC:  drive supported, but it doesn't have a temperature sensor.
/dev/sdd: Generic-MS/MS-Pro: S.M.A.R.T. not available
/dev/sde: Canon MP610 series: S.M.A.R.T. not available
/dev/sdf: Hitachi HDS722020ALA330: 40°C
/dev/sdg: Hitachi HDS722020ALA330: 42°C
/dev/sdh: Hitachi HDS722020ALA330: 41°C
/CODE]

i hope you understand my poor english. thanks a lot.

---

