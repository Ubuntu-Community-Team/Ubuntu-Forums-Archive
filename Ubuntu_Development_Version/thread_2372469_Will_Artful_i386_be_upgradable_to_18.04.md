---
title: "Will Artful i386 be upgradable to 18.04?"
date: 2017-09-25
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2017-09-25
I have a rather odd but serious question. AFAIK i386 images will no longer be available beginning with 18.04, but there was some vague mention of older i386 operating systems being upgradeable to 18.04, so that leads me to think 16.04 i386 -> 18.04 i386 or 17.10 i386 ->  18.04 i386 may be possible. Does anyone here have any insider info regarding this? The last useful info I found regarding this dates back to June 2016:

[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-June/016675.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-June/016675.html)

There is a bit more uninformative discussion the following month and then nothing at all :(

My specific reason for wanting to find out is an effort at reviving some Intel Atom 230 machines which run much, much better on i386 than they do on amd64. I've even tried bumping the RAM up from 2GB to 3GB (in some cases actually 4GB but only about 3200MB is usable due to hardware/BIOS limitations). Even with something as light as Bodhi performance stinks in the standard version but improves greatly with their legacy version.

I've tried both the i386 and amd64 versions of Xenial and Artful, and the i386 versions absolutely perform much, much better - equally so with Xenial and Artful. The amd64 versions are really almost unusable due to high CPU usage while the RAM usage remains very low - seems odd I know but RAM usage increases while CPU usage decreases using the i386 version.

Regarding desktop environments the only noticeable difference in performance between Flashback w/metacity, Mate, Lubuntu, Xubuntu and Enlightenment is file management where PCManFM is the clear winner, but all perform well enough with only 2GB of RAM to provide a wide variety of choices. If Artful i386 is upgradeable to 18.04 i386 that would be my clear choice even if the i386 kernel received limited security updates, otherwise I'd go with Xenial and set them to never release-upgrade.

Sorry to ramble but I was in hopes someone here may know what actual decision has been made. Or maybe it's just too soon to know?????????

Oops - almost left something out! A light browser is an absolute MUST with these Atom 230's! Forget about either Firefox or Chrome! I'm leaning heavily toward Pale Moon but Midori also works quite well. And I may as well mention that I've even tried both the 32 and 64 bit versions of Windows 10 on one of these boxes with the same results. While these Atom 230's are 64 bit capable I'd describe them as "64 bit unusable" - think dial-up slow (with many freezes)!

---

### Post by cariboo on 2017-09-25
If I remember correctly, there won't be a 386 iso, but the packages will still be in the repository, so it should be possible to upgrade to 18.04 on an i386 system.

---

### Post by deadflowr on 2017-09-25
> I'm leaning heavily toward Pale Moon but Midori also works quite well.
Sad news then:
[https://ubuntuforums.org/showthread.php?t=2371648]("https://ubuntuforums.org/showthread.php?t=2371648")

---

### Post by ventrical on 2017-09-25
@kansasnoob,

I sent mail to devs to see whats up. if I get answer I'll post it.

Regards..

---

### Post by kansasnoob on 2017-09-25
> **deadflowr said:**
> Sad news then:
[https://ubuntuforums.org/showthread.php?t=2371648]("https://ubuntuforums.org/showthread.php?t=2371648")

I'd only tried it in Bodhi so far. Pale Moon is NOT easy to install:

[https://linux.palemoon.org/download/installer/](https://linux.palemoon.org/download/installer/)

Not horribly hard but I'm lazy :D

---

### Post by kansasnoob on 2017-09-25
> **ventrical said:**
> @kansasnoob,

I sent mail to devs to see whats up. if I get answer I'll post it.

Regards..

Cool, thanks :D

---

### Post by cariboo on 2017-09-27
This just popped up on the Ubuntu-dev mailing list:

[https://lists.ubuntu.com/archives/ubuntu-devel/2017-September/039999.html](https://lists.ubuntu.com/archives/ubuntu-devel/2017-September/039999.html)

---

### Post by kansasnoob on 2017-09-27
They posted the answer on ubuntu-release. First [from Dimitri John Ledkov]("https://lists.ubuntu.com/archives/ubuntu-release/2017-September/004212.html"):

> Dear Release team,

Please action the below and remove Ubuntu Desktop i386 daily-live
images from the release manifest for Beta and Final milestones of
17.10 and therefore do not ship ubuntu-desktop-i386.iso artifact for
17.10.

As a followup to this thread it has been confirmed that argumentation
below is sound, and furthermore there is no longer any effective qa or
testing of the desktop product on actual i386 hardware (explicitly non
x86_64 CPUs).

There are no other changes requested to d-i, mini.iso, archive, or the
upgrade paths.


And then [followed up by Iain Lane]("https://lists.ubuntu.com/archives/ubuntu-release/2017-September/004213.html"):

> Done. What this means is that [B]Ubuntu desktop is not releasing i386 with
the final beta, and we won't build i386 ISOs any more.

Other flavours are unaffected and, as xnox said, existing installations
that are on i386 on a previous release will be able to upgrade to 17.10
and 18.04 when they are released and they'll continue to be supported as
normal[/B].

So it will be possible to upgrade i386 versions of either 16.04 or 17.10 (probably even 16.10 or 17.04 under certain circumstances) to 18.04 i386. And it'll be up to each flavor as to whether or not they'll continue building i386 images. I suspect at least Ubuntu MATE, Xubuntu, and Lubuntu will do so.

---

### Post by ventrical on 2017-09-27
Thanks Cariboo

> 
[I]and furthermore there is no longer any effective qa or
[/I]>[I] testing of the desktop product on actual i386 hardware (explicitly non
[/I]>[I] x86_64 CPUs).


thats basically what killed it..

[/I]

---

### Post by kansasnoob on 2017-09-27
> **cariboo said:**
> This just popped up on the Ubuntu-dev mailing list:

[https://lists.ubuntu.com/archives/ubuntu-devel/2017-September/039999.html](https://lists.ubuntu.com/archives/ubuntu-devel/2017-September/039999.html)

You beat me to it :D

---

### Post by mörgæs on 2017-10-01
So the 17.10 and 18.04 repositories will contain a complete selection of 32 bit packages.

Does this mean that one can still install the 32 bit minimal ISO and add the GUI using ```
sudo apt install ubuntu-desktop
```?

---

### Post by cariboo on 2017-10-01
As far as I can see, there are no plans for any 32-bit iso of any sort, upgrade is the only path.

---

### Post by kansasnoob on 2017-10-01
> **mörgæs said:**
> So the 17.10 and 18.04 repositories will contain a complete selection of 32 bit packages.

Does this mean that one can still install the 32 bit minimal ISO and add the GUI using ```
sudo apt install ubuntu-desktop
```?

I think the mini.iso is safe:

[https://lists.ubuntu.com/archives/ubuntu-release/2017-September/004212.html](https://lists.ubuntu.com/archives/ubuntu-release/2017-September/004212.html)

> Dear Release team,

Please action the below and remove Ubuntu Desktop i386 daily-live
images from the release manifest for Beta and Final milestones of
17.10 and therefore do not ship ubuntu-desktop-i386.iso artifact for
17.10.

As a followup to this thread it has been confirmed that argumentation
below is sound, and furthermore there is no longer any effective qa or
testing of the desktop product on actual i386 hardware (explicitly non
x86_64 CPUs).

[B]There are no other changes requested to d-i, mini.iso, archive, or the
upgrade paths.
[/B]
Regards,

Dimitri.

---

### Post by mörgæs on 2017-10-01
With a minimal ISO and a full repository it should be possible to do a fresh install of 17.10, 32 bit. Still I have only seen links talking about upgrading to 17.10. 

What am I missing here?

---

### Post by kansasnoob on 2017-10-02
> **mörgæs said:**
> With a minimal ISO and a full repository it should be possible to do a fresh install of 17.10, 32 bit. Still I have only seen links talking about upgrading to 17.10. 

What am I missing here?

I'd specifically asked about upgrades because that most concerned me at the time, but the facts are summed up in the two links I posted here:

[https://ubuntuforums.org/showthread.php?t=2372469&p=13691051#post13691051](https://ubuntuforums.org/showthread.php?t=2372469&p=13691051#post13691051)

It really just boils down to only the ubuntu-desktop-i386.iso being eliminated. Everything else stays the same for the foreseeable future. I'd expect to see some further deprecation of 32 bit OS's in the future but no idea how soon that may be. I'm fairly certain that it will be possible to upgrade either 16.04 or 17.10 to 18.04 and get the full five years of kernel support which would take the effected hardware all the way through April 2023.

Hmmm, I see they seem to have restarted the cron job for the i386 images:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

It had previously stopped at 20170926 I think :confused:

---

### Post by Chanath on 2017-10-02
> **kansasnoob said:**
> I'd specifically asked about upgrades because that most concerned me at the time, but the facts are summed up in the two links I posted here:

[https://ubuntuforums.org/showthread.php?t=2372469&p=13691051#post13691051](https://ubuntuforums.org/showthread.php?t=2372469&p=13691051#post13691051)

It really just boils down to only the ubuntu-desktop-i386.iso being eliminated. Everything else stays the same for the foreseeable future. I'd expect to see some further deprecation of 32 bit OS's in the future but no idea how soon that may be. I'm fairly certain that it will be possible to upgrade either 16.04 or 17.10 to 18.04 and get the full five years of kernel support which would take the effected hardware all the way through April 2023.

Hmmm, I see they seem to have restarted the cron job for the i386 images:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

It had previously stopped at 20170926 I think :confused:

It appears that only the Gnome devs can't keep/maintain the i386 setup, while all other can. Maybe, too much problem of keeping/maintaining "system extensions" two platforms.

---

### Post by cariboo on 2017-10-02
There are many 32-bit systems still being produced as part of the IOT. I'm working on a home automation project using [home assistant]("https://home-assistant.io/"), even though I'm running Debian, there are many users running Ubuntu, almost all the devices used are 32-bit.

---

### Post by jbicha on 2017-10-02
> **Chanath said:**
> It appears that only the Gnome devs can't keep/maintain the i386 setup, while all other can. Maybe, too much problem of keeping/maintaining "system extensions" two platforms.

The problem is that Canonical commits to supporting the official Ubuntu LTS flavor for 5 years. There is a high probably that Firefox and Chromium will not be easily buildable on 32-bit systems sometime soon. Google already officially does not support 32-bit for Chrome.

Another popular app that dropped 32-bit support is darktable.

There are security benefits to using amd64. There are performance benefits. There is benefit to using the same architecture that all of the developers and the vast majority of users use.

And Ubuntu is not the only (or even first) distro dropping 32-bit support.

---

### Post by mörgæs on 2017-10-02
There are also benefits to using 32 bit, for example privacy. Some people prefer hardware from a time before spyware was baked into the motherboard and some people don't have access to the luxury of buying 64 bit processor power. They might not post here but their needs are not less important.

---

### Post by ventrical on 2017-10-04
@all

Nothing you didn't already know.



> 

                     [SIZE=2]Hey Dale,
 
 There is not going to be an Ubuntu Desktop i386 iso starting this cycle
 (the change is active now)
 
 Cheers,
 Sebastien Bacher


Regards..
[/SIZE]

---

