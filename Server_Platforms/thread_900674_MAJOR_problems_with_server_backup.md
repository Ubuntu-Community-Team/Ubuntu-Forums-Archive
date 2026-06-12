---
title: "MAJOR problems with server backup"
date: 2008-08-25
forum: Server Platforms
---

### Post by Titan8990 on 2008-08-25
The problem I am having is the drive letter assigned to my backup HDD changing. Here is the setup:

Two HDDs on a 3ware RAID card in a RAID 1 configuration.

One External HDD connected via USB (this used to be eSATA but I had to change that due to the same problem I am discussing here).

What is happening is about once a week it gives that external USB drive a new letter and it is no longer mounted on the spot that I put it. This says it all:

```
jordan@einstein:/var/log$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda1 on /media/sda1 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdc1 on /media/sda1 type ext3 (rw)
/dev/sdd1 on /media/backup type ext3 (rw)

jordan@einstein:/var/log$ cd /media/backup/

jordan@einstein:/media/backup$ ls
ls: reading directory .: Input/output error

jordan@einstein:/media/sda1$ sudo fdisk -l

Disk /dev/sdb: 250.0 GB, 250057219584 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b3151

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29920   240332368+  83  Linux
/dev/sdb2           29921       30401     3863632+  82  Linux swap / Solaris

Disk /dev/sde: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10c310fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001   83  Linux
```



What is causing this issue?

I **must** have these backups.

I appreciate any insight someone might have in regards to this issue.

Edit:

