---
title: "Ubuntu 14.04 LTS - Ensuring Long Term Support"
date: 2016-03-02
forum: Ubuntu, Linux and OS Chat
---

### Post by tatonqek on 2016-03-02
Greetings Everyone,

I have a few question regarding Ubuntu 14.04 and how it handles End of Life and updates.I am working in IT for a company that values set and forget Ubuntu workstations. Begin spread out all over the state, most of these computers can go several months or even years without being serviced by the IT department. 

I understand that 14.04 and 14.04.1 have full support through 2019. I made a fresh install using a 14.04.1 ISO, and started the Software Updater. After it finished and restarted, I discovered that Ubuntu was version 14.04.4, which only has 6 months of support.

1. If I continue to use the 14.04.4 release, what will need to be done after the 6 months of support is over?
2. Alternatively, how can I ensure that I am receiving Important updates without triggering an update to a newer version with a shorter support period.

Thanks for any recommendations you can give.

---

### Post by TheFu on 2016-03-02
Don't use "dist-upgrade" after you get to 14.04.1. Only use "upgrade" then.
OR
You'll need to ensure that dist-upgrade is run monthly (anything longer and the updates back up and huge updates leads to wonky systems, IMHO. 14.04.5 will be released and the dist-upgrade process will get that update which will be supported until the published EOL for 14.04.

Details are here: [https://wiki.ubuntu.com/Kernel/Support](https://wiki.ubuntu.com/Kernel/Support)  definitely review the entire page as some important info happens after the top part.

BTW, having a fallback plan for patches that happen infrequently is important.  Restore from the pre-dist-upgrade backup that was made and don't use dist-upgrade again. That is what I would do.

Oh - and it is probably best to look at the software-updater settings before running it again.  I don't use any GUI tools for this. Don't feel I have enough control with those things.

---

### Post by Bucky Ball on 2016-03-02
*Thread moved to **Ubuntu, Linux and OS Chat**.*

I run these three commands once or twice a week:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Otherwise, stay with .1 and dont run the last command.

I generally install the next LTS when it is released or just before on another partition and play around with it for awhile then migrate over when things are looking solid there, but I wonder if staying with the point releases might increase chances of a problem free upgrade to the next LTS when the time comes if you go that way ... :-k

It doesn't matter what you use, you'll get the 'important' updates for that release. Just update/upgrade regularly. If you are using 14.04.4, just keep using the three commands above and you will always be in support until 2019. There will be no EOL between point releases if that is what you're fearing. The .4 release doesn't die and leave you hanging. If you're doing your updates/upgrades, you'll be on .5 and won't even notice the EOL.

Here's me, fully up to date:

```
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty
```

Last time I looked it was .3. *shrug* :)

* One reason people do stick with a particular point release is that something changes in the next one and their hardware doesn't agree with it. Some recommend that if you're system is all good on the 14.04.1 release, let sleeping dogs lie and stay there. Never had that issue with LTS releases myself, though, and that's about all I've used for the last eight years.

---

### Post by sudodus on 2016-03-03
I think it works like this:

1. If you ***update && upgrade*** you get no kernel upgrades at all which is bad.

