---
title: "UNITY 2D now officially dropped and removed from repos"
date: 2012-08-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-08-15
The newest gnome-session_3.5.5-0ubuntu2 removes ubuntu-2d session.
This is because unity-2d is no longer supported, only unity-3d is used now.

[https://launchpad.net/ubuntu/quantal/+source/gnome-session/3.5.5-0ubuntu3]("https://launchpad.net/ubuntu/quantal/+source/gnome-session/3.5.5-0ubuntu2")

---

### Post by jppr on 2012-08-15
yep and this... [https://launchpad.net/ubuntu/quantal/+source/gnome-session/3.5.5-0ubuntu3](https://launchpad.net/ubuntu/quantal/+source/gnome-session/3.5.5-0ubuntu3)

---

### Post by Stinger on 2012-08-15
Well like Fedora17, I can see the llvmpipe is used if no hardware acceleration is available now.

Lets hope Unity is not to resource hungry on low spec. hardware to give a pleasant user experience.

---

### Post by madjr on 2012-08-15
[http://www.webupd8.org/2012/08/unity-2d-no-longer-installed-by-default.html](http://www.webupd8.org/2012/08/unity-2d-no-longer-installed-by-default.html)

> According to the latest "ubuntu-meta" package update from the Ubuntu Quantal Quetzal repositories, Unity 2D will no longer be installed by default in Ubuntu 12.10, and Unity 2D users are being transitioned to the Unity 3D session, just like it was discussed at UDS-Q.

Further more, the latest Unity package, uploaded to the Ubuntu Quantal repositories a few hours ago, uses a "dummy" Unity-2D package, so Unity 2D is no longer available in the repositories and won't be installable at all in Quantal.

Ubuntu users without graphical acceleration will be able to use Unity 3D thanks to **llvmpipe**, so there will be no fallback session anymore and Unity will look the same for all users.


I wonder if this is causing these graphical problems:
[http://ubuntuforums.org/showthread.php?t=2039669](http://ubuntuforums.org/showthread.php?t=2039669)

---

### Post by xebian on 2012-08-15
opps..silly me:)

---

### Post by xebian on 2012-08-15
I just did and upgrade

silly me  :)

---

### Post by vasa1 on 2012-08-15
Here's more on the "dummy" packages for Unity 2D: [http://www.ubuntuupdates.org/packages/latest_logs?utf8=%E2%9C%93&dist=quantal&commit=Filter&noppa=0&levels%5Bbase%5D=1&levels%5Bbackports%5D=1&levels%5Bproposed%5D=1&levels%5Bsecurity%5D=1&levels%5Bupdates%5D=1](http://www.ubuntuupdates.org/packages/latest_logs?utf8=%E2%9C%93&dist=quantal&commit=Filter&noppa=0&levels%5Bbase%5D=1&levels%5Bbackports%5D=1&levels%5Bproposed%5D=1&levels%5Bsecurity%5D=1&levels%5Bupdates%5D=1)

---

### Post by nilarimogard on 2012-08-15
See here: [https://launchpad.net/ubuntu/+source/unity/6.2.0-0ubuntu2](https://launchpad.net/ubuntu/+source/unity/6.2.0-0ubuntu2) - scroll down and you'll notice it says "transitional dummy package" for all unity-2d packages.

---

### Post by xebian on 2012-08-15
Sorry guys..my bad :)

---

### Post by philinux on 2012-08-15
Another take on this. And threads merged.

[http://www.iloveubuntu.net/unity-2d-removed-ubuntu-1210-default](http://www.iloveubuntu.net/unity-2d-removed-ubuntu-1210-default)

---

### Post by vasa1 on 2012-08-15
> **Stinger said:**
> Well like Fedora17, I can see the llvmpipe is used if no hardware acceleration is available now.

Lets hope Unity is not to resource hungry on low spec. hardware to give a pleasant user experience.

I think that is unavoidable? What is divided between two processors (GPU and CPU) on modern boxes will be handled by CPU alone on older ones

I wonder if the devs will use a few "old" boxes for testing ;)

---

### Post by Stinger on 2012-08-15
> **vasa1 said:**
> I think that is unavoidable? What is divided between two processors (GPU and CPU) on modern boxes will be handled by CPU alone on older ones

I wonder if the devs will use a few "old" boxes for testing ;)

That's not exactly what I meant.
I meant how will Unity3d witch relies on compiz run on old hardware that runs fine with Unity2d that AFAIK don't need compiz ?
Unity3d with compiz via the llvmpipe is my worry. 
Will it take up to many resources on such machines compared to Unity2d to make a pleasant user experience ?

---

### Post by xeizo on 2012-08-15
It certainly doesn't work at all when using the proprietary Nvidia-driver, the same problems Firefox and Thunderbird have had for the past few days now affect the entire desktop. 

That's nice work, Ubuntu without an accelerated desktop - Unity 2D at least worked, how about the now upcoming Steam-client for Linux? Won't be usable on vanilla-Ubuntu if this persists. The open source drivers CAN NOT play modern games as of yet(only old cheezy Linux-ones).

I had to install the xubuntu-desktop to be able to use my computer at all ](*,)

