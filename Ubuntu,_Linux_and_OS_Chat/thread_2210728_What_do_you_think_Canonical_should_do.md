---
title: "What do you think Canonical should do?"
date: 2014-03-12
forum: Ubuntu, Linux and OS Chat
---

### Post by nunecas123 on 2014-03-12
My point with this thread is suggestions for Canonical. I know they probably won't hear but at least we get to discuss what things should be changed.

Good day! :D

---

### Post by mikewhatever on 2014-03-12
...and why do you think anything should be changed?

---

### Post by ian-weisser on 2014-03-12
An Ubuntu Developer Summit is going on TODAY, 100% open to the public and online.
Why bother with a quickly-forgotten forum thread when you can *talk* to the actual development and design teams, and participate in the decisionmaking?

---

### Post by forrestcupp on 2014-03-13
They should make TV commercials with hipsters to make everyone think Ubuntu is cool.

---

### Post by Dave_L on 2014-03-14
Canonical should make its own brand of coffee! \\:D/

---

### Post by PaulW2U on 2014-03-14
> **nunecas123 said:**
> My point with this thread is suggestions for Canonical. I know they probably won't hear but at least we get to discuss what things should be changed.

And the point of that is what?

If you want to change what any of the flavours do then you can talk to them directly as the groups are very small. But Mark Shuttleworth and Canonical have a long term plan for Ubuntu in which they are talking with global partners about a variety of platforms. Millions of pounds/dollars/euros are at stake.

Sorry but I can't see the point of a random thread on a user forum inviting discussion about something that will never be read let alone be considered by those that are in a position to change things. :confused:

---

### Post by forrestcupp on 2014-03-14
> **PaulW2U said:**
> And the point of that is what?

If you want to change what any of the flavours do then you can talk to them directly as the groups are very small. But Mark Shuttleworth and Canonical have a long term plan for Ubuntu in which they are talking with global partners about a variety of platforms. Millions of pounds/dollars/euros are at stake.

Sorry but I can't see the point of a random thread on a user forum inviting discussion about something that will never be read let alone be considered by those that are in a position to change things. :confused:

It doesn't have to make a difference. It can just be an interesting conversation on a forum. Plus, for the people who think that everything has to make a difference, maybe brainstorming on a forum will inspire someone to take the ideas to the proper venue. There's no point in going to the proper venue if you don't already have something to present. ;)

---

### Post by Jonor on 2014-03-14
Possibly an old chestnut ?
How about changing the codename for releases to remove the implicit pressure of getting them out in one particular target month.
So 14.04 becomes 14.1 and 14.10 becomes 14.2 ; it is still informative to the year.
Having only one decimal place should avoid most confusion leaving only those people who call 14.10 14.1 to have to reteach themselves.

---

### Post by lykwydchykyn on 2014-03-14
Start an industry training & certification program for Ubuntu techs.

---

### Post by Dave_L on 2014-03-15
> **Jonor said:**
> Possibly an old chestnut ?
How about changing the codename for releases to remove the implicit pressure of getting them out in one particular target month.
So 14.04 becomes 14.1 and 14.10 becomes 14.2 ; it is still informative to the year.
Having only one decimal place should avoid most confusion leaving only those people who call 14.10 14.1 to have to reteach themselves.

I disagree.

A predictable release schedule forces (and allows) developers, testers and users to plan ahead and use consistent methodology. The naming convention helps enforce the schedule.

If the specific date were not part of the name, then an influential developer could insist a release be delayed a month so that "his change" gets incorporated. Or some other excuse would be found to delay a release. And the effect could snowball, leading to releases being delayed by months.

---

### Post by Jonor on 2014-03-15
They perhaps could and that would be one of the risks along with not having the motivation that some people appreciate 
of having to work to a deadline but whoever makes the final decision would not feel forced into releasing something prematurely. 
Very occasional delays of a few weeks happens in other distros that use plain numbering and i think it is a better risk.
My thoughts are particularly on 13.10 which had crashing of major apps on release on my hardware but was much better about 4-6 weeks later.

---

### Post by ian-weisser on 2014-03-15
I have not seen evidence that "deadline pressure" is an issue at all, nor that deadlines are reducing Ubuntu's quality.

If your broken application was imported from Debian, then that import deadline was already over 60 days before release. That's not "deadline pressure." That seems more like a lack of volunteer testers for your hardware and/or application. More time would not help.

One of the original reasons (and great strengths) of the six-month release cycle is that frequent releases reduce the importance of deadlines - upstreams can release when they are ready. 

The every-three-month checkups at Ubuntu Developer Summits already look  for unrealistic goals and struggling projects.

---

### Post by aspergerian on 2014-03-16
Canonical could develop an installation procedure that allows a person to install to a USB drive (eg, flash or HDD) and do so without modifying the MBR on sda. Removing or disconnecting an internal HDD seems excessive for what instead could/should be a accomplished by a GUI choice:

_install as dual boot and modify MBR or GRUB on sda.
_install only to external device without modifying MBR or installing GRUB on sda.

---

### Post by coffeecat on 2014-03-16
> **aspergerian said:**
> Canonical could develop an installation procedure that allows a person to install to a USB drive (eg, flash or HDD) and do so without modifying the MBR on sda. Removing or disconnecting an internal HDD seems excessive for what instead could/should be a accomplished by a GUI choice:

_install as dual boot and modify MBR or GRUB on sda.
_install only to external device without modifying MBR or installing GRUB on sda.

You can do that already with the GUI installer - it's been possible for years. I've done that a few times myself, installing to a USB drive and installing grub only on the mbr of the USB drive.

---

### Post by aspergerian on 2014-03-16
> **coffeecat said:**
> You can do that already with the GUI installer - it's been possible for years. I've done that a few times myself, installing to a USB drive and installing grub only on the mbr of the USB drive.

Are you referring to a full install to the USB drive or to an install which includes the iso file as a necessary part of the USB-drive installation?

---

### Post by coffeecat on 2014-03-16
A full bootable install.

---

### Post by cariboo on 2014-03-16
I'm currently running Trusty Gnome-shell on a 32GiB usb thumb drive, this is a full install:

```
 df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1        28G  3.7G   23G  14% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.0G   12K  2.0G   1% /dev
tmpfs           404M  1.2M  403M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  380K  2.0G   1% /run/shm
none            100M   28K  100M   1% /run/user
/dev/sr0        7.5G  7.5G     0 100% /media/cariboo/<RED_2>
```

This is the fdisk -l output, the drive I'm running from is the second one, /dev/sdb:

```
sudo fdisk -l
[sudo] password for cariboo: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aa8aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    19531344     9764648+  83  Linux
/dev/sda2        19531776    23437311     1952768   82  Linux swap / Solaris
/dev/sda3        23437312   488396799   232479744   83  Linux

Disk /dev/sdb: 32.0 GB, 32015679488 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62530624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000151fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    58593844    29295898+  83  Linux
/dev/sdb2        58595326    62529535     1967105    5  Extended
/dev/sdb5        58595328    62529535     1967104   82  Linux swap / Solaris
```

---

### Post by aspergerian on 2014-03-16
coffeecat and cariboo907,

Thank you for the responses. I'm pursuing Howto in the Installation & Upgrades forum [here]("http://ubuntuforums.org/showthread.php?t=2208266").

---

