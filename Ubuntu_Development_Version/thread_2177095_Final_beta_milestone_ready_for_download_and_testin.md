---
title: "Final beta milestone ready for download and testing."
date: 2013-09-27
forum: Ubuntu Development Version
---

### Post by philinux on 2013-09-27
[http://iloveubuntu.net/ubuntu-1310-final-beta-released-and-available-download](http://iloveubuntu.net/ubuntu-1310-final-beta-released-and-available-download)

Lots of info here too.

[http://www.omgubuntu.co.uk/2013/09/ubuntu-13-10-final-beta-released-download?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2013/09/ubuntu-13-10-final-beta-released-download?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by jerrylamos on 2013-09-27
Lubuntu 13.10 Beta running well here.  Cleanest ubiquity install I've seen in years.  It's on USB SSD.  Acer netbook with external TV monitor.  I'll try ubuntu next on netbook, notebook, tower.  BTW, I boot the .iso directly from SSD.  Someone else can test DVD, network install, USB create disk,  ...  I install a lot so I take the easy quick way out.

Update.  On same hardware, saucy beta ubuntu ubiquity runs a couple seconds and quits.  I've been installing ubuntu saucy on this setup practically every two weeks, no go this time.  Bug 1232182.  I'll try another zsync tomorrow.....

---

### Post by kansasnoob on 2013-09-27
I've only tested Ubuntu, Ubuntu GNOME, and Lubuntu so I can't comment on the other flavors but my results with an Intel Atom CPU 230 @ 1.60GHz w/Intel 82945G/GZ Integrated Graphics are as follows:

Ubuntu Saucy final Beta is largely unusable ..... it takes nearly 5 (yes five) minutes for the dash to launch so you can even open an app not located in the launcher. It takes about 2 minutes even to open an app such as "files" in the launcher. Makes me wonder what the minimum specs are going to be .............. maybe a gazillion GHz CPU with a graphics board the size of the space station ;)

Ubuntu GNOME final Beta is pretty good. I've encountered few problems using it out-of-box :D

Lubuntu final Beta is experiencing a lot of kernel freezes :(

---

### Post by tdockery97 on 2013-09-27
Interesting.  Seems to run very well following one early crash where it froze up for a while.  Is the clock/calendar not supposed to be on the panel by default anymore?  It's not there, and in the system settings everything regarding the clock is dimmed out so cannot be changed.  Anyone else see this behavior?

---

### Post by grahammechanical on 2013-09-27
@tdockery97

If we go to Time and Date in System Settings and open the Clock tab there is a tick box = Show a clock in the menu bar. I think that is what you are looking for.

Regards.

---

### Post by rrnbtter on 2013-09-27
Greetings,

> **kansasnoob said:**
>  Makes me wonder what the minimum specs are going to be .............. maybe a gazillion GHz CPU with a graphics board the size of the space station ;) 

Saucy runs great with my GM45 Intel graphics, 2.18 Celeron, 4G RAM.  I'm leaving Raring on my wife's Atom 1.6Ghz, 2Gig Ram. She is happy with what she has and doesn't want an update. I might just go Jerry's route and run an ISO on it just to see what happens. If I get time to do that I'll report in, but I'm going on vacation Tuesday and probably won't have time till I get back. 

I have personally always considered a System upgrade to be a hardware support issue and didn't really expect retro support until I switched to linux. I get your expections though, most of us Linux users are spoiled with hardware persistance.  When I was supporting Windows just an MS Office upgrade would slow the machine to a crawl. Haven't had that so far with Linux. I do think the time comes when you have to move on and if Raring is the limit for my wife's Atom I will have to let it run it's course and then buy her a new system. That being said, what I have on both machines is perfect and I'm willing to replace both to try-out whats coming around the corner.

---

### Post by JonPaul on 2013-09-27
Tried to upgrade 13.04 to 13.10 from usb image. hung at login to ubuntu one and had to do a hard reset. when I restarted it offered an upgrade from 13.10 to 13.10. None of my apps or themes from 13.04 remained. fortunately home was on separate partition. having put my apps back it seems no slower or faster than 13.04.
 indicator-sysmonitor now has a strange icon... otherwise no problems to speak of.:-k

---

### Post by ventrical on 2013-09-27
I got this thing (saucy-beta) running on one of my older rmachines. A P4M266 with  [AMD/ATI] RV350 [Radeon 9600 Series] with only 128mb ram and 1.2GB MoBo 233MHz ram!!!! And it is even more enhanced that Raring or Precise and I am brining this on from a live session.

  Also those horrible, annoying mutiple-menu bars are gone. Probably just a watermark to see if we are really testing ! :) lol.

  Now for hard install and then unity-system-compositor.

