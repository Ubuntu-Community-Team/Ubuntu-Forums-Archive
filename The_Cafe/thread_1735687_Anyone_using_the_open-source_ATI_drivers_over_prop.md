---
title: "Anyone using the open-source ATI drivers over proprietary?"
date: 2011-04-21
forum: The Cafe
---

### Post by akand074 on 2011-04-21
Hey guys,

I'm going to update to Ubuntu 11.04 soon on my desktop, already have on my laptop. I was just wondering if anyone uses the open-source drivers over the proprietary and if they'd like to share their experience? I hear the open-source drivers are getting really good (some have 3D acceleration, does mine?). I had the open-source drivers running for a few days on my laptop before I installed the proprietary drivers and it was running perfectly. I'm using the ATI Radeon HD 5770 card, I don't game, though I watch HD movies often (up to ~25GB files sometimes) and the occasional encode (though isn't that pure CPU?). With that said is there any real benefit to the proprietary drivers? Is the open-source more stable than the proprietary? I notice my boot splash gets ugly after installing proprietary drivers. If the proprietary only has pros and no major cons then I would just continue to use them. I'm likely going to stick with Unity on my laptop but might either use Unity or Gnome 3 on my desktop until Unity matures a bit more but undecided, so I didn't set up cube or anything so I don't know if those things work now with the open-source drivers... but I think they did in 10.10 with my card.. can't remember. Anyways I'd like to hear people's input and experiences with both.

---

### Post by aaaantoine on 2011-04-21
I'm using open source drivers.  I do so on my laptop out of necessity -- the Radeon Xpress 1100 is no longer supported by AMD Catalyst.  I do so on my desktop primarily because I'd rather have the Linux graphics stack for best stability.

I get 3D acceleration on my Radeon 4200, though admittedly it pales in comparison to the performance in Windows.  Performance on the Xpress 1100 just plain sucks, but that has nothing to do with the drivers. ;)

---

