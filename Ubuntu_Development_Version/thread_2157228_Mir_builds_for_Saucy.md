---
title: "Mir builds for Saucy"
date: 2013-06-24
forum: Ubuntu Development Version
---

### Post by jfernyhough on 2013-06-24
Mir has been building for Precise for a while, but now we have builds for newer releases - and most importantly for Saucy!

[https://launchpad.net/~mir-team/+archive/staging?field.series_filter=saucy](https://launchpad.net/~mir-team/+archive/staging?field.series_filter=saucy)

Patience... :D

Oh, a useful command in advance:

$ sudo ppa-purge ppa:mir-team/staging

;)
```

Image:
[IMG]https://lh6.googleusercontent.com/-s2u3o9bVJLg/Ucik0LTRZvI/AAAAAAAACfM/oKO6-1SRx-Y/w1387-h778-no/mir-builds.png[/IMG]
1 spacer
2 spacer
3 spacer
4 spacer
5 spacer
6 spacer
7 spacer
8 spacer
9 spacer
10 spacer
```

---

### Post by grahammechanical on 2013-06-24
> [COLOR=#333333][FONT=Ubuntu Mono]USE THESE AT YOUR OWN RISK. BE PREPARED TO MANUALLY FIX YOUR SYSTEM IF IT BREAKS.[/FONT][/COLOR]

That is why I am running saucy on btrfs. Can roll back to before the wonky code was installed.

---

### Post by zika on 2013-06-25
What does it brings? What is the insentive to try that PPA?

---

### Post by cecilpierce on 2013-06-25
> **zika said:**
> What does it brings? What is the insentive to try that PPA?

Nothing. just another head ache...:P

---

### Post by zika on 2013-06-25
> **cecilpierce said:**
> Nothing. just another head ache...:P
[http://test.ubuntu-discourse.org/t/non-unity-desktops-now-running-on-xmir/479](http://test.ubuntu-discourse.org/t/non-unity-desktops-now-running-on-xmir/479)
Maybe there is more than that...

---

### Post by zika on 2013-06-25
Is it not a mistake in [http://unity.ubuntu.com/mir/using_mir_on_pc.html](http://unity.ubuntu.com/mir/using_mir_on_pc.html) ...?
```
type=mir
```
instead of```
type=unity
```in /etc/lightdm/lightdm.conf...
For a start...
It seems that I'm not right... It puts me in lowgraphicsmode either way... Works (without Mir) only if omitted...
There are some inconsistencies in PPA at this moment... Not really much different from the last time I've checked... :P
Lots of downgrades and LightDM not ready because... because... some packages are newer than expected and some...

Update&#8321;: Made it work! I'm writing this from Chromium in Mir... ;) The only thing that is annoying is having two different cursors for mouse, one working and one just disturbing... ;)

```
:~$ ps aux | grep unity-system-compositorroot      7840  1.3  0.4 733164 19276 ?        Sl   15:45   0:03 /usr/bin/unity-system-compositor --from-dm-fd 8 --to-dm-fd 13 --vt 7
:~$ grep -i xmir /var/log/Xorg.0.log
[   231.531] xorg-server 2:1.13.3+xmir1-0 (For technical support please see http://www.ubuntu.com/support) 
[   231.538] (II) LoadModule: "xmir"
[   231.538] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
[   231.605] (II) Module xmir: vendor="X.Org Foundation"
[   231.675] (II) RADEON(0): Output XMIR-1 has no monitor section
[   231.675] (II) RADEON(0): Printing probed modes for output XMIR-1
[   231.675] (II) RADEON(0): Modeline "XMIR mode of death"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz eP)
[   231.675] (II) RADEON(0): Output XMIR-1 connected
[   231.675] (II) RADEON(0): Output XMIR-1 using initial mode XMIR mode of death
:~$ ls -l /var/log/lightdm/unity-system-compositor.log
-rw------- 1 root root 6664 Jun 25 15:45 /var/log/lightdm/unity-system-compositor.log
```

Update&#8322;: Sound works (S/PDIF, important to me), works with 3.10... Enough for today... One day I'll solve these two cursors... Until then... Back to normality...

Update&#8323;: It seems that two cursors are related to LightDM not Mir... Yes, both type={mir,unity} work... Now I'll got to go to GDM to have some real work done... :P

Update&#8324;: Yes it is a kind of struggle to make Ricotzs PPas, Mir PPa and several other cohabitate... ;)

---

### Post by grahammechanical on 2013-06-25
Well, I have just broken another saucy install. I am having difficulty getting into my two saucy+btrfs installs. So, I put in a new saucy on Ext4 and it booted without any of the problems that btrfs+saucy is giving me. And then I messed around with MIR again.

I followed the instructions and after re-stating lightdm I got a black screen with just the cursor. Reboot just got me to a low resolution demo of 5 dots changing from white to red and back again.

It does not matter if type=mir or unity. I did notice something I may have done wrong. The instructions said

> sudo restart lightdm

but going through my notes from a previous experiment it seems that the correct code is

```
sudo service lightdm restart
```

I wonder if that difference caused the problem. And to rub my nose it it, I just tried to get into my main saucy+btrfs that this morning would not let me in no matter what and here I am using it. The thing loaded as sweet as anything.

Time for a nap, I think.

---

### Post by dino99 on 2013-06-25
you are very brave, guys : mir is only at the 0.0.5 release  :confused: (way too far from 0.90 or 1.0.0)

---

### Post by zika on 2013-06-25
> **dino99 said:**
> you are very brave, guys : mir is only at the 0.0.5 release  :confused: (way too far from 0.90 or 1.0.0)You're the only one in the whole world who would use word &#8222;brave&#8220; to describe this... Many other words come to my mind...
See You when it becomes 0.1.0rc1... ;)

---

### Post by jfernyhough on 2013-06-25
Plain U+1 is boringly stable... we need to add a random mix of pre-alpha PPAs just to have some fun! :D

---

### Post by zika on 2013-06-25
> **jfernyhough said:**
> Plain U+1 is boringly stable... we need to add a random mix of pre-alpha PPAs just to have some fun! :D[http://www.youtube.com/watch?v=UXA32CHV6Sc](http://www.youtube.com/watch?v=UXA32CHV6Sc)

---

### Post by jfernyhough on 2013-06-25
Well, I tried to get it running and failed. I just ended up with normal X. I am running xserver 1.14, though, which might not help (and I can't see fglrx playing nicely).

---

### Post by ventrical on 2013-06-25
> **jfernyhough said:**
> Mir has been building for Precise for a while, but now we have builds for newer releases - and most importantly for Saucy!

[https://launchpad.net/~mir-team/+archive/staging?field.series_filter=saucy](https://launchpad.net/~mir-team/+archive/staging?field.series_filter=saucy)

Patience... :D

Oh, a useful command in advance:

$ sudo ppa-purge ppa:mir-team/staging



Thanks .. saved one busted machine already after removing and installing saucy filter.

---

### Post by zika on 2013-06-26
Just heads up: After excursion into Mir PPA and ppa-purge my LightDM goes into LowGraphicsMode... I'll sort that out, I hope, but just to report... Luckily I have GDM, startx, xinit, lot of other escape routes... ;)
Also, think about not using /etc/apt/preferences.d/50-pin-mir.pref file...

---

### Post by ventrical on 2013-06-26
> **zika said:**
> Just heads up: After excursion into Mir PPA and ppa-purge my LightDM goes into LowGraphicsMode... I'll sort that out, I hope, but just to report... Luckily I have GDM, startx, xinit, lot of other escape routes... ;)
Also, think about not using /etc/apt/preferences.d/50-pin-mir.pref file...

 I tried a lot of these same things earlier on. Thanks for the reminders. I am not preaching at anyone or trying to discourage anyone but. so far, for desktops, it's been a real disappointment. I was very enthusiastic at first, the demos were interesting .. etc.. I guess I'll just keep watching.

regards

---

### Post by zika on 2013-06-26
Except for two cursors I did not have any complaints on Mir running on my machine... Browser, LO (latest prerelease), many apps were running effortlessly... Trouble with two cursors made me jump out of that train yesterday but I left my door open PPA is on only I do not use file [COLOR=#000000]/etc/apt/preferences.d/50-pin-mir.pref anymore so upgrades are not constrained to MirPPA... The only scar I have from that excursion is LightDM that now does not work... (see above)... But I'm sure I'll sort that out once I need to or get enough time to think about that... That scar prevents me from getting into mir again, though...[/COLOR]

---

### Post by ventrical on 2013-06-26
Basically when they pulled the 'mir'  binary everything went south after that.  It was a real surprise for raring also. So , yesterday I used the saucy filter, removed the raring ppa;, installed the saucy ppa:  and it busted. Removed the saucy ppa and I have that system recovered. whew...

umm.. I'll keep at it though :)

Chris Rogers said they removed the 'mir'  binary because it was too confusing, but, now it is more confusing that ever !

2 cents worth :)

---

### Post by zika on 2013-06-26
Beauty[COLOR=#000000] is in the [/COLOR]eye[COLOR=#000000] of the [/COLOR]beholder[COLOR=#000000] - the meaning and origin of this saying.
I like it and it works...[/COLOR]

---

### Post by cariboo on 2013-06-27
I found this in my inbox this morning, from Oliver Ries:

> Hi,


My name is Olli Ries from Canonical and I am the Engineering Director for Unity and Mir. I wanted to give you an update on the roadmap for Ubuntu&#8217;s graphical stack over the next few releases.

Our Display Server Mir has gone from a proof of concept, sufficient to justify its announcement in March this year, to high quality, high performance component that we think will deliver the fastest, cleanest display experience for the Ubuntu platform. We are confident that all desktop environments and derivatives will work well throughout the transition, based on our ability to provide a full X compatibility layer.

Here is the roadmap and milestones for the Ubuntu graphics stack transition to Mir:

Ubuntu 13.10:
XMir on Mir by default, with a fallback session to X where there is no Mir driver support, supported for 9 months

Ubuntu 14.04 LTS:
XMir as default with the fallback session removed, full Mir driver support, traditional LTS support for 5 years

Ubuntu 14.10 and beyond:
Mir stack as default, including rootless X support for legacy X applications, supported for 9 months

XMir: X & Unity7 running on top of the system compositor Mir
Mir stack: Mir as system compositor with Unity 8 as session shell on top

Using Mir as a X compatible system compositor in 14.04 which can host any Desktop Environment that is running on X today, will allow all dependent Ubuntu derivatives to run on top of this stack in 13.10 and 14.04 without any changes needed on their side [1]. Canonical is committed to support XMir for 5 years during the 14.04 lifecycle, which will give derivatives enough time to evaluate the graphics stack landscape and to make informed decisions when they are ready.

There is good progress in getting XMir into a distro ready state. A PPA [2] was setup to allow early dogfooding, daily landing tests will be turned on for the full stack (XMir, X, Compiz, Unity), automated performance test results are about to be published on the Ubuntu QA dashboard, inclusion to universe is on it&#8217;s way and we are preparing the MIR (see what I did there ;) for Mir ahead of Feature Freeze. Quality and ship criteria will be assessed and made available at that time.

However, please be aware that the PPA today is still tagged experimental/testing and will see rapid changes over the next couple of weeks.  We will invite you for more widespread testing when ready.

Feel free to discuss any questions with the team directly here or on the mir-devel list.

Ubuntu will be the first Linux distribution to start replacing X as part of their default configuration. We appreciate your support and patience in that endeavor.

best,
Olli


[1]: various flavors running unmodified on top of XMir - [https://www.youtube.com/watch?v=8h0m-ZjPxe8](https://www.youtube.com/watch?v=8h0m-ZjPxe8)
[2]: System Compositor Testing PPA - [https://launchpad.net/~mir-team/+archive/system-compositor-testing](https://launchpad.net/~mir-team/+archive/system-compositor-testing)

---

### Post by dino99 on 2013-06-27
Looks like the Mir team is growing up and baking faster than initially drawn :p
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5NzM](http://www.phoronix.com/scan.php?page=news_item&px=MTM5NzM)

---

### Post by zika on 2013-06-27
> **cariboo907 said:**
> I found this in my inbox this morning, from Oliver Ries:Thank You for sharing this with us...

---

### Post by EgoGratis on 2013-06-27
Yes i think it makes sense to push Mir BUT currently i am a bit confused about all the PPAs:

This one should give us system compositor + Mir?

[https://launchpad.net/~mir-team/+archive/system-compositor-testing](https://launchpad.net/~mir-team/+archive/system-compositor-testing)

But ARM builds fails.

This one should give us Unity 8 on top of Mir?

[https://launchpad.net/~phablet-team/+archive/mir](https://launchpad.net/~phablet-team/+archive/mir)

But amd64 and i386 build failed.

Then there are core apps:

[https://launchpad.net/~ubuntu-touch-coreapps-drivers/+archive/daily](https://launchpad.net/~ubuntu-touch-coreapps-drivers/+archive/daily)

But to be able to test them QT5 and SDK PPA must be added?

[https://launchpad.net/~canonical-qt5-edgers/+archive/qt5-proper](https://launchpad.net/~canonical-qt5-edgers/+archive/qt5-proper)
[https://launchpad.net/~ubuntu-sdk-team/+archive/ppa](https://launchpad.net/~ubuntu-sdk-team/+archive/ppa)

Did i list everything concerning Ubuntu 13.10 tester or is there something i missed? Currently you can test Unity 8 on top of Mir if you own ARM device and you can test "plain console based Mir" on x86 and you can test core apps on x86? 

By the end of this dev cycle user should be able to use all of this by default if users has FOSS drivers installed if proprietary driver is used fallback to Xorg will happen but in Ubuntu 14.04 there will be just Mir and no Xorg anymore just Xmir for legacy apps? That surely indicates Nvidia will support Mir through EGL in my opinion and AMD will work at least with FOSS driver that is maturing:

 [http://www.phoronix.com/scan.php?page=news_item&px=MTM5NjE](http://www.phoronix.com/scan.php?page=news_item&px=MTM5NjE)

But i bet they will support Mir through EGL too. Bold move indeed but i guess i do like it and it makes sense to push once it was decided this is the way to go. About Wayland i guess i do look forward to see some (healthy) competition!

---

### Post by dino99 on 2013-06-27
pre-pre......pre alpha :lolflag:

---

### Post by grahammechanical on 2013-06-27
Well, I am there right now. I had a fresh install of saucy just waiting. No problems following those instructions. Not noticing any difference. but the code to find out if we are running on MIR is not very helpful

```
ps afx | grep unity-system-compositor
```

gives

> 3292 ?        Sl     0:00  \_ /usr/bin/unity-system-compositor --from-dm-fd 7 --to-dm-fd 13 --vt 7
3993 pts/13   S+     0:00                  \_ grep --color=auto unity-system-compositor

I suppose it would simply say unity instead of unity-system-compositor

The double vision cursors remind me of my old Maths teacher. He had eyes like a football team - one home and one away.

Regards.

---

### Post by zika on 2013-06-27
> **grahammechanical said:**
> Well, I am there right now. I had a fresh install of saucy just waiting. No problems following those instructions. Not noticing any difference. but the code to find out if we are running on MIR is not very helpful

```
ps afx | grep unity-system-compositor
```

gives



I suppose it would simply say unity instead of unity-system-compositor

The double vision cursors remind me of my old Maths teacher. He had eyes like a football team - one home and one away.

Regards.Since I am (kind of) a Maths teacher, maybe that is the source of the problem I had... Good to know... :P

---

### Post by grahammechanical on 2013-06-27
My wife says that she had a teacher with a similar affliction but he could hit a boy with a piece of chalk while looking somewhere else; Ah, the good old days of teaching. :)

I have noticed whilst posting on this forum that there is a slight delay in keyboard response. I do not know if that is a MIR effect. No crashes.

---

### Post by EgoGratis on 2013-06-27
[http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

---

### Post by QDR06VV9 on 2013-06-27
> **grahammechanical said:**
> My wife says that she had a teacher with a similar affliction but he could hit a boy with a piece of chalk while looking somewhere else; Ah, the good old days of teaching. :)

I have noticed whilst posting on this forum that there is a slight delay in keyboard response. I do not know if that is a MIR effect. No crashes.

Nope! I think it might have to do with the auto save feature..?:confused:

---

### Post by ventrical on 2013-06-27
> **EgoGratis said:**
> [http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

I get this gigantic UBUNTU at plymouth . then , I have to go to recovery, lighdm loads up, I log on and check 'about this computer ' and get this strange outcome:

---

### Post by ventrical on 2013-06-27
> **EgoGratis said:**
> [http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

Whoops .. followed everything to a 't'!

I get this for my graphics driver now... so I'm not really sure if it's working.

---

### Post by ventrical on 2013-06-27
> **ventrical said:**
> Whoops .. followed everything to a 't'!

I get this for my graphics driver now... so I'm not really sure if it's working.

Edit:

Thankfully I had btrfs on that saucy install (which is a work in progress)!! :) I am just baffled at how it rolled back seamlessly.

---

### Post by EgoGratis on 2013-06-27
> I get this for my graphics driver now... so I'm not really sure if it's working.

You will know when you have XMir on top of Mir running Unity 7 when you will get 2 mouse cursors.

> Right now (due to a bug that is almost a feature;) you will recognize  that Mir is running by having 2 mouse pointers (HW & SW mouse  pointer). This will go away and we will provide you with another more  obvious watermark to identify you are running on Mir.

[http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

I did manage to test it and i can confirm "lagging" when it comes to keyboard input and general 3D "lagging" when using Compiz snap effect for example on older ATI card running FOSS driver. Default Unity 7 on Xorg (Ubuntu 13.10) works without any noticeable lagging on this PC. I could test on Nouveau and Intel if i would install Ubuntu 13.10 on other boxes but i doubt the result would be different.

This will need to improve in my opinion if Mir (XMir on top of Mir running Unity 7) will be introduced by default in Ubuntu 13.10. There might be a chance the test was done without the access to full 3D GPU acceleration and that makes the difference compared to default Unity 7 on top of Xorg? Because the difference is really big like instant and fluid Compiz snap effect on Unity 7 running on top of Xorg and from 3 to 5 seconds of lagging Compiz snap animation effect when XMir on top of Mir running Unity 7 is used.

But OK at least now we are able to test it! Great!

---

### Post by dino99 on 2013-06-28
For testing purposes, a secondary software cursor is rendered in the upper-left hand corner as a simple indicator that Mir is being used. Canonical says though a better Mir watermark is forthcoming for indicating Mir is in use rather than just X. The other way to find out if XMir/Mir is in use is by checking the /var/log/Xorg.0.log for XMir and also seeing if the "unity-system-compositor" process is active on the system.

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_xmir_benchmark&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_xmir_benchmark&num=1)

[http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

---

### Post by zika on 2013-06-28
Sadly I did not get enough time yet to try to fix LowGraphicsMode LightDM starts in now at my place... Fault seems to be just mine because I've mixed too many PPAs in the process... I do hope that it will fix itself by converging all of these PPAs... But I do fear more than I really do hope... ;)
Update&#8321;: Finally, got some spare time, file /etc/apt/preferences.d/50-pin-mir.pref is essential... It is the only way to make upgrades &#8222;behave&#8220;... ;) Rude but true...
Back in two-cursor world...

---

### Post by grahammechanical on 2013-06-28
I did my first reboot of saucy+ext4+mir and I had to use Resume. Now that runs on llvmpipe and there is a definite slow motion effect with the minimizing and restoring of windows due to llvmpipe but the typing lag in this firefox window has gone. Strange that a subset of Nouveau should work better in one regard than the full Nouveau.

When I shutdown last night there was a rapid flashing as the screen tried to switch back and forth between the Plymouth shutdown screen and the Xserver Linux screen. I think that it interferred with the shutdown process.

---

### Post by EgoGratis on 2013-06-28
> Now that runs on llvmpipe and there is a definite slow motion effect  with the minimizing and restoring of windows due to llvmpipe but the  typing lag in this firefox window has gone.

Yes this was my first thougt what if llvmpipe is used when using Mir compared to hardware 3D when using default Xorg. I think this is reasonable explanation why the difference in performance was so big in my test.

---

### Post by jerrylamos on 2013-06-29
Being ignorant about all this, I just did a 
```
sudo add-apt-repository ppa:mir-team/staging
sudo apt-get update
sudo apt-get dist-upgrade
```
noted that lightdm was being kept back?
did a 
```
sudo apt-get -f install
```
nothing much.

Rebooted, is up and running.  About the only difference in the first few minutes is a alt-tab to switch windows from browser to terminal takes about a minute.
Cursor select on the windows runs O.K.

How do I tell what if anything Mir is running?  Thanks.

```
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) IGD 
OpenGL version string:  2.1 Mesa 9.2.0-devel

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

---

### Post by zika on 2013-06-29
> **jerrylamos said:**
> Being ignorant about all this, I just did a 
sudo add-apt-repository ppa:mir-team/staging
sudo apt-get update
sudo apt-get dist-upgrade
noted that lightdm was being kept back?
did a 
sudo apt-get -f install
nothing much.

Rebooted, is up and running.  About the only difference in the first few minutes is a alt-tab to switch windows from browser to terminal takes about a minute.
Cursor select on the windows runs O.K.

How do I tell what if anything Mir is running?  Thanks.

00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) IGD 
OpenGL version string:  2.1 Mesa 9.2.0-devel

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
[http://ubuntuforums.org/showthread.php?t=2157228&p=12705865#post12705865](http://ubuntuforums.org/showthread.php?t=2157228&p=12705865#post12705865)
(„code“ tags would make Your post much more readable...)

---

### Post by grahammechanical on 2013-06-29
> How do I tell what if anything Mir is running?

You should have two cursors - a whitearrow head that is  a real cursor and a black arrow head. There is a different PPA to use. You see it here in this blog post.

[http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

Join in and regards.

---

### Post by zika on 2013-06-29
I'm back in two-cursor world of Mir... 
[http://ubuntuforums.org/showthread.php?t=2157228&p=12709457#post12709457](http://ubuntuforums.org/showthread.php?t=2157228&p=12709457#post12709457) (Update&#8321;)
Update: Apt-tools proved itself in this and many other cases... Very good set of tools...

---

### Post by jerrylamos on 2013-06-29
Atter several tries, mangaged to get booted with Ollie's stuff.  Two cursors.
Sluggins keyboard.
External monitor is sset at 1920x1080, "unknown monitor", pretty tiny for a 15.5 inch flat screen TV.  Settings Displays calls it an  unknown  and won't set it to anything else. let me try xrandr.

---

### Post by EgoGratis on 2013-06-29
There is no multi monitor support yet.

---

### Post by ventrical on 2013-06-29
> **grahammechanical said:**
> Well, I am there right now. I had a fresh install of saucy just waiting. No problems following those instructions. Not noticing any difference. but the code to find out if we are running on MIR is not very helpful

```
ps afx | grep unity-system-compositor
```

gives



I suppose it would simply say unity instead of unity-system-compositor

The double vision cursors remind me of my old Maths teacher. He had eyes like a football team - one home and one away.

Regards.


I don't have the double vision cursor after a successful install of todays daily saucy on an older P4 machine with ATi graphics. It's a little slow .. but working, I presume.

---

### Post by ventrical on 2013-06-29
Mir gone mad on Saucy :)

ehehehehe

[http://www.youtube.com/watch?v=U7821es9LQs&feature=youtu.be](http://www.youtube.com/watch?v=U7821es9LQs&feature=youtu.be)

---

### Post by mc4man on 2013-06-29
> **ventrical said:**
> I don't have the double vision cursor after a successful install of todays daily saucy on an older P4 machine with ATi graphics. It's a little slow .. but working, I presume.

You may want to add this or something similar to any of your grep commands so you don't confuse the irrelevant to the relevant (or in above posted  case lack of

|grep -v grep

Ex. where mir is running (& pretty poor in regards to compiz
> $ ps afx | grep unity-system-compositor |grep -v grep
 1187 ?        Sl     0:01  \_ /usr/bin/unity-system-compositor --from-dm-fd 10 --to-dm-fd 13 --vt 7




---

### Post by mc4man on 2013-06-29
While it works ok to purge & return, at least here rebooted to low graphics screen. 
May have been useful if the recently linked instructions to test mir mentioned that when removing one should remove entirely or comment out the entry in 
/etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf

---

### Post by ventrical on 2013-06-29
> **mc4man said:**
> You may want to add this or something similar to any of your grep commands so you don't confuse the irrelevant to the relevant (or in above posted  case lack of

|grep -v grep

Ex. where mir is running (& pretty poor in regards to compiz

 I posted my youtube video in the previous post. Double cursor there. Mir Gone Mad. :)
 I had to run it from recovery mode, resume and then :
```

sudo service lightdm restart

```

yep .. and compiz pretty slow too.

---

### Post by jerrylamos on 2013-06-29
> **EgoGratis said:**
> There is no multi monitor support yet.
What it is doing is running the external monitor, a TV set plugged in to VGA, at 1920x1080 which is pretty hard to read but it does work when I remember to use the correct cursor..
Settings Displays calls it an unknown monitor with no other choice of resolution.  Settings Displays does not see the built in netbook screen.
xrandr calls the external monitor XMIR-1
The built in netbook should run at 1024x600.  It's doing a constant dizzy horizontal spin.
Let me see if I can turn xmir off.

Whew.  Worked fine.  Put a # in front of type=unity in the following file.
```

sudo gedit /etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf
[SeatDefaults]
#type=unity
```
then ```
sudo restart lightdm
```

---

### Post by EgoGratis on 2013-06-29
> Settings Displays does not see the built in netbook screen.

Probably it would if you would disconnect TV set first and then booted the netbook?

---

### Post by jerrylamos on 2013-06-29
> **EgoGratis said:**
> Probably it would if you would disconnect TV set first and then booted the netbook?
Didn't try that, the little netbook is hidden behind the TV.  I'm enjoyimg saucy at 1920x1080 instead of 1024x600 netbook screen..

BTW, with the MIR updates, and type=unity commented out, I'm getting some gorgeous full screen BBC videos of Stage1 of Tour de France.  That on a 1 GB Acer Aspire 1 netbook saucy amd64 3.10.0-1, dual 1.66 gHz Intel Atom on 1.5 MB internet.

Now for the next dread update....

---

### Post by cariboo on 2013-06-30
> **jerrylamos said:**
> Being ignorant about all this, I just did a 
```
sudo add-apt-repository ppa:mir-team/staging
sudo apt-get update
sudo apt-get dist-upgrade
```
noted that lightdm was being kept back?
did a 
```
sudo apt-get -f install
```
nothing much.

Rebooted, is up and running.  About the only difference in the first few minutes is a alt-tab to switch windows from browser to terminal takes about a minute.
Cursor select on the windows runs O.K.

How do I tell what if anything Mir is running?  Thanks.

```
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) IGD 
OpenGL version string:  2.1 Mesa 9.2.0-devel

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

The only real difference I can see between the output of /usr/lib/nux/unity_support_test -p -f on your system and mine, aside from the graphics card, is the mesa version:

```
/usr/lib/nux/unity_support_test -p -f
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA8
OpenGL version string:  3.0 Mesa 9.2.0-devel

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

BTW, the dual cursors, are really annoying. :-D

---

### Post by ventrical on 2013-06-30
> **grahammechanical said:**
> You should have two cursors - a whitearrow head that is  a real cursor and a black arrow head. There is a different PPA to use. You see it here in this blog post.

[http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

Join in and regards.


You can converge the two cursors into one by simply moving the cursor (arrow) all the way into the top left hand corner, but, it does not get rid of the flashy mouse arrow.

edit:

At least that is what I was able to do on an older ATi graphics adapter.

---

### Post by grahammechanical on 2013-06-30
> **mc4man said:**
> While it works ok to purge & return, at least here rebooted to low graphics screen. 
May have been useful if the recently linked instructions to test mir mentioned that when removing one should remove entirely or comment out the entry in 
/etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf

> [COLOR=#666666][FONT=Ubuntu]In order to switch Mir off/on temporarily, one simply needs to manually edit /etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf[/FONT][/COLOR]

[SeatDefaults]
type=unity
[COLOR=#666666][FONT=Ubuntu]
Simply comment the 2nd line out if you want to turn of Mir and go back to X instead[/FONT][/COLOR]

[SeatDefaults]
#type=unity
[COLOR=#666666][FONT=Ubuntu]
If you want to go back to Mir, well, you know what to do. Any change must be followed by a restart of lightdm from a console/VT in order to take effect.[/FONT][/COLOR]

$> sudo restart lightdm

Regards.

---

### Post by jerrylamos on 2013-06-30
Still playing around with Mir on netbook dual screen.  Flip back and forth with the #type=unity vs. type=unity.  

Both the netbook built in and the external TV are running, though with max resolution on the TV I should be using a magnifying lens.

At this stage I've been told external monitor isn't supported but it does run.  There isn't any support for settings displays either.

And as reported previously keyboard response is slow.

Some actions like Alt-Tab very slow, also selections on the applets on top right of the desktop are very slow.

Has not been crashing.  I've sure had a lot of X crashes in the past.

Did an update today, anything else I should be doing to keep up with the ppa?

Thanks.

p.s. saucy was getting pretty boring.  Nice to try some half-baked code.

---

### Post by EgoGratis on 2013-06-30
> At this stage I've been told external monitor isn't supported but it  does run.  There isn't any support for settings displays either.

Yes as i said earlier multi monitor support is not available yet.

> p.s. saucy was getting pretty boring.  Nice to try some half-baked code.

I agree.

---

### Post by buzzingrobot on 2013-06-30
I've upgraded 13.04 to 13.10. It's an Nvidia card. Is it safe to say that if the system is happy with Nouveau, it will be happy with Mir? Or, is Mir only safe for Intel at the moment?

---

### Post by sanderj on 2013-06-30
FWIW:

I'm joing this thread: based on [http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/) I've activated Mir on my Saucy on my laptop, and ... it just works.

- I do have the two mouse pointers, which both move when I use my USB mouse. Annoying
- When I only use my touchpad, the big ugly mouse pointer does not move. So that is a workaround for me
- Yesterday I had several X and plymouth crashes. No crashes today. Mabye because I now use my touchpad?
- I'm running Mir on two laptops, and both laptops have an Intel GPU.

---

### Post by deadflowr on 2013-06-30
Mir is suppose to work on the open-source drivers for radeon,intel and nouveau.

Whether or not it actually does is to be determined.

---

### Post by grahammechanical on 2013-06-30
At the moment MIR is supposed to work with graphic cards that can run suitably with an open source driver be it Nouveau, Intel or Raedon. Canonical is working with Nvidia and ATI to get them modifying their proprietary drivers to work with MIR.

You might want to look at these to links

[http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

[http://ubuntuforums.org/showthread.php?t=2157228](http://ubuntuforums.org/showthread.php?t=2157228)

That second link is a forum thread where some of us have been recounting our experiments with saucy+mir. You are welcome to join in.

I have an Nvidia GT 220 and I have one saucy install with Nvidia and one with Nouveau and MIR. And apart from one or two small things I would not know the difference. Not from using the OS.

Regards.

---

### Post by cariboo on 2013-06-30
See my post [here]("http://ubuntuforums.org/showthread.php?t=2157228&p=12711908&viewfull=1#post12711908"). The only thing I've noticed is the graphics adapter temp, is a bit higher than when using the closed source driver.

---

### Post by sanderj on 2013-07-01
Update:

Just had a 'hang': my touchpad could not control the 'real' mouse pointer anymore. The USB mouse could control the big mouse pointer (which is not so useful). I did a CTRL ALT F1, and then a "sudo restart lightdm" which killed the GUI session.

---

### Post by buzzingrobot on 2013-07-01
Ah, that didn't work so well. :-?

Followed the steps at ollie-ries. Things locked up restarting LightDM.  Took 3 reboots before LightDM showed up and I could log in. The launcher and the panel weren't there, but the two mouse cursors were. 

When I removed and purged Mir, the system booted up into the low-resolution warning. Tried twice to reboot into recovery mode, but couldn't move the cursor or otherwise edit the Grub menu.  Got there on the third reboot. Opened a shell and installed an Nvidia driver.  Rebooted, into a high-resolution display of the low-resolution warning, and no mouse or keyboard.

C'est la vie.  Think I'll wait.  Off to reinstall.

---

### Post by zika on 2013-07-01
> **buzzingrobot said:**
> Ah, that didn't work so well. :-?

Followed the steps at ollie-ries. Things locked up restarting LightDM.  Took 3 reboots before LightDM showed up and I could log in. The launcher and the panel weren't there, but the two mouse cursors were. 

When I removed and purged Mir, the system booted up into the low-resolution warning. Tried twice to reboot into recovery mode, but couldn't move the cursor or otherwise edit the Grub menu.  Got there on the third reboot. Opened a shell and installed an Nvidia driver.  Rebooted, into a high-resolution display of the low-resolution warning, and no mouse or keyboard.

C'est la vie.  Think I'll wait.  Off to reinstall.Install GDM so You could use that install...
I'm yet to find a route backwards once LightDM from Mir PPA fails... I'm on ATI...
GDM is good to have either way...

Update&#8321;: Or SlIM, I forgot to mention...

---

### Post by mc4man on 2013-07-01
> **buzzingrobot said:**
> 
When I removed and purged Mir, the system booted up into the low-resolution warning. Tried twice to reboot into recovery mode, but couldn't move the cursor or otherwise edit the Grub menu.  Got there on the third reboot. Opened a shell and installed an Nvidia driver.  Rebooted, into a high-resolution display of the low-resolution warning, and no mouse or keyboard.

C'est la vie.  Think I'll wait.  Off to reinstall.
I mentioned here that the instructions for **removing **mir failed to mention something ...
[http://ubuntuforums.org/showthread.php?t=2157228&p=12711473&viewfull=1#post12711473](http://ubuntuforums.org/showthread.php?t=2157228&p=12711473&viewfull=1#post12711473)

---

### Post by grahammechanical on 2013-07-01
> **sanderj said:**
> Update:

Just had a 'hang': my touchpad could not control the 'real' mouse pointer anymore. The USB mouse could control the big mouse pointer (which is not so useful). I did a CTRL ALT F1, and then a "sudo restart lightdm" which killed the GUI session.

If it happens again - it usually does - you could try unplugging the mouse and plugging it back in. You never know, it might be a gentler way of getting things going a gain.

Regards

---

### Post by zika on 2013-07-01
> **mc4man said:**
> I mentioned here that the instructions for **removing **mir failed to mention something ...
[http://ubuntuforums.org/showthread.php?t=2157228&p=12711473&viewfull=1#post12711473](http://ubuntuforums.org/showthread.php?t=2157228&p=12711473&viewfull=1#post12711473)I'm afraid that that is not a cure for problems given above... It is a step in right direction, but...

---

### Post by ventrical on 2013-07-01
So far I have had several non-working installs of  the new mir+saucy across different form factors. The best fallback I have found , other than a complete re-install is the btrfs filesystem . I can always get back to my original (or previous) before upgrade of :ppas to mir. I know it is not a cure but it offers a solution to the downtime involved.

---

### Post by grahammechanical on 2013-07-01
I have just put in another saucy+btrfs install from today's ISO image. I am glad to see that Ubiquity is no longer crashing. I have just put in MIR and I have noticed an improvement. The delayed insertion point response in documents has gone. I can type normally. I had to double check that I was on mir. Yes, I do have 2 cursors. By that I mean I still make plenty of typos but  I cannot blame MIR/Nouveau.

CORRECTION. Typing is fine. The issue appears whenI backspace. The insertion stops and then jumps one character space. It makes typo correction screamingly difficult.

I do not think that sudo restart lightdm is the correct code even when used with a tty. I got a blackscreen with flashing cursor. Everything fine after a reboot. No low graphic mode. I think that a shutdown and reboot might be bettter. I will test it out.

I am on btrfs because I want to install the various alternative desktops to see how they fair on MIR. So, I may need a rollback method. I have taken a snapshot of the base system. Now to take a snapshot of the base system+mir and then add Xbuntu desktop.

Regards.

UPDATE: This is proving more difficult than I thought. I can find Gnome shell in the saucy software centre but not the desktops of Kubuntu, Lubuntu and Xubuntu.

UPDATE 2: The alternative desktops are in Synaptic. I am now typing this from the Xubuntu desktop on Ubuntu+btrfs+mir. It all seems fine. Log out and log in failed. Got a glimpse of the log in screen then a black screen with the white cursor frozen. Rebooted fine.

UPDATE 3: The Kubuntu broke the reboot. Either that or it is saucy+btrfs playing its usual game of will she, won't she load to a login screen. I rollback to before I install Kubuntu desktop but I messed up the rollback commands and still could not boot. But it is fixed now. I am back in or either  Ubuntu or Xubuntu.

UPDATE 4: I tried again. This time with Lubuntu desktop. I am there right now posting this. I have noticed that we do not get the two cursors with llvmpipe (recovery resume) and that Xubuntu plymouth spash screen has taken over. A lot of stuff comes in with each desktop. Lubuntu has added a Lubuntu Nexus 7 to the login options. Now, that is what is called over-compensating.

UPDATE 5: I have just put in Gnome Shell and it also is running on Ubuntu saucy and mir. I am getting a collection of applications. Some are duplicates.

UPDATE 6: Final update for tonight. I am now working on Kubuntu desktop on Ubuntu+btrfs+mir with Unity, Xubuntu, Lubuntu, Gnome Shell & Kubuntu desktops all available form the log in screen.

---

### Post by cecilpierce on 2013-07-01
Nvidia card, nouveau driver and on 4 saucys all I get is black screen and mouse pointer, think I'll quit for awhile or until some thing new pops up :confused:

ps have 32 and 64bit saucy

---

### Post by cecilpierce on 2013-07-01
After just black screen and pointer I did:
[SeatDefaults]
#type=unity
and now flashy orange, yellow and green top and side panels, every nice :(

---

### Post by mc4man on 2013-07-01
> **zika said:**
> I'm afraid that that is not a cure for problems given above... It is a step in right direction, but...

I'd say that it's quite likely it would have solved the Op's reboot into low graphics after purging the mir ppa. 
(unless he happened to remove or comment out the entry in that file..

---

### Post by zika on 2013-07-01
> **mc4man said:**
> I'd say that it's quite likely it would have solved the Op's reboot into low graphics after purging the mir ppa. 
(unless he happened to remove or comment out the entry in that file..My experience is different... But, that should not be general... ;)

I do remeber: &#8222;USE THESE AT YOUR OWN RISK. BE PREPARED TO MANUALLY FIX YOUR SYSTEM IF IT BREAKS.&#8220; and I stand warned...
It did nor break... ;) Would not dare in front of me... ;)

---

### Post by zika on 2013-07-01
We all were properly warned: &#8222;USE THESE AT YOUR OWN RISK. BE PREPARED TO MANUALLY FIX YOUR SYSTEM IF IT BREAKS.&#8220;...
It did not break... ;)

Should not these two topics be merged:
[http://ubuntuforums.org/showthread.php?t=2158811](http://ubuntuforums.org/showthread.php?t=2158811)
[http://ubuntuforums.org/showthread.php?t=2157228](http://ubuntuforums.org/showthread.php?t=2157228)
...?

---

### Post by cariboo on 2013-07-01
Merged to similar threads.

---

### Post by NikTh on 2013-07-01
After the latest updates, xmir died with signal 6. I have been reported this as a [bug]("https://bugs.launchpad.net/mir/+bug/1196355"). Everything messed up, I cannot even start the display manager, I cannot even switch to a VT. Only SysRq can reboot the system. 

Also a test case of Mir **native** in 13.10 can be found [here]("https://www.youtube.com/watch?v=zil-lRNlaks"). Sorry for the poor quality, I must buy a new cam.. some day :P

---

### Post by jerrylamos on 2013-07-01
Gave up on the mess and did a fresh zsync, fresh install, fumbled around with Ollie's notes and the ppa stuff, wound up with duplicate sources.list entries, and

It's working.  Dual cursors and all.  I'm using the external monitor as I type.  ??

Pretty soon it'll figure out it is not supposed to be working and crash, but not yet.

BTW, anyone trying the unity 8 ppa on top of this mess yet?

---

### Post by buzzingrobot on 2013-07-01
> **mc4man said:**
> I'd say that it's quite likely it would have solved the Op's reboot into low graphics after purging the mir ppa. 
(unless he happened to remove or comment out the entry in that file..

Nope, I didn't.  I'll remember the next time I give it a try.

---

### Post by jerrylamos on 2013-07-01
> **EgoGratis said:**
> Yes i think it makes sense to push Mir BUT currently i am a bit confused about all the PPAs:

This one should give us system compositor + Mir?

[https://launchpad.net/~mir-team/+archive/system-compositor-testing](https://launchpad.net/~mir-team/+archive/system-compositor-testing)

But ARM builds fails.

This one should give us Unity 8 on top of Mir?

[https://launchpad.net/~phablet-team/+archive/mir](https://launchpad.net/~phablet-team/+archive/mir)

O.K., I'm running the mir thing, dual cursors sluggish keyboard and all, and tried the unity8 ppa, and rebooted.  Any pointers on what to do to try unity8?

Thanks.  

BTW, I'm no unity fan, I just run it to report bugs.  On my tablets 7" 9" 10" I try to set them to "desktop" where possible.

---

### Post by EgoGratis on 2013-07-01
> Any pointers on what to do to try unity8?

I guess ATM you could test it on ARM based device but reading this:

[http://iloveubuntu.net/lightdm-174-landed-ubuntu-1310-mir-based-unity-support](http://iloveubuntu.net/lightdm-174-landed-ubuntu-1310-mir-based-unity-support)

I think Unity 8 could land on some PPA or to be directly available in Ubuntu 13.10 soon. AFAIK this is the plan to have demo Unity 8 session (mobile one) available in Ubuntu 13.10 and because Unity 8 will not talk X11 anymore it will use Mir directly and not XMir anymore! If you have any ARM  device you would put Ubuntu on you could use that PPA for test i guess but if u want to test it on your netbook you have to wait a bit more.

---

### Post by ventrical on 2013-07-01
On Lubuntu, mir is running unimpeded with only one cursor on a fresh, daily, saucy desktop-i386.

```

ventrical@ventrical-P4M266A-8237:~$ ps afx | grep unity-system-compositor
 2619 pts/0    S+     0:00      \_ grep --color=auto unity-system-compositor
ventrical@ventrical-P4M266A-8237:~$ ps aux | grep unity-system-compositor
1000      2634  0.0  0.0   5664   816 pts/0    S+   17:54   0:00 grep --color=auto unity-system-compositor
ventrical@ventrical-P4M266A-8237:~$ grep -i xmir /var/log/Xorg.0.log
[   175.289] xorg-server 2:1.13.3+xmir1-0 (For technical support please see http://www.ubuntu.com/support) 
ventrical@ventrical-P4M266A-8237:~$ ls -l /var/log/lightdm/unity-system-compositor.log
-rw------- 1 root root 110 Jul  1 17:48 /var/log/lightdm/unity-system-compositor.log
ventrical@ventrical-P4M266A-8237:~$ 

```

edit 

hmmmm .. nope .. I don't think so because xorg is comming up in system monitor.

edit:

but all other indicators point that it is running ..

---

### Post by mc4man on 2013-07-01
what would be interesting here concerning unity8 (no compiz), will be whether it has h tearing. Atm  xmir brings it back,  even worse if I kill off compiz & unity.

As far as unity7/compiz/xmir - if tearing isn't eliminated then it's just one big step back.

---

### Post by jerrylamos on 2013-07-01
> **ventrical said:**
> On Lubuntu, mir is running unimpeded with only one cursor on a fresh, daily, saucy desktop-i386.

hmmmm .. nope .. I don't think so because xorg is comming up in system monitor.
unity here, dual cursors.  on a terminal window the highest users are
Xorg
compiz
chrome
unity-system-co
top
...

With dual cursors and other symptoms I'm pretty sure it's running xMir.

---

### Post by mc4man on 2013-07-01
> **ventrical said:**
> On Lubuntu, mir is running unimpeded with only one cursor on a fresh, daily, saucy desktop-i386.

```

ventrical@ventrical-P4M266A-8237:~$ ps afx | grep unity-system-compositor
 2619 pts/0    S+     0:00      \_ grep --color=auto unity-system-compositor
ventrical@ventrical-P4M266A-8237:~$ ps aux | grep unity-system-compositor
1000      2634  0.0  0.0   5664   816 pts/0    S+   17:54   0:00 grep --color=auto unity-system-compositor


```

edit 

hmmmm .. nope .. I don't think so because xorg is comming up in system monitor.

"\_ grep -color=auto unity-system-compositor" is just grep returning a result on itself
(that's why I mentioned you should add a |grep -v grep so as not to get confused by meaningless result

---

### Post by grahammechanical on 2013-07-01
I have itemized my progress today in an earlier post. Just to re-cap, I now have Saucy+mir running Unity, Xubuntu, Lubuntu, Gnome Shell & Kubuntu desktops (not all at once). Taking into account the usual issues of running a development branch just past Alpha stage on a developmental display manager, I would say that things are working well. There are problems logging out and in and with Restart. But shutdown is snappy.  Dare I try Cinnamon? It is in the software centre. Well, I am also on btrfs. So, if something breaks it is easy enough to do a roll back. Something for tomorrow, may be.

Regards.

---

### Post by mc4man on 2013-07-01
> **grahammechanical said:**
> I have itemized my progress today in an earlier post. Just to re-cap, I now have Saucy+mir running Unity, Xubuntu, Lubuntu, Gnome Shell & Kubuntu desktops (not all at once). Taking into account the usual issues of running a development branch just past Alpha stage on a developmental display manager, I would say that things are working well. There are problems logging out and in and with Restart. But shutdown is snappy.  Dare I try Cinnamon? It is in the software centre. Well, I am also on btrfs. So, if something breaks it is easy enough to do a roll back. Something for tomorrow, may be.

Regards.
A few neg i've noticed other than the obvious with slow typing/cursor & the aforementioned h tearing - 
Here after login plymouthhd tends to max 1 core for no good reason, killing it off shows no ill effects
(maybe erroneous reporting, maybe not.
Shutdown/restarts are good, logouts remain awful, around 10 sec's (current bug on some hardware

---

### Post by ventrical on 2013-07-01
> **mc4man said:**
> "\_ grep -color=auto unity-system-compositor" is just grep returning a result on itself
(that's why I mentioned you should add a |grep -v grep so as not to get confused by meaningless result

I did add that and it did nothing.

Thanks for your observations.

I'll have to try some other systems around here. Iv'e only been successful on one machine so far with ATi graphics.

---

### Post by mc4man on 2013-07-01
> **ventrical said:**
> I did add that and it did nothing.

If you ran ps afx | grep unity-system-compositor |grep -v grep & got nothing then it's the proper result if unity-system-compositor  is not running

Ex. I'm back on **13.04**, no mir, no nothing - 
> :~$ ps afx | grep unity-system-compositor |grep -v grep
doug@doug-XPS-M1330:~$
> :~$ ps afx | grep unity-system-compositor 
 2659 pts/0    S+     0:00      \_ grep --color=auto unity-system-compositor
doug@doug-XPS-M1330:~$

---

### Post by ventrical on 2013-07-01
> **mc4man said:**
> If you ran ps afx | grep unity-system-compositor |grep -v grep & got nothing then it's the proper result if unity-system-compositor  is not running

Ex. I'm back on **13.04**, no mir, no nothing -

Yes . I see .. thanks. Obviously mir is not running on this fresh Lubuntu install on a machine that runs Ubuntu saucy (Unity) just fine under mir.

Thanks again..

back to the drawing board :)
edit*
ahhh.. I highly suspect that my KVM switcher is not supported.

---

### Post by zika on 2013-07-02
> **mc4man said:**
> "\_ grep -color=auto unity-system-compositor" is just grep returning a result on itself
(that's why I mentioned you should add a |grep -v grep so as not to get confused by meaningless result
Here we go another round... Did not we have this sorted in first thread about Mir... ? ;)

---

### Post by jerrylamos on 2013-07-02
Mir running (or is it xmir) O.K. however the only screen resolution (x)mir will do on this 15.5" TV external monitor is it's max resolution of 1920x1080 which although sharp is pretty small for my eyes.  Dual cursors are a bit confusing but usable.  systems settings displays won't set resolution, and xrandr isn't successful either although it does call the screen XMIR-1 instead of normal VGA1.  

So after checking things out for obvious bugs I boot 13.10.0-1 normal xwindows at 1360x768 which is a comfortable read.  I've got a 1440x900 external monitor to try - it's drying out after getting splashed with houseplant water.

---

### Post by zika on 2013-07-02
Just to report: patience payed off: LightDM works again...

---

### Post by cecilpierce on 2013-07-02
Im lost in this mess, sometimes it works and sometimes it just goes blank screen.
Just did dist-upgrade and it boots up with the colored panels and top says xorg is working ???
I have type=unity in /etc/lightdm.d/10-unity-system-compositor.conf, any ideas or did I do something else wrong, hmmmm!

---

### Post by zika on 2013-07-02
> **cecilpierce said:**
> Im lost in this mess, sometimes it works and sometimes it just goes blank screen.
Just did dist-upgrade and it boots up with the colored panels and top says xorg is working ???
I have type=unity in /etc/lightdm.d/10-unity-system-compositor.conf, any ideas or did I do something else wrong, hmmmm!Why xorg should not work? Mir is still working atop X...

---

### Post by cecilpierce on 2013-07-02
> **zika said:**
> Why xorg should not work? Mir is still working atop X...

Oh! ok thanks, I didn't know that. I'm still confused by all the reading I've doing latley.

Does anyone else have those red green and yellow lines in the top and side docks ?

They turn off and on on the side but the top stays on, but if I point the mouse up in the top and click it shows what your pointing at.

---

### Post by balloons on 2013-07-02
Just a friendly reminder if you wish to utilize the tracker to report and track your results, they would be most appreciated I'm sure. Cadence testing this cycle has a bit of a twist in that we're tracking packages over the course of the cycle. You'll be able to see and view historical results as we go and reference a common buglist of stuff found by you and other testers. Here's the testcase for Xmir :-)

[http://packages.qa.ubuntu.com/qatracker/milestones/298/builds/47622/testcases/1572/results](http://packages.qa.ubuntu.com/qatracker/milestones/298/builds/47622/testcases/1572/results)

---

### Post by mc4man on 2013-07-02
> **cecilpierce said:**
> Oh! ok thanks, I didn't know that. I'm still confused by all the reading I've doing latley.

Does anyone else have those red green and yellow lines in the top and side docks ?

They turn off and on on the side but the top stays on, but if I point the mouse up in the top and click it shows what your pointing at.

The 1st time I used this did get the yellow bar, this time it hasn't appeared.
If you had used ppa-purge before, then added repo back & updated ect as per link you should check & make sure the unity-system-compositor package is installed (didn't get installed the 2nd time around here.

If you run that grep command it'll tell you if unity-system-compositor is running or in top, if you pick up & shake a window it should show up - screen (also shows plymouthd after login getting pegged

---

### Post by monkeybrain2012 on 2013-07-02
Hi,

Yesterday I was trying to give it a spin following the instructions here [http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)
However, after restarting lightdm I got a blackscreen with only a white arrow (which is movable). Rebooting get a big blank blackscreen with no error or nothing. 
It is a fresh install of Saucy's daily build from yesterday. I do have a Nvidia card but I wasn't using any proprietary driver. 
Is there a way to fix it instead of reinstalling?

Thanks

Edit: I have also installed the Compiz experimental ppa [https://launchpad.net/~smspillaz/+archive/compiz-experimental](https://launchpad.net/~smspillaz/+archive/compiz-experimental) It fixes many problems in the default version. Perhaps I should have purged it before I tried mir but if xmir works as advertised then it shouldn't matter, right?

---

### Post by cecilpierce on 2013-07-02
@mc4man

I don't see unity-system-compositor or plymouthd in top, I tried reinstall unity-system-compositor.

What was the grep cmd ? I think I tried the wrong one.

Thanks

---

### Post by mc4man on 2013-07-02
> **cecilpierce said:**
> @mc4man

I don't see unity-system-compositor or plymouthd in top, I tried reinstall unity-system-compositor.

What was the grep cmd ? I think I tried the wrong one.

Thanks
```
ps afx | grep unity-system-compositor

```

---

### Post by grahammechanical on 2013-07-02
I have just tried

```
ps afx | grep unity-system-compsi
```

with the deliberate spelling mistake and it produces the same kind of result as the the code with the correct spelling. I think that all we are doing is a "hallo world" kind of thing. I would like a definite method of knowing that Xmir is running. Reason? I just put Mir on an install of Kubuntu and I do not get the two cursors or any of the other little indications that Mir gives us.

By the way, I do not run restart lightdm. I think that it is better to shutdown and reboot. 

Regards.

---

### Post by sanderj on 2013-07-02
Olli's page only says:

> You can also simply check if the system compositor process is running:

$> ps afx | grep unity-system-compositor

... but not what to expect. :-(

However, I would *expect* more lines than just the grep line itself. However, I do not get those. Oh, wait, the ugly second mouse pointer is also gone. Maybe I'm not running Mir anymore .... ?

---

### Post by mc4man on 2013-07-02
definitive atm would be 2 cursors
as far as grep - 
This is when it's running, blue matters, **red doesn't**, not now, not ever
> ~$ ps afx | grep unity-system-com
 [COLOR="#000080"]1172 ?        Sl     0:00  \_ /usr/bin/unity-system-compositor --from-dm-fd 9 --to-dm-fd 13 --vt 7[/COLOR]
 [COLOR="#FF0000"]2297 pts/11   S+     0:00          |       \_ grep --color=auto unity-system-com[/COLOR]


If you misspell you will only return grep on grep (color=auto), the red above (meaningless

---

### Post by sanderj on 2013-07-02
OK, the other laptop still has the other, large, useless mouse pointer. So here we go:

```
sander@flappie:~$ ps afx | grep unity-system-compositor
 1630 ?        Sl     0:01  \_ /usr/bin/unity-system-compositor --from-dm-fd 10 --to-dm-fd 13 --vt 7
 5843 pts/9    S+     0:00          |       \_ grep --color=auto unity-system-compositor

sander@flappie:~$ ps ax | grep unity-system-compositor 
 1630 ?        Sl     0:03 /usr/bin/unity-system-compositor --from-dm-fd 10 --to-dm-fd 13 --vt 7
 7227 pts/9    S+     0:00 grep --color=auto unity-system-compositor


sander@flappie:~$ ps ax | grep unity-system-compositor | grep -vi grep
 1630 ?        Sl     0:03 /usr/bin/unity-system-compositor --from-dm-fd 10 --to-dm-fd 13 --vt 7
sander@flappie:~$ 



```

So ... can others verify that:


```
ps ax | grep unity-system-compositor | grep -vi grep
```

gives output on systems running Mir, but not on systems not running Mir?

---

### Post by cecilpierce on 2013-07-02
> **grahammechanical said:**
> I have just tried

```
ps afx | grep unity-system-compsi
```

with the deliberate spelling mistake and it produces the same kind of result as the the code with the correct spelling. I think that all we are doing is a "hallo world" kind of thing. I would like a definite method of knowing that Xmir is running. Reason? I just put Mir on an install of Kubuntu and I do not get the two cursors or any of the other little indications that Mir gives us.

By the way, I do not run restart lightdm. I think that it is better to shutdown and reboot. 

Regards.

I tried the same thing, got the same results, must be something missing.

---

### Post by cecilpierce on 2013-07-02
After all above posts I guess im not runnimg xmir !

---

### Post by W00ster on 2013-07-02
> **mc4man said:**
> 
|grep -v grep



$ alias grep="grep -v grep"

---

### Post by grahammechanical on 2013-07-02
> Oh, wait, the ugly second mouse pointer is also gone. Maybe I'm not running Mir anymore .... ?

I think the dualing cursors have been fixed. Today I installed the flavours with a view to putting them on mir. A couple of hours ago I set Kubuntu up with mir and then Lubuntu. Both had single cursors. Next I went into Saucy Ubuntu that was already on mir and had the cursed cursors + all the alternative desktops and after I run update and rebooted there is only one cursor. Included in the update was stuff regarding unity-system-compositor. And yet when I run that code for checking I do not get any blue writing but the red that we are all seeing.

I have also noticed that if we boot with recovery>resume that brings in llvmpipe and that only had one cursor anyway.

UPDATE: I have just gone back onto the official mir wiki and not only is the site now in keeping with Ubuntu design specifications but I also found this

> In theory, you should now find yourself back in Ubuntu and not notice  anything different. You can verify you're in Mir several ways:

```
ps aux | grep unity-system-compositor
```
```
grep -i xmir /var/log/Xorg.0.log
```
```
ls -l /var/log/lightdm/unity-system-compositor.log
```

[http://unity.ubuntu.com/mir/using_mir_on_pc.html](http://unity.ubuntu.com/mir/using_mir_on_pc.html)

And this is what I get

> graham@sda4-saucy-btrfs:~$ ps aux | grep unity-system-compositor
graham    2849  0.0  0.0  13648   952 pts/0    S+   23:46   0:00 grep --color=auto [COLOR=#ff0000]unity-system-compositor[/COLOR]

> graham@sda4-saucy-btrfs:~$ grep -i xmir /var/log/Xorg.0.log
[    27.559] xorg-server 2:1.13.3+[COLOR=#ff0000]xmir[/COLOR]1-0 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))

> graham@sda4-saucy-btrfs:~$ ls -l /var/log/lightdm/unity-system-compositor.log
-rw------- 1 root root 2280 Jul  2 23:27 /var/log/lightdm/unity-system-compositor.log

I am glad that the devs are updating the wiki.

Regards.

---

### Post by mc4man on 2013-07-02
> **grahammechanical said:**
>  whatever
.
You're not running it. unity-system-compositor has to be  running

Last time in full - when it's up - 
> ps afx | grep unity-system-com |grep -v grep
 1138 ?        Sl     0:01  \_ [COLOR="#0000CD"]/usr/bin/unity-system-compositor[/COLOR] --from-dm-fd 10 --to-dm-fd 13 --vt 7


> grep -i xmir /var/log/Xorg.0.log
[    26.326] xorg-server 2:1.13.3+xmir1-0 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    26.346] (II) LoadModule: "xmir"
[    26.346] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
[    26.380] (II) Module xmir: vendor="X.Org Foundation"
[    26.654] (II) NOUVEAU(0): Output XMIR-1 has no monitor section
[    26.654] (II) NOUVEAU(0): Printing probed modes for output XMIR-1
[    26.654] (II) NOUVEAU(0): Modeline "XMIR mode of death"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz eP)
[    26.654] (II) NOUVEAU(0): Output XMIR-1 connected
[    26.654] (II) NOUVEAU(0): Output XMIR-1 using initial mode XMIR mode of death
[    26.654] (**) NOUVEAU(0):  Driver mode "XMIR mode of death": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 59.9 Hz
[    26.654] (II) NOUVEAU(0): Modeline "XMIR mode of death"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz eP)

edit: some lightbulb absurdness
> 
doug@doug-XPS-M1330:~$ ps afx | grep grep
 2743 pts/0    S+     0:00                  \_ [COLOR="#FF0000"]grep[/COLOR] --color=auto [COLOR="#FF0000"]grep[/COLOR]

doug@doug-XPS-M1330:~$ ps afx | grep grep |grep -v grep
doug@doug-XPS-M1330:~$
> 
doug@doug-XPS-M1330:~$ ps afx | grep Axis-bold-as-love
 2746 pts/0    S+     0:00                  \_ grep --color=auto [COLOR="#FF0000"]Axis-bold-as-love[/COLOR]


---

### Post by grahammechanical on 2013-07-02
This is what I see in /var/log/lighdm/lightdm.log

> [+3.63s] DEBUG: Launching process 1292: /usr/sbin/unity-system-compositor --from-dm-fd 10 --to-dm-fd 13 --vt 7
> [+3.63s] DEBUG: Waiting for system compositor for 60s
> [+4.02s] DEBUG: Compositor closed communication channel
[+4.02s] DEBUG: Process 1292 exited with return value 1
[+4.02s] DEBUG: Releasing VT 7
[+4.02s] DEBUG: Compositor failed to start, switching to VT mode

But why?

---

### Post by ventrical on 2013-07-02
I tried mac4mans method even with the two cursors running and still did not get the 'blue' code.  In some other instances I think we are being rolled back to Xorg because I'll notice some really strange flickering, two cursors, then one , flash and then a stable X screen.

I think mac is right though.

---

### Post by grahammechanical on 2013-07-02
I have just rolled back to the system state on 01/07/2013 (advantage of being on btrfs) and I now have the curse of the two cursors back and this is what I get with those three commands for the mir wiki

> graham@sda4-saucy-btrfs:~$ ps aux | grep unity-system-compositor
root      1391  0.8  1.9 735396 19840 ?        Sl   03:04   0:01 /usr/bin/[COLOR=#ff0000]unity-system-compositor[/COLOR] --from-dm-fd 7 --to-dm-fd 13 --vt 7
graham    2651  0.0  0.0  13652   952 pts/0    S+   03:06   0:00 grep --color=auto[COLOR=#ff0000] unity-system-compositor[/COLOR]

> graham@sda4-saucy-btrfs:~$ grep -i xmir /var/log/Xorg.0.log
[    25.949] xorg-server 2:1.13.3+[COLOR=#ff0000]xmir[/COLOR]1-0 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    26.027] (II) LoadModule: "[COLOR=#ff0000]xmir[/COLOR]"
[    26.027] (II) Loading /usr/lib/xorg/modules/extensions/lib[COLOR=#ff0000]xmir[/COLOR].so
[    26.067] (II) Module [COLOR=#ff0000]xmir[/COLOR]: vendor="X.Org Foundation"
[    26.280] (II) NOUVEAU(0): Output [COLOR=#ff0000]XMIR[/COLOR]-1 has no monitor section
[    26.280] (II) NOUVEAU(0): Printing probed modes for output [COLOR=#ff0000]XMIR[/COLOR]-1
[    26.280] (II) NOUVEAU(0): Modeline "[COLOR=#ff0000]XMIR[/COLOR] mode of death"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[    26.280] (II) NOUVEAU(0): Output [COLOR=#ff0000]XMIR[/COLOR]-1 connected
[    26.280] (II) NOUVEAU(0): Output [COLOR=#ff0000]XMIR[/COLOR]-1 using initial mode XMIR mode of death
[    26.280] (**) NOUVEAU(0):  Driver mode "[COLOR=#ff0000]XMIR[/COLOR] mode of death": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
[    26.280] (II) NOUVEAU(0): Modeline "[COLOR=#ff0000]XMIR [/COLOR]mode of death"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)

> graham@sda4-saucy-btrfs:~$ ls -l /var/log/lightdm/unity-system-compositor.log
-rw------- 1 root root 6664 Jul  3 03:04 /var/log/lightdm/unity-system-compositor.log

I conclude

1) all these commands are doing is searching for a character string in a file and echoing the output to the screen
2) I am running on Xmir
3) the second command is the one that counts at the moment
4) something in the updates on 02/07/2013 broke Xmir.

I did add that 50-pin-mir.pref file which was supposed to stop the usual updates from overriding the code brough in by the PPA. Either that has not worked or code updated by the PPA is bugged. Still, it is all in the game.

Tomorrow I will spend some time on this multi-desktop install. First Xubuntu kicked out the Ubuntu plymouth screen, then Lubuntu kicked out the Xubuntu plymouth screen. It also has two log in background. I get a quick view of ubuntu-warty-final and the Xubuntu backgrong jumps in. And as for the Kubuntu desktop. That does not play fair. It renamed the Grub menu to Kubuntu Gnu/Linux. When it is just supposed to be a desktop. 

Regards.

---

### Post by NikTh on 2013-07-03
> **grahammechanical said:**
> 
4) something in the updates on 02/07/2013 broke Xmir.

For me it was 01/07/2013 when the updates have crashed my desktop. [https://bugs.launchpad.net/mir/+bug/1196355](https://bugs.launchpad.net/mir/+bug/1196355)
Today I installed the system again. Fresh and new, when I added the PPA and made all updates, reboot and .. boom. Same thing. :(

---

### Post by zika on 2013-07-03
> **NikTh said:**
> For me it was 01/07/2013 when the updates have crashed my desktop. [https://bugs.launchpad.net/mir/+bug/1196355](https://bugs.launchpad.net/mir/+bug/1196355)
Today I installed the system again. Fresh and new, when I added the PPA and made all updates, reboot and .. boom. Same thing. :(
I guess that the only thing that is broken (and not only these days, it comes and goes) is LightDM... You should have at least one DM apart from LightDM ready... I have GDM and SliM...Or You should know how to use startx/xinit... System is far from being broken... Just DM... You do not buy a new car if Your lock breaks...

---

### Post by NikTh on 2013-07-03
> **zika said:**
> I guess that the only thing that is broken (and not only these days, it comes and goes) is LightDM... You should have at least one DM apart from LightDM ready... I have GDM and SliM...Or You should know how to use startx/xinit... System is far from being broken... Just DM... You do not buy a new car if Your lock breaks...

The LightDM now it starts. 5 times I rebooted and all of them the LightDM started. But I have no desktop. The deskop is unusable. 
If you read the bug report in previous installation I couldn't even switch to a VT. Black screen, nothing - zero response. Only SysRq rebooted the system. I think that this is not far from being broken. 
(So this time we made a progress ? ) 

Keep in mind that the system is pure. I have installed nothing. Only the updates and the Xmir PPA. Nothing else.

---

### Post by ventrical on 2013-07-04
Yes ..after updates , the only working (two mouse) session of mir that I have busted.

---

### Post by zika on 2013-07-04
> **NikTh said:**
> The LightDM now it starts. 5 times I rebooted and all of them the LightDM started. But I have no desktop. The deskop is unusable. 
If you read the bug report in previous installation I couldn't even switch to a VT. Black screen, nothing - zero response. Only SysRq rebooted the system. I think that this is not far from being broken. 
(So this time we made a progress ? ) 

Keep in mind that the system is pure. I have installed nothing. Only the updates and the Xmir PPA. Nothing else.Simple „text“ in boot-line in Grub (doable while booting) solves that kind of trouble... It is very far from really being broken, trust me...

---

### Post by grahammechanical on 2013-07-04
I have been watching a replay of a Jono Bacon video conference. It had an update on mir and a one hour session just on mir. It gave me a clue about what might be happening.

If xmir does not detect an open source driver it hands over to xserver. My system runs fine on Nouveau and xmir was up and running. I think that the problems lies with this detecting of the open source driver not working properly. 

I have an install of Lubuntu that I could not get xmir running. Then yesterday I booted into it determined to purge the ppa and I got the cursed cursors back. I think that at the moment xmir detection of open source drivers is hit and miss.

I have xmir also working on Kubuntu, Xubuntu, & Ubuntu studio but not on Ubuntu Gnome. Not sure about the wisdom of updating those systems. I might just do it once a week. With the exception of Lubuntu they are on btrfs, so I can rollback if xmir breaks down. I could not install Lubuntu with btrfs format partition.

I have given up on my idea of have Ubuntu+ mir + 4 alternative desktops. These alternative bring in more than a UI. It seems to me that they bring in half the distribution. Too much complication. I shall install a Ubuntu daily and put it on xmir and watch things develop.

Regards.

---

### Post by wojox on 2013-07-04
Loaded (thanks intel):
```
wojox@wojox-laptop:~$ pidof unity-system-compositor
1156
wojox@wojox-laptop:~$ pidof X
1173
wojox@wojox-laptop:~$ grep -i LoadModule /var/log/Xorg.0.log
[    21.382] (II) LoadModule: "glx"
[    21.388] (II) LoadModule: "xmir"
[    21.410] (II) LoadModule: "intel"
[    21.411] (II) LoadModule: "vesa"
[    21.412] (II) LoadModule: "modesetting"
[    21.412] (II) LoadModule: "fbdev"
[    21.414] (II) UnloadModule: "vesa"
[    21.414] (II) UnloadModule: "modesetting"
[    21.414] (II) UnloadModule: "fbdev"
[    21.417] (II) LoadModule: "fb"
[    21.433] (II) LoadModule: "dri2"
[    21.487] (II) LoadModule: "evdev"
[    21.508] (II) LoadModule: "synaptics"
wojox@wojox-laptop:~$ 

```

---

### Post by jerrylamos on 2013-07-05
xmir barely working after update to 3.10.0-2.  Gets the two cursors which barely move.  Screen flickers constantly.

I do a couple actions like connect to hidden wireless network then the cursors hardly move.  When the black cursor hits the left edge of the screen I can't get the white cursor over there to select any action.

I wonder what level of saucy the mir people are using?

If I get motivated I'll do a zsync, install saucy, and try to put (x)mir on again.

---

### Post by grahammechanical on 2013-07-05
I think we have to be careful about blaming xmir for the sort of issues we sometimes get with the development branch. For example I get this with my standard Saucy without xmir

> [COLOR=#000000] I have no desktop. The deskop is unusable. [/COLOR]

Compiz is crashing and dconf reset & setsid unity have no effect. It was hit and miss that I got to the login screen. Now I get the login screen but no Unity afterwards.

Ah, well. You do not have to be crazy to work here, but it helps.

Regards.

---

### Post by wojox on 2013-07-05
> **grahammechanical said:**
> ah, well. You do not have to be crazy to work here, but it helps.

:)

---

### Post by ventrical on 2013-07-05
> **grahammechanical said:**
> 

Ah, well. You do not have to be crazy to work here, but it helps.

Regards.

:)

Gee.. that pic was just terrible :)hehehe

---

### Post by NikTh on 2013-07-05
> **grahammechanical said:**
> I think we have to be careful about blaming xmir for the sort of issues we sometimes get with the development branch. For example I get this with my standard Saucy without xmir

Compiz is crashing and dconf reset & setsid unity have no effect. It was hit and miss that I got to the login screen. Now I get the login screen but no Unity afterwards.

Ah, well. You do not have to be crazy to work here, but it helps.

Regards.

We have exactly the same problem.. ( nouveau ? )

I will not reinstall again, I will wait until some updates released and see what happen. Soon, this PPA will be moved in Universe and the new daily build will have Xmir enabled by default. Then maybe I install once more.

---

### Post by ventrical on 2013-07-05
I still yet have to remove some of my machines from  KVM.Obviously that feature is not supported ? If rolling back to llvmpipe is to be the standard every time there is a questionable graphics adapter that don't jive with nouveau then it looks like the road ahead may be very sluggish. However , in all fairness, this is all still experimental stages of mir so I'll keep testing it.

---

### Post by ventrical on 2013-07-05
Pulling one of my main desktops off the KVM did nothing to improve the mir situation. After fresh install+btrfs, then, update/upgrade, then, add mir ppa instructions etc.. and nothing on nouveau (nvidia Geforce 210/218).

also .. after dist-upgrade BEFORE install of mir ppa and lightdm is busted by default.

---

### Post by ventrical on 2013-07-05
Question:

Do we have to have the saucy-proposed repo enabled?

---

### Post by wojox on 2013-07-05
> **ventrical said:**
> Question:

Do we have to have the saucy-proposed repo enabled?

No

---

### Post by ventrical on 2013-07-06
Lighdm working ok now.

No hide nor hair of mir.

---

### Post by grahammechanical on 2013-07-06
It is safer not to have proposed enabled. Proposed brings in code to be tested before it gets put into main. Useful with a stable install but not so useful if the install is having problems.

---

### Post by wojox on 2013-07-06
I'm running this stock. I've no upgraded kernels or video drivers from outside the repos.

---

### Post by ventrical on 2013-07-06
> **wojox said:**
> I'm running this stock. I've no upgraded kernels or video drivers from outside the repos.

Same here. No dice though on mir after removing one of my main machines from the KVM an doing fresh update/upgrade.. I have one occasion of mir on an older machine (two cursors) (Ati Radeon) but none of the indicators that mir is actually running. I didn't update it  yet because I am trying to inspect it as an anomoly of some sort.

 I guess all thats left is to wait for updates or do what grahammechanical suggested and zsync the .iso and see what happens.

---

### Post by ventrical on 2013-07-06
> **grahammechanical said:**
> It is safer not to have proposed enabled. Proposed brings in code to be tested before it gets put into main. Useful with a stable install but not so useful if the install is having problems.

Thanks for the reminder:)

I think the saucy updates themselves have busted mir. I'll look into that soon.

---

### Post by grahammechanical on 2013-07-06
> **ventrical said:**
> Thanks for the reminder:)

I think the saucy updates themselves have busted mir. I'll look into that soon.

I agree. Yesterday I installed image 20130704 on btrfs and I cannot get to a desktop. Today, I just installed the same image on Ext4 and Appearance does not have any background images or a behaviour tab. No way to reduce launcher icon size, enable workspaces, switch on autohide or change background. And there are also two On-line Accounts icons.

It looks like stuff is being brought straight in from Gnome.org without any modification to Ubuntu design. A little too much 4th of July in some parts of the Ubuntu community?

Regards.

---

### Post by ventrical on 2013-07-06
I zsynced the saucy-desktop-i386 just a little over an hour ago. Installed just seamlessly on +btrfs. Then followed Olli's random thoughts and I have a perfectly working session of Xorg!! This, on an Intell Dual Core 2.66GHzwith NVidia GEforce 210/218. I know it's nouveau driver but where the E'll mir went to is another story all together. Guess I'll try my ATi machine ofline from my KVM.

---

### Post by ventrical on 2013-07-06
Here's what I get from the unity-system-compositor.log

```

ERROR: /build/buildd/mir-0.0.6bzr798saucy0/src/server/graphics/gbm/gbm_display_helpers.cpp(267): Throw in function int mir::graphics::gbm::helpers::DRMHelper::open_drm_device(const mir::graphics::gbm::helpers::UdevHelper&)
Dynamic exception type: boost::exception_detail::clone_impl<boost::exception_detail::error_info_injector<std::runtime_error> >
std::exception::what: Error opening DRM device
[boost::errinfo_errno_*] = 0, "Success"

```

---

### Post by ventrical on 2013-07-06
And yes.. it is rolling back to xserver .. this from lightdm.log

```

[+0.01s] DEBUG: Launching process 2858: /usr/sbin/unity-system-compositor --from-dm-fd 7 --to-dm-fd 11 --vt 7
[+0.01s] DEBUG: Waiting for system compositor for 60s
[+0.01s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.03s] DEBUG: Compositor closed communication channel
[+0.03s] DEBUG: Process 2858 exited with return value 1
[+0.03s] DEBUG: Releasing VT 7
[+0.03s] DEBUG: Compositor failed to start, switching to VT mode
[+0.03s] DEBUG: Starting seat
[+0.03s] DEBUG: Starting new display for greeter
[+0.03s] DEBUG: Starting X server on Unity compositor

```

edit:

My theory is that there is a problem with nouveau.

---

### Post by ventrical on 2013-07-06
Ahhh ! .. It just occured to me that perhaps this current state of testing is due to testing of the actual rollback feature to Xorg, which , is a success!!

---

### Post by ventrical on 2013-07-06
Ati graphics X1250 .. ppfffft!  Nada...

---

### Post by NikTh on 2013-07-06
> **ventrical said:**
> And yes.. it is rolling back to xserver .. this from lightdm.log

```

[+0.01s] DEBUG: Launching process 2858: /usr/sbin/unity-system-compositor --from-dm-fd 7 --to-dm-fd 11 --vt 7
[+0.01s] DEBUG: Waiting for system compositor for 60s
[+0.01s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.03s] DEBUG: Compositor closed communication channel
[+0.03s] DEBUG: Process 2858 exited with return value 1
[+0.03s] DEBUG: Releasing VT 7
[+0.03s] DEBUG: Compositor failed to start, switching to VT mode
[+0.03s] DEBUG: Starting seat
[+0.03s] DEBUG: Starting new display for greeter
[+0.03s] DEBUG: Starting X server on Unity compositor

```

edit:

**My theory is that there is a problem with nouveau**.

Agreed with your theory. Same problem on my installation. Either with Xmir enabled or disabled.

---

### Post by ventrical on 2013-07-06
> **NikTh said:**
> Agreed with your theory. Same problem on my installation. Either with Xmir enabled or disabled.


Actually I just read where Jon says that some graphics driver devs 'refuse' to write drivers for mir.  Obviously we are now experiencing the backlash (err..or payback) for what some think Canonical did to wayland.

At least it is rolling back nicely to xserver without bringing in that horrid llvmpipe. Whatever braintrust who thought that llvmpipe would replace Unity 2D must have been dreaming somthing. I recall very vividly that the Unity 2D scroll in the dash was a 'smooth' scroll (almost touch-screen like) and they have yet since to emulate that (on desktops) with Unity 3D.I can forsee a tremendous amount of breakage over the next few months.

  I mean ..  what were they thinking ?

edit:

Actually it is loading unity- compositor on Xserver .. so my mistake.

However.. I do not get the results that mac4man and a few others get when entering  those grep test codes, but that does not mean the untiy compositor is not running (as per the log file).

.

---

### Post by ventrical on 2013-07-06
I removed all info from lighdm.log, rebooted right into lighdm and logged on. According to the newly written (lightdm.log) logfile it reports that unity system compositor is loaded on xserver

```

[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.7.4, UID=0 PID=991
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Adding default seat
[+0.04s] DEBUG: Compositor will replace Plymouth
[+0.04s] DEBUG: Deactivating Plymouth (attempt #1)
[+1.08s] DEBUG: Deactivating Plymouth (attempt #2)
[+2.77s] DEBUG: Using VT 7
[+2.77s] DEBUG: Logging to /var/log/lightdm/unity-system-compositor.log
[+2.77s] DEBUG: Launching process 1162: /usr/sbin/unity-system-compositor --from-dm-fd 7 --to-dm-fd 13 --vt 7
[+2.77s] DEBUG: Waiting for system compositor for 60s
[+2.77s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+2.77s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+3.53s] DEBUG: Compositor closed communication channel
[+3.54s] DEBUG: Process 1162 exited with return value 1
[+3.54s] DEBUG: Releasing VT 7
[+3.54s] DEBUG: Compositor failed to start, switching to VT mode
[+3.54s] DEBUG: Starting seat
[+3.54s] DEBUG: Starting new display for greeter
[+3.54s] DEBUG: Starting X server on Unity compositor
[+3.54s] DEBUG: Using VT 7
[+3.54s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+3.54s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+3.54s] DEBUG: Launching X Server
[+3.54s] DEBUG: Launching process 1164: /usr/bin/X -core :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+3.54s] DEBUG: Waiting for ready signal from X server :0
[+3.96s] DEBUG: Got signal 10 from process 1164
[+3.96s] DEBUG: Got signal from X server :0
[+3.96s] DEBUG: Connecting to XServer :0
[+3.96s] DEBUG: Starting greeter
[+3.96s] DEBUG: Started session 1167 with service 'lightdm-greeter', username 'lightdm'
[+4.19s] DEBUG: Session 1167 authentication complete with return value 0: Success
[+4.19s] DEBUG: Greeter authorized
[+4.19s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+4.19s] DEBUG: Session 1167 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+4.88s] DEBUG: Greeter connected version=1.7.4
[+4.88s] DEBUG: Greeter connected, display is ready
[+4.88s] DEBUG: New display ready, switching to it
[+4.88s] DEBUG: Activating VT 7
[+5.33s] DEBUG: Greeter start authentication for ventrical
[+5.33s] DEBUG: Started session 1269 with service 'lightdm', username 'ventrical'
[+5.35s] DEBUG: Greeter start authentication for ventrical
[+5.35s] DEBUG: Session 1269: Sending SIGTERM
[+5.35s] DEBUG: Started session 1270 with service 'lightdm', username 'ventrical'
[+5.35s] DEBUG: Session 1269 terminated with signal 15
[+5.35s] DEBUG: Session 1269 failed during authentication
[+5.36s] DEBUG: Session 1270 got 1 message(s) from PAM
[+5.36s] DEBUG: Prompt greeter with 1 message(s)
[+14.02s] DEBUG: Continue authentication
[+14.15s] DEBUG: Session 1270 authentication complete with return value 0: Success
[+14.15s] DEBUG: Authenticate result for user ventrical: Success
[+14.18s] DEBUG: User ventrical authorized
[+14.19s] DEBUG: Greeter requests session ubuntu
[+14.19s] DEBUG: Using session ubuntu
[+14.19s] DEBUG: Stopping greeter
[+14.19s] DEBUG: Session 1167: Sending SIGTERM
[+14.20s] DEBUG: Session 1167 exited with return value 0
[+14.20s] DEBUG: Greeter quit
[+14.29s] DEBUG: Dropping privileges to uid 1000
[+14.29s] DEBUG: Calling setresgid
[+14.29s] DEBUG: Calling setresuid
[+14.29s] DEBUG: Restoring privileges
[+14.29s] DEBUG: Calling setresuid
[+14.29s] DEBUG: Calling setresgid
[+14.32s] DEBUG: Dropping privileges to uid 1000
[+14.32s] DEBUG: Calling setresgid
[+14.32s] DEBUG: Calling setresuid
[+14.32s] DEBUG: Writing /home/ventrical/.dmrc
[+14.34s] DEBUG: Restoring privileges
[+14.34s] DEBUG: Calling setresuid
[+14.34s] DEBUG: Calling setresgid
[+14.36s] DEBUG: Starting session ubuntu as user ventrical
[+14.36s] DEBUG: Session 1270 running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+14.39s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+14.39s] DEBUG: Greeter closed communication channel

```

... so .. it appears that  *mir*  (unity-system-compositor) is locked and loaded unless I am misinterperetting the results of lightdm.log.

edit:

Whats this .. "staring xserver on unity compositor" ??

---

### Post by NikTh on 2013-07-06
I went for updates but to no avail. Same behavior. I took some logs and pasted on pastebin, in case someone wants to examine. 


[LIST=1]
[*][dmesg]("http://pastebin.com/raw.php?i=SZHcmqw5")
[*][Xorg.0.log]("http://pastebin.com/raw.php?i=JfAPQyzD")
[*][x-0.log]("http://pastebin.com/raw.php?i=dxQJa4nJ")
[*][lightdm.log]("http://pastebin.com/raw.php?i=TWvTFCZr")
[*][unity-system-compositor.log]("http://pastebin.com/raw.php?i=8HkrjhWL")
[/LIST]

---

### Post by grahammechanical on 2013-07-06
did you notice these three comments?

> W[COLOR=#000000][FONT=Ubuntu Mono]aiting for system compositor for 60s
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]Compositor closed communication channel
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]Compositor failed to start, switching to VT mode[/FONT][/COLOR]

All done between 2.77s and 3.54s. Then it launches x server. It is my guess that Unity-system-compositor is failing to recognise an open source video driver when it meets one and then drops out and what we get is the xserver fallback. 

I have been wondering how the Kubuntu and Lubuntu devs would fix things so that they didn't get mir when it comes so early in the boot process. I think we now have the answer. They have sabotaged the code.

Remember, boys, If you can't take a joke, you shouldn't have joined.

@ventrical. I have had another one of my stupid ideas. That btrfs recovery mode apt snapshot option. It launches a dialog listing all apt_snapshots. I wonder if the code that does that can be used as a basis for a simple snapshot management utility. I will try to track down where the script is that works the recovery mode menu.

Regards.

---

### Post by ventrical on 2013-07-07
I have been looking at this bug:

[https://bugs.launchpad.net/unity-system-compositor/+bug/1195509](https://bugs.launchpad.net/unity-system-compositor/+bug/1195509)

It's close to what we are getting .. but I am getting good fallback to X.

---

### Post by ventrical on 2013-07-07
> **grahammechanical said:**
> did you notice these three comments?



All done between 2.77s and 3.54s. Then it launches x server. It is my guess that Unity-system-compositor is failing to recognise an open source video driver when it meets one and then drops out and what we get is the xserver fallback. 

I have been wondering how the Kubuntu and Lubuntu devs would fix things so that they didn't get mir when it comes so early in the boot process. I think we now have the answer. They have sabotaged the code.

Remember, boys, If you can't take a joke, you shouldn't have joined.



At this stage I really think they are  just trying different things. I guess we will just have to roll with it for now.

> 

@ventrical. I have had another one of my stupid ideas. That btrfs recovery mode apt snapshot option. It launches a dialog listing all apt_snapshots. I wonder if the code that does that can be used as a basis for a simple snapshot management utility. I will try to track down where the script is that works the recovery mode menu.

Regards.

You know what ! Thats not stupid at all.  There are all kinds of gems to be discovered in all  of those log files. The thing is , trying to track them down. BTRFS has been a bright spot in this dev release. At tleast there has been something interesting to hack around with.

---

### Post by grahammechanical on 2013-07-07
> [COLOR=#000000]The thing is , trying to track them down. [/COLOR]

I also though it would be hard but the initial research was surprising easy. Recovery mode is run Whiptail which is built using a Debian package called Newt. And there are scripts that I think can be subverted.

/lib/recovery-mode/recovery-menu.
/lib/recovery-mode/options. This options folder contains the scripts that are run when we select a recovery mode option.
/usr/bin/apt-btrfs-snapshot. This script contains the apt-snapshot commands. So, when we run the command to list all snapshots it is this script that is run.

I am hoping that there is something similar for btrfs-tools but it is proving difficult to find. If I make progress with this I will open a fresh thread on making a snapshot utility.

Regards.

---

### Post by ventrical on 2013-07-07
@grahamechanical

thanks for tracking that info down.

Here is plymouth.d bug that I get for mir. I have been ignoring trying to report it- so I thought I would. It has been confirmed in quantal but I thought I would open up a bug report in saucy.



[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1198688](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1198688)

---

### Post by mc4man on 2013-07-07
> **ventrical said:**
> @grahamechanical

thanks for tracking that info down.

Here is plymouth.d bug that I get for mir. I have been ignoring trying to report it- so I thought I would. It has been confirmed in quantal but I thought I would open up a bug report in saucy.



[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1198688](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1198688)

bug is unrelated to mir/xmir. (possibly the mir packages make it more likely to occur),  Seen here from very get go on 13.10, been around in earlier Ubunru releases for some time now

---

### Post by ventrical on 2013-07-07
> **mc4man said:**
> bug is unrelated to mir/xmir. (possibly the mir packages make it more likely to occur),  Seen here from very get go on 13.10, been around in earlier Ubunru releases for some time now

As always  .. thanks for the input.

---

### Post by ventrical on 2013-07-07
I have mir back on line with my intel based graphics desktop.

```

ventrical@ventrical-Dell-DV051:~$ ps afx | grep unity-system-compositor |grep -v grep
  994 ?        Sl     0:03  \_ /usr/sbin/unity-system-compositor --from-dm-fd 10 --to-dm-fd 13 --vt 7
ventrical@ventrical-Dell-DV051:~$ 



```

---

### Post by ventrical on 2013-07-07
Ok .. what I did was fresh install saucy THEN reboot. THEN I updated/dist-upgrade.

sudo apt-get update
sudo apt-get dist-upgrade

You will notice another version of 3.10.0.2 kernel. That was the buster that busted my ATI install.

After that update , THEN do the code at Olli's random thoughts link. I did NOT choose to use the pin preferences option. Now it boots right into mir from logon.  I took a video of it and there are all sort of new anomolies. One being a persitent pink screen when trying to copy and paste and the Unity dash is dog slow (but I think I know the problem there). All other apps are really snappy. So far it is very stable.

edit:btw .. this on Intel based graphics card

---

### Post by ventrical on 2013-07-07
This video is a little boring and fuzzy but it is where mir is at currently on one of my machines. Still has the double cursor.

[http://www.youtube.com/watch?v=6uFQ21mOX5E&feature=youtu.be](http://www.youtube.com/watch?v=6uFQ21mOX5E&feature=youtu.be)

---

### Post by EgoGratis on 2013-07-07
This is what we tester wanted all along yes. Once it will be polished there will be no double cursor anymore...

Where will be the fun in that!

---

### Post by ventrical on 2013-07-07
> **EgoGratis said:**
> This is what we tester wanted all along yes. Once it will be polished there will be no double cursor anymore...

Where will be the fun in that!


 I noticed that the compiz rotating cube/cylinder appears to have  like a fluid or substance in it :)  uhhh.... it's pretty surreal. The edges are a lot sharper and it is more defined and smoother animation, not clunky like.

Yeah.. the double cursor is fun:) Doh! :)  I think it is the next "new shiny thing" :) I think unity has come a long way :)

Now I can sleep...

Oy vey..

---

### Post by EgoGratis on 2013-07-07
> I noticed that the compiz rotating cube/cylinder appears to have  like a fluid or substance in it :smile:  uhhh.... it's pretty surreal. The edges are a lot sharper and it is more defined and smoother animation, not clunky like.

Priceless... Quite a shame we will probably be saying good bye to Compiz in next dev cycle. But there will probably be this new thing called Unity 8 and i hope it will meet my expectations.

---

### Post by jerrylamos on 2013-07-07
> **EgoGratis said:**
> Priceless... Quite a shame we will probably be saying good bye to Compiz in next dev cycle. But there will probably be this new thing called Unity 8 and i hope it will meet my expectations.I got unity8 installed, following the "Building Unity 8" instructions.  It came up with a little vertical window looking like a phone.  Looks a little silly on the left side of this 1440x900 screen.  Anyway it's up and running with no apps like firefox or terminal or office or whatever.  As I get motivated I'll look around to see what it can do.

---

### Post by ventrical on 2013-07-08
> **jerrylamos said:**
> I got unity8 installed, following the "Building Unity 8" instructions.  It came up with a little vertical window looking like a phone.  Looks a little silly on the left side of this 1440x900 screen.  Anyway it's up and running with no apps like firefox or terminal or office or whatever.  As I get motivated I'll look around to see what it can do.


 Is that Unity 8 on top of mir?

---

### Post by ventrical on 2013-07-08
> **EgoGratis said:**
> Priceless... Quite a shame we will probably be saying good bye to Compiz in next dev cycle. But there will probably be this new thing called Unity 8 and i hope it will meet my expectations.


  It will be sad to see that go (if it actually does). That had been part of all the fun in testing graphics cards. I have a Lepan tablet and an iPad II. They are two of the most boring machines I have.  hardly ever use them. I mean .. if this is the way that Ubuntu is going then  .. I just don't get it.

---

### Post by sanderj on 2013-07-08
I just did an update on my laptop, did a "sudo restart lightdm", and a black screen with the Big Ugly Cursor (BUC) appeared for a second, and then only a black screen with a white underscore character in the upper left corner. I did a restart, and after the Ubuntu logo with five dots, I get the same: black screen with the BUC, then black screen with the underscore.

Anything I can do to repair this?

---

### Post by deadflowr on 2013-07-08
> **sanderj said:**
> I just did an update on my laptop, did a "sudo restart lightdm", and a black screen with the Big Ugly Cursor (BUC) appeared for a second, and then only a black screen with a white underscore character in the upper left corner. I did a restart, and after the Ubuntu logo with five dots, I get the same: black screen with the BUC, then black screen with the underscore.

Anything I can do to repair this?

You can try disabling mir
If you can get a tty1-6 session going, open the file /etc/lightdm/lightdm.conf.d/10_unity-system-compositor and comment out the line
type=unity
#type=unity
and save
then try a reboot, restart X.
Don't know if it'll work, but worth a shot.

After brainfart edit: If you get a usable desktop after disabling mir, look in the lightdm or xorg logfiles, hopefully they can point to the errors.

---

### Post by ventrical on 2013-07-08
> **sanderj said:**
> I just did an update on my laptop, did a "sudo restart lightdm", and a black screen with the Big Ugly Cursor (BUC) appeared for a second, and then only a black screen with a white underscore character in the upper left corner. I did a restart, and after the Ubuntu logo with five dots, I get the same: black screen with the BUC, then black screen with the underscore.

Anything I can do to repair this?

 What did you do an update of?

  An existing working install of saucy+mir ?

---

### Post by sanderj on 2013-07-08
I couldn't get tty1-6, so I did a reboot, said GRUB to boot "single", and got the root command prompt. I commented the unity line, saved, rebooted ... and now I have a non-GUI screen. I log in as normal user, and then type "startx" which results in an error message "exec: /usr/bin/X: not found".

Ouch. The X executable not found? That is still needed with XMir, isn't it?

---

### Post by sanderj on 2013-07-08
> **ventrical said:**
> What did you do an update of?

  An existing working install of saucy+mir ?

Update of the OS (yes, saucy + mir): sudo apt-get update && sudo apt-get ugprade

---

### Post by ventrical on 2013-07-08
> **sanderj said:**
> Update of the OS (yes, saucy + mir): sudo apt-get update && sudo apt-get ugprade


What I have found to be a working method is to:

1. Get the daily saucy-desktop-i386.iso. (or zsync existing)
2. Make bootable USB.
3. Install on system.
4. After successful install THEN 
    sudo apt-get update
    sudo apt-get dist-upgrade

5. After all of this THEN install the mir ppa  [http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)   and
    sudo apt-get update
    sudo apt-get dist-upgrade

 I choose not to pin the pref file.

Also .. it appears that the kernel version  3.10.0.2x is busting mir .. pin or no pin. so it is better to install all upgrades before installing the mir ppa.

---

### Post by sanderj on 2013-07-08
> **ventrical said:**
> What I have found to be a working method is to:

1. Get the daily saucy-desktop-i386.iso. (or zsync existing)
2. Make bootable USB.
3. Install on system.
4. After successful install THEN 
    sudo apt-get update
    sudo apt-get dist-upgrade

5. After all of this THEN install the mir ppa  [http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)   and
    sudo apt-get update
    sudo apt-get dist-upgrade

 I choose not to pin the pref file.

Also .. it appears that the kernel version  3.10.0.2x is busting mir .. pin or no pin.

Isn't that a fresh install?
FYI: I had Mir running successfully. Until it fell back to plain X a week ago or so (as others experienced too), and until the system was not functioning anymore at all after today's update/upgrade.

---

### Post by deadflowr on 2013-07-08
> [COLOR=#000000]I couldn't get tty1-6, so I did a reboot, said GRUB to boot "single", and got the root command prompt. I commented the unity line, saved, rebooted ... and now I have a non-GUI screen. I log in as normal user, and then type "startx" which results in an error message "exec: /usr/bin/X: not found".[/COLOR]

[COLOR=#000000]Ouch. The X executable not found? That is still needed with XMir, isn't it?[/COLOR] 

I ran an update on a mir system I've got running and got this(dist-upgrade)
```
Calculating upgrade... DoneThe following packages will be REMOVED:
  ubuntu-desktop xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware
The following packages will be upgraded:
  apparmor apport apport-gtk dpkg indicator-datetime indicator-power
  libapparmor-perl libapparmor1 libdpkg-perl libgail-common libgail18
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libqpdf10 libunity-core-6.0-7
  libunity-gtk2-parser0 libunity-gtk3-parser0 libxfixes3 libxi6 python3-apport
  python3-problem-report qpdf unity unity-common unity-gtk-module-common
  unity-gtk2-module unity-gtk3-module unity-services
29 upgraded, 0 newly installed, 33 to remove and 0 not upgraded.
Need to get 7,885 kB of archives.
After this operation, 12.0 MB disk space will be freed.
Do you want to continue [Y/n]? 



```

Obviously I aborted, But I wonder if this happened to you as well.

---

### Post by sanderj on 2013-07-08
Ouch. That might have happened on my system as it would explain my current "no X binary" ...

---

### Post by ventrical on 2013-07-08
> **sanderj said:**
> Isn't that a fresh install?
FYI: I had Mir running successfully. Until it fell back to plain X a week ago or so (as others experienced too), and until the system was not functioning anymore at all after today's update/upgrade.


Thats exactly it.   I have my saucy .iso from a  few days back with 3.10.0.2 but .. then there was another upgrade of kernel (version) 3.10.0.2 and thats what busted mir. So, when you do a fresh install and THEN update/upgrade first and THEN install mir ppa it will not break. I am now working this method with ATi and nouveau. My working install is on Intel Graphics and I am now experimenting with Vidia/Ati as I write.

  My theory then is that the newer kernel version busted working mir install. Solution is to fresh install, update/upgrade and  THEN install mir ppa.

---

### Post by ventrical on 2013-07-08
> **deadflowr said:**
> I ran an update on a mir system I've got running and got this(dist-upgrade)
```
Calculating upgrade... DoneThe following packages will be REMOVED:
  ubuntu-desktop xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware
The following packages will be upgraded:
  apparmor apport apport-gtk dpkg indicator-datetime indicator-power
  libapparmor-perl libapparmor1 libdpkg-perl libgail-common libgail18
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libqpdf10 libunity-core-6.0-7
  libunity-gtk2-parser0 libunity-gtk3-parser0 libxfixes3 libxi6 python3-apport
  python3-problem-report qpdf unity unity-common unity-gtk-module-common
  unity-gtk2-module unity-gtk3-module unity-services
29 upgraded, 0 newly installed, 33 to remove and 0 not upgraded.
Need to get 7,885 kB of archives.
After this operation, 12.0 MB disk space will be freed.
Do you want to continue [Y/n]? 



```

Obviously I aborted, But I wonder if this happened to you as well.

Absolutely . I did not abort (silly me) and it removed all of the unity lenses as well.

---

### Post by ventrical on 2013-07-08
Now holding back these packages:

```

Reading state information... Done
The following packages have been kept back:
  xserver-xorg-video-ati xserver-xorg-video-intel xserver-xorg-video-nouveau
  xserver-xorg-video-radeon
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
ventrical@ventrical-P4M266A-8237:~$ 

```

Edit:

These packages were held back on a desktop system with ATi Graphics hardware.

---

### Post by mc4man on 2013-07-08
the xserver-xorg-video-nouveau in the mir team ppa is not good to go with xserver updates,  abi-13 vs. 14
So either wait or purge the ppa & you can upgrade. (& re-install the xserver-xorg-video-nouveau  package if already removed

---

### Post by ventrical on 2013-07-08
> **mc4man said:**
> the xserver-xorg-video-nouveau in the mir team ppa is not good to go with xserver updates,  abi-13 vs. 14
So either wait or purge the ppa & you can upgrade. (& re-install the xserver-xorg-video-nouveau  package if already removed

Guess I have no choice but to wait. The xradeon,xati and xnouveau are the ones that will not work but the xintel is working with mir.

edit:

correction. The xserver-xorg-video-intel  is also being held back from Intel based graphics .. so it's across the board... but why it's working on the one... perhaps if I updated/upgraded it I would get the hold backs on that. 

@mc4man..

How long do you think the wait is?

2. Does this affect everybody?

---

### Post by ventrical on 2013-07-08
> **sanderj said:**
> Isn't that a fresh install?
FYI: I had Mir running successfully. Until it fell back to plain X a week ago or so (as others experienced too), and until the system was not functioning anymore at all after today's update/upgrade.


it appears that I was wrong about the kernel version .. looks like the xorg video drivers are being held back because of a new er version of another component so I guess we will all have to wait. (I'll fiddle around with the working one I got so far)  :)

---

### Post by mc4man on 2013-07-08
> **ventrical said:**
> Guess I have no choice but to wait. The xradeon,xati and xnouveau are the ones that will not work but the xintel is working with mir.

edit:

correction. The xserver-xorg-video-intel  is also being held back from Intel based graphics .. so it's across the board... but why it's working on the one... perhaps if I updated/upgraded it I would get the hold backs on that. 

@mc4man..

How long do you think the wait is?

2. Does this affect everybody?

No idea - I had put back the the ppa last night to test some vsync stuff (never got around to ) & noticed when I updated xserver today it was going to remove nouveau.
So to see,   I let it - rebooted into lvmpipe which is close to useless so purged the ppa & re-installed nouveau

To me the ppa is currently worthless, either get a barrage of plymouthd crash popups or if plymouthd doesn't crash it keeps running after login (which it shouldn't.
Add that to crappy cursor & keyboard input, breaking vsync, ect., no reason here to use till at least those issues are fixed...

---

### Post by NikTh on 2013-07-08
> **mc4man said:**
> 
To me the ppa is currently worthless, either get a barrage of plymouthd crash popups or if plymouthd doesn't crash it keeps running after login (which it shouldn't.
Add that to crappy cursor & keyboard input, breaking vsync, ect., no reason here to use till at least those issues are fixed...

Me too. Same things. 

I couldn't resits and today I made a new installation (daily build). After adding the PPA.... same sh#%$ diffrent day :P

I have to wait.

---

### Post by wojox on 2013-07-08
> **ventrical said:**
> Does this affect everybody?

+1

---

### Post by ventrical on 2013-07-09
@mc4man and all

Hey .. thanks you guys.  Testing mir has not been fun. I had more fun testing those mir demo thingys a while back.

---

### Post by cecilpierce on 2013-07-09
I'd like to know how you guys can test something that won't work...:D

Good luck, can't wait to see it blast off !

---

### Post by ventrical on 2013-07-09
> **cecilpierce said:**
> I'd like to know how you guys can test something that won't work...:D

Good luck, can't wait to see it blast off !

For some reason I was able to get it running on my Dell tower. (I am sure if I update now it will break). But I see what you mean. I don't think just because we get something installed and running is really testing it.  I also think they are letting it out only a little at a time - then pulling it .. back and forth so to speak.

Even Mark is having a hit and  miss experience with mir.

"[TABLE]
[TR]
[TD][Mark Shuttleworth (sabdfl)]("https://launchpad.net/%7Esabdfl")             wrote             on 2013-06-28:                          [/TD]
                       [TD="class: bug-comment-index"]           [ #6]("https://bugs.launchpad.net/unity-system-compositor/+bug/1195509/comments/6")           [/TD]
         [/TR]
            [/TABLE]
                               Oddly, this  morning my laptop booted straight into Mir with no problems. Either the  issue is fixed for me, or it's racy and I just (finally!) got lucky."



  I guess it is safe to say that 'mir' has not reached that "sexy" stage as of yet :)

---

### Post by ventrical on 2013-07-09
If Canonical wants 'mir' to be the Rock Star that it has been hyped to be , then they will have to start throwing us testers some bones to chomp on rather than just a few bisqiuts here and there :)

---

### Post by cecilpierce on 2013-07-09
Yep it gave me so much trouble I gave up til something gives. Waylands starting to look better to me. Have you tried the Maui live CD ? There suposed to come out with an installable one this month, I hope !

[http://www.maui-project.org/download/](http://www.maui-project.org/download/)

---

### Post by ventrical on 2013-07-09
Thanks for the link. I think I'll do some more research on btrfs and Lubuntu. Also  I would like to check up on Kubuntu until mir gets back on line.

---

### Post by grahammechanical on 2013-07-09
> **ventrical said:**
> Thanks for the link. I think I'll do some more research on btrfs and Lubuntu. Also  I would like to check up on Kubuntu until mir gets back on line.

Lubuntu is the only flavour that I have been unable to install with btrfs. And Ubuntu Gnome is the only flavour that I have been unable to get xmir working. Mind you I have not updated these installs for a week. That maybe the reason they are still working. I put in a fresh Ubuntu Saucy from the 20130707 image and xmir is working on that. Not going to update it for a while.

I noticed a strange thing on my standard saucy-btrfs. I am sure that kernels 3.10.0-1 and 3.10.0-2 came in. Well, now they are gone and I only have 3.10.0-0. And yet the image from 7th installs kernel 3.10.0-2. 

Regards.

---

### Post by ventrical on 2013-07-09
> **grahammechanical said:**
> 

I noticed a strange thing on my standard saucy-btrfs. I am sure that kernels 3.10.0-1 and 3.10.0-2 came in. Well, now they are gone and I only have 3.10.0-0. And yet the image from 7th installs kernel 3.10.0-2. 

Regards.


 On the working mir install I have that is true also and I will not update that install either. The thing is (from 7 July/2013) that that .iso will install with 3.10.0.2 flat out and then updates will again install another *variant* of 3.10.0.2 kernel. Of course any further installs after that and xmir will break.

So the observation being that there was a rapid succesion of the 3.10.2.0 kernel version update and that makes me wonder. Whatever, if anything, that means is beyond me but is of interest anyways.

---

### Post by ventrical on 2013-07-09
Ok... here is a wild one for today:

```

Fetched 18.1 MB in 1min 12s (250 kB/s)                                         
Reading package lists... Done
ventrical@ventrical-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
 libxfixes3 : Breaks: xserver-xorg-core (< 2:1.14) but 2:1.13.3+xmir1-0 is to be installed
 libxi6 : Breaks: xserver-xorg-core (< 2:1.14) but 2:1.13.3+xmir1-0 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
ventrical@ventrical-desktop:~$ 

```

and now it wants to do this..

```

Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libunity-core-6.0-7 libxfixes3 libxi6 unity unity-common unity-services xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion
  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware
The following packages will be upgraded:
  apparmor apport apport-gtk dpkg friends friends-dispatcher friends-facebook friends-twitter gnome-control-center
  gnome-control-center-data indicator-datetime indicator-power libapparmor-perl libapparmor1 libdpkg-perl libdrm-intel1
  libdrm-nouveau2 libdrm-radeon1 libdrm2 libgail-common libgail18 libgnome-control-center1 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libqpdf10 libqt5core5 libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5 libqt5printsupport5
  libqt5sql5 libqt5sql5-sqlite libqt5test5 libqt5widgets5 libqt5xml5 libunity-gtk2-parser0 libunity-gtk3-parser0
  python-configglue python3-apport python3-problem-report qpdf unity-gtk-module-common unity-gtk2-module
  unity-gtk3-module xserver-common
47 upgraded, 0 newly installed, 0 to remove and 34 not upgraded.
Need to get 15.9 MB of archives.
After this operation, 146 kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

So it did.

---

### Post by cecilpierce on 2013-07-09
Geez! I DL Lubuntu and Xubuntu daily 13.10, tried usb stick and burn to CD, to try mir with them and both installers crash about 3/4 through, what the heck ???

---

### Post by grahammechanical on 2013-07-09
> **cecilpierce said:**
> Geez! I DL Lubuntu and Xubuntu daily 13.10, tried usb stick and burn to CD, to try mir with them and both installers crash about 3/4 through, what the heck ???

How are you installing? From the second screen - Install Ubuntu or from a live session? I have had installers crash on me at the copying files section. It usually says not enough disk space even though the partition is 10GB But when I try again from the live session the install succeeds.

Regards.

---

### Post by cecilpierce on 2013-07-09
I tried both three times and its just annoying so I got mad and through the cd in the trash. 

I'll wait til things get a little better, I'm running low on CD's.

---

### Post by sanderj on 2013-07-09
> **cecilpierce said:**
>  I'm running low on CD's.

... maybe invest 5 Euro in a 4GB USB-stick ... ;-)

---

### Post by monkeybrain2012 on 2013-07-09
Is he using a different ppa than you guys? :)

[http://www.markshuttleworth.com/archives/1269](http://www.markshuttleworth.com/archives/1269)

---

### Post by ventrical on 2013-07-09
> **monkeybrain2012 said:**
> Is he using a different ppa than you guys? :)

[http://www.markshuttleworth.com/archives/1269](http://www.markshuttleworth.com/archives/1269)

 Well that explains why mir will work with my Dell and not my other machines...


 I thought mir was busted  (for the rest of us)..????

---

### Post by mc4man on 2013-07-09
> **ventrical said:**
> Well that explains why mir will work with my Dell and not my other machines...


 I thought mir was busted  (for the rest of us)..????

It's not particularly 'broken' , just a matter of how well it performs
As far as the hang concerning the mir ppa with new xserver that's almost 100% taken care of, at least on nouveau installs.
To check went ahead with the ppa again enabled & a dist-upgrade. Everything upgraded/installed except xserver-xorg-core which is currently hung up on this - 

> sudo apt-get install -s  --only-upgrade  xserver-xorg-core
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xserver-xorg-core : Depends: libmirclient1 (>= 0.0.6bzr[COLOR="#0000CD"]828[/COLOR]saucy0) but 0.0.6bzr[COLOR="#FF0000"]798[/COLOR]saucy0 is to be installed
So when 828 or higher is available then that last package can upgrade

What happens if you upgrade all but the above & reboot, don't know, guess I could see.

---

### Post by ventrical on 2013-07-09
> **mc4man said:**
> It's not particularly 'broken' , just a matter of how well it performs
As far as the hang concerning the mir ppa with new xserver that's almost 100% taken care of, at least on nouveau installs.
To check went ahead with the ppa again enabled & a dist-upgrade. Everything upgraded/installed except xserver-xorg-core which is currently hung up on this - 


So when 828 or higher is available then that last package can upgrade

What happens if you upgrade all but the above & reboot, don't know, guess I could see.


  I went to  Mark's blog and he propounds that it is working good for him. I am now on my Dell (Intel based) and I went to update and got the same thing I have been getting all day yesterday and today on all of my machines:

```

ventrical@ventrical-Dell-DV051:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
 libxfixes3 : Breaks: xserver-xorg-core (< 2:1.14) but 2:1.13.3+xmir1-0 is to be installed
 libxi6 : Breaks: xserver-xorg-core (< 2:1.14) but 2:1.13.3+xmir1-0 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
ventrical@ventrical-Dell-DV051:~$ 

```

btw .. I'll check my nVidia based setups. I won't have to purge because I never authenticated the install. Oh well .. thats why were here I guess.

mir is still working on the Dell btw..

but no updates

---

### Post by mc4man on 2013-07-09
> **ventrical said:**
> I went to  Mark's blog and he propounds that it is working good for him. I am now on my Dell (Intel based) and I went to update and got the same thing I have been getting all day yesterday and today on all of my machines:

```

ventrical@ventrical-Dell-DV051:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
 libxfixes3 : Breaks: xserver-xorg-core (< 2:1.14) but 2:1.13.3+xmir1-0 is to be installed
 libxi6 : Breaks: xserver-xorg-core (< 2:1.14) but 2:1.13.3+xmir1-0 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
ventrical@ventrical-Dell-DV051:~$ 

```

btw .. I'll check my nVidia based setups. I won't have to purge because I never authenticated the install. Oh well .. thats why were here I guess.

mir is still working on the Dell btw..

but no updates

As I just mentioned the xserver-xorg-core from the ppa can not be upgraded to until some mir source packages are updated. 
Saw they just built elsewhere so installed & then the new xserver-xorg-core can be installed, thereby finishing the upgrade

> ~/Downloads/inmir$ sudo dpkg -i *.deb
[sudo] password for doug: 
(Reading database ... 292260 files and directories currently installed.)
Preparing to replace libmirclient1:amd64 0.0.6bzr798saucy0  (using libmirclient1_0.0.6bzr832saucy0+833~saucy1_amd64.deb) ...
Unpacking replacement libmirclient1:amd64 ...
Preparing to replace libmirprotobuf0:amd64 0.0.6bzr798saucy0 (using libmirprotobuf0_0.0.6bzr832saucy0+833~saucy1_amd64.deb) ...
Unpacking replacement libmirprotobuf0:amd64 ...
Setting up libmirprotobuf0:amd64 (0.0.6bzr832saucy0+833~saucy1) ...
Setting up libmirclient1:amd64 (0.0.6bzr832saucy0+833~saucy1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

Folowed by 

> $ sudo apt-get install   --only-upgrade  xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavdevice53 libavfilter2 libavutil-dev libdrm2:i386
Use 'apt-get autoremove' to remove them.
Suggested packages:
  xfonts-100dpi xfonts-75dpi
The following packages will be upgraded:
  xserver-xorg-core
1 upgraded, 0 newly installed, 0 to remove 
Need to get 1,656 kB of archives.
After this operation, 19.5 kB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/mir-team/system-compositor-testing/ubuntu/](http://ppa.launchpad.net/mir-team/system-compositor-testing/ubuntu/) saucy/main xserver-xorg-core amd64 2:1.14.1-0ubuntu0.8+xmir1 [1,656 kB]
Fetched 1,656 kB in 3s (455 kB/s)              
(Reading database ... 292260 files and directories currently installed.)
Preparing to replace xserver-xorg-core 2:1.14.1-0ubuntu0.8 (using .../xserver-xorg-core_2%3a1.14.1-0ubuntu0.8+xmir1_amd64.deb) ...
Unpacking replacement xserver-xorg-core ...
Processing triggers for man-db ...
Setting up xserver-xorg-core (2:1.14.1-0ubuntu0.8+xmir1) ...



see screen

---

### Post by sanderj on 2013-07-09
> **monkeybrain2012 said:**
> Is he using a different ppa than you guys? :)

[http://www.markshuttleworth.com/archives/1269](http://www.markshuttleworth.com/archives/1269)

Mark says: > It will land in 13.10 just as soon as our QA and release teams are happy that its ready for very widespread testing.

Pity he doesn't mention an ETA for that. What do we think: in a week? A month? Probably not three months as it's now 2013-07, and three months would mean the release month of 13.10.

---

### Post by ventrical on 2013-07-09
> **mc4man said:**
> As I just mentioned the xserver-xorg-core from the ppa can not be upgraded to until some mir source packages are updated. 
Saw they just built elsewhere so installed & then the new xserver-xorg-core can be installed, thereby finishing the upgrade



Folowed by 



see screen

Where do I get :

libmirclient1 (>= 0.0.6bzr827saucy0)

?

Also .. I upgraded  on nVidia base and it rolled over to llvmpipe.  Sheesh..this &&^$$es me off.

:)

---

### Post by ventrical on 2013-07-09
> **sanderj said:**
> Mark says: 

Pity he doesn't mention an ETA for that. What do we think: in a week? A month? Probably not three months as it's now 2013-07, and three months would mean the release month of 13.10.

I thought ubuntu forums *IS* widespread testing !!!!!!!!!!! ?

edit .. ok . I get it .. ubuntuforums is at the low end of the ubuntu hierarchy...

as Phil Collins would say .. 'geee..'

---

### Post by mc4man on 2013-07-09
> **ventrical said:**
> Where do I get :

libmirclient1 (>= 0.0.6bzr827saucy0)

?

Also .. I upgraded  on nVidia base and it rolled over to llvmpipe.  Sheesh..this &&^$$es me off.

:)

I'd probably wait for them to show in saucy repo's, not exactly sure what the intended target is

As is this latest go round fails to start, shows this error - 
> /usr/sbin/unity-system-compositor: symbol lookup error: /usr/lib/x86_64-linux-gnu/libEGL.so.1: undefined symbol: mir_egl_mesa_display_is_valid


Part of the libegl1-mesa package

Also with the ppa packages but not using unity-system-compositor I get indicator-datetime-service pegging a core+ & grabbing a whole lot of ram as in screen

---

### Post by ventrical on 2013-07-09
@mc4man

thanks .. for your sharing of information.

---

### Post by mc4man on 2013-07-09
All back up now without error, there were some new mesa & a unity-system-compositor packages just published
> Upgraded the following packages:
libegl1-mesa (9.2~git20130628.g6b676e6-0ubuntu0+mir1-jenkins83saucy0) to 9.2~git20130628.g6b676e6-0ubuntu0+mir4-jenkins86saucy0
libegl1-mesa-drivers (9.2~git20130628.g6b676e6-0ubuntu0+mir1-jenkins83saucy0) to 9.2~git20130628.g6b676e6-0ubuntu0+mir4-jenkins86saucy0
libgbm1 (9.2~git20130628.g6b676e6-0ubuntu0+mir1-jenkins83saucy0) to 9.2~git20130628.g6b676e6-0ubuntu0+mir4-jenkins86saucy0
libgl1-mesa-dev (9.2~git20130628.g6b676e6-0ubuntu0+mir1-jenkins83saucy0) to 9.2~git20130628.g6b676e6-0ubuntu0+mir4-jenkins86saucy0
libgl1-mesa-dri (9.2~git20130628.g6b676e6-0ubuntu0+mir1-jenkins83saucy0) to 9.2~git20130628.g6b676e6-0ubuntu0+mir4-jenkins86saucy0
libgl1-mesa-glx (9.2~git20130628.g6b676e6-0ubuntu0+mir1-jenkins83saucy0) to 9.2~git20130628.g6b676e6-0ubuntu0+mir4-jenkins86saucy0
libglapi-mesa (9.2~git20130628.g6b676e6-0ubuntu0+mir1-jenkins83saucy0) to 9.2~git20130628.g6b676e6-0ubuntu0+mir4-jenkins86saucy0
libgles2-mesa (9.2~git20130628.g6b676e6-0ubuntu0+mir1-jenkins83saucy0) to 9.2~git20130628.g6b676e6-0ubuntu0+mir4-jenkins86saucy0
libgtk-3-doc (3.8.2-3ubuntu2) to 3.8.2-3ubuntu2+mc3man1
libmirserver0 (0.0.6bzr798saucy0) to 0.0.6bzr832saucy0
libopenvg1-mesa (9.2~git20130628.g6b676e6-0ubuntu0+mir1-jenkins83saucy0) to 9.2~git20130628.g6b676e6-0ubuntu0+mir4-jenkins86saucy0
libxatracker1 (9.2~git20130628.g6b676e6-0ubuntu0+mir1-jenkins83saucy0) to 9.2~git20130628.g6b676e6-0ubuntu0+mir4-jenkins86saucy0
mesa-common-dev (9.2~git20130628.g6b676e6-0ubuntu0+mir1-jenkins83saucy0) to 9.2~git20130628.g6b676e6-0ubuntu0+mir4-jenkins86saucy0
python-dirspec (4.2.0-1) to 4.2.0-1ubuntu1
python3-dirspec (4.2.0-1) to 4.2.0-1ubuntu1
unity-system-compositor (0.0.1bzr33saucy0) to 0.0.1bzr33saucy0.144

So maybe try again
(if still getting hung up on libmirclient1 & libmirprotobuf0 then I'll point you to some packages with minor trepidation..

---

### Post by mc4man on 2013-07-09
Some of the previous lag, ect. is gone with the new builds, one exception could be this forum - at times almost impossible, about a 7 - 10 sec. delay per keystoke. 
(though at other times input is good, like this edit works fine

Fine now in a terminal & gedit., and was ok in browser in  launchpad, find in synaptic is good at times, lags on other attempt

Over all pretty inconsistent

---

### Post by ventrical on 2013-07-10
@mc4man

Right you are!  The upgrade went well here. (on nVidia/nouveau) Now to see if mir is working :)

---

### Post by ventrical on 2013-07-10
All I get is a nice clean rollback to X.

---

### Post by mc4man on 2013-07-10
> **ventrical said:**
> All I get is a nice clean rollback to X.
If you had previously edited that file to comment out line (/etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf
Then check & uncomment (or check & make sure it's even there

Otherwise maybe read thru lightdm.log & unity-system-compositor.log (in /var/log/lightdm, you'll  need root permission to view

---

### Post by ventrical on 2013-07-10
Will do.

 On the Intel (Dell) (after upgrade)  I have only the one cursor. The type response time is good (here and now). Only problem is unity Dash is super slow (snails pace) to come up. Compiz works good and  that bug when the cursor is moved all the way to the right of the screen and a blank screen shows up , is gone.

edit;

Nope !! Updates busted mir on Intel.

That was my last working  mir.

---

### Post by ventrical on 2013-07-10
> **mc4man said:**
> If you had previously edited that file to comment out line (/etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf
Then check & uncomment (or check & make sure it's even there

Otherwise maybe read thru lightdm.log & unity-system-compositor.log (in /var/log/lightdm, you'll  need root permission to view

My apologies.. I should have said  'a nice clean rollback to X with Unity Desktop.'

All those files are there.

I still get the same errors (nouveau) with lightdm and unity-system-comp.

```

[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.7.4, UID=0 PID=2492
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Adding default seat
[+0.01s] DEBUG: Using VT 7
[+0.01s] DEBUG: Logging to /var/log/lightdm/unity-system-compositor.log
[+0.01s] DEBUG: Launching process 2498: /usr/sbin/unity-system-compositor --from-dm-fd 7 --to-dm-fd 14 --vt 7
[+0.01s] DEBUG: Waiting for system compositor for 60s
[+0.01s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.34s] DEBUG: Compositor closed communication channel
[+0.34s] DEBUG: Process 2498 exited with return value 1
[+0.34s] DEBUG: Releasing VT 7
[+0.34s] DEBUG: Compositor failed to start, switching to VT mode
[+0.34s] DEBUG: Starting seat
[+0.34s] DEBUG: Starting new display for greeter
[+0.34s] DEBUG: Starting X server on Unity compositor
[+0.34s] DEBUG: Using VT 7
[+0.34s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.34s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.34s] DEBUG: Launching X Server
[+0.34s] DEBUG: Launching process 2500: /usr/bin/X -core :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.34s] DEBUG: Waiting for ready signal from X server :0
[+0.64s] DEBUG: Got signal 10 from process 2500
[+0.64s] DEBUG: Got signal from X server :0
[+0.64s] DEBUG: Connecting to XServer :0
[+0.64s] DEBUG: Starting greeter
[+0.64s] DEBUG: Started session 2503 with service 'lightdm-greeter', username 'lightdm'
[+0.69s] DEBUG: Session 2503 authentication complete with return value 0: Success
[+0.69s] DEBUG: Greeter authorized
[+0.69s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+0.69s] DEBUG: Session 2503 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+0.99s] DEBUG: Greeter connected version=1.7.4
[+0.99s] DEBUG: Greeter connected, display is ready
[+0.99s] DEBUG: New display ready, switching to it
[+0.99s] DEBUG: Activating VT 7
[+1.26s] DEBUG: Greeter start authentication for ventrical
[+1.26s] DEBUG: Started session 2578 with service 'lightdm', username 'ventrical'
[+1.27s] DEBUG: Session 2578 got 1 message(s) from PAM
[+1.27s] DEBUG: Prompt greeter with 1 message(s)
[+1.27s] DEBUG: Greeter start authentication for ventrical
[+1.27s] DEBUG: Session 2578: Sending SIGTERM
[+1.27s] DEBUG: Started session 2579 with service 'lightdm', username 'ventrical'
[+1.27s] DEBUG: Session 2578 terminated with signal 15
[+1.27s] DEBUG: Session 2578 failed during authentication
[+1.29s] DEBUG: Session 2579 got 1 message(s) from PAM
[+1.29s] DEBUG: Prompt greeter with 1 message(s)
[+9.02s] DEBUG: Continue authentication
[+9.15s] DEBUG: Session 2579 authentication complete with return value 0: Success
[+9.15s] DEBUG: Authenticate result for user ventrical: Success
[+9.17s] DEBUG: User ventrical authorized
[+9.18s] DEBUG: Greeter requests session ubuntu
[+9.18s] DEBUG: Using session ubuntu
[+9.18s] DEBUG: Stopping greeter
[+9.18s] DEBUG: Session 2503: Sending SIGTERM
[+9.21s] DEBUG: Session 2503 exited with return value 0
[+9.21s] DEBUG: Greeter quit
[+9.29s] DEBUG: Dropping privileges to uid 1000
[+9.29s] DEBUG: Calling setresgid
[+9.29s] DEBUG: Calling setresuid
[+9.29s] DEBUG: Restoring privileges
[+9.29s] DEBUG: Calling setresuid
[+9.29s] DEBUG: Calling setresgid
[+9.31s] DEBUG: Dropping privileges to uid 1000
[+9.31s] DEBUG: Calling setresgid
[+9.31s] DEBUG: Calling setresuid
[+9.31s] DEBUG: Writing /home/ventrical/.dmrc
[+9.31s] DEBUG: Restoring privileges
[+9.31s] DEBUG: Calling setresuid
[+9.31s] DEBUG: Calling setresgid
[+9.33s] DEBUG: Starting session ubuntu as user ventrical
[+9.33s] DEBUG: Session 2579 running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+9.36s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+9.36s] DEBUG: Greeter closed communication channel

```

```
ERROR: /build/buildd/mir-0.0.6bzr832saucy0/src/server/graphics/gbm/gbm_cursor.cpp(46): Throw in function mir::graphics::gbm::GBMCursor::GBMBOWrapper::GBMBOWrapper(mir::graphics::gbm::GBMPlatform&)
Dynamic exception type: boost::exception_detail::clone_impl<boost::exception_detail::error_info_injector<std::runtime_error> >
std::exception::what: failed to create gbm buffer

```

---

### Post by rrich1974 on 2013-07-10
sorry fo asking...
if i will try ubuntu latest daily build on a live usb, i will have MIR as a default display server or i must install it afterward. 
thanx.

---

### Post by zika on 2013-07-10
> **rrich1974 said:**
> sorry fo asking...
if i will try ubuntu latest daily build on a live usb, i will have MIR as a default display server or i must install it afterward. 
thanx.
No. Yes.
Mir is not even in Alpha stage...

---

### Post by grahammechanical on 2013-07-10
> **rrich1974 said:**
> sorry fo asking...
if i will try ubuntu latest daily build on a live usb, i will have MIR as a default display server or i must install it afterward. 
thanx.

This is what we have been working from

[http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

It works for some of us. It does not work for some of us. It mir is running you should see two cursors (at the moment). Or run this command

```
grep -i LoadModule /var/log/Xorg.0.log
```

You should see references to Nouveau and xmir.

I am of the opinion that once we have mir running then we should not update the system not for a few days. Things are not quite right at the moment in my opinion.

Regards.

---

### Post by zika on 2013-07-10
> **grahammechanical said:**
> I am of the opinion that once we have mir running then we should not update the system not for a few days. Things are not quite right at the moment in my opinion.Using most frequently changing PPA with resolution of a week...?
What about btrfs and rollback...? ;)

---

### Post by ventrical on 2013-07-10
> **grahammechanical said:**
> 

I am of the opinion that once we have mir running then we should not update the system not for a few days. Things are not quite right at the moment in my opinion.

Regards.

Mark Shutttleworth may be having great success (as well as the devs) because it appears they are working with high end Intel chipset, a seemingly mir favorite. I blew out my mir on my Dell this morning by upgrading.  I think it may have had to do with not setting the pref pins. Once we have mir working we should set that file. My mistake.  With my USB v3.0 and my SATAIII SSD it only takes a few minutes to do a fresh install.

---

### Post by ventrical on 2013-07-10
> **zika said:**
> Using most frequently changing PPA with resolution of a week...?
What about btrfs and rollback...? ;)


Good question.  I haven't had a successful rollback with btrfs because I only had mir  running on two seperate machines that were not formatted with btrfs. I have other machines formatted  with btrfs that have had the mir ppa installed, then failed, and have had successful rollbacks to origninal state.  So I for one cannot confirm if the btrfs rollback would rollback into workring state of mir after an upgrade that may have broke the system, but it will rollback to an original working state from a mir breakage.

---

### Post by zika on 2013-07-10
> **ventrical said:**
> Good question.  I haven't had a successful rollback with btrfs because I only had mir  running on two seperate machines that were not formatted with btrfs. I have other machines formatted  with btrfs that have had the mir ppa installed, then failed, and have had successful rollbacks to original state.  So I for one cannot confirm if the btrfs rollback would rollback into workring state of mir after an upgrade that may have broke the system, but ti will rollback to an original working state from a mir breakage.
Simply put: Mir can not break system... It can only break LightDM and somewhat X... System is OK either way... You (I suspect) count case when You can not use LightDM as a broken system which is (if my assumption is true) far from true...
We've had occasions in Testing where DM was broken but we lived happily for a day or week with other ways of using X or using another DM...
Just show me one way how Mir could break system...
I've (and still do) with Mir and all troubles I've got myself (with help of Mir) I managed to rectify and I'm writting this from the same install that is more than a half a dozen months old if not older...
Just have right tools handy and... write all the stuff that You're changing on paper, and... Bob is Your uncle, as they say, I'm told...

---

### Post by ventrical on 2013-07-10
> **zika said:**
> Simply put: Mir can not break system... It can only break LightDM and somewhat X... System is OK either way... You (I suspect) count case when You can not use LightDM as a broken system which is (if my assumption is true) far from true...
We've had occasions in Testing where DM was broken but we lived happily for a day or week with other ways of using X or using another DM...
Just show me one way how Mir could break system...
I've (and still do) with Mir and all troubles I've got myself (with help of Mir) I managed to rectify and I'm writting this from the same install that is more than a half a dozen months old if not older...
Just have right tools handy and... write all the stuff that You're changing on paper, and... Bob is Your uncle, as they say, I'm told...

 Basically this is what I have been trying to say .. and btrfs fills that gap .. but you're right.

when I say "busted" I mean that .. yes .. lighdm is not working and cannot get unity desktop .. etc...  I totally understand that with much work, downtime and fiddling around it is most likely that a 'busted' *mir* system can be brought back to some semblance of workability (have yet to see it documented) but with USB 3.0, SSD and only 7 minutes to install it saves me a lot of downtime just to do a fresh install and get back online.

.. and I am writing stuff down on paper..

Zika said  "Just show me one way how Mir could break system..."

  Mir .. in effect 'breaks' the Unity Desktop. It may not break terminal or recovery mode but Unity is in a non productive state in most cases (as per evidenced by all the reports here) I need not to go there..

thanks for your  help zika..

---

### Post by ventrical on 2013-07-10
> **grahammechanical said:**
> This is what we have been working from

[http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

It works for some of us. It does not work for some of us. It mir is running you should see two cursors (at the moment). Or run this command

```
grep -i LoadModule /var/log/Xorg.0.log
```

You should see references to Nouveau and xmir.

I am of the opinion that once we have mir running then we should not update the system not for a few days. Things are not quite right at the moment in my opinion.

Regards.

  I have this on my Dell.

```

ventrical@ventrical-Dell-DV051:~$ grep -i LoadModule /var/log/Xorg.0.log
[    27.733] (II) LoadModule: "glx"
[    27.914] (II) LoadModule: "xmir"
[    28.016] (II) LoadModule: "intel"
[    28.053] (II) LoadModule: "vesa"
[    28.074] (II) LoadModule: "modesetting"
[    28.082] (II) LoadModule: "fbdev"
[    28.104] (II) UnloadModule: "vesa"
[    28.104] (II) UnloadModule: "modesetting"
[    28.105] (II) UnloadModule: "fbdev"
[    28.106] (II) LoadModule: "fb"
[    28.136] (II) LoadModule: "dri2"
[    28.283] (II) LoadModule: "evdev"
ventrical@ventrical-Dell-DV051:~$ 

```

---

### Post by anca-emanuel on 2013-07-10
[http://www.markshuttleworth.com/archives/1269](http://www.markshuttleworth.com/archives/1269)

Mark says mir works for him.
[[IMG]http://i.imgur.com/Yui9I4Hl.png[/IMG]]("http://fc06.deviantart.net/fs71/i/2012/054/1/9/courage_the_cowardly_dog__by_drakefire3k-d4qrzk9.png")

---

### Post by ventrical on 2013-07-10
> **mc4man said:**
> I'd probably wait for them to show in saucy repo's, not exactly sure what the intended target is

As is this latest go round fails to start, shows this error - 

Part of the libegl1-mesa package

Also with the ppa packages but not using unity-system-compositor I get indicator-datetime-service pegging a core+ & grabbing a whole lot of ram as in screen


 All those depnds are now resolved , at least with my Dell (Intel base). There is a nasty bug. When moving the cursor to the right  (like try to push the mouse pointer off the screen) the screen will go blank or blue or pink .. then move the mouse towards the left and the screen will come back. Top reports compiz pegged at 67% when this happens but then it goes back down after a few seconds of inactivity.

---

### Post by zika on 2013-07-10
> **ventrical said:**
> work, downtime and fiddling around it is most likely that a 'busted' *mir* system can be brought back to some semblance of workability (have yet to see it documented) but with USB 3.0, SSD and only 7 minutes to install it saves me a lot of downtime just to do a fresh install and get back online.
[B]Vive [B]la[COLOR=#000000] différence...
[/COLOR][/B][/B]I really do not mind spending couple of minutes in saving install that is custom fit for my needs (not talking about looks (i do not care about looks) but about tools)...
Yes, I work on this machine and listen music and...
The only thing I do not like is re-install... ;) Which, it seems You do quite quick... Maybe I should try, but not on my machine...
If a whell or something less is broken I do not change my whole car... ;)

---

### Post by ventrical on 2013-07-10
> **zika said:**
> [B]Vive [B]la[COLOR=#000000] différence...
[/COLOR][/B][/B]I really do not mind spending couple of minutes in saving install that is custom fit for my needs (not talking about looks (i do not care about looks) but about tools)...
Yes, I work on this machine and listen music and...
The only thing I do not like is re-install... ;) Which, it seems You do quite quick... Maybe I should try, but not on my machine...
If a whell or something less is broken I do not change my whole car... ;)


 I have 7 (seven) machines going here. I love hacking and fiddling and discovering when I got extra time. (did that with btrfs) <thats pretty well documented>. What more can I say.

Yeah .. don't change the whole car .. etc.. but remember - you have to take the old wheel off before you put the new one on ;)  I like speedy ubuntu systems. Particularily I like speedy Unity desktop. You can put four new wheels on an old rust-bucket clunker and it will still be an old rust-bucket clunker. ;)

---

### Post by cecilpierce on 2013-07-10
Got colored panels again, wonder what causes that ?

---

### Post by dino99 on 2013-07-10
> **cecilpierce said:**
> Got colored panels again, wonder what causes that ?

is it with or without the 3D glasses ?

i suppose you have added some snippets inside bashrc a while back, then forgot it.

---

### Post by zika on 2013-07-10
> **ventrical said:**
> I have 7 (seven) machines going here. I love hacking and fiddling and discovering when I got extra time. (did that with btrfs) <thats pretty well documented>. What more can I say.

Yeah .. don't change the whole car .. etc.. but remember - you have to take the old wheel off before you put the new one on ;)  I like speedy ubuntu systems. Particularily I like speedy Unity desktop. You can put four new wheels on an old rust-bucket clunker and it will still be an old rust-bucket clunker. ;)
No, I'll fix broken wheel...
How could You know what is broken if You do not try to fix it...

---

### Post by grahammechanical on 2013-07-10
> **zika said:**
> Using most frequently changing PPA with resolution of a week...?
What about btrfs and rollback...? ;)

I have just tested that. It works. And something is most definitely breaking something and it is the recent updates. Here is the story.

Saucy+btrfs install from 7th July daily image + mir = working + apt-btrfs-snapshot = working.Still running xmir. No updates other than those that came with dist-upgrade to get mir.

 Just now (10th) ran on update and it = black screen on restart. Recovery Resume = desktop but no mir.

Use Recovery apt-snapshot to revert to snapshot taken as the update was initiated = restart  = black screen. Resume = login screen bounce.

Use Recovery apt-snapshot to revert to snapshot taken on 9th July = resume = blackscreen and reboot = desktop + mir.

When we use Recovery mode Resume is the ony boot option after we have tried the other options such as apt-snapshot or network and resume does not load the video driver even if it is Nouveau. It loads llvmpipe.

So, btrfs rollback from a broken desktop does work but I do not think that it is the mir that is breaking things. On my daily working saucy I am getting compiz crashing with SIGSEGV in get CompPluginVTable 20090315_unityshell() = broken OS


Regards.

---

### Post by ventrical on 2013-07-10
> **zika said:**
> No, I'll fix broken wheel...
How could You know what is broken if You do not try to fix it...

[http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)

---

### Post by mc4man on 2013-07-10
> **cecilpierce said:**
> Got colored panels again, wonder what causes that ?

Just the current overall instability of the unity compositor.
Once & a while I do get the yellow though it's under the unity panel.
At least here things can be ok on one log in, a bit south on others or go bad during a session
For example I just logged out/in & getting absolutely no keyboard lag, even in this post. That could & likely will change at some point during this session or on a later login.

Another example - 
During last login indicator-datetime-service at some point started running amok,  pegging a core & leaking copious amounts of memory. Wasn't really prepared to log (pidstat), but screen will show. Normally it uses about 7000kB, after 15 min. of running off had taken 1.6 gig's

---

### Post by grahammechanical on 2013-07-10
> **cecilpierce said:**
> Got colored panels again, wonder what causes that ?

What settings do you have for the Dash blur and the opacity of the top panel and the Launcher. I am using the standard Radiance theme with the default settings. I have not tested these things but I suppose we should.

Regards.

---

### Post by zika on 2013-07-10
> **ventrical said:**
> [http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)
Knocking on open door. I've participated in that thread...

---

### Post by NikTh on 2013-07-11
I filled a new bug here : [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1200097](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1200097) 
Somehow, apport allowed me to report this bug even with third-party software installed (Xmir ppa enabled). 

The report now is full of logs by apport-gtk. I hope this helps devs to spot the exact problem.

---

### Post by cecilpierce on 2013-07-11
> **NikTh said:**
> I filled a new bug here : [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1200097](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1200097) 
Somehow, apport allowed me to report this bug even with third-party software installed (Xmir ppa enabled). 

The report now is full of logs by apport-gtk. I hope this helps devs to spot the exact problem.

Thanks! Maybe now something will get fixed...:P

---

### Post by wojox on 2013-07-11
```
[SeatDefaults]
#type=unity
```

Still rely on this with my Intel driver. There is a bit of a delay typing with Mir enabled. Mouse and trackpad are better.

Awesome, Ubuntu has it's own Graphics Stack. :)

---

### Post by cecilpierce on 2013-07-11
Nice!   :(

---

### Post by wojox on 2013-07-11
> **cecilpierce said:**
> Nice!   :(

Proprietary drivers at their best. :)

---

### Post by sanderj on 2013-07-11
After my other Mir install died too (black screen after a reboot), even without executing any updates, I'm now back on 13.04.

I'll wait until 13.10 has Mir builtin. Hopefully that's soon.

---

### Post by rrnbtter on 2013-07-11
Greetings,

> **sanderj said:**
>  I'll wait until 13.10 has Mir builtin. Hopefully that's soon.

+1
Especially since mir for desktop is being hacked at this point. It isn't even in the repos.  In addition, with some of the continuing updates 13.04 is getting very impressive, at least for me.  It is really nicer than anything I have ever used no matter the genre. I hope I'm not just getting lazy but I do have Saucy running on my alternate HD. 
PS Thanks to all of you serious testers for your input it has been scary fun so far. There is just no usable mir driven desktop thus far and I have work to do. Gee, I think Precise, Quantal, and Raring spoiled me!

---

### Post by wojox on 2013-07-12
> **rrnbtter said:**
> Thanks to all of you serious testers for your input it has been scary fun so far. 

+1 the folks who test proprietary drivers have the hardest job with the least amount of thanks. :)

---

### Post by sanderj on 2013-07-12
> **wojox said:**
> +1 the folks who test proprietary drivers have the hardest job with the least amount of thanks. :)

That's why I try to avoid any hardware that needs/prefers a proprietary driver. Therefore only Intel GPU's for me ...

---

### Post by zika on 2013-07-12
> **sanderj said:**
> That's why I try to avoid any hardware that needs/prefers a proprietary driver. Therefore only Intel GPU's for me ...What's wrong with ATI? ;)

---

### Post by jerrylamos on 2013-07-12
Latest Saucy updates and ppa mir for the last days, mir not working, Alt-Tab takes many many seconds.  Shutdown hangs forever depleting battery.  Bug written.  Keyboard response O.K., likely because mir not working?

Logout/login very very slow.  Internal error, bug written.

Another partition at same level of Saucy without ppa no such problems.

I wonder what level of saucy the mir developers are using?  Or is there something additional to do over what Ollie has written?

---

### Post by ventrical on 2013-07-12
> **jerrylamos said:**
> Latest Saucy updates and ppa mir for the last days, mir not working, Alt-Tab takes many many seconds.  Shutdown hangs forever depleting battery.  Bug written.  Keyboard response O.K., likely because mir not working?

Logout/login very very slow.  Internal error, bug written.

Another partition at same level of Saucy without ppa no such problems.

I wonder what level of saucy the mir developers are using?  Or is there something additional to do over what Ollie has written?


There will not be a stable mir for desktop computers until 14.04 dev. Only tablets , phones (and tvs? ) for now.


The only Mir-native Linux desktop right now is Unity 8. By [[COLOR=#234865][COLOR=#234865 !important][FONT=verdana][COLOR=#234865 !important][FONT=verdana]Ubuntu[/FONT][/FONT][/COLOR][/COLOR][/COLOR]]("http://www.phoronix.com/scan.php?page=news_item&px=MTM5NDQ#")  13.10, Canonical wants Unity 8 with Mir as an experimental option on  the desktop though for mobile Ubuntu Touch devices it may be in good  standing then. Mir on the Linux desktop isn't expected to be stable  until 2014. It was just last week that [a package archive was created for Mir / Unity 8]("http://www.phoronix.com/scan.php?page=news_item&px=MTM5Mzc") for those wanting to try out this experimental code on Ubuntu Touch.[HR][/HR]


from..

[http://www.phoronix.com/scan.php?page=news_item&px=MTM5NDQ](http://www.phoronix.com/scan.php?page=news_item&px=MTM5NDQ)

---

### Post by jerrylamos on 2013-07-12
> **ventrical said:**
> There will not be a stable mir for desktop computers until 14.04 dev. Only tablets , phones (and tvs? ) for now.


The only Mir-native Linux desktop right now is Unity 8. By [[COLOR=#234865][COLOR=#234865 !important][FONT=verdana][COLOR=#234865 !important][FONT=verdana]Ubuntu[/FONT][/FONT][/COLOR][/COLOR][/COLOR]]("http://www.phoronix.com/scan.php?page=news_item&px=MTM5NDQ#")  13.10, Canonical wants Unity 8 with Mir as an experimental option on  the desktop though for mobile Ubuntu Touch devices it may be in good  standing then. Mir on the Linux desktop isn't expected to be stable  until 2014. It was just last week that [a package archive was created for Mir / Unity 8]("http://www.phoronix.com/scan.php?page=news_item&px=MTM5Mzc") for those wanting to try out this experimental code on Ubuntu Touch.[HR][/HR]


from..

[http://www.phoronix.com/scan.php?page=news_item&px=MTM5NDQ](http://www.phoronix.com/scan.php?page=news_item&px=MTM5NDQ)

Updated saucy amd64 today, 12 July 2013, then put on mir ppa.  Sort of running, dual cursors and all.  Got in internal error, Plymouth, on boot.

Keyboard response a little faster than the last time mir would run for me..

Had a lot of unstable logging in to ubuntu forums.

Note this is an external monitor on an Acer Aspire 1 netbook, Intel Atom.

IIntel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller

BTW, external monitor is a 15.5" TV only resolution supported is the max of 1920x1080 hard to read vs. normal 1366x768.

---

### Post by wojox on 2013-07-14
Found this tonight [URL="http://blog.cooperteam.net/2013/07/xmir-performance.html"] XMir Performance
Or: Why XMir is slower than X, and how we'll fix it[/URL]

---

