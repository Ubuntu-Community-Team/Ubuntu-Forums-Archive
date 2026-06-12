---
title: "The answer to my prayers!"
date: 2009-12-19
forum: Virtualisation
---

### Post by Tamalin on 2009-12-19
After many long hours spent uselessly toiling away on forums, trying desperately to get my iPod touch 2G to sync with VirtualBox, praying it would work, my prayers have been answered.  I now want to share my solution with the world so no-one else has to go through that.

First, I followed the instructions from [this thread]("http://ubuntuforums.org/showthread.php?t=970628").  However, I think it needed to be supplemented by [this]("https://help.ubuntu.com/community/VirtualBox/USB").  I was using Ubuntu 8.04 Hardy.  After doing all this over and over, nothing worked.  I didn't recieve any error messages, but my iPod wasn't really picked up much by XP either.  It was listed in VB as a connected USB device, but it didn't do anything.  Later I ran "sudo /etc/init.d/vboxdrv setup" and rebooted.  This still didn't accomplish anything.  Finally, and idea came to my head wich could have been nothing other than divine intervention.  I went to my XP control panel and selected "Administrative Tools" then I went to "Computer Management".  In computer management, I selected "Computer Management (local)" -> "System Tools" -> "Device Manager"  I saw one of the listed devices was listed with a ? icon.  I selected this and looked at the properties.  I saw that according to the computer, it was having a problem, and I needed to install the driver.  So I installed the driver.  After less than a minute the driver was installed, and it suddenly worked perfectly.  My iPod was recognized, and photos were transferred, and iTunes picked it up instantly.  I was ecstatic.  This may have had something to do with my USB hardware (I am using an IBM Z60t).  I am SO thankful for this fix.  I hope someone else can find this information useful.

---

