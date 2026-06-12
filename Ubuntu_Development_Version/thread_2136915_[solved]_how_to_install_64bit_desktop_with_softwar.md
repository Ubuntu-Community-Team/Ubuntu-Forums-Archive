---
title: "[solved] how to install 64bit desktop with software raid 1"
date: 2013-04-19
forum: Ubuntu Development Version
---

### Post by eyjoel on 2013-04-19
hello community,

i am looking for infos how to install my pc with 13.04 64bit desktop version together with software raid1 on my 2 ssd disks.
at [https://help.ubuntu.com/13.04/](https://help.ubuntu.com/13.04/) the link for the desktop help is dead. the link for the server edition show infos about the installer how to setup the installation with a software raid.
when i try to follow this instruction i found that "physical volume for RAID" in the installer is missing. 

is there a diffence in the installer between desktop and server or is this an error?
i have searched the bugs in launchpad but could not find a corresponding bug.

is it possible to make the raid setup manually and continue with the installer?

best regards

--christian

---

### Post by Gone fishing on 2013-04-19
I built a desktop with raid1 - I'm working away from the family and wanted to build a system that would be fine until I go back home even if an HD failed.

Download and use the alternate CD [http://cdimage.ubuntu.com/lubuntu/daily/current/](http://cdimage.ubuntu.com/lubuntu/daily/current/) and its quite straight forward even if the text mode installer is the prettiest. These instructions seemed about right [http://www.jasonmyres.com/2011/03/installing-ubuntu-10-04-lts-on-a-software-raid1-volume/](http://www.jasonmyres.com/2011/03/installing-ubuntu-10-04-lts-on-a-software-raid1-volume/)

---

### Post by eyjoel on 2013-04-26
hello gone fishing,

thank you for your answer.

i saw that this is a alternate cd for lubuntu with a lxde environment. i guess there is no alterate cd for ubuntu itself?
i have ubuntu already running on my notebook with unity. for the installation on my pc i would like to use unity also.
is it possible to have unity with the lubuntu installation? if yes do i only have to install a unity package after the installation?

best regards

--christian

---

### Post by orawax on 2013-05-27
This has been marked as solved, but I'll add that you could use the [Netboot image]("http://cdimage.ubuntu.com/netboot/13.04/").

---