Another phenom .iso .. though I must say i have rarely seen the phenom iso's come out in a beta such as this.

Regards..

---

### Post by craig10x on 2013-09-27
tdockery97: check the tick box in the time/date settings to see if it is properly checked as grahammechanical mentioned...i did notice after doing today's (rather large) amount of updates in my running development of 13.10 and when i restarted, the clock was gone on the panel....so i logged out and back in and it came back again...perhaps there were some updates that caused a little glitch on that...i will watch to see if it continues to do that when i boot up...

---

### Post by screaminj3sus on 2013-09-27
Smart scopes makes the dash ridiculously slow.... if I do something simple like type "terminal" and hit enter, there is like a full 3-4 second delay before anything even happens. I had to turn off online results in the dash which completely brought it back to 13.04 speed (13.04's dash was quick whether or not online results were on), smart scopes seems to be in pretty bad shape for a final beta... This is a fast system too. i5-3210m, 8GB DDR3, 256 GB SSD, intel HD4000.

Also ubuquity wouldn't even launch on either of my computers on the live session. I tried burning another liveusb too using a different stick. it would only launch if I booted directly into "install ubuntu" in the live session clicking on install just does nothing. There's been a bug about this in launchpad reported by someone else for about a week too.

On the installed session I ran into several other annoying issues: mainly the gnome-settings-daemon input "hotplug-command" hook is totally broken, and this hook is important because its the only way to change certain touchpad settings without gnome overriding them. Looks like that bug is assigned though. I ran into the known issue where the "blank screen" option keeps resetting to never.

For the good though: Compiz seems to be in good shape this release, much less buggy. The refined ambiance theme is a massive improvement, and the system has been very stable and crash free (typically I can't use an ubuntu beta without all kinds of random apport popups, but none so far in saucy).

---

### Post by ventrical on 2013-09-27
After one install on older machine it worked well but unity-system compositor would cause flashing and flikerty. I was able to restore back to X by removing unity-system-comp..

  I then tried a nomodeset install and got a VESA dirver (unlike the first which was a Gallium) Now it is like molasses.  This of course is a regression of the hard-installation process because I have suacy on another hdd on the same machine that works great with unity system-comp, ccsm and is very fast.

  It's like the jockeying process does not know what it is doing (again). Have not tried it on my power machines as of yet but it is otherwise very stable in "live" session mode and installs solidly so far.

---

### Post by ventrical on 2013-09-27
... as usual.. a smooth and flawless install with the Sandybridge Desktop.

---

### Post by VMC on 2013-09-27
> **kansasnoob said:**
> I've only tested Ubuntu, Ubuntu GNOME, [s]and Lubuntu so I can't comment on the other flavors but my results with an Intel Atom CPU 230 @ 1.60GHz w/Intel 82945G/GZ Integrated Graphics[/s] are as follows:

Ubuntu Saucy final Beta is largely unusable ..... it takes nearly 5 (yes five) minutes for the dash to launch so you can even open an app not located in the launcher. It takes about 2 minutes even to open an app such as "files" in the launcher. Makes me wonder what the minimum specs are going to be .............. maybe a gazillion GHz CPU with a graphics board the size of the space station ;)

Ubuntu GNOME final Beta is pretty good. I've encountered few problems using it out-of-box :D

[s]Lubuntu final Beta is experiencing a lot of kernel freezes[/s] :(
Testing the day before the beta, I have pretty much the same outcome, also Kubuntu is **flawless**. Using *AMD Athlon(tm) II X2 250 Processor × 2 ,GeForce 6150SE nForce 430/integrated/SSE2.*

Ubuntu Saucy is almost useless. I have downloaded a Quantal kernel, and on the beta I will try that kernel to see if I get improvements on the graphics side. Trying to determine what's up with nvidia. Maybe an oler nouveau will work.

---

### Post by PaulW2U on 2013-09-28
> **VMC said:**
> Testing the day before the beta, I have pretty much the same outcome, also Kubuntu is **flawless**. 

I just wanted to get a 13.10 beta installed on my spare laptop _quickly_ and I had the released Ubuntu, Kubuntu, Lubuntu, Xubuntu and Ubuntu Gnome beta images downloaded and ready to install.

After several attempts to get Ubuntu installed I gave up as the installation process either froze or prompted a reboot which then froze after my laptop was restarted. Kubuntu, as usual, installed first time and without any problems although to be fair to the Ubuntu installer my hard drive had by then already been partitioned and formatted to remove Windows Vista. 

Anyway, I'm now busy updating, installing additional software and customising Kubuntu to match the 13.04 installation on my main laptop. It looks like I'll not bother with Ubuntu 13.10 now and will look at upgrading my Ubuntu 12.04 installation to 14.04 sometime during the next development cycle.

---

### Post by grahammechanical on 2013-09-28
Well, that was a waste of a couple of hours. I am beginning to doubt the wisdom of calling something a beta release just because a date in the calendar has been reached. I make no comment on Ubuntu 13.10 the OS but I cannot recommend the live session image for anything but testing purposes.

Trying to install from the live session desktop failed because the install icon (in Launcher and Dash) failed to activate the Installer. The actual installation worked up to a point. The Ubuntu One login for a returning user does not progress beyond endlessly repeating to validate the users login details. We need to click "login later" to get any further.

On reboot I got past the login screen to a black screen with only the white mouse cursor showing. Rebooting into Recovery mode>resume brings up a login screen that bounces back. Using Recovery>Root to update and then a full root loads to a login screen that bounces back. 

All this = Unusable installation. This is not a good advertisement for Ubuntu. 

Regards.

---

### Post by Lars Noodén on 2013-09-28
@grahammechanical, If it's a bug that you can reproduce consistently, be sure to file a proper bug report in Launchpad so that your effort does not go to waste.

---

### Post by kansasnoob on 2013-09-28
> **grahammechanical said:**
> Well, that was a waste of a couple of hours. I am beginning to doubt the wisdom of calling something a beta release just because a date in the calendar has been reached. I make no comment on Ubuntu 13.10 the OS but I cannot recommend the live session image for anything but testing purposes.

Trying to install from the live session desktop failed because the install icon (in Launcher and Dash) failed to activate the Installer. The actual installation worked up to a point. The Ubuntu One login for a returning user does not progress beyond endlessly repeating to validate the users login details. We need to click "login later" to get any further.

On reboot I got past the login screen to a black screen with only the white mouse cursor showing. Rebooting into Recovery mode>resume brings up a login screen that bounces back. Using Recovery>Root to update and then a full root loads to a login screen that bounces back. 

All this = Unusable installation. This is not a good advertisement for Ubuntu. 

Regards.

I agree, particularly when you say, "***I am beginning to doubt the wisdom of calling something a beta release just because a date in the calendar has been reached***."

I've been testing all of the Saucy Lubuntu and Ubuntu GNOME alphas and betas, and this is the worst of the bunch, although Ubuntu GNOME is the most stable of those three ........ can't comment on the other flavors ATM.

I personally see this as another indication that so-called "cadence testing" is a failure when it comes to iso images, maybe it's OK for individual apps, but what Ubuntu is now calling a "Final Beta" is actually "Alpha 1" quality!!!!!

In fact the Lubuntu and Ubuntu GNOME images are a gazillion times more stable than Ubuntu itself. Bad advertisement indeed :(

---

### Post by craig10x on 2013-09-28
Ubuntu 13.10 development is running quite nicely though and pretty darn stable so i am not so sure you can judge by live daily build isos...i installed about 2 months ago and it keeps getting better...i think it will be a really nice release... :D

---

### Post by spier on 2013-09-28
Well, I got my brand new asus s400ca, windows8 preinstalled, spend past two days reading every post about uefi, boot-repair, wathever, really scared.
Today, took a deep breath, make some room in HD using win8 (remembered wy I leaved windows years ago), and installed saucy. 
As grahammechanical pointed, it only installs from boot option - live intaller icon does nothing, but I'm amazed as it went flawlesly. Maybe just a beginner's luck...

---

### Post by kansasnoob on 2013-09-28
> **craig10x said:**
> Ubuntu 13.10 development is running quite nicely though and pretty darn stable so i am not so sure you can judge by live daily build isos...i installed about 2 months ago and it keeps getting better...i think it will be a really nice release... :D

I'm not talking about "daily builds". I'm talking about what Ubuntu represented as a "Final Beta". Have you tried that image?

---

### Post by grahammechanical on 2013-09-28
Now here is a weird thing. I have just re-installed using the same image. This time I selected Install Ubuntu from the text mode screen and the install went as it should and upon reboot I am at a working desktop. Now blackscreen. No login screen bounce back. How is it possible for the different options to install to work differently?

I have found one negative thing. It is not loading xmir. Did I tick install third party software without intending to? No. No proprietary video driver. It is on Gallium 0.4 = Nouveau. 

Regards.

---

### Post by Mateusz Stachowski on 2013-09-28
It's not loading XMir because it's still not enabled by default. You still have to enable universe repo and install unity-system-compositor package. Then you either reboot or restart LightDM.

---

### Post by grahammechanical on 2013-09-28
> **Mateusz Stachowski said:**
> It's not loading XMir because it's still not enabled by default. You still have to enable universe repo and install unity-system-compositor package. Then you either reboot or restart LightDM.

I know. I am just waiting for when that happens so I can install over my long term development branch install. 
 
I have been running saucy on xmir for weeks. I even have one saucy install where the repositories are pointing to the "devel" repositories. Anyway, I know that the little glitches that this new install has are nothing to do with xmir. Glitches like rebooting after an update to the kernel and loosing the power cog menu. Then a log out and back in bringing back the power cog menu but loosing the clock app indicatior. And yes, I do have the box ticked to put the clock in the top panel. And the clock settings page is greyed out. But as I say, this cannot be anything to do with xmir.

Regards.

---

### Post by craig10x on 2013-09-28
> **kansasnoob said:**
> I'm not talking about "daily builds". I'm talking about what Ubuntu represented as a "Final Beta". Have you tried that image?

Yes..actually ran it today...ran super on the live session but didn't try installing of course, since i am already running it...i did bring up the installer from the live session and it seemed to be working normal too...though of course, i was careful not to hit "install now"...

@grahammechanical: i don't think they have activated xmir by default yet...as you know, i am running 13.10 on my toshiba laptop with intel so naturally it's the open source drivers but they haven't turned it on by default yet, so i wouldn't be surprised if it was like that on the beta iso also...when i ran package manager, i see the packages but they aren't actually installed...they are supposed to turn it on by feature freeze but that is not until Oct 10th...so i'd imagine that sometime between now and then, the update will come down to activate it...

An interesting thing i noticed about the installer is it always gives you the option to UPGRADE rather then clean install, in this case, i am running Saucy and i can Upgrade to 13.10 if i wish...i might use that when the 13.10 final iso comes out to upgrade my 13.10 development to 13.10 final....in that way, i would imagine it will clean out the extra stuff i accumulated from all the updating in development...
After that point, i will upgrade only from final to final versions of ubuntu...as i am not planning on staying on development...

---

### Post by Gyokuro on 2013-09-29
> **VMC said:**
> Testing the day before the beta, I have pretty much the same outcome, also Kubuntu is **flawless**. Using *AMD Athlon(tm) II X2 250 Processor × 2 ,GeForce 6150SE nForce 430/integrated/SSE2.*

Ubuntu Saucy is almost useless. I have downloaded a Quantal kernel, and on the beta I will try that kernel to see if I get improvements on the graphics side. Trying to determine what's up with nvidia. Maybe an oler nouveau will work.

That was expected as Kubuntu (Lubuntu, Xubuntu) stick with Xorg but beta took ages to boot on an Intel system - QQ booted 30% faster and now I have to check why Saucy takes so long to boot.

---

### Post by pauljwells on 2013-09-29
> **kansasnoob said:**
> I've only tested Ubuntu, Ubuntu GNOME, and Lubuntu so I can't comment on the other flavors but my results with an Intel Atom CPU 230 @ 1.60GHz w/Intel 82945G/GZ Integrated Graphics are as follows:

Ubuntu Saucy final Beta is largely unusable ..... it takes nearly 5 (yes five) minutes for the dash to launch so you can even open an app not located in the launcher. It takes about 2 minutes even to open an app such as "files" in the launcher. Makes me wonder what the minimum specs are going to be .............. maybe a gazillion GHz CPU with a graphics board the size of the space station ;)

Ubuntu GNOME final Beta is pretty good. I've encountered few problems using it out-of-box :D

Lubuntu final Beta is experiencing a lot of kernel freezes :(

You need to create ~/.xprofile with the line in it
```
export UNITY_LOW_GFX_MODE=1
```

This will switch off some of the power-hungry effects. I have unity running nicely on an Atom

---

### Post by kansasnoob on 2013-09-29
> **pauljwells said:**
> You need to create ~/.xprofile with the line in it
```
export UNITY_LOW_GFX_MODE=1
```

This will switch off some of the power-hungry effects. I have unity running nicely on an Atom

Cool, I'll try that .............. but you realize since it's largely unusable out-of-box that most people will just try it and then walk away ;)

---

### Post by jerrylamos on 2013-09-29
> **kansasnoob said:**
> Cool, I'll try that .............. but you realize since it's largely unusable out-of-box that most people will just try it and then walk away ;)
Success:
Lubuntu saucy beta install clean as a whistle, 

Except for Ubuntu disconnecting from hidden wireless network at boot.  Chromebook, 12.04, nook, samsung galaxy, ... tell them once about the hidden network and connect automatically at boot every time.  Ubuntu gives me the message "Disconnected....".  Look at network, says the network is out of range.  It's not, by policy network manager tries to connect without using the encryption key it has.  Launchpad bugs about this for ages.  "Not a bug, it's network manager policy".  Not user friendly.

Lubuntu of course is for someone familiar with linux, not a newbie.

Ubuntu install buggy.  On two pc's so far, 64 and 32, "top" shows ubiquity starting for a couple seconds then drops off.  No activity at all.  Minutes later, give command line sudo killall -15 ubiquity, then sudo ubiquity.  "top" shows a couple seconds activity, then nothing for 3 minutes.  Finally ubiquity starts up.  I see there's a daily build dated 29 September I'll try that.

One try, connected wireless encrypted then started ubiquity.  Finally got to the ubuntu one thing, I selected later (maybe never) and ubiquity froze.  10 minutes later, no activity at all, discovered internet had dropped out.  Ubiquity/ubuntu didnt tell me that, just sat there with "top" saying ubiquity 99.6% cpu (dual processor, 200% is available) and 6.5% memory.  O.K., open install without internet, usual nothing, killall, sudo ubiquity and got going again.  I haven't noticed much different than earlier builds this month, except for the difficulties on install which I have not had all thru saucy cycle.

Oh, one new item, in both install and first boot, external monitor shows built in smaller desktop overlaid on larger external monitor disktop.  Bug written.  systems settings displays fixes that.  

Oh, bug on displays, unity shows only "built in".  Select mirror, shows both.  Turn off built in, select 1360x768 on external, gives me only the choice of counter clockwise or clockwise.  No normal rotation.  Cut it down to 1024x768, set normal, set apply, do the settings displays again and now normal is available for 1360x768.  That's an old launchpad bug been around for months.

Well I'm up and running.  This ubuntu/unity install experience on two pc's not for newbies.

---

### Post by ventrical on 2013-09-29
There is regression on my Dell Dimension 3100 tower desktop on the 'live' session. That old PC has been a workhorse and has loaded most every iso very expeditiously, until now. It does, however, have an older instell graphics chipset. As I reported earlier - smooth install and "live' on Sandybridge. Smooth "live' on older ATI radeon but crappy install afterworks.

 Now .. on to nVidia..
:)

