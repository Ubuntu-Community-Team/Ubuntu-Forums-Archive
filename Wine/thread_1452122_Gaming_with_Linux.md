---
title: "Gaming with Linux"
date: 2010-04-11
forum: Wine
---

### Post by Shoie13 on 2010-04-11
Recently decided to attempt to move to Ubuntu as the primary OS due to problems with W7, however, the games collection was the major issue. I've installed Steam and EVE with no problems, however, upon testing Portal and EVE online, major graphical bugs have arrived.

With EVE, I was able to update and login successfully, but the whole OS locked up at the station and I couldn't do anything (granted I don't know how to kill a problematic process like this or restart X or whatever). With Portal, I got to the main menu before flashing static boxes took over the screen and I had to power off the computer again. Now, EVE isn't even working even after a reinstall. I'm using wine 1.1.42 with wine-doors, proprietary ATI driver and these specs:

MOBO: DFI LANPARTY DK 790GX-M2RS 
GPU : Radeon HD 4870 512MB 
CPU : AMD Phenom 9850 2.5ghz Quad
RAM : Kingston 4GB(2x2GB) DDR2
OS : Ubuntu 9.10 64-bit Desktop, Windows Vista Ultimate 64-bit

---

### Post by efikkan on 2010-04-11
Wich driver do you use?

To kill a process:
* Press Ctrl + Alt + F1
* Login
* Enter "top"
* Find the PID of the process
* press q to quit top
* Enter "kill <pid>", where <pid> is the number you found in top
* press Ctrl + Alt + F7 to resume your graphical session

---

### Post by Shoie13 on 2010-04-11
> **efikkan said:**
> Wich driver do you use?


The ATI/AMD proprietary FGLRX driver. Is there more to it than that? And thanks for the information. Wasn't sure how to get back to the graphical session.

---

### Post by efikkan on 2010-04-11
So you are using the driver wich are "bundled" in Ubuntu 9.10, wich displays version 2D driver 8.66.10, Catalyst 2.11 and OpenGL 2.1.9016 in catalyst control center?

I suggest you try a new Catalyst driver from AMD.

---

### Post by Shoie13 on 2010-04-11
Yes, those are the driver numbers I have in the CCC. I will try updating it direct from AMD and see the results.

---

### Post by Shoie13 on 2010-04-11
I've updated the drivers and completely reinstalled EVE again, then applied the patch. I set Wine to emulate a virtual desktop of 1024x768(native 1280x1024). I was able to login to EVE and select a chracter, but the OS locked up upon entering the game and I was unable to switch to the console to kill the process. Now, EVE won't launch again.

---

### Post by efikkan on 2010-04-11
Have you tried to run the games (in wine) in terminal, to see any error messages?

---

### Post by NightwishFan on 2010-04-11
Easy way to kill X is: alt+sysrq+k

---

### Post by Shoie13 on 2010-04-11
> **efikkan said:**
> Have you tried to run the games (in wine) in terminal, to see any error messages?

shoie13@shoie13-desktop:~$ wine "C:\Program Files\CCP\EVE\eve.exe" 
err: ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err: ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:heap:HeapSetInformation 0x7c9000 0 0x33fc6c 4
fixme:win:EnumDisplayDevicesW ((null),0,0x338d7c,0x00000000), stub!
shoie13@shoie13-desktop:~$

---