Anyway, this is Alpha/Beta, but it doesn't look promising to kill the entire desktop this late in development ...

---

### Post by philinux on 2012-08-15
> **xeizo said:**
> It certainly doesn't work at all when using the proprietary Nvidia-driver, the same problems Firefox and Thunderbird have had for the past few days now affect the entire desktop. 

That's nice work, Ubuntu without an accelerated desktop - Unity 2D at least worked, how about the now upcoming Steam-client for Linux? Won't be usable on vanilla-Ubuntu if this persists. The open source drivers CAN NOT play modern games as of yet(only old cheezy Linux-ones).

I had to install the xubuntu-desktop to be able to use my computer at all ](*,)

Anyway, this is Alpha/Beta, but it doesn't look promising to kill the entire desktop this late in development ...

I'll be testing this later. (nvidia 8600GT)

[edit] got a desktop with just wallpaper and nothing else. ctrl alt t and did a unity --reset. All ok now.

I need to test a clean install.

---

### Post by EgoGratis on 2012-08-15
I will test this later but i do have two questions now:

-What is the command that shows if Unity uses GPU acceleration or not.
-Will GMA 500 users have Unity 3D and if yes can somebody test and tell us how does it work.

---

### Post by philinux on 2012-08-15
> **EgoGratis said:**
> I will test this later but i do have two questions now:

-What is the command that shows if Unity uses GPU acceleration or not.
-Will GMA 500 users have Unity 3D and if yes can somebody test and tell us how does it work.

/usr/lib/nux/unity_support_test -p

For first question.

---

### Post by EgoGratis on 2012-08-15
I see and i imagine this line is important/changes:

GPU: 
Not software rendered:    yes

CPU: 
Not software rendered:    no

Maybe it would be better if it would change to **Software rendered** and answer would be **yes** or **no**.

---

### Post by vasa1 on 2012-08-15
> **EgoGratis said:**
> I see and i imagine this line is important/changes:

GPU: 
Not software rendered:    yes

CPU: 
Not software rendered:    no

Maybe it would be better if it would change to **Software rendered** and answer would be **yes** or **no**.

Double negatives are more fun. I don't know why the options are phrased the way they are.

```
~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 8.0.2

_Not_ software rendered:    yes
_Not_ blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
Inspiron-1545:~$ 

```

---

### Post by EgoGratis on 2012-08-15
Now that i think of it probably because user is less confused if all answers are **yes** because this test was used to determine if Unity 3D is supported or not. Probably this test will change soon because it will not be used anymore to tell if Unity 3D is supported on hardware or not but if it uses GPU or not.

Because from now on at least in theory Unity 3D is supported everywhere and test for this is not needed anymore?

---

### Post by EgoGratis on 2012-08-15
And i have one more question how do i manually set if i want to use GPU or not? For testing purposes this "switch" would be useful. 

Is there simple way to tell Unity to use GPU or not and by doing this to not disable/enable 3D support.

---

### Post by frogotronic on 2012-08-15
What about gnome-panel/gnome-classic?   Will that still be available?

- CH

---

### Post by kaldor on 2012-08-15
> **cement_head said:**
> What about gnome-panel/gnome-classic?   Will that still be available?

- CH

GNOME "Classic" (fallback mode) isn't part of Unity, but rather the GNOME project. It's not going away within the foreseeable future :)

---

### Post by mc4man on 2012-08-15
> **EgoGratis said:**
> 
Because from now on at least in theory Unity 3D is supported everywhere and test for this is not needed anymore?
I would assume, but don't actually know, that the test, (or a test) for 3d support will determine if llvmpipe is used or not
(fail = llvmpipe


Whether there is any way to test llvmpipe with 3d capable hardware don't know, if not then it would be up to those who hardware does use llvmpipe to see how well unity/compiz works out

---

### Post by mc4man on 2012-08-15
> **xeizo said:**
> It certainly doesn't work at all when using the proprietary Nvidia-driver, the same problems Firefox and Thunderbird have had for the past few days now affect the entire desktop. 

That's nice work, Ubuntu without an accelerated desktop - Unity 2D at least worked, how about the now upcoming Steam-client for Linux? Won't be usable on vanilla-Ubuntu if this persists. The open source drivers CAN NOT play modern games as of yet(only old cheezy Linux-ones).

I had to install the xubuntu-desktop to be able to use my computer at all ](*,)