---

### Post by ventrical on 2013-09-29
The live session is working awesomely on one of my Intel Asus machines with nVidia GT218/210. Unity Dash/Panel ..a-OK.

```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 0e)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
01:04.0 Mass storage controller: Integrated Technology Express, Inc. IT8212 Dual channel ATA RAID controller (rev 13)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
04:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)
04:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
ubuntu@ubuntu:~$ 

```

---

### Post by ventrical on 2013-09-29
I was even able to install unity-system-compositor in the live session (thought it would never work)  then go to terminal and :

```

sudo service lightdm restart

```

*note* I had to enable the  repository so I could install unity-system-comp.

```
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Beta i386 (20130925.1) saucy InRelease
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Beta i386 (20130925.1) saucy/main Translation-en_US
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Beta i386 (20130925.1) saucy/main Translation-en
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Beta i386 (20130925.1) saucy/restricted Translation-en_US
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Beta i386 (20130925.1) saucy/restricted Translation-en
Ign http://archive.ubuntu.com saucy InRelease                             
Ign http://archive.ubuntu.com saucy-updates InRelease        
Get:1 http://archive.ubuntu.com saucy Release.gpg [933 B]
Get:2 http://archive.ubuntu.com saucy-updates Release.gpg [933 B]        
Get:3 http://archive.ubuntu.com saucy Release [49.6 kB]                  
Get:4 http://archive.ubuntu.com saucy-updates Release [49.6 kB]      
Get:5 http://archive.ubuntu.com saucy/main i386 Packages [1,253 kB]   
Ign http://security.ubuntu.com saucy-security InRelease                        
Get:6 http://archive.ubuntu.com saucy/restricted i386 Packages [10.0 kB]       
Get:7 http://security.ubuntu.com saucy-security Release.gpg [933 B]            
Get:8 http://security.ubuntu.com saucy-security Release [49.6 kB]              
Get:9 http://archive.ubuntu.com saucy/universe i386 Packages [5,659 kB]        
Get:10 http://security.ubuntu.com saucy-security/main i386 Packages [14 B]     
Get:11 http://security.ubuntu.com saucy-security/restricted i386 Packages [14 B]
Get:12 http://security.ubuntu.com saucy-security/universe i386 Packages [14 B] 
Get:13 http://security.ubuntu.com saucy-security/main Translation-en [14 B]    
Get:14 http://security.ubuntu.com saucy-security/restricted Translation-en [14 B]
Get:15 http://security.ubuntu.com saucy-security/universe Translation-en [14 B]
Ign http://security.ubuntu.com saucy-security/main Translation-en_US           
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com saucy-security/universe Translation-en_US       
Get:16 http://archive.ubuntu.com saucy/main Translation-en [711 kB]            
Hit http://archive.ubuntu.com saucy/restricted Translation-en                  
Get:17 http://archive.ubuntu.com saucy/universe Translation-en [3,887 kB]      
Get:18 http://archive.ubuntu.com saucy-updates/main i386 Packages [14 B]       
Get:19 http://archive.ubuntu.com saucy-updates/restricted i386 Packages [14 B] 
Get:20 http://archive.ubuntu.com saucy-updates/universe i386 Packages [14 B]   
Get:21 http://archive.ubuntu.com saucy-updates/main Translation-en [14 B]      
Get:22 http://archive.ubuntu.com saucy-updates/restricted Translation-en [14 B]
Get:23 http://archive.ubuntu.com saucy-updates/universe Translation-en [14 B]  
Ign http://archive.ubuntu.com saucy/main Translation-en_US                     
Ign http://archive.ubuntu.com saucy/restricted Translation-en_US               
Ign http://archive.ubuntu.com saucy/universe Translation-en_US                 
Ign http://archive.ubuntu.com saucy-updates/main Translation-en_US             
Ign http://archive.ubuntu.com saucy-updates/restricted Translation-en_US       
Ign http://archive.ubuntu.com saucy-updates/universe Translation-en_US         
Fetched 11.7 MB in 46s (252 kB/s)                                              
Reading package lists... Done
ubuntu@ubuntu:~$ 

```

