---
title: "New kernel 3.8.0-17.27 nvidia-310 kernel module failed to build."
date: 2013-04-08
forum: Ubuntu Development Version
---

### Post by philinux on 2013-04-08
System borked at moment. Boots into desktop but no unity. Tried previous kernel and same result. Purged 310 and reinstalled but still no joy.

Going to uninstall latest kernel and reinstall 310.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-310/+bug/1166007](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-310/+bug/1166007)

---

### Post by philinux on 2013-04-08
Ok removed new kernel and installed nvidia-310 which builds correctly for 3.8.0-16.

But, no unity.

From cli it says no unity-panel-service and plugin opengl not loaded. Anyone got a suggestion to get this unborked.

[edit]
Ok I reset unity dconf reset -f /org/compiz/ and reinstalled compiz and rebooted. Hey presto desktop back to normal.

---

### Post by Frogs Hair on 2013-04-08
I had the same problem last night . Nvidia 3.10 failed to install properly, but I recovered on the second attempt. When I ran the Unity support test GLX failed. The new Linux header was a held package and I didn't notce the partial upgrade from synaptic (my fault). By the time I came back from supper the header was available. I first installed the header and then reinstalled Nvidia 3.10. The resolution was extra large :shock: but, I was able to work in classic no effects. The new kernel is up and running.

---

### Post by PilotPaul on 2013-04-08
Curiously I don't seem to have this kernel installed, despite doing all updates...is this restricted to specific systems? I am running on an Acer Aspire S3....

ah found the problem...for some reason my linux-image and linux-header packages were not being updated...fixed now - sorry to distract from the real issue (i.e. nvidia), just confused me that I hadn't got the latest kernel!

---

### Post by philinux on 2013-04-08
> **Frogs Hair said:**
> I had the same problem last night . Nvidia 3.10 failed to install properly, but I recovered on the second attempt. When I ran the Unity support test GLX failed. The new Linux header was a held package and I didn't notce the partial upgrade from synaptic (my fault). By the time I came back from supper the header was available. I first installed the header and then reinstalled Nvidia 3.10. The resolution was extra large :shock: but, I was able to work in classic no effects. The new kernel is up and running.

I'll stick with the old kernel for now. For info the full version of the kernel that fails is 3.8.0-17.**27**

---

### Post by dino99 on 2013-04-08
Does not get issue here on i386 with nvidia-313-updates

i often have seen your issue here with different users & kernels; i wonder if they have the required packages installed  to get the driver compiled successfully ?

i always have : build-essential, linux-source (& the likes), linux-libc-dev  installed, and never get compilation issue.

---

### Post by philinux on 2013-04-08
> **dino99 said:**
> Does not get issue here on i386 with nvidia-313-updates

i often have seen your issue here with different users & kernels; i wonder if they have the required packages installed  to get the driver compiled successfully ?

i always have : build-essential, linux-source (& the likes), linux-libc-dev  installed, and never get compilation issue.

It builds fine with 3.8.0-16 so I guess the required packages are installed.

This is from the make log.
> If you are using a Linux 2.4 kernel, please make sure
you either have configured kernel sources matching your
kernel or the correct set of kernel headers installed
on your system.

If you are using a Linux 2.6 kernel, please make sure
you have configured kernel sources matching your kernel
installed on your system. If you specified a separate
output directory using either the "KBUILD_OUTPUT" or
the "O" KBUILD parameter, make sure to specify this
directory with the SYSOUT environment variable or with
the equivalent nvidia-installer command line option.

Depending on where and how the kernel sources (or the
kernel headers) were installed, you may need to specify
their location with the SYSSRC environment variable or
the equivalent nvidia-installer command line option.

*** Unable to determine the target kernel version. ***

make: *** [select_makefile] Error 1

---

### Post by dino99 on 2013-04-08
as said above : be sure to have the "kernel sources matching..."  : really check with synaptic

i've forgotten to answer about the unity issue, run:

compiz --replace ccp &
setsid unity

---

### Post by Frogs Hair on 2013-04-08
I noticed the performance was a bit choppy with Nvidia  3.10 & Kernel: 3.8.0-17-generic and switched to 3.13 and all is well . I use 3.14 on the windows side anyway.

