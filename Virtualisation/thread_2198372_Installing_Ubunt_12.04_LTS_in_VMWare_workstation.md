---
title: "Installing Ubunt 12.04 LTS in VMWare workstation"
date: 2014-01-08
forum: Virtualisation
---

### Post by thekeshav on 2014-01-08
Hello ! 
Currently I am using windows 8 dual boot with BT 5 R3. I wanted to install Ubuntu 12.04 LTS (64-bit) in VMware Workstation 10, installed it and tried to install Ubuntu. I mounted the Ubuntu .ISO file and proceed to next. When I start "Power virtual machine" it is showing the following the image 
:                                                                                                     [ATTACH=CONFIG]249322[/ATTACH]
I tried again by increasing memory size to 2.00GB and No. of processors 2, but it wasn't worked. Please help me to get solution for this . . . . . Thanks in Advance. :)

---

### Post by tomearp on 2014-01-08
The fact that the VM has proceeded to try and boot from the network suggests one of the following:

The CD-ROM drive is not "Connected." With the VM turned off go into the settings and make sure Connect at power on is selected. Also double-check that the path and filename are pointing to an ISO that exists.

The ISO file is invalid. See [this page for ISO md5 hashes]("https://help.ubuntu.com/community/UbuntuHashes") and [this one for information on how to generate the md5 hash of your iso in various operating systems]("https://help.ubuntu.com/community/HowToMD5SUM").

The boot order of the VM is incorrect. When the VM first powers on there is a screen that briefly appears with some options, hit Esc to get to a one-time boot menu and try manually selecting the CD drive. If it carries on trying to network boot then it's likely one of the issues above.

---

### Post by thekeshav on 2014-01-10
Thanks for your reply :) Actually what I did is I have downloaded Ubuntu in a .zip file, I extracted those. After, all selecting making them as a .ISO file in Nero Image burner. Is that process of ISO burning correct and that file to I am mounting. Or I need to do some thing else to install successfully.

---

### Post by nilla78ro on 2014-01-10
try downloading the iso from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) or server

---