It came back up with the  "Try Ubuntu, Install Ubuntu" screen. I clicked "Try Ubuntu" and it brought me back to  the Unity Dash/panel. I crtl+alt+t, ran top and voila' there was unity-system-comp.

BTW .. I most always choose  (discard on shutdown) when making startup Disks with SDC. I don't think this would even work with a persistive drive.

Now I am going to try at an overclock. 

Currently:

```
ubuntu@ubuntu:~$ sudo dmidecode -t processor | grep "Speed"
    Max Speed: 4000 MHz
    Current Speed: 3367 MHz
ubuntu@ubuntu:~$ 

```

---

### Post by ventrical on 2013-09-29
... and it's just rocking on overclock.

```

ubuntu@ubuntu:~$ sensors
nouveau-pci-0400
Adapter: PCI adapter
temp1:        +37.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.55 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.58 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4066 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +36.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +32.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +20.0°C  (high = +80.0°C, crit = +125.0°C)

ubuntu@ubuntu:~$ sudo dmidecode -t processor | grep "Speed"
    Max Speed: 4000 MHz
    Current Speed: 4087 MHz
ubuntu@ubuntu:~$ 

```

ASUS P5AD2-E Deluxe MoBo

---

### Post by ventrical on 2013-09-29
it is working equally as well in "live" on my AMD Athlon Dual Core 5000+X2 with nVidia GT218/210

