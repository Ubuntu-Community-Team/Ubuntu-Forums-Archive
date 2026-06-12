---
title: "Howto: Boot Live CD over PXE (detailed, 10.04.3 desktop)"
date: 2012-04-29
forum: Server Platforms
---

### Post by Jonathan L on 2012-04-29
Dear all

Just putting my notes in public in case of some use.

_**How to boot the Live CD over PXE**_

Exact details are given for booting 10.04.3 Desktop, from 10.04.3 Server.

I have tested these instructions and booted these images:

```
f63028da38308d917cd1460e14fb8540  ubuntu-10.04.3-desktop-i386.iso
557231ce93ae8e98e214424cb02f8761  ubuntu-10.04.4-desktop-i386.iso
d791352694374f1c478779f7f4447a3f  ubuntu-12.04-desktop-i386.iso
5eccab9d5956956c3dc28d5a6c4a2e69  edubuntu-10.04-dvd-i386.iso
```In the following instructions, substitute for the green part if you're not using ubuntu-10.04.3-desktop-i386.iso

I've tried this with quite a number of pieces of hardware, including

[LIST]
[*]HP DL320 G2 server 2 Gbyte RAM
[*]Lenovo Thinkpad X121e (won't boot 10.04, requires different ethernet driver)
[*]Many Intel motherboards
[/LIST]
 
Note that I don't unpack the CD-ROM image, I use it as is,  (but there's no reason you can't unpack it into the exports directory).   I keep them like that so I have a simple directory of all the Live-CD  for testing, and the network boot menu offers you the list of versions.

This setup is in live production use on a couple of sites.  There is a  known bug (at least with this 10.04.3 Desktop) which is that you can't  boot several clients simultaneously as there is a bug in the DHCP  client.

_**SERVER PREPARATION**_

You can use any server. or combination of servers, which provides
DHCP -- you need to specify some extra flags
TFTP -- to deliver the initial kernel and filesystem file
NFS -- to deliver the subsequent files

The following describes how to set that up for 10.03 server.

_**Packages**_

The server needs a few pieces of software:
```
sudo apt-get install -y dhcp3-server
sudo apt-get install -y tftpd-hpa
sudo apt-get install -y nfs-kernel-server
```If you want to use the exact packages that are known to work,, Use ubuntu-10.04.3-server-i386.iso, mount it on /cdrom, and do

DHCPD

```
sudo dpkg -i /cdrom/pool/main/d/dhcp3/dhcp3-server_3.1.3-2ubuntu3_i386.deb
```TFTPD

```
sudo dpkg -i /cdrom/pool/main/t/tftp-hpa/tftpd-hpa_5.0-11ubuntu2.1_i386.deb
```NFS

```
  sudo dpkg -i /cdrom/pool/main/p/portmap/portmap_6.0.0-1ubuntu2.1_i386.deb
  sudo dpkg -i /cdrom/pool/main/libe/libevent/libevent-1.4-2_1.4.13-stable-1_i386.deb
  sudo dpkg -i /cdrom/pool/main/libg/libgssglue/libgssglue1_0.1-4_i386.deb
  sudo dpkg -i /cdrom/pool/main/libn/libnfsidmap/libnfsidmap2_0.23-2_i386.deb
  sudo dpkg -i /cdrom/pool/main/libr/librpcsecgss/librpcsecgss3_0.19-2_i386.deb
 sudo dpkg -i /cdrom/pool/main/n/nfs-utils/nfs-common_1.2.0-4ubuntu4.1_i386.deb
sudo dpkg -i /cdrom/pool/main/n/nfs-utils/nfs-kernel-server_1.2.0-4ubuntu4.1_i386.deb
```_**DHCP settings, using ISC DHCPD 3**_

Each of my clients is given a static address: you'll probably have  dynamic allocation.  The critical part is server-name, and filename.  Configuration is done (for this DHCP software) in /etc/dhcp3/dhcpd.conf, and you'll need to edit the red parts to suit your own network.

```
host client1 {
  hardware ethernet [COLOR=Red]11:22:33:44:55:66[/COLOR];
[COLOR=Black]  fixed-address [COLOR=Red]192.168.1.66[/COLOR];
  option routers [COLOR=Red]192.168.1.16[/COLOR];
  [/COLOR][COLOR=Black]server-name "[COLOR=Red]192.168.1.32[/COLOR]";
[/COLOR][COLOR=Black]filename "pxelinux.0";[/COLOR]
}
```_**TFTPD**_

Using tftpd-hpa, didn't need any configuration of itself.


_**PXE Files**_

We need pxelinux.0 and vesamenu.c32, which are stored on the TFTP server and run on the client.

```
mkdir /tmp/scratch
cd /tmp/scratch
wget http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/netboot.tar.gz
tar xvfz netboot.tar.gz
sudo cp ubuntu-installer/i386/pxelinux.0 ubuntu-installer/i386/boot-screens/vesamenu.c32 /var/lib/tftpboot  
sudo mkdir /var/lib/tftpboot/pxelinux.cfg
md5sum /var/lib/tftpboot/pxelinux.0 /var/lib/tftpboot/vesamenu.c32 
86d7c19925f7cb5d9f1f54c0dec7812a  /var/lib/tftpboot/pxelinux.0
9c05a151103a42f0855f195408509a2e  /var/lib/tftpboot/vesamenu.c32


```We need a default file /var/lib/tftpboot/pxelinux.cfg/default: you'll need to edit the red part for your own network:

```
DEFAULT vesamenu.c32
MENU TITLE Network boot
LABEL [COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR]
  MENU LABEL [COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR]
[COLOR=Black]  KERNEL [COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR]/vmlinuz
  [/COLOR][COLOR=Black]APPEND initrd=[COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR]/initrd.[COLOR=Black]lz[/COLOR]  root=/dev/nfs boot=casper netboot=nfs  nfsroot=[COLOR=Red]192.168.1.32[/COLOR]:/exports/[COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR] splash --[/COLOR]
```_**CDROM image**_

I keep the CD-ROM images in /cdroms and mount them as loopback devices.

The IP address needs to be the IP address of your NFS server.

There are two cricital parts:
1.  Making available the CD-ROM tree
2.  Picking up a couple of the files and putting them in the TFTP  directory

```
sudo mkdir /cdroms
cd /cdroms
sudo wget http://old-releases.ubuntu.com/releases/1[COLOR=Lime]0.04.3/ubuntu-10.04.3-desktop-i386[/COLOR].iso
md5sum /cdroms/[COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR].iso
f63028da38308d917cd1460e14fb8540  /cdroms/[COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR].iso 
``` That CD-ROM is exported here:
```
sudo mkdir /exports/[COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR]
```  Add the following to /etc/fstab to auto-mount on reboot 
 ```
/cdroms/[COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR].iso     /exports/[COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR]    iso9660    ro,loop,auto    0     0
```Mount it
```
sudo mount -a
```  Following for /etc/exports to allow clients to read this directory
 ```
/exports/[COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR] 192.168.1.1/24(ro,no_root_squash,no_subtree_check,async) 
```Rexport
```
sudo exportfs -a 
```if you've copied the contents of the  CD-ROM to /exports/[COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR] you won't need the mount;  you'll still need the line in /etc/exports

  _**Make PXEBOOT area for this and put the files in it**_

 ```
sudo mkdir /var/lib/tftpboot/[COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR]
sudo cp /exports/[COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR]/casper/vmlinuz /var/lib/tftpboot/ubuntu-10.04.3-desktop-i386
sudo cp  /exports/[COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR]/casper/initrd.lz /var/lib/tftpboot/[COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR] 
```At this point you should be able to boot successfully.

_**CLIENT**_

You have to ensure that your client can boot PXE.  Sometimes you have to put this in the boot order of your computer in your BIOS, sometimes you have to press a key, often F12.

Typically the boot sequence looks like this:
1.  DHCP messages from the PXE boot firmware
2.  Tries to TFTP fetch various files, eventually using "default" (usually too fast to see)
3.  Menu of your single Ubuntu image
4.  Select it
5.  Loads kernel then the init file (with dots, 5 secs)
6.  Splash screen (lasts perhaps 50 sec)
7.  Ubuntu desktop

If the splash screen stays a long time (or you're impatient) press escape to see the text screen with messages, and escape to get back to the graphical screen.


[B]OPTIONAL: If you have to change the initial file system (initrd.lz)
[/B] 
First we unpack the .lz:

```
sudo mount -o loop /exports/[COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR]/casper/filesystem.squashfs /mnt
sudo mkdir /tmp/newroot
cd /tmp/newroot
lzcat -S .lz /exports/[COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR]/casper/initrd.lz  |  sudo cpio -i 
```OPTIONAL STEP: In my case I needed to add some  ether drivers (for Dell Poweredge R210-II), which  you will probably skip:
```
sudo cp -R /mnt/lib/firmware/2.6.32-33-generic/bnx2 lib/firmware/2.6.32-33-generic
sudo cp /mnt/lib/modules/2.6.32-33-generic/kernel/drivers/net/bnx2.ko    lib/modules/2.6.32-33-generic/kernel/drivers/net
sudo depmod -b `pwd` 2.6.32-33-generic
```Build the new initial file system:

```
sudo sh -c "find . | cpio --dereference -o -H newc | lzma -9 >  /var/lib/tftpboot/[COLOR=Lime]ubuntu-10.04.3-desktop-i386[/COLOR]/initrd.lz" 
```[U][B]
OPTIONAL: Edits to the Boot Filesystem
[/B][/U]
The boot filesystem is a squashfs filesystem as a big file on the  CD-ROM.  if you need to change anything on this you have to unpack,  edit, repack.  I needed to change rc.local of the booted system.

You must have squashfs tools and also mkisofs
```
 sudo apt-get install squashfs-tools

```Assuming (as above) the tree is mounted already, copy it to a temporary directory
```
mkdir /tmp/newimage
cd /exports/ubuntu-10.04.3-desktop-i386
# following careful copy from current directory includes .disk and any hidden 'dot' files
sudo cp -Rp . /tmp/newimage

```Unpack the squashfs system
```
 cd /tmp/newimage/casper
 sudo unsquashfs filesystem.squashfs 
```Add the extra files
```
 cd squashfs.root
 cd etc
# whatever edits you need
vi rc.local
```Repack the squashfs
```
 cd /tmp/newimage/casper
 sudo rm filesystem.squashfs
 sudo mksquashfs squashfs-root filesystem.squashfs
 sudo chmod 444 filesystem.squashfs
```Then repack the CD-ROM image.   (Or leave it as a normal directory tree under /exports).
```
sudo mkisofs -D -r -V "FIXED" -cache-inodes -J -l -b   isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot  -boot-load-size  4 -boot-info-table -o  ../ubuntu-10.04.3-desktop-i386-fixed.iso . 
```(adjust filenames in  mounts and exports if necessary)

I hope that helps someone.

Kind regards,
Jonathan

---

### Post by klqn on 2012-07-24
Thanks for the write up.  I followed you instructions and it worked on a single (1 NIC) PC, but when I try to boot a client with 4 NICs cards installed (eth0, eth1, eth2 and eth4)and eth0 connected - the rest of the NICs are not connected, it hangs there forever.

Do you know how fix this?

---

### Post by Jonathan L on 2012-09-20
> **klqn said:**
> Thanks for the write up.  I followed you instructions and it worked on a single (1 NIC) PC, but when I try to boot a client with 4 NICs cards installed (eth0, eth1, eth2 and eth4)and eth0 connected - the rest of the NICs are not connected, it hangs there forever.

Do you know how fix this?

Hi ...

Just noticed this question, I'm sure you've moved on by now.

My guess is that the kernel doesn't have the driver for the ethernet cards you're using.  The TFTP process works because that's in the ROM of eth0.  If this is the case, it will go wrong at the point the kernel needs to access the NFS.  This is the exact problem I had, which is covered by the section "OPTIONAL: If you have to change the initial file system".

Hope that helps.

Kind regards,
Jonathan.

---

### Post by cybercity@localhost on 2012-09-23
very nice tutorial thank you for posting.

---

### Post by lah7 on 2013-09-04
After spending hours reading confusing tutorials, thank you Jonathan L for your excellent guide.

I'm going to leave some additional notes about getting this to work on** Ubuntu 13.04 Server** with** Lubuntu 13.04 i386** as the live CD.

The entire guide remains similar, except from 2 things.
 
_**1.**_ The **dhcp3-server** didn't seem to work for me on **Ubuntu Server 13.04.** Instead, I used some advise as seen on [https://help.ubuntu.com/community/Installation/QuickNetboot](https://help.ubuntu.com/community/Installation/QuickNetboot) and installed **dnsmasq** instead.

```
sudo apt-get install dnsmasq
```

At the end of the file, add this to your network settings to** /etc/dnsmasq.conf**
```
dhcp-range=[COLOR=#0000ff]<Start IP Range>[/COLOR],[COLOR=#0000ff]<End IP Range>[/COLOR],12h
enable-tftp
tftp-root=/var/lib/tftpboot
dhcp-boot=pxelinux.0
dhcp-option=3,[COLOR=#0000ff]<Default Gateway>[/COLOR]
dhcp-option=6,[COLOR=#0000ff]<DNS Server>[/COLOR]
```

Restart the computer or execute:
```
sudo service dnsmasq restart
```
This would give clients dynamic addresses and not static IPs as the OP posted.
[U][B]

2.[/B][/U] The **tftpd-hpa** daemon didn't start by default.
```
sudo nano /etc/default/tftpd-hpa
```
Add the line: ```
RUN_DAEMON="yes"
```
As pointed out on [https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)


I hope this also may be useful to somebody in the future. :) Packages do change their behaviours over time.

---

### Post by aaronflora on 2013-11-22
Hi,

I followed this tutorial:
[http://www.howtogeek.com/61263/](http://www.howtogeek.com/61263/)

I set this up on 10.04.4 Desktop that I have had FOG running on for 3 years.

I copied my .iso's to the same dir I mounted them to via loopback.

**ls -lash /tftpboot/howtogeek/linux/ubuntu/12/32**
2.0K dr-xr-xr-x 1 root root 2.0K 2013-08-20 13:10 .
4.0K drwxrwxrwx 4 root root 4.0K 2013-11-20 14:25 ..
 512 -r--r--r-- 1 root root  134 2013-08-20 13:07 autorun.inf
2.0K dr-xr-xr-x 1 root root 2.0K 2013-08-20 13:10 boot
2.0K dr-xr-xr-x 1 root root 2.0K 2013-08-20 13:10 casper
2.0K dr-xr-xr-x 1 root root 2.0K 2013-08-20 13:10 .disk
2.0K dr-xr-xr-x 1 root root 2.0K 2013-08-20 13:10 dists
2.0K dr-xr-xr-x 1 root root 2.0K 2013-08-20 13:10 install
18K dr-xr-xr-x 1 root root  18K 2013-08-20 13:10 isolinux
4.0K -r--r--r-- 1 root root 3.7K 2013-08-20 13:10 md5sum.txt
2.0K dr-xr-xr-x 1 root root 2.0K 2013-08-20 13:10 pics
2.0K dr-xr-xr-x 1 root root 2.0K 2013-08-20 13:10 pool
2.0K dr-xr-xr-x 1 root root 2.0K 2013-08-20 13:10 preseed
512 -r--r--r-- 1 root root  233 2013-08-20 13:10 README.diskdefines
0 lr-xr-xr-x 1 root root    1 2013-08-20 13:10 ubuntu -> .
2.4M -r--r--r-- 1 root root 2.4M 2013-04-19 11:25 wubi.exe



I set up 3 PXE boot menu items identically:
Ubuntu 12.04.3 64
Ubuntu 12.04.3 32
Peppermint 4

The Ubuntu 64 entry does nothing from PXE menu. (hit enter on the entry and the menu flickers and you can continue to navigate menu, but nothing happens)

The Ubuntu 32 loads a splash and then times out to a BusyBox prompt "(initramfs) unable to find a live file system on the network"

The Peppermint 4 entry loads and boots perfectly.

**PXE MENU**
LABEL Ubuntu 64 12.04.3
KERNEL howtogeek/linux/ubuntu/12/64/casper/vmlinuz
APPEND root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.89.49:/tftpboot/howtogeek/linux/ubuntu/12/64 initrd=howtogeek/linux/ubuntu/12/64/casper/initrd.lz quiet splash --
LABEL Ubuntu 32 12.04.3
MENU DEFAULT
KERNEL howtogeek/linux/ubuntu/12/32/casper/vmlinuz
APPEND root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.89.49:/tftpboot/howtogeek/linux/ubuntu/12/32 initrd=howtogeek/linux/ubuntu/12/32/casper/initrd.lz quiet splash --
LABEL Peppermint 4
KERNEL howtogeek/linux/peppermint/casper/vmlinuz
APPEND root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.89.49:/tftpboot/howtogeek/linux/peppermint initrd=howtogeek/linux/peppermint/casper/initrd.lz quiet splash --


**FSTAB**
/tftpboot/howtogeek/linux/ubuntu/12/64/ubuntu-12.04.3-desktop-amd64.iso /tftpboot/howtogeek/linux/ubuntu/12/64 udf,iso9660 user,loop 0 0
/tftpboot/howtogeek/linux/ubuntu/12/32/ubuntu-12.04.3-desktop-i386.iso /tftpboot/howtogeek/linux/ubuntu/12/32 udf,iso9660 user,loop 0 0
/tftpboot/howtogeek/linux/peppermint/pm32.iso /tftpboot/howtogeek/linux/peppermint udf,iso9660 user,loop 0 0

**EXPORTS**
/tftpboot/howtogeek/linux/ubuntu/12/64/ *(ro,sync,no_wdelay,insecure_locks,no_root_squash,insecure)
/tftpboot/howtogeek/linux/ubuntu/12/32/ *(ro,sync,no_wdelay,insecure_locks,no_root_squash,insecure)
/tftpboot/howtogeek/linux/peppermint/ *(ro,sync,no_wdelay,insecure_locks,no_root_squash,insecure)


I am a n00ber so don't take it easy on me, any help would be appreciated.

---

