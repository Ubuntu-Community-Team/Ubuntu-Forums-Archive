---
title: "Ubuntu 20.04 LTS - Unable to find volume group when booting"
date: 2021-11-25
forum: Server Platforms
---

### Post by iversc on 2021-11-25
Hello, just looking to get some assistance or get pointed in the right direction for this.

I seem to be having some sort of lvm issue, possibly an initramfs issue?


When booting, the system seems to be unable to find the volume group for the root system.  It will say exactly that when booting, and then it will say it can't find the mapper device(in this case, /dev/mapper/shinoko--vg-root), and it will drop to the busybox initramfs shell.

In this shell, I can see the hard drive and partition that the volume is hosted on manually, (/dev/sda), but running lvm commands to scan the system(like lvm pvs or lvm lvs) will come back with nothing.


When I boot a live environment, I have no issues accessing that volume group at all.  I can see it via lvs/pvs, it's device is available in /dev/mapper, and I can even mount it and seem to be able to access all the data on it just fine.


I've tried rebuilding grub and the initramfs while chrooted into the system from a liveusb, but still seem to be at this same point.


Do you have any advice on where to look next?  I'm not quite sure where to go from here. 


Thanks in advance!

---

### Post by MAFoElffen on 2021-11-26
When you say that you mound the installed system... Did you mean that you mounted the disks or the LVM LV's? 

If while you did where mounted into the the installed system, did you test to see that everything was okay there?

If while mounted into the installed system, please run the Forum's 'system-info' script... and let's see what that says about the installed system's hardware. configuration and settings....

---

### Post by iversc on 2021-11-27
I mounted /dev/mapper/shinoko--vg-root successfully while running a liveusb, and was able to browse everything in the filesystem.  I think that means the LVM LV?

With the poking around I did while mounted, I seem to be able to access everything successfully, though I haven't done a completely thorough check of every file.  Every file I've thought to check has worked, though; even chrooting into the mounted system.

Here's the pastebin for the system-info run.  I ran this while chrooted into the system from the liveusb environment.

[https://paste.ubuntu.com/p/2xhw5YxVn6/](https://paste.ubuntu.com/p/2xhw5YxVn6/)

---

### Post by darkod on 2021-11-27
Is this Ubuntu Server or Desktop? Did you do any "special install" or simply a default install?

Is there a separate /boot partition? (sorry, couldn't look in the pastebin)

Even though I think it is not necessary these days, I tend to create a separate 2GB /boot partition outside the LVM. In your case it looks like it is not autoactivating the LVM, hence it can't find it to continue boot.

I think you could try the following:
1). In the grub menu select the advanced/recovery option.
2). In the recovery menu select drop to root shell.
3). Try to activate the LVM by 'vgchange -ay' (I think that was the command)
4). Back in the recovery menu select continue boot.

See if that gets you further, by manually activating the LVM.

If this is really the case of not autoactivating the LVM it would be very strange. I think that since many versions ago, both server and desktop release autoactivate the LVM always. If there was something special done during installation maybe it didn't put the correct process in place for the LVM. Or you hit some bug...

---

### Post by MAFoElffen on 2021-11-27
The pastebin at that link was blank(???)

Could you please post the contents of your ~/system-info-link.log? That pastebin-upload log file will show when it was uploaded (or not) and the link to where the report was uploaded to... 

The output of that report would have shown all the questions that Darko asked and I would like to know... Such as what the media was that it was originally installed from, the LVM information, the layout, etc...

If it didn't upload, you can still copy/paste the report contents into a post, wrapped in [noparse][Code] / [Code][/noparse] Tags. The report is located at ~/system-info.txt 

I would like to know if that report somehow failed that upload though and/or if there was something wrong with that report... As I am the author and maintainer of that Forum's script, I am ultimately responsible for keeping it working right. 

