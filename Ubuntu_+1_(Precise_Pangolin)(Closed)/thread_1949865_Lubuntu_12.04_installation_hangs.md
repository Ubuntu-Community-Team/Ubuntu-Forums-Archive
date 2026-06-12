---
title: "Lubuntu 12.04 installation hangs"
date: 2012-03-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by SmashedPotato on 2012-03-31
I'm trying to install Lubuntu 12.04 beta 2 on my BenQ Joybook U121 with the infamous GMA500 graphics driver. When the installer gets up to the point where I enter details about my username and computer name and then I press next, the installer window freezes indefinitely without going to the next screen. 

Since I'm using a netbook I'm installing from USB. I've used Unetbootin and the LiLi USB Creator with neither working. I already have a Windows 7 partition and I'm installing over an old Ubuntu partition. I also have to use the 'sudo service lightdm restart' command to get the graphics working.

Can someone help me work out what's wrong? Thanks

---

### Post by marinara on 2012-03-31
yeah i had lockups with unetbootin too. i thought it was just me.

try formatting your ubuntu partition
also, there is a menu when you first boot.  the unetbootin menu.  usually you have several options to install lubuntu, try all of them.

---

### Post by oldos2er on 2012-03-31
Thread moved to Ubuntu +1 (Precise Pangolin).

---

### Post by nm_geo on 2012-03-31
The isos are all hybrids now (meaning) you can install them on a USB with the dd method and commands, but you must be very careful.  Here are the steps I use to place the iso on a Flash Drive.

  Create bootable USB PP as of 11/25/2011 and all newer versions.

One partition only...format fat32 (raw) a new one out of the box should work.

I used Gparted to reformat my USB to make sure it was clean...

In terminal ```
cd isos/lu
``` (that's where I keep my zsync copies of lubuntu precise)

Then 

```
sudo dd if=precise-desktop-i386.iso of=/dev/sdb  
```Your flash drive might not be sdb be sure you make sbx correct.  The dd command will write that iso to where ever you direct it. You will also be surprised by time it takes depending on the speed of USB bus and the write speed of your Flash drive. 

You can not create a persistent iso with this method. So if you
want a persistent Flash Drive use Startup Disk Creater. It works well also.

  
> **SmashedPotato said:**
> I'm trying to install Lubuntu 12.04 Beta 2 on my BenQ Joybook U121 with the infamous GMA500 graphics driver. When the installer gets up to the point where I enter details about my username and computer name and then I press next, the installer window freezes indefinitely without going to the next screen. 

Since I'm using a netbook I'm installing from USB. I've used Unetbootin and the LiLi USB Creator with neither working. I already have a Windows 7 partition and I'm installing over an old Ubuntu partition. I also have to use the 'sudo service lightdm restart' command to get the graphics working.

Can someone help me work out what's wrong? Thanks

---

### Post by SmashedPotato on 2012-03-31
Thanks for the replies.

Before I received the advice though, I let the installer run even though it seemed like it was frozen. I installed boot-repair in the meantime and when I restarted, it seems Lubuntu had installed but had not been configured i.e. no users added, no locale, empty hosts file. So I went through a few hoops setting that up through fiddling with the installation with the LiveUSB and  my installation is working fine now.

---

### Post by nm_geo on 2012-03-31
> **SmashedPotato said:**
> Thanks for the replies.

Before I received the advice though, I let the installer run even though it seemed like it was frozen. I installed boot-repair in the meantime and when I restarted, it seems Lubuntu had installed but had not been configured i.e. no users added, no locale, empty hosts file. So I went through a few hoops setting that up through fiddling with the installation with the LiveUSB and  my installation is working fine now.

May I recommend making a live USB with the dd method. You might need it later and I think you will be happy with the out come. Just make it and run it trying Lubuntu. No need to re-install if your is working.

---

### Post by wildneuro on 2012-04-06
> **SmashedPotato said:**
> I'm trying to install Lubuntu 12.04 beta 2 on my BenQ Joybook U121 with the infamous GMA500 graphics driver. When the installer gets up to the point where I enter details about my username and computer name and then I press next, the installer window freezes indefinitely without going to the next screen. 

Since I'm using a netbook I'm installing from USB. I've used Unetbootin and the LiLi USB Creator with neither working. I already have a Windows 7 partition and I'm installing over an old Ubuntu partition. I also have to use the 'sudo service lightdm restart' command to get the graphics working.

Can someone help me work out what's wrong? Thanks

Hi all.

Is anyone SOLVE this? I have Asus Eee PC 1201HA, and also, when I try to install 12.04 and enter my username and pass, it hang on process:

ubiquity (it takes 100% CPU). Help! :)

---

### Post by wildneuro on 2012-04-06
> **wildneuro said:**
> Hi all.

Is anyone SOLVE this? I have Asus Eee PC 1201HA, and also, when I try to install 12.04 and enter my username and pass, it hang on process:

ubiquity (it takes 100% CPU). Help! :)

SOLVED

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/909179](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/909179)

It hang because try to shot you with yours web cams. Just need to delete python app:

**> sudo rm /usr/lib/ubiquity/plugins/ubi-webcam.py**

Its work!

---

