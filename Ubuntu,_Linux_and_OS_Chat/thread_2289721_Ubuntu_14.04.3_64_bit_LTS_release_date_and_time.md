---
title: "Ubuntu 14.04.3 64 bit LTS release date and time?"
date: 2015-08-06
forum: Ubuntu, Linux and OS Chat
---

### Post by Welly Wu on 2015-08-06
I know that Canonical will release Ubuntu 14.04.3 64 bit LTS GNU/Linux today on August 6th, 2015. However, what time will it be released? Does anyone here know when it will become available today? Thanks.

---

### Post by PaulW2U on 2015-08-06
*Thread moved to **Ubuntu, Linux and OS Chat**.*

As I type this I'm looking at one of the IRC channels where the release managers are discussing various bugs and fixes. There are at least two Ubuntu flavours that are not ready to release as more testing may be required.

Occasionally Canonical do set a release time, Ubuntu 10.10  springs to mind but usually it's a case of **it'll be released when it's ready**. :)

---

### Post by vasa1 on 2015-08-06
```
09:24 PM ~ $ cat /etc/os-release | grep VERSION=
VERSION="14.04.3 LTS, Trusty Tahr"
09:24 PM ~ $ 

```
Looks like I got it already?

---

### Post by PaulW2U on 2015-08-06
> **vasa1 said:**
> ```
09:24 PM ~ $ cat /etc/os-release | grep VERSION=
VERSION="14.04.3 LTS, Trusty Tahr"
09:24 PM ~ $ 

```
Looks like I got it already?

vasa1, what you have posted is the contents of a file that has been updated in preparation for the new point release.

Until the Release Manager issues an email to various official mailing lists then Ubuntu 14.04.3 has **not** been released.

---

### Post by vasa1 on 2015-08-06
> **PaulW2U said:**
> vasa1, what you have posted is the contents of a file that has been updated in preparation for the new point release.

Until the Release Manager issues an email to various official mailing lists then Ubuntu 14.04.3 has **not** been released.
Okay! I was hoping that the Lubuntu devs were ahead of the pack ;)

---

### Post by Welly Wu on 2015-08-06
I too already got Ubuntu 14.04.3 64 bit LTS GNU/Linux, but I'm having a problem installing the latest hardware enablement stack on my ZaReason Zeto desktop PC. I created a thread in the general support forum. Please take a look at it and help me out over there. Thank you.

---

### Post by Welly Wu on 2015-08-06
Does this mean that the new LTS hardware enablement stack is not yet available? I just installed it on my roommate's ASUS K50IJ notebook PC successfully. What gives?

---

### Post by PaulW2U on 2015-08-06
Welly Wu, what I am saying is that although you have what **you** think might be released as Ubuntu 14.04.3, I can 100% confirm that it has not yet been officially released. 

You may well have downloaded what will be 14.04.3 but until the Release Manager has had confirmation from **all** of the Ubuntu flavours that their versions are ready then the official announcement of the release will not be sent.

---

### Post by Welly Wu on 2015-08-06
Can someone take a look at my support thread and help me: [http://ubuntuforums.org/showthread.php?t=2289730](http://ubuntuforums.org/showthread.php?t=2289730)

---

### Post by QIII on 2015-08-06
Patience please, Welly Wu.  Your support request will be answered in due time -- along with the questions of thousands of others.

---

### Post by monkeybrain20122 on 2015-08-06
If your OS is working now don't get the hardware enablement stack, at least make an image of your current OS before you do. I think it creates more problems than it solved for users who are already running the OS happily.

---

### Post by Min_Jia on 2015-08-06
Are we expecting the official release of LTS 14.04.3? I saw someone in this forum already installed 14.04.3, however the main website still shows 14.04.2 as the latest. Anyone could confirm that today is the schedule release date for 14.04.3?

---

### Post by howefield on 2015-08-06
Threads merged.

Yes, today is scheduled day for 14.04.3 release.

---

### Post by Min_Jia on 2015-08-06
> **howefield said:**
> Threads merged.

Yes, today is scheduled day for 14.04.3 release.

Thanks for your confirmation. I am waiting for it to dual boot with Win 10. I plan to use Ubuntu as my main OS for everything, and switch to Win10 only when I need MS Office, Acrobat and maybe Adobe Photoshop..

---

### Post by howefield on 2015-08-06
It is out now, go knock yourself out :)

---

### Post by rattskjelke on 2015-08-06
I had Xubuntu 14.04.2 until two days ago when I did my usual update (every few days) I noticed it replaced *lsb-release*. 

Now if I do "*cat /etc/lsb-release*" I get:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"

It didn't even ask if I wanted to upgrade to a new version. The Xubuntu download page still shows 14.04.2.

---

### Post by Min_Jia on 2015-08-06
> **howefield said:**
> It is out now, go knock yourself out :)

LOL, thanks mate.. Downloading now.

---

### Post by howefield on 2015-08-06
> **rattskjelke said:**
> I had Xubuntu 14.04.2 until two days ago when I did my usual update (every few days) I noticed it replaced *lsb-release*. 

Now if I do "*cat /etc/lsb-release*" I get:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"

It didn't even ask if I wanted to upgrade to a new version. The Xubuntu download page still shows 14.04.2.

Your file has been updated in advance of the "release".

By updating your system in the usual manner you will automatically go to 14.04.3 - keep on updating and you will end up on 14.04.4 ect, ect. This release is merely 14.04 rolled up with all the updates since the original release to save downloading 14.04 and then a boat load of updates. 14.04.3 includes a hardware enablement stack which mainly benefits new installations/hardware with updated kernel and X support. If you are already on 14.04.x it's no big deal.

---

### Post by PaulW2U on 2015-08-06
And the official announcement:

[Ubuntu 14.04.3 LTS released]("https://lists.ubuntu.com/archives/ubuntu-release/2015-August/003338.html")

So the flavour sites should now start updating if they haven't done already.

---