EDIT:
FYI to anyone else reading this post later on... If you are not in contact with me personally, the preferred method to file bugs on the Forum's 'system-info' script would be to file them at [https://github.com/UbuntuForums/system-info/issues/new/choose](https://github.com/UbuntuForums/system-info/issues/new/choose) ... That will send an email directly to me... Or if that will not let you for some reason, just send me a PM.

---

### Post by iversc on 2021-11-28
> **darkod said:**
> Is this Ubuntu Server or Desktop? Did you do any "special install" or simply a default install?

Is there a separate /boot partition? (sorry, couldn't look in the pastebin)

---

See if that gets you further, by manually activating the LVM.


Don't think I've done anything special.  It started as a Ubuntu 16.04 LTS server install, and upgraded to 18.04 and then 20.04 over time.

Yes, there is a separate /boot partition.

I didn't seem to have a 'drop into a root shell' option in grub, but letting booting continue and drop me into a shell when it fails, using 'lvm vgchange -ay' doesn't seem to get me anywhere.

EDIT: Nope, it doesn't get me anywhere, but running the command from a booted liveusb seems to work just fine.   I'm even more lost, now.


> **MAFoElffen said:**
> The pastebin at that link was blank(???)

Could you please post the contents of your ~/system-info-link.log? That pastebin-upload log file will show when it was uploaded (or not) and the link to where the report was uploaded to... 

The output of that report would have shown all the questions that Darko asked and I would like to know... Such as what the media was that it was originally installed from, the LVM information, the layout, etc...

If it didn't upload, you can still copy/paste the report contents into a post, wrapped in [noparse]```
 / [Code][/noparse] Tags. The report is located at ~/system-info.txt 

I would like to know if that report somehow failed that upload though and/or if there was something wrong with that report... As I am the author and maintainer of that Forum's script, I am ultimately responsible for keeping it working right. 

EDIT:
FYI to anyone else reading this post later on... If you are not in contact with me personally, the preferred method to file bugs on the Forum's 'system-info' script would be to file them at [https://github.com/UbuntuForums/system-info/issues/new/choose](https://github.com/UbuntuForums/system-info/issues/new/choose) ... That will send an email directly to me... Or if that will not let you for some reason, just send me a PM.

I have no idea why the paste would be coming up as blank for you, I can see it just fine.  That's extremely weird.


system-info-link.log contents:
[code]Uploaded Report: 2021-11-26  23:15:54 CST (-600):
View at: https://paste.ubuntu.com/p/2xhw5YxVn6/
```

Contents of the pastebin that I see:

```
[COLOR=#000000]Starting the Ubuntu Forums 'system-info' Report: 2021-11-26  23:15:54 CST (-0600)[/COLOR]    Part of the Ama-gi Project
    Version: 01.00-01, Script Date: 2021.09.30

---------------------------------------------------------------
Main Complaint: Unable to find LVM VG when booting
Problem Description:  The system is unable to fully boot due to not being able to mount the LVM VG when starting up.  Attempting to scan the system in the initramfs busybox seems to also not be able to find the LVM VG.  Booting the system from a live USB seems to find the VG just fine, and is able to mount it.
---------- General Computer Specifications:

  --- Computer/CPU Information from 'lshw -C cpu' --- 
*-Cpu
    Description: CPU
    Product: Intel(R) Atom(TM) CPU D2550   @ 1.86GHz
    Vendor: Intel Corp.
    Physical id: 4
    Bus info: cpu@0
    Version: Intel(R) Atom(TM) CPU D2550   @ 1.86GHz
    Serial: [REMOVED]
    Slot: LGA1155
    Size: 1865MHz
    Capacity: 1865MHz
    Width: 64 bits
    Clock: 533MHz
    Capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 
        apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse 
        sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts 
        nopl nonstop_tsc cpuid aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 
        cx16 xtpr pdcm movbe lahf_lm dtherm arat
    Configuration: cores=2 enabledcores=1 threads=2

computer
    Description: Notebook
    Product: EB1033 (SKU)
    Vendor: ASUSTeK Computer INC.
    Version: 0608
    Serial: [REMOVED]
    Width: 64 bits
    Capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    Configuration:
        boot=normal
        chassis=notebook
        family=Eee Family
        sku=SKU
        uuid=[REMOVED]

------------------ SMBIOS Information from '/sys/class/dmi/id/' 
Bios Vendor:         American Megatrends Inc.
Bios Version:        0608
Bios Release:        4.6
Board Vendor:        ASUSTeK COMPUTER INC.
Board Name:          EB1033
Board Version:       x.xx
Board Serial:        MB-1234567890
Board Asset Tag:     To be filled by O.E.M.

Current boot mode:   Legacy mode (alias CSM alias BIOS mode)
EFI variables are not supported on this system


---------- Memory Information:
              total        used        free      shared  buff/cache   available
Mem:          3.8Gi       669Mi       136Mi       120Mi       3.0Gi       2.8Gi
Swap:            0B          0B          0B

---------- IP Adress Information:
  --- IP Adress Information from 'ip addr' --- 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
3: wlp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000

  --- Internet Connection Status from 'ping [various addresses]' --- 
Connected to Internet with DNS

  --- Network Device Status Summary from 'ip addr' ---  
These Network Devices are up:
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000

  --- Hostname from 'hostname --fqdn' ---  
The 'Hostname' of the computer system is: ubuntu


---------- File system specs from 'df -h':
Filesystem                   Type  Size  Used Avail Use% Mounted on
/dev/mapper/shinoko--vg-root ext4  106G   41G   60G  41% /
/dev/sda1                    ext2  472M  322M  126M  72% /boot

---------- Disk/Partition Information From 'fdisk':

Disk /dev/sda: 111.81 GiB, 120034123776 bytes, 234441648 sectors
Disk model: Crucial_CT120M50
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x72d93c3e

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048    999423    997376   487M 83 Linux
/dev/sda2       1001470 234440703 233439234 111.3G  5 Extended
/dev/sda5       1001472 234440703 233439232 111.3G 8e Linux LVM

Partition 2 does not start on physical sector boundary.

Disk /dev/mapper/shinoko--vg-root: 107.34 GiB, 115246891008 bytes, 225091584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/mapper/shinoko--vg-swap_1: 3.10 GiB, 4269801472 bytes, 8339456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/sdb: 3.86 GiB, 4127195136 bytes, 8060928 sectors
Disk model: USB DISK 2.0    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x2cf4ba3a

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdb1  *          0 5999871 5999872  2.9G  0 Empty
/dev/sdb2       5271500 5279499    8000  3.9M ef EFI (FAT-12/16/32)
/dev/sdb3       6000640 8060927 2060288 1006M 83 Linux

---------- Disk/Partition Information From 'lsblk':
NAME                     SIZE FSTYPE LABEL MOUNTPOINT MODEL
loop0                      2G                         
loop1                   55.4M                         
loop2                    219M                         
loop3                   32.3M                         
loop4                     51M                         
loop5                   65.1M                         
sda                    111.8G                         Crucial_CT120M50
|-sda1                   487M              /boot      
|-sda2                     1K                         
`-sda5                 111.3G                         
  |-shinoko--vg-root   107.3G              /          
  `-shinoko--vg-swap_1     4G                         
sdb                      3.9G                         USB DISK 2.0    
|-sdb1                   2.9G                         
|-sdb2                   3.9M                         
`-sdb3                  1006M                         
   ------- 'lsblk' information continued ...
NAME                   HOTPLUG PARTUUID UUID
sda                          0          
|-sda1                       0          
|-sda2                       0          
`-sda5                       0          
  |-shinoko--vg-root         0          
  `-shinoko--vg-swap_1       0          
sdb                          1          
|-sdb1                       1          
|-sdb2                       1          
`-sdb3                       1          

---------- Mount Details of '/etc/fstab':
/dev/mapper/shinoko--vg-root /               ext4    errors=remount-ro 0       1
UUID=a2b49621-fda5-41b7-bce5-a999cb9256aa /boot           ext2    defaults        0       2
/dev/mapper/shinoko--vg-swap_1 none            swap    sw              0       0
//MAKOTO/server_backups$    /mnt/bkup    cifs    uid=chris,credentials=/root/auth.conf    0     0

---------- Current Mount Details of 'mount':
/dev/mapper/shinoko--vg-root on / type ext4 (rw,relatime)
/dev/sda1 on /boot type ext2 (rw,relatime,stripe=4)

---------- USB Information from 'lsusb -t -v':
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/3p, 12M
        ID 03f0:010c HP, Inc Multimedia Keyboard Hub
        |__ Port 1: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 12M
            ID 03f0:020c HP, Inc Multimedia Keyboard
        |__ Port 1: Dev 3, If 1, Class=Human Interface Device, Driver=usbhid, 12M
            ID 03f0:020c HP, Inc Multimedia Keyboard
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/8p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 1: Dev 2, If 0, Class=Mass Storage, Driver=usb-storage, 480M
        ID 13fe:1e00 Kingston Technology Company Inc. Flash Drive 2 GB [ICIDU 2 GB]
    |__ Port 2: Dev 3, If 0, Class=Mass Storage, Driver=usb-storage, 480M
        ID 058f:6366 Alcor Micro Corp. Multi Flash Reader

---------- Video Details from 'lshw':

  *-display
       description: VGA compatible controller
       product: GF119M [GeForce 610M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: 
           irq:35 
           memory:da000000-daffffff 
           memory:d0000000-d7ffffff 
           memory:d8000000-d9ffffff 
           ioport:d000(size=128) 
           memory:c0000-dffff

   --- Graphics Environment Continued form 'various graphics ENVs' ----
The Current Configured Desktop is: <Not Populated> 
The Current Desktop Session is: <Not Populated> 
The Current Session Type is: <No Graphics Session Type Loaded> 
The Current Display Manager is: lightdm
The Current Desktop Theme: 'Greybird'
The Current Virtual TTYs being used are:
    TTY#    Used By
    tty2    gdm-x-session
    tty2    Xorg
    tty2    gnome-session-b

---------- Repository Information from '/etc/apt/sources.list and etc/apt/sources.list.d/':

Sources List:
deb http://us.archive.ubuntu.com/ubuntu/ focal main restricted
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ focal universe
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ focal multiverse
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse

Sources List from SourcesD:
/etc/apt/sources.list.d/matrix.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/certbot-ubuntu-certbot-xenial.list.save:
File had no entries.
/etc/apt/sources.list.d/nginx-ubuntu-mainline-bionic.list.save:
File had no entries.
/etc/apt/sources.list.d/mariadb.list.save:
File had no entries.
/etc/apt/sources.list.d/nginx-ubuntu-mainline-bionic.list:
File had no entries.
/etc/apt/sources.list.d/lb5-alpha.list.distUpgrade:
deb https://chrisiverson.net/lb5-alpha/repo dev main
/etc/apt/sources.list.d/nginx-ubuntu-mainline-bionic.list.distUpgrade:
deb http://ppa.launchpad.net/nginx/mainline/ubuntu bionic main
/etc/apt/sources.list.d/mariadb.list:
File had no entries.
/etc/apt/sources.list.d/mariadb.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/matrix.list:
File had no entries.
/etc/apt/sources.list.d/ondrej-ubuntu-nginx-mainline-focal.list:
deb http://ppa.launchpad.net/ondrej/nginx-mainline/ubuntu focal main
/etc/apt/sources.list.d/certbot-ubuntu-certbot-xenial.list:
File had no entries.
/etc/apt/sources.list.d/matrix.list.save:
File had no entries.
/etc/apt/sources.list.d/lb5-alpha.list:
deb https://chrisiverson.net/lb5-alpha/repo dev main
/etc/apt/sources.list.d/ondrej-ubuntu-php-xenial.list.save:
File had no entries.
/etc/apt/sources.list.d/microsoft-prod.list.distUpgrade:
deb [arch=amd64] https://packages.microsoft.com/ubuntu/18.04/prod bionic main
/etc/apt/sources.list.d/certbot-ubuntu-certbot-xenial.list.distUpgrade:
deb-src http://ppa.launchpad.net/certbot/certbot/ubuntu bionic main
/etc/apt/sources.list.d/lb5-alpha.list.save:
File had no entries.
/etc/apt/sources.list.d/ondrej-ubuntu-php-xenial.list.distUpgrade:
deb-src http://ppa.launchpad.net/ondrej/php/ubuntu bionic main
/etc/apt/sources.list.d/microsoft-prod.list.save:
File had no entries.
/etc/apt/sources.list.d/ondrej-ubuntu-php-xenial.list:
File had no entries.

---------- Other Details from 'Various':
The current kernel version is:       5.11.0-27-generic 
The current release description is:  Ubuntu 20.04.3 LTS 
Original Installation Date:          2016-07-04+13:46:13 
Original Installation Media: Ubuntu-Server 16.04 LTS "Xenial Xerus" - Release amd64 (20160420.3)


These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference from 'apt-cache show':
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.11.0.40.44
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.4.0.26.32

   --- HWE Package Status from 'dpkg':
HWE package linux-generic-hwe-20.04 was not detected. Please check 
kernel version to verify range

   --- Certified Hardware Platform Status: (By the Ubuntu Wiki Standards)
Ubuntu Certified Hardware Platform. Safe to install 
the Hardware Enablement Stack (HWE).

Currently logged in User(s):
NAME     LINE         TIME         COMMENT

The User running this script was: chris
uid=1000(chris)
gid=1000(chris)
groups=1000(chris),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),
110(lxd),115(lpadmin),116(sambashare),1002(tlsKeyAccess)

*** End Of Report ***
```

---

### Post by MAFoElffen on 2021-11-28
Never mind... I'm off work now, and now it comes up for me fine. I can see it now...

Original installatination: 
```
Original Installation Media: Ubuntu-Server 16.04 LTS "Xenial Xerus" - Release amd64 (20160420.3)
```

The original fstab and mount information:
```

---------- Mount Details of '/etc/fstab':
/dev/mapper/shinoko--vg-root /               ext4    errors=remount-ro 0       1
UUID=a2b49621-fda5-41b7-bce5-a999cb9256aa /boot           ext2    defaults        0       2
/dev/mapper/shinoko--vg-swap_1 none            swap    sw              0       0
//MAKOTO/server_backups$    /mnt/bkup    cifs    uid=chris,credentials=/root/auth.conf    0     0

```
Relevant disk and lvm info:
```

---------- Disk/Partition Information From 'lsblk':
NAME                     SIZE FSTYPE LABEL MOUNTPOINT MODEL
sda                    111.8G                         Crucial_CT120M50
[COLOR=#ff0000]|-sda1                   487M              /boot [/COLOR]     
|-sda2                     1K                         
`-sda5                 111.3G                         
  [COLOR=#ff0000]|-shinoko--vg-root   107.3G              /          
  `-shinoko--vg-swap_1     4G                         [/COLOR]

------- 'lsblk' information continued ...
NAME                   HOTPLUG PARTUUID UUID
sda                          0          
|-sda1                       0          
|-sda2                     0
`-sda5                       0          
  |-shinoko--vg-root         0          
  `-shinoko--vg-swap_1       0          

---------- Disk/Partition Information From 'fdisk':

Disk /dev/sda: 111.81 GiB, 120034123776 bytes, 234441648 sectors
Disk model: Crucial_CT120M50
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x72d93c3e

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048    999423    997376   487M 83 Linux
/dev/sda2       1001470 234440703 233439234 111.3G  5 Extended
/dev/sda5       1001472 234440703 233439232 111.3G 8e Linux LVM

Partition 2 does not start on physical sector boundary.

Disk /dev/mapper/shinoko--vg-root: 107.34 GiB, 115246891008 bytes, 225091584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/mapper/shinoko--vg-swap_1: 3.10 GiB, 4269801472 bytes, 8339456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/sdb: 3.86 GiB, 4127195136 bytes, 8060928 sectors
Disk model: USB DISK 2.0    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x2cf4ba3a

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdb1  *          0 5999871 5999872  2.9G  0 [COLOR=#ff0000]Empty[/COLOR]
/dev/sdb2       5271500 5279499    8000  3.9M ef [COLOR=#ff0000]EFI (FAT-12/16/32)[/COLOR]
/dev/sdb3       6000640 8060927 2060288 1006M 83 Linux

```
And in BIOS:
```

Current boot mode:   Legacy mode (alias CSM alias BIOS mode)
EFI variables are not supported on this system

```

=========================
So why did I point those out?

I see that you are booting Legacy boot to an MBR partitoned disk, where sda1 is your Boot partition and sda5 is an LVM2 extend (PV, type LVM/BE). Curious that sda2 shows as an EFI partition on a machince that is only reporting that it is capable of Legacy Boot(?) Bu that is a distraction and curiosity for now.

@Darko? Look the the partition type identified by /dev/sda1... In 16.04, when it did an LVM2 install on Server Edition, it set the boot partion as type exte2 or ext3 didn't it? That should still show up as being identified as type Linux... Not as "Empty". /dev/sda1 is the bootable "boot partition" partition... That is just odd, and not at all what I would have expected...

---

### Post by darkod on 2021-11-28
@MAFoElffen, I think you mixed up sda and sdb (the usb stick used for live boot and diagnosis). Reread the fdisk part in your last post again. sda is shown relatively OK. It shows sda1 as Linux, and the logical partition sda5 holding the LVM.

It is sdb that shows the Empty and EFI.

However I have no explanation why LVM is not activated at boot. Might have something to do that as we know now, this was upgrade 16.04 -> 18.04 -> 20.04.

Maybe the last upgrade process missed to do something?? Would some sort of update initramfs help (is possible to do it from chroot I believe)?

---

### Post by oldfred on 2021-11-28
My systems often change flash drive to sda & rest of drives move up one.

Lets try Boot-Repair & its advanced mode. Not sure if it will mount LVM or not, but if it does not see if you can manually mount it or it will not work.
And choose the full reinstall of grub and new kernel. New kernel & grub will trigger an update to initramfs. You can do the same if chrooted. 

Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO (unless 21.10)
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by iversc on 2021-11-28
Here's the paste link to the boot-info summary report.

[https://paste.ubuntu.com/p/Q4tsCwVjCD/](https://paste.ubuntu.com/p/Q4tsCwVjCD/)

---

### Post by oldfred on 2021-11-28
Do not run the auto fix, but use advanced mode and choose total reinstall of grub and update to newest kernel options.
Make sure LVM is mounted. but it looks like it did get mounted in report.

---

### Post by iversc on 2021-11-28
Sadly, doesn't seem to have fixed the issue.  Still get stuck at the same point; initramfs insists that the vg doesn't exist.

I did wind up having to follow those steps twice, though; it seems the helper program mistook the first word of "no raid disks" to be a device name, and tried to install grub to /dev/mapper/no...

Second time, I made sure to explicitly tell it to set grub up on /dev/sda.

I've got pastebin results for both of my attempts at running the repair.


First one: [https://paste.ubuntu.com/p/rFgkqPCxKS/](https://paste.ubuntu.com/p/rFgkqPCxKS/)

Second one: [https://paste.ubuntu.com/p/nbn2jMTmrX/](https://paste.ubuntu.com/p/nbn2jMTmrX/)

---

### Post by oldfred on 2021-11-28
Did you use Advanced mode?

Not seen all the kernels listed like that? Have you not housecleaned old kernels?
Assume this is an upgrade and that is why it is looking at all the very old kernels?
When chrooted run 
sudo apt autoremove

You have at least one repository not working. That confuses the reinstall.
Failed to fetch [https://chrisiverson.net/lb5-alpha/repo/dists/dev/InRelease](https://chrisiverson.net/lb5-alpha/repo/dists/dev/InRelease)

You also show menu.lst.
That is from grub, now grub legacy which has not been used for 10 years.
Did you try to manually install grub, not grub-pc which is the BIOS boot version of grub2?

---

### Post by iversc on 2021-11-29
> **oldfred said:**
> Did you use Advanced mode?

Yes, and going in to detail, on each tab, I chose:

Main options: Restall GRUB, Unhide boot menu

GRUB location: Separate /boot partition sda1, Place GRUB into sda(was mapper/no for the first run)

GRUB options: Purge GRUB before reinstalling it, purge kernels then reinstall latest kernel

MBR options: tab is blank

Other options: Create a BootInfo summary, Upload the report to a pastebin, Participate to statistics, Check internet connection


> **oldfred said:**
> Not seen all the kernels listed like that? Have you not housecleaned old kernels?
Assume this is an upgrade and that is why it is looking at all the very old kernels?

I don't know why they all show up as installed; before the purge, only the three most recent were installed.  There's no way my boot partition could even hold all that.

Heck, even the script itself says they're not installed when it tries to remove them later on!

Maybe it is a legacy of the fact that this has been upgraded multiple times?

Hmm, looking at the dpkg output, they all say they're in "rc" status - desired action "remove", package status "config files", if I understand the dpkg output correctly.

I don't know why so many kernels would be in that status.

> **oldfred said:**
> When chrooted run 
sudo apt autoremove

Done, all those kernels still show up as "rc" status when dpkg -l is run.

I went in and used dpkg -P to remove all trace of those old kernels completely.


> **oldfred said:**
> You have at least one repository not working. That confuses the reinstall.
Failed to fetch [https://chrisiverson.net/lb5-alpha/repo/dists/dev/InRelease](https://chrisiverson.net/lb5-alpha/repo/dists/dev/InRelease)

I'll just remove that to prevent issues.  (It's a personal project repo hosted on the very device that I'm troubleshooting.)


> **oldfred said:**
> You also show menu.lst.
That is from grub, now grub legacy which has not been used for 10 years.
Did you try to manually install grub, not grub-pc which is the BIOS boot version of grub2?

I'm not sure... I don't think I tried anything that would wind up installing that version of grub.  The most grub troubleshooting I did before this was just trying to run update-grub.

---

### Post by oldfred on 2021-11-29
If you install to sda, that should work.
But it should be updating grub.cfg not a menu.lst.
I did not think Boot-Repair even worked with grub legacy.

The kernel listing must be some issue with Boot-Repair.

---

### Post by iversc on 2021-11-29
I think I had an old package from years ago that was autogenerating a menu.lst file.  I got rid of that package, as well as tidied up the kernels, and this was the latest boot-repair attempt, using the same options.

[https://paste.ubuntu.com/p/xx6tS65dSm/](https://paste.ubuntu.com/p/xx6tS65dSm/)

Sadly, still no luck, though.  Still trying stuff when I can.

I did find someone that seemed to have the same symptoms(with a hardware difference; they have a hardware RAID, and I don't), but they just wound up rebuilding the server from scratch.  

[https://unix.stackexchange.com/questions/672137/lvm-volume-group-not-found](https://unix.stackexchange.com/questions/672137/lvm-volume-group-not-found)


Thanks for your assistance so far, you've definitely helped me find some things that needed to be looked at, even if I haven't fixed the issue yet.

---

### Post by oldfred on 2021-11-30
Report is not showing fstab which is in the LVM.
Is Boot-Repair correctly mounting LVM?

Post /etc/fstab from your chroot or when running Boot-Repair and LVM is mounted.
Some found manually mounting (and decrypting when encrypted) before running Boot-Repair works better?

---

### Post by darkod on 2021-11-30
Honestly I am quite disconnected from the boot-info script lately and what its automatic processes do. It looks like you removed all kernels and installed just the latest one, right?

I would have liked to see what happens when booting an older kernel. Do you still have any?

If yes, try to boot an older one. In the grub menu select the Advanced entry, and you will see a list of older kernels too. Select the oldest one you have, but select the "normal" entry, not the 'recovery'.

Also can you please confirm if you noticed how did this exactly happen? Some important key points are:

1). Did it stop booting the LVM right after the 18.04 -> 20.04 upgrade? Or was it booting X months and then decided to give you issues?

2). Did it stop booting after you did apt-get dist-upgrade for example? In the link you mentioned in post #16 the problem might have been related to updating the system/packages.

I know all of this is frustrating but so far no solution was found. So depending how you feel you might also decide to simply reinstall from scratch. One advice for the future though. Try not to put everything on single root LV. You are chopping off your own foot there because if you format the LV to reinstall, you lose all data on it. On the other hand if you have another LV mounted at /data for example, you can keep it intact but do a complete OS reinstall.

PS. If you don't have any older kernel I would try to install some using chroot and then try to boot it. Worth of try. But you would have to install the specific kernel by hand so to speak, because it won't be the latest one. I would even try with the very first kernel that 20.04 came out with.

---

### Post by iversc on 2021-12-01
> **oldfred said:**
> Report is not showing fstab which is in the LVM.
Is Boot-Repair correctly mounting LVM?

Post /etc/fstab from your chroot or when running Boot-Repair and LVM is mounted.
Some found manually mounting (and decrypting when encrypted) before running Boot-Repair works better?

I'll pull out the fstab and post it, as well as trying the boot-repair again after manually mounting the volume.


> **darkod said:**
> Honestly I am quite disconnected from the boot-info script lately and what its automatic processes do. It looks like you removed all kernels and installed just the latest one, right?

I would have liked to see what happens when booting an older kernel. Do you still have any?

If yes, try to boot an older one. In the grub menu select the Advanced entry, and you will see a list of older kernels too. Select the oldest one you have, but select the "normal" entry, not the 'recovery'.

I don't still have them, but the oldest one that was still on my system before trying all of this(I think was 5.4.0-87 or 88) resulted in the same issue.



> **darkod said:**
> Also can you please confirm if you noticed how did this exactly happen? Some important key points are:

1). Did it stop booting the LVM right after the 18.04 -> 20.04 upgrade? Or was it booting X months and then decided to give you issues?

2). Did it stop booting after you did apt-get dist-upgrade for example? In the link you mentioned in post #16 the problem might have been related to updating the system/packages.

It wasn't a version upgrade; while this system was an upgrade from 18.04, I upgraded to 20.04 pretty much as soon as the point release was available and upgrading was enabled.  It's been running since then without issues.

It was definitely after an update, though.  There were updates that were applied, but unfortunately, I'm unsure as to which upgrades were applied.  I've got automatic upgrades turned on for many things, and it was in a reboot-required state for quite a while before I rebooted to finish the update that needed it.



> **darkod said:**
> I know all of this is frustrating but so far no solution was found. So depending how you feel you might also decide to simply reinstall from scratch. One advice for the future though. Try not to put everything on single root LV. You are chopping off your own foot there because if you format the LV to reinstall, you lose all data on it. On the other hand if you have another LV mounted at /data for example, you can keep it intact but do a complete OS reinstall.

PS. If you don't have any older kernel I would try to install some using chroot and then try to boot it. Worth of try. But you would have to install the specific kernel by hand so to speak, because it won't be the latest one. I would even try with the very first kernel that 20.04 came out with.

I've actually tried this with a couple older kernel versions; one dating back to July, and one dating back to January.  (5.4.0-80 and 5.4.0-60, IIRC).  Not a bad idea to try the initial kernel that 20.04.1 came with, though, since I know for sure that worked.


While I am considering a rebuild, I'm honestly very curious as to what exactly is happening.  I'll keep plugging away.  Thanks!

---

