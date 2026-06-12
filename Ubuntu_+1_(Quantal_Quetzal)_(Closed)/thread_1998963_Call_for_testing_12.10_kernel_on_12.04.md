---
title: "Call for testing 12.10 kernel on 12.04"
date: 2012-06-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by balloons on 2012-06-07
For anyone still running precise (or wants to help), as you know the kernel team will be supporting newer kernels on the LTS release of ubuntu. As part of that, they need help in testing these newer kernels on the 12.04 release. SO, if you are running precise and want a newer kernel (or need it for hardware enablement) your in luck.

Also making a grand appearance is the a test build of the qatracker, with new features to support this type of testing. Please go check it out and leave feedback on it, etc. Does this make calls for testing easier for everyone?

[http://www.theorangenotebook.com/2012/06/call-for-testing-1210-kernel-on-1204.html](http://www.theorangenotebook.com/2012/06/call-for-testing-1210-kernel-on-1204.html)

---

### Post by jerrylamos on 2012-06-07
I've got an Ocelot partition which I could do a fresh install 12.04 Precise on for testing the 12.10 kernel.  Let me see if the install goes O.K.

Jerry

Up and running:

Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise
Linux version 3.4.0-4-generic (buildd@actinium) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #9~precise1-Ubuntu SMP Tue Jun 5 03:57:33 UTC 2012

Is that what's expected?

Do note I've a quantal on the same hard drive at 3.4.0.5-generic.  
Neither says "generic-pae".  I tried booting a quantal "generic" on a Pentium M and got a reject because of missing pae flag.

---

### Post by quids on 2012-06-08
I've already been using using Kernel 3.4 in 12.04 as my system was pretty much unusable with Kernel 3.2. I regularly suffered application crashes and the framerate from my nVidia GTX560TI was appalling.

Kernel upgrade and nVidia driver upgrade made it a completely different system.

Only  problem I've come across is that logging has to be disabled in UFW for the firewall to work properly at bootup.

---

### Post by kaldor on 2012-06-08
I've got a question about the kernel upgrades on the LTS. 

How will this affect stability of PC's, since it will be a regular update? Particularly proprietary driver users. I'm using the fglrx 12.x driver which is default in Precise and does not support kernels beyond 3.2.x. For me, it's not a huge problem (I can struggle well enough against fglrx), but what about the average users who don't understand what's going on? Will the upgrade to 3.4 mess with the users with fglrx installed? That's just one example, of course.

Just wondering how this will work without being painful.


> Does this make calls for testing easier for everyone?

Yep!

---

### Post by balloons on 2012-06-08
> **kaldor said:**
> I've got a question about the kernel upgrades on the LTS. 

How will this affect stability of PC's, since it will be a regular update? Particularly proprietary driver users. I'm using the fglrx 12.x driver which is default in Precise and does not support kernels beyond 3.2.x. For me, it's not a huge problem (I can struggle well enough against fglrx), but what about the average users who don't understand what's going on? Will the upgrade to 3.4 mess with the users with fglrx installed? That's just one example, of course.

Just wondering how this will work without being painful.

Yep!

Kaldor, part of the testing on this now is to get feedback like this. The kernel team is building this so that it will support proprietary driver users -- the net result is intended to be that everything stays the same or in the case of hardware enablement gets improved. Given the nature of the LTS release especially, regressions simply can't be an option. I'd encourage you to leave a comment on your submission about how the fglrx drivers work for you after upgrading; the kernel team will be reviewing the results. Of course, thanks for mentioning it here, I will try and bring it up as well.

PS - I love how you folks all think like this :-) Always on the lookout for corner cases or the not-so obvious. Should be interesting to see how it works out; glad your helping!

---

### Post by balloons on 2012-06-08
> **quids said:**
> I've already been using using Kernel 3.4 in 12.04 as my system was pretty much unusable with Kernel 3.2. I regularly suffered application crashes and the framerate from my nVidia GTX560TI was appalling.

Kernel upgrade and nVidia driver upgrade made it a completely different system.

Only  problem I've come across is that logging has to be disabled in UFW for the firewall to work properly at bootup.

Quids -- are you using the mainline kernel for this? Please do try the kernel from the ppa, and see if things work for you (including the ufw problem your mentioning). If problems persist, file that bug :-) E their way, submit a pass/fail -- it helps. Thanks!

---

