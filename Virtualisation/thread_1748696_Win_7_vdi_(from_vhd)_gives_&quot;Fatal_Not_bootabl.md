---
title: "Win 7 vdi (from vhd) gives &quot;Fatal: Not bootable medium..&quot;"
date: 2011-05-03
forum: Virtualisation
---

### Post by rwigle on 2011-05-03
I see a number of similar threads, but they all concern trying to create a virtual machine from a CD or ISO image. 

I have a running Win 7 install, and created a virtual hard drive *.vhd using Disk2vhd. Then I converted it to vdi format using virtualboxmanage.

I then created a virtual machine with this vdi file as the hard disk.
When I try to boot the virtual machine in virtualbox ose (under Ubuntu Lucid 64) I get the above-mentioned error. I have set the virtual machine I have to boot first from the hard disk and unchecked floppies and CD drive. 

The machine is a Toshiba Tecra R700 with Windows 7 (64) and Lucid (64) both installed.

Any suggestions?

---

### Post by rwigle on 2011-05-05
I am wondering if this is related to my dual boot configuration. I have a Windows 7, Vista Loader and Ubuntu all on the hard drive (see attached boot-info summary) and I have seen some reference to grub being on the wrong partition.

---

### Post by rwigle on 2011-05-17
It seems that the problem was with the virtual machines I created under Windows 7 on the Tecra R-700. I copied a couple other Windows vdi/vhd files from other computers and they seem to run fine under virtualbox.

After several tries, I have given up on creating a virtual hard disk (vhd)  with the disk2vhd utility on the Tecra R-700.

The specifics are:

Tecra R-700 dual booting Windows 7 (64) and Ubuntu Lucid.

To repeat, I think the problem was creating vhd files of the Windows 7 installation on the Tecra R-700.

The solution was to use virtual machines created on other (real) machines. These seem to work fine on the Tecra R-700 under virtualbox.

---