Edit: After installing 3.13 I looked at my residual configuration in synaptic and found the 173 driver was installed even though 3.10 experimental was displayed as installed in additional drivers. ???  That explains the choppy behavior. I checked Xserver settings this time. (shakes head and smiles)

---

### Post by VeeDubb on 2013-04-08
So, some updates today seem to have bricked my system, and my ham-fisted attempts at troubleshooting appear to have made it worse.


After installing some updates this afternoon (I've been running RR for a couple of weeks) I got the usual "Your system must restart to complete updates" message and rebooted.

On reboot, my desktop background and the various files cluttering my desktop loaded up, but Unity did not.  I was able to get a terminal open, and tried a few things, also noting that no window decorations or controls were loading.  When I tried to run nvidia-settings, I got an error that I didn't appear to be running an nvidia driver.

I then spent some time trying to figure out how to get the "Additional Drivers" app loaded up from the command line, but couldn't figure it out.  So, I tried to use jockey-text to enable a driver.  Unfortunately, from the directions I found browsing the web via my phone, I had to run init 1 before enabling a graphics driver that way, which killed my WiFi, and I've never had any success with configuring WiFi from the terminal.

After various reboots, I ended up opening Synaptic from the terminal, and installed the nvidia 313 package from there.  Then proceeded to reboot.  

For just a second or two before X shutdown for the reboot, I saw the "Your system is running in low graphics mode" prompt asking me if I wanted to configure my display, but I didn't have time to interact with it before X shut down.

The system got half way through the boot, and dropped to a blinking cursor without a functioning terminal.

Waited to make sure it wasn't just taking a while, and then did a hard reboot.

When I attempted to get the GRUB menu to come up so I could boot up in single-user terminal mode, I got a brief message that said "GRUB loading," but GRUB never loaded, and it eventually continued on with an unsuccessful boot.


Now I don't appear to be able to even get to a single user terminal for trouble shooting.

Can anybody point me in a useful direction that doesn't involve reformatting / and reinstalling?  I do have access to a live image on USB, which I'm using to type this, and if worst comes to worst, my /home is on a separate partition, so reinstalling without data loss is an option, although a very unpalatable one...

---

### Post by VeeDubb on 2013-04-08
Update:  I'm not sure why, but grub seems to 'sometimes' work.  About 1 reboot in 3, I can get the grub menu to come up.  

If I try to boot into failsafe X, I get the same unsuccessful boot.

If I try to enable networking using the menu, it gives lots of feedback about various network modules being loaded up, but never returns to the menu or a terminal.  

I'm left with dropping to a root shell, but I'm a bit behind the 8-ball trying to figure out what to do from there.

Suggestions?

---

### Post by PJs Ronin on 2013-04-08
I think I just got clobbered by the same problem, but at least Grub comes up.   When I first booted this morning I did an update through synaptic and noticed that there was an update to (among other things) 3.8.0-17 headers from -16.   I installed the updates, rebooted and ended up with a borked system.   I haven't figured out what went wrong yet, but by selecting the -16 version rather than the -17 version on boot I am at least back up in 'normal' mode.

Oh, I also booted from live USB and did a [Boot Repair]("http://ubuntuforums.org/showthread.php?t=1769482&highlight=boot+repair") to clean up Grub.

Edit: ruh roh [http://ubuntuforums.org/showthread.php?t=2133507&p=12594026#post12594026](http://ubuntuforums.org/showthread.php?t=2133507&p=12594026#post12594026)

---

### Post by cecilpierce on 2013-04-08
Problem here is it boots but after a few seconds the screen goes black for a few seconds and comes back on then black again, happens about three time and finally goes black for good. It even happen with the 16 kernel with nvidia-current but now I put the nouveau back on and still the same, this is a new 3 day old install :confused:

---

### Post by Frogs Hair on 2013-04-08
Related thread but , both of us did different things to resolve the problem. I am currently using the new kernel.   [http://ubuntuforums.org/showthread.php?t=2133507](http://ubuntuforums.org/showthread.php?t=2133507)

---

### Post by VeeDubb on 2013-04-08
> **PJs Ronin said:**
> I think I just got clobbered by the same problem, but at least Grub comes up.   When I first booted this morning I did an update through synaptic and noticed that there was an update to (among other things) 3.8.0-17 headers from -16.   I installed the updates, rebooted and ended up with a borked system.   I haven't figured out what went wrong yet, but by selecting the -16 version rather than the -17 version on boot I am at least back up in 'normal' mode.

Oh, I also booted from live USB and did a [Boot Repair]("http://ubuntuforums.org/showthread.php?t=1769482&highlight=boot+repair") to clean up Grub.

Edit: ruh roh [http://ubuntuforums.org/showthread.php?t=2133507&p=12594026#post12594026](http://ubuntuforums.org/showthread.php?t=2133507&p=12594026#post12594026)

Thanks.  It's been so long since I had any serious boot problems that I think my last issue was trying to repair LILO on Mandrake. ](*,)

> **Frogs Hair said:**
> Related thread but , both of us did different things to resolve the problem. I am currently using the new kernel.   [http://ubuntuforums.org/showthread.php?t=2133507](http://ubuntuforums.org/showthread.php?t=2133507)

Looks like I may be in a lot of trouble.  My bad fix is not going to help me here.

---

### Post by VeeDubb on 2013-04-08
Well, there's some light.  I got back into grub, booted using an older kernel, and everything is at least back to where it was before I tried to fix it.  I can get to a desktop (sans unity) and hopefully from here I'll be able to purge all things nvidia and see if I can get it going again.  Hopefully a kernel update will solve it for real before it matters.

---

### Post by QDR06VV9 on 2013-04-08
> **VeeDubb said:**
> Well, there's some light.  I got back into grub, booted using an older kernel, and everything is at least back to where it was before I tried to fix it.  I can get to a desktop (sans unity) and hopefully from here I'll be able to purge all things nvidia and see if I can get it going again.  Hopefully a kernel update will solve it for real before it matters.

sudo apt-get install nvidia-curent && apt-get install nvidia-settings
This Worked for me and then had to reset unity.
"compiz --replace ccp &"    And Then
"unity-reset"
There is a deb file for 13.04 on the Link Below
Instructions found here-------->   [http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)
Hope It Helps.
[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
This has worked on 2 Machines with Raring installed. Cheers!

---

### Post by stinkeye on 2013-04-08
Bit confused here???
What kernel should I be using in an up to date install.
Made new thread...
_[http://ubuntuforums.org/showthread.php?t=2133714&p=12595031#post12595031](http://ubuntuforums.org/showthread.php?t=2133714&p=12595031#post12595031)_

---

### Post by QDR06VV9 on 2013-04-08
> **stinkeye said:**
> Bit confused here???
What kernel should I be using in an up to date install.

```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **uname -a**
Linux Raring [COLOR="#FF0000"]3.8.0-13-generic[/COLOR] #23-Ubuntu SMP Mon Mar 18 18:09:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

[COLOR="#008000"]glen@Raring:~$[/COLOR]  **dpkg-query -l 'linux-image*'**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                Version                Architecture           Description
+++-===================================-======================-======================-============================================================================
un  linux-image                         <none>                                        (no description available)
un  linux-image-3.0                     <none>                                        (no description available)
ii  linux-image-3.8.0-10-generic        3.8.0-10.19            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-11-generic        3.8.0-11.20            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-12-generic        3.8.0-12.21            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-13-generic        3.8.0-13.23            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-14-generic        3.8.0-14.24            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-15-generic        3.8.0-15.25            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-16-generic        3.8.0-16.26            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-17-generic        3.8.0-17.27            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-6-generic         3.8.0-6.13             amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-7-generic         3.8.0-7.15             amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-8-generic         3.8.0-8.17             amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-9-generic         3.8.0-9.18             amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-10-generic  3.8.0-10.19            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-11-generic  3.8.0-11.20            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-12-generic  3.8.0-12.21            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-13-generic  3.8.0-13.23            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-14-generic  3.8.0-14.24            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-15-generic  3.8.0-15.25            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-16-generic  3.8.0-16.26            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-17-generic  3.8.0-17.27            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-6-generic   3.8.0-6.13             amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-7-generic   3.8.0-7.15             amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-8-generic   3.8.0-8.17             amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-9-generic   3.8.0-9.18             amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic                 3.8.0.17.32            amd64                  Generic Linux kernel image
```





3.8.0-17-generic

---

### Post by stinkeye on 2013-04-08
[COLOR="#FF0000"]Edit[/COLOR] I'll make a new thread rather clutter than this one.

> **runrickus said:**
> 3.8.0-17-generic

---

### Post by QDR06VV9 on 2013-04-09
> **stinkeye said:**
> Am I missing some package needed to update the kernel?

 Have You Ran "sudo apt-get update"  And "sudo apt-get dist-upgrade" Recently?
I just pulled it in tonite!
With the one Machine Dual Booting I had to use bootrepair to get to 3.8.0-17
other wise it would boot to 3.0.16..
But Now Running nvidia 313.26
With Kernel 3.8.0-17-generic!!
Everything Is Smooth as Butter!!

---

### Post by VeeDubb on 2013-04-09
I've got my problem all sorted out, and I'll run down how I got it going for me.  I'm sure there are other solutions that will work, but right now, 3.8.0-17-generic won't work with nvidia, or at least not with the nvidia drivers I was running.  This also may not apply to a new install anyway, but when I upgraded from 3.8.0-17-generic to 3.8.0-16-generic it all fell apart.

1. Use grub to boot into 3.8.0-16-generic

2. Open up synaptic, and purge everything to do with 3.8.0-17-generic and everything relating to nvidia, as well as the kernel and nvidia meta packages so that it doesn't auto-update until the kernel gets fixed and I'm ready to install a new kernel.

3. Reboot, and check to make sure you're running 3.8.0-16-generic

4. Open up synaptic, and manually install the nvidia 304 drivers and 304 settings app.  Do not reinstall any of the nvidia meta-packages.

5. Reboot.

6. In a terminal: ```
dconf reset -f /org/compiz/
``` (you may be asked to install dconf if you're not already running it.

7. In a terminal: ```
unity --reset-icons
```

8. Reboot

---

### Post by merlos on 2013-04-09
The same happened to me 

I subscribed this bug on launchpad
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1166253](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1166253)

I think that anyone affected should click the "affect me" link on top of the page.

---

### Post by victor9098 on 2013-04-09
This happened to be me last night, and again this morning. All I have done to get to a working desktop is use synaptic to remove all the nvidia packages and restart. The peculiar thing on restart is that other users account will be working just fine at this stage, but going into my account (admin) and Unity will still be missing. Using a mix of the dconf commands listed above usually gets things back to normal. Will reinstall the 310 repo (the suggested one for my nvidia card) late to see if things back to normal.

---

### Post by merlos on 2013-04-09
Victor the problem is -17 kernel with nvidia proprietary drivers
I solved booting into -16 and now I have installed 310 drivers

---

### Post by victor9098 on 2013-04-09
> **merlos said:**
> Victor the problem is -17 kernel with nvidia proprietary drivers
I solved booting into -16 and now I have installed 310 drivers

Yeah, looks like I have 3.8.0-17.27 installed. For me it just means not messing on Steam, so will leave the almighty GRUB alone for now. Fingers crossed they consider this bug worth addressing :)

EDIT:

Does anyone have a bug number associated with this to mark as 'affecting me'?

---

### Post by merlos on 2013-04-09
> **victor9098 said:**
> Yeah, looks like I have 3.8.0-17.27 installed. For me it just means not messing on Steam, so will leave the almighty GRUB alone for now. Fingers crossed they consider this bug worth addressing :)

EDIT:

Does anyone have a bug number associated with this to mark as 'affecting me'?

I subscribed this one
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1166253](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1166253)

---

### Post by Chelidze on 2013-04-09
Same problem here I did an update today 200 mb file or so 
[IMG]http://i.imgur.com/CIVyVRql.jpg[/IMG]

This is what I got after the reboot, after this I selected enabled open source drivers but only the resolution has changed but I do not see the dash or anything else

---

### Post by philinux on 2013-04-09
Threads Merged.

New bugs on this are being marked as a duplicate of [https://bugs.launchpad.net/bugs/576648](https://bugs.launchpad.net/bugs/576648)

---

### Post by Frogs Hair on 2013-04-09
My computer is doing fine, but I did switch from the 3.10 to 3.13 driver and have received xorg-server and unity updates since the initial problem. The update this morning gave a configure grub notice and all was well after restart.   
Hostname: ubuntuOS: Ubuntu 13.04 x86_64
Kernel: 3.8.0-17-generic
Uptime: 0:05
Window Manager: Compiz
Desktop Environment: GNOME
Shell: Bash
Terminal: Xterm
Packages: 2002
NVIDIA Driver Version 313.26
4-9-2013
Unity 7.0
Xorg-severcore-core 1.13.3

---

### Post by sgage on 2013-04-09
My rather inelegant solution to this issue was to install the 3.9 kernel from mainline. Forward escape! :KS

---

### Post by philinux on 2013-04-09
> **sgage said:**
> My rather inelegant solution to this issue was to install the 3.9 kernel from mainline. Forward escape! :KS

Lol indeed.

Mine today was to install nvidia-current which pulls in the 304 driver. Then install the new kernel. All worky now.

---

### Post by QDR06VV9 on 2013-04-09
Mine today was to install nvidia-current which pulls in the 304 driver. Then install the new kernel. All worky now.[/QUOTE]


313.26  Works Splendid Here..
:P

---

### Post by grahammechanical on 2013-04-09
Like many I am splashing around trying to fix this issue. Some who are less experienced might find this helpful

When the desktop only has the wallpaper, then right click on the desktop and select Change Desktop Background and you now have access the System Settings and all the utilities including Addiitonal Drivers in Software and Updates.

Ctrl+Alt+T = Terminal
Ctrl+Alt+F1 = a tty = a commandline
Ctrl+Alt+F7 = return to Desktop

gksudo will launch utilities with a graphical user interface. For example,

gksudo software-center = Ubuntu Software Centre

gksudo update-manager = runs the Update Manager with a button to select Settings which in turn gives acccess to Repositories; Ubuntu software; Other Software; Updates; Authentication; Additonal Drivers.

gksudo nautilus = load file manager

gksudo synaptic = load Synaptic Package Manager (if installed) with an option to Fix broken Packages

sudo shutdown -h now = Shutdown now

sudo shutdown -r now = Reboot now

Stuff like this is useful in these situations as I am finding out. It is all part of running the development branch. Expect more of this with a rollowing update release.

Regards.

---

### Post by sgage on 2013-04-09
> **grahammechanical said:**
> Like many I am splashing around trying to fix this issue. Some who are less experienced might find this helpful

When the desktop only has the wallpaper, then right click on the desktop and select Change Desktop Background and you now have access the System Settings and all the utilities including Addiitonal Drivers in Software and Updates.

Ctrl+Alt+T = Terminal
Ctrl+Alt+F1 = a tty = a commandline
Ctrl+Alt+F7 = return to Desktop

gksudo will launch utilities with a graphical user interface. For example,

gksudo software-center = Ubuntu Software Centre

gksudo update-manager = runs the Update Manager with a button to select Settings which in turn gives acccess to Repositories; Ubuntu software; Other Software; Updates; Authentication; Additonal Drivers.

gksudo nautilus = load file manager

gksudo synaptic = load Synaptic Package Manager (if installed) with an option to Fix broken Packages

sudo shutdown -h now = Shutdown now

sudo shutdown -r now = Reboot now

Stuff like this is useful in these situations as I am finding out. It is all part of running the development branch. Expect more of this with a rollowing update release.

Regards.

A very nice tool kit, which can really help to broaden one's options in scenarios like this... Thanks!

---

### Post by cururu on 2013-04-09
Hi!

I just updated linux-source/headers and recompiled the same NVidia Driver and it worked fine again.

```

# apt-get update
# apt-get upgrade -y
# apt-get install gcc module-assistant linux-source linux-headers-$(uname -r) -y
# m-a prepare -y 
# mount -rw -o remount / 

CRTL+ALT+F1 (if not already in a terminal outside X)
# service lightdm stop

# chmod +x NVIDIA-Linux-x86_64-310.44.run 
# ./NVIDIA-Linux-x86_64-310.44.run
 
```

---

### Post by Frogs Hair on 2013-04-09
Updated linux header package has come via update manager.

---

### Post by philinux on 2013-04-09
> **cururu said:**
> Hi!

I just updated linux-source/headers and recompiled the same NVidia Driver and it worked fine again.

```

# apt-get update
# apt-get upgrade -y
# apt-get install gcc module-assistant linux-source linux-headers-$(uname -r) -y
# m-a prepare -y 
# mount -rw -o remount / 

CRTL+ALT+F1 (if not already in a terminal outside X)
# service lightdm stop

# chmod +x NVIDIA-Linux-x86_64-310.44.run 
# ./NVIDIA-Linux-x86_64-310.44.run
 
```

The bug refers to the normal method of activating nvidia drivers and kernel upgrades. Not a manual install.

---

### Post by mc4man on 2013-04-09
It *appears* to be a simple fix for the 310 drivers, if so then maybe there is no intention to offer them??. (too many as is
Ex. with modified 310 package - 
> $ sudo dpkg -i '/home/doug/Documents/nvidia-310_310.32-0ubuntu2_amd64.deb' 
[sudo] password for doug: 
Selecting previously unselected package nvidia-310.
(Reading database ... 267951 files and directories currently installed.)
Unpacking nvidia-310 (from .../nvidia-310_310.32-0ubuntu2_amd64.deb) ...
Setting up nvidia-310 (310.32-0ubuntu2) ...
update-alternatives: using /usr/lib/nvidia-310/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: skip creation of /usr/lib/XvMCConfig because associated file /usr/lib/nvidia-310/XvMCConfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: using /usr/lib/nvidia-310/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-310
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Loading new nvidia-310-310.32 DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-17-generic
Building for architecture x86_64
Building initial module for 3.8.0-17-generic
Done.

nvidia_310:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.8.0-17-generic/updates/dkms/

depmod....

DKMS: install completed.
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-17-generic
doug@doug-XPS-M1330:~/Documents$ 

For info's sake change made - 
```
--- /home/doug/Documents/nvidia-310_310.32-0ubuntu2_amd64/usr/src/nvidia-310-310.32/conftest.sh	2013-03-08 11:35:45.000000000 -0500
+++ /home/doug/Documents/nvidia-310_310.32-0ubuntu2_amd64/usr/src/nvidia-310-310.32/conftest.sh	2013-03-08 11:35:38.000000000 -0500
@@ -156,7 +156,7 @@
     fi
 
     CFLAGS="$BASE_CFLAGS $MACH_CFLAGS $OUTPUT_CFLAGS $AUTOCONF_CFLAGS"
-    CFLAGS="$CFLAGS -I$HEADERS -I$HEADERS/uapi"
+    CFLAGS="$CFLAGS -I$HEADERS -I$HEADERS/uapi -I$OUTPUT/include/generated/uapi"
 
     if [ "$ARCH" = "i386" -o "$ARCH" = "x86_64" ]; then
         CFLAGS="$CFLAGS -I$SOURCES/arch/x86/include"
@@ -1649,7 +1649,8 @@
         FILE="linux/version.h"
         SELECTED_MAKEFILE=""
 
-        if [ -f $HEADERS/$FILE -o -f $OUTPUT/include/$FILE ]; then
+        if [ -f $HEADERS/$FILE -o -f $OUTPUT/include/$FILE -o \
+	     -f $OUTPUT/include/generated/uapi/$FILE ]; then
             #
             # We are either looking at a configured kernel source
             # tree or at headers shipped for a specific kernel.

```

Personally would just go with 304 or 313 untill 310 is fixed (if it is

---

### Post by VeeDubb on 2013-04-17
I see that the kernel int he repos is now up to -18, but I still can't use nvidia-313 with the kernel from the repos.  Has anybody been able to get nvidia working with the latest kernel and nvidia-313 from the repos, or are people who want/need 313 stuck with either a non-repo kernel or a non-repo driver?

---

