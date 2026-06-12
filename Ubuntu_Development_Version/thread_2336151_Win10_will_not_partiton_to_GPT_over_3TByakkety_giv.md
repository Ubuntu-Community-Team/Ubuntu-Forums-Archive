---
title: "Win10 will not partiton to GPT over 3TB/yakkety gives error with side by side install"
date: 2016-09-05
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-09-05
Just downloaded and installed new Windows 10. It will not install in UEFI mode and will not allow for GPT in the installer (as previous versions did allow). When trying to install yakkety it will recognize Windows 10 but  will give msdos partion table error and will not install on side by side.

'exceeds the msdos partiton table imposed maximum'


edit:

Trying 'something else' with free space locks and freezes the installer. 
Regards..

---

### Post by sudodus on 2016-09-05
What happens if you use gparted and create a GUID partition table, GPT, and the partitions you want *before* booting into the Windows 10 installer? That should give Windows a hint what to use ;-)

But there might be a problem. I remember that *oldfred* has written that Windows uses the MSDOS partition table in BIOS mode and GPT in UEFI mode. You need GPT to use the whole 3 TB drive, so if you want Windows, you could try if it works in UEFI mode. (I can imagine that you don't want UEFI mode, but there might be no choice unless you squeeze Windows into a virtual machine or put Windows on a separate disk.)

---

### Post by ventrical on 2016-09-05
> **sudodus said:**
> What happens if you use gparted and create a GUID partition table, GPT, and the partitions you want *before* booting into the Windows 10 installer? That should give Windows a hint what to use ;-)

But there might be a problem. I remember that *oldfred* has written that Windows uses the MSDOS partition table in BIOS mode and GPT in UEFI mode. You need GPT to use the whole 3 TB drive, so if you want Windows, you could try if it works in UEFI mode. (I can imagine that you don't want UEFI mode, but there might be no choice unless you squeeze Windows into a virtual machine or put Windows on a separate disk.)

The drive was originally created with a GPT and then all data wiped.  I downloaded the new free Windows 10 to see if they had fixed the problem with booting with Ubuntu. When you first boot up the Windows install disk there is an option to 'extend' the partition  to use the whole 3TB. This used to work by creating a GPT. Now it just  creates 1 500MB reserved partition and 1 2TB partiton with a 780GB of unused space.  So my reason for reporting all this is that there is something broke with the windows installer but I'll  try as you suggested. I will also try another ISO   of ubuntu non yakkety.

Regards..

---

### Post by sudodus on 2016-09-05
> **ventrical said:**
> ... I downloaded the new [COLOR="#cc0000"]free[/COLOR] Windows 10 to see if they had fixed the problem with booting with Ubuntu. ...

Maybe this is a crippled version.

---

### Post by ventrical on 2016-09-06
> **sudodus said:**
> Maybe this is a crippled version.

I completely wiped the drive previously so this probably wiped the GPT...hmmm but maybe your right . I never thought of 'crippled' version. I was assuming there was a partnership with MS and ubuntu.

---

### Post by oldfred on 2016-09-06
It was my understanding that how you boot Windows UEFI or BIOS is then how it installs. Just like Ubuntu.

But some drive mfg. have used a proprietary MBR formatting to enable XP to boot on drives over the MBR limit of 2TB. It actually uses either 2048 or 4096 logical sectoring. Normally with gpt you have 512 logical sectors but 4096 physical sectors for new larger drives.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

---

### Post by ventrical on 2016-09-06
@oldfred..

Windows 8 and earlier  Windows 10 releases gave the option to 'extend' the partions just before the install process. So there was the Windows Installer  showing partitons.  You could delete all the partitons, then create or (add) a partiton. This would give you the 500mb, 2GB and 1TB of unused space. Then click 'extend' and you have the one big partiton which you could install Windows and Ubuntu onto.  Now the 'extend' options gives an error and I even wiped the drive previously.

  Thank you for your reply. The (new) windows 10 iso gives 2 options . home and pro. So i have been using 'home' version. maybe I will try pro install and see if the 'extend' options works.

regards..

---

### Post by oldfred on 2016-09-06
I also saw that Windows 10 now wants another recovery  partition after the main install. And as system grows, it may want to auto resize it.
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)

And they also now want that recovery on BIOS/MBR systems.
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-biosmbr-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-biosmbr-based-hard-drive-partitions)

---

### Post by ventrical on 2016-09-07
> **oldfred said:**
> I also saw that Windows 10 now wants another recovery  partition after the main install. And as system grows, it may want to auto resize it.
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)

And they also now want that recovery on BIOS/MBR systems.
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-biosmbr-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-biosmbr-based-hard-drive-partitions)

Thank you. The Windows 10 Pro install did the same thing . It would not extend. These problems with the partitions and the way that Microsoft is installing them has not progressed in the least to the benefit of ease of installation for Ubuntu. It has gone from bad to worse IMO.

Regards..

---

### Post by ventrical on 2016-09-07
I used gparted, created GPT and got this message:

"Windows cannot be installed to this disk. The selected disk is of the GPT partition style."

-more-to-come-

So far, the latest build of Windows 10 seems to be designed to be anti-linux/ubuntu. I used to be able to install Windows 8/10 in BIOS mode and also ubuntu on resized without using gparted. I am trying different method.  My point here being .. if the new build is installing is such a way then how will ubuntu be able to be installed. I even tried stable trusty and it does not even recognized the windows 10 bootloader but yakkety does recognize Windows 10.

-more-

Obviously there is also something wrong with the way I prepped the hdd as gparted will not resize ntfs filesystem.



edit:

So far .. no success. It has been a  tremendous amount of downtime. This statement may sound a little paranoid but it appears that MS has found a way to keep ubuntu off the hard drive. Sort of .. if you install windows 10 on it, they own the hard drive. I do have another machine with a working install that is installed in BIOS mode and is below 2TB so I am going to try a yakkety install on that macjine. I will also use the 3TB drive, install trusty or yakkety on it and then try to install the new Win 10 build in a virtual box.


-more-

yakkety now only gives me the option to erase and install ubuntu (on BIOS install of 150GB hdd)


Regards..

---

### Post by ventrical on 2016-09-07
Works just fine on Virual Box.

---

