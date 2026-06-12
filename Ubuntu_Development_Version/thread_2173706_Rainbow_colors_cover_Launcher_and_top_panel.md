---
title: "Rainbow colors cover Launcher and top panel"
date: 2013-09-10
forum: Ubuntu Development Version
---

### Post by VMC on 2013-09-10
[IMG]http://i.imgur.com/2upGBgO.png[/IMG]
This has been like this for the past 3 days, of iso zsyncing. 'nomodeset' is the only option that stops it, with limited resolution. 'nvidia.modeset=0, or modeset=0 doesn't affect it.
No bug reports that I could find. Anyone else see this.

---

### Post by grahammechanical on 2013-09-11
I am now trying today's daily image. I do not get that effect when I run the TRY option from the text screen. Or when I allow the image to load to the GUI TRY - INSTALL dialog. Although at that screen I do get a stack of eight top panels. It has been like that for days. But the actual Live session seems normal.

For the record, the live session is not running on Xmir. So, we cannot blame that.

---

### Post by VMC on 2013-09-11
> **grahammechanical said:**
> ...

For the record, the live session is not running on Xmir. So, we cannot blame that.That would have been my next question. :)

Also, I did go ahead and install it the first time this came up, just to see if anything changed - it didn't.

If anyone else has the "[COLOR=#000000]nVidia Geforce 6150 SE[/COLOR]" could you please test it. Thanks.

Time for a bug report.

---

### Post by philinux on 2013-09-11
> **VMC said:**
> That would have been my next question. :)

Also, I did go ahead and install it the first time this came up, just to see if anything changed - it didn't.

If anyone else has the "[COLOR=#000000]nVidia Geforce 6150 SE[/COLOR]" could you please test it. Thanks.

Time for a bug report.

Is that effect caused by/using nouveau or nvidia driver?

---

### Post by VMC on 2013-09-11
Its caused by booting a LiveCD, no drivers installed. And I don't install any. The default driver needs may be the issue.

---

### Post by philinux on 2013-09-11
> **VMC said:**
> Its caused by booting a LiveCD, no drivers installed. And I don't install any. The default driver needs may be the issue.

So it will be nouveau that's in control. I have a 8600gt i'll give the live usb a go tomoz. See if I get same.

---

### Post by VMC on 2013-09-11
Something weird is going on with that display. If, for example, push hard right, the Launcher  comes into view and the color then follows the mouse. The top panel cannot change rainbow colors, but I can right click and open stuff. 
I tried the usual suspects; compiz --replace, gtk-window-decorator replace, etc. I'm just waiting for someone else with a integrated nvidia chip to chime in.

Soon enough I will report the problem to the authorities.

---

### Post by mc4man on 2013-09-11
Don't see any issue here with a nvidia 8400m which is nv50 in nouveau.
Your card is nv40 in nouveau so I'd look for others with similar, (nv40), chipsets (6000 & 7000 series

---

### Post by philinux on 2013-09-12
Just booted daily live iso on a machine with 8600gt and all is fine with that gpu.

---

### Post by eco2geek2 on 2013-09-23
Yes, I have the exact same issue with an Nvidia GeForce 7300 GS video card when using the nouveau driver. The launcher flickers in and out of view, but the tooltips are rainbow-colored translucent blocks. The dash is sort of a translucent yellow. And the top bar remains as in your picture above. It does respond to mouse clicks by showing menus, if you know where to click.

I don't know how to solve the problem using the nouveau driver. Installing the proprietary nvidia driver (from the repositories) does solve the problem. (Note: you can install the nvidia driver from the repositories even if you're running from live media; it just takes a bit of work.)

---

### Post by VMC on 2013-09-23
Yes, thanks for reporting this. I will need to file a bug report. Installing nvidia-173 solved my issue regarding the "rainbow" effect, but now I have a severe lag issue. I'm sure its all tied to nouveau.
ubuntu12.04 had no problem. saucy's nouveau Version: 2.4.46-1. I'll have to check Precise version.

---

### Post by corradoventu on 2013-09-23
same problem w nvidia 7600 Gt nouveau saucy installed (no live) amd64 intel

---

