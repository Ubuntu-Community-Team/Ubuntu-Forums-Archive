---
title: "Adaptec 2405 Ubuntu 8.04.1 server resest after grub"
date: 2008-09-30
forum: Server Platforms
---

### Post by mugedoc on 2008-09-30
In a PC with ASUS M2NPV-VM motherboard, processor AM2 X2 3800 AMD (64 BITS), two hd Western Digital 1TB'm riding a RAID 1 controller with the Adaptec 2405.
Having previously created in the 2405 controller Adaptec Array of discs using RAID 1, the bios of the plate is both the boot CD-ROM as the raid 1.
I make the installation of ubuntu server 8.04.1 and sees a single disk sda, partitioning disks with a partition for boot, one for /, / usr, / var ....
The installation ends successfully, sack the installation CD and restart after the BIOS and the Adaptec controller, is grub, I choose the boot and was hung, it does not show anything, and the keyboard does not respond, or Shift key depressed, or numerical , Or anything
After testing several times, it started the installation CD in rescue mode, and loads ubuntu, from partitions Console amount and the facility there, I notice that the driver has aacraid in / var / log / installer, I review the logs in / var / log and are empty, there has never been a starter.
I check in / boot / grub / device.map and pointing to / dev / sda
I try to re-create the RAID 1, even low-level formatting disks from the controller, reinstall the server ubuntu 8.04.1 and everything's fine. Ther Extract CD, restarts, it shows grub and restarts, does not load the ubuntu ...
What is happening? The rescue mode if I start the installation but has never come to boot ...

Any idea ???

--- thanks

---

### Post by mugedoc on 2008-10-01
======================================================================
# With Fedora 9 is also the grub was stopped and the keyboard does not respond.
Booting Fedora ' (2.6.25-14.fc9.x86_64)'
root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel /vmlinuz-2.6.24-14.fc9.x86_64 ro root=UUID=be..................................
[Linux-bzimage, setup=0x2e00, size=0x1f63b8]
# And since it does nothing more ....
# The keyboard did not answer the block number or block capitals

======================================================================
And other time, I'm try install Centos 5.2, finish installation, restart, show grub and display
Booting CentOS ' (2.6.18-92.el5)'
root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel /vmlinuz-2.6.18-92.el5 ro root=/dev/VolGroup00/LogVol00
[Linux-bzImage, setup=0x1e00, size=0x1c3f9c]
_
# No load linux, this is the last display line...
======================================================================
Return to ubuntu, add new hd, install ubuntu server 8.04.1 , /boot / in a hd ide, /home in a RAID Apactec 2405, finish install, extrac CD, reboot, and not show grub, nothig...
:guitar::guitar:


======================================================================

---

### Post by mugedoc on 2008-10-01
BIOS setup the boot recognize SCSI adaptec, is the only one harddisk bootable, linux kernel have got module aacraid from 2.6.xx, I try change in the grub to boot paremter pci=noacpi aacraid.............. press b and nothing , the linux not load nothing...

¿ Do you have any idea ?
:popcorn:

---

### Post by mugedoc on 2008-10-01
modify the BIOS, restore default values and save, reboot the computer, load the bios, load de Adaptec 2405, show one RAID Array, show grub, select default and nothing... the key board not response and the screen is black, with blink cursor.....
:confused:

---

### Post by mugedoc on 2008-10-01
Start computer from CD ubuntu, mode recue, from console mount the partition and view the log:

cat /var/log/boot
(Nothing has been logged yet.)

cat /var/log/dmesg
(Nothing has been logged yet.)

cat /var/log/message

/* void, 0 bytes */

---

### Post by mugedoc on 2008-10-01
Hello from Adaptec-

Thank you for your message.

None of the OS's utilized (Ubuntu 8.04.1, Fedora 9, CentOS 5.2) are listed as a supported OS for the 2405 controller.

