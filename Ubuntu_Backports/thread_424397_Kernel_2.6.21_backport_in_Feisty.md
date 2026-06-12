---
title: "Kernel 2.6.21 backport in Feisty"
date: 2007-04-26
forum: Ubuntu Backports
---

### Post by alfredio on 2007-04-26
Hi backport people,
I'd like to see the 2.6.21 kernel backported in Feisty.

I know it is rather new software, however, I think there will be many users that will benefit from a 2.6.21 kernel. Indeed, the last version of the kernel includes the 1.0.14rc3 audio driver from alsa, which supports many recent motherboards (from sept 2006 until now, like the Asus M2N-MX, which has been discussed a lot for support on the ubuntu forums). In other words, having the 2.6.21 kernel in Feisty would be the "official" and, most of all, clean solution to many of the hardware problems affecting Ubuntu user that have relatively new hardware.

I already successfully compiled, packaged (with the Ubuntu/Debian way) and ran the 2.6.21 kernel, however I had problem with restricted-drivers, because they are handled differently from the standard Debian way. I also saw that git.kernel.org contains an ubuntu branch for the 2.6.21 kernel, so this may help you a lot. 

I hope you can lend an hand to users like me that like to see their hardware supported.
(Another solution may be some documentation, or a complete tutorial, on how to generate a custom linux-restricted-module package the Ubuntu way, just like it is possible now to generate a custom kernel package the Ubuntu/Debian way).

Thank you very much for your support.

---

### Post by nicolas2b on 2007-04-27
Yes, it can be wonderful if it's in the feistybackport

---

### Post by justinchudgar on 2007-04-29
I would also like to see 2.6.21 as it contains the sensor modules necessary for my mobo. Since I have an Atheros NIC as LAN connection, having restricted-modules is critical for me. If anyone can direct me on how to compile 2.6.21 with the restricted modules, it would be greatly appreciated. Google has not guided me so far.

---

### Post by jhewer on 2007-04-30
I'd also love to see this, since CPU scaling doesn't work with the current kernel with my Via C7 processor.  I've heard great things about CPU scaling in 2.6.21

Cheers

---

### Post by k0001 on 2007-05-02
I'd love it! since without kernel 2.6.21, there's no support for w83627dhg sensor, which has been included in a lot of new motherboards lately.

lot's of new hardware support afaik in 2.6.21!

please backport it =)

---

### Post by alfredio on 2007-05-03
For those of you needing the 2.6.21 kernel in order to get the latest alsa drivers, I can report another solution. You will install the latest alsa driver with the current 2.6.20 kernel (tried, it works).

