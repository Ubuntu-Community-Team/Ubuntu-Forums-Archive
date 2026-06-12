---
title: "new trusty and xenial daily iso files are generated and need testing"
date: 2016-06-26
forum: Ubuntu Development Version
---

### Post by sudodus on 2016-06-26
The LTS versions are getting prepared for the next point releases, 14.04.5 and 16.04.1. New trusty and xenial daily iso files are generated and need testing

- to be discussed here and

- reported at the iso tracker  [http://iso.qa.ubuntu.com](http://iso.qa.ubuntu.com)

-o-

***At least Lubuntu's links to the iso files at the iso tracker are bad (the xenial links are missing [COLOR="#008000"]'xenial'[/COLOR] in the directory path).***

You find the relevant iso files for Lubuntu desktop 32-bit via

```
zsync http://cdimage.ubuntu.com/lubuntu/trusty/daily-live/current/trusty-desktop-i386.iso.zsync

zsync http://cdimage.ubuntu.com/lubuntu/xenial/daily-live/current/xenial-desktop-i386.iso.zsync
```

and the corresponding files for the other iso files, e.g.

for Lubuntu 16.04 alternate 64-bit via

```
zsync http://cdimage.ubuntu.com/lubuntu/xenial/daily/current/xenial-alternate-amd64.iso.zsync
```

***Edit:*** Example how to use zsync:

- Create a suitable directory for the iso file(s) and ***[COLOR="#0000FF"]cd[/COLOR]*** to that directory.
- Run the [COLOR="#0000FF"]zsync command line[/COLOR].

```
$ [COLOR="#0000FF"]zsync http://cdimage.ubuntu.com/lubuntu/xenial/daily/current/xenial-alternate-i386.iso.zsync[/COLOR]
#################### 100.0% 0.0 kBps DONE    

reading seed file xenial-alternate-i386.iso: *****************************************************************************************
**************************************************************************************************************************************
**************************************************************************************************************************************
**************************************************************************************************************************************
**************************************************************************************************************************************
********************
Read xenial-alternate-i386.iso. Target 47.3% complete.      *******
downloading from http://cdimage.ubuntu.com/lubuntu/xenial/daily/current/xenial-alternate-i386.iso:
#################### 100.0% 4890.2 kBps DONE      

verifying download...checksum matches OK
used 365350912 local, fetched 407501427
```

---

### Post by sudodus on 2016-06-26
The Lubuntu desktop 32-bit iso files work (with grey bugs), but the Lubuntu Xenial alternate 64-bit iso managed to throw two red bugs into my face:

[failure while configuring required package while installing Lubuntu alternate](https://bugs.launchpad.net/ubuntu/+source/debootstrap/+bug/1596279)

[the target drive is not found when connected via USB 3 while installing Lubuntu alternate](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1596281)

Please check if you are affected, and in that case, please mark that the bug 'affects me too'.

Maybe somebody should check the server iso and the mini.iso, if they are affected by these bugs too.

---

### Post by jimmy-frydkaer on 2016-06-26
xenial install went a'walk on me on bare metal

---

### Post by sudodus on 2016-06-26
Which iso file did you test :-)

---

### Post by MikeMecanic on 2016-06-26
Thanks for the info.
 
 
 [Getting this message]("http://iso.qa.ubuntu.com/qatracker/milestones/351/builds") for Kylin 20160625 and Ubuntu 20160626
 
 
 *Not Found*
 *The requested URL /ubuntukylin/daily-live/20160625/xenial-desktop-amd64.iso was not found on this server.*
 *Apache/2.2.22 (Ubuntu) Server at cdimage.ubuntu.com Port 80*
 
 
 But if I go [there as usual]("http://cdimage.ubuntu.com/"), I'm able to download the ISO (should be the same).

---

### Post by sudodus on 2016-06-26
There is an interval between the uploads of the various flavours, part of the time the flavours have different dates for the current daily iso file. Some flavour might be delayed because of a particular problem, otherwise they should be updated within an hour or two from one day to another.

***Edit:***

[.../ubuntukylin/xenial/daily-live/current/xenial-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/ubuntukylin/xenial/daily-live/current/xenial-desktop-i386.iso.zsync) exists. You need 'xenial' in the directory path.

[.../xenial/daily-live/current/xenial-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/xenial/daily-live/current/xenial-desktop-i386.iso.zsync) exists. You need 'xenial' in the directory path.

This is why I supplied the links in post #1.

---

### Post by kansasnoob on 2016-07-08
I posted a message at Ubuntu GNOME:

[https://lists.launchpad.net/ubuntu-gnome-development/msg00001.html](https://lists.launchpad.net/ubuntu-gnome-development/msg00001.html)

I shared that at Ubuntu GNOME QA and the standard users mailing list also.

---

### Post by ventrical on 2016-07-08
> **kansasnoob said:**
> I posted a message at Ubuntu GNOME:

[https://lists.launchpad.net/ubuntu-gnome-development/msg00001.html](https://lists.launchpad.net/ubuntu-gnome-development/msg00001.html)

I shared that at Ubuntu GNOME QA and the standard users mailing list also.

I read your message. I really pray for your wellness. I have 6 machines with several hdds with various  stages of installs and sometimes I don't know where to begin. All I do is volunteer work and my regular jobs so I don't fall below the poverty level. Ubuntu testing takes a big chunk of my time (as I see it does your's also). My ISP is Bell and they put me in the poor house each time I try to increase my download speed so  it takes a little while to download .ISOs. However.. ubuntu testing is what I do. :)  and so I will keep all of what you have posted at your link in my front pocket.

Regards..

---

### Post by ventrical on 2016-07-08
Ahhh .. be nice if there was something there.

---

### Post by ventrical on 2016-07-08
> **kansasnoob said:**
> I posted a message at Ubuntu GNOME:

[https://lists.launchpad.net/ubuntu-gnome-development/msg00001.html](https://lists.launchpad.net/ubuntu-gnome-development/msg00001.html)

I shared that at Ubuntu GNOME QA and the standard users mailing list also.

Here goes a wily upgrade to xenial:

---

### Post by ventrical on 2016-07-08
First time I've seen this one but then I don't use the automated upgrader much.

edit:

I moved this topic to another thread.

apologies..

---

### Post by sudodus on 2016-07-09
> **ventrical said:**
> Ahhh .. be nice if there was something there.

Please use the ***zsync*** command lines from the first post of this thread to find the current daily iso files :-)

(There should be a **.../trusty/...** or **.../xenial/...** in the path, not only **.../trusty-...** or **.../xenial-...** in the name.)

---

### Post by kansasnoob on 2016-07-09
> **sudodus said:**
> There is an interval between the uploads of the various flavours, part of the time the flavours have different dates for the current daily iso file. Some flavour might be delayed because of a particular problem, otherwise they should be updated within an hour or two from one day to another.

***Edit:***

[.../ubuntukylin/xenial/daily-live/current/xenial-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/ubuntukylin/xenial/daily-live/current/xenial-desktop-i386.iso.zsync) exists. You need 'xenial' in the directory path.

[.../xenial/daily-live/current/xenial-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/xenial/daily-live/current/xenial-desktop-i386.iso.zsync) exists. You need 'xenial' in the directory path.

This is why I supplied the links in post #1.

I filed a bug report:

[https://bugs.launchpad.net/ubuntu-qa-website/+bug/1600458](https://bugs.launchpad.net/ubuntu-qa-website/+bug/1600458)

---

### Post by kansasnoob on 2016-07-09
> **kansasnoob said:**
> I filed a bug report:

[https://bugs.launchpad.net/ubuntu-qa-website/+bug/1600458](https://bugs.launchpad.net/ubuntu-qa-website/+bug/1600458)

It would be cool if someone that uses IRC Chat could share that with Ubuntu QA @ #ubuntu-quality on freenode. Live chat moves too quickly for me :(

---

### Post by sudodus on 2016-07-09
I have confirmed the bug (in the bug report).

---

### Post by ventrical on 2016-07-09
@kansasnoob, all

I updated from 14.04.1 to 14.04.4 to 16.04.

 It did not go well. Although I do have my install back with full upgraded 16.04 ubuntu-desktop I had to wrangle with terminal and recovery to get it back.

 It does not update grub at the end of the upgrade,. You have to do it manually and I could not boot into systemd. I had to use upstart.

Regards..

---

### Post by ventrical on 2016-07-10
> **sudodus said:**
> The LTS versions are getting prepared for the next point releases, 14.04.5 and 16.04.1. New trusty and xenial daily iso files are generated and need testing

- to be discussed here and

- reported at the iso tracker  [http://iso.qa.ubuntu.com](http://iso.qa.ubuntu.com)

-o-

***At least Lubuntu's links to the iso files at the iso tracker are bad (the xenial links are missing [COLOR=#008000]'xenial'[/COLOR] in the directory path).***

You find the relevant iso files for Lubuntu desktop 32-bit via

```
zsync http://cdimage.ubuntu.com/lubuntu/trusty/daily-live/current/trusty-desktop-i386.iso.zsync

zsync http://cdimage.ubuntu.com/lubuntu/xenial/daily-live/current/xenial-desktop-i386.iso.zsync
```

and the corresponding files for the other iso files, e.g.

for Lubuntu 16.04 alternate 64-bit via

```
zsync http://cdimage.ubuntu.com/lubuntu/xenial/daily/current/xenial-alternate-amd64.iso.zsync
```

***Edit:*** Example how to use zsync:

- Create a suitable directory for the iso file(s) and ***[COLOR=#0000FF]cd[/COLOR]*** to that directory.
- Run the [COLOR=#0000FF]zsync command line[/COLOR].

```
$ [COLOR=#0000FF]zsync http://cdimage.ubuntu.com/lubuntu/xenial/daily/current/xenial-alternate-i386.iso.zsync[/COLOR]
#################### 100.0% 0.0 kBps DONE    

reading seed file xenial-alternate-i386.iso: *****************************************************************************************
**************************************************************************************************************************************
**************************************************************************************************************************************
**************************************************************************************************************************************
**************************************************************************************************************************************
********************
Read xenial-alternate-i386.iso. Target 47.3% complete.      *******
downloading from http://cdimage.ubuntu.com/lubuntu/xenial/daily/current/xenial-alternate-i386.iso:
#################### 100.0% 4890.2 kBps DONE      

verifying download...checksum matches OK
used 365350912 local, fetched 407501427
```

What is zsync link for lubuntu-14.04.1-alternate-i386.iso?

regards..

---

### Post by ventrical on 2016-07-10
What I am doing is  I commited an hdd to testing the upgrades of lubuntu 14.04.1 i386 and amd64bit and i386 alternate installs to point release and xenial upgrade. I have all three 14.04.1 lubuntu releases previously on one of my other installs so bandwidth is saved for me.

Regards..

---

### Post by sudodus on 2016-07-11
I think there is only one Lubuntu Trusty daily iso file, and it is there for us to test what will soon be released as ***Lubuntu 14.04.5 LTS***.

**lubuntu-14.04.1-alternate-i386.iso** is released, and will not be changed. But there are zsync files (and also torrent files) for the original 14.04 LTS and all point releases in the following link,

[.../lubuntu/releases/14.04.1/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04.1/release/)

You find the released versions and flavours via the following link,

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by ventrical on 2016-07-11
I have all the 14.04.1 ISO  releases of lubuntu. Basically I just wanted to test the upgrade on them.

> 
Week of July 18th:

The first point release of Xenial (16.04.1) is due on July 21st so we  need to test both i386 and amd64 installation media. We also need to  perform upgrade tests for both architectures from all four available HWE  versions of Trusty. To do so we&#8217;d need to start with the proper Trusty  installation media and then apply all standard updates before performing  the release upgrade tests: 14.04.1 w/OEM Trusty HWE &#8594; Xenial


@kansasnoob

I have a commited machine with two virgin installs of lubuntu trusty 14.04.1.  i386 and amd64bit. I have upgraded the i386 to 14.04.4 witout a glitch and will do the same with amd64bit. Then I will upgrade to xenial and report back here. That will be my contribution for whatever it's worth. Time permitting I will do more.

Regards..

regards..

---

### Post by geppetto on 2016-07-19
I posted my problem at [https://ubuntuforums.org/showthread.php?t=2331033](https://ubuntuforums.org/showthread.php?t=2331033) (see below)

I have downloaded now the daily image at [http://archive.ubuntu.com/ubuntu/dists/xenial/main/installer-i386/20101020ubuntu451/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/xenial/main/installer-i386/20101020ubuntu451/images/netboot/mini.iso) and the problem persists.

I copy here the text of the above post:

===
The creation of a VirtualBox Ubuntu image worked perfectly yesterday morning (July 16 2016). In the afternoon I repeated the process but the installation procedure stopped when trying to install the nic-firmware package: it simply stops at 26% of the installation process suggesting to change mirror. I've tried several mirrors, with no success. The problem persists today (July 17).

To reproduce the problem, download the 32bit 16.04 "minimal" installation iso, and proceed with the creation of the VirtualBox machine (i.e., create the empty vm, add a virtual disk, set the mini.iso as installation CD, run the installation). After setting locales and hostname, the installation starts downloading the packages; the initial downloads are successful, but the process pauses when the nic-firmware is reached, and after a delay the download is interrupted with a message suggesting to change mirror.

I suspect the package has been deleted or replaced.

Thank you
===

I received only a funny reply that I do not mention here.

Thank you

---

### Post by sudodus on 2016-07-19
Thanks for the heads up :-)

I sent the following mail to two Lubuntu mailing lists hoping to get help to find out more about it and (I hope) find a solution. (Some people are testing Lubuntu in virtual machines (VirtualBox and KVM & virt-manager)).

> Hi lubuntuers,

There is an Ubuntu Forums thread about problems with mini.iso (32-bit) in VirtualBox.

[https://ubuntuforums.org/showthread.php?t=2331033](https://ubuntuforums.org/showthread.php?t=2331033)

1. Do you think this a real bug in mini.iso?

2. Is there a corresponding bug in Lubuntu?

3. Do you know of a bug report about it?

4. Should we be concerned about it? Will it affect the possibility to install Lubuntu via the mini.iso and maybe also via the Ubuntu Server iso file?

Best regards
Nio 

---

### Post by sudodus on 2016-07-20
[SIZE=4]It works for me to install from the 16.04.1 LTS 32-bit mini.iso  in a real computer as well as in VirtualBox[/SIZE]

I tested the current Xenial 32-bit mini.iso in Virtualbox version 5.0.24_Ubuntu r108355 , the current version that comes with an up to date Xenial installed system.

1. The link to the current iso file in the qa tracker is faulty. I found the correct one via [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

[archive.ubuntu.com/ubuntu/dists/xenial-updates/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/installer-i386/current/images/netboot/mini.iso)

```
$ ls -ltr mini.iso
-rw-rw-r-- 1 nio nio 50331648 jul 19 21:13 mini.iso  # my local time corresponding to UTC 19:13 as listed at the link.
$ md5sum mini.iso
8de386f9001c762956a86b1b4654452d  mini.iso
```

2. *ctrl + alt + F2* (or similar) was necessary to 'wake up the installed system' after reboot (with Intel graphics). Otherwise the iso file works - I found no problem in VirtualBox.

.o.

***Edit:*** I don't know why you had problems, *geppetto*. Maybe because you were using a bad version of the mini.iso, maybe because you used an old or badly configured virtual machine, maybe the network connection caused problems.

I use wired internet (ethernet) with the mini.iso during the installation. But if you install a desktop system (into the text-only mini system), for example Lubuntu or Xubuntu, it will bring a working wifi system too, at least if there is suitable hardware for it (for example in laptops and netbooks, or with a USB wifi adapter). If there are problems with wifi, I would blame the virtual machine or the host operating system rather than the mini.iso.

---

### Post by geppetto on 2016-07-20
Checked the md5 of your mini.iso and it was different from mine. So I downloaded from you link: now, no problem with nic-firmware, but the installation hangs in exactly the same way with package scsi-modules-4.4.0-0-31-generic-di. I can't double check right now, I'm on travel, but I'll try to be more precise as soon as I'm by my desk.

---

### Post by geppetto on 2016-07-20
Checked n-times and it's always that. I checked virtualbox version and it is synchronized with current xenial revision (namely VirtualBox Version 5.0.24_Ubuntu r108355). The mini.iso is identical to the one you use (same md5), and the virtual machine is new, with no special features. Anyway, it's configured in the same way as the one I used on saturday, and working ok. The problem is now with scsi (!), and so, no interference from hw available on the vm. I think I will try to create a 15.10 and upgrade, and watch for silent mini.iso updates...

---

### Post by sudodus on 2016-07-20
Too bad. I don't understand why you have problems with that scsi package.

Edit: Is it a server with some old scsi hardware?

Unfortunately 15.10 will very soon pass end of life (I think during this month, so it is not a good alternative). It is better to try ***a mini.iso of the previous LTS release, 14.04.1 LTS***.

Another better alternative to get a mini system with a text interface is to ***start from a compressed image file or a tarball*** of already installed systems according to the following links. It is a shortcut to a working mini system with only text user interface (until you install a graphical desktop environment).

64-bits:
[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

32-bits:
[Tested and debugged system to install [Ubuntu flavours of] Xenial 32-bit alias 16.04 LTS]](https://ubuntuforums.org/showthread.php?t=2172971&page=3&p=13511441#post13511441)

[ OBI/Xenial-32-txt](https://help.ubuntu.com/community/OBI/Xenial-32-txt)

---

### Post by geppetto on 2016-07-20
The 15.10 workaround means that I first install my minimal 15.10 (I want an ubuntu with ssh-server only, in a reproducible way) and next do-release-upgrade. And it just worked: less than 700MB for a 16.04. But I will not mark the problem as solved: it's a workaround, not a solution. I'll try again the native 16.04 mini.iso, but at this point I got my result :-)

Bye and thank you

---

### Post by sudodus on 2016-07-20
Congratulations to finding the workaround, and thanks for sharing your solution :-)

Please write it also ***in your own thread***, and mark that thread as SOLVED (click on **Thread Tools** at the top of the page). It will help other people find your solution.

---

### Post by geppetto on 2016-07-21
Ok, but can't mark mine as a solution. This thread too looks similar, and might merge:

[https://ubuntuforums.org/showthread.php?t=2329080](https://ubuntuforums.org/showthread.php?t=2329080)

---

### Post by kansasnoob on 2016-07-25
I've noticed that the Ubuntu Trusty daily images have been frozen at 20160723 so I'm hoping the next respin will have the lts-xenial HWE bits.

---

### Post by kansasnoob on 2016-07-26
> **kansasnoob said:**
> I've noticed that the Ubuntu Trusty daily images have been frozen at 20160723 so I'm hoping the next respin will have the lts-xenial HWE bits.

According to the amd64 manifest the lts-xenial bits have landed in Trusty:

[http://cdimage.ubuntu.com/trusty/daily-live/current/trusty-desktop-amd64.manifest](http://cdimage.ubuntu.com/trusty/daily-live/current/trusty-desktop-amd64.manifest)

I hope to have time to test one today :)

---

### Post by ventrical on 2016-07-29
I recived e-mail abotu a bug I submitted:

> 
  [SIZE=2] Hello ventrical, or anyone else affected,

Accepted ubuntu-release-upgrader into xenial-proposed. The package will
build now and be available at [https://launchpad.net/ubuntu/+source](https://launchpad.net/ubuntu/+source)
/ubuntu-release-upgrader/1:16.04.15 in a few hours, and then in the
-proposed repository.

Please help us by testing this new package.  See
[https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed) for documentation how to
enable and use -proposed.  Your feedback will aid us getting this update
out to other Ubuntu users.

If this package fixes the bug for you, please add a comment to this bug,
mentioning the version of the package you tested, and change the tag
from verification-needed to verification-done. If it does not fix the
bug for you, please add a comment stating that, and change the tag to
verification-failed.  In either case, details of your testing will help
us make a better decision.

Further information regarding the verification process can be found at
[https://wiki.ubuntu.com/QATeam/PerformingSRUVerification](https://wiki.ubuntu.com/QATeam/PerformingSRUVerification) .  Thank you in
advance!

** Changed in: ubuntu-release-upgrader (Ubuntu Xenial)
       Status: In Progress => Fix Committed

** Tags added: verification-needed

-- 
You received this bug notification because you are subscribed to the bug
report.
[https://bugs.launchpad.net/bugs/1603576](https://bugs.launchpad.net/bugs/1603576)

Title:
  release-upgrader shows that Xenial is still in development & doesn't
  mention it's LTS

Status in ubuntu-release-upgrader package in Ubuntu:
  Invalid
Status in ubuntu-release-upgrader source package in Xenial:
  Fix Committed

Bug description:
  [Test Case]
  1) Look at [http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/dist-upgrader-all/current/ReleaseAnnouncement](http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/dist-upgrader-all/current/ReleaseAnnouncement) and notice that it doesn't have "16.04 LTS".

  When the new version of dist-upgrader is built replace -updates w/
  -proposed and observe "16.04 LTS".

  ----------------------------------------------------------------------

  while testing an upgrade from Lubuntu 14.04.4 to xenial using update-
  manager -d -c it notifys that xenial is still in development and not
  an LTS version. - see screenshot at link.

  [https://ubuntuforums.org/showthread.php?t=2330857&p=13517778#post13517778](https://ubuntuforums.org/showthread.php?t=2330857&p=13517778#post13517778)

  ProblemType: BugDistroRelease: Ubuntu 16.04
  Package: update-manager 1:16.04.3
  ProcVersionSignature: Ubuntu 4.4.0-31.50-generic 4.4.13
  Uname: Linux 4.4.0-31-generic x86_64
  ApportVersion: 2.20.1-0ubuntu2.1
  Aptdaemon:

  Architecture: amd64
  CurrentDesktop: LXDE
  Date: Fri Jul 15 18:28:53 2016
  GsettingsChanges:
   b'com.ubuntu.update-manager' b'first-run' b'false'
   b'com.ubuntu.update-manager' b'launch-time' b'1468616417'
  InstallationDate: Installed on 2016-07-11 (4 days ago)
  InstallationMedia: Lubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
  PackageArchitecture: allSourcePackage: update-manager
  UpgradeStatus: Upgraded to xenial on 2016-07-15 (0 days ago)

To manage notifications about this bug go to:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1603576/+subscriptions](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1603576/+subscriptions)



..but taking a side step here I switched over to Ubuntu Desktop 14.04.1 .iso, hard installed it and  got the following notification in screenshot below. So I am assuming that the new package was automatically installed during the installation. I will then go ahead with the installation.



 [/SIZE]

---

### Post by ventrical on 2016-07-29
And I got an absolute fail...

so I will ..
```

sudo apt-get update
sudo apt-get dist-upgrade

```

and then try again..

---

### Post by ventrical on 2016-07-29
...done .. and now proceeding with upgrade..

---

### Post by ventrical on 2016-07-29
This was a successful upgrade. The performance of xenial is much quicker than trusty 14.04.1

... so .. it is not difficult now to upgrade from a 14.04.1 version of trusty to xenial with the exception that it may have to be fully updated to 14.04.4 or at least have the depend.

Regards..

---

### Post by ventrical on 2016-07-29
For what it is worth I am choosing not to remove obsolete files when offered by the upgrader. I have had many problems with this. Also .. not being rolled over into llvmpipe is nice too :)

regards..

---

### Post by QDR06VV9 on 2016-07-29
> **ventrical said:**
> This was a successful upgrade. The performance of xenial is much quicker than trusty 14.04.1

... so .. it is not difficult now to upgrade from a 14.04.1 version of trusty to xenial with the exception that it may have to be fully updated to 14.04.4 or at least have the depend.

Regards..

This was before the Update Manger notified of the the Upgrade to 16.04 on my machine..but out of 3 installs with the various versions IE 14.04.1, 14.04.3, and 14.04.4....the 14.04.4 was the only one that upgraded successfully.
The other 2 versions were frozen with installing fonts.
Keep in mind this was before the the Update Manager reported the new Upgrade.
Keep up the good work you guys..and i miss this.:(
Regards

---

### Post by sudodus on 2016-07-30
I have been testing that it works to create ***persistent live drives of the current releases and particularly the release candidates*** (14.04.5 LTS, 16.04.1 LTS and Yakkety Yak).

It works for me :-)

I have tried two methods,

***1. systems made with mkusb, single drive persistent live systems:***

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

***2. 'Simple persistence': systems, that use a cloned read-only boot drive (CD, DVD, USB) and another drive with partitions for persistence:***

[mkusb/sp](https://help.ubuntu.com/community/mkusb/sp)

I described this method to help also new people understand what is needed to make a persistent live system, and how it can be enhanced with extra partitions. This can be a good alternative now that several tools clone the iso file to a USB drive, for example mkusb, gnome-disks, usb-creator-gtk version 0.3.2-. These boot drives will be read-only, so you cannot put a file or partition for persistence onto it.

You are very welcome to test these things, and report both good and bad results :-)

---