### Post by eco2geek2 on 2013-09-23
> Installing nvidia-173 solved my issue
If you've got a 6150 chipset, try using the 304.108 driver (package name: nvidia-304-updates). 304.xx is the last one that supports series 6 and 7 GeForce GPUs. It's probably faster than the 173.xx driver.

(Note: when you use the Nvidia driver, nouveau is totally disabled, so your lag doesn't have to do with nouveau. You could probably experiment with Nvidia's command-line tool, nvidia-xconfig, to create a customized /etc/X11/xorg.conf with settings that would help speed things up.)

Having experience with both GPUs, I can tell you that both the 6- and 7-series have problems with GLX compositing using the nouveau driver on other Linux distros, as well. It's not just Unity on Ubuntu.

---

### Post by VMC on 2013-09-23
Thanks for the info. One reason I choose '173' is that its small (20mb), and also I wasn't sure where the development ended for the '6150' chip. So as you suggested, I'll try '304'.

Also, what I do is after I get the deb files, I then compress "/var/cache/apt/archives", and save it.  I can just uncompress and just "sudo dpkg -i *deb" that file location on next install. 
> [COLOR=#000000]Having experience with both GPUs, I can tell you that both the 6- and 7-series have problems with GLX compositing using the nouveau driver on other Linux distros, as well. It's not just Unity on Ubuntu. Kubuntu doesn't have this issue at all, and runs very fast. But it will freeze until I install my modified config files(.kde/share/config), then it **never** fails, lags or freeze.[/COLOR]

---

### Post by cecilpierce on 2013-09-26
Just reinstalled daily, still a mess, no cure yet ?

---

### Post by eco2geek2 on 2013-10-03
The best solution is to install the proprietary nvidia driver, from Ubuntu's repository.

However, this reminds me of an [old openSUSE bug]("https://bugzilla.novell.com/show_bug.cgi?id=669783") involving the nouveau driver and GeForce 6- and 7-series cards (including the 6150, which I had at the time). Try this from the Live CD (OK, it no longer fits on a CD, but you know what I mean):

Create a file named "50-device.conf" (without the quotes) in /usr/share/X11/xorg.conf.d with the following lines:
```
Section "Device"
    Identifier "Card0"
    Option "NoAccel" "1"
    Option "ShadowFB" "1"
EndSection
```

and then go to a VT (virtual terminal) and stop and then start lightdm. Unity comes up without the launcher and global menu bar covered with the rainbow coloration shown in the first post, on my box. But compositing is pretty slow. YMMV.

---

### Post by VMC on 2013-10-03
> **eco2geek2 said:**
> The best solution is to install the proprietary nvidia driver, from Ubuntu's repository.

However, this reminds me of an [old openSUSE bug]("https://bugzilla.novell.com/show_bug.cgi?id=669783") involving the nouveau driver and GeForce 6- and 7-series cards (including the 6150, which I had at the time). Try this from the Live CD (OK, it no longer fits on a CD, but you know what I mean):

Create a file named "50-device.conf" (without the quotes) in /usr/share/X11/xorg.conf.d with the following lines:
```
Section "Device"
    Identifier "Card0"
    Option "NoAccel" "1"
    Option "ShadowFB" "1"
EndSection
```

and then go to a VT (virtual terminal) and stop and then start lightdm. Unity comes up without the launcher and global menu bar covered with the rainbow coloration shown in the first post, on my box. But compositing is pretty slow. YMMV.
Thanks! That worked. BTW, reading the man on xorg.conf, you don't need to add the "1". It defaults to true, so:
```
Section "Device"
    Identifier "Card0"
    Option "NoAccel"
    Option "ShadowFB"
EndSection
```Works the same. Just a FYI.

I'm actually using the livecd right now. I was thinking it would freeze at some point, and in fact it did, but not as I thought.
I kept pumping programs into the system to see when it would crash, freeze. It frooze when I was playing a song from [I]Rhythmbox.
[/I]So using a VT and top, I was looking for anyoffending program. The mouse would work but no response. 
Replacing compiz didn't work, but killing *Rhythmbox *did[I].
[/I]
I will read that link you posted. Thanks again for this "fix".

I played games, used Libreoffice, etc, etc. It still works.

---

### Post by VMC on 2013-10-03
Interestingly that Suse bug report is almost 2 years old. I just now experienced the problems. The screen shots with the grabled display is exactly what I got using Fedora and Mint. Maybe this "fix" what work with them as well. The bug report poster also said using a previous xorg-x11-driver-video-nouveau worked. That was going to be my next step, since Precise works great, and Saucy worked up until several weeks ago.

---

### Post by eco2geek2 on 2013-10-03
> BTW, reading the man on xorg.conf, you don't need to add the "1". It defaults to true
Thanks, didn't know that.

> The bug report poster also said using a previous  xorg-x11-driver-video-nouveau worked. That was going to be my next step,  since Precise works great, and Saucy worked up until several weeks ago.
How do you revert to prior packages using *buntu, anyway? Where do you get the old packages from, and how do you keep dist-upgrades from replacing them? I've been using Ubuntu-based distros (and betas) for years now and have never done this. (I'm familiar with the concept of [apt-pinning]("http://jaqque.sbih.org/kplug/apt-pinning.html").)