### Post by fjgaude on 2012-06-08
My system was stable, Suspend, Resume, etc., on all recent kernels, the box is Intel graphic based. Notice this post:

[http://ubuntuforums.org/showthread.php?p=12009969#post12009969](http://ubuntuforums.org/showthread.php?p=12009969#post12009969)

Do believe the latest kernel provides even better Intel speed. Notice the low gtkperf score!

---

### Post by kaldor on 2012-06-08
> **fjgaude said:**
> My system was stable, Suspend, Resume, etc., on all recent kernels, the box is Intel graphic based. Notice this post:

[http://ubuntuforums.org/showthread.php?p=12009969#post12009969](http://ubuntuforums.org/showthread.php?p=12009969#post12009969)

Do believe the latest kernel provides even better Intel speed. Notice the low gtkperf score!

Intel graphics tend to improve bit by bit every kernel release. Not surprised :)

Even Ivy Bridge had day 0 support, and works better than Sandy Bridge.

---

### Post by quids on 2012-06-08
> **guitara said:**
> Quids -- are you using the mainline kernel for this? Please do try the kernel from the ppa, and see if things work for you (including the ufw problem your mentioning). If problems persist, file that bug :-) E their way, submit a pass/fail -- it helps. Thanks!

Guitara - Yes I was using the Mainline kernel.
Sure thing I'll give the PPA version a go

---

### Post by quids on 2012-06-08
I just did a real quick test with a Virtualbox guest of Ubuntu 12.04 that had UFW installed.
Interestingly the Quantal Kernel didn't cause any issues with the Firewall starting up.

Perhaps it was some other problem with my system unrelated to the kernel. 

How long will the PPA be around for? 
Is it safe to run my system on it, or should I do the tests and then go back to manually checking the Mainline repo for new kernel updates?

---

### Post by fjgaude on 2012-06-09
> **kaldor said:**
> Intel graphics tend to improve bit by bit every kernel release. Not surprised :)

Even Ivy Bridge had day 0 support, and works better than Sandy Bridge.

Interesting that Intel works with Linux so closely, at least with graphics: trying to rule the day against AMD and nvidia?

---

### Post by jerrylamos on 2012-06-09
Installed the 12.10 kernel.  Runs O.K.  

Now will updates to 12.04 update it too?  Doesn't seem to since my quantals are at 3.4.0-5 and the precise is stall at 3.4.0-4 after updating.

Jerry

---

### Post by balloons on 2012-06-11
> **jerrylamos said:**
> Installed the 12.10 kernel.  Runs O.K.  

Now will updates to 12.04 update it too?  Doesn't seem to since my quantals are at 3.4.0-5 and the precise is stall at 3.4.0-4 after updating.

Jerry

Jerry, thanks for trying it out ;-) Feel free to add your results to the results page -- just need to login with your ubuntu sso and you should be good to go:

[http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16265/testcases/1301/results](http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16265/testcases/1301/results)