### Post by beew on 2011-04-21
[http://ubuntuforums.org/showthread.php?t=1730006](http://ubuntuforums.org/showthread.php?t=1730006)


I think the open source drivers are interesting for development purpose but IMO if you use the open diver you may as well get a cheap Intel card because the open driver can't use most functions of the graphic card. You can get Compiz with an old Intel card, it isn't really that big a deal. Unity 3 D ran without problem on my Dell D410.

---

### Post by el_koraco on 2011-04-21
I am, not so much by choice, but due to the fact that fglrx wreaks havoc on my machine. Depends on the needs I guess, with fglrx i was not able to watch HD videos on my laptop, but with radeon it works just fine. I suggest you try both for a week, and then decide. Although the only real way of getting rid of fglrx once installed is to reinstall the system. 

Big lol

---

### Post by handy on 2011-04-21
I've been using the git open-source driver stack & kernels for most of the last 18 months. The speed of improvements in so many ways over that period of time is really quite amazing.

I'm running an HD2600 Pro /256MB GPU, on Arch 64bit.

You may or may not find anything interesting in this thread, the first post has a number of informative links & some potentially valuable info' to Ubuntu users also:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

This thread isn't very active of late, as there really haven't been much in the way of problems to discuss. The improvements just keep on coming. 

I've been using Gallium for months now & it is just great. It is my understanding that Ubuntu 11.04 installs Gallium by default, which is great.

---

### Post by 3Miro on 2011-04-21
I have couple of Radeon 4xxx cards and for both of them I have much better experience with the FOSS drivers. Unity works great with the FOSS driver anyway. I think the FOSS drivers for the 5xxx series was even better (but don't quote me on that). For anything Radeon 4xxx and newer, I recommend the FOSS drivers, the prop ones are only for the case if something isn't working properly.

---

### Post by akand074 on 2011-04-22
Yeah from what I'm hearing, I might just stick with the FOSS drivers until I hit a problem or performance issue. In which case I'll install the proprietary ones. Seems like a logical way to go.

---

### Post by Lucradia on 2011-04-22
Propietary AMD Drivers have one of two problems in Linux:

1. You get that silly "Device not supported" watermark in ther upper right, or lower right of the screen (it's an OSD, it doesn't appear on screenshots / video recording, thank heavens.)

2. When using DRI Enabled composition such as Mutter, Clutter, Compiz, or the like. The computer may slow to a halt when simply dragging a window. This does not occur when using Wine games, without your compositing enabled. For whatever reason, Wine chooses to bypass DRI.

Intel has the same issue as number 2 when DRI is forced. (This is because Intel can't handle DRI, it must use AiGLX.)

The OSS Drivers don't have this problem usually, but some AMD Radeons will not allow compiz usage with OSS, but will allow OpenGL / Wine 3D to work.

And we all know about the issue with NVIDIA Quaddros >_>

---

### Post by krapp on 2011-04-22
Installing the proprietary driver has been the easiest way on both Ubuntu and Debian to get my second display to work. Not saying that I couldn't have fiddled around with the open source driver before installing the non-free one, but a tie dyed color screen requires a fix, and fglrx or whatever it's called seemed the easiest solution. I have the Mobility Radeon HD 5730.

---

### Post by Lucradia on 2011-04-22
> **krapp said:**
> Installing the proprietary driver has been the easiest way on both Ubuntu and Debian to get my second display to work. Not saying that I couldn't have fiddled around with the open source driver before installing the non-free one, but a tie dyed color screen requires a fix, and fglrx or whatever it's called seemed the easiest solution. I have the Mobility Radeon HD 5730.

The fglrx provided via jockey is not the same as the actual propietary driver released by AMD. The fglrx provided by ubuntu is the non-free open-source driver, if you can believe that.

---

### Post by Claus7 on 2011-04-22
Hello,

since you are interested in everyday tasks, and you have verified that the open source drivers are ok with you, then stick with those. You won't have to install them from time to time in case a kernel update comes along.

For gpu computing I think that the proprietary ones via amd's website seem to be a must.

Regards!

---

### Post by krapp on 2011-04-22
> **Lucradia said:**
> The fglrx provided via jockey is not the same as the actual propietary driver released by AMD. The fglrx provided by ubuntu is the non-free open-source driver, if you can believe that.

I'm not sure what jockey is, but on both Debian and Ubuntu I installed the Catalyst Control Center by installing fglrx if I remember correctly.

The Debian Wiki says as much [http://wiki.debian.org/ATIProprietary](http://wiki.debian.org/ATIProprietary) but according to [http://en.wikipedia.org/wiki/Fglrx#Linux](http://en.wikipedia.org/wiki/Fglrx#Linux) fglrx no longer exists, so I'm not sure what's what.

---

### Post by Lucradia on 2011-04-22
> **krapp said:**
> I'm not sure what jockey is, but on both Debian and Ubuntu I installed the Catalyst Control Center by installing fglrx if I remember correctly.

The Debian Wiki says as much [http://wiki.debian.org/ATIProprietary](http://wiki.debian.org/ATIProprietary) but according to [http://en.wikipedia.org/wiki/Fglrx#Linux](http://en.wikipedia.org/wiki/Fglrx#Linux) fglrx no longer exists, so I'm not sure what's what.

On Ubuntu, running jockey-gtk opens up the "Hardware Drivers" dialog.

jockey-common is the back-end and text/CLI version.

---

### Post by neu5eeCh on 2011-04-22
I use the open source drivers. Some 3-D games, like Flightgear, don't work very well, but I'm not a gamer. What's interesting though, is that video playback sucks with proprietary drivers. There's lots and lots of tear out. The open source drivers are almost comparable to windows in terms of video playback. So... I use open source.

---

### Post by screaminj3sus on 2011-04-22
fglrx is still all around better right now. For a while the only reason I ever used the oss drivers was because fglrx had tearing, and no way to stop tearing in videos, but now with the tear free desktop feature that's solved. The only other advantage they have right now is you can always use them with the latest kernel/xorg ect...

Power management for the oss drivers is basically useless and using them on a mobile system isn't really an option. Terrible battery life and extremely high temps just idling.

> **VTPoet said:**
> I use the open source drivers. Some 3-D games, like Flightgear, don't work very well, but I'm not a gamer. What's interesting though, is that video playback sucks with proprietary drivers. There's lots and lots of tear out. The open source drivers are almost comparable to windows in terms of video playback. So... I use open source.

This used to be the only reason I didn't use catalyst but its not an issue anymore. This is fixed in the newer catalyst releases. Open catalyst control center and enable "tear free desktop" no more tearing in videos or compiz.

And IMO neither driver comes close to windows when it comes to video playback. No hardware acceleration.

---

### Post by neu5eeCh on 2011-04-22
> **screaminj3sus said:**
>  And IMO neither driver comes close to windows when it comes to video playback. No hardware acceleration.

Wayland. I have high, high hopes for Wayland.

---

### Post by Claus7 on 2011-04-22
Hello,

> **screaminj3sus said:**
> 
...This used to be the only reason I didn't use catalyst but its not an issue anymore. This is fixed in the newer catalyst releases. Open catalyst control center and enable "tear free desktop" no more tearing in videos or compiz.


I had a minor tearing as well, while I was playing videos, yet it really was almost negligible. With your solution there is really no tearing at all!

Thank you,
Regards!

---

### Post by krapp on 2011-04-22
> **screaminj3sus said:**
> 



This used to be the only reason I didn't use catalyst but its not an issue anymore. This is fixed in the newer catalyst releases. Open catalyst control center and enable "tear free desktop" no more tearing in videos or compiz.

And IMO neither driver comes close to windows when it comes to video playback. No hardware acceleration.

Where in the control center is this? I am using version 2.13 and Catalyst 10.9.

---

### Post by screaminj3sus on 2011-04-22
> **krapp said:**
> Where in the control center is this? I am using version 2.13 and Catalyst 10.9.

You need catalyst 11.x (I believe it was introduced in 11.2)

[IMG]http://img585.imageshack.us/img585/9573/screenshotjxw.png[/IMG]

---

### Post by akand074 on 2011-04-23
I suppose it might be better to just go straight to the proprietary drivers as I usually do. Until the open-source ones get better. I'll install it directly from AMD though. I may play around with the open-source for a bit first too. I'm learning a lot though. I can't wait until I don't need any proprietary software on my system. Open-source alternatives seem to integrate much better.

---

### Post by Claus7 on 2011-04-23
Hello,

> **akand074 said:**
> I suppose it might be better to just go straight to the proprietary drivers as I usually do. Until the open-source ones get better. I'll install it directly from AMD though. I may play around with the open-source for a bit first too. I'm learning a lot though. I can't wait until I don't need any proprietary software on my system. Open-source alternatives seem to integrate much better.

just don't forget that while "playing around", every time you install a new driver you have to remove totally your previous one with all the files and libraries affiliated to it.

Regards!

---

### Post by blueturtl on 2011-04-23
Using OSS drivers here with Radeon HD 4650.

I do this because... 1) the desktop environment and Compiz work better with the OSS drivers (video playback has ugly tearing and other VSYNC issues with Catalyst and Compiz) and 2) because Catalyst under my test has not improved compatibility or performance for any games that fail to work with the OSS drivers.

---

### Post by Zero Prime on 2011-04-23
> **Lucradia said:**
> Propietary AMD Drivers have one of two problems in Linux:

1. You get that silly "Device not supported" watermark in ther upper right, or lower right of the screen (it's an OSD, it doesn't appear on screenshots / video recording, thank heavens.)

2. When using DRI Enabled composition such as Mutter, Clutter, Compiz, or the like. The computer may slow to a halt when simply dragging a window. This does not occur when using Wine games, without your compositing enabled. For whatever reason, Wine chooses to bypass DRI.

Intel has the same issue as number 2 when DRI is forced. (This is because Intel can't handle DRI, it must use AiGLX.)

The OSS Drivers don't have this problem usually, but some AMD Radeons will not allow compiz usage with OSS, but will allow OpenGL / Wine 3D to work.

And we all know about the issue with NVIDIA Quaddros >_>

Never had either of these problems, and I've been using AMD/ATI for years.

---

### Post by Lucradia on 2011-04-23
> **Zero Prime said:**
> Never had either of these problems, and I've been using AMD/ATI for years.

Then I guess I'm the oddball out for problem 1, along with over a dozen other users. (There is a launchpad bug, which is still active, concerning the AMD Logo overlay issue.)

---

### Post by screaminj3sus on 2011-04-23
> **Zero Prime said:**
> Never had either of these problems, and I've been using AMD/ATI for years.

This is only a problem with the "11.4b hotfix" driver. (the watermark)

I've never had the issue with dragging a window in compiz slowing everything down...

---

### Post by Lucradia on 2011-04-23
> **screaminj3sus said:**
> I've never had the issue with dragging a window in compiz slowing everything down...

Everyone who says this usually gets their non-free driver from the Hardware Drivers dialog (Jockey) in the System > Admin menu, and not via envy or AMD's website.

I've only had it happen about 4 times, and it only happened with the RUN / Envy drivers. Not jockey, not OSS.

---

### Post by Zero Prime on 2011-04-23
LoL, so we should stick with the driver provided in additional drivers.  Hmmm, no wonder I've never had a problem :)  Plus, I get all the effects I want with no lag :)

---

### Post by Lucradia on 2011-04-23
> **Zero Prime said:**
> LoL, so we should stick with the driver provided in additional drivers.  Hmmm, no wonder I've never had a problem :)  Plus, I get all the effects I want with no lag :)

Which is the opposite usually of nvidia. I get less lag with the propietary nvidia.com driver than the one from jockey. Then again, the one from jockey is just the same as the Run, just older.

---

### Post by screaminj3sus on 2011-04-23
> **Lucradia said:**
> Everyone who says this usually gets their non-free driver from the Hardware Drivers dialog (Jockey) in the System > Admin menu, and not via envy or AMD's website.

I've only had it happen about 4 times, and it only happened with the RUN / Envy drivers. Not jockey, not OSS.

Which issue are you talking about? The watermark? That one is a known issue with the specific driver I mentioned

I've never had either issue (I haven't used the 11.4b driver, I've used up to 11.3 and the 11.5 prerelease in natty). Right now I've installed mine using jockey because I am on natty and the repo drivers are the only ones that work. But in 10.10 (and other distros) I used the driver from amd's website, and installed them with the buildpkg option and never had those issues either.

---

### Post by Lucradia on 2011-04-23
> **screaminj3sus said:**
> buildpkg option

This option always errored for me, so I had to have the run file do a general install.

---

### Post by neu5eeCh on 2011-04-23
Well... I was excited to install the new Catalyst Control Center but no go. Followed the instructions here:

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

I suspect that my card isn't supported?

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

I reinstalled the open source drivers and will continue happily word-processing in 2D. Why isn't the new Control Center in the repo?

---

### Post by Lucradia on 2011-04-23
> **VTPoet said:**
> Why isn't the new Control Center in the repo?

You mean jockey. The *official* CCC can't be in the repo, because the *official* CCC is part of the non-free package.

---

### Post by screaminj3sus on 2011-04-23
> **VTPoet said:**
> Well... I was excited to install the new Catalyst Control Center but no go. Followed the instructions here:

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

I suspect that my card isn't supported?

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

I reinstalled the open source drivers and will continue happily word-processing in 2D. Why isn't the new Control Center in the repo?

Your card should be supported.

---