```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB600 IDE
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 01)
04:06.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
05:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46)
05:09.0 USB controller: NEC Corporation OHCI USB Controller (rev 41)
05:09.1 USB controller: NEC Corporation OHCI USB Controller (rev 41)
05:09.2 USB controller: NEC Corporation uPD72010x USB 2.0 Controller (rev 02)
ubuntu@ubuntu:~$


```
ASUS VM2 MoBo

---

### Post by su:bhatta on 2013-09-30
Thank god i read up the 4 pages. I seem to be the only person who is commenting on Ubuntu Studio Development release.

Been using for nearly 2  months. 2 days back there was 126MB updates and then everything went haywire. 
Got a new menu, Studio programs installer, with that. Both were great additions I found.

1)sometimes the OS boots up, I login, the wallpaper and the top panel comes but everything is frozen. Docky, conky nothing shows, everything freezes, Ctrl+AlT+F1 gives 'Stopping mount network filesystems      [ok]', from there i can reboot, if i am lucky there is no more problem i get a nice working system. 
Else I get same problem & have to reboot till I get a working system.

2)Sometimes if computer gets locked then i get black screen and it never wakes up, everything is frozen.

Currently am typing from the same machine, who'd know that something is wrong? It has become moody ;)

Had installed Gnome on Ubuntu Studio and have reported a bunch of bugs and 3 have been confirmed ... lets see where it all goes, i am a patient man.