I mainly use KDE-based distros (like Kubuntu and openSUSE) due to personal preference. With the newer versions of KDE, you can switch between the XRender and GLX backends, so if you've got screen glitches with the nouveau driver (which I do, with what seems like the entire crop of new distros coming out - F20, openSUSE 13.1, and Kubuntu 13.10), you can usually resolve the problem **and** have your compositing effects if you can see the screen well enough to bring up System Settings and switch from GLX to XRender. AFAIK, Unity only works with GLX.

(openSUSE 11.4, the version that bug report refers to, displayed too garbled of a screen to even see anything clearly, which is why you had to create an xorg.conf prior to starting the display manager, kdm.)

---

### Post by VMC on 2013-10-04
I also have Kubuntu 1310 installed and it is almost perfect. The trick is to boot first time using '*nomodeset*', then afterwards I can boot normally. Don't need any gimmick to use *nouveau*. Also UbuntuGNOME is almost the same. Only Ubuntu(Unity) do I have issues.

After trying that 
"fix" for a while and also using it on UbuntuGNOME, it is not usable. The color is now OK, but the experience is sluggish.

Regarding downgrading my xorg*nouveau. I found it may be more work than worth. There's a topic a couple of years ago, on , I think Natty, that described the scenario.

---

### Post by cariboo on 2013-10-04
I saw the same type of problem, on my Intel graphics powered netbook, but I think it was more due to a problem with Atom cpus and compiz, as I was seeing compiz use 156% cpu resource's.

---

### Post by Mateusz Stachowski on 2013-10-07
There is a new bugfix release of Mesa from upstream in Saucy. Which should resolve the [rainbow colors]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1232940") bug for Nouveau and hopefully other drivers.

