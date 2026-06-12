---
title: "cannot install 16.04 from live CD or USB stick"
date: 2016-06-05
forum: Ubuntu Studio
---

### Post by raymondvillain on 2016-06-05
Using Ubuntu 14.04 with no problems.  Downloaded iso image of Ubuntu Studio 16.04, intending to install it on a new 120 Gbyte ssd.

Can't get past the part where one specifies the keyboard language, freezes up.  Mouse fails to respond, nothing to do but do a hard boot.

This happens if I use a DVD or a USB stick.

Any ideas?

I have an AMD machine, 16 Gbytes of RAM, radeon graphics.

---

### Post by sudodus on 2016-06-06
Did you check that the md5sum matches (to make sure the download was successful)?

What tools did you use to create the USB boot drive, and the DVD boot disk?

Are you running in BIOS mode or UEFI mode?

Are you intending to dual boot with Windows or some other operating system?

Please specify your computer,

- Brand name and model
- CPU
- RAM (known: 16 GiB)
- graphics chip/card (more details about the model, not only 'radeon')
- wifi chip/card

-o-

The problem might be solved with the first point release 16.04.1 LTS late in July or early August. Anyway, I suggest that you continue with 14.04 LTS, and try 16.04.x LTS again later.

---

### Post by raymondvillain on 2016-06-06
Thanks for the suggestion.

How do I find out if running in BIOS or UEFI?

Machine is a "build your own", Gigabyte motherboard, AMD-FX-6300 Six core processor
graphics card:  AMD RADEON HD 6570
wifi is a "Panda" wifi on a USB stick, using FIOS router in home, should I try installing with a cat5 cable to connect to the router instead of wifi?

I did check the md5sum and SHA256sum on both the DVD and the USB stick, both methods gave agreement.

Made the USB stick with unetbootin

---

### Post by sudodus on 2016-06-06
When you run linux, for example Ubuntu Studio 14.04 LTS or any live session (booted from USB), check with the following command line (copy and paste)

```
test -d /sys/firmware/efi && echo efi || echo bios
```

AMD is not providing proprietary drivers for 16.04, but instead they have helped making the free built-in linux driver better. I do not use AMD/ATI/Radeon graphics, but many people at our Ubuntu Forums do. I hope you can get good advice about your card by someone who knows. (Their support is often good for new cards, but not so good for old cards).

I don't know about your wifi stick, it might not be recognized. It is a ***good idea to connect via wired internet*** (ethernet with your CAT5 cable) during the installation. This might solve your problem.

If you get this far, the md5sum is good, and you have used Unetbootin, I think the pendrive is good.

---

### Post by raymondvillain on 2016-06-06
Many thanks, will try wired connection to router:

Output of the suggested command:

> user@COMPUTER:~$ sudo test -d /sys/firmware/efi && echo efi || echo bios
[sudo] password for user: 
bios
user@COMPUTER:~$ 

Is bios or UEFI better for Ubuntu studio?  Guess I have to figure out how to change it from BIOS to UEFI.

Thanks again for your suggestions.

---

### Post by sudodus on 2016-06-06
Once linux is running, it makes no difference. The main reason to use UEFI is that computers nowadays come installed with Windows in UEFI mode. And if you want to dual boot, it is easier to install linux in the same mode. Otherwise you have to change boot mode every time you want to switch between linux and Windows.

So I suggest that you continue using BIOS mode.

If you want more than two partitions, you should prepare for it now, before installing. You can use ***gparted*** in a live session booted from another drive (not the target drive you want to install into).

---

### Post by oldfred on 2016-06-06
How you boot install media UEFI or BIOS is then how it installs. But then you have to have system set to boot in that same mode.
There actually are three boot modes you can install in - UEFI with secure boot, standard UEFI, and BIOS/CSM/Legacy.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Whether you install in UEFI or BIOS best to update UEFI/BIOS on motherboard.

Many Gigabyte boards have IOMMU settings in UEFI, that needs changing & then a boot parameter for iommu

 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370) 

There are some slight advantages to UEFI, but it is newer. But always best to boot Ubuntu in same boot mode as you have installed Windows if you have Windows. And Windows installs in the same boot mode as you boot install media.

If only Ubuntu use gpt partitioning whether UEFI or BIOS. Ubuntu can boot from gpt with BIOS. Windows only boots from gpt partitioned drives with UEFI.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 
    
I have been using gpt since about Ubuntu 10.10 with XP on MBR drive and Ubuntu on gpt drive. I started formatting all new drives or totally reformatted drives to gpt. Soon after I realized drives may eventually go into new UEFI system and started adding both the ESP - efi system partition and bios_grub partition so drive could be configured either way without totally repartitioning and reformatting.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)

---

### Post by raymondvillain on 2016-06-07
Thanks again, sudodus, used ethernet cable to connect to internet, installation went pretty smooth.  Couple of minor glitches.  So I'll mark this solved and encourage others to use a wired ethernet connection when installing Ubuntu Studio.

---