Thank God, I have Wheezy with all my audio programs running with 3.2.0-4-RT kernel :)

P.S. Downloading the Beta2 image now in Wheezy, maybe I am missing something, lets  see if it works better.

---

### Post by ventrical on 2013-09-30
I just did a hard install of Ubuntu beta i386 at a labour intensive 4.167GHz overclock and it went perfectly on  P5AD2-E deluxe with nVidia GT1218/210.

 The only difference I notice is that the Audio Icon on the top right is muted by default.

*edit* After installing unity-system-compositor my CPU temp shot up almost 14 degrees C, but then backed down to a cool:

```

ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.55 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.58 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4041 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +36.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +32.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +20.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +37.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ 

```

as which it is running at now.

---

### Post by sammiev on 2013-09-30
Hi  ventrical,

What type of box are you using? Your temperature is very good to say the least. ):P

---

### Post by ventrical on 2013-10-01
> **sammiev said:**
> Hi  ventrical,

What type of box are you using? Your temperature is very good to say the least. ):P

Hi Sammiev,

I am running several boxes but the one in question is an ASUS P5AD2-E Deluxe with a WDC WD400BD hdd, 2 GBs of 800MHz DDR2 w nVidia GT218/210. I also have been experiementing with the Cedar Mill Celeron Ds (3.20GHz) which I can overclock saucy to 5.2 GHz on stock cooling and also some 3.4 and 3.2 Pentiums LGA775 sockets. With the Pentiums the HTs get unstable about 4.8GHz but the single core non HTTs Celerons will  perform cool as cucumbers at 5.2GHz. 