Anyway, this is Alpha/Beta, but it doesn't look promising to kill the entire desktop this late in development ...

nvidia drivers work fine, at least for most. 
What doesn't work is if you try to use xserver 1.13 with nvidia drivers in a 3d session.
That has nothing to do with this at all and if people enable proposed or a ppa repo & upgrade xserver to 1.13 or higher well then that's too bad for them. 
downgrade xserver or use nouveau

---

### Post by lucazade on 2012-08-15
last time I tried gnome-shell with llvmpipe on a gma500 (fedora 17 live) speed was not so bad (slower btw than a plain metacity session) and with some graphical glitches.

don't know how unity could work with llvmpie, i'll try as soon as it will be available!

---

### Post by madjr on 2012-08-15
> **lucazade said:**
> last time I tried gnome-shell with llvmpipe on a gma500 (fedora 17 live) speed was not so bad (slower btw than a plain metacity session) and with some graphical glitches.

don't know how unity could work with llvmpie, i'll try as soon as it will be available!

not sure either but here are the instructions related to the porting:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1035261](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1035261)

---

### Post by fjgaude on 2012-08-15
> **lucazade said:**
> last time I tried gnome-shell with llvmpipe on a gma500 (fedora 17 live) speed was not so bad (slower btw than a plain metacity session) and with some graphical glitches.

don't know how unity could work with llvmpie, i'll try as soon as it will be available!

It's working, well mostly, on my Dell netbook, Poulsbo.

---

### Post by Stinger on 2012-08-15
> **EgoGratis said:**
> And i have one more question how do i manually set if i want to use GPU or not? For testing purposes this "switch" would be useful. 

Is there simple way to tell Unity to use GPU or not and by doing this to not disable/enable 3D support.

