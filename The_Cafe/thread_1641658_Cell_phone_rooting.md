---
title: "Cell phone rooting"
date: 2010-12-09
forum: The Cafe
---

### Post by 1927Vinton on 2010-12-09
If your cell phone is an HTC ARIA and you want to root it, Internet Web sites suggest you create a UBUNTU LiveCD and then follow the instructions given when the CD program runs. What if UBUNTU is your operating system and you want to root your HTC ARIA? Any suggestions? The UBUNTU LiveCD is for people with Microsoft's operating system.

---

### Post by shobon on 2010-12-09
I have an Aria and I used Unrevoked to root it, then I proceeded to install CyanogenMOD, all went well.

---

### Post by Spr0k3t on 2010-12-09
I don't have an HTC Aria... but the information found on the rooting process should be generally the same.  Running Cyanogenmod here as well with the help of Clockworkmod.

---

### Post by 1927Vinton on 2010-12-13
> **Spr0k3t said:**
> I don't have an HTC Aria... but the information found on the rooting process should be generally the same.  Running Cyanogenmod here as well with the help of Clockworkmod.

Thanks. I got my ATC Aria rooted. Now I am having trouble figuring out how to unlock NAND. Also, I need to back up my ROM image so I can intall CyanogenMOD. Any suggestions?

---

### Post by treesurf on 2010-12-14
The best place to ask about this will be in the xda-developers forum specifically dedicated to the Aria:

[http://forum.xda-developers.com/forumdisplay.php?f=683](http://forum.xda-developers.com/forumdisplay.php?f=683)

---

### Post by HappinessNow on 2010-12-14
> **1927Vinton said:**
> Thanks. I got my ATC Aria rooted. Now I am having trouble figuring out how to unlock NAND. Also, I need to back up my ROM image so I can intall CyanogenMOD. Any suggestions?

I use 'ROM Manager Premium' it does all the wipes and backups you need, great if want to utilize CyanogenMod 6 Nightlies

---

### Post by amitabhishek on 2010-12-14
> **1927Vinton said:**
> Thanks. I got my ATC Aria rooted. Now I am having trouble figuring out how to unlock NAND. Also, I need to back up my ROM image so I can intall CyanogenMOD. Any suggestions?

Just follow these steps:

a)Install Ubuntu

b)Download Unrevoked (Linux version) from their website. Unzip & save on desktop

c)Download[ Cyanogenmod ROM]("http://wiki.cyanogenmod.com/index.php?title=HTC_Aria:_Full_Update_Guide") and Google apps. Save on desktop.

d)Once all downloads are done. Plug your phone via USB and run unrevoked as super user. Unrevoked will remove NAND lock and install clockworkmod in the recovery partition. 

e)Your phone is now rooted & you will see a superuser icon in application menu.

f) Save the Cyanogenmod & Google apps in the root of the SD card and switch off the phone.

g) Start the phone by pressing down volume button and power simultaneously. Now use volume button again to scroll at "recovery" and select it using power button.

h) Clockworkmod recovery ROM will now boot and will give various options:

[IMG]http://img816.imageshack.us/img816/1240/deviceh.png[/IMG]

You can now use trackball/trackpad to highlight and select options. 

i)Scroll to 'backup and restore' and backup your existing ROM important step) by selecting 'Backup'(in the next menu/screen).

j) Come back to the main clockworkmod menu and select 'wipe data/factory reset' and 'wipe cache partition' one after another.
 
j)Come back to the main clockworkmod menu again and select 'install zip from sdcard'.

k)Select Cyanogen zip file and flash it and then flash Google apps in the same way

l)Once done; restart phone and have fun! :)

Ensure the phone is fully charged and don't blame me if your device is bricked :) (though chances are negligible). Though this tut is based on my HTC Desire it will work on Aria too.

---

### Post by slackthumbz on 2010-12-14
I have an n900, to root it I open up an xterm and type root.</smug>

---

### Post by amitabhishek on 2010-12-14
N900 is a great phone and I own one. But here we are talking about flashing & not rooting alone.  Hence few more steps.

---

