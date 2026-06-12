---
title: "Update on fs-corrupting kernel bug?"
date: 2009-07-21
forum: System76 Support
---

### Post by phyzome on 2009-07-21
A number of us System76 customers were hit by a kernel bug introduced in the kernel that came with Jaunty. This bug quickly caused massive filesystem corruption on 64-bit machines (including System76's Pangolins.) Here is the launchpad thread, :

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all)

I am wondering if this issue has been resolved regarding the System76 machines. Has anyone who experienced the problem braved the upgrade to Jaunty with a newer kernel and found that the bug did not arise again? Is there any official word on how to prevent this issue?

I'm still stuck on Intrepid, and I'd like to get to Jaunty sometime before Karmic comes out... :-/

Further links to investigate:
[LIST]
[*][Possible fix in kernel](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=commit;h=b29e79bf557ce777878518da154f4a0becb1de0e)
[*][How to use a newer kernel image than the ISO provides](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691/comments/122)
[*][An approach to finding the first broken version](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691/comments/129)
[/LIST]

---

### Post by gila_monster on 2009-07-21
phyzome,

this seems to be limited to 2.6.28-11 -- is that your understanding as well? I'm running 2.6.28-13 (Linux Mint), and so far so good. I've been having other problems, though, that MIGHT be related.

---

### Post by phyzome on 2009-07-21
> **gila_monster said:**
> phyzome,

this seems to be limited to 2.6.28-11 -- is that your understanding as well?
I was under the impression that the problem *started* in 2.6.28-11, and that there is no clear answer as to whether it has been fixed.

> **gila_monster said:**
> I'm running 2.6.28-13 (Linux Mint), and so far so good. I've been having other problems, though, that MIGHT be related.
You would know. Your programs would start crashing, and when you rebooted, the OS would entirely fail to start, possibly as early as the second-stage boot loader.

---

### Post by gila_monster on 2009-07-21
> **phyzome said:**
> I was under the impression that the problem *started* in 2.6.28-11, and that there is no clear answer as to whether it has been fixed.

[elided]

You would know. Your programs would start crashing, and when you rebooted, the OS would entirely fail to start, possibly as early as the second-stage boot loader.

Thanks for the clarification. So far, no issues with -13, for what that is worth.

---

### Post by phyzome on 2009-07-21
> **gila_monster said:**
> Thanks for the clarification. So far, no issues with -13, for what that is worth.

What machine do you have? I'm on the Pangolin Performance (specifically panp4i.)

---

### Post by gila_monster on 2009-07-22
> **phyzome said:**
> What machine do you have? I'm on the Pangolin Performance (specifically panp4i.)

panp4n. My problems stem from an interaction between X and the nVidia driver, and they appear to be specific to my particular box, since nobody else has seen them. I updated to the 185 driver, and all is well...for now. Currently, also running Linux Mint (long story, may go back to straight Ubuntu at the next release). Not sure if Mint has a newer kernel. I wouldn't think so.

---

### Post by mike1212 on 2009-07-22
I've been having problems with my system76 pangolin I got on July 10th.  It's using 2.6.28-13.  I've had fsck's on starup, program freezes and program crashes which is pretty uncool on a brand new machine.  I mean, I like to tinker with my computer, but really.

note: I have disabled the nvdia driver because that seemed to have solved some problems I was having on my system76 serval machine.

---

### Post by gila_monster on 2009-07-22
> **mike1212 said:**
> I've been having problems with my system76 pangolin I got on July 10th.  It's using 2.6.28-13.  I've had fsck's on starup, program freezes and program crashes which is pretty uncool on a brand new machine.  I mean, I like to tinker with my computer, but really.

note: I have disabled the nvdia driver because that seemed to have solved some problems I was having on my system76 serval machine.

Out of curiosity, what file system are the partitions using? I've read that ext4 may have some issues under Ubuntu. I have mine set to ext3 right now. Was using ext4 for a while for the root partition, but I never determined whether it was related to my nVidia/X problem.

---

### Post by mike1212 on 2009-07-22
my pangolin uses ext3 type filesystem.  that's what came from system76 2 weeks ago.

note:  after disabling nvdia driver I've booted 3 or 4 times with no issues.  really short sample time, but so far so good.

---