The ppa will be updated by the kernel team as the cycle progresses (I'm not sure of the schedule persay), but it will be much more static than the new quantal kernels.

---

### Post by jinjorge on 2012-06-12
is there a need for testing 3.5 kernel on 12.04?

Currently running 3.5.0-030500rc1-generic #201206022335 SMP Sun Jun 3 03:36:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

J

---

### Post by pbhedlund on 2012-06-13
Kernels 3.2 (Precise) and 3.4 (Quantal) have a bug in nouveau that makes them unusable on Nvidia 320M graphics adapters. Kernels 3.3 and 3.5 are not affected. See [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/898784](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/898784) and linked bug reports.

I think it would be unfortunate if this bug gets to persist in an LTS release.

---

### Post by balloons on 2012-06-13
> **pbhedlund said:**
> Kernels 3.2 (Precise) and 3.4 (Quantal) have a bug in nouveau that makes them unusable on Nvidia 320M graphics adapters. Kernels 3.3 and 3.5 are not affected. See [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/898784](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/898784) and linked bug reports.

I think it would be unfortunate if this bug gets to persist in an LTS release.

This is exactly the type of thing we hope to uncover in testing! Can you run the test and confirm the quantal kernel for precise from the ppa fails to work with nvidia 320m running nouveau? If so, file the result as failed and link your bug, explaining 3.3 and 3.5 don't have the issue. Since it's been fixed upstream, this should be fixable. Thanks!

---

### Post by balloons on 2012-06-13
> **jinjorge said:**
> is there a need for testing 3.5 kernel on 12.04?

Currently running 3.5.0-030500rc1-generic #201206022335 SMP Sun Jun 3 03:36:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

J

Is that from mainline or source? Regardless, this testing is for specific builds of the newer kernel to precise. The package in this ppa isn't vanilla upstream, as it has the ubuntu patchset and backports in it like a "normal" ubuntu kernel. As an LTS, we want to be careful about updating something like the kernel -- no regressions, while at the same time giving precise a long enablement lifespan for new hardware and improved support. After 3.5 releases and quantal moves to it, it's likely the quantal kernel for precise will be updated to 3.5.

---

### Post by jerrylamos on 2012-06-13
> **guitara said:**
> ...while at the same time giving precise a long enablement lifespan for new hardware and improved support. After 3.5 releases and quantal moves to it, it's likely the quantal kernel for precise will be updated to 3.5.Do note I'm running on a Pentium M here which has no pae flag.  It's upgraded to quantal as far as it can with some packages not installing, in particular ubuntu quantal kernel so far is pae only.

Now I do have later pc's which will run newer software, do note quantal FGLRX is busted on my wide screen notebook. CLI XRANDR will sort of get it limping.

Usually I drop off a pc when it gets too slow with the added overhead.  So far this one's running fine, internet video et. al. precise lubuntu very well, quantal ubuntu except for some packages that won't install like the kernel.

So at what point does precise LTS start dropping off support for hardware that now happily runs on it?

Thanks, Jerry

---

### Post by philinux on 2012-06-13
I can give this a go tomoz. When does the testing finish?

---

### Post by balloons on 2012-06-13
> **jerrylamos said:**
> Do note I'm running on a Pentium M here which has no pae flag.  It's upgraded to quantal as far as it can with some packages not installing, in particular ubuntu quantal kernel so far is pae only.

Now I do have later pc's which will run newer software, do note quantal FGLRX is busted on my wide screen notebook. CLI XRANDR will sort of get it limping.

Usually I drop off a pc when it gets too slow with the added overhead.  So far this one's running fine, internet video et. al. precise lubuntu very well, quantal ubuntu except for some packages that won't install like the kernel.

So at what point does precise LTS start dropping off support for hardware that now happily runs on it?

Thanks, Jerry

Jerry, the tech board decided to drop support for non-pae as of the 12.10 release. There are no plans to offer a non-pae kernel for quantal or any future releases. The quantal kernel upgrade for the precise LTS has a pre-install check that will determine if your hardware is PAE capable or not. The same check is in place for quantal (which is why you didn't get a quantal kernel). So you won't be prompted to install a non-compatible kernel. The non-pae kernel in precise will be supported for 5 years with security and bug fix updates; same as any other supported kernel flavor on precise.

I also have an old pentium M laptop, but it died, so I kind of squeezed out of this issue. However I do run a custom kernel which is a bit old now on a netbook simply because it works perfectly, so there is no reason to upgrade it. I've run 10.04, 11.04, 11.10 and 12.04 all fine using it. So it's not the end of the world persay, beyond security and bugfix updates. For that you could keep the precise archives around and update your kernel via them if you want to run quantal and beyond.

Does that make sense?

---

### Post by balloons on 2012-06-13
> **philinux said:**
> I can give this a go tomoz. When does the testing finish?

This testing will occur until it's released to precise, so it's going to be awhile. I was just thinking about this and realized given the much longer timeframe on this, there might be a couple points (like now, and just before it goes into precise) where I ask for more focused testing on it to ensure we've caught bugs. In the interim, it will revert to more ad-hoc testing as and when you can through the cycle. I mean, leaving the ppa installed and reporting the results as it updates (in case it ever breaks) I think would be a nice way to do that that's low key.

---

### Post by philinux on 2012-06-13
> **guitara said:**
> This testing will occur until it's released to precise, so it's going to be awhile. I was just thinking about this and realized given the much longer timeframe on this, there might be a couple points (like now, and just before it goes into precise) where I ask for more focused testing on it to ensure we've caught bugs. In the interim, it will revert to more ad-hoc testing as and when you can through the cycle. I mean, leaving the ppa installed and reporting the results as it updates (in case it ever breaks) I think would be a nice way to do that that's low key.

nVidia 8600GT

This > > Loading new nvidia-current-295.40 DKMS files...
First Installation: checking all kernels...
Building only for 3.4.0-4-generic
Building for architecture x86_64
Building initial module for 3.4.0-4-generic
ERROR (dkms apport): kernel package linux-headers-3.4.0-4-generic is not supported
Error! Bad return status for module build on kernel: 3.4.0-4-generic (x86_64)
Consult /var/lib/dkms/nvidia-current/295.40/build/make.log for more information.

I got unity 2d. I'll post this info to the qa tracker later. Bed time

Otherwise running ok.

[edit] ok submitted report as passed but should it be In Progress as driver failed to build.
/var/lib/dkms/nvidia-current/295.40/build/make.log attached

[edit 2] nvidia-current purged and 3d unity working with nouveau driver.

---

### Post by balloons on 2012-06-14
> **philinux said:**
> nVidia 8600GT

This > 

I got unity 2d. I'll post this info to the qa tracker later. Bed time

Otherwise running ok.

[edit] ok submitted report as passed but should it be In Progress as driver failed to build.
/var/lib/dkms/nvidia-current/295.40/build/make.log attached

[edit 2] nvidia-current purged and 3d unity working with nouveau driver.

Feel free to file a bug on the nvidia driver failing, even though it's running with the nouveau driver. You should be able to edit your result so the bug gets linked in (it's helpful for me to keep track that way :-) ) Thanks for reporting!!

