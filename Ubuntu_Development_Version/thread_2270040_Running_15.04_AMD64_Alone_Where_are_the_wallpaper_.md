---
title: "Running 15.04 AMD64 Alone: Where are the wallpaper updates?"
date: 2015-03-19
forum: Ubuntu Development Version
---

### Post by MikeMecanic on 2015-03-19
Just receive AN UPDATE with wallpaper 15.04 and there is no change.  Where are they?  Read in the forum that it's the 14.10 wallpaper that are include in the 15.04 package.  

So far, it seems to run faster: boot up, shut down and in the desktop environment.  Network connection is faster and it's also faster to close the connection: instantly.  The installation was not easy at all: 5 attempts with an ISO DVD.  See my last post: Where to start.  **Run smoother, stable on Opera [COLOR=#000000][FONT=Arial]28.0.1750.48 / [/FONT][/COLOR][COLOR=#000000][FONT=Arial] [/FONT][/COLOR]**[COLOR=#000000][FONT=Arial]**Ubuntu Vivid Vervet (development branch) (x86_64; Unity)**[/FONT][/COLOR]** .**  Terminal is now available on a desktop right click: very good modification.  There is a modification in the network setup that I don't get?  **The DCB Setup...**

Post-installation was O.K. except maybe for the printer and the anti-virus ClamTK.  Will try to re-install ClamTK because maybe I made a false command:  The COMPUTER Folder is not available for scanning. not reachable.  The Gufw Firewall is set for the 15.04 version and was able to import profile (202 rules) from my last installation: 14.04.2LTS.  I ddin't test it yet

Bug number one:  Empty trash on right click on the trash icon (Bottom Left):  Two windows open: The regular pop-up asking empty all items in the trash (isn't it enough?) and a second window (not really needed). the HOME FOLDER.  Is it from the same guy that decide (2 weeks ago) to enlarge the software updater very cute little window:  Pretty distressing.  The little windows design looks better in 15.04 and run faster.  Same apply for the Network Tools Application: scan smoother and smaller.  Sharp design.

Bug number 2 (Post-installation):  HP Doctor works fine but the 15.04 version is not listed.  Knowing that i'm running a beta version, there is no rush for that one:)

For the rest, time will tell.  **There is no bug on my machine: i3 Chipset / 4gig of ram**.  Will come back to provide more feedback...

All the best,

---

### Post by motang on 2015-03-19
I got the new wallpapers, have you tried running apt-get update and apt-get upgrade, if that doesn't work apt-get dist-upgrade in the terminal?

---

### Post by MikeMecanic on 2015-03-19
No, not working.  I extract directly in the desktop but there the same that I have in* change Desktop **Background*.  No modification since I installed 15.04 yesterday.  The upgrade was this afternoon...  You should replace XP by Windows 8 because it's also an obsolete O/S push away by 12.04 LTS.

---

### Post by motang on 2015-03-19
Odd, have you checked all the boxes in Software and Updates (maybe it is in the pre-release).

Ha, you are right I should change it from XP. I haven't changed my signature since making this account back in 06.

---

### Post by grahammechanical on 2015-03-19
Vivid Vervet, to give 15.04 its development code name, is built on the 14.10 code base. So, it starts out looking very much like 14.10 including the wallpapers but over time the logos and stuff change to those of 15.04.

My version of vivid that I have been running since the start of development got the new vivid wallpapers last week. Mind you I do have the proposed repository enabled and that means we get stuff a bit early than if the proposed repository was not enabled. Stuff in proposed can break things. Although I would expect the latest daily images to have the new wallpapers.

I can confirm the bug with the Empty Trash producing a confirmation dialog and opening nautilus at the home folder. Unintended consequence, I expect. Perhaps it is the new way to launch the File Manager. :)

I noticed something today, nm-tools is not included anymore. The terminal says to get it I must install network manager but it is installed and when I try to install network manager I am told that I already have the latest version. So, no more nm-tools. So, sad.

Regards.

---

### Post by cariboo on 2015-03-19
On my system it looks like the Vivid wallpaper was installed on March 11th, the contents of /usr/share/backgrounds should look something like the attached screenshot.

**Edit:** One thing I always wondered about, is why each new background is always called warty-final-ubuntu.png

---

### Post by MikeMecanic on 2015-03-19
**[COLOR=#ff0000]T[B]hat's what I get.  But The update didn't change the pictures in the wallpaper file**:[/COLOR][/B]

**hp@hp-610-1130f:~$ cd /usr/share/backgrounds**
**hp@hp-610-1130f:/usr/share/backgrounds$ ls -l**
**total 19192**
**-rw-r--r-- 1 root root 1848512 Mar 19 09:11 150305-cinqAA_by_Pierre_Cante.jpg**
**-rw-r--r-- 1 root root 1508619 Mar 19 09:11 Cedar_Wax_Wing_by_Raymond_Lavoie.jpg**
**-rw-r--r-- 1 root root 2134733 Mar 19 09:11 Christmas_Lights_by_RaDu_GaLaN.jpg**
**drwxr-xr-x 2 root root    4096 Mar 19 14:25 contest**
**-rw-r--r-- 1 root root  703744 Mar 19 09:11 Euphoria!_by_Tomasino.cz.jpg**
**-rw-r--r-- 1 root root 1235913 Mar 19 09:11 Oyster_Catcher_in_the_Rocks_by_Raymond_Lavoie.jpg**
**-rw-r--r-- 1 root root 1773391 Mar 19 09:11 Polka_Dots_and_Moonbeams_by_SirPecanGum.jpg**
**-rw-r--r-- 1 root root 1608442 Mar 19 09:11 Primavera_by_Vivian_Morales.jpg**
**-rw-r--r-- 1 root root  211925 Mar 19 09:28 Suru_Wallpaper_Desktop_4096x2304_Gray.png**
**-rw-r--r-- 1 root root 1211371 Mar 19 09:11 Tenerife_Roques_de_Anaga_by_Frederik_Schulz.jpg**
**-rw-r--r-- 1 root root 1320045 Mar 19 09:11 Tesla_by_Tomasino.cz.jpg**
**-rw-r--r-- 1 root root 2326987 Mar 19 09:11 Traviny_by_Tomasino.cz.jpg**
**-rw-r--r-- 1 root root 3740503 Mar 19 18:35 warty-final-ubuntu.png**
**hp@hp-610-1130f:/usr/share/backgrounds$ **

---

