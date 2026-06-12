---
title: "Where is 12.04.3?"
date: 2013-08-23
forum: Ubuntu, Linux and OS Chat
---

### Post by jadedcyborg on 2013-08-23
Okay so according to the release schedule 12.04.3 should have been released with the 13.04 HWE stack yesterday, but still I can't find it anywhere. Is there any particular reason that it hasn't been released yet?

---

### Post by PaulW2U on 2013-08-23
I don't know why it hasn't been released but: 

[https://lists.ubuntu.com/archives/ubuntu-release/2013-August/002489.html](https://lists.ubuntu.com/archives/ubuntu-release/2013-August/002489.html)

suggests that you should see it released some time today.

---

### Post by grahammechanical on 2013-08-23
> The 12.04.3 point release is set to release this Thurs, Aug 22.  I  am hearing rumors there may be a small slip, ie 1 day slip, but it  should
 be going out this week.  We are not aware of any critical issues at this time that would warrant any respins.

So, Ubuntu fails yet again!

[URL="http://voices.canonical.com/kernelteam/2013/08/20/kernel-team-meeting-minutes-august-20-2013/"]http://voices.canonical.com/kernelteam/2013/08/20/kernel-team-meeting-minutes-august-20-2013/


[/URL]

---

### Post by TiloBunt on 2013-08-23
I'm also waiting for the iso download of 12.04.3 
btw my desktop and server already shows "Description:    Ubuntu 12.04.3 LTS"

```

tilo@wiki2:~$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:        12.04
Codename:       precise
tilo@wiki2:~$ uname -a
Linux wiki2 3.5.0-37-generic #58~precise1-Ubuntu SMP Wed Jul 10 17:48:11 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
tilo@wiki2:~$

```

---

### Post by OrangeCrate on 2013-08-23
No worries, NORAD is tracking it's progress. It's over Angola right now...

---

### Post by vNa5h on 2013-08-23
> **OrangeCrate said:**
> No worries, NORAD is tracking it's progress. It's over Angola right now...

??

---

### Post by deadflowr on 2013-08-23
It's buried in the end zone of Giants Stadium, next to Jimmy Hoffa.

---

### Post by OrangeCrate on 2013-08-23
> **vNa5h said:**
> ??

NORAD tracks Santa Claus on Christmas eve.

[http://www.noradsanta.org/](http://www.noradsanta.org/)

If you have 12.04.2, and you've been updating regularly, you will have 12.04.3 without doing anything. It's not a separate release, it's just a snapshot to disk to include all of the updates to that point.

Type this at the terminal to check which version you have, keep checking occasionally, to see when you have the .3 release.

```
lsb_release -a
```

Don't lose any sleep over whether they're to the minute with the release to disk (for new installs) or not.

---

### Post by Ikaru on 2013-08-23
> **OrangeCrate said:**
> 

If you have 12.04.2, and you've been updating regularly, you will have 12.04.3 without doing anything. It's not a separate release, it's just a snapshot to disk to include all of the updates to that point.

That's right. I always update my system so I already have ubuntu 12.04.3 and so should everybody who updated recently.

---

### Post by oldfred on 2013-08-23
I still have the original 12.04 and never did the upgrade to 12.04.2. I never checked before on version, but my kernel is still 3.2.0 series and now it says I have 12.04.3, but not new kernel. Kernel was updated today.

fred@fred-Precise:~$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"
NAME="Ubuntu"
VERSION="12.04.3 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.3 LTS)"
VERSION_ID="12.04"

fred@fred-Precise:~$  uname -a
Linux fred-Precise 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:01:03 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by deadflowr on 2013-08-23
Hey oldfred, if you installed from Ubuntu 12.04 and not from later point releases and have continuously updated you'll stay on the original kernel and x stack.
If you installed a newer downloaded image, you'll get the newer kernel and x stack.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
This is for 12.04.2, but should hold true for what happens during a point release.
Look at the section for LTS hardware enablement stack.

---

### Post by OrangeCrate on 2013-08-23
Post removed for ungrateful response.

---

### Post by OrangeCrate on 2013-08-23
Ditto.

---

### Post by TiloBunt on 2013-08-23
[QUOTE=oldfred;12766901]


12.04 has a  kernel hardware enablement option  [http://askubuntu.com/questions/248914/what-is-hwe-hardware-enablement](http://askubuntu.com/questions/248914/what-is-hwe-hardware-enablement) 
if you want to can get to 3.5 or now to 3.8 kernel. check Ubuntu FAW on HWE here [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

btw 12.04.3 iso is now available at [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by oldfred on 2013-08-23
I know I can upgrade kernel, just I have not (yet).
Local mirror I use to download from does not yet show 12.04.3, but I expect it soon.

---

### Post by buzzingrobot on 2013-08-23
Setting specific dates for software release months in advance is silly, but missing such a date isn't failure.  Announce a target timeframe, then set the real date a week or two out.

---

### Post by monkeybrain20122 on 2013-08-23
It has arrived, am downloading right now.

---

### Post by tdockery97 on 2013-08-23
Got it, installed it, and it runs flawlessly.:D

---

### Post by craig10x on 2013-08-24
Just curious...but does 12.04.3 have all the unity improvements one finds on 13.04?
Also, if one runs an LTS release, can you upgrade to each new point release without re-installing?

---

### Post by PaulW2U on 2013-08-24
> **craig10x said:**
> Just curious...but does 12.04.3 have all the unity improvements one finds on 13.04?

No, the Unity version remains the same.

> **craig10x said:**
> Also, if one runs an LTS release, can you upgrade to each new point release without re-installing?

Yes. By accepting all updates you're automatically upgraded to 12.04.3. To check run the following command in a terminal window:

```
lsb_release -a
```

The same will apply to 12.04.4 and 12.04.5 in due course.

---

### Post by craig10x on 2013-08-24
Thanks Paul....love your avatar by the way...always liked the flintstones :D
I'm currently running 13.04 and will likely upgrade to 13.10 as well but starting with 14.04 i am considering going LTS to LTS and was just curious how it works...

---

### Post by nenadlatinovic on 2013-08-24
.3 arrived sometime yesterday, it seems.

---

### Post by monkeybrain20122 on 2013-08-24
> **craig10x said:**
> Thanks Paul....love your avatar by the way...always liked the flintstones :D
I'm currently running 13.04 and will likely upgrade to 13.10 as well but starting with 14.04 i am considering going LTS to LTS and was just curious how it works...

I am running 13.04 as my main system right now. But I have 12.04 on an external hard drive and setup in pretty much similar way as a portable and also as a fallback in case 13.10 is messy because of Mir. :) I have explored different options in case Mir breaks my system: Fedora, Debian SID, Manjaro Linux, Both Fedora and Manjaro are good (especially Fedora, which in some ways is better than Ubuntu IMO) Manjaro is based on Arch, feel very fast and clean and is rolling,  a  big problem is some non open software are packaged only as .deb and rpm, I have no idea how to install those in Manjaro since there is no source to compile (Chrome, e.g, It seems that it is in ARCH's repo and can be installed that way, but haven't figured out how yet). I will continue to use them seriously as well (Debian is just for testing and comparison, too unstable), but as a drop in replacement for 13.04 nothing is closer than 12.04 (I have the latest kernel and software through ppa as well as some Unity bug fixes, so in a way it is pretty much the same as 13.04 as I turn off all the online search anyway)

---

### Post by craig10x on 2013-08-24
Hmmm....thanks for that feedback, monkeybrain2012 :)

Well, let's see...with the same kernel as 13.04 has now (in the 12.04.3) and you say unity is pretty much on par with 13.04 with the updates to it you have gotten (and i turn off the shopping search too)...then i might want to consider installing it to replace 13.04 and then go straight to 14.04 (using an upgrade) when that comes out....thus bypassing 13.10 altogether...interesting possibility for me to "ponder"....i probably should download it and run it live to check it out ;)

---

### Post by monkeybrain20122 on 2013-08-24
> **craig10x said:**
> Hmmm....thanks for that feedback, monkeybrain2012 :)

Well, let's see...with the same kernel as 13.04 has now (in the 12.04.3) and you say unity is pretty much on par with 13.04 with the updates to it you have gotten;)

My kernel is newer than the stock kernel in 13.04. I put kernel 3.10.7 on it, that is more ahead of 3.8x for 13.04. There is no obvious advantage, but just want to see if it can be done. (I of course also put 3.10.7 on 13.04, again doesn't seem to have  any obvious advantage but doesn't break anything either, I heard the newest Nvidia driver needs kernel 3.9+, but I can't confirm that this is the case)

There are a few Unity bugs in 12.04 (most important for me is scale). You can get the fixes by finding the relevant ppa(s) here 
[https://launchpad.net/~mc3man](https://launchpad.net/~mc3man) There are also some workarounds for a few other things using docnf editor.  So after these tweaks Unity is pretty much on par. 

After installing 12.04.3 I have only one problem, which is that logout takes a full minute (not kernel related, I tested it with different kernels), but since I usually just poweroff or reboot this is not a show stopping issue for me. Still trying to figure out why.

---

### Post by craig10x on 2013-08-24
I'm still a bit confused though...from what i have been reading i get the impression that even with all the normal updates, you would not have everything that the newest point release iso contains (for example: the upgrade to the kernel that 13.04 has)....if that is the case, i was wondering, in the LTS does you Software Updater tell you there is a new point release available and give you the option to upgrade to it?
Or must you run the actual live iso and ask it to upgrade you to the new version?

---

### Post by monkeybrain20122 on 2013-08-25
> **craig10x said:**
> I'm still a bit confused though...from what i have been reading i get the impression that even with all the normal updates, you would not have everything that the newest point release iso contains (for example: the upgrade to the kernel that 13.04 has)....if that is the case, i was wondering, in the LTS does you Software Updater tell you there is a new point release available and give you the option to upgrade to it?
Or must you run the actual live iso and ask it to upgrade you to the new version?

I think normally you just do your daily upgrading (via update manager or synaptic) then you arrive at the latest point release (say going from 12.04.1 to 12.04.2), I don't think there is any special notification from update manager, though I cannot be sure because I always turn it off,I prefer to manually check and install update with synaptic.  But something is different about 12.04.3 as it is the first time they actually upgrade some core stuffs to the latest release for a LTR, so from what I understand there are actually two 12.04.3 around, the version that resulted from clean installation and the version that resulted from upgrading/updating 12.04.2. My understanding is that the clean install version has newer kernel and graphic stack backported from raring but the upgraded/updated version doesn't (not sure about kernel, but graphic stack doesn't change). It is easy to install or remove kernels but I am not sure if you can switch graphic stack between the two versions. This is my understanding.

Edited: Oh now I remember something, I have a $10 usb wifi card which doesn't work with kernel 3.2 from 12.04 without messing with some conf files but in 12.10 it just works because the module was experimental in 3.2 and was turned off by default, so if I am to use this it will just work in 12.04.3 as well if it is the one with kernel 3.8.

---

### Post by craig10x on 2013-08-25
Thanks...i thought perhaps it lets you upgrade through the software manager and get the new kernel, graphic stack, etc like the new iso release has...
Or is there a command you can enter in the terminal that brings it all in?

Anyone know?

---

### Post by mastablasta on 2013-08-25
same old 3.2 kernel but says 12.04.3
heh...

i am wondering if my sound issues would have been resolved in new kernel or are they made worse.

---

### Post by deadflowr on 2013-08-25
> **craig10x said:**
> Thanks...i thought perhaps it lets you upgrade through the software manager and get the new kernel, graphic stack, etc like the new iso release has...
Or is there a command you can enter in the terminal that brings it all in?

Anyone know?

Here ya go
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

The one thing I've never been sure about is how long the LTS-otherdistrostuffs are supported for Precise.
I know the 3.2 kernel series will be supported for the whole five years, but how long do the others get?

Somewhere I thought it was mentioned that they only get support for the duration of the distro version the are from/named for.
But I really don't know.

---

### Post by craig10x on 2013-08-25
Thank you deadflowr...that linked page really explains it very well...
Must be a blue moon...you were very helpful :D he he...

I have a feeling i will just stay with 13.04 then...upgrade to 13.10, to 14.04, etc...
If only ubuntu had a rolling release....sigh (i don't mean the unofficial ubuntu development rolling release)...

---

### Post by tagadabaw on 2013-09-04
> **oldfred said:**
> I still have the original 12.04 and never did the upgrade to 12.04.2. I never checked before on version, but my kernel is still 3.2.0 series and now it says I have 12.04.3, but not new kernel. Kernel was updated today.

fred@fred-Precise:~$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"
NAME="Ubuntu"
VERSION="12.04.3 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.3 LTS)"
VERSION_ID="12.04"

fred@fred-Precise:~$  uname -a
Linux fred-Precise 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:01:03 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Same with me.
Welcome message in SSH login:
Welcome to Ubuntu 12.04.3 LTS (GNU/Linux 3.2.0-53-generic x86_64)
lsb_release -a:
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise

uname -a
inux XXXXXXXX 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:01:03 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by buzzingrobot on 2013-09-04
I believe you will need to explicitly upgrade.  See here: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