---

### Post by philinux on 2012-06-14
> **guitara said:**
> Feel free to file a bug on the nvidia driver failing, even though it's running with the nouveau driver. You should be able to edit your result so the bug gets linked in (it's helpful for me to keep track that way :-) ) Thanks for reporting!!

Ah. But surely there is no suitable nvidia current for this kernel in 12.04 so is it technically a bug.

---

### Post by pbhedlund on 2012-06-14
> **guitara said:**
> This is exactly the type of thing we hope to uncover in testing! Can you run the test and confirm the quantal kernel for precise from the ppa fails to work with nvidia 320m running nouveau? If so, file the result as failed and link your bug, explaining 3.3 and 3.5 don't have the issue. Since it's been fixed upstream, this should be fixable. Thanks!

Done!

---

### Post by balloons on 2012-06-15
> **philinux said:**
> Ah. But surely there is no suitable nvidia current for this kernel in 12.04 so is it technically a bug.

mmm.. When this is offered as an upgrade, it needs to just work. If it doesn't, I consider it a bug :-) You might be right, and the kernel team might have it on there radar, but I consider it a bug in this context :-)

---

### Post by philinux on 2012-06-15
> **guitara said:**
> mmm.. When this is offered as an upgrade, it needs to just work. If it doesn't, I consider it a bug :-) You might be right, and the kernel team might have it on there radar, but I consider it a bug in this context :-)

Ok I'll ubuntu-bug linux when I get back on.

---

### Post by kaldor on 2012-06-15
The fglrx and NVIDIA drivers should just be refreshed every few months. It shouldn't be up to the user to discover that a kernel update will require them to get a new driver.

What are the plans for this? Maybe every point release or something?

Apologies if I've missed anything :P

---

### Post by jinjorge on 2012-06-15
> **guitara said:**
> Is that from mainline or source? Regardless, this testing is for specific builds of the newer kernel to precise. The package in this ppa isn't vanilla upstream, as it has the ubuntu patchset and backports in it like a "normal" ubuntu kernel. As an LTS, we want to be careful about updating something like the kernel -- no regressions, while at the same time giving precise a long enablement lifespan for new hardware and improved support. After 3.5 releases and quantal moves to it, it's likely the quantal kernel for precise will be updated to 3.5.

Thanks for the response. The reason I asked is I was doing some upstream testing of the 3.5 kernel running on 12.04 to see if I could repro a kernel panic bug.

As to your question on where I got this kernel, here are the notes in the bug should shed some light

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1006171/comments/30](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1006171/comments/30)

J

---

### Post by jerrylamos on 2012-06-15
> **kaldor said:**
> The fglrx and NVIDIA drivers should just be refreshed every few months. It shouldn't be up to the user to discover that a kernel update will require them to get a new driver.

What are the plans for this? Maybe every point release or something?

Apologies if I've missed anything :P
Display driver driving me nuts on my newest wide screen notebook - something about fglrx I gather.  systems settings, display, appy bombs out bug #1007588:

GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `org.gnome.SettingsDaemon.XRANDR_2' on object at path /org/gnome/SettingsDaemon/XRANDR 

Only way I've been able get partial recovery is with CLI xrandr to set screen resolution.  And of course it gets nowhere on systems settings, additional drivers.  Launchpad is doing some work on the bug example it helps a little bit to turn the touchpad on.  

I touch type and touchpads drive me nuts since my hands are all over the keyboard and forever getting wierd stuff from the touchpad.  So now I'm using an external keyboard to avoid bumping the touchpad.

Jerry

---

### Post by mc4man on 2012-06-16
> **philinux said:**
> Ok I'll ubuntu-bug linux when I get back on.

Did you file a bug on that yet? Should be this bug so I guess the ppa wasn't aware of ??
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/993506](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/993506)

What should also be noted is that more than an insignificant amount of users will have issues with nvidia drivers over 290.XX,  so some consideration should be given to fixing that package also for 3.4 kernel

While somewhat irrelevant you can use 12.10's nvidia-current with the ppa kernel in 12.04

Edit: while it's likely that if 3.4 makes it into 12.04 they may decide to just offer up 295.53+ I'm sure they are many that could benefit from both 3.4 & 290.10 nvidia. While it's not quite as straightforward a source edit as seen in bug report it is quite doable & really should be considered, if only  just ppa'd rather than official

The give back by using 290 is the recent cve vulnerability but there always will be one or another, that's up to the user who may prefer 12.04 usability over remote chance

> Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current ...
Setting up nvidia-current (290.10-0ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-290.10 DKMS files...
Building for architecture i686
Building initial module for 3.4.0-5-generic
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.4.0-5-generic/updates/dkms/

depmod....

DKMS: install completed.

---

### Post by philinux on 2012-06-16
I bugged it anyway. They can always dup it of course.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1014091](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1014091)

[edit] for got to say the ubuntu-bug linux failed.
> The problem cannot be reported:

This is not an official Ubuntu package. Please remove any third party package and try again.


---

### Post by grahammechanical on 2012-06-16
Can I add a little bit regarding the Nvidia driver issue?

The 3.4.0-4 kernel on Precise gave me Nouveau + Unity 2D and Additional drivers could not activate the Nvidia driver.

When I tried to activate the Nvidia driver on one of my Quantal installs (3.4.0-1 kernel) it too was unable to activate the Nvidia driver.

On Precise + 3.2 kernel the Nidia driver is 295.40 on a GT220 and it works fine.

On Quantal + 3.4.0-1 kernel + Nouveau = Unity 3D.

So, I suggest there are two issues here.

1) There are still problems with the Nvidia drivers.
2) Nouveau needs to give 3D in Precise like it does in Quantal. Then issues with updating the precise kernel to 3.4.0-4 and defaulting to Nouveau will not be so noticeable. 

Regards.

---

### Post by Yellow Pasque on 2012-06-16
> **philinux said:**
> I bugged it anyway. They can always dup it of course.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1014091](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1014091)

I dup'd your bug. Here's the main report: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/993506](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/993506)

Basically, the version of the nvidia driver (295.40) found in Precise/12.04  doesn't work with kernel 3.4, so you have to install a newer version (x-swat ppa makes it easy: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) ).

---

### Post by philinux on 2012-06-16
> **Temüjin said:**
> I dup'd your bug. Here's the main report: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/993506](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/993506)

Basically, the version of the nvidia driver (295.40) found in Precise/12.04  doesn't work with kernel 3.4, so you have to install a newer version (x-swat ppa makes it easy: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) ).

Ok that's fine but I'm not using another ppa. This needs to be fixed for general 12.04 users. Me I'll stick with nouveau until its fixed. Like maybe backport a new driver or SRU update.

---

### Post by Yellow Pasque on 2012-06-16
> **philinux said:**
> Ok that's fine but I'm not using another ppa. This needs to be fixed for general 12.04 users. Me I'll stick with nouveau until its fixed. Like maybe backport a new driver or SRU update.
Hmm. I think that's what nvidia-current-updates is for.

---

### Post by unibroker on 2012-06-16
On installation I get the follow error message:  ```
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-x-swat-q-lts-backport-precise.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
```

Any ideas?

---

### Post by mc4man on 2012-06-16
> **unibroker said:**
> On installation I get the follow error message:  ```
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-x-swat-q-lts-backport-precise.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
```

Any ideas?open that file in a root text editor & fix, sounds like "main" got broken to a 3rd line

Current file here - 
```
deb http://ppa.launchpad.net/ubuntu-x-swat/q-lts-backport/ubuntu precise main
deb-src http://ppa.launchpad.net/ubuntu-x-swat/q-lts-backport/ubuntu precise main


