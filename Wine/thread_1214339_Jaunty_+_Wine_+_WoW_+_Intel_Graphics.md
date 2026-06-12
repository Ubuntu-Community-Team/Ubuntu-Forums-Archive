---
title: "Jaunty + Wine + WoW + Intel Graphics"
date: 2009-07-15
forum: Wine
---

### Post by ct728m on 2009-07-15
Hello! I am a fairly new user to the Linux world and seem to be having a little trouble with getting WoW to work with Wine under Ubuntu 9.04 Jaunty. I downloaded all the patches for WoW separately and patched the system on a Windows XP box. I then copied the entire folder contents to my external hard drive. I am able to start it with "/media/ExternalHDD/WoW/WoW.exe". The game starts up but the graphics are horrible with a huge black screen. I believe the problem to be the drivers for the graphics card, but I need a little help with either updating it or editing the xorg.conf file. I also am not 100% sure which version of Wine I am running because on the about screen it just says "PACKAGE_STRING". Hopefully I have provided enough information below.

```
laptop:~$ cat /proc/version
Linux version 2.6.28-13-generic (buildd@vernadsky) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009

```

```
laptop:~$ lspci | grep 915
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)
```

```
asd3144@asd3144-laptop:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server cofiguration file

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

---

### Post by ThisEndlessFall on 2009-07-15
I'm sorry but Jaunty has broken Intel graphic drivers. You may want to dual boot with Windows if you want to play WoW.

Or buy a Nvidia graphics card if your PC has the room for one. They work very well, especially with WINE.

---

### Post by Dougie187 on 2009-07-15
> **ThisEndlessFall said:**
> I'm sorry but Jaunty has broken Intel graphic drivers. You may want to dual boot with Windows if you want to play WoW.

Or buy a Nvidia graphics card if your PC has the room for one. They work very well, especially with WINE.

Or revert to Hardy or Intrepid.

---

### Post by ct728m on 2009-07-15
>  	Quote:
 	 	 		 			 				 					Originally Posted by **ThisEndlessFall** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7623176#post7623176") 				
 				[I]I'm sorry but Jaunty has broken Intel graphic drivers. You may want to dual boot with Windows if you want to play WoW.

Or buy a Nvidia graphics card if your PC has the room for one. They work very well, especially with WINE.[/I]
 			 		 	 	 
Or revert to Hardy or Intrepid.

At this point since I have Jaunty installed over the entire 60GB HDD, I do not think it would be an easy task to dual boot with Windows. I have always heard its easier to have Windows installed first before installing Ubuntu.

Is it possible to downgrade to Hardy or Intrepid? I know when I installed Jaunty that I set up some of the folders on different partitions to make it easy to reinstall if necessary, but not sure what else I might mess up.

---

### Post by ThisEndlessFall on 2009-07-15
> **ct728m said:**
> At this point since I have Jaunty installed over the entire 60GB HDD, I do not think it would be an easy task to dual boot with Windows. I have always heard its easier to have Windows installed first before installing Ubuntu.

Is it possible to downgrade to Hardy or Intrepid? I know when I installed Jaunty that I set up some of the folders on different partitions to make it easy to reinstall if necessary, but not sure what else I might mess up.

I would really suggest investing in a Nvidia (not ATI under any circumstances, their drivers for linux are very bad) card. A GForce 6600GT or above would work very well for you, as long as your PC has a spare PCI/AGP/PCI-E slot of course.

---

### Post by ct728m on 2009-07-15
Nope because its a laptop. And its not really worth me investing in one of those external video cards either since this is a work laptop.

---

### Post by ThisEndlessFall on 2009-07-15
> **ct728m said:**
> Nope because its a laptop. And its not really worth me investing in one of those external video cards either since this is a work laptop.

Oh ok. Then I would suggest abandoning Ubuntu altogether and returning to Windows. 
It works better with Intel GPU's. 
You could try returning to Hardy which has O-K Intel drivers as far as I know, but I have read so many problems that people are having running WoW under WINE with an Intel GPU on these & other forums, that I really would suggest returning to Windows for now until Karmic when hopefully the Intel issue will be fixed.

It will save a lot of headaches.

---

### Post by NightMKoder on 2009-07-16
I'm on karmic and intel has gotten a lot more stable. Of course you have to live with regressions in other things, but the intel drivers feel a lot better in karmic.

---

### Post by HotShotDJ on 2009-07-17
There are SEVERAL fixes for the problem with Intel video cards in Jaunty. Before spending money on new video cards (not an option for your laptop), or changing to a different version of Ubuntu, or (gasp!) downgrading to Windows, why not try one of them?  Here is the one that worked perfectly for me: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

