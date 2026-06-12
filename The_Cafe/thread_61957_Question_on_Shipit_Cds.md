---
title: "Question on Shipit Cds"
date: 2005-09-02
forum: The Cafe
---

### Post by alcedo on 2005-09-02
Hi people, i am wondering whether Ubuntu would keep on mailing new cds to you on a regular basis ? for example, i just received my ubuntu Cd, version 5.04. I am now thinking about future release. Would i still get future release mailed to me ? or do i have to download future releases ? Best is if i could get future releases mailed to me of course.

---

### Post by DJ_Max on 2005-09-02
[QUOTE=alcedo]Hi people, i am wondering whether Ubuntu would keep on mailing new cds to you on a regular basis ? for example, i just received my ubuntu Cd, version 5.04. I am now thinking about future release. Would i still get future release mailed to me ? or do i have to download future releases ? Best is if i could get future releases mailed to me of course.[/QUOTE]
 [http://ubuntuforums.org/showthread.php?t=49905&highlight=shipit](http://ubuntuforums.org/showthread.php?t=49905&highlight=shipit)

---

### Post by aysiu on 2005-09-02
[QUOTE=alcedo] Best is if i could get future releases mailed to me of course.[/QUOTE] Why is that best? Even on dial-up a sudo apt-get dist-upgrade would take less time than the CDs...

---

### Post by alcedo on 2005-09-03
Well, i kind of felt that its the best to have them shipped over as i want to update the entire OS ? (because fedora core requires me to do so, and i can't stand the long wait of downloading 700mb worth of content) so yeah. i am knew to debian / ubuntu way of doing things though. 

To summarise, apt-get would upgrade the entire OS and install new packages and over write old packages as well ?

---

### Post by aysiu on 2005-09-03
When you do an apt-get dist-upgrade, it doesn't download an entire 700 MB disk image. It just upgrades the existing OS (the kernel, etc.). I haven't done a dist-upgrade in Ubuntu, but I did one for Blag, and it took maybe about fifteen minutes over broadband internet.

I'm not sure if it updates all the old packages, but you can do that even before Breezy comes out by doing *sudo apt-get update* and then *sudo apt-get upgrade*.

"Upgrade" here upgrades your existing programs. "Dist-upgrade" upgrades the entire OS.

---

### Post by alcedo on 2005-09-04
ar. ok.  so i guess there really isnt a need to keep on getting new release than. apt get function should do the trick :P

---

### Post by alcedo on 2005-09-04
Btw, is
sudo apt-get update  is for packages updates ?
sudo apt-get upgrade is for OS updates ?

are there any apt-get functions to updates ? or is that the only 2. Thanks for the help  :razz:

---

### Post by aysiu on 2005-09-04
[QUOTE=alcedo]ar. ok.  so i guess there really isnt a need to keep on getting new release than. apt get function should do the trick :P[/QUOTE] Before you do the apt-get update and apt-get dist-upgrade, you'll have to change your /etc/apt/sources.list so that all the hoary references become breezy.

---

