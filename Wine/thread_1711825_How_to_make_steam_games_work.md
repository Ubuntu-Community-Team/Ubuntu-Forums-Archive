---
title: "How to make steam games work?"
date: 2011-03-21
forum: Wine
---

### Post by mcavoybn on 2011-03-21
I installed team fortress 2 and steam into wine ,and now the game refuses to work. I installed it using this tutorial: 

[http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/]("http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/")

Everything worked great, steam runs fine, and everything goes just as it should, except when I try to start the game. I click the 'Play' icon under Team Fortress 2, then the 'Preparing Team Fortress 2' window pops up, goes away and then NOTHING HAPPENS.

Is this a problem with Wine or should I look elsewhere for a solution?

Thank You

---

### Post by Zenmij on 2011-03-21
I have this same problem. Try typing this in a terminal, and paste what happens when you try to launch a game
```

env WINEPREFIX="/home/YOUR USERNAME/.wine" wine "C:\Program Files\Steam\Steam.exe"

```

For instance, I get:

```
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  128 (GLX)
  Minor opcode of failed request:  4 (X_GLXDestroyContext)
  Serial number of failed request:  1142
  Current serial number in output stream:  1142

```

---

### Post by cogadh on 2011-03-21
That's a video card/driver error. What do you have for video hardware?

---

### Post by mcavoybn on 2011-03-21
@Zenmij: I ran the code, it opened Steam, and then tried running the game and the same problem happened. The first window to start the game popped up, and then nothing happens. I don't get an error message or anything.

@cogadh: How would I go about finding that info? I can't seem to find anywhere that describes any drivers/hardware. I am on a Toshiba laptop, which is hooked up to a vizio led tv/monitor. (Sorry, I am fairly new to linux)

---

### Post by gamblor01 on 2011-03-21
> **mcavoybn said:**
> How would I go about finding that info? I can't seem to find anywhere that describes any drivers/hardware. I am on a Toshiba laptop, which is hooked up to a vizio led tv/monitor. (Sorry, I am fairly new to linux)

First things first, try opening the terminal and running the command **lspci**.  That will list all of the PCI buses and devices in your system.  Generally there will be one for VGA which will show us which video card your laptop has (Intel, Nvidia, ATI, etc.).  From there we can figure out if you have the appropriate/best video driver installed.

I have been running Steam games for a long time (as far back as Ubuntu 7.10) via Wine so I know it works.  Some other questions that might be useful:

- What version of wine are you running?  (I think something like **wine -version** or **wine --version** will tell you)

- Have you tweaked anything in Wine or Steam at all?  For example, I tried in the past to copy over native DLL files from a Windows installation to get DirectX 9.0 working and I finally discovered that it just screwed everything up.  Or have you passed any additional options to the game in Steam?  For example, I used to change the heapsize and force DirectX 8.1.  You can do this by right-clicking the game in the Steam menu and changing options, or you can just invoke it from the command line and pass in the options directly (substitute your username and password for %user% and %pw%):

wine "C:\Program Files\Steam\steam.exe" -login %user% %pw% -applaunch 440 -heapsize 1048576 -dxlevel 81



You might also look at posting on the winehq.org forums.  Many of the wine developers frequently visit that forum and can be incredibly helpful!

---

### Post by mcavoybn on 2011-03-22
> First things first, try opening the terminal and running the command lspci. That will list all of the PCI buses and devices in your system. Generally there will be one for VGA which will show us which video card your laptop has (Intel, Nvidia, ATI, etc.). From there we can figure out if you have the appropriate/best video driver installed.

Ran lspci, da output:
PCI bridge: Advanced Micro Devices [AMD] RS78- PCI to PCI bridge (PCIE port 0) (and the same thing for ports 1 & 2)
SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
Don't think the USB Controllers are all that important...
SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
Audio device: ATI Technologies Inc SB (Intel HDA)
ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
Host bridge: blahblahblah 
VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]

> - What version of wine are you running? (I think something like wine -version or wine --version will tell you)

wine 1.2.2

> - Have you tweaked anything in Wine or Steam at all? For example, I tried in the past to copy over native DLL files from a Windows installation to get DirectX 9.0 working and I finally discovered that it just screwed everything up. Or have you passed any additional options to the game in Steam? For example, I used to change the heapsize and force DirectX 8.1. You can do this by right-clicking the game in the Steam menu and changing options, or you can just invoke it from the command line and pass in the options directly (substitute your username and password for %user% and %pw%):


Not that I am aware of. I just started using Ubuntu again, after Windows 7 was killed on my computer, so nothing has been tampered with beyond something that another program might have done. Steam/TF2 were installed hardly 24 hours ago, so I don't think anything could have been done to them, and I definitely have not tampered with anything manually.

---

### Post by gamblor01 on 2011-03-22
Cool...good to know you haven't tweaked anything.  It looks like you have an ATI card, and it also looks like you're running Ubuntu 10.10, which should automatically detect the ATI card and prompt you to install the drivers (specifically, the jockey-gtk program should have fired up and told you about "restricted drivers").