btw .. This mobo has a special -fanless  solid state cooling device on the underside of the processor socket "Power Temperature"  and it will actually go cooler than ambient.

 There are  lot of bugs with this current beta on older machines with legacy ATi or nVidia cards but it works just great on my power towers and Sandybridge.

Regards..

---

### Post by sammiev on 2013-10-01
Thanks, you keep these interesting. :)

---

### Post by ventrical on 2013-10-01
Thank you ! I would go nuts  from boredom if I couldn't overclock my boxes.  :) Some of the older boxes are better than the i5 i7 series. Those things have so many restrictions on them that it is hard to tame them. And they got that bad batch of thermal paste (Intel Engineering at its best) so they are going to heat up unless you de-lid them , take the old paste out, repaste them with Arctic Silver X4 and reseal them. I think they fixed the most recent batch but have fun with the cross references :) lol



Regards..

---

### Post by ortermagic on 2013-10-04
> **craig10x said:**
> Ubuntu 13.10 development is running quite nicely though and pretty darn stable so i am not so sure you can judge by live daily build isos...i installed about 2 months ago and it keeps getting better...i think it will be a really nice release... :D

Same here

---

### Post by jerrylamos on 2013-10-06
I got into more Launchpad bugs on this Beta milestone than any of the previous milestones.  

