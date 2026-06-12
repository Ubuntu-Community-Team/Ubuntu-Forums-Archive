---
title: "Trusty Make Startup Disk application"
date: 2014-04-08
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2014-04-08
I tried to used Trusty Make Startup Disk application  on both 32 bit and 64 bit installations. Both cases would not enable the option "Stored in reserved extra space"

I know the hardware works because I used UNetbootin to create what I wanted!:KS

Maybe I'm missing something with the default app ????

Should the application also create startup DVDs?

---

### Post by ventrical on 2014-04-08
> **pfeiffep said:**
> I tried to used Trusty Make Startup Disk application  on both 32 bit and 64 bit installations. Both cases would not enable the option "Stored in reserved extra space"

I know the hardware works because I used UNetbootin to create what I wanted!:KS

Maybe I'm missing something with the default app ????

Should the application also create startup DVDs?

 I use Brasero to make dvd isos.

 There has been some bugs with SDC during this cycle (and previous).

---

### Post by ventrical on 2014-04-08
This here:

[http://ubuntuforums.org/showthread.php?t=2213752&highlight=Startup+Disk+Creator](http://ubuntuforums.org/showthread.php?t=2213752&highlight=Startup+Disk+Creator)

---

### Post by pfeiffep on 2014-04-08
+1 > **ventrical said:**
> I use Brasero to make dvd isos.

 There has been some bugs with SDC during this cycle (and previous).

I also use Brasero usually - I was hoping to have one tool for both type of startups.

---

### Post by ventrical on 2014-04-08
> **pfeiffep said:**
> +1 

I also use Brasero usually - I was hoping to have one tool for both type of startups.

I have 8 boxes and 3 lappys (4 boxes on a KVM.)  I use Maveric (10.10)to do all my SDC USB drives.  The cycles afterwards have been hit and miss with SDC  but then thats just what I do.

---

### Post by pfeiffep on 2014-04-10
Not certain what happened before:oops: but the issue seems to be resolved now.
Steps taken:[INDENT]1- sudo apt-getupdate, upgrade, autoclean, autoremove

2-pfeiffep@Pete-dell:~$ uname -a
Linux Pete-dell3.13.0-22-generic #44-Ubuntu SMP Wed Apr 2 20:04:41 UTC 2014 i686i686 i686 GNU/Linux

pfeiffep@Pete-dell:~$lsb_release -a
No LSB modules areavailable.
DistributorID:    Ubuntu
Description:    UbuntuTrusty Tahr (development branch)
Release:    14.04
Codename:    trusty

3- download 32bitiso{10-Apr-2014 07:56  949M  Desktop image for PC (Intel x86)computers (standard download) }

4-insure usb portand flash drive are functional using gparted – format fat 32results 4.0GB free

5- launch StartupDisk Creator  - which worked as expected[/INDENT]

---

### Post by mc4man on 2014-04-10
As far as Sdc & usb - if you format the drive before attempting to create in sdc it will work fine. Currently sdc cannot do the format - 
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1294877](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1294877)

---

### Post by pfeiffep on 2014-04-10
+1> **mc4man said:**
> As far as Sdc & usb - if you format the drive before attempting to create in sdc it will work fine. Currently sdc cannot do the format - 
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1294877](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1294877)Should I be able to make a DVD using Startup Disk Creator?  
I use brassero now with no problems

---

### Post by mc4man on 2014-04-10
> **pfeiffep said:**
>  Should I be able to make a DVD using Startup Disk Creator?  

No, it's for usb & claims to do sd cards
(- the actual name of the source/package(s) is 'usb-creator/usb-creator-gtk', ect.

---