Click on System > Administration > Additional Drivers (and give it a minute or so to scan your system).  It should open a window that gives you an option for the ATI drivers (I think it's called flgrx or something like that?  I'm not positive -- I always used Nvidia cards).  Anyway, make sure that the one which is "recommended" is selected.  If not, check it, apply the changes, and follow the instructions.  You probably have to restart (or at least logout/login to get a new X session).

If you have already done that then chances are that you are already using the best driver available.  You can check the driver with the **lsmod** command (somewhere in that output will be an ATI or flgrx line) but jockey should install the appropriate driver if you use the instructions from the previous paragraph.

If you have that driver and things still aren't working then I would suggest firing up steam.exe with the WINEDEBUG=+all switch.  It would be best to save this output to a script file so do something like this in terminal:

```

$ script steam.txt
$ WINEDEBUG=+all wine "C:\Program Files\Steam\steam.exe"

(wait until it crashes and then you can exit)

$ exit

```

After you type exit it will save all of the output to the file named steam.txt.  Then you can post that on the winehq forums and hopefully one of the developers there can get you squared away.  You can try and post it here but I'm definitely not the best with debugging wine output.  Maybe someone else is but the wine forums would almost certainly be able to help you.

---

### Post by mcavoybn on 2011-03-22
Ok.. this is VERY embarrassing, but last night (before I read your new reply) I installed the ati catalyst driver manually by downloading the x86 linux driver from the ati website. I installed it, and figured that it would all go down smoothly, but it didn't.

My wobbly windows weren't working (SHUT. DOWN. EVERYTHING.) and the desktop switcher cube, and just about everything from the CompizConfig settings refused to work the way it should. Also, alot of default Ubuntu GUI things weren't working right, so I knew something went horribly wrong with the new driver I installed.

This afternoon I read your post (gamblor01) and did everything you suggested. The right drivers were installed, everything was checked and good and the way it should be, but still nothing worked. I decided I must delete one of the instances of the drivers I installed.

This is where everything went wrong. I deleted it by typing:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

It ran, and I rebooted, and now all I get is some sort of Bash/Terminal prompt on startup. It asks me for my username and my password, but there is no GUI/GNOME in sight.

I tried reinstalling the drivers from the low-graphics recovery mode, and it all worked 100% fine, but now I have 2 catalyst managers in my system>preferences, and activating the driver through system>administration>additional drivers, does not work an error message pops up and says I need to look at /var/log/jockey.log, which I couldn't make any sense of.

Please, help. Where do i go?/What do i do? 
Can I not activate the drivers in recovery mode? That just seems silly.

---

### Post by Camoy on 2011-03-23
I have the same issue, here is the information gamblor01 asked for:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

I'm also running wine 1.2.2 on Ubuntu 10.10.

---

### Post by gamblor01 on 2011-03-24
> **mcavoybn said:**
> Ok.. this is VERY embarrassing, but last night (before I read your new reply) I installed the ati catalyst driver manually by downloading the x86 linux driver from the ati website. I installed it, and figured that it would all go down smoothly, but it didn't.

My wobbly windows weren't working (SHUT. DOWN. EVERYTHING.) and the desktop switcher cube, and just about everything from the CompizConfig settings refused to work the way it should. Also, alot of default Ubuntu GUI things weren't working right, so I knew something went horribly wrong with the new driver I installed.

This afternoon I read your post (gamblor01) and did everything you suggested. The right drivers were installed, everything was checked and good and the way it should be, but still nothing worked. I decided I must delete one of the instances of the drivers I installed.

This is where everything went wrong. I deleted it by typing:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

It ran, and I rebooted, and now all I get is some sort of Bash/Terminal prompt on startup. It asks me for my username and my password, but there is no GUI/GNOME in sight.

I tried reinstalling the drivers from the low-graphics recovery mode, and it all worked 100% fine, but now I have 2 catalyst managers in my system>preferences, and activating the driver through system>administration>additional drivers, does not work an error message pops up and says I need to look at /var/log/jockey.log, which I couldn't make any sense of.

Please, help. Where do i go?/What do i do? 
Can I not activate the drivers in recovery mode? That just seems silly.

It happens -- don't worry.  Most likely it dropped you to a shell because the /etc/X11/xorg.conf file was incorrect.  It could also be the case that the driver identified inside of xorg.conf (probably fglrx) was no longer available to the machine.  In that case you would need to specify some other, default driver.  I'm honestly not sure what the default driver is when Ubuntu is first installed -- maybe vesa?

If you want to post the contents of your xorg.conf file and the jockey.log file we can take a look and see if there are any glaring issues.

In regard to the two catalyst manager, I would right-click on the Applications/Places/System menu (make sure it's closed first) and then hit edit menus.  From here you should be able to dive down into the menu for System > Preferences.  Then click on each of the catalyst options and select Properties.  It should tell you where they are pointing to -- which may even be the exact same location (in which case you can delete one because they are two shortcuts pointing to the exact same location).

Ultimately I think you guys will be better of posting on the winehq forums since, well, you are having problems with wine and not Ubuntu specifically.  Wine is a package you can install in Ubuntu, sure, but the folks at winehq.org are the ones that are actually developing that application and therefore will probably be of the most help.

---

