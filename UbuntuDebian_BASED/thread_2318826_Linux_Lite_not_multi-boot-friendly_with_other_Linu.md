---
title: "Linux Lite not multi-boot-friendly with other Linux OS,  but..."
date: 2016-03-29
forum: Ubuntu/Debian BASED
---

### Post by slappedbyzsa on 2016-03-29
This past year or so I have been on an epic Linux tasting journey.  I have multi PCs and other portables,  all of which now have at least one version of Linux with Windows of one type or another.  My Desktops in general have 3 or 4 Linux systems with ancient XP. I'm loving the learning experience.

Over the last few days it has become obvious to me that the grub in Linux Lite is not compatible with the grub choice (grub2?) of many of my other Linux systems..  Most of them happily live side by side.  Install Linux Lite and it's obvious that it's grub,  which looks alot like something made for DOS (e.g. primitive)  had better be installed last.  If it is replaced by the other Linux system grubs,  Linux Lite will no longer be accessible,  even if I update the data to the newer grub in question.  I kind of like what I've seen in Linux Lite and would like to have a chance to trial it along with the other distros. Oh yes,  my version of LL is OS 2.8 32bit.

This had me wondering about the possibility of uninstalling the grub which is supplied with Linux Lite and choosing grub2 as it's replacement from the Synaptic center.  Unfortunately I think (it was a long night) that I tried that and the tactic failed.

I came up with a possible alternative.  What if... Only for the case of Linux Lite,  I installed it's grub on a different drive boot sector (such as sdb)  as my other systems are catalogued in the boot sector of sda)  Then I would assume that updating the grub stored in the main mbr would also cause it to find the information stored in the grub installed by Linux Lite on my other drive. Or do I know what I am talking about?  I am clearly not an expert in grubology or Linux,  but it seems like a possibility.

I'd appreciate the knowledgeable feedback of someone who knows a bit more.  I am basicly a newbie who has acquired a boatload of experience rather rapidly over the past year.

Thanks for your attention.

---

### Post by oldfred on 2016-03-29
Moved to otherOS sub-forum, not Ubuntu flavor.

Do not know Linux Lite. Does it use grub2 or grub-legacy?

 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by grahammechanical on 2016-03-29
According to the Linux Lite developers Linux Lite is built on a Ubuntu LTS release. If Linux Lite 2.8 is built on Ubuntu 14.04 LTS then it should already be using Grub 2. Don't be distracted by the black background of the Grub menu. Ubuntu has a purple background. The other flavours of Ubuntu have their own colour. But other than the background colour the Grub 2 menu will look pretty much the same. Unless we modify it in some way.

It is a usual practice for the last installed Linux to install its Grub boot loader into the MBR of the hard disk and thus over-writing the existing Grub boot loader. Are you saying that when you install Linux Lite last its Grub boot menu does not offer loading options for the other OS installed on the hard drive? Are you saying that when you re-install Grub from one of the other OS it does not detect Linux Lite?

If we have one hard drive (sda) and Ubuntu installed on it along with one or more other OS, then we can load into Ubuntu and open the terminal and run

```
sudo update-grub
```

Watch the printout to screen. It should list all the OS detected on that hard drive. If Ubuntu is in control of that boot loader then those OS should appear in the Grub boot menu. If they do not then it may be that Ubuntu is not in charge of the boot menu. To put Ubuntu in charge of the boot menu after running the first command run this second command

```
sudo grub-install /dev/sda
```

This is correct if there is one drive (sda). If there is another drive (sdb) and Ubuntu is on sdb then the command would have to be changed. 

```
sudo grub-install /dev/sdb
```

How you do this in other distributions of Linux I cannot say. Do not assume that these commands will work on other distributions of Linux.

Regards.

---

### Post by buzzingrobot on 2016-03-29
The package listing at Distrowatch says Lite 2.8 uses grub 2.02beta2, the same as 14.04.  I checked a Lite repo mirror and there's no grub there, so, presumably, it is using the 14.04 grub package.

---

### Post by slappedbyzsa on 2016-03-30
> **buzzingrobot said:**
> The package listing at Distrowatch says Lite 2.8 uses grub 2.02beta2, the same as 14.04.  I checked a Lite repo mirror and there's no grub there, so, presumably, it is using the 14.04 grub package.


Thank you for the information regarding grub2 in Linux Lite.

Please note my notation on the bottom of this reply which supplies an answer as I found additional information amoment ago.

OK:  My situation is something otherwise.  The systems of this desktop are Linux Mint (latest update on sda8); Zorin 11 (latest update on sda5) and Peppermint 6 (latest update on sda4).  I had included Linux Lite (latest update on sdb8).  So as you see we are talking more than one harddrive.  Windows XP Pro Sp2 sda1.  

First of all I have experienced successful installations of other linux-ubuntu type systems on sdb with the systems currently installed on sda and all of these systems did interact comfortably sharing whatever was the last grub installed on sda. I would set up the grub with grub customizer to boot whatever was the last booted system.  All systems would have grub customizer installed in this manner.  Add Linux Lite to sdb with other ntfs partitions and there was no problem booting to any OS as long as Linux Lite was the last system installed.  If you do not install Linux Lite last then the situation is quite different..  While you can install other Linux systems in any order (to my experience) and even utilize additional harddrives for Linux OS(say, sda; sdb; sdc) in this manner they will be found by the last grub update and future updates without a problem,  Linux Lite is clearly not simularly resilient.  Once the shared updated grub on sda is updated by a following install by another Linux system,  Linux Lite will not be found by the sda grub.  It will continue to be listed,  but the listing will not work any longer.  Every other system will boot without a problem, but booting to Linux Lite will not be available.

I am not certain why Linux Lite would be the exception to this rule,  but I have run across other postings that have suggested this very same behavior by Linux Lite.  It simply does not seem to be happy unless it has the last word in grub installations.  

This suggests something further.  That would be that in future updates of the grub version on any other Linux Ubuntu OS in the original multi-boot menu,  regardless of Linux Lite being originally installed last, there is the possibility that the user of multiple boot linux systems would lose access to Linux Lite,  if you follow what I am saying. 

I have tried to keep data down in my reply but these are the basics as I have experienced them.

OK:  Having published this I immediately afterward found important information which supplied an explanation for this behavior.  It explained that Linux Lite versions 2 had been altered to be more friendly to shared boots with Windows 7.  This alteration left Linux Lite 2 less compatible with multiple linux distro installations.  Earlier versions of Linux Lite did not (according to this information) suffer from the same limitations.

---

### Post by oldfred on 2016-03-31
If nothing else for your own understanding of what is where:
 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 

When grub2's os-prober does not find another install, you can always copy its boot stanza from its grub.cfg into 40_custom of the grub2 you are using to boot.

I prefer manual customizing over grub customizer. Grub customizer adds its own scripts which some times causes issues.

      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

