---
title: "Ubuntu 16.04?"
date: 2016-05-05
forum: Ubuntu, Linux and OS Chat
---

### Post by frank18 on 2016-05-05
I just want to ask,why to install Ubuntu 1604? if you are running Ubuntu 14.04 LTS with no issues at all, while 1604 seems to be a Mess?

---

### Post by cariboo on 2016-05-05
If you have newer hardware, 14.04 may not support it. I've been running 16.04 since last October (Development cycle) on my laptop and desktop with zero problems. You usually won't hear from people that are running a newly released version, if they are happy with it.

---

### Post by kansasnoob on 2016-05-05
I'm keeping most of the machines I maintain on Trusty because they're working fine and still supported until April 2019. If it ain't broke don't fix it.

---

### Post by pauljw on 2016-05-05
> **kansasnoob said:**
> I'm keeping most of the machines I maintain on Trusty because they're working fine and still supported until April 2019. If it ain't broke don't fix it.

+1 on keeping 14.04LTS.  It's running without issue on both mine and my daughters laptops.  It's stable, secure and supported till 2019.  Unless you find a specific need that requires the upgrade, I wouldn't recommend it.  To upgrade simply because an upgrade is available defeats the purpose of the LTS build.

If you just want to satisfy your curiosity, try installing virtualbox and running new releases as virtual machines.  Works very well for me.

---

### Post by QIII on 2016-05-05
I'll be keeping my servers running Trusty for a while.  Maybe until 18.04 comes out.

On this machine I have Trusty on one SSD and Xenial on another.  I'd go all Xenial, except that the AMDGPU driver is not completely ironed out and AMDGPU-Pro is a beta that isn't yet intended for Xenial.  I expect to be doing some testing as it moves along.  Testing always brings the possibility of catastrophe, so I'm not putting all my eggs in that basket.  But if it were not for that, my daily driver would be running only Xenial.

---

### Post by grahammechanical on 2016-05-06
The release notes say this,

> 14.04 LTS to LTS upgrades will be enabled with the 16.04.1 LTS point release, in approximately 3 months time.

So, 14.04 LTS users should not be upgrading at this time anyway. I disagree with the opinion that 16.04 is a mess. I have been running xenial as my daily driver all through its 26 week development and not had to re-install it.

Upgrading is a mess for some people every time there is a new release. This is why we recommend either a fresh install or reverting to open source video drivers and a desktop that is as default as possible before running the upgrade.

It is because 16.04 will be the last LTS using Unity 7 that efforts are being made to keep 16.04 useful for most of its life. It has a software store that can now install Debian & Snap packaged applications even though there are few snap packages that we would want to use at the moment. And, depending on the response of motherboard manufacturers, the same software store will be able to do BIOS/UEFI firmware updates. Who is going to be the first to test that out? 

There is still a lot of development happening to 16.04. A Mir/Unity 8 log in option that will get more & more useful as time goes on so that we can get used to what might be the default session on the 18.04 LTS. All of it will take place without breaking the OS. I am confident of that.

Regards.

Regards.

---

### Post by frank18 on 2016-05-06
Thanks guys; i have a Desktop Lenovo ThinkCenter a71, I5  duo core 2400 CPU 3.1GHZ Ram 4 GB socket 1155 ATI AMD 6450 running Ubuntu 14.04,i have an extra HDD with 15.10 installed and  i tried it and must say that was a huge mess, i did not have a good experience,
Since this is a final version of Ubuntu 1604LTS, i maybe give it a try on this extra HDD.

---

### Post by neu5eeCh on 2016-05-06
> **grahammechanical said:**
> It is because 16.04 will be the last LTS using Unity 7.....

HAHAHAHAHA! Oops... sorry. :oops: Don't know what came over me. You were saying?

---

### Post by kansasnoob on 2016-05-06
> AMD 6450

You'll want to read this:

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Graphics_and_Display](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Graphics_and_Display)

> The fglrx driver is now deprecated in 16.04, and we recommend its open source alternatives (radeon and amdgpu). AMD put a lot of work into the drivers, and we backported kernel code from Linux 4.5 to provide a better experience. 

---

### Post by poorguy on 2016-05-07
I did it just because I had several desktops that wasn't doing anything.
Two installed right out of the box and works perfectly no complaints.
 
A third desktop has a shutdown problem and have to use the power button to do a shutdown.

No regrets with Ubuntu Mate 16.04. 
This is my first Linux OS release and a new learning experience.

Whats really been an issue for me is learning about all of the new  changes but that is a learning problem I have and not the distro.

---

### Post by frank18 on 2016-05-07
[COLOR=#000000][FONT=verdana]Hi guys i just installed Ubuntu 1604 on a spare extra HDD that i have, so far i overcomed some install bugs the only thing that im dissapointed cause i installed Chrome and i have it in the task-bar but it doesn't open or show in the desktop,[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]is there anything i can do! thanks[/FONT][/COLOR]

---

### Post by poorguy on 2016-05-07
Hey frank18,

Google Chrome doesn't support 32bit Linux anymore. Didn't say if you installed 32 bit or 64 bit.

---

### Post by frank18 on 2016-05-07
> **poorguy said:**
> Hey frank18,

Google Chrome doesn't support 32bit Linux anymore. Didn't say if you installed 32 bit or 64 bit.

Thanks poorguy; i did install 64 bit, also i can't launch synaptic

---

### Post by poorguy on 2016-05-07
Hey frank18,

Lot of problems with 16.04 release.

---

### Post by SantaFe on 2016-05-07
I installed Ubuntu-MATE 16.04 because it is the first LTS version.  ;)

