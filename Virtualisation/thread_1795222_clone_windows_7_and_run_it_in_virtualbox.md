---
title: "clone windows 7 and run it in virtualbox"
date: 2011-07-02
forum: Virtualisation
---

### Post by FrAggLE-Rock on 2011-07-02
hi 

i have a win 7 preinstalled und ubuntu 11.04

i like to clone the windows 7 partition and run it in virtualbox,
so i don't have to restart my laptop every time i need windows.

is this possible?

thx

---

### Post by Paddy Landau on 2011-07-02
I've never tried it, but I believe it is possible. Whether it will work is another question, because Windows will need slightly different drivers to access the peripheral devices.

You also need sufficient RAM to be able to run Windows at the same time as another OS, because Windows requires a lot of RAM.

I strongly recommend that you uninstall the default VirtualBox (VB) and install the latest version from the [VirtualBox downloads]("http://www.virtualbox.org/wiki/Linux_Downloads") (scroll down to Debian-based Linux distributions); then install the VirtualBox Extension Pack (available from the [main VB downloads page]("http://www.virtualbox.org/wiki/Downloads")).

Here is how I would do it:


[LIST=1]
[*]Start VB. Create a virtual machine (VM) with a virtual disk *slightly larger than* as your existing Windows partition.
[*]Download the ISO for [CloneZilla]("http://www.clonezilla.org/").
[*]Start your new VM; as it starts, it shows an Oracle VB logo. Immediately press F12 so that it presents a text menu.
[*]From the VB menu (not from the text menu), select Devices > CD/DVD Devices > Choose a virtual CD/DVD disk file > select your CloneZilla ISO.
[*]From the text menu, select c to choose the CD-ROM.
[*]CloneZilla will load into the VM.
[*]Clone your real Windows partition to your virtual disk.
[LIST]
[*]Ensure that you clone the right way around, otherwise you will trash your real Windows partition.
[/LIST]
 
[*]I believe that you will have to rebuild the MBR (the boot record) of the VM, for which you can use EasyBCD, otherwise the VM will try to boot (unsuccessfully) into the real Windows.
[/LIST]

As I say, I have never tried this, so I cannot guarantee that it would work. You may find it easier to install Windows into your VM and copy your settings across.

If it does work, you can install the Guest Additions (Devices > Install Guest Additions) into your VM.

---

