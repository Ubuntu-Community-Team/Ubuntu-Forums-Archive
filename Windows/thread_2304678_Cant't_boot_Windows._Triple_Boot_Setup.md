---
title: "Cant't boot Windows. Triple Boot Setup"
date: 2015-11-28
forum: Windows
---

### Post by Michael_Chacko on 2015-11-28
My brother has an old MacBook 5,3 from 2008/9. It ran OSX with bootcamp windows.

He wanted me to install linux, and I did! I got rEFIt so I could choose which OS I could boot into. 

When partitioning the the drive for linux using gparted, it said it would move the windows partition to the left and then shrink the volume. After doing that, I installed linux.
Everything looked liked it was fine, until I tried to boot windows. I get the following error message in windows:[COLOR=#000000]**the boot selection failed because a required device is inaccessible**
[/COLOR]Great. I read up on the issue and saw that it could be fixed with a repair CD. The thing is the CD drive doesnt work, so it will have to be a bootable usb.

 I made a repair CD from another windows machine and copied the files to a bootable USB. When running it through rEFIt, it shows the exact same error message, as if the repair usb never ran...

Not sure what I should do. Im thinking the MBR tables may be messed up, but I don't have access to the original Windows cd or the bootcamp cd (If there is one)


EDIT: It's worth noting that all my windows files are still accessible from OSX and linux. So my windows partition is not deleted.

---

### Post by Bucky Ball on 2015-11-28
*Thread moved to **Windows**.*

I can't help but others should be able to. The bad news: You should only resize Windows partitions with Windows software. Using Gparted or other Linux tools to resize the Win OS partition can get you into trouble. As I think you may have discovered.

---

### Post by Michael_Chacko on 2015-11-28
Yes, I had tried with Windows previously, but the disk mgmt tool kept crashing.

---

### Post by yancek on 2015-11-29
> When partitioning the the drive for linux using gparted, it said it  would move the windows partition to the left and then shrink the volume

High risk option particularly if you have no backup/repair medium.  When you move the files to the left on that partition, you moved the location of the boot files.

What repair CD are you referring to?  If it is meant to be a bootable medium, I doubt if simply copying it to a flash drive will work and I would expect the result you got.  Generally some specific software is used to create a 'bootable' flash drive rather than just copying data.

So is the problem now that you can boot OSX and Linux but not windows?  You might try getting the boot repair software from the link below and downloading it and selecting the option to create bootinfo summary.  You can post the output here and it will provide a lot of detailed information on drives/partitions and boot files and someone should be able to help.

[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Bucky Ball on 2015-11-29
@yancek: You forgot the [Boot Repair link]("https://help.ubuntu.com/community/Boot-Repair"). :)

---