---

### Post by frank18 on 2016-05-07
> **SantaFe said:**
> I installed Ubuntu-MATE 16.04 because it is the first LTS version.  ;)



Well i've had it.with 1604, i'm back on Ubuntu 14.04 no more issues,

---

### Post by poorguy on 2016-05-07
> **frank18 said:**
> Well i've had it.with 1604, i'm back on Ubuntu 14.04 no more issues,

I expected it to have some problems and in my case I can't do a proper shutdown but I believe that will be fixed eventually by the next point release.

-------------------------------------------------------------------------------------------------------------
SantaFe Posted. 	 	 		[INDENT] 			 				Re: Ubuntu 16.04?
 			 			I installed Ubuntu-MATE 16.04 because it is the first LTS version.  :wink: 		[/INDENT] 	
-------------------------------------------------------------------------------------------------------------

^ This is another cool reason IMO.

---

### Post by kansasnoob on 2016-05-08
> **SantaFe said:**
> I installed Ubuntu-MATE 16.04 because it is the first LTS version.  ;)

I've been using Ubuntu MATE Xenial for just 2 1/2 days and I've only encountered two issues that also affect Ubuntu and Ubuntu GNOME; [optical discs w/data don't always mount]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1577768") properly, and we still get the [pesky disc already mounted warning]("https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1069964") when inserting blank media in an optical drive. I think both of those are because GNOME made a mess of gvfs, gvfsd, and fuse nearly 4 years ago :(

But the MATE DE has shown itself to be rock solid, and it's nostalgic. It reminds me why I started using Ubuntu circa 2007, everything just works and it's easily customized .................................... I may end up being a convert ................. or would that be a revert :)

---

### Post by frank18 on 2016-05-08
> **poorguy said:**
> I expected it to have some problems and in my case I can't do a proper shutdown but I believe that will be fixed eventually by the next point release.

-------------------------------------------------------------------------------------------------------------
SantaFe Posted.[INDENT]                              Re: Ubuntu 16.04?
                          I installed Ubuntu-MATE 16.04 because it is the first LTS version.  :wink:         [/INDENT]
    
-------------------------------------------------------------------------------------------------------------

^ This is another cool reason IMO.

I don't think you will fix that,hope i'm wrong, but i have a similar experience but with windows 10 on one of my desktops,the same desktop i install Ubuntu and it shuts down without issues on both 1404 and 1604,i think it has to do with Hardware rather then the software which seems to me it's not friendly at all with all this apps stuff trying to mach windows which spend millions while Ubuntu spends peanuts compared to win.

---

### Post by poorguy on 2016-05-08
> **frank18 said:**
> I don't think you will fix that,hope i'm wrong, but i have a similar experience but with windows 10 on one of my desktops,the same desktop i install Ubuntu and it shuts down without issues on both 1404 and 1604,i think it has to do with Hardware rather then the software which seems to me it's not friendly at all with all this apps stuff trying to mach windows which spend millions while Ubuntu spends peanuts compared to win.

Well I won't know until the next point release.
I did read somewhere about Intel hardware problems and Ubuntu 16.04.

---

### Post by neu5eeCh on 2016-05-08
For what it's worth, I was having all sorts of problems with 16.04 until I reverted to an older kernel (4.2 instead of 4.4). I think there's a nasty regression in 4.4 having to do with Intel drivers. It messed all sorts of things up. Try an older kernel before you give up on 16.04.

---

### Post by night_sky2 on 2016-05-09
The Trusty Tahr has been very trusty for me so far. Kernel 3.13 is rock solid. I won't upgrade until I have to change to another computer. I mean why fixing something that isn't broke? It makes absolutely no sense. There is a reason why Ubuntu 14.04 is supported until 2019, so that enterprises and home users who desire to remain on a stable release for a long time, can actually do so.

---

### Post by poorguy on 2016-05-09
Yeah Trusty Tahr 14.04 / 3.13 Kernel is rock solid.

One thing I've noticed about 16.04 it sure seems to use a lot of memory compared to 14.04.

---

### Post by kansasnoob on 2016-05-09
> **VTPoet said:**
> For what it's worth, I was having all sorts of problems with 16.04 until I reverted to an older kernel (4.2 instead of 4.4). I think there's a nasty regression in 4.4 having to do with Intel drivers. It messed all sorts of things up. Try an older kernel before you give up on 16.04.

But doing so results in running a kernel that will not receive all appropriate security updates! I sometimes use the [mainline kernels]("https://wiki.ubuntu.com/Kernel/MainlineBuilds#Does_the_kernel_team_support_the_mainline_kernel_builds.3F") for testing but it's important to read all warnings:

> Does the kernel team support the mainline kernel builds?

The mainline kernels builds are produced for debugging purposes and therefore come with no support. Use them at your own risk. 

---

