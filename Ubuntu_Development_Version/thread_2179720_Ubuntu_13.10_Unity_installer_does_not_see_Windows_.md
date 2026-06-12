---
title: "Ubuntu 13.10 Unity installer does not see Windows 8."
date: 2013-10-09
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2013-10-09
Here are 2 screenshots, one of disk management the other with a partition manager.  As  you can see windows 8 is there, also there is 160 gb of unallocated space to install Ubuntu.  However when I attempt to install Ubuntu fro live usb, with secure boot efi, I get the following message:

"This computer currently has no detected operating system what would you like to do."



[ATTACH=CONFIG]246842[/ATTACH][ATTACH=CONFIG]246843[/ATTACH]

Any takers?

Henry

---

### Post by Chelidze on 2013-10-09
Did you try running a non beta version of ubuntu ??? if yes does it shows you that you are running a different os ??
Honestly I think it does not shows you the partition because of [COLOR=#000000]Uefi Secure Boot. 
[/COLOR]i might be wrong because I am not an expert here plus I have never installed ubuntu on Uefi system so I do not know but I think you should look into it

---

### Post by Hewjr100 on 2013-10-09
As far as uefi and secure boot goes I have installed ubuntu 13.10 on this system, but overwriting windows 8.  So ubuntu 13.10 does install with secure boot, but apparently not when dual booting with windows 8.  Having said that I will try with 13.04 and report back.

Henry

---

### Post by Chelidze on 2013-10-09
> **Hewjr100 said:**
> As far as uefi and secure boot goes I have installed ubuntu 13.10 on this system, but overwriting windows 8.  So ubuntu 13.10 does install with secure boot, but apparently not when dual booting with windows 8.  Having said that I will try with 13.04 and report back.

Henry

 If you have free space allocated already why not manually set the partitions ??

Some information I found 

[http://askubuntu.com/questions/323249/windows-8-os-not-detected-12-04-install-new-computer-build-uefi-secure-boot-e](http://askubuntu.com/questions/323249/windows-8-os-not-detected-12-04-install-new-computer-build-uefi-secure-boot-e)

[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

[http://youtu.be/PK7gWIkAY7s?t=2m5s](http://youtu.be/PK7gWIkAY7s?t=2m5s)

---

### Post by Hewjr100 on 2013-10-09
You talkin' to me (looking in the mirror). I can't manually boil water:D  But just for the heck of it I'll try.

Henry

---

### Post by Hewjr100 on 2013-10-09
Oh btw I tried 13.04 and only got  bash prompt after booting live usb.

Henry

---

### Post by Chelidze on 2013-10-09
> **Hewjr100 said:**
> You talkin' to me (looking in the mirror). I can't manually boil water:D  But just for the heck of it I'll try.

Henry

You will do great. 
Did stable ubuntu showed any promise ??

---

### Post by grahammechanical on 2013-10-10
I have never installed Ubuntu on a Windows 8 machine. I know that Ubuntu will install with secure boot enabled since 12.10 and can handle UEFI. We need fast boot turned off. 
The second image shows that the disk is GPT. And that may have something to do with it.

This is not an issue specifically related to Ubuntu 13.10. The little I have learned about this has come from reading the many threads about installing Ubuntu on Windows 8 machines that there are scattered throughout this forum.

Regards.

---

### Post by grahammechanical on 2013-10-10
Sorry double post for some reason. Wonky fingers no doubt.

Regards.

---

### Post by Hewjr100 on 2013-10-10
That is my problem, as far as  know there is no way to custom instal window oem image.  Today's daily image (10-10-13) does show windows partitions and free space, but  am afriad if I manually partition, then it will boot without windows 8 option in grub.  Also how should I partion the 160 gb free space and not have an free space left over.

Henry

---

### Post by Chelidze on 2013-10-10
> **Hewjr100 said:**
> That is my problem, as far as  know there is no way to custom instal window oem image.  Today's daily image (10-10-13) does show windows partitions and free space, but  am afriad if I manually partition, then it will boot without windows 8 option in grub.  Also how should I partion the 160 gb free space and not have an free space left over.

Henry


take a look at this video

[http://youtu.be/0W7XYAB4cLc?t=9m9s](http://youtu.be/0W7XYAB4cLc?t=9m9s)

you can look at this as well

[http://youtu.be/qBCHsgry2RQ](http://youtu.be/qBCHsgry2RQ)

---