> [COLOR=#333333][FONT=Ubuntu Mono]mesa (9.2.1-1ubuntu1) saucy; urgency=low[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]  [ Robert Hooker ]
  * Add i915-dont-default-to-2.1.patch: Stop defaulting to OpenGL 2.1 that is not
    fully implemented in hardware on gen3 GPUs, the software fallbacks make Unity
    unusably slow. (LP: [#1222602]("https://bugs.launchpad.net/bugs/1222602"))
  [ Maarten Lankhorst ]
  * New upstream bugfix release. (LP: [#1232940]("https://bugs.launchpad.net/bugs/1232940"))[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]mesa (9.2.1-1) experimental; urgency=low[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]  * New upstream release.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono] -- Maarten Lankhorst <maarten.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]lankhorst@[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]ubuntu.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]com> Mon, 07 Oct 2013 10:39:18 +0200[/FONT][/COLOR]

---

### Post by VMC on 2013-10-07
> [COLOR=#333333]*[FONT=ubuntu mono]* new upstream bugfix release. (lp: [#1232940]("https://bugs.launchpad.net/bugs/1232940"))[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=ubuntu mono]mesa (9.2.1-1) experimental; urgency=low[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=ubuntu mono]* new upstream release.[/FONT]*[/COLOR]

This is not fixed using today's ISO ([saucy-desktop-amd64.iso]("http://cdimage.ubuntu.com/daily-live/current/saucy-desktop-amd64.iso")[COLOR=#000000]           07-Oct-2013 07:48).

Not unsure what 9.2.1-1 experimental means, since we are already at 9.2-1ubuntu3.  Unless mesa 9.2.1-1 experimental is a test release.

edit: looking at the changes file, it looks like the "mesa 9.2.1-1ubuntu1" was excepted [/COLOR]*Mon Oct 7 09:43:23, *and today's ISO is before that. Hopefully tomorrow's ISO will have the fix.

---

### Post by VMC on 2013-10-07
I just installed today's gnome-saucy-iso, and when completed I updated everything, and mesa was one of the updates. Upon update completion I noticed the gui's are smoother now. I never had the "color" issue with gnome, but things have changed.

Also the 7 mesa lib's are all now 9.2-1.1. they were 9.2-1.3. 

Next is to install Ubunue-saucy and see what takes place.

---

### Post by mc4man on 2013-10-07
> **VMC said:**
> This is not fixed using today's ISO ([saucy-desktop-amd64.iso]("http://cdimage.ubuntu.com/daily-live/current/saucy-desktop-amd64.iso")[COLOR=#000000]           07-Oct-2013 07:48).

Not unsure what 9.2.1-1 experimental means, since we are already at 9.2-1ubuntu3.  Unless mesa 9.2.1-1 experimental is a test release.

edit: looking at the changes file, it looks like the "mesa 9.2.1-1ubuntu1" was excepted [/COLOR]*Mon Oct 7 09:43:23, *and today's ISO is before that. Hopefully tomorrow's ISO will have the fix.

"experimental " is[ the debian source ]("http://packages.debian.org/source/experimental/mesa")that ubuntu takes & packages
You can always ck. the manifest file to see what & what versions are on the image
Ex. of todays amd64
[http://cdimage.ubuntu.com/daily-live/current/saucy-desktop-amd64.manifest](http://cdimage.ubuntu.com/daily-live/current/saucy-desktop-amd64.manifest)

---

### Post by VMC on 2013-10-07
> **mc4man said:**
> "experimental " is[ the debian source ]("http://packages.debian.org/source/experimental/mesa")that ubuntu takes & packages
You can always ck. the manifest file to see what & what versions are on the image
Ex. of todays amd64
[http://cdimage.ubuntu.com/daily-live/current/saucy-desktop-amd64.manifest](http://cdimage.ubuntu.com/daily-live/current/saucy-desktop-amd64.manifest)
I checked those mesa files, and they all were the same as mine 9.2-1.3, which fails.

---

### Post by VMC on 2013-10-07
**It's fixed!**

I first noticed that not only was gnome-saucy reacted smoother, but the games were also fixed. They had some weird abnormality, in that once I won a game it would remove the game-gui and only show my stats. Usually the same **and** stats were displayed. Also, on the shell, moving from one icon to another it had a another weird flashing of attributes. Now that is all fixed.

Also, I downloaded today's Ubuntu Saucy ISO, Then updated everything which included mesa. Its all good again. No more "color me rainbow" :)

I will mark this as solved.

PS - mesa would have been the last place I would have ventured into. My thinking was either xorg, nouveau. I'll have to find how mesa plays into all this. Thanks for all the comments.

---

### Post by kansasnoob on 2013-10-07
> **VMC said:**
> **It's fixed!**

I first noticed that not only was gnome-saucy reacted smoother, but the games were also fixed. They had some weird abnormality, in that once I won a game it would remove the game-gui and only show my stats. Usually the same **and** stats were displayed. Also, on the shell, moving from one icon to another it had a another weird flashing of attributes. Now that is all fixed.

Also, I downloaded today's Ubuntu Saucy ISO, Then updated everything which included mesa. Its all good again. No more "color me rainbow" :)

I will mark this as solved.

PS - mesa would have been the last place I would have ventured into. My thinking was either xorg, nouveau. I'll have to find how mesa plays into all this. Thanks for all the comments.

Fixed up my Intel Atom box too :D

I kept looking for an update solely related to "intel", guess I'm not as sharp as I thought.

---

### Post by mc4man on 2013-10-07
the 'Gallium3D drivers' are in Mesa

---

### Post by VMC on 2013-10-07
Answering my own question, I found this ***[mesa]("http://www.mesa3d.org/intro.html")*** explanation.

---

### Post by corradoventu on 2013-10-10
SOLVED by last update - nvidia 7600 Gt nouveau saucy installed (no live) amd64 intel

---