2. If you ***update && dist-upgrade*** from 14.04.1 LTS you get kernel upgrades within the trusty series, 3.13. The output of ***lsb_release -a*** will be upgraded to new point releases, but the hardware enablement stack and the kernel series will not be upgraded. This is also what is done by the automatic updating system of the desktop flavours of Ubuntu (I'm not sure about the server version). ***I would recommend this method***, and I ***think*** it will stay within the supported packages. ***[COLOR="#0000FF"]I would welcome other people to comment on this issue[/COLOR]*** :-)

3. If you upgrade the hardware enablement stack (and the kernel series), you will pass through systems without LTS: 14.04.2, 14.04.3, 14.04.4 with the utopic, vivid, wily kernels. 14.04.5 LTS will get the xenial kernel series, which again will have LTS.

See this link: [LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by TheFu on 2016-03-03
According to the man page for apt-get

>        upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.


>        dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The dist-upgrade
           command may therefore remove some packages. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages.


So - use **upgrade** and you'll get patches for the installed kernel, but not newer kernels (which would break the LTS standing).  [s]**dist-upgrade** is what migrates from 3.13.x to 3.16.y to 3.19.z kernels - WE DON'T WANT THAT.[/s]  My mistake.

BTW, no need to run both **upgrade** and **dist-upgrade** options.  dist-upgrade **alone** does an upgrade **plus** all the other things.

According to the manpage - and this is how it works and has been working for a very long time on all my Ubuntu servers.  Running dist-upgrade is *mostly safe*, but running just upgrade is **very safe**.  Aptitude uses the "safe-upgrade" option like plain "upgrade".  "full-upgrade" is like dist-upgrade in apt-get.

[https://askubuntu.com/questions/221/how-to-force-installation-of-kernel-updates-when-using-apt-get-upgrade](https://askubuntu.com/questions/221/how-to-force-installation-of-kernel-updates-when-using-apt-get-upgrade) has more on this question.

---

### Post by v3.xx on 2016-03-03
> **sudodus said:**
> I think it works like this:

2. If you ***update && dist-upgrade*** from 14.04.1 LTS you get kernel upgrades within the trusty series, 3.13. The output of ***lsb_release -a*** will be upgraded to new point releases, but the hardware enablement stack and the kernel series will not be upgraded. This is also what is done by the automatic updating system of the desktop flavours of Ubuntu (I'm not sure about the server version). ***I would recommend this method***, and I ***think*** it will stay within the supported packages. ***[COLOR="#0000FF"]I would welcome other people to comment on this issue[/COLOR]*** :-)

This is the way it works on my box.

---

### Post by nargaroth_reg on 2016-03-03
> **v3.xx said:**
> This is the way it works on my box.
On mine too, I always automatically update using dist-upgrade and I always get point release updates for the 3.13 kernel, not the kernels from the newer releases, which is what I want since all my hardware works with it. Originally I installed 14.04.1, as sudodus' post explains.

---

### Post by grahammechanical on 2016-03-03
The Ubuntu 14.04.1 that is now 14.04.4, what Linux kernel does it have?

```
uname -a
```

You may find that it is the 14.04.1 kernel.

If your company buys new hardware you may need the latest Linux kernels and hardware modules. So, install the latest Ubuntu 14.04 from the Ubuntu web site. That is at present 14.04.4.

Regards.

---

### Post by kansasnoob on 2016-03-04
> **nargaroth_reg said:**
> On mine too, I always automatically update using dist-upgrade and I always get point release updates for the 3.13 kernel, not the kernels from the newer releases, which is what I want since all my hardware works with it. Originally I installed 14.04.1, as sudodus' post explains.

Me three .......... or is that four :D

Running apt-get dist-upgrade will NOT upgrade the kernel series. If you install using either the 14.04 or 14.04.1 media you'll remain on the original 3.13 series kernel and X-stack which are supported continuously throughout Trusty EOL in 2019 unless the user foolishly chooses to manually upgrade to a newer HWE stack:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

When the package 'base-files' is upgraded it changes the release info and nothing else:

> base-files (7.2ubuntu5.4) trusty; urgency=medium

  * /etc/issue, /etc/issue.net, /etc/lsb-release, /etc/os-release: [B]Bump
    version number to 14.04.4 in preparation for the point release.[/B]

 -- Adam Conrad <adconrad@ubuntu.com>  Tue, 16 Feb 2016 09:29:13 -0700

base-files (7.2ubuntu5.3) trusty; urgency=medium

  * /etc/issue, /etc/issue.net, /etc/lsb-release, /etc/os-release: [B]Bump
    version number to 14.04.3 in preparation for the point release.[/B]

 -- Adam Conrad <adconrad@ubuntu.com>  Mon, 03 Aug 2015 10:39:14 -0600

base-files (7.2ubuntu5.2) trusty; urgency=medium

  * /etc/issue, /etc/issue.net, /etc/lsb-release, /etc/os-release: [B]Bump
    version number to 14.04.2 in preparation for the point release.[/B]

 -- Adam Conrad <adconrad@ubuntu.com>  Tue, 03 Feb 2015 02:06:57 -0700

base-files (7.2ubuntu5.1) trusty; urgency=medium

  * /etc/issue, /etc/issue.net, /etc/lsb-release, /etc/os-release: [B]Bump
    version number to 14.04.1 in preparation for the point release.
[/B]
 -- Adam Conrad <adconrad@ubuntu.com>  Tue, 22 Jul 2014 09:22:44 -0600

base-files (7.2ubuntu5) trusty; urgency=medium

  * /etc/issue{,.net}, /etc/{lsb,os}-release: Prepare for **14.04 LTS release**.

 -- Matthias Klose <doko@ubuntu.com>  Thu, 10 Apr 2014 23:58:33 +0200

---

### Post by mikodo on 2016-03-04
Hi,

I have never used the [HWE Stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") but, have read reports of using it, can be a venture fraught with peril.

Why, I dunno.

---

### Post by tom-bellas3rd on 2016-03-05
I can't find any documentation that states 14.04.4 is only 9 months of support. Everything I read states its part of the 5 year LTS package.

---

### Post by Bucky Ball on 2016-03-05
[Try this]("https://wiki.ubuntu.com/Releases"). Hasn't got 14.04.4 up there yet, but you get the picture.

---

### Post by tom-bellas3rd on 2016-03-05
Ah thank you. Now I understand.  :)

---

### Post by Bucky Ball on 2016-03-05
I *think* it will stop at the .5 release and that will be supported throughout. I think. ;)

---

### Post by kansasnoob on 2016-03-05
> **Bucky Ball said:**
> I *think* it will stop at the .5 release and that will be supported throughout. I think. ;)

Correct, only those who installed using the 14.04.2, 14.04.3, and 14.04.4 media will be effected by HWE EOL in August, at which time they'll be prompted by the software updater to do an HWE upgrade to the Xenial HWE-stack. I hope it goes smoother than it did in Precise.

---

### Post by night_sky2 on 2016-03-06
> **tatonqek said:**
> I understand that 14.04 and 14.04.1 have full support through 2019. I made a fresh install using a 14.04.1 ISO, and started the Software Updater. After it finished and restarted, **I discovered that Ubuntu was version 14.04.4, which only has 6 months of support.**

Not at all.

The_ kerne_l (v4.2) shipped with Ubuntu 14.04.04 is only supported 6 months. But that's actually a good thing IMO. Kernel updates can be a cause of instability on some systems so better no updating it more than it should or even not at all (like Mint does). The LTS release still ensure maintenance of essential packages and apps for security and improvement purposes until 2019.

---

### Post by mc4man on 2016-03-06
Post # 4 is correct. To put simply lts kernel & mesa packages are *not upgrades* to 14.04/14.04.1 release packages so no upgrade command can ever install them.

---

### Post by ChuangTzu on 2016-03-07
In general if you want LTS then only do apt-get update and apt-get upgrade or aptitude update, aptitude upgrade (of course you would need to install aptitude for that).  Only use dist-upgrade if you are upgrading to the next dist. release or forward release.  So dist-upgrade is suitable for those on the 6 month plan or you are upgrading to the next LTS, but once on LTS then only do the reg. apt-get update and apt-get upgrade.    Hope that helps.  :)

---

### Post by QIII on 2016-03-07
dist-upgrade does not upgrade to the next release.  It upgrades packages in the current release.

do-release-upgrade upgrades to the next release.

---

### Post by ChuangTzu on 2016-03-07
> **QIII said:**
> dist-upgrade does not upgrade to the next release.  It upgrades packages in the current release.  do-release-upgrade upgrades to the next release.  You are correct....That was Debian slipping through.  :)

---

### Post by QIII on 2016-03-07
Typically, dist-upgrade works the same way in Debian.

There, dist-upgrade only moves to the next release if you have modified your sources accordingly.  The same holds true for Ubuntu -- in fact that is how many of us upgrade to the development release at the start of a new cycle:  replace the old version with the new in sources and dist-upgrade.

---

### Post by QDR06VV9 on 2016-03-07
> **qiii said:**
> typically, dist-upgrade works the same way in debian.

There, dist-upgrade only moves to the next release if you have modified your sources accordingly.  The same holds true for ubuntu -- **in fact that is how many of us upgrade to the development release at the start of a new cycle:  Replace the old version with the new in sources and dist-upgrade**.
+2 :d

---