```

---

### Post by unibroker on 2012-06-16
> **mc4man said:**
> open that file in a root text editor & fix, sounds like "main" got broken to a 3rd line

Current file here - 
```
deb http://ppa.launchpad.net/ubuntu-x-swat/q-lts-backport/ubuntu precise main
deb-src http://ppa.launchpad.net/ubuntu-x-swat/q-lts-backport/ubuntu precise main


```

Thanks!  For some reason "ain" got added to a 3rd line.

---

### Post by scradock on 2012-06-16
I'm currently running the QQ 3.5.0-030500rc2 kernel in 12.04 LTS. Seems to work fine except that virtualbox won't start because dkms doesn't know about 3.5 kernel... But that's true in QQuetzal as well.

HTH

---

### Post by philinux on 2012-06-17
> **Temüjin said:**
> Hmm. I think that's what nvidia-current-updates is for.

Yes. But if we are dropping this kernel on unsuspecting 12.04 nVidia users it has to work out of the box. I suspect most will have gone with the Recommended Driver.

---

### Post by jan-banan on 2012-06-17
If i want to try the new kernel but not risk the stability of my current system, is it still safe to install this kernel? Will it mess with my current kernel?

---

### Post by dino99 on 2012-06-17
> **jan-banan said:**
> If i want to try the new kernel but not risk the stability of my current system, is it still safe to install this kernel? Will it mess with my current kernel?

if you does not uninstall the previous good kernel, then you still can boot on it if the testing one is not good enough

---

### Post by dino99 on 2012-06-17
Hopes that Quantal kernel will be quickly 3.5 rc3 & up, because it is better than the 3.4 serie

---

### Post by fjgaude on 2012-06-17
I'm running kernel 3.5rc3 and 12.04 on my main box. Works extremely well, a little faster than kernel 3.2 or 3.4. So... I'll keep using it.

Seems most of the issues people have with new kernels is the video drivers for ATI and nvidia boards. Mine is Intel, solid.

---

### Post by DingusFett on 2012-06-18
I have had issue with my resolution on an Nvidia card since upgrading, as per this thread:
[http://ubuntuforums.org/showthread.php?t=2005140](http://ubuntuforums.org/showthread.php?t=2005140)

Even though I have gone back to previous kernel, the problem persists, even in my Windows partition. Does anybody think giving 3.5 a try would help this out? I'm still quite new to linux, but figured I'd give 3.4 a test, and no really regretting it.

---

### Post by jfernyhough on 2012-06-20
Just as a note the backport testing kernel has been updated to 3.5.0-1.1. Nvidia seems to be working OK with 302.17-0ubuntu1~precise~xup1 from x-swat. VirtualBox kernel module failed to build (but then I don't use it much on my 311c ;))

---

### Post by SpaceCeph on 2012-06-20
Tz, I updated too, but nothing works fine. My mouse doesn't work and I can't set the resolution like it was before.

Edit: No wlan, no lan, terrible resolution... Not the best update for me.
In QQ there was the same kernel update today, no problems.

---

### Post by balloons on 2012-06-21
> **SpaceCeph said:**
> Tz, I updated too, but nothing works fine. My mouse doesn't work and I can't set the resolution like it was before.

Edit: No wlan, no lan, terrible resolution... Not the best update for me.
In QQ there was the same kernel update today, no problems.

Most interesting SpaceCeph! Same hardware, same kernel, different OS and things work in one but not the other. I'd love to see the report on that and what hardware/drivers your using.

---

### Post by dino99 on 2012-06-21
Confirm this newest 3.5.1-1 a must have one: works way better than 3.4 serie, for example the ram footprint is far lower, the fans are running slower, less noisy, due to the huge acpi rework done.

I also have the mouse issue, but to my experience it is not related to this latest kernel, 3.4 is having too.
 For example when playing aisleriot card game, grabbing a card is very hard after a while, then dragging often lost the card; so it seems to be  more related to bad memory dealing or pointers not refreshed. Have tried many tweakings from mouse system settings, but nothing works  with quantal, but precise works normally.

---

### Post by philinux on 2012-06-21
I just tried installing nvidia-current-updates:
  Candidate: 295.49-0ubuntu0.1

This also fails to build with this kernel. With the same errors as 295.40

```
Building initial module for 3.4.0-4-generic
ERROR (dkms apport): kernel package linux-headers-3.4.0-4-generic is not supported
Error! Bad return status for module build on kernel: 3.4.0-4-generic (x86_64)
```

---

### Post by dino99 on 2012-06-21
> **philinux said:**
> I just tried installing nvidia-current-updates:
  Candidate: 295.49-0ubuntu0.1

This also fails to build with this kernel. With the same errors as 295.40

```
Building initial module for 3.4.0-4-generic
ERROR (dkms apport): kernel package linux-headers-3.4.0-4-generic is not supported
Error! Bad return status for module build on kernel: 3.4.0-4-generic (x86_64)
```

on i386 i does not get trouble with 302.xx driver and xorg 1.12 abi (from edgers)

---

### Post by philinux on 2012-06-21
> **jfernyhough said:**
> Just as a note the backport testing kernel has been updated to 3.5.0-1.1. Nvidia seems to be working OK with 302.17-0ubuntu1~precise~xup1 from x-swat. VirtualBox kernel module failed to build (but then I don't use it much on my 311c ;))

Is there a smoke test results set up for this? I'm just updating and off for a reboot.

---

### Post by balloons on 2012-06-21
> **philinux said:**
> Is there a smoke test results set up for this? I'm just updating and off for a reboot.

Yes, there's a new build (just like the isotracker) with the old results archived and saved, and a new blank slate ready to report against the new build:

[http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16283/testcases/1301/results](http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16283/testcases/1301/results)

PS -- I need to / will be migrating this to the prod tracker soon ;-) I'll let everyone know when it happens of course.

EDIT: I should say, this should be automated, but is currently manual. Hence, thanks for reminding me!

---

### Post by philinux on 2012-06-21
> **guitara said:**
> Yes, there's a new build (just like the isotracker) with the old results archived and saved, and a new blank slate ready to report against the new build:

[http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16283/testcases/1301/results](http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16283/testcases/1301/results)

PS -- I need to / will be migrating this to the prod tracker soon ;-) I'll let everyone know when it happens of course.

EDIT: I should say, this should be automated, but is currently manual. Hence, thanks for reminding me!

I purged the ppa after testing. So I'll start again. However one thing is wrong. The uninstall command is incorrect.
[http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16265/downloads](http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16265/downloads)
> sudo apt-get remove --purge linux-image-generic-lts-quantal linux-headers-generic-lts-quantal linux-image-3.5.0.1.5-generic linux-headers-3.5.0.1.5-generic


The packages installing are these linux-headers-3.5.0-1 linux-headers-3.5.0-1-generic linux-headers-generic-lts-quantal
  linux-image-3.5.0-1-generic linux-image-generic-lts-quantal

---

### Post by balloons on 2012-06-21
> **philinux said:**
> I purged the ppa after testing. So I'll start again. However one thing is wrong. The uninstall command is incorrect.
[http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16265/downloads](http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16265/downloads)


The packages installing are these linux-headers-3.5.0-1 linux-headers-3.5.0-1-generic linux-headers-generic-lts-quantal
  linux-image-3.5.0-1-generic linux-image-generic-lts-quantal

Thank you again! Gotta keep this balloons guy in line!

---

### Post by balloons on 2012-07-03
So I updated the old post with some new info -- I've gotten some specific hardware the kernel team wants to ensure things work properly for. Check out the new wiki page: [https://wiki.ubuntu.com/Testing/Kernel](https://wiki.ubuntu.com/Testing/Kernel). If possible go ahead and put your name down next to the hardware bits you have.

This is all of course the precursor to us getting a proper hardware db. I know I sound like a broken record, but fingers crossed, should be up and running during this cycle. I would love everyone's feedback on the format and ease of use for this. I want to make this easier for everyone to use and see what's going on. Ohh, and yea, it should be more fun also :-)

---

### Post by balloons on 2012-07-10
Just a bump to thank all of you who put your info on this page! We've got full coverage on graphics drivers - wahoo! However, if you happen to have something on the list that's not yet covered, or perhaps only covered by one other person, consider adding yourself to this page and testing.

[https://wiki.ubuntu.com/Testing/Kernel](https://wiki.ubuntu.com/Testing/Kernel)

---

