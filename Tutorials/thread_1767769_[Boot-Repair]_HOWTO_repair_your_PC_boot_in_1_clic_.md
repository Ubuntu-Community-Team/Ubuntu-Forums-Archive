---
title: "[Boot-Repair] HOWTO repair your PC boot in 1 clic !"
date: 2011-05-26
forum: Tutorials
---

### Post by YannBuntu on 2011-05-26
Many computer boot problems can be solved by reinstalling GRUB. Here is a short HOWTO to do this :

1) Boot on any Ubuntu live-CD (choose "Try Ubuntu")

2) Install and run Boot-Repair

[HTML]sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo sed 's/trusty/saucy/g' -i /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
sudo apt-get update
sudo apt-get install -y boot-repair && (boot-repair &)[/HTML]

3) Click on "Recommended repair", or go into the Advanced options to customize GRUB options
[IMG]http://pix.toile-libre.org/upload/img/1315191717.png[/IMG]

More information on : [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Enjoy ! :P

---

### Post by YannBuntu on 2011-07-13
Articles about Boot-Repair :

**- English:**
["Boot-Repair - Simple tool to repair frequent boot problems" on Ubuntugeek]("http://www.ubuntugeek.com/boot-repair-simple-tool-to-repair-frequent-boot-problems.html")
["Fix Ubuntu Boot Issues" on webupd8]("http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html")
["Reinstalling GRUB in Ubuntu Made Easy!" on MyGeekOpinions]("http://mygeekopinions.blogspot.com/2011/06/install-boot-repair-in-ubuntu-1104.html")
["Graphical Tool to Repair Frequent Boot Problems (Install Boot-Repair in Ubuntu via PPA)" on WebCoz]("http://www.webcoz.com/boot-repair-graphical-tool-to-repair-frequent-boot-problems-install-boot-repair-in-ubuntu-via-ppa/")
["Boot Repair Fixes Frequent Ubuntu Boot Problems" on Addictivetips]("http://www.addictivetips.com/ubuntu-linux-tips/boot-repair-fixes-frequent-ubuntu-boot-problems")
["Boot-Repair Restores GRUB Loader and MBR to get back access to Ubuntu" on Wrock]("http://wrock.org/pc-world-menia/boot-repair-restores-grub-loader-and-mbr-to-get-back-access-to-ubuntu")
["Fix Ubuntu Boot Issues (After Installing Another OS Or Faulty GRUB Upgrade)" on My Bookmark]("http://mybookmarks.ro/desktop-ubuntu/boot-repair-fix-ubuntu-boot-issues-after-installing-another-os-or-faulty-grub-upgrade-2/")
["How to Install Boot-Repair in Ubuntu 11.04 Natty Narwhal, Fix Ubuntu Boot Issues with Boot-Repair" on WebCoz]("http://www.webcoz.com/how-to-install-boot-repair-in-ubuntu-11-04-natty-narwhal-fix-ubuntu-boot-issues-with-boot-repair/")
["Boot-Repair : Fix Ubuntu Boot Issues (After Installing Another OS Or Faulty GRUB Upgrade)" on LinuxO]("http://www.linuxo.com/content/boot-repair-fix-ubuntu-boot-issues-after-installing-another-os-or-faulty-grub-upgrade")
["Boot Fix - GRUB Error Solution - Linux Ubuntu" on YouTube]("http://www.youtube.com/watch?v=cbIHWoJhIII")

**- Italian:**
["Boot-Repair" on UbuntuBond]("http://ubuntubond.blogspot.com/2011/06/boot-repair.html")

**- French:**
["Boot-Repair: Réparer le démarrage du PC (GRUB, MBR) en 1 clic !" on ubuntu-fr]("http://forum.ubuntu-fr.org/viewtopic.php?pid=4726141")

---

### Post by coffeecat on 2014-08-05
Bump to reopen thread.

---