### Post by gila_monster on 2009-07-22
> **mike1212 said:**
> my pangolin uses ext3 type filesystem.  that's what came from system76 2 weeks ago.

note:  after disabling nvdia driver I've booted 3 or 4 times with no issues.  really short sample time, but so far so good.

Interesting. Might not really be the kernel -- but don't quote me, it's hard to tell.

When I get home tonight, I'll dig up the instructions I used to install the nVidia 185 drivers. You can try that and see if it helps. I've had no issues since I did that (other than gnome-do sucking up a huge amount of RAM for indexing).

---

### Post by robert.rankin.jr on 2009-07-22
Based on responses in the bug report and my own experience, I'm pretty sure it's a kernel issue. Maybe the nVidia driver screws this kernel up. I'm no expert, so I can't comment. I also have no clue about the -13, but I've heard that the -14 (in jaunty-proposed) may fix the problem. I'm still using the 32-bit version because trying to operate with a 64bit installation is too difficult. If you want to use Jaunty, I'd use the 32bit version. It is confirmed, though, that you can install the 64bit version and upgrade the kernel. Check out this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691/comments/122](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691/comments/122)

You don't need to do the intrepid install, you can just follow the instructions from within a working Jaunty installation on the first boot. Or, if you're paranoid like me, and neither like upgrades nor screwed up installations, you can install from the usb-disk, reboot, chroot into the new environment and do the kernel install.

Robert

---

### Post by gila_monster on 2009-07-22
Good info, Robert. Thanks.

As promised, and in case anyone wants to try it, the instructions for the new nVidia driver are here: [HTML]http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185+installation[/HTML]

I had no trouble with this, but I've done this kind of thing before. **If you are not sure of what you are doing, I recommend not trying this unless you are looking to learn some things.** When it goes well, it's wonderful. When it doesn't, it can take a while to clean up the mess. The instructions are clear, but a bit complicated.

---

### Post by glacialfury on 2009-08-04
For those wondering about the filesystem mattering, I've had this occur on a serp4, Ubuntu and Kubuntu 64 bit jaunty under both ext3 and ext4.  I haven't looked into nvidia involvement yet though.

---

### Post by thomasaaron on 2009-08-04
glacialfury, I don't think there is an nvidia element to it. I believe it has to do with some change in the SATA controller drivers.

---

### Post by phyzome on 2009-08-04
> **thomasaaron said:**
> glacialfury, I don't think there is an nvidia element to it. I believe it has to do with some change in the SATA controller drivers.

Have you been able to reproduce it on a test machine?

---

### Post by thomasaaron on 2009-08-04
Working on it right now. I have a SerP4 on my desk and I'm doing some huge file transfers with it. Hopefully that will crack it.

JDB says he thinks it doesn't happen on a 32-bit kernel. Problem is, that *might* forfeit suspend functionality.

---

### Post by glacialfury on 2009-08-05
I wonder.  Most of the relevant bug reports point toward it being a specific kernel; x.x.x.x-11, whichever one ships with the 9.04 installation, and affecting primarily (exclusively?) the 64-bit version.  It may not be worth your while to hunt down the hardware portion of it specifically, since it seems it is triggered by the kernel, and it can be fixed relatively easily by changing the kernel.

I followed a two-line command to download and swap out the kernel, and it hasn't had any problems since then.

---

### Post by thomasaaron on 2009-08-05
Good points...

Could you please post your process?

---

### Post by samalex on 2009-08-05
Just curious I have a Pangolin Performance in transit now.  Will it be preloaded with the 2.6.28-11 kernel?  If so is it recommended to upgrade to -13 or whatever the latest is in the Ubuntu repositories?

Just checking, I don't want to drop all my stuff on the laptop then run into file system corruption.

Thanks ...

Sam

---

### Post by thomasaaron on 2009-08-05
samalex,

I *think* we're shipping with the *-13 kernel, and the problem does seem related to large file transfers.

However, it's not clear to me yet if this problem is affecting the PanP5 -- but it may be. I'm running a number of tests right now.

This bug is a priority, and we're wrestling with it quite actively.

---

### Post by samalex on 2009-08-05
Hi Thomas,

Awesome, thanks.  When the laptop arrives (hopefully Friday) I'll check the kernel version and run it through the ringer before transferring any huge amounts of data to it.  If you guys do find a fix or have suggestions on updates, I'll keep an eye on the forum.