Also, the drive is specified my UUID in /etc/fstab (although this shouldn't matter since the server is never rebooted).

```
jordan@einstein:/media/backup$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=eb90ff26-b99d-44b3-aedc-f641b6ed6faa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=567bbf65-3e84-4fc1-831e-74ee1603dd62 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
UUID=1649f5ce-e869-4a3f-b7a9-e638e0bfdc80       /media/backup     ext3    defaults0       2
```


When I first began the external drive as /dev/sda and the filesystem drive was /dev/sdb. Now it has moved itself all the way down to sde. What is going to happen when ubuntu is out of letters?

---

### Post by y@w on 2008-08-25
Are you unplugging or turning off the drive in between?

---

### Post by Titan8990 on 2008-08-25
The drive is plugged into a battery backup along with the server. It is never turned off.

I do occasionally plug in a thumb drive. Could this be what is pushing it further down the line?

---

### Post by buntunub on 2008-08-25
Sounds like you need to set some udev rules..

---

### Post by Titan8990 on 2008-08-26
Udev rules are new to me. I looked at the udev man pages and saw that the rules should be in /etc/udev/rules.d. Is there a specific one that is customary for personal rules? I notice that there are many different rule types. Which one should I add to? Make a new rule?

If I had to guess I would say it was 20-names-rules but I don't see anything in there about names to begin with:

```
jordan@einstein:/etc/udev/rules.d$ cat 20-names.rules
# This file establishes the device names according to Ubuntu policy.
# See udev(7) for syntax.
#
# Permissions and ownership of devices must not be set here, but in
# 40-permissions.rules; user-friendly symlinks to devices should be
# set in 60-symlinks.rules.

# CPU devices, group under /dev/cpu
KERNEL=="cpu[0-9]*",                    NAME="cpu/%n/cpuid"
KERNEL=="msr[0-9]*",                    NAME="cpu/%n/msr"
KERNEL=="microcode",                    NAME="cpu/microcode"

# Device mapper targets
KERNEL=="device-mapper",                NAME="mapper/control"

# IEEE1394 devices, group under their own directories
KERNEL=="dv1394-[0-9]*",                NAME="dv1394/%n"
KERNEL=="video1394-[0-9]*",             NAME="video1394/%n"

# Infiniband devices
KERNEL=="umad[0-9]*",                   NAME="infiniband/%k"
KERNEL=="issm[0-9]*,                    NAME="infiniband/%k"
KERNEL=="uverbs[0-9]*,                  NAME="infiniband/%k"
KERNEL=="ucm[0-9]*,                     NAME="infiniband/%k"
KERNEL=="rdma_ucm",                     NAME="infiniband/%k"

# Input devices, group under /dev/input
KERNEL=="event[0-9]*",                  NAME="input/%k"
KERNEL=="mice",                         NAME="input/%k"
KERNEL=="mouse[0-9]*",                  NAME="input/%k"
KERNEL=="js[0-9]*",                     NAME="input/%k"
KERNEL=="ts[0-9]*",                     NAME="input/%k"
KERNEL=="uinput",                       NAME="input/%k"

# ISDN devices, group under /dev/capi
KERNEL=="capi",                         NAME="capi20"
KERNEL=="capi[0-9]*",                   NAME="capi/%n"

# Packet CD devices, group under /dev/pktcdvd
KERNEL=="pktcdvd",                      NAME="pktcdvd/control"
KERNEL=="pktcdvd[0-9]*",                NAME="pktcdvd/%k"

# Sound devices, group under /dev/snd
KERNEL=="controlC[0-9]*",               NAME="snd/%k"
KERNEL=="hwC[D0-9]*",                   NAME="snd/%k"
KERNEL=="midiC[D0-9]*",                 NAME="snd/%k"
KERNEL=="pcmC[D0-9cp]*",                NAME="snd/%k"
KERNEL=="seq",                          NAME="snd/%k"
KERNEL=="timer",                        NAME="snd/%k"

# USB devices (usbfs replacement), group under /dev/bus/usb
SUBSYSTEM!="usb_device", GOTO="usb_device_end"
IMPORT{program}="usb_device_name --export %k"
ENV{USB_BUS}=="?*", ENV{USB_DEV}=="?*", \
        NAME="bus/usb/$env{USB_BUS}/$env{USB_DEV}"
LABEL="usb_device_end"

# Other USB devices, commonly grouped under /dev/usb
KERNEL=="auer[0-9]*",                   NAME="usb/%k"
KERNEL=="cpad[0-9]*",                   NAME="usb/%k"
KERNEL=="dabusb[0-9]*",                 NAME="usb/%k"
KERNEL=="hiddev[0-9]*",                 NAME="usb/%k"
KERNEL=="legousbtower[0-9]*",           NAME="usb/%k"
SUBSYSTEMS=="usb", KERNEL=="lp[0-9]*",  NAME="usb/%k"

# Video devices, group dvb devices under /dev/dvb
SUBSYSTEM!="dvb", GOTO="dvb_end"
IMPORT{program}="dvb_device_name --export %k"
ENV{DVB_ADAPTER}=="?*", ENV{DVB_DEV}=="?*", \
        NAME="dvb/adapter$env{DVB_ADAPTER}/$env{DVB_NAME}"
LABEL="dvb_end"

# Video devices, group cards under /dev/dri
KERNEL=="card[0-9]*",                   NAME="dri/%k"

# Zaptel devices, group under /dev/zap
KERNEL=="zapctl",                       NAME="zap/ctl"
KERNEL=="zaptimer",                     NAME="zap/timer"
KERNEL=="zapchannel",                   NAME="zap/channel"
KERNEL=="zappseudo",                    NAME="zap/pseudo"
KERNEL=="zap[0-9]*",                    NAME="zap/%n"

# SCSI CD-ROM devices use /dev/scdN now
SUBSYSTEMS=="scsi", KERNEL=="sr[0-9]*", NAME="scd%n"

# Raw block devices need to be /dev/raw/*
SUBSYSTEM=="raw", KERNEL=="raw[0-9]*",  NAME="raw/%k"

# Other devices
KERNEL=="hw_random",                    NAME="hwrng"
KERNEL=="tun",                          NAME="net/%k"
```

I appreciate any help I can get.

---

### Post by Titan8990 on 2008-08-26
Alright, I found this guide here: [http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

But when I run the example command to find information about the device it is different.

In the guide:

```
udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.
  looking at the device chain at '/sys/devices/pci0000:00/0000:00:02.0/usb1/1-3':
    BUS=="usb"
    ID=="1-3"
    DRIVER=="usb"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bDeviceClass}=="00"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bMaxPower}=="100mA"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bNumInterfaces}==" 1"
    SYSFS{bcdDevice}=="0100"
    SYSFS{bmAttributes}=="80"
    SYSFS{configuration}==""
    SYSFS{devnum}=="6"
    SYSFS{idProduct}=="0005"
    SYSFS{idVendor}=="0c76"
    SYSFS{maxchild}=="0"
    SYSFS{product}=="TS128MJFLASHA"
    SYSFS{speed}=="12"
    SYSFS{version}==" 1.10"
```


From my machine:

```
jordan@einstein:~$ udevinfo -a -p $(udevinfo -q path -n /dev/sde)

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/block/sde':
    KERNEL=="sde"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{capability}=="12"
    ATTR{stat}=="   48655    19303   539245    73630     6056   111728   942312  1624320        0    85100  1698020"
    ATTR{size}=="976771055"
    ATTR{removable}=="0"
    ATTR{range}=="16"
    ATTR{dev}=="8:64"

  looking at parent device '/devices/pci0000:00/0000:00:13.5/usb6/6-1/6-1:1.0/host22/target22:0:0/22:0:0:0':
    KERNELS=="22:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{ioerr_cnt}=="0x0"
    ATTRS{iodone_cnt}=="0xd5be"
    ATTRS{iorequest_cnt}=="0xd5be"
    ATTRS{iocounterbits}=="32"
    ATTRS{timeout}=="30"
    ATTRS{state}=="running"
    ATTRS{rev}=="4.48"
    ATTRS{model}=="ST3500320AS     "
    ATTRS{vendor}=="Initio  "
    ATTRS{scsi_level}=="0"
    ATTRS{type}=="0"
    ATTRS{queue_type}=="none"
    ATTRS{queue_depth}=="1"
    ATTRS{device_blocked}=="0"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:13.5/usb6/6-1/6-1:1.0/host22/target22:0:0':
    KERNELS=="target22:0:0"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""

  looking at parent device '/devices/pci0000:00/0000:00:13.5/usb6/6-1/6-1:1.0/host22':
    KERNELS=="host22"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""

  looking at parent device '/devices/pci0000:00/0000:00:13.5/usb6/6-1/6-1:1.0':
    KERNELS=="6-1:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{modalias}=="usb:v13FDp1650d0448dc00dsc00dp00ic08isc06ip50"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"

  looking at parent device '/devices/pci0000:00/0000:00:13.5/usb6/6-1':
    KERNELS=="6-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="00101016500000000"
    ATTRS{product}=="ST3500320AS     "
    ATTRS{manufacturer}=="Initio  "
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{devnum}=="27"
    ATTRS{busnum}=="6"
    ATTRS{speed}=="480"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bcdDevice}=="0448"
    ATTRS{idProduct}=="1650"
    ATTRS{idVendor}=="13fd"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{bmAttributes}=="c0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""
    ATTRS{dev}=="189:666"

  looking at parent device '/devices/pci0000:00/0000:00:13.5/usb6':
    KERNELS=="usb6"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="0000:00:13.5"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{manufacturer}=="Linux 2.6.22-15-server ehci_hcd"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="10"
    ATTRS{version}==" 2.00"
    ATTRS{devnum}=="1"
    ATTRS{busnum}=="6"
    ATTRS{speed}=="480"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bcdDevice}=="0206"
    ATTRS{idProduct}=="0000"
    ATTRS{idVendor}=="0000"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""
    ATTRS{dev}=="189:640"

  looking at parent device '/devices/pci0000:00/0000:00:13.5':
    KERNELS=="0000:00:13.5"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{msi_bus}==""
    ATTRS{broken_parity_status}=="0"
    ATTRS{modalias}=="pci:v00001002d00004386sv00001458sd00005004bc0Csc03i20"
    ATTRS{local_cpus}=="ff"
    ATTRS{irq}=="19"
    ATTRS{class}=="0x0c0320"
    ATTRS{subsystem_device}=="0x5004"
    ATTRS{subsystem_vendor}=="0x1458"
    ATTRS{device}=="0x4386"
    ATTRS{vendor}=="0x1002"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""

jordan@einstein:~$ udevinfo -a -p $(udevinfo -q path -n /dev/sde) | grep BUS
jordan@einstein:~$ udevinfo -a -p $(udevinfo -q path -n /dev/sde) | grep -i 'BUS'
    ATTRS{busnum}=="6"
    ATTRS{busnum}=="6"
    ATTRS{msi_bus}==""
```


All my devices are prefixed with ATTRS while the ones in the guide are prefixed with SYSFS.

So in the guide the rules look like this:

```
BUS=="usb", SYSFS{product}=="TS128MJFLASHA", KERNEL=="sd?1", NAME="transcend128mb", SYMLINK="usbdevices/transcend128mb"
```

Would this be correct for me:

```
SUBSYSTEMS=="usb", ATTRS{product}=="ST3500320AS     ", KERNEL=="sd?1", NAME="backupdrive", SYMLINK="usbdevices/backupdrive"
```

I would really like someone to confirm that this is correct before I implement it.

---

### Post by Titan8990 on 2008-08-27
bump, would really like some feedback.

---

### Post by Titan8990 on 2008-08-28
up

---

### Post by Titan8990 on 2008-08-29
last bump before I make a new thread specifically titled "Help with udev rules".

---

