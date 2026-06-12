---
title: "Difference between 14.04 and 14.04.2 releases"
date: 2015-04-25
forum: Ubuntu, Linux and OS Chat
---

### Post by tech291083 on 2015-04-25
Hi,

Is there any special difference between Ubuntu 14.04 LTS (Desktop/Server and all other variants) and Ubuntu 14.04.2 LTS (Desktop/Server and all other variants)?

I already have the original Ubuntu 14.04 LTS (Desktop(32 and 64 bit)+Server(32 and 64 bit)), keeping in mind the fact that I will be supported for 5 years. Do I need to download and install the latest Ubuntu 14.04.2 LTS (Desktop+Server, 32 and 64 bit)? Will this 14.04.2 be supported for 5 years? Thanks.

---

### Post by Keith_Helms on 2015-04-26
If you've been letting software updater keep your system up to date you have everything that's in 14.04.2 except for something called the Hardware Enablement Stack or LTS Enablement Stack.   What that does is puts you on a newer kernel and newer Xorg video drivers, which are currently the ones from the 14.10 release.  You can install those manually from the repository which should make your system identical to if you had started with a 14.04.2 install.

Details on how to do it are here:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

The only "catch" to doing this is that a given HWE stack actually has a shorter support period than the rest of the LTS release and you'll have to upgrade again to a newer HWE stack at some point before the 5 years are up.   The current schedule is at the bottom of the link I included under "LTS Kernel Support Schedule".

If I've misstated anything, I'm sure a moderator will jump in to correct me.

---

### Post by grahammechanical on 2015-04-26
Since Ubuntu 14.04 was released there have been developments in computer hardware. The Linux kernel developers work hard to keep up to date with new hardware by improving the Linux kernel.

To keep Ubuntu 14.04 up to date also we get what the developers call point releases. So, when 14.04 was released it came with kernel 3.13. When 14.04.1 was released it still had the 3.13 kernel but later revisions of it. Ubuntu 14.04.2 has the 3.16 kernel that came with Ubuntu 14.10. There is also other stuff that is included in what the developers call the hardware enablement stack. In this way new installs of Ubuntu 14.04 will be as up to date with new hardware as it is possible to be.

If we already have Ubuntu 14.04 installed we will not automatically move on to these newer hardware enablement stacks. We have to have to accept the offer to upgrade or run some code.

The 3.13 kernel in 14.04 and in 14.04.1 will be supported for the full length of the 14.04 support period. That is up to April 2019. The 3.16 kernel in 14.04.2 will only get 18 months support. The kernel in 14.04.3 will only get 12 months support. The kernel in 14.04.4 will only get 6 months support. This is because the next LTS (16.04) will be released by the time the support period for those kernels ends.

The kernel in 14.04.5 will be supported until April 2019. So, we either stay on 14.04 or 14.04.1 or we move on to 14.04.2 and then on to 14.04.3 and the following point releases until we upgrade to 16.04.

I got this information from here

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

> The 14.04.2 and newer point release will ship with an updated kernel and  X stack by default. If you have installed with older media you can use  the following to install the newer kernel from 14.10 (Utopic):

Regards.

---

### Post by tech291083 on 2015-04-26
> **Keith_Helms said:**
> If you've been letting software updater keep your system up to date you have everything that's in 14.04.2 except for something called the Hardware Enablement Stack or LTS Enablement Stack.   What that does is puts you on a newer kernel and newer Xorg video drivers, which are currently the ones from the 14.10 release.  You can install those manually from the repository which should make your system identical to if you had started with a 14.04.2 install.

Details on how to do it are here:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

The only "catch" to doing this is that a given HWE stack actually has a shorter support period than the rest of the LTS release and you'll have to upgrade again to a newer HWE stack at some point before the 5 years are up.   The current schedule is at the bottom of the link I included under "LTS Kernel Support Schedule".

If I've misstated anything, I'm sure a moderator will jump in to correct me.

Thanks. I think I get your point.

Now, my understanding is...

I will from now onwards use only the 14.04 LTS version thinking that it will be supported fully ie all of its components including the kernel until 2019, and not any of the subsequent upgrades ie 14.04.1, 14.04.2 and so on, as they are the same as the original 14.04 LTS, but only include update (hardware related etc).

So if I stick with the origianl 14.04 LTS, then whenever I update my system fully, it will automatically upgrade to the latest available version at that point in time ie 14.04.x, am I right here? And the upgrade to the latest version will automatically have all the components upgraded to their latest versions including the kernel (and packages) etc. 

Now this thing called LTS Enablement Stack, is new to me. Never heard of it before and as you mentioned and I understand if I stick with the original 14.04 LTS and whenever I update my system fully, everything else will be upgraded ie kernel and packages except the LTS Enablement Stack itself. Right? And I will have to do it manually. In short I can use 14.04 LTS and keep updating it until 2019, which is the year upto which its official support will continue. I just want peace of mind by sticking with 14.04 LTS and keep updating it until 2019. That's all. 

Thanks.

---

