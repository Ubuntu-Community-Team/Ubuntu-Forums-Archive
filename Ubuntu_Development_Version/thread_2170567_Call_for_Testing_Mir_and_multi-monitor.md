---
title: "Call for Testing: Mir and multi-monitor"
date: 2013-08-26
forum: Ubuntu Development Version
---

### Post by yetanotherssoname2 on 2013-08-26
I know these forums have been buzzing already all cycle with fun Mir testing, but I would invite you all to participate in this last test before feature freeze for Mir which includes multi-monitor support. Go find any unknown bugs and let the team know how it's working on your machines. They've setup a wiki page with all the info you need here:

[https://wiki.ubuntu.com/Mir/MultiMonitorTesting](https://wiki.ubuntu.com/Mir/MultiMonitorTesting)

Happy Testing everyone!

---

### Post by cariboo on 2013-08-26
Yay, something else to do on my days off, as if I don't have enough to do already. :-P

---

### Post by ventrical on 2013-08-27
I tired already with SandyBridge/nVidia... lost network on first try.

Will keep trying.

@nick

Excellent wiki link nick. Thanks !

Regards..

---

### Post by ventrical on 2013-08-27
> **cariboo907 said:**
> Yay, something else to do on my days off, as if I don't have enough to do already. :-P


I get up usually at 3:00am and go from there. Any time I spend testing Ubuntu I consider space/time in between :)

---

### Post by cariboo on 2013-08-27
> **ventrical said:**
> I get up usually at 3:00am and go from there. Any time I spend testing Ubuntu I consider space/time in between :)

My work day starts at 10:30PM PST, I normally get up around 5:30PM so even though the times are different I do about the same thing.

---

### Post by ventrical on 2013-08-27
> **cariboo907 said:**
> My work day starts at 10:30PM PST, I normally get up around 5:30PM so even though the times are different I do about the same thing.


 I did midnights on and off for about 7 years. One of my proffs way back said . "The best programs are written between  11:00 pm and 4:00am in the morning." Go figure :)

  However .. 90% of the time I find for Ubuntu is quality time.  I have more freedom to experiment and there is less downtime.

---

### Post by yetanotherssoname2 on 2013-08-27
> **ventrical said:**
> I did midnights on and off for about 7 years. One of my proffs way back said . "The best programs are written between  11:00 pm and 4:00am in the morning." Go figure :)

  However .. 90% of the time I find for Ubuntu is quality time.  I have more freedom to experiment and there is less downtime.


Isn't that the truth! You don't even feel fully awake until 2 am when you are on a coding high like that :-)

---

### Post by yetanotherssoname2 on 2013-08-27
Note these bugs ati and nvidia users:

[https://bugs.launchpad.net/xmir/+bug/1217009](https://bugs.launchpad.net/xmir/+bug/1217009)
[https://bugs.launchpad.net/xmir/+bug/1217005](https://bugs.launchpad.net/xmir/+bug/1217005)

---

### Post by jerrylamos on 2013-08-28
Bummer.  Acer Aspire 5253 wide screen notebook with 1600x900 external monitor ATI Radeon saucy 3.11.0-4 followed instructions in [https://wiki.ubuntu.com/Mir/MultiMonitorTesting](https://wiki.ubuntu.com/Mir/MultiMonitorTesting) rebooted to 2 black screens.
Booted in recovery mode and now ubuntu thinks the external monitor is built in, with 1152 resolution, and the real built in is black.
"top" shows Xorg, no hint of compositor, screen is patchy and jerky.

ubuntu reports internal error, bug report failed because of "third party packages" i.e. mir?

Disconnected external monitor, reboots to black screen on real built in.
Booted with only built in in recovery mode.  Only gets 1024x768 not 1366.
screen patchy and jerky.  "top" shows Xorg no hint of mir or compositor.

Wrote bug report Bug 1217637.  

Now what, apt-get remove system compositor?  Remove the ppa?  Re-install saucy?  So I booted 13.04 in another partition.  Time to do a zsync.

BTW, I do have a netbook (this one) with external monitor and Intel graphics.  I could try mir on that after I get the wide screen notebook going again.

Added Xorg.0.log, Xorg.1.log, Xorg, Xorg.failsafe.log, .xsession.errors.  Looks to me like Xorg couldn't understand the graphics controller - no problem before mir install.  
Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6310]

---

### Post by ventrical on 2013-08-28
> **nskaggs said:**
> Isn't that the truth! You don't even feel fully awake until 2 am when you are on a coding high like that :-)

 Back in 1990 it was awesome. I'd be in the com-sci lab until 7am! :) on the VAX-UNIX and IBM-XTs with CGA monitors using DOS 3.0! :) lol

 Now I am doing some O'clocking with a 3.4GHz gallatin on an ASUS board .. running saucy on fvwm-crystal at 4.002 GHz. ! :) LOL 

Unity and Gnome Fallback are having a hard time with the overclock, not to mention dual monitors :)

```


ventrical@ventrical-asus-aiproactive-extreme:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Saucy Salamander (development branch)
Release:    13.10
Codename:    saucy
ventrical@ventrical-asus-aiproactive-extreme:~$ uname -a
Linux ventrical-asus-aiproactive-extreme 3.11.0-3-generic #7-Ubuntu SMP Tue Aug 20 15:25:23 UTC 2013 i686 i686 i686 GNU/Linux
ventrical@ventrical-asus-aiproactive-extreme:~$ sudo dmidecode -t processor | grep "Speed"
    Max Speed: 4000 MHz
    Current Speed: 4002 MHz
ventrical@ventrical-asus-aiproactive-extreme:~$ 

```

