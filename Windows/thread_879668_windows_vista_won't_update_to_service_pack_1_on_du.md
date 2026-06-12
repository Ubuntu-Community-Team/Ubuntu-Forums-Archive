---
title: "windows vista won't update to service pack 1 on dual boot setups"
date: 2008-08-04
forum: Windows
---

### Post by macabro22 on 2008-08-04
[http://apcmag.com/vista_sp1_wont_install_on_dualboot_systems_microsoft.htm](http://apcmag.com/vista_sp1_wont_install_on_dualboot_systems_microsoft.htm)

Hi, I am looking forward to solve this matter. Can someone post a step by step solution? I don't want to brake hardy.

---

### Post by fiddledd on 2008-08-04
AFAIK this only applies to Windows Vista Enterprise or Ultimate Edition. I had no problems after SP1 with a Linux mint dual boot. I'm running Vista Home Premium. Just image your hard drive with Acronis True Image (not free) or [Clonezilla](http://www.clonezilla.org/) (free OSS) before you install SP1, then you can restore to how it was if necessary.

---

### Post by macabro22 on 2008-08-04
> **fiddledd said:**
> AFAIK this only applies to Windows Vista Enterprise or Ultimate Edition. I had no problems after SP1 with a Linux mint dual boot. I'm running Vista Home Premium. Just image your hard drive with Acronis True Image (not free) or [Clonezilla](http://www.clonezilla.org/) (free OSS) before you install SP1, then you can restore to how it was if necessary.

I also have vista ultimate edition but the update process fails here. =(

---

### Post by rockface on 2008-08-04
> **fiddledd said:**
> AFAIK this only applies to Windows Vista Enterprise or Ultimate Edition. I had no problems after SP1 with a Linux mint dual boot. I'm running Vista Home Premium. Just image your hard drive with Acronis True Image (not free) or [Clonezilla](http://www.clonezilla.org/) (free OSS) before you install SP1, then you can restore to how it was if necessary.

I knew of a 'Norton Ghost' OSS type solution for my backups. I just forgot the product name and respective URL. Many thanks.

---

### Post by macabro22 on 2008-08-23
You misunderstand. I am unable to finish the update process. I don´t even get to the point where it breaks GRUB(the linux boot chooser thingy).

---

### Post by cmat on 2008-08-25
Oh this explains a lot. I wonder if I can trade in my Vista Business license for a Home Premium. Since I need both Windows and Linux to do work.

---

### Post by macabro22 on 2008-08-25
> **cmat said:**
> Oh this explains a lot. I wonder if I can trade in my Vista Business license for a Home Premium. Since I need both Windows and Linux to do work.

Actually this upgrade obstacle has nothing to do with the windows version. I just went through  the hassle of installing sp1 in my vista home premium guided by microsoft online support.

The upgrade process only worked after reinstalling vista and recovering MBR.

Fortunatelly GRUB cand be easily recovered afterwards and you will get both OS working again.

I suggest you just recover your MBR, update vista, and then recover GRUB that way you very likely can skip the reinstallation step which would take several hours.

Good luck.

---

### Post by cmat on 2008-08-26
If I only knew about this earlier. It's too much downtime. Vista's installation set me back a few hours trying to figure out what the heck was going on with SP1 and then going back to my original setup. I lost a day of work.

---