I found this on the Mint forum, see if you can use it, only " LIBGL_ALWAYS_SOFTWARE=1 " should be executed I think, but maybe someone with more expertise could help here.
[http://forums.linuxmint.com/viewtopic.php?f=60&t=104132&start=0]("http://forums.linuxmint.com/viewtopic.php?f=60&t=104132&start=0")

---

### Post by Petro Dawg on 2012-08-15
I have a question...  I recently began using Ubuntu2D because 3D was making my laptop run way to hot (maxing over 90 Celsius - even with Jupiter installed on low power mode); using 2D I now hover in the 50 degree range.    So, how will this change affect me?  Will my current 2D installation still receive the updates it needs or will I have to move to Xfce to keep my temps down?

---

### Post by effenberg0x0 on 2012-08-15
If you have a working "3D-Capable VGA + VGA Drivers + VGA Module + XOrg xserver + Compiz + Unity set" and you stop lightdm, unload the VGA module, blacklist it (as well as any other alternative VGA module you might have), restart lightdm and still get a Unity 3D session, (which you can test with nux-tools/unity-support-test or anything GLX) then you are definitely using llvmpipe, right? Is that it?

Regards,
Effenberg

---

### Post by ventrical on 2012-08-16
> **philinux said:**
> I'll be testing this later. (nvidia 8600GT)

[edit] got a desktop with just wallpaper and nothing else. ctrl alt t and did a unity --reset. All ok now.

I need to test a clean install.


Here's what happened to me on:
unity reset

```

ventrical@ventrical:~$ unity reset
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service: no process found
compiz (core) - Info: Loading plugin: reset
compiz (core) - Error: Failed to load plugin: reset
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
Initializing composite options...done
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Starting plugin: opengl
Initializing opengl options...done
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
Initializing decor options...done
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
Initializing vpswitch options...done
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
Initializing snap options...done
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
Initializing mousepoll options...done
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
Initializing resize options...done
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
Initializing place options...done
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
Initializing move options...done
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
Initializing wall options...done
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
Initializing grid options...done
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
Initializing session options...done
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
Initializing gnomecompat options...done
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
Initializing animation options...done
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
Initializing fade options...done
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
Initializing unitymtgrabhandles options...done
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
Initializing workarounds options...done
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
Initializing scale options...done
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
Initializing expo options...done
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
Initializing ezoom options...done
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 26: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 31: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 40: Having multiple values in <test> isn't supported and may not works as expected
compiz (unityshell) - Error: OpenGL 1.4+ not supported

compiz (unityshell) - Error: GL_ARB_fragment_program not supported

compiz (core) - Error: Plugin initScreen failed: unityshell
compiz (core) - Error: Failed to start plugin: unityshell
compiz (core) - Info: Unloading plugin: unityshell
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  18 (X_ChangeProperty)
  Resource id in failed request:  0x2400022
  Serial number of failed request:  8552
  Current serial number in output stream:  8556
ventrical@ventrical:~$ firefox

```

but I can run my programs from terminal.

Any  pointers anyone.?

This is a system that ran on Unity 2D

Dell Opti GX27G

---

### Post by EgoGratis on 2012-08-16
> **Petro Dawg said:**
> I have a question...  I recently began using Ubuntu2D because 3D was making my laptop run way to hot (maxing over 90 Celsius - even with Jupiter installed on low power mode); using 2D I now hover in the 50 degree range.    So, how will this change affect me?  Will my current 2D installation still receive the updates it needs or will I have to move to Xfce to keep my temps down?

Probably your GPU is overheating under load and if that is true then running Unity 3D on CPU should not overheat your GPU but for that to happen there has to be some easy user controllable "switch" that user can use to select if GPU should be used or not.

I didn't try it yet but it was suggested in this topic this might be the switch:

> I found this on the Mint forum, see if you can use it, only "  LIBGL_ALWAYS_SOFTWARE=1 " should be executed I think, but maybe someone  with more expertise could help here.> It's working, well mostly, on my Dell netbook, Poulsbo.Then i guess Unity 3D should run well too and if this is true nice addition for users of this hardware to be able to run Unity 3D and not to use too much CPU power while doing it.

---

### Post by fjgaude on 2012-08-16
The dropping of 2D is just about complete. My Dell netbook can change the size of Launch icons with the Change Desktop Desktop mouse right click. That was never possible before. As they say, most things will be possible for the less powerful boxes.

Lots of bugs remain but as you know the devs are hard at work removing them, one at a time. <smile>

---

### Post by EgoGratis on 2012-08-16
One question what about remote desktop and things like NX that don't work with Unity 3D?

---

### Post by fjgaude on 2012-08-16
> **EgoGratis said:**
> One question what about remote desktop and things like NX that don't work with Unity 3D?

I'm not into such things, and maybe Luca will reply. Things are still very early, long before release, still Alpha 2 and 3 to come. So... we wait and wonder!

---

### Post by jerrylamos on 2012-08-16
> **fjgaude said:**
> The dropping of 2D is just about complete. My Dell netbook can change the size of Launch icons with the Change Desktop Desktop mouse right click. That was never possible before. As they say, most things will be possible for the less powerful boxes.

Lots of bugs remain but as you know the devs are hard at work removing them, one at a time. <smile>
"Change Desktop Desktop mouse right click" - where is that?  I didn't find that selection in "System Settings" or in "Dash Home."

There are a number of "feetures" that the devs are not likely to remove - during testing I re-boot a lot, and 3D is the most sluggish desktop boot I've seen.  Also if I do "top" on terminal Compiz is right up there on %CPU and continues to go up as more "feetures" are added.  Well, their way or the highway.  I've a spare partition let me try Lubuntu again.

Wonder if anyone who knows how will revive 2D.

Jerry

---

### Post by cariboo on 2012-08-16
> **jerrylamos said:**
> "Change Desktop Desktop mouse right click" - where is that?  I didn't find that selection in "System Settings" or in "Dash Home."

There are a number of "feetures" that the devs are not likely to remove - during testing I re-boot a lot, and 3D is the most sluggish desktop boot I've seen.  Also if I do "top" on terminal Compiz is right up there on %CPU and continues to go up as more "feetures" are added.  Well, their way or the highway.  I've a spare partition let me try Lubuntu again.

Wonder if anyone who knows how will revive 2D.

Jerry

I did a fresh install this morning, the option is there when I right click on the desktop. Clicking on the cog wheel I also see several other changes.

Notice:

[LIST]
[*]About this computer
[*]Ubuntu Help
[*]Restart
[/LIST]

---

### Post by jerrylamos on 2012-08-16
[QUOTE=cariboo907;12176764]I did a fresh install this morning, the option is there when I right click on the desktop. Clicking on the cog wheel I also see several other changes.

Thanks, found it.  
Right click on desktop
Change Desktop Background
Very bottom of resulting Appearance menu, 
launcher icon size
I set it to 32.

Thanks, Jerry

---

### Post by GreatDanton on 2012-08-16
Latest updates brought Change desktop background back. Same here.

@cariboo907 This is a little offtopic question but I noticed on the second picture you don't have name under guest session. Did you remove it or is it possible to make user without name?

Regards.

---

### Post by critin on 2012-08-16
Guess this finishes it for me and my old Dell Dimension 4550 on new ubuntus.   I'd hoped that llvmpipe would be auto installed if computer was 3D incapable, but if it was, it didn't work.  If I have to install it, I will, but from what I've read it installs automatically.

I upgraded, then I fresh installed and updated, still no good.  I get wallpaper just fine, but dash/launchers icons are gone.   Super key does nothing.  Any navigation is very slow.   I checked drivers and am running the recommended noveau.  Password doesn't even work, so had to go in via Guest Acct.  Comp. freezes soon after clicking around.  

Apps seem to work fine, (files, etc.)

---

### Post by fjgaude on 2012-08-16
My netbook is not Unity 3D capable and the latest 12.10 Alpha3 installed okay. The full features of Unity are not there but all the old 2D ones are along with much more. So we move in the right direction.

Unity is being programmed to work with all hardware, slow and fast. That's been stated a few times on the forums here.

---

### Post by effenberg0x0 on 2012-08-16
> **critin said:**
> Guess this finishes it for me and my old Dell Dimension 4550 on new ubuntus.   I'd hoped that llvmpipe would be auto installed if computer was 3D incapable, but if it was, it didn't work.  If I have to install it, I will, but from what I've read it installs automatically.

I upgraded, then I fresh installed and updated, still no good.  I get wallpaper just fine, but dash/launchers icons are gone.   Super key does nothing.  Any navigation is very slow.   I checked drivers and am running the recommended noveau.  Password doesn't even work, so had to go in via Guest Acct.  Comp. freezes soon after clicking around.  

Apps seem to work fine, (files, etc.)

It's important we all keep in mind that this is the Ubuntu+1 discussion, we're all testers of a Development Release and not of a finished product. Things are expected to broke in our hands because we voluntarily agreed to be this buffer between development and the end-product, protecting ordinary non-technical end-users from problems they can't deal with. 

We are supposed to be the "specialists" - the ones that are not worried about breaking our setups over and over everyday, to share knowledge and help each other, to discuss openly and find solutions, work around problems, report bugs, take our opinions to developers, etc.

Lets talk about llvmpipe (how to install, uninstall, test, break, fix, what works, what doesn't work, etc) now, and create good bug reports when needed. We have a responsibility in this the minute we start testing.  

Regards,
Effenberg

---

### Post by critin on 2012-08-16
> **effenberg0x0 said:**
> It's important we all keep in mind that this is the Ubuntu+1 discussion, we're all testers of a Development Release and not of a finished product. Things are expected to broke in our hands because we voluntarily agreed to be this buffer between development and the end-product, protecting ordinary non-technical end-users from problems they can't deal with. 

We are supposed to be the "specialists" - the ones that are not worried about breaking our setups over and over everyday, to share knowledge and help each other, to discuss openly and find solutions, work around problems, report bugs, take our opinions to developers, etc.

Lets talk about llvmpipe (how to install, uninstall, test, break, fix, what works, what doesn't work, etc) now, and create good bug reports when needed. We have a responsibility in this the minute we start testing.  

Regards,
Effenberg

Sorry, did I sound gripey?  I didn't intend to.  I'm one of those ordinary, non-tech users that enjoys trying to find solutions.   I was listing what I'd done and which issues I'd had.  I'm not a specialist, but I don't worry about breaking things, that's half the enjoyment for me.  I'd noticed others had posted similar issues and was adding my experience, hoping to gain some knowledge.   Again, my apologies for

---

### Post by walker195 on 2012-08-16
i didnt like unity 2d but for people who like unity 3d but dont have power to run it its great they should keep as a download in the software center

---

### Post by effenberg0x0 on 2012-08-16
> **walker195 said:**
> i didnt like unity 2d but for people who like unity 3d but dont have power to run it its great they should keep as a download in the software center

Hey, no need to apologize or anything. I think I sounded too harsh and that would be unfair. We need more people donating their time and patience to development releases and I am thankful you are testing. As you mentioned it was over for you and your Dell laptop, I just wanted to point out that 12.10 is unfinished and it's normal (and expected) that us testers (which includes technical and non-technical users) experience severe problems. As long as we try to do our best here, we increase the chances it will work better when it reaches ordinary users as a finished product. 

Sorry again.

Regards,
Effenberg

---

### Post by CrByte on 2012-08-17
Wanted to test this out in virtualbox so far does not really work, the screen just flashes and has some weird image retention.

---

### Post by jerrylamos on 2012-08-17
I'll run 3D on occasion to see if there's a way to get crisp sharp clear size 32 icons - to see what I'm seeing, on 3D open a few tabs on Firefox and Nautilus and terminal and switch between them with Alt-tab I can't tell what fuzzy sponge bob things are swirling around.  That's what Ubuntu development wants I've got choices so along with test 3D looking for bugs I mostly run Precise 2D and even Lubuntu.

Choices. Yes I've a couple touchy feely tablets just to see what people are talking about, but don't use them much since I'm much faster with a keyboard and mouse.

Take your choice, seems to me Unity is headed for a tablet lookalike.  Or smartphone.

Jerry

---

### Post by ads52 on 2012-08-17
> **CrByte said:**
> Wanted to test this out in virtualbox so far does not really work, the screen just flashes and has some weird image retention.

I also cannot get Quantal working in Virtualbox with symptoms as above. Anybody have any luck with this?

---

### Post by forcecore on 2012-08-19
I am glad they got rid of 2D version, Unity has more features and less installed packages too in default .iso

---

### Post by critin on 2012-08-20
> **forcecore said:**
> I am glad they got rid of 2D version, Unity has more features and less installed packages too in default .iso

You must have the computer everyone is looking for.  Did 3D just work for you or did you have to do something to it?  Or could you use it before?  You are using ubuntu?

---

### Post by cariboo on 2012-08-21
> **critin said:**
> You must have the computer everyone is looking for.  Did 3D just work for you or did you have to do something to it?  Or could you use it before?  You are using ubuntu?

I have to admit I never liked Unity 2D either, so far except for a mistake I made myself 3D has always worked for me. I'm currently running 3D using the nouveau driver, and patiently waiting for the new Nvidia driver to become available.

---

### Post by jerrylamos on 2012-08-21
Choices.  I've got current architecture notebook amd64, netbook, 3.3 gHz tower running either 12.10 with LXDE desktop and also Precise 2D for salvage when Ubiquity clobbers Grub (last night!).

I tried Kubuntu and XFCE4 - I'm more productive with LXDE.  I can log back in as 3D for brief testing purposes.  Lubuntu I get the feel that Development might drop it, but more importantly to me I use Firefox, LibreOffice, et. al. so for me it's easier just to install Ubuntu then LXDE deskop.

---

### Post by balloons on 2012-08-21
There's so many unity2d threads.. Anyways, spamming this link to all of them as I think it will help. If you want to try the new version of compiz (and help test it!) check this out. LLVMpipe is enabled, and working well for me so far. See how it fares for you. 

[http://ubuntuforums.org/showthread.php?t=2045579](http://ubuntuforums.org/showthread.php?t=2045579)

---

### Post by jerrylamos on 2012-08-21
> **guitara said:**
> There's so many unity2d threads.. Anyways, spamming this link to all of them as I think it will help. If you want to try the new version of compiz (and help test it!) check this out. LLVMpipe is enabled, and working well for me so far. See how it fares for you. 

[http://ubuntuforums.org/showthread.php?t=2045579](http://ubuntuforums.org/showthread.php?t=2045579)
Fully agree. Too many 2D threads.  To some of us, it's an indication of how many people are affected.

For me, all Unity and Compiz have to do is run long enough to sudo apt-get install synaptic and select lxde-desktop.  One of my Quantal installs is back at A2, let me hop to it.

---

### Post by pressureman on 2012-08-21
> **jerrylamos said:**
> For me, all Unity and Compiz have to do is run long enough to sudo apt-get install synaptic and select lxde-desktop.  One of my Quantal installs is back at A2, let me hop to it.

Why do you even need a desktop to do that? Just switch to a text mode VT and execute the command.

---

### Post by cariboo on 2012-08-21
> **jerrylamos said:**
> Fully agree. Too many 2D threads.  To some of us, it's an indication of how many people are affected.

For me, all Unity and Compiz have to do is run long enough to sudo apt-get install synaptic and select lxde-desktop.  One of my Quantal installs is back at A2, let me hop to it.

This more a problem of the new type of members we  are seeing, I've noticed in general that many new users are creating threads, without checking if there is already one dealing with their problem. We've seen it here especially with the Nvidia driver problem, and to some extent the Unity 2D/3D threads.

---

### Post by jerrylamos on 2012-08-22
> **pressureman said:**
> Why do you even need a desktop to do that? Just switch to a text mode VT and execute the command.I like Synaptic.  I suppose I could use apt-cache search, apt-cache depends, apt-cache install but I like Synaptic.  Of course I use Firefox, Libre, Nautilus, gparted, as bunch of other applications in 12.10 Ubuntu.  They run fine with LXDE.  I set repositories with Synaptic, set update frequency (never, I do that frequently anyway). etc.  There are other ways I just prefer Synaptic.  Rather interesting the attitude that comes across from some people posting about others who are not using Unity.  Hope that comment doesn't go against the COC.

Jerry

---

### Post by NormanFLinux on 2012-09-15
> **EgoGratis said:**
> I will test this later but i do have two questions now:

-What is the command that shows if Unity uses GPU acceleration or not.
-Will GMA 500 users have Unity 3D and if yes can somebody test and tell us how does it work.


It works fine on GMA 500 but there is some tearing and screen redraw in a crash. The new Unity will support computers made in the last 10 years. But not any older since there is a point of diminishing returns with Unity with very old - not mainstream - hardware.

---

### Post by jerrylamos on 2012-09-15
> **NormanFLinux said:**
> It works fine on GMA 500 but there is some tearing and screen redraw in a crash. The new Unity will support computers made in the last 10 years. But not any older since there is a point of diminishing returns with Unity with very old - not mainstream - hardware.

I've got a nice IBM Thinkpad T40 made in 2006 that does 2D not 3D and does not do PAE hence no QQ.  That's less than 10 years old.  I've got Precise 2D and Precise Lubuntu on it.  Presumably Precise will be supported for a while yet, and I assume that includes 2D (but maybe not Lubuntu).

---

### Post by josephmills on 2012-09-15
This is more then what err...........
example: 
previews 
unity 2d = 3 pages of code for all previews
TIME on Video 0:57 
[http://www.youtube.com/watch?v=ca4XtZ70RPI](http://www.youtube.com/watch?v=ca4XtZ70RPI)

unity 3d 
over 15 pages of code and not as many options ? 

qt5 and qt-quick2 have 100% opengles support and embeded and harmo......


errrr

---

### Post by lucazade on 2012-09-16
> **NormanFLinux said:**
> It works fine on GMA 500 but there is some tearing and screen redraw in a crash. The new Unity will support computers made in the last 10 years. But not any older since there is a point of diminishing returns with Unity with very old - not mainstream - hardware.

No, it doesn't work good on the gma500. It is slow and buggy, it runs at 1 or 2 frame per seconds and it is full of glitches.

It doesn't work good also on the Thinkpad T40 with an Ati Radeon 7500 mobility..

But on these machines any other DE works like a charm.. take a look at kde.

---

### Post by jerrylamos on 2012-09-16
> **lucazade said:**
> No, it doesn't work good on the gma500. It is slow and buggy...But on these machines any other DE works like a charm.. take a look at kde.Looking across Disro's, KDE is alive and well as is a number of other desktops.  "Unity" isn't used by anyone else - "single source" which can be a concern for application developers.  Just an idle observation since we all have choices.  

I did like it in the old days when Ubuntu was consistantly the top of the list for Linux distro's.

---

### Post by vexorian on 2012-09-16
Is it possible to use compiz with llvmpipe even when full 3d is supported?

What I am looking for right now is something like being able to do:

```

compiz --replace --use-llvmpipe

```
That would replace currently running compiz and make it use llvmpipe. This would have high hopes of being a good "performance mode" to switch to before playing video games.


--
I would treat 12.10 unity not working completely fine on computers that were completely able to run unity-2D as a huge regression and report it as a bug. Devs need to learn of the true consequences of dropping unity-2D. They should have at least have had a transition release in which both unity-2D and llvmpipe unity are used. It is not like removing unity 2d allowed them to stop needing a DVD to install.

---

### Post by jbicha on 2012-09-16
> **vexorian said:**
> 
I would treat 12.10 unity not working completely fine on computers that were completely able to run unity-2D as a huge regression and report it as a bug. Devs need to learn of the true consequences of dropping unity-2D. They should have at least have had a transition release in which both unity-2D and llvmpipe unity are used. It is not like removing unity 2d allowed them to stop needing a DVD to install.

Theoretically, Unity 2D could come back in universe but it needs developers to work on it. Unity 2D has never been ported to gsettings and that's a prerequisite for it coming back to life. Unity 2D also needs some way of handling new Unity features like previews.

---

### Post by vexorian on 2012-09-16
It does not really *need* them you know. I think that old unity-2D as a fallback is better than nothing.

---

### Post by jerrylamos on 2012-09-16
> **vexorian said:**
> ...I think that old unity-2D as a fallback is better than nothing.Casual observation from a number of publications and internet the fallback is other distros.

Now I haven't seen any info from Ubuntu on market penetration compared to, say, Mint, etc.

So far my 3 test recent pc's will run all of the choices (I rarely run Unity) and the IBM Thinkpad T40 is fine with Precise 2D.

---

### Post by vexorian on 2012-09-16
I'd say that seeing how Ubuntu was the first choice for Valve's project to support Linux, it must not be doing terribly bad against other distros in Desktop marketshare.

---

### Post by MG&amp;TL on 2012-09-16
> **vexorian said:**
> I'd say that seeing how Ubuntu was the first choice for Valve's project to support Linux, it must not be doing terribly bad against other distros in Desktop marketshare.

Thank you. 


That aside, I'm a little confused. Everyone seems to be running around headless because "it's software rendering". My understanding was that Unity2d (using Qt and associated technologies) used software rendering, as does llvmpipe. So the only difference is that it's one codebase, less work, and the same effects as previously. 

If I'm mistaken, please correct me. If not, why are people getting so worked up about it?

---

### Post by jerrylamos on 2012-09-16
> **MG&TL said:**
> If I'm mistaken, please correct me. If not, why are people getting so worked up about it?Just guessing, if the commenting people really liked Unity experience and its hardware and CPU% demands there wouldn't be any thought about 2D.

---

### Post by MG&amp;TL on 2012-09-16
> **jerrylamos said:**
> Just guessing, if the commenting people really liked Unity experience and its hardware and CPU% demands there wouldn't be any thought about 2D.

Some people's hardware won't run Unity, but they still like the general experience enough to want a not-hardware-accelerated version. :P

---

### Post by kansasnoob on 2012-09-16
I maintain a lot of boxes with P4M800 graphics that won't even begin to run Ubuntu now but they will run Jeremy Bicha's ubuntu GNOME remix - with either gnome-shell or classic (no-effects):

[http://ubuntuforums.org/showthread.php?t=2052509](http://ubuntuforums.org/showthread.php?t=2052509)

I wish I could properly update that OP but due to the one week editing limit I can't :(

---

### Post by vexorian on 2012-09-16
> **MG&TL said:**
> Thank you. 


That aside, I'm a little confused. Everyone seems to be running around headless because "it's software rendering". My understanding was that Unity2d (using Qt and associated technologies) used software rendering, as does llvmpipe. So the only difference is that it's one codebase, less work, and the same effects as previously. 

If I'm mistaken, please correct me. If not, why are people getting so worked up about it?
The real problem might as well be that ubuntu doesn't correctly decide whether to use llvmpipe or not. Various intel cards do have some sort of 3d accel and *can* run normal compiz with**out** llvmpipe, only terribly slow.

We need an easy way to know if llvmpipe is being used or not. And also one to specify that we want it used.

Edit: I meant with**out** llvmpipe, not with.

---

### Post by MG&amp;TL on 2012-09-16
> **vexorian said:**
> The real problem might as well be that ubuntu doesn't correctly decide whether to use llvmpipe or not. Various intel cards do have some sort of 3d accel and *can* run normal compiz with llvmpipe, only terribly slow.

We need an easy way to know if llvmpipe is being used or not. And also one to specify that we want it used.

Bug report time? I can't think it would be that hard to implement either, given that it's an environment variable that can be set/unset as wished. I'd do it myself, but I'm not comfortable with the Unity source code.

---

### Post by mc4man on 2012-09-16
> **vexorian said:**
> 
We need an easy way to know if llvmpipe is being used or not. And also one to specify that we want it used.

Other than some new hardware where the video isn't supported by open source drivers it should be pretty obvious to users post install.

if not run glxinfo - if you see this, well..

> OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301)
OpenGL version string: 2.1 Mesa 8.1-devel
OpenGL shading language version string: 1.20



edit or look in Details . graphics,  again obvious

---

### Post by CoreyB. on 2012-09-16
> **mc4man said:**
> or look in Details . graphics,  again obvious

I'm sorry, I don't find it obvious. Does Experience Standard mean llvmpipe or not?

---