### Post by Keith_Helms on 2015-04-26
> **tech291083 said:**
> 
So if I stick with the origianl 14.04 LTS, then whenever I update my system fully, it will automatically upgrade to the latest available version at that point in time ie 14.04.x, am I right here? And the upgrade to the latest version will automatically have all the components upgraded to their latest versions including the kernel (and packages) etc. 


That's mostly correct.   When you update your system, all components except the kernel and the xorg graphics will be updated to the same versions as are in the newest 14.04.x point release (or higher versions if the newest 14.04.x point release has been out a while).  The kernel will be updated to the latest maintenance version in the 3.13 series (currently 3.13.0.49.56 on my system) not the absolute latest kernel version (4.0 just came out) and not the kernel version that is in the latest 14.04.x refresh (currently the 3.16 kernel with 14.04.2).  The same thing applies to the xserver xorg packages.

---

### Post by tech291083 on 2015-05-07
> **grahammechanical said:**
> 

The 3.13 kernel in 14.04 and in 14.04.1 will be supported for the full length of the 14.04 support period. That is up to April 2019. The 3.16 kernel in 14.04.2 will only get 18 months support. The kernel in 14.04.3 will only get 12 months support. The kernel in 14.04.4 will only get 6 months support. This is because the next LTS (16.04) will be released by the time the support period for those kernels ends.

The kernel in 14.04.5 will be supported until April 2019. So, we either stay on 14.04 or 14.04.1 or we move on to 14.04.2 and then on to 14.04.3 and the following point releases until we upgrade to 16.04.


Well I appreciate the time you have spent explaining the concept to me. I think after thinking for a while, it is better (with my limited technical ability, but unlimited enthusiasm for Linux distros including, but not limited to Ubuntu) that I keep using 14.04 version and not go for subsequent point releases (14.04.x) whenever they come up. As far as I know and you have mentioned 14.04 LTS will be supported until 2019 as long as one continues to update his system, nothing really matters to me as I am a regular user of Ubuntu and not an expert yet. I always update Ubuntu no matter what. So I will continue using 14.04 LTS and politely say no to the subsequent point releases (14.04.x) to make my life simple. Thanks a lot.

---

### Post by oldfred on 2015-05-07
It will tell you that you have the newer point release, just not the new kernel that is only with the Enablement stack. You will get kernel updates for security or major issues that are backported.

I still have my orginal 14.04, but it says it is 14.04.2 and has original 3.13.xx major version kernel.

fred@trusy-ar:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.2 LTS"
fred@trusy-ar:~$ uname -a
Linux trusy-ar 3.13.0-52-generic #86-Ubuntu SMP Mon May 4 04:32:59 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Bucky Ball on 2015-05-08
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by AleveSicofante on 2015-05-09
> **grahammechanical said:**
> The 3.13 kernel in 14.04 and in 14.04.1 will be supported for the full length of the 14.04 support period. That is up to April 2019. The 3.16 kernel in 14.04.2 will only get 18 months support. The kernel in 14.04.3 will only get 12 months support. The kernel in 14.04.4 will only get 6 months support. This is because the next LTS (16.04) will be released by the time the support period for those kernels ends.

The kernel in 14.04.5 will be supported until April 2019. So, we either stay on 14.04 or 14.04.1 or we move on to 14.04.2 and then on to 14.04.3 and the following point releases until we upgrade to 16.04.

I got this information from here

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards.