Thanks --

Sam

---

### Post by phyzome on 2009-08-05
> **thomasaaron said:**
> This bug is a priority, and we're wrestling with it quite actively.

This is good to hear. :-)

Let me know if I can help. I have a spare 6GB partition on my panp4i, and I'd be willing to install with a couple different kernels.

---

### Post by thomasaaron on 2009-08-05
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all)

That's the pertinent launchpad report. There are a couple ways to fix it, for sure. But I don't really recommend either just yet.

One could install 32-bit Ubuntu. But who wants that?
There's also a round-about fix on post 122 or 123. Not ideal.

The devs are under HUGE pressure with this one, and it's fixed in Karmic -- and they've promised we won't have to wait for Karmic for the fix. It's largely a waiting game at this point.

Until I find out more, I'd minimize large file transfers.

---

### Post by gila_monster on 2009-08-05
I did try the solution in post 122, and it seemed to work, but I did not hammer the system particularly hard after that.

Currently running the 2.6.18-14 kernel, and no issues, but again not hammering hard.

For fun, I'm attempting to install Gentoo on the spare (Gateway) laptop. Have had zero success...and yet, it's less frustrating than the current problem! ;)

---

### Post by thomasaaron on 2009-08-05
Thanks, gila_monster.

OK, I've got an SerP4 computer in my shop. This is one that a customer sent in for diagnosis. It has been hit by this bug.

Right now, I'm running the *-14 kernel. I've downloaded almost 30 GB of data to it today, and I'm not seeing any problem at all. 

fsck keeps giving it a clean bill of health.

Is there anyone out there having this problem on the *-14 kernel?

There was a weak hint in that bug report that it *might/maybe/fingers-crossed* be fixed in *-14.

---

### Post by glacialfury on 2009-09-28
I hate to revive this dreaded topic, but I think I might have this in Karmic-alpha5.  I did a clean install of Karmic about two weeks ago, which initially worked fine, and then gradually started having errors, culminating in the "Can't boot, run fsck" sequence we all know and love.  Since then I've simply been using my Windows partition for my work, but I'm sure you'd all like me to return to my happier opensource self.

The information about this bug is not well delineated and I don't have the time to experiment that I used to; what can I do to ...
a) confirm whether this is, in fact, the same bug
b) repair or create a workaround

I'm happy to run any commands or output for you lot, and there's nothing critical on the damaged partition, so we can do whatever you like to it.

It's a SERP4, plagued by problems in nearly every version.
8.04-8.10: kernel oops related to clocksource causes block
9.04-9.10: filesystem corruption caused by ?kernel problem

I'm also willing to try another distro if you feel this will alleviate the problem.  I like Ubuntu very much, but exploring is also fun, if I can expect stability out of something else.

Regards,

---

### Post by thomasaaron on 2009-09-28
It's difficult right now to tell if it is the same bug. Did Karmic install with ext4 by default? If so, there could be a problem there too. We've not started testing with Karmic yet, and probably won't for a couple of weeks.

Also, I've heard it doesn't exist in 32-bit.

---

### Post by jdb on 2009-09-28
> **thomasaaron said:**
> It's difficult right now to tell if it is the same bug. Did Karmic install with ext4 by default? If so, there could be a problem there too. We've not started testing with Karmic yet, and probably won't for a couple of weeks.

Also, I've heard it doesn't exist in 32-bit.

WOW! if it's not available in 32 bit there is a lot of hardware out there (here) that will be left behind.
Out of 7 boxes in this house, only 3 are 64 bit machines.

jdb

---

### Post by phyzome on 2009-09-28
> **jdb said:**
> WOW! if it's not available in 32 bit there is a lot of hardware out there (here) that will be left behind.
Out of 7 boxes in this house, only 3 are 64 bit machines.

No, the *bug* isn't available in 32-bit.

---

### Post by HotShotDJ on 2009-09-28
Thomasaaron --

I've gone through the above linked bug report regarding this issue in preparation for the imminent arrival of my PanP5.  I have a thought regarding this problem until Karmic goes gold.