Some workarounds from the launchpad bug entries have helped but of course they are not in the daily build .iso code.  I can't tell from the launchpad bug comments whether the RC will have fixes or not.

My desktop is still screwed up the hide/unhide launcher behavior leaves a big black launcher background vertical bar where it is supposed to restore the wallpaper.

---

### Post by grahammechanical on 2013-10-06
> [COLOR=#000000]the hide/unhide launcher behavior leaves a big black launcher background vertical bar where it is supposed to restore the wallpaper.[/COLOR]

When I see that I know I am using the video fallback mode of llvmpipe. I see llvmpipe as a sub set of Nouveau that is used for graphic cards that cannot run Ubuntu Unity 3D. It is the replacement of Unity 2D+metacity. I get it when I run Recovery Resume. 

Regards.

---

### Post by jerrylamos on 2013-10-06
> **grahammechanical said:**
> When I see that I know I am using the video fallback mode of llvmpipe. I see llvmpipe as a sub set of Nouveau that is used for graphic cards that cannot run Ubuntu Unity 3D. It is the replacement of Unity 2D+metacity. I get it when I run Recovery Resume. 

Regards.
This is Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller running normal, not Recovery.  

I've even made a couple stabs at mir with it, however it is not supposed to be ready for external monitor yet.  Waiting for a hint mir is ready for another go.

I have no experience with Unity 3D (and no interest so far) on my netbook, notebook, or tower.  I tend to run full screen  or nearly full screen applications such as internet browser, office, terminal utilities, videos, digital photos, etc. on 1600x900 or 1440x900 or 1366x768 external monitors.  I do very little with the desktop except set wallpaper to my wife in a bathing suit on vacation on an Australian beach.

---