---

### Post by jerrylamos on 2013-08-29
"Testing has now completed thank you for submitting your results".

I did install the mir ppa on a netbook with  
Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
built in screen 1024x600
15.5" vga external moniotor 1920x1080 usually run at 1360x768

What I get is:
systems settings displays thinks I have one 40" display (I wish)
displays doesn't show the built-in display at all
External screen shows 1360x768 with 1024x600 overlayed onto it
built in screen just shows the 1024x600 part
So I can get launcher displayed at 1360 or at 1024
Sort of working at times stops and then after some time resumes working
I saved the Xorg.0.log in case someone is interested, though from the top line they are done testing.
Let me see if I can remove the ppa until next time.

Yes, the ppa is removed, mir no longer shows, and running normally - until next time.

---

### Post by jerrylamos on 2013-08-31
Launchpad asked me to take the ppa off, update, and try again since there have been ATI updates.
Well, ppa off didn't maybe fumble finger on my part, so I re-installed.  Running fine.  Likely the best 13.10 I've had.

Put the ppa back on and wham, black screens.  ubuntu/xorg/mir can't recognize what screens there are and how to run them.

It would at least boot with nomodeset crippled one screen black, the other in an odd resolution so I sent some evidence to
[https://bugs.launchpad.net/xmir/+bug/1217637](https://bugs.launchpad.net/xmir/+bug/1217637)

---

### Post by cariboo on 2013-08-31
> **jerrylamos said:**
> Launchpad asked me to take the ppa off, update, and try again since there have been ATI updates.
Well, ppa off didn't maybe fumble finger on my part, so I re-installed.  Running fine.  Likely the best 13.10 I've had.

Put the ppa back on and wham, black screens.  ubuntu/xorg/mir can't recognize what screens there are and how to run them.

It would at least boot with nomodeset crippled one screen black, the other in an odd resolution so I sent some evidence to
[https://bugs.launchpad.net/xmir/+bug/1217637](https://bugs.launchpad.net/xmir/+bug/1217637)

Are you running the open source ATI/AMD driver?

---

### Post by jerrylamos on 2013-09-01
> **cariboo907 said:**
> Are you running the open source ATI/AMD driver?
I installed the .iso from Daily Build and am using it just like ubuntu shipped it.  Nothing added or deleted.  What's the command to show which driver and level is actually being used?
Thanks....

Basically the problem with the Radeon and also with my Intel on my netbook is that mir does not know what the graphic screens are in the case of multi-monitor.  On the Radeon it thinks the external monitor is built in and doesn't know what kind.  Saucy without mir no problem.  On the Intel Atom it thinks the 15.5" TV monitor is a 40" external monitor, what it does is display 1024x600 on the built in and overlays this on top of whatever resolution set on the TV, example 1360x768 with a 1024x600 overlay on the top right.  Two sets of launchers.  Without mir no problem.

Somehow with mir it has lost the ability to detect what the screens are.

---

### Post by ventrical on 2013-09-01
> **jerrylamos said:**
> I installed the .iso from Daily Build and am using it just like ubuntu shipped it.  Nothing added or deleted.  What's the command to show which driver and level is actually being used?
Thanks....


```


sudo lshw -C display


```

---

### Post by jerrylamos on 2013-09-01
> **cariboo907 said:**
> Are you running the open source ATI/AMD driver?
Here's lshw ubuntu running normally:

jerry@Aspire-5253:~$ sudo lshw -C display
[sudo] password for jerry: 
  *-display               
       description: VGA compatible controller
       product: Wrestler [Radeon HD 6310]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:41 memory:80000000-8fffffff ioport:4000(size=256) memory:90400000-9043ffff

Here's lshw mir from Ctrl-Alt-F1 because screens boot to black:

  *-display
       description: VGA compatible controller
       product: Wrestler [Radeon HD 6310]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:41 memory:80000000-8fffffff ioport:4000(size=256) memory:90400000-9043ffff

As I enter this, I had to boot nomodeset to be able to get any desktop at all:

@Aspire-5253:~$ sudo lshw -C display
[sudo] password for jerry: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Wrestler [Radeon HD 6310]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:80000000-8fffffff ioport:4000(size=256) memory:90400000-9043ffff

Now if I do a 
sudo service lightdsm start
things go black.  After a while I do 
Ctrl-Alt-F1
which says service failed to start (or some such words).

So in every case the display software is there, but somehow mir and/or Xorg can't recognize it....

---

### Post by QDR06VV9 on 2013-09-03
> **cariboo907 said:**
> My work day starts at 10:30PM PST, I normally get up around 5:30PM so even though the times are different I do about the same thing.

Yes me also, I do notice you two(ventrical) in the wee hours.

---

### Post by ventrical on 2013-09-04
> **runrickus said:**
> Yes me also, I do notice you two(ventrical) in the wee hours.

My work day usually starts at 3:00am EST so I am up .. first checking msg base. Sometimes I get illuminated with overclocking  so - I'm up.  Whatever time in between I spend on Ubuntu testing. Testing Ubuntu has somehow made me a better malware removal tech for Microsoft based OSes. It doesn't take me  as much time and somehow I have learned to bend the matrix - so to speak :) lol  and then there is work ! ....

edit.. oh yeah  . i forgot .. and then there is sleep ! :) zzzzzzzzzzzzzzz  :) lol

---