According to the bug report, the problem is also fixed in the 2.6.30 kernel.  I've been using that kernel as a drop-in replacement on my current system (32 bit) since its RC days without an issue due to the Intel Video problems in Jaunty.  It is a pretty painless install - here is the code for getting and installing the 64 bit version:```
$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.5/linux-headers-2.6.30-02063005-generic_2.6.30-02063005_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.5/linux-headers-2.6.30-02063005_2.6.30-02063005_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.5/linux-image-2.6.30-02063005-generic_2.6.30-02063005_amd64.deb
$ sudo dpkg -i linux-headers-2.6.30-02063005-generic_2.6.30-02063005_amd64.deb linux-headers-2.6.30-02063005_2.6.30-02063005_all.deb linux-image-2.6.30-02063005-generic_2.6.30-02063005_amd64.deb
```On the down side, this kernel will break AppArmor, so people who need AppArmor won't be able to use it.  I don't know if there are other problems that I didn't think of.  As I said, I've been using it on a 32 bit Dell system, so I don't know what unintended consequences the 64 bit 2.6.30 kernel might have on a System76 computer.

---

### Post by jdb on 2009-09-28
> **phyzome said:**
> No, the *bug* isn't available in 32-bit.

Ahhh, the *bug* isn't available :redface:
Should I feel I'm being slighted??? :lolflag:

jdb

---

### Post by thomasaaron on 2009-09-28
> I've gone through the above linked bug report regarding this issue in preparation for the imminent arrival of my PanP5.

I've not actually seen this bug with my own eyes on the PanP5. It seems to only hit our older Servals (no longer in production).

Pyzome, did *you* have it?

---

### Post by phyzome on 2009-09-28
> **thomasaaron said:**
> Phyzome, did *you* have it?

Yep, on my panp4i. I'm still running Intrepid because of it.

---

### Post by samalex on 2009-09-28
Hope you guys don't mind me chiming in...  When I got my PanP5 laptop about 2 months ago it did have the dreaded 2.6.28-11 kernel preloaded, but the first updates it ran moved me to -12 and I think I'm at -13 or -14 now (at work so I don't have laptop booted up right now) but I'm on the latest in the Ubuntu repositories.

When I ordered my laptop my fear was that I'd get this bug, but I haven't had any of the corrupt file system problems seen with this bug (knocking on wood) and I've copied MANY large files onto the laptop.  


Take care -

Sam

---

### Post by glacialfury on 2009-09-28
I can't recall offhand if I used ext4 or ext3; I'll have to run fsck from the livecd so I can fix it enough to tell.  I *do* know it uses kernel 2.6.31.10, which should be well past the fix.

I had this same problem before with both ext3 and ext4 in jaunty, so I'm not convinced it's that, but I'll take a look in the next couple days.

---

### Post by EmmEff on 2009-09-29
For what it's worth, I am also seeing the problem with 2.6.31.10 on Ext3.  For some reason, it seems to manifest itself primarily with bzip2 when unzipping a large (>100MB) file.

BTW, I am not running System76 hardware.

---

### Post by glacialfury on 2009-09-29
I haven't noticed an association with large file transfers; I suppose it depends on how you define large.  My primary work involves use and conversion (to OO.org) of Microsoft Office documents, often 10-25mb powerpoint files, and pdf files up to 50mb.  I transfer many small files frequently and download frequently (the office files mentioned above), but moving clumps of files exceeding 1-2 gb is rare; might have done it a couple times since the install.

I boot and shut down frequently, I *think* I was using the closed Nvidia drivers, but otherwise don't mess with much except the interface layout.  I mention the OpenOffice powerpoint->impress because impress files are simply zipped collections; I don't know what OO.org uses to decompress them, but maybe it has to do with your bzip problem, EmmEff

---

### Post by phyzome on 2010-03-12
Well, I recently had the opportunity to upgrade my system again, this time laying down an encrypted partition and putting Karmic into it. I found that the corruption bug is **still there**! I was unable to replicate it reliably, even using the iozone filesystem benchmarking tool, but it would sometimes appear within 10 minutes.

In any event, I found a setting in my BIOS to set the OS compatibility mode from "Other" to "Vista", which shows another field that lets you switch between IDE and AHCI mode. I used this switch and my system has been running fine!

Caveat: I had to scrap my Windows XP partition to do this, and installed Windows 7 in its place. Also be aware that changing this will likely screw up any *existing* Windows installation of any version.

---

