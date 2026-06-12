---
title: "Upgraded from 12.04 to 12.10, &quot;failed to idle channel 1&quot; error"
date: 2012-10-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by HolyMythos on 2012-10-03
So stupid me decided to update from 12.04 to 12.10 Beta-2 because I figured that my luck had changed when dealing with OS upgrades (I've had a data-ruining problem with every OS upgrade since Windows 95).

I updated to 12.10 Beta-2 through the Update Manager in 12.04. After going through the entire installation and the final "restart the computer" step I was greeted to a lovely error screen. The screen has a bunch of numbers (sorry, I'm not tech savvy enough to know how to retrieve an error report) and the lines "failed to idle channel 1", followed by a couple seconds of a frozen screen, followed by another line with "PFIFO playlist failed" (may not be exact wording but definitely PFIFO playlist).

I've googled (through my phone) to people saying that adding "nomodeset" to the GRUB loader will load the OS. And it did... somewhat. I got my desktop loaded, but with no sidebar or topbar, and only my background and desktop icons. Clicking on anything makes me send an error report, which makes me send an error report for sending the error report because it can't send the original error report. Somehow I got Firefox working and got on here to post the problem.

I know the problem has to do with my graphics card (nVidia GeForce GTX560 Ti) but the "nomodeset" workaround is worthless in helping me fix the problem. I can't access any windows or a terminal and I have no idea how Firefox even started (I think it had something to do with the failed bug reports).

Any help on how to fix this would be wonderful. Even if it were to go back to 12.04. I'm a complete newbie when it comes to Ubuntu. I just want my computer to work correctly again x.X

---

### Post by dino99 on 2012-10-03
i know that update-manager is the ubuntu default choice; but hey its so buggy that synaptic is a way better choice.

Using nomodeset on the boot line is also a bad idea, simply remove "splash" and then : sudo update-grub

Even if you are not a techy, its always a good idea to glance at your logs: /home/youruser/.xsession-errors (ctrl+h to unhide it) and into /var/log/ to find usefull warnings/errors.

And your data is safe if your /home is on a separate partition (and you does not reformat it indeed when reinstalling a distro)

---

### Post by HolyMythos on 2012-10-03
Removing splash instead of adding nomodeset doesn't solve the problem unfortunately. It works for a split second before displaying the same errors again. The only way I can get Ubuntu to boot properly is to delete nomodeset but even then it loads with no top bar or sidebar so I cannot navigate anything. If there was a terminal code to restore the topbar and side bar it would make the computer useable (albeit somewhat annoying) until I figured out how to fix the problem.

---

### Post by dino99 on 2012-10-03
As i understand, this system might have some old settings left behind the dist-upgrade(s) made. 

You can rename (or delete) those folders into /home: .local , .gnome2, .config, .gconf (ctrl+h to unhide them)
Then logout/in, they will be cleanly rebuilt (but without your custom settings as its a reset)

Otherwise when your are logged you can reset the desktop (gnome, unity, GS) via a terminal: unity --reset , gnome --replace , gnome-shell --replace , ...

---

### Post by HolyMythos on 2012-10-03
In the .local folder from home there's only one folder, Splash, and no other folders (hidden or unhidden). Also, running the code "unit --reset" gives the output "ERROR: the reset option is now deprecated" (which I have no idea what that means). Any other codes you gave "gnome: command not found" and "gnome-shell: command not found".

---

### Post by dino99 on 2012-10-03
are you using ubuntu ? or xubuntu/kubuntu/else ? how have you made the installation ?

---

### Post by HolyMythos on 2012-10-03
Ubuntu 12.10 is what I'm using now. I built the computer in June/July and put Ubuntu 12.04 on it from a LiveCD. Then, yesterday, I used the Update Manager to upgrade to 12.10 Beta-2. It went through the entire installation process and when I had to restart the computer is when I got the error.

---

### Post by HolyMythos on 2012-10-03
When I type "unity" into terminal I get the following (don't know if it helps)
> 
compiz (core) - Info: Loading plugin: core
unity-panel-service: no process found
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Starting plugin: opengl
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Error: Plugin initScreen failed: opengl
compiz (core) - Error: Failed to start plugin: opengl
compiz (core) - Info: Unloading plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: wall
compiz (core) - Error: Failed to start plugin: wall
compiz (core) - Info: Unloading plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: animation
compiz (core) - Error: Failed to start plugin: animation
compiz (core) - Info: Unloading plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: fade
compiz (core) - Error: Failed to start plugin: fade
compiz (core) - Info: Unloading plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: unitymtgrabhandles
compiz (core) - Error: Failed to start plugin: unitymtgrabhandles
compiz (core) - Info: Unloading plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Error: Plugin 'opengl' not loaded.

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: scale
compiz (core) - Error: Failed to start plugin: scale
compiz (core) - Info: Unloading plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: expo
compiz (core) - Error: Failed to start plugin: expo
compiz (core) - Info: Unloading plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: ezoom
compiz (core) - Error: Failed to start plugin: ezoom
compiz (core) - Info: Unloading plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: unityshell
compiz (core) - Error: Failed to start plugin: unityshell
compiz (core) - Info: Unloading plugin: unityshell
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Stopping plugin: workarounds
compiz (core) - Info: Unloading plugin: workarounds
compiz (core) - Info: Stopping plugin: gnomecompat
compiz (core) - Info: Unloading plugin: gnomecompat
compiz (core) - Info: Stopping plugin: session
compiz (core) - Info: Unloading plugin: session
compiz (core) - Info: Stopping plugin: imgpng
compiz (core) - Info: Unloading plugin: imgpng
compiz (core) - Info: Stopping plugin: regex
compiz (core) - Info: Unloading plugin: regex
compiz (core) - Info: Stopping plugin: grid
compiz (core) - Info: Unloading plugin: grid
compiz (core) - Info: Stopping plugin: move
compiz (core) - Info: Unloading plugin: move
compiz (core) - Info: Stopping plugin: place
compiz (core) - Info: Unloading plugin: place
compiz (core) - Info: Stopping plugin: resize
compiz (core) - Info: Unloading plugin: resize
compiz (core) - Info: Stopping plugin: mousepoll
compiz (core) - Info: Unloading plugin: mousepoll
compiz (core) - Info: Stopping plugin: snap
compiz (core) - Info: Unloading plugin: snap
compiz (core) - Info: Stopping plugin: vpswitch
compiz (core) - Info: Unloading plugin: vpswitch
compiz (core) - Info: Stopping plugin: decor
compiz (core) - Info: Unloading plugin: decor
compiz (core) - Info: Stopping plugin: compiztoolbox
compiz (core) - Info: Unloading plugin: compiztoolbox
compiz (core) - Info: Stopping plugin: composite
compiz (core) - Info: Unloading plugin: composite
compiz (core) - Info: Stopping plugin: ccp
compiz (core) - Info: Unloading plugin: ccp
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core

(process:2245): GLib-WARNING **: /build/buildd/glib2.0-2.34.0/./glib/gmain.c:1817: ref_count == 0, but source was still attached to a context!
Segmentation fault (core dumped)

Also, when I startup, these are the errors that I receive:

> 
(    20.845939) (drm) nouveau 0000:01:00.0: GPU lockup - switching to software fbcon
(    56.895124) (drm) nouveau 0000:01:00.0: Failed to idle channel 1.
(    60.892060) (drm) nouveau 0000:01:00.0: PFIFO - playlist update failed

#At this point the screen freezes, flashes black, comes back up for a few seconds then puts out

(  100.396145) (drm) nouveau 0000:01:00.0 Failed to idle channel 1.
(  112.393231) (drm) nouveau 0000:01:00.0 PFIFO - playlist update failed

It then repeats the last two lines over and over with different leading numbers.

---

### Post by grahammechanical on 2012-10-03
Do you get a Grub Menu? If not then note this comment


> Hidden Menu Operations Not Expected (Abnormal):

The user may be able to display the menu in one or more of the following ways:

Holding down the SHIFT key early in the boot process until the menu displays.

GRUB 2 searches for a depressed SHIFT key signal during boot. If the key is pressed or GRUB 2 cannot determine the status of the key, the menu is displayed.

Pressing the ESC key during a 3 second window as GRUB 2 runs.

From this link

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

When you get to the Grub menu can select recovery mode. And then Resume. I sometimes find that way will get me to a login screen and maybe a desktop. If you get to a desktop and a terminal you can try these commands

```
sudo apt-get install dconf-tools
```

```
dconf reset -f /org/compiz
```

```
setsid unity
```

That should give you the desktop you are looking for. I have been assured that those commands will reset Compiz and re-start Unity in 12.10

You need a proprietary video driver. In 12.10 we do not have the Additional Drivers utility anymore. So, go to System Settings>Software Sources and at the Ubuntu Software tab tick the box marked 'Proprietary drivers for devices (restricted).' You may then need to open the Additional Drivers tab and select a driver to use. It should download and install.

I get the Failed to idle channel message on a 12.10 install where I use the Nouveau open source driver. It stops me getting to a log in screen. Are you set to automatically log in? But if I can get to a log in screen by using nomodeset I can usually get to a destop. Nouveau works fine after that on my hardware but perhaps not on yours.

I also want to add that I was able use 11.10 from beta 2 and 12.04 from Alpha 1 but with 12.10 from Alpha 2 through and beyond beta 2 there have been issues with video and getting to a login screen and a desktop. I am not sure that they are resolved even now.

Regards.

---

### Post by WorLord on 2012-10-03
Same exact video card, same exact problem.  Nouveau simply doesn't work (took splash out of the grub config).  

Only the nVidia binary blobs work.

---

### Post by effenberg0x0 on 2012-10-03
"failed to idle channel 1" is a Nouveau-specific string, as you can see via Google.

> compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Starting plugin: opengl
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Error: Plugin initScreen failed: opengl
compiz (core) - Error: Failed to start plugin: opengl
compiz (core) - Info: Unloading plugin: opengl

Therefore no composite/OpenGL support - No Unity, as expected.

IMO the best option is to download and install Nvidia using the proprietary/binary installer from Nvidia website. Luckily it will blacklist nouveau for you. It it doesn't, you have to do it manually in /etc/modprobe.d/

This should get you going: [http://ubuntuforums.org/showpost.php?p=12235014&postcount=19](http://ubuntuforums.org/showpost.php?p=12235014&postcount=19)

Regards,
Effenberg

---

### Post by HolyMythos on 2012-10-03
> **grahammechanical said:**
> Do you get a Grub Menu? If not then note this comment
 
 
 
 
From this link
 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
 
When you get to the Grub menu can select recovery mode. And then Resume. I sometimes find that way will get me to a login screen and maybe a desktop. If you get to a desktop and a terminal you can try these commands
 
```
sudo apt-get install dconf-tools
```
 
```
dconf reset -f /org/compiz
```
 
```
setsid unity
```
 
That should give you the desktop you are looking for. I have been assured that those commands will reset Compiz and re-start Unity in 12.10
 
You need a proprietary video driver. In 12.10 we do not have the Additional Drivers utility anymore. So, go to System Settings>Software Sources and at the Ubuntu Software tab tick the box marked 'Proprietary drivers for devices (restricted).' You may then need to open the Additional Drivers tab and select a driver to use. It should download and install.
 
I get the Failed to idle channel message on a 12.10 install where I use the Nouveau open source driver. It stops me getting to a log in screen. Are you set to automatically log in? But if I can get to a log in screen by using nomodeset I can usually get to a destop. Nouveau works fine after that on my hardware but perhaps not on yours.
 
I also want to add that I was able use 11.10 from beta 2 and 12.04 from Alpha 1 but with 12.10 from Alpha 2 through and beyond beta 2 there have been issues with video and getting to a login screen and a desktop. I am not sure that they are resolved even now.
 
Regards.
 
I have to use SHIFT to get into Grub, but yes, it does appear. Unfortunately I'm at work right now so I'll try to bring up Unity with the codes given when I get home. I am not set to automatically log in. "nomodeset" does get my to login just not with Unity, and without Unity I cant get to any of the menus needed to try and fix the problem. Hopefully, with those codes, I can get unity to load.
 
The one question I do have is that if I do the System Settings>Software Sources process to download the drivers, will it fix the boot problem? I've been manually entering Grub and then editing in "nomodeset" every boot because using "sudo update-grub" does not save the changes (adding nomodeset) to Grub. The only thing I can think of is that I'm not using the "sudo update-grub" code correctly. Hitting Shift at the right time during startup is somewhat of a pain since the time between the motherboard boot screen and the nouveau error is tenths of a second.
 
All I want to be able to do is have Ubuntu load correctly from power-on :P
 
> **effenberg0x0 said:**
> "failed to idle channel 1" is a Nouveau-specific string, as you can see via Google.
 
 
 
Therefore no composite/OpenGL support - No Unity, as expected.
 
IMO the best option is to download and install Nvidia using the proprietary/binary installer from Nvidia website. Luckily it will blacklist nouveau for you. It it doesn't, you have to do it manually in /etc/modprobe.d/
 
This should get you going: [http://ubuntuforums.org/showpost.php?p=12235014&postcount=19](http://ubuntuforums.org/showpost.php?p=12235014&postcount=19)
 
Regards,
Effenberg
 
Will updating the drivers through the Ubuntu Software Sources process listed in the above quoted post do the same as this? I'm very, very inexperienced when it comes to drivers and the like so I honestly have no clue if one thing is related to another or not. It just seemed like what was said in the other qutoed post essentially the same as what you were suggesting.
 
Either way, thank you both of you. Hopefully it'll work when I get home.

---

### Post by grahammechanical on 2012-10-04
It is my understanding that the video driver will kick in early in the boot process. So, that by the time you get to the log in screen you should be using the video driver.

Once you install/activate the proprietary driver things should be fine. You can activate the driver either way. By using Software Sources or the command-line which may be necessary if you cannot get to the desktop.

Regards.

---

### Post by dino99 on 2012-10-04
```
( 100.396145) (drm) nouveau 0000:01:00.0 Failed to idle channel 1.
( 112.393231) (drm) nouveau 0000:01:00.0 PFIFO - playlist update failed
```

into a terminal (ctrl+t):

sudo apt-get install --reinstall libdrm-nouveau1a
sudo apt-get install --reinstall libdrm-nouveau2

---

### Post by HolyMythos on 2012-10-04
When trying to reinstall and start unity when using the terminal codes given in post 9 I get the same message that I posted in Post 8; [http://ubuntuforums.org/showpost.php?p=12275740&postcount=8](http://ubuntuforums.org/showpost.php?p=12275740&postcount=8)

Unity tries to start but then crashes. This means I cannot go into the Software Sources menu to download the drivers. Someone said that I could use the command line to get the drivers, what would be the code that I would use to get said drivers?

---

### Post by HolyMythos on 2012-10-04
[B]Fixed the problem!

[/B]So when trying to download the drivers from the GPU from the nVidia website, I went to a white-screen where it then crashed (the driver update). After it crashed it opened up the Software Center (thank god) and I could navigate to the Software Sources tab. I switched to a proprietary driver. After the reboot everything worked as normal (I get a ten second freeze with screen tearing on login but it goes away after that).

So, I had to;

*Hold SHIFT after the motherboard screen on startup to get GRUB to appear
*Edit the Ubuntu line to add "nomodeset" without quotes before "Quiet splash" on one of the lines
*Startup Ubuntu
*Somehow get to the Software Center to get to the Software Sources tab
*Switch to a proprietary driver

Fixed. Thank god.

---