[http://www.adaptec.com/en-US/support/raid/sas_raid/SAS-2405/](http://www.adaptec.com/en-US/support/raid/sas_raid/SAS-2405/)

We do have Source Code available for unsupported revisions of Linux here;

[http://www.adaptec.com/en-US/downloads/linux_source/linux_source_code?productId=SAS-2405&dn=Adaptec+RAID+2405](http://www.adaptec.com/en-US/downloads/linux_source/linux_source_code?productId=SAS-2405&dn=Adaptec+RAID+2405)


The source code is provided on an "as is" basis for building and installing the drivers on unsupported versions of Linux.

For details on building and installing source code please see your Linux documentation.

See the Readme for additional information and the Release Notes for a description of the release.

It would also be suggessted, to negate any possible resource issues, that the controller and the MB be at the latest FW/ BIOS revisions.

Thank you for using ASK US

---

### Post by mugedoc on 2008-10-02
/ / Adaptec informs me that I need to download the drivers, although in theory and brings the AACR in the kernel.

> We do have Source Code available for unsupported revisions of Linux here;
> [http://www.adaptec.com/en-US/downloads/linux_source/linux_source_code?productId=SAS-2405&dn=Adaptec](http://www.adaptec.com/en-US/downloads/linux_source/linux_source_code?productId=SAS-2405&dn=Adaptec) RAID 2405

/ / Download the latest driver
[http://www.adaptec.com/en-US/speed/raid/aac/linux/aacraid_dkms_v1_1_5-2459_tgz.htm](http://www.adaptec.com/en-US/speed/raid/aac/linux/aacraid_dkms_v1_1_5-2459_tgz.htm)

aacraid_dkms_v1.1.5-2459.tgz

/ * NOTES .........................
  * The complication is that the ubuntu does not start, but the grub is not started after the linux.
  * All these operations have to do starting the system from the CD in rescue mode
  * Mounting partitions manually, loading the shell ... / bin / bash
  * The kernel is not loaded into memory which is installed on the disk, but the kernel on the CD.
  * Who knows what will happen?
  *
  * Documents in which I have relied to do this ...
  *
  * In Spanish [http://www.wikilearning.com/tutorial/como_compilar_el_kernel_en_ubuntu-como_compilar_el_kernel_en_ubuntu/8234-1](http://www.wikilearning.com/tutorial/como_compilar_el_kernel_en_ubuntu-como_compilar_el_kernel_en_ubuntu/8234-1)
  * In Spanish [http://www.ubuntu-es.org/index.php?q=node/97169](http://www.ubuntu-es.org/index.php?q=node/97169)
  * In English there are many post and documentation .... googlea a bit
  * [Www.google.com](Www.google.com) / linux
  * /
 
# # # Guess can be made in far fewer steps, and maybe not even need to download the source code
# # # Just compile the driver and add it as a module.
# # # If anyone knows how you count. thanks


/ / Decompressing
[user @ localhost] $ tar-xvzf aacraid_dkms_v1.1.5-2459.tgz

/ / I get the following files AACR-1.1.5.2459-dkms.noarch.rpm DKMS-2.0.19-1.noarch.rpm
/ / Read the "readme.txt"

/ / Convert rpm to deb, to install this alien
[user @ localhost] $ sudo apt-get install alien debhelper dpkg-dev build-essential
/ / transform the rpm to deb
[user @ localhost] $ sudo alien AACR-1.1.5.2459-dkms.noarch.rpm
[user @ localhost] $ sudo alien DKMS-2.0.19-1.noarch.rpm
/ / Install the deb
[user @ localhost] $ sudo dpkg-i AACR-1.1.5.2459-1-all.deb
[user @ localhost] $ sudo dpkg-i DKMS-2.0.19-2-all.deb

/ / Then you create sources / usr/src/aacraid-1.1.5.2459

/ / I do not have the kernel source for what I have to download

/ / I believe that this had already done so
[root @ localhost] $ apt-get install build-essential

/ / Disclaimer sources? I think this is just the image ...
[root @ localhost] $ apt-get install linux-image-2.6.24-19-server
# # # This was necessary?

/ / Now that I download the source code
[root @ localhost] $ apt-get install linux-source-2.26-24
# # # Perhaps just needed the amd64

/ / Unzip the tar.bz2
[root @ localhost] $ cd / usr / src
[root @ localhost] $ tar-xvjf linux-source-2.6.24.tar.bz2

/ / Libncurses do you have?
[root @ localhost] $ apt-cache search libncurses
/ / If you do not have
[root @ localhost] $ apt-get install libncurses

/ / Move to the directory of sources
[root @ localhost] $ cd / usr/src/linux-source-2.6.24

/ / From a configuration known
[root @ localhost] $ cp / boot/config-2.6.24-19-server. config

/ / From a configuration known
[root @ localhost] $ oldconfig make menuconfig

# # # Gives me errors but I still
# # # I think I will add many modules you do not need ....

/ / Install another utility to compile and thus avoiding run make dep, make clean, make bzImage and make modules
[root @ localhost] $ apt-get install kernel-package

/ / Man make-kpkg

/ / Compile, I think it clean
[root @ localhost] $ make-kpkg clean

/ / Compile, and create image header
[root @ localhost] $ make-kpkg - initrd kernel_image kernel_headers

# # # # This takes a long time, a respite tomato ...

# # # #

/ / It has created two packages. Deb
[root @ localhost] $ cd / usr / src
[root @ localhost] $ ls-ltr

/ / I has generated the following. Deb ?????
linux-header-2.6.24-3_2.6.24.3-10.00.Custom_amd64.deb
linux-image-2.6.24-3_2.6.24.3-10.00.Custom_amd64.deb

/ / Install the kernel generated, it is easy
[root @ localhost] $ dpkg-i linux-image-2.6.24-3_2.6.24.3-10.00.Custom_amd64.deb
/ / Install kernel headers
[root @ localhost] $ dpkg-i-header linux-2.6.24-3_2.6.24.3-10.00.Custom_amd64.deb

# # # Will update grub? I think so

/ / Tips. Tips -> copied from Alejandro Garrido Mota -> [http://www.ubuntu-es.org/index.php?q=node/97169](http://www.ubuntu-es.org/index.php?q=node/97169)
* All kernels that have existed in Linux can be found at: [http://kernel.org/pub/linux/kernel](http://kernel.org/pub/linux/kernel)
* Consult the manual for make-kpkg documentation that is simple and Spanish. man make-kpkg

/ / Now the driver for the Adaptec 2405, you'd forgotten that all this is to add the AACR in theory driver is already in the kernel?

/ / Build the driver to a different system to native, as the charged is the cd and installed it has not started
/ / Consult readme.txt containing the aacraid_dkms_v1.1.5-2459.tgz
/ / According to your case

/ / 1. I try this and nothing, error
[root @ localhost] $ DKMS build 2.6.24.3-m-k-AACR v 1.1.5.2459
[root @ localhost] $ DKMS install 2.6.24.3-m-k-AACR v 1.1.5.2459

/ / 2. I try this and nothing, error
[root @ localhost] $ DKMS build - kernelsourcedir = / usr/src/linux-source-2.6.24-k 2.6.24.3-m-AACR v 1.1.5.2459
[root @ localhost] $ DKMS install - kernelsourcedir = / usr/src/linux-source-2.6.24-k 2.6.24.3-m-AACR v 1.1.5.2459

/ / 3. I try this and nothing, error
[root @ localhost] $ DKMS build - config = / boot/config-2.6.24.3 - kernelsourcedir = / usr/src/linux-source-2.6.24-k 2.6.24.3-m-AACR v 1.1.5.2459
[root @ localhost] $ DKMS install - config = / boot/config-2.6.24.3 - kernelsourcedir = / usr/src/linux-source-2.6.24-k 2.6.24.3-m-AACR v 1.1.5.2459

# # # Gives me the error in the "DKMS Buil ..."

/ / As the sources are at AACR / usr/src/linux-source-2.6.24
/ / Vamo to try to create a deb and then install it with dpkg-i
/ / Use this mini tutorial
[http://www.ubuntu-es.org/index.php?q=node/11143](http://www.ubuntu-es.org/index.php?q=node/11143)

# # # It does not create a deb as of / usr/src/aacraid-1.1.5.2459
dh_make
fakeroot debian / rules binary
/ / Error 2

I will keep trying ............
:guitar:

---

### Post by mugedoc on 2008-10-02
aacraid in ubuntu is equal that aacraid-1.1.5.2459 ???

---

### Post by mugedoc on 2008-10-07
In the end, reinstall the ubuntu.
1. I think the first RAID 1 mirroring from the BIOS of the controller Adaptec 2405, using two disks
western digital.
2. Then check the BIOS on the motherboard that harddisk recognizes the card as a hard disk.
3. Ubuntu 8.04.1 install the server, detects a single hard disk sda.
I think the partitions and install ubuntu.
4. The installation is perfectly restart, is grub and restart without loading anything about linux.
5. Hard drives connect directly to the motherboard, is all the information, partitions, etc ...
Boots the ubuntu perfectly, download the driver, so to convert. Deb, install it, and what do you with DKMS. Everything OK.
6. Again I connect the controller Adaptec 2405, the BIOS of the controller makes REBUILD,
GRUB shows and instead of loading Linux, restarts ....


/ / Download the latest driver
[http://www.adaptec.com/en-US/speed/raid/aac/linux/aacraid_dkms_v1_1_5-2459_tgz.htm](http://www.adaptec.com/en-US/speed/raid/aac/linux/aacraid_dkms_v1_1_5-2459_tgz.htm)

/ / Create directory, and move ....
[user @ localhost] $ mkdir AACR
[user @ localhost] $ cd AACR
[user @ localhost] $ mv descargas/aacraid_dkms_v1.1.5-2459.tgz.
/ / Decompress
[user @ localhost] $ tar-xvzf aacraid_dkms_v1.1.5-2459.tgz

/ / Convert rpm to deb, to install this alien
[user @ localhost] $ sudo apt-get install alien debhelper dpkg-dev build-essential
/ / transform the rpm to deb
[user @ localhost] $ sudo alien AACR-1.1.5.2459-dkms.noarch.rpm
/ / Install
[user @ localhost] $ sudo dpkg-i aacraid_1.1.5.2459-1_all.deb

/ / Install DKMS
[user @ localhost] $ sudo apt-get install DKMS

/ / We need the sources
[user @ localhost] $ sudo apt-get install linux-headers-2.6.24-19-server


/ / Build and install a driver:
[root @ localhost] $ DKMS add AACR-m-v 1.1.5.2459
[root @ localhost] $ DKMS build-m AACR-v 1.1.5.2459
products in / var/lib/dkms/aacraid/1.1.5.xxxx / <kernel> / <arch> / module /
[root @ localhost] $ DKMS install-m AACR-v 1.1.5.2459


Even taking the driver AACR-1.1.5.2459 show grub and after reboot, reset

---