### Post by Shoie13 on 2010-04-11
For whatever reason, following the instructions here [http://ubuntuforums.org/showpost.php?p=8050178&postcount=4](http://ubuntuforums.org/showpost.php?p=8050178&postcount=4) allowed EVE to start up again, however, it is still locking up the entire system forcing a poweroff once the character is selected and it's about to enter the actual game after login.

---

### Post by VinisLentoje on 2010-04-12
Maybe it won't be much of a help, but how about trying to run the game on a different X session? There is a small chance that it would fix the problem.

here is a sh script to run a game on a different X session. You will need to edit it a little.
(I did not write this script, I took it from the web a long time ago, and do not remember from where exactly, so I am not able to point You to it's original location. Well, slightly edited the comments on it.)

```
#!/bin/sh
# This script disables all the text output for Wine
# debugging for improved performace.
# uncomment if launching from console session
# sudo /etc/init.d/gdm stop
# KDE use this instead
# sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
# (you do need to take that part out, as you are using an ATI card,
# but I left it for you if you will ever need it for an nvidia card)
sudo X :3 -ac & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd "/this/is/an/example/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
# (the "WINEDEBUG=-all" part disables the console output,
# so, if you want to log it AND do it while running a
# different X server, remove this part)
DISPLAY=:3 WINEDEBUG=-all wine "C:\this\is\also\an\example.exe"
```

Also, if You would provide the console output it would be way easier to help You. But since the whole system hangs up, you will need a tool that would dump the output into a file, and do it in "real time".

And, problems with power supply can cause total system hangups when graphics-intensive games are run. So You should check Your power supply and see if it is not the cause. By the way, one of my friends had a similar problem and it turned out that it was because of the power supply and and defective mainboard at the same time.

---

### Post by DrMelon on 2010-04-12
Note that any Source games that use the Orange Box Engine (portal, tf2, HL2:EP2) will only run if you right-click on the game in steam, click properties, and then "Set Launch Options...".

In the launch options box, type this: "-dxlevel 81", and hit OK.

Your graphics won't be quite as impressive as they were on Windows, but it'll run.

Since Valve are bringing all their games to Mac (and therefore using OpenGL) we may see full Linux compatibility soon.

---

### Post by darthmob on 2010-04-12
In my opinion Wine simply isn't worth the time and effort you have to put into it. If you want to play Windows games install Windows in dual boot.

You may have to put in some time once to fix the problems with Win7 but with Wine you get it for every game and you will still only have a mediocre experience (unless you are running games which are 10+ years old, they sometimes work better than on Windows).

---

### Post by Shoie13 on 2010-04-12
> **VinisLentoje said:**
> Maybe it won't be much of a help, but how about trying to run the game on a different X session? There is a small chance that it would fix the problem.
[snip]
This didn't resolve the problem. :-/

> **VinisLentoje said:**
> 
Also, if You would provide the console output it would be way easier to help You. But since the whole system hangs up, you will need a tool that would dump the output into a file, and do it in "real time".
Is there a way or program I could use to do this so I can get the output?

> **VinisLentoje said:**
> 
And, problems with power supply can cause total system hangups when graphics-intensive games are run. So You should check Your power supply and see if it is not the cause. By the way, one of my friends had a similar problem and it turned out that it was because of the power supply and and defective mainboard at the same time.
I doubt that's the problem. PSU is a Corsair CMPSU-750TX 750W, so quality and powerful enough for the equipment. It's also not old or overstressed, and EVE as well as all my other games (new and old alike) run flawlessly at maximum settings under Windows.


> **darthmob said:**
> In my opinion Wine simply isn't worth the time and effort you have to put into it. If you want to play Windows games install Windows in dual boot.

You may have to put in some time once to fix the problems with Win7 but with Wine you get it for every game and you will still only have a mediocre experience (unless you are running games which are 10+ years old, they sometimes work better than on Windows).

I have Windows on dualboot, but that's pretty much simply a fallback plan if I can't get my games to run under Linux. I'm really hoping to get away from Windows dependencies as much as humanly possible.

---

### Post by asdfoo on 2010-04-12
> **Shoie13 said:**
> For whatever reason, following the instructions here [http://ubuntuforums.org/showpost.php?p=8050178&postcount=4](http://ubuntuforums.org/showpost.php?p=8050178&postcount=4) allowed EVE to start up again, however, it is still locking up the entire system forcing a poweroff once the character is selected and it's about to enter the actual game after login.

entire system lockups are due to buggy video drivers.  Unfortunately ATI have a long history of these, I used to experience them all the time with my radeon 9800 pro.  not much you can do except report the problem to ATI.

Other alternative is trying to the free/open source ati drivers, but they aren't quite as feature complete as fglrx.

I since switched to nvidia and I've never had a system lockup in linux.

---

