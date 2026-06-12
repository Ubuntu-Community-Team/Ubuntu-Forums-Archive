---
title: "Dualbooting windows 8.1 and Elementary OS"
date: 2014-09-07
forum: Ubuntu/Debian BASED
---

### Post by Alexander_Alsing on 2014-09-07
Hi.

I'm having troubles installing Elementary OS(EOS) as my scond OS besides windows 8.1 pro. The EOS forum suggested me that i asked my question here, so here goes. 

I have 1 SSD and 1 HDD, on the SSD i have partitioned it to two main patitions - 1 for windows and 1 for Elementary OS. On the HDD i have 2 paritions for windows storage and 2 partitions for EOS (1 swap on 16GB and 1 for /home on 150 GB). I am able to install EOS and see it in the boot menu, but when i boot in EOS i get a black screen with the text "GNU GRUB...", and the possibility to see which commands i can use with TAP, much like this picture: 
[http://recursostic.educacion.es/observatorio/web/images/upload/ccam0040/grub/Sistema_arranque_GRUB_elv_html_m43a065f0.png](http://recursostic.educacion.es/observatorio/web/images/upload/ccam0040/grub/Sistema_arranque_GRUB_elv_html_m43a065f0.png)

I have tried to install EOS multiple times but with the same outcome. Then i have tried to use boot repair, to fix the boot problem: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I am able to make a live usb from it and boot from it, but when i choose to boot from the live usb with boot repair the screen is just black. - then i tried it with a DVD and another usb - still with the same outcome....

This is quite annoying and i hope that you can help me :)!

---

### Post by lisati on 2014-09-07
*Thread moved to **Other Operating Systems and Projects**.*

---

### Post by LostFarmer on 2014-09-07
Do not have mush time right now but you may have hit a bug ,[https://bugs.launchpad.net/elementaryos/+bug/1355698](https://bugs.launchpad.net/elementaryos/+bug/1355698). There are fixes there you can try.
Can try the last post [http://ubuntuforums.org/showthread.php?t=2239951&page=2](http://ubuntuforums.org/showthread.php?t=2239951&page=2)

When you run boot-repair a URL is listed for you to post when seeking help, it is very useful , it gives us more info on what is going on.

---

### Post by Alexander_Alsing on 2014-09-07
Got i solved! - i needed to enable CSM and then i was able to boot boot-repair, which fixed my problem :)

---

### Post by Stinger on 2014-09-07
Alexander,  I'm curious of which version of elementary you have successfully installed, Luna or Freya ?

---

### Post by Alexander_Alsing on 2014-09-07
> **Stinger said:**
> Alexander,  I'm curious of which version of elementary you have successfully installed, Luna or Freya ?
Luna :)

---