Please follow the instructions reported in [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
with the following patch:
In order to install the required tools, use the following command instead of the proposed one:

```
sudo apt-get install build-essential ncurses-dev gettext libasound2-dev
```

(that is: you also need gettext and libasound2-dev in order to compile)

The official Ubuntu instructions say that this SEEMS an intrusive operation (installing something from source, especially kernel drivers, is likely to break the apt package system), but actually it isn't. I hope they are right :-)

Hope this can be useful to someone of you that is waiting for the 2.6.21 kernel, just to get the new alsa drivers...

---

### Post by cjbehm on 2007-05-10
Count me in for wanting a backport! I've built my own kernel in the past, but it's not something I want to do. I know I'll spend days sorting out all the stuff I break :P

---

### Post by engla on 2007-05-10
Don't you all know this won't happen? Backports doesn't do *complicated* packages. The kernel is problably one of the most complicated, and it updates several core libraries and ties to lots of core services..

---

### Post by jerrylamos on 2007-05-10
Well on this system I've got 2.6.22-1

uname -a
Linux Linux-Gutsy 2.6.22-1-generic #1 SMP Mon Apr 30 10:49:22 GMT 2007 i686 GNU/Linux

from Synaptic.

I installed the kernel package and edited menu.lst to point to the right kernel.

Now I'd previously changed feisty > gutsy in sources.list, enabled every Synaptic repository in sight, and did update and upgrade.

I don't know if you need the sources.list stuff for the kernel or not.

Cheers, Jerry

---

### Post by mmxbass on 2007-05-21
Agreed that something like this would be a serious service to the users. There's various hardware (not just mono sensors) that many of us depend on that simply does not work in 2.6.20 and is known to be functional in 2.6.21.

---

### Post by ebethune on 2007-05-21
I also would like to see 2.6.21 in Feisty.  My HP scanner will not work with 2.6.20, apparently due to a problem with USB that is referenced here 

[http://lists.alioth.debian.org/pipermail/sane-devel/2007-February/018615.html](http://lists.alioth.debian.org/pipermail/sane-devel/2007-February/018615.html)

This is reported to be fixed in 2.6.21

---

### Post by bcasanov on 2007-05-23
I am not sure if the new kernel would help me solve the sound problems I have been having, [http://ubuntuforums.org/showthread.php?t=433514&highlight=cannot+hear+sound+in](http://ubuntuforums.org/showthread.php?t=433514&highlight=cannot+hear+sound+in), but if this helps with a lot of hardware issues many users have been having, count me in with wanting to see  the new kernel or the alsa drivers in the repositories or backports.  Only one question remains: are the new alsa drivers already in the backports?

---

### Post by ian dobson on 2007-05-26
+1 for me.

I'm interested in a backport/updated kernel too. 

I need a 2.6.21 kernel for lm-sensors as the sensor chip is only supported in a new kernel.

Regards
Ian Dobson

---

### Post by ehst on 2007-05-29
I need the new kernel version to use my wireless PCI card RTL-8185... In the 2.6.20 version my card don`t work...

[]`s

---

### Post by mustali on 2007-05-29
I too would love to see 2.6.21 in fiesty.

I am looking forward to using Intel's PowerTOP to increase my lappy's battery life.

So far, it looks like its going to take a long time for that to happen.. will wait till then.. :popcorn:

---

### Post by kwaanens on 2007-05-30
+1 from me!

I really need this, in order to have some sort of monitoring on my desktop/multimedia computer. I currently have no monitoring available, except for hddtemp and nvidia temperature.
The culprit being my ASUS P5B Deluxe mobo.

Please! I know this is complicated, but the rewards are very big for a lot of us.

- Ketil

---

### Post by zero-Q on 2007-06-01
+1 to backport because of[ dmraid issue ]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110245")

---

### Post by Yanson on 2007-06-04
+1 for RAID6 reshape.

---

### Post by Yoeri on 2007-06-07
+1 Backport to get rid of Windows for using my Epson Perfection 1670 scanner ...

---

### Post by CorporateGoth on 2007-06-08
Add me to the list.  2.6.21 has a fix for the Sierra Wireless cards that are shipped in every Lenovo that has BroadbandAccess support (from Verizon) built in. Basically it will make the card turn on when the driver is loaded - a simple fix, which I have done as a patch and made a custom kernel for - but the restricted drivers I need (fglrx and ipw3945) screw me over due to there being no easy way to make a custom restricted drivers package.

---

### Post by deadspider187 on 2007-06-08
I could use the NO_HZ and powertop patches included in 2.6.21.  What's the hold up, 2.6.22 will be out soon and we still don't have 2.6.21?

---

### Post by alfredio on 2007-06-08
> What's the hold up, 2.6.22 will be out soon and we still don't have 2.6.21?
This is correct. When Ubuntu is released, every six month, a suite of software is selected. For the successive six month after the release, the policy is not to upgrade the software, with the only exception of (small) bug fixes (because big bug fixes may introduce new bigger bugs themselves).

A "backport" is an exception to this rule. If a user requests a backport, then he is asking to upgrade a program, even if it is not release time (usually the new version will be present in the next release, so we are "porting back" a package from a newer release to an older, this is why we call them "backports"). Moreover, backports are not mandatory: you can choose if you want them or if you prefer to use the old, stable, version of the software (actually, if you don't say anything, then you use the old stable version; while if you add "backports" to your repositories, then you are willing to use backported versions).

Here, we are kindly asking for a backport of the kernel. However, we know feisty ships with the 2.6.20, and we don't expect 2.6.21 to become an official kernel, not before the next release.

By the way, it seems that our request is not going to be satisfied, not in feisty :-).

---

### Post by mmxbass on 2007-06-08
The request will be satisfied if they can get it through their heads that enough people are unhappy.

---

### Post by deadspider187 on 2007-06-09
I can understand that.  I'm usually a gentoo user, but feisty has a lot of big advantages right now, especially out-of-the-box support for stuff.  Since I'm not really used to apt-get and repositories, is there a repository for bleeding-edge stuff, even if it's not supported by the ubuntu team?

---

### Post by mmxbass on 2007-06-09
> **deadspider187 said:**
> I can understand that.  I'm usually a gentoo user, but feisty has a lot of big advantages right now, especially out-of-the-box support for stuff.  Since I'm not really used to apt-get and repositories, is there a repository for bleeding-edge stuff, even if it's not supported by the ubuntu team?There's always the Debian unstable repositories. Not something I'd recommend, but they're there.

---

### Post by exc220 on 2007-06-11
I'd love the backport...I'm running feisty on a P5B-Deluxe and would love to have some temp monitoring!!

---

### Post by strabes on 2007-06-17
I'd like it so that I can add support for my Microsoft Natural Ergonomic Keyboard 4000's extra buttons for which all patches are written for 2.6.21.

---

### Post by sunshine12 on 2007-06-20
2.6.21 supporting silan sc92031, that will solve my ethernet card compatibility problem..

---

### Post by angryfirelord on 2007-06-23
Personally, I'd wait until 2.6.22 is completed. 2.6.21 had some experimental stuff thrown into it.
[http://www.linux-watch.com/news/NS8296942554.html]("http://www.linux-watch.com/news/NS8296942554.html")

You probably could use a Debian kernel, but you'd lose the automatic hardware detection since there is no linux-restricted package for Debian.

---

### Post by Franko30 on 2007-06-25
**+1 for backport:**

The Epson Perfection 1670 snapscan problem that was introduced with Feisty drives me crazy.

See: [http://ubuntuforums.org/showthread.php?t=26911&page=3](http://ubuntuforums.org/showthread.php?t=26911&page=3)

Franko30

---

### Post by evilgeek on 2007-07-10
To rekindle this subject again... It would be great if the current latest stable kernel (2.6.22) would be backported to Feisty as the latest kernel has the updated mac80211 modules needed in order for stable operation of the latest Intel iwlwifi drivers needed for the new 4965AGN chip set. Current I'm using ndiswrapper but it'd be great if I could use the native drivers.

---

### Post by angryfirelord on 2007-07-10
Kernel updates would be way too tricky for backports. I'm sure the last thing the Ubuntu devs need is a flood of posts about how the update broke their system. If you want to run a more updates kernel, you can do a couple of things:

-compile your own. There are some tutorials hanging around. Google is your friend here. [http://www.isi.edu/~weiye/howto/kernel.html]("http://www.isi.edu/~weiye/howto/kernel.html")
-attempt to use Gusty's kernel. This could be problematic and may just break your system.
-upgrade or install Gusty. It would probably be like running Debian Unstable/Experimental on the system.
-run Debian Unstable. Despite the name, Unstable is really not all that, well, unstable. You just have to run apt-get/aptitude daily and if something breaks, oh well. The same can be said for Gusty at the moment.
-run another distro. Fedora & Slackware both contain 2.6.21 kernels.

---

### Post by dopry on 2007-07-22
I've been doing some exprimenting with the 2.6.22-8 kernel from gutsy on feisty. It seems to behave pretty well except I have to recompile a few wifi drivers... You mileage may vary, but you can always reboot into your old kernel and dpkg --purge the one from gutsy if theings don't go well for you... 

Don't expect anyone to support such a configuration.

---

### Post by mmxbass on 2007-07-22
The whole thing is nearly moot at this point. Feisty's time to shine is already half over almost to the day.

---

### Post by bensam40 on 2007-09-15
I have ubuntu 7.04 in my p4,3.06 dual core, intel 965 mb with sata 80gb hdd.  how to install kernel 2.6.21 in my system?

---

### Post by mazor on 2007-10-02
> **bensam40 said:**
> I have ubuntu 7.04 in my p4,3.06 dual core, intel 965 mb with sata 80gb hdd.  how to install kernel 2.6.21 in my system?

Goto this ubuntu forum topic

[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

It clearly shows how to do it. I used the second method and it is working now.

If you run VMWARE you will need the latest update patch to recompile to latest kernel.

For me, I had to also disable EVMS or change the conf file. this is only for those that have the recursive device not ready bug after kernel or Gutsy upgrade.

MAzor

---

### Post by mmxbass on 2007-10-02
Is there even a point to this discussion anymore? Gutsy is coming out in a little over two weeks and it runs 2.6.22.

---

### Post by kwaanens on 2007-10-03
> **hexnet said:**
> Is there even a point to this discussion anymore? Gutsy is coming out in a little over two weeks and it runs 2.6.22.

No there is no point to the discussion of backporting.
That's why the last post discussing *backporting* here is from July 10th :)

- Ketil

---