This doesn't make sense to me. Say I buy a new computer today and I want  to stay on the current LTS release for its promised support time (that's April 2019). I go to download the LTS version and what I  get is 14.04.2. And you're telling me this will only be supported until April 2016? That frontally contradicts what's written in [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by deadflowr on 2015-05-09
> **AleveSicofante said:**
> This doesn't make sense to me. Say I buy a new computer today and I want  to stay on the current LTS release for its promised support time (that's April 2019). I go to download the LTS version and what I  get is 14.04.2. And you're telling me this will only be supported until April 2016? That frontally contradicts what's written in [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

14.04 will be supported until April 2019, regardless of which point release the user installed.
The kernel version and graphics stack installed per point release will not. (the exception being the original and the first point release, those kernels and graphics stack are supported the full five years)
However, when the 14.04.5 point release arrives users using the installed versions of point release 14.04.2, .3, and .4 will get an option to upgrade to the kernel version used in 14.04.5.
Hopefully this time around the option will be more pronounced, as I think the option to do so for 12.04 users was iffy...

---

### Post by AleveSicofante on 2015-05-09
Again, this is NOT what the download page says. It makes ZERO exceptions explicit. I'd love some official Ubuntu representative to make this clear. If you're a Canonical employee, please suggest Canonical to state the exceptions in the download page. As it currently is, it's misguiding to say the least.

Also: what are the kernel and graphics stack versions in 14.04.2 downloadable ISO? If they're not the latest, what's the point (pun intended)?

---

### Post by deadflowr on 2015-05-09
> Also: what are the kernel and graphics stack versions in 14.04.2 downloadable ISO? If they're not the latest, what's the point (pun intended)?
They are the versions used in 14.10.

They link you to the release notes that explains it well
[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes)
seems explicit enough...

---

### Post by AleveSicofante on 2015-05-09
You're not answering the main point.

---

### Post by Elfy on 2015-05-09
If the point is what's mentioned at ubuntu.com - then no-one here can do anything about that. 

It's certainly going to be unlikely that a Canonical employee will happen by this thread.

Best I could suggest would be to create a bug report if you think that it is a bug

[https://bugs.launchpad.net/ubuntu-website-content/+filebug](https://bugs.launchpad.net/ubuntu-website-content/+filebug)

---

### Post by AleveSicofante on 2015-05-09
The point is deadflowr is saying basically that 14.04.2 (and upcoming .x versions from that) has no five years **full** support and Canonical is saying the opposite at the download page in ubuntu.com. Who should I believe?

---

### Post by Elfy on 2015-05-09
14.04.2 can't have 5 years of support. 

14.04 does - it's point releases are just 'mini-releases' *during* the 5 years

---

### Post by Elfy on 2015-05-09
14.04.2 can't have 5 years of support. 

14.04 does - it's point releases are just 'mini-releases' *during* the 5 years

---

### Post by AleveSicofante on 2015-05-09
"Ubuntu 14.04.2 LTS comes with five years of security and maintenance updates, guaranteed."

I'll concede they mean 5 years from 14.04 first release. That's until April, 2019. There's no way to infer from the download page that 14.04.2 in particular won't have security and maintenance updates (which in my view implies both the kernel and graphics stack, since it isn't said otherwise anywhere) past April, 2016, like deadflowr claims.

---

### Post by mc4man on 2015-05-09
I'm probably missing something but, - 
All non kernel & non mesa packages will receive typical 5 yr support
The hwe installs will also get the full 5 yr support for kernel & mesa as long as the user manually moves their current hwe-lts install to the next lts set of packages.
This can be done either by - 
1. a fresh install of next point release (14.04.2 image, 14.04.3 image 14.04.4 ...ect.
2. installing the newly available lts kernel & mesa packages in their current 14.04, 14.04.1, 14.04.2 ...  install

The final lts (14.04.5) is supported till the 5 yr eol for kernel & mesa

---

### Post by AleveSicofante on 2015-05-10
Thank you for clarifying, mc4man. That makes total sense and restores my confidence in LTS point releases.

---

### Post by kagashe on 2015-05-10
When you click on download link on [ubuntu.com/dekstop]("http://www.ubuntu.com/desktop") today it offers Ubuntu 14.04.2 LTS 64-bit ISO. That is because the Hardware of the person who wants to download is likely to be newer and may not work well on 14.04. Following is my personal experience:
I bought Lenovo G50-45 in Dec 2014 and used Ubuntu 14.04. The pci id of Video card was not included in Ubuntu 14.04, even than it worked but could not load Radeon driver. When I went for Hardware Enablement Stack the Kernel 3.16 and associated driver is working very well with 3D support on Unity.

When the support for 3.16 ends or even before that I will get the next Kernel and so on till 2019.

Kamalakar

---

### Post by Keith_Helms on 2015-05-10
Now that we've beat this issue to death, could someone explain to me why Xubuntu (I don't know about the other flavors) 14.04.2 does not have the 3.16 kernel?

---

### Post by kagashe on 2015-05-10
> **Keith_Helms said:**
> Now that we've beat this issue to death, could someone explain to me why Xubuntu (I don't know about the other flavors) 14.04.2 does not have the 3.16 kernel?
Unlike Ubuntu 14.04 Xubuntu 14.04 is supported only for 3 years and not 5.
Xubuntu is meant comparatively for old hardware and does not need hardware enablement stack in fact it may cause problems on old hardware.

Kamalakar

---

### Post by tech291083 on 2015-06-25
Thanks a lot friends.

---

### Post by kansasnoob on 2015-06-26
> **Keith_Helms said:**
> Now that we've beat this issue to death, could someone explain to me why Xubuntu (I don't know about the other flavors) 14.04.2 does not have the 3.16 kernel?

According to the [manifest for Xubuntu 14.04.2]("http://cdimage.ubuntu.com/xubuntu/releases/14.04/release/xubuntu-14.04.2-desktop-i386.manifest") it does have the 3.16 version kernel:

> linux-generic-lts-utopic	3.16.0.30.23
linux-headers-3.16.0-30	3.16.0-30.40~14.04.1
linux-headers-3.16.0-30-generic	3.16.0-30.40~14.04.1
linux-headers-generic-lts-utopic	3.16.0.30.23
linux-image-3.16.0-30-generic	3.16.0-30.40~14.04.1
linux-image-extra-3.16.0-30-generic	3.16.0-30.40~14.04.1
linux-image-generic-lts-utopic	3.16.0.30.23

If you installed using either the 14.04 or 14.04.1 images you'll remain on the 3.13 series kernel:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support)

---

### Post by Bucky Ball on 2015-06-26
> **kansasnoob said:**
> According to the manifest for Xubuntu 14.04.2 it does have the 3.16 version kernel ... If you installed using either the 14.04 or 14.04.1 images you'll remain on the 3.13 series kernel:



Yep. I have machines running both and that is exactly right. ;)

---

