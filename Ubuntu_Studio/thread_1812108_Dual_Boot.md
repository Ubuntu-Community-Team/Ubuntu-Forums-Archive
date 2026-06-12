---
title: "Dual Boot"
date: 2011-07-25
forum: Ubuntu Studio
---

### Post by platyiwings on 2011-07-25
Hi there,

I've been using mac OSX10.4 and Ubuntu on Intel imac with dual boot using rEFIt boot chooser.

What I am thinking is that I delete OSX10.4 from my machine and replace with ubuntu studio.  Then I would like to set up dual boot ubuntu and ubuntu studio.  

My worries are:

Boot loader for choosing OS...(Grub boot loader to be installed when the Ubuntu Studio is installed?)

Is it possible to simply install Ubuntu Studio to OSX 10.4.11 partitioned area?  

Kindly regards,

---

### Post by sgx on 2011-07-25
I would first install on an external hard-drive, or on a usbstick.
If it works, you can do a full install, but there won't be much advantage having two ubuntus, unless you are a habitual tester.
(I fall into that group, new distros are great fun to explore!)
Cheers

---

### Post by nd456 on 2011-07-26
There is 0% reason to have ubuntu and ubuntu studio, ubuntu studio is ubutnu with some audio programs pre-installed.

---

### Post by platyiwings on 2011-07-26
> **nd456 said:**
> There is 0% reason to have ubuntu and ubuntu studio, ubuntu studio is ubutnu with some audio programs pre-installed.

Thank you very much for the replaying. I understand what kind of Ubuntu Studio is.

thank you very  much

---

### Post by platyiwings on 2011-07-26
> **sgx said:**
> I would first install on an external hard-drive, or on a usbstick.
If it works, you can do a full install, but there won't be much advantage having two ubuntus, unless you are a habitual tester.
(I fall into that group, new distros are great fun to explore!)
Cheers


Do I need to ask the mod changing the thread place,if I don't install Ubuntu- studio?  It doesn't matter if the Ubuntu and Ubuntu studio is basically same.

What I would like to do:

I would like to replace Mac OSX 10.4.11 with Ubuntu(English language setting if possible considering keyboard etc.) on internal HDD for learning and testing purposes. I should keep current Ubuntu(Japanese Language setting) as it is since I installed useful software and lots of important data in there already. In addition this is only machine I have and I'm using day-to-day.


My worry is that how to install Grub boot loader.... I used it earlier days when I started Ubuntu...but I don't know why it appeared grub loader.. I delete and install many times...

I convinced that Ubuntu can be useful for future computer system. Then, I would like to go forward next step... learning and testing linux commands, Ubuntu itself and etc. 


Can you or anyone help me on how to dual boot settings for two Ubuntus....


Internal HDD I created is as follows:

OSX10.4.11
sda1  fat32 EFI 200MB
ada2  hfs+ 50GB


Ubuntu Linux
sda3   linux Swap 1.21GB
sda4   ext4  /    97.6GB


Memory 2GB


Kindly regards,

---

### Post by marseille on 2011-07-26
see Ubuntu Documentation:

Dual Boot MacOSX
[https://help.ubuntu.com/community/DualBoot/MacOSX](https://help.ubuntu.com/community/DualBoot/MacOSX)

Mactel Support Team AppleIntelInstallation
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by platyiwings on 2011-07-26
> **marseille said:**
> see Ubuntu Documentation:

Dual Boot MacOSX
[https://help.ubuntu.com/community/DualBoot/MacOSX](https://help.ubuntu.com/community/DualBoot/MacOSX)

Mactel Support Team AppleIntelInstallation
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)


Thank you very much for the linked sites.  I could successfully install Ubuntu to the OSX10.4.11 partitioned area.  I can use Grub boot loader for selecting previous Ubuntu installed different partitioned.  

The point is to be remained EFI partitioned area and install Ubuntu to HFS+ partitioned area.  I think Ubuntu Studio can be installed with same way.


1.) It takes 30 seconds... till the Grub boot loader appears...

   I tried bless--device /dev/disk01 --SetBoot  -legacy

Is there any way to cut off the time to come up GRUB boot loader menu?



2) I'm not familiar with GRUB yet.... I would like to change the default setting for booting.

Sda5 is set as default. I would like to change from sda5 to sda4.


3) We don't need two swap areas technically?


----------------
sda1 EFI

sda2 swap 1.3G

sda5 Linux 52GB*

sda3 swap 1.3G

sda4 Linux 105G


can you or anyone help me on this please.

Kindly Regards

---

### Post by platyiwings on 2011-07-26
> **platyiwings said:**
> Thank you very much for the linked sites.  I could successfully install Ubuntu to the OSX10.4.11 partitioned area.  I can use Grub boot loader for selecting previous Ubuntu installed different partitioned.  

The point is to be remained EFI partitioned area and install Ubuntu to HFS+ partitioned area.  I think Ubuntu Studio can be installed with same way.


1.) It takes 30 seconds... till the Grub boot loader appears...

   I tried bless--device /dev/disk01 --SetBoot  -legacy

Is there any way to cut off the time to come up GRUB boot loader menu?



2) I'm not familiar with GRUB yet.... I would like to change the default setting for booting.

Sda5 is set as default. I would like to change from sda5 to sda4.


3) We don't need two swap areas technically?


----------------
sda1 EFI

sda2 swap 1.3G

sda5 Linux 52GB*

sda3 swap 1.3G

sda4 Linux 105G


can you or anyone help me on this please.

Kindly Regards

> 
1.) It takes 30 seconds... till the Grub boot loader appears...

   I tried bless--device /dev/disk01 --SetBoot  -legacy

Is there any way to cut off the time to come up GRUB boot loader menu?
I could resolve the issues referring the above command and documentation on Ubuntu.  We should use that from OSX10.4.11 terminal window as documentation says.

> 2) I'm not familiar with GRUB yet.... I would like to change the default setting for booting. sda5 is set as default. I would like to change from sda5 to sda4.There is no longer exist grub boot loader menufile on the Ubuntu 11, from version 9?  and editing is more complicated. However, regarding the change of default of booting, we can get GUI editing tool software from Software Center.  

I found a Grub2 documentation for further references.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)


> 3) We don't need two swap areas technically?I'm not sure but it works so far without problem.

Thanks 
:)

---

### Post by platyiwings on 2011-07-27
> **nd456 said:**
> There is 0% reason to have ubuntu and ubuntu studio, ubuntu studio is ubutnu with some audio programs pre-installed.


Thank you very much for the replying message.  I confirmed that Ubuntu could produce better quality sound installing some programs.

thanx

:)

---

