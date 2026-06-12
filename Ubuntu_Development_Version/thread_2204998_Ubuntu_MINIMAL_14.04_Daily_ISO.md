---
title: "Ubuntu MINIMAL 14.04 Daily ISO"
date: 2014-02-11
forum: Ubuntu Development Version
---

### Post by leespa on 2014-02-11
I have a new Intel Baytrail NUC incoming. Plan is for a full-time, HTPC running XBMC.

BOXDN2820FYKH0 
[http://ark.intel.com/products/78953/Intel-NUC-Kit-DN2820FYK](http://ark.intel.com/products/78953/Intel-NUC-Kit-DN2820FYK)

Due to bleeding edge hardware I'll be forced to use latest kernel, etc. Does anyone know where to find a Daily build / ISO of the 14.04 Ubuntu Minimal? An ISO or other means to get base installed and then run a package manager to keep current.

I can easily find the Daily Desktop and Server builds, but nothing for Minimal. Ubuntu min + XBMC has worked excellent for all other HTPC's so I'd prefer to stick with this route.

TIA

-----------------------------------------------------------------------------------
Solved by the following: 
-- Used one of the Server daily ISO's to get same minimal base but with UEFI boot support. [http://cdimage.ubuntu.com/ubuntu-server/daily/current/](http://cdimage.ubuntu.com/ubuntu-server/daily/current/)
-- Then upgraded the kernel to get Baytrail support via the Mainline kernel builds. [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)

---

### Post by grahammechanical on 2014-02-11
I can find where the minimum images are for stable releases - 13.10 being the latest, but not for a release under development. May be they do not yet exist as the code base is changing all the time. The variety of daily images available has been reduced to make better use of resources. That could be the reason. You may need to install from the 13.10 minimal image and then upgrade to the Linux 3.13 kernel.

[http://ubuntuhandbook.org/index.php/2014/01/linux-kernel-3-13-install-in-ubuntu-linux-mint/](http://ubuntuhandbook.org/index.php/2014/01/linux-kernel-3-13-install-in-ubuntu-linux-mint/)

Regards.

---

### Post by VMC on 2014-02-11
Have you tried the Daily Ubuntu Core? :

 [http://cdimage.ubuntu.com/ubuntu-core/daily/current/](http://cdimage.ubuntu.com/ubuntu-core/daily/current/)

---

### Post by leespa on 2014-02-11
@graham - thanks. I'll prolly give that a whirl.

Apparently others using OpenElec have had success with kernel 3.14-rcX ... I'll aim for that too.

@VMC - no I have not, but thanks for info too. I might just try an older ISO + newer kernel to limp along until 14.04 official...just want to get XBMC up & running with minimal fuss...*if possible*. ;-)

I'll post back what if anything works once I get the HW in my hands.

---

### Post by sudodus on 2014-02-11
Tarballs :-D

Like the containers of distros for my One Button Installer!

Is the old mini.iso installer abandoned in favour of Ubuntu Core tarballs?

---

### Post by sudodus on 2014-02-12
> **kansasnoob said:**
> Uh, 'ubuntu-core' and the Netboot image are two different things:

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds)

But a few hours ago the netboot image had the wrong kernel - it takes a few hours some times for things to get in sync :wink:

> **sudodus said:**
> For several days (weeks) I have seen no mini.iso

Also now when following your link I get

**Not Found**

> **kansasnoob said:**
> Yeah, it seems the QA Tracker is a hot mess,  but these links to the mini.iso should work if the kernel has been  upgraded:

[http://www.fr.php.net/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/](http://www.fr.php.net/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/)

[http://www.fr.php.net/ubuntu/dists/trusty/main/installer-amd64/current/images/netboot/](http://www.fr.php.net/ubuntu/dists/trusty/main/installer-amd64/current/images/netboot/)

And I was able to download the Ubuntu mini.iso via these French links

Thanks kansasnoob :-)

*Edit*: Here is the origin of one of the quoted posts: [http://ubuntuforums.org/showthread.php?t=2174725&page=9&p=12926787#post12926787](http://ubuntuforums.org/showthread.php?t=2174725&page=9&p=12926787#post12926787)

---

### Post by Bucky Ball on 2014-02-12
*Thread moved to **Ubuntu +1**.*

What makes you think you're forced to use an unreleased and still testing release? You are aware that 14.04 LTS is not officially released until April? Repeat: 14.04 is testing and not intended for, or advised for, use in production environments or where you need stability and reliability. Expect unexpected breakages. You probably won't get an easy ride. 

Also, all support requests, bug reports and anything else regarding 14.04 go in this sub-forum, nowhere else. Thanks.

---

### Post by zika on 2014-02-12
> **leespa said:**
> I have a new Intel Baytrail NUC incoming. Plan is for a full-time, HTPC running XBMC.

BOXDN2820FYKH0 
[http://ark.intel.com/products/78953/Intel-NUC-Kit-DN2820FYK](http://ark.intel.com/products/78953/Intel-NUC-Kit-DN2820FYK)

Due to bleeding edge hardware I'll be forced to use latest kernel, etc. Does anyone know where to find a Daily build / ISO of the 14.04 Ubuntu Minimal? An ISO or other means to get base installed and then run a package manager to keep current.

I can easily find the Daily Desktop and Server builds, but nothing for Minimal. Ubuntu min + XBMC has worked excellent for all other HTPC's so I'd prefer to stick with this route.

TIADid You contemplate using current stable edition of Ubuntu and adding to it (if You really need) kernel from (for example) [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) ...? Just to render my opinion...

---

### Post by leespa on 2014-02-12
@Bucky Ball, @zika - only people reporting good results with this 1-2 month-old hardware are using 3.14 kernels. Intel is still very active in BIOS development for this unit for instance.

As suggested above I will try an older release + new kernel and/or the Daily Core. I'm acutely aware that this is likely to give a rough ride, but it's just a HTPC that is OK to limp along until mainline support is available.

Still waiting on hardware arrival at this point - should get to testing it late this week or early next.

Thx

---

### Post by zika on 2014-02-12
> **leespa said:**
> @Bucky Ball, @zika - only people reporting good results with this 1-2 month-old hardware are using 3.14 kernels. Intel is still very active in BIOS development for this unit for instance.
As suggested above I will try an older release + new kernel and/or the Daily Core. I'm acutely aware that **this is likely to give a rough ride**, but it's just a HTPC that is OK to limp along until mainline support is available.
Still waiting on hardware arrival at this point - should get to testing it late this week or early next.
ThxI can (almost) reassure You that using older_release+newest_kernel should be much more pleasant ride that entering (especially if You do not have experience in U+1) U+1 now... As smooth as a ride in U+1 were up to now, experience tells me that month before last one is time when nice breakage can be expected... ;) As an added bonus is the fact that You can upgrade at any moment if you feel like doing it... ;)

---

### Post by leespa on 2014-02-21
FINALLY got this thing put together within last hour, updated BIOS. Hit first roadblock, however, since all prior posts I've read on this suggest UEFI OS installation.

However, trying with a Ubuntu 13.10 x64 mini.iso and of course it does NOT support UEFI booting... Shall I try the Ubuntu Core route or is there a practical way to make a mini.iso UEFI boot compatible?

A 12.04 LiveCD/USB boots just fine in UEFI mode. 

TIA

----------------------------------------------------------------------------------------------------

Update: dloaded a daily ISO of server_x64, installing in UEFI mode, Minimal installation. Moving on... ;-)

---

### Post by leespa on 2014-02-25
So I got server_daily.iso installed and just upgraded kernel to 3.14-rc4. The earth hasn't exploded yet so I consider that a good sign.

Questions I have is - is the **ppa:kernel-ppa/ppa** pretty much useless? Didn't seem to pick up any useful install options for new kernels once added so I just dloaded and installed the debs as per below?

[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds#Installing_Mainline_Kernels](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds#Installing_Mainline_Kernels)

---

### Post by Jhongy on 2014-03-03
+1 on using the latest kernel. Use the latest -rc if you can. All the baytrail support is still going in.

For example, the CPU scaling on kernels prior to 3.14-rc4 wasn't even working properly.

Definitely don't go with the "stable version" as other people are suggesting here if you want things to actually work well; this is bleeding edge hardware. Of course, you will get bugs either way.

---

### Post by leespa on 2014-03-03
So I marked this as solved - updated post 1.

The daily server ISO + 3.14-rc4 has worked well. Ran the unit with the latest XBMC Gotham alpha and had no crashes or even bugs seen thus far...worked very well.

Thanks all.

---

