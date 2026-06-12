---
title: "My grandma is still on Lubuntu 18.04 until COVID-19 lockdown is lifted"
date: 2021-04-01
forum: Ubuntu, Linux and OS Chat
---

### Post by salamilimos on 2021-04-01
I'm maintaining my grandma's old laptop and I've installed Lubuntu 18.04 on it back in 2018, but now, due to the COVID-19 lockdown, I cannot go out and visit her and upgrade her laptop, so what are the dangers of her using Lubuntu 18.04 past it's EOL which is this month.

She uses the laptop for Facebook, Gmail and YouTube.

---

### Post by CelticWarrior on 2021-04-01
EoL system should be upgraded, let me start with this is case what I'm going to say next is misinterpreted.

The risks are minimal.
LTS releases have a 5 years support cycle which is reduced to only 3 for flavors like Lubuntu. This means that Lubuntu desktop specific packages won't be updated/patched after its EoL that you correctly identified. However, the common Ubuntu core will still get updates and arguably the potential exploits are in it rather in the desktop specific part but is conceivable that things can go wrong with Lubuntu specific things as well.

Please keep in mind I'm NOT a security expert, very far from it. If a true expert replies here saying that what I posted is rubbish, please ignore me and listen to them.

---

### Post by salamilimos on 2021-04-01
Thanks for this answer. In my case I have no choice since I cannot visit my grandma right now and with the cases of COVID-19 going up in my country, I might not be able to visit my grandma until next year.

---

### Post by CatKiller on 2021-04-01
I'm not a security expert, either, but I agree with CelticWarrior.

It's all the same software from the same repositories. The base bits - kernel, drivers, libraries, and so on - are maintained by Canonical, and they'll provide security updates and bugfixes for the five years. The Lubuntu-specific bits (and equivalents for the other flavours) are maintained by the Lubuntu team, which is way smaller and doesn't have the resources to maintain multiple releases for an extended period. 

There's a command you can use, which I can't remember, to see which parts have support for how long. 

As long as your grandmother is installing all the security updates that come down the pipe, you should be fine. Obviously keep an eye out for any problems that are specific to LXDE and reconsider if any crop up. Upgrade when you get the chance.

---

### Post by guiverc on 2021-04-01
I agree with what's already been provided.

I think `ubuntu-support-status` is the command @CatKiller couldn't recall; `ubuntu-security-status` for later releases, both of which (for appropriate releases) can be used to see what is still supported, what isn't supported etc.

I'd evaluate the decision on what applications are being used.  My guess is the primary program being used is a browser; so I'd recommend for sure using a supported browser eg. [https://packages.ubuntu.com/bionic-updates/firefox](https://packages.ubuntu.com/bionic-updates/firefox) which you'll note isn't a Lubuntu specific package thus will be supported beyond just this month (being a 'main' repository package)
[I]

I have Lubuntu 18.04 LTS on a couple of systems here, and I'm not in any  hurry yet to upgrade them. Likely significant though; they aren't my primary  boxes (this box is and it's running *hirsute* and it'll be likely next to upgrade), but some of my 18.04 boxes are x86/i386 only so can't upgrade to a supported release (as 19.04 was last for i386), so for me it'll likely be switching to Debian.[/I]

---

### Post by salamilimos on 2021-04-02
> **guiverc said:**
> I agree with what's already been provided.

I think `ubuntu-support-status` is the command @CatKiller couldn't recall; `ubuntu-security-status` for later releases, both of which (for appropriate releases) can be used to see what is still supported, what isn't supported etc.

I'd evaluate the decision on what applications are being used.  My guess is the primary program being used is a browser; so I'd recommend for sure using a supported browser eg. [https://packages.ubuntu.com/bionic-updates/firefox](https://packages.ubuntu.com/bionic-updates/firefox) which you'll note isn't a Lubuntu specific package thus will be supported beyond just this month (being a 'main' repository package)

Yes, my grandma is using Firefox. Everything she needs was installed by default already. All I did was configure everything for her, like larger fonts on both system and Firefox because of her poor eyesight.

*> **guiverc said:**
> I have Lubuntu 18.04 LTS on a couple of systems here, and I'm not in any  hurry yet to upgrade them. Likely significant though; they aren't my primary  boxes (this box is and it's running [I]hirsute* and it'll be likely next to upgrade), but some of my 18.04 boxes are x86/i386 only so can't upgrade to a supported release (as 19.04 was last for i386), so for me it'll likely be switching to Debian.[/I]

Thanks for the info, and damn, my grandma's laptop is 32-bit only too, so I can't upgrade her at all. I have no experience with Debian and I heard it's harder to maintain and configure and I heard that Linus Torvalds had a hard time installing Debian himself. Is Debian grandparent friendly?

---

### Post by CatKiller on 2021-04-02
> **salamilimos said:**
> damn, my grandma's laptop is 32-bit only too
It's worth checking that it's *actually* 32-bit, and not just "came with 32-bit Windows." Early 64-bit Windows versions were terrible, so 64-bit hardware came with 32-bit Windows for a long time.

---

### Post by salamilimos on 2021-04-02
> **CatKiller said:**
> It's worth checking that it's *actually* 32-bit, and not just "came with 32-bit Windows." Early 64-bit Windows versions were terrible, so 64-bit hardware came with 32-bit Windows for a long time.

Yes, I've checked it, it is 32-bit only.

---

### Post by Irihapeti on 2021-04-02
I had Debian on an old 32-bit EeePC until very recently. I have a rather peculiar way of installing, so I can't really comment about the inherent difficulty, but once it's set up, it chugs along like any other distro. A suggestion is that you try Debian in a VM and see for yourself.

I suspect that a good deal is going to depend on the actual hardware involved. If it's something that's fairly mainstream, I would think that the install process is going to be relatively painless. The fun starts when you have some unusual piece of hardware and have to go looking for drivers and obscure configurations.

---

### Post by guiverc on 2021-04-02
> **salamilimos said:**
> Yes, my grandma is using Firefox. Everything she needs was installed by default already.  ...

.. Thanks for the info, and damn, my grandma's laptop is 32-bit only too, so I can't upgrade her at all. I have no experience with Debian and I heard it's harder to maintain and configure and I heard that Linus Torvalds had a hard time installing Debian himself. Is Debian grandparent friendly?

If you were using Ubuntu 18.04 Desktop, everything that comes by default comes with 5 years of support, as they include only packages from 'main'.

All the Lubuntu specific packages are from 'universe' where 3 years is full-life for a LTS release; so note it's only because `firefox` is also provided with Ubuntu Desktop that it has longer support (ie. a package Lubuntu uses from main Ubuntu Desktop).  For details on repositories you can see [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

As for Debian, I tend to think of Ubuntu and Debian as being ~identical in almost every way. I use both and switch from one to the other ignoring which I'm using as I do see them as both the same for all practical purposes (*I started as a Debian user though; maybe significant*)

I'll note the following differences though

- Ubuntu and Debian release at different times, so they never perfectly align, and using Debian packages on a Ubuntu system, or Ubuntu intended packages on a Debian system involves risk and thus should be avoided; just as using a package built for one release (eg. trusty or 14.04) in another system (eg. bionic or 18.04).

- Repositories have different names, but so what (eg. 'universe' in Ubuntu is 'contrib' in Debian), and other superficial issues that can *trip* up a newbie

- Kernel modules (drivers) are easier in Ubuntu, as there are extra tools provided in Ubuntu systems like `ubuntu-drivers` but most of my hardware doesn't require this anyway; I do usually use the *non-free* Debian ISOs (Debian defaults to '*free*' only, Ubuntu includes '*non-free*' by default requiring you to purposely select '*free*' only).  FYI: I think it's the *free/non-free* that catches most users; many not even realizing Ubuntu has a 'free' install option, and some Debian users using '*free*' media expecting it to be like a Ubuntu (with *non-free* as default)

I've probably confused you, but '*free as in freedom, not as in free beer*'.

*free* = all free software, fully open-source
non-free = no $cost to use but no source code provided (binaries only available), no freedom to modify, reverse-engineer it etc.

I do see Debian as equally *grandparent* friendly as Ubuntu.

FYI: if I have a system I tend to know I'll ignore and thus it'll fall behind in upgrades.. I tend to opt for Debian as I've generally found it easier to bring up to date than Ubuntu (*but that could just be how I use the two*)

---

### Post by grahammechanical on 2021-04-03
Debian will provide an ISO image that installs the LXDE desktop environment that Lubuntu 18.04 uses. I recently wanted to install 32 bit Debian as a trial to see how long support of 32 bit continued. I had great difficulty getting Ubuntu to burn the ISO image to USB memory stick. USB Creator would not recognise the Debian ISO image as an ISO to be burnt. You might want to install MKUSB. That had the skill to overcome the problem.

[https://cdimage.debian.org/debian-cd/current-live/i386/bt-hybrid/](https://cdimage.debian.org/debian-cd/current-live/i386/bt-hybrid/)

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Regards

---

### Post by drewhowden on 2021-04-09
Is it possible for you to call your grandma and walk her through the process of upgrading to Lubuntu 20.04?

It's really as simple as opening up a terminal, typing "do-release-upgrade", and following the on-screen prompts (for people who are unaware).

---

### Post by guiverc on 2021-04-09
> **drewhowden said:**
> Is it possible for you to call your grandma and walk her through the process of upgrading to Lubuntu 20.04?

It's really as simple as opening up a terminal, typing "do-release-upgrade", and following the on-screen prompts (for people who are unaware).

I would advise against that.

From my understanding of the prior threads, it won't work due to i386 nature of the box... but if if it does, I'd still advise against it.

In the [Lubuntu 20.04 LTS release notes]("https://lubuntu.me/focal-2-released/") (in fact all releases notes since 18.10) you'll read the following


> ***Note***, due to the extensive changes required  for the shift in desktop environments, the Lubuntu team does not support  upgrading from 18.04 or below to any greater release. Doing so will  result in a broken system. If you are on 18.04 or below and would like  to upgrade, please do a fresh install. 

That's there for a reason... the result of upgrade will leave some LXDE parts that no longer function, meaning menu items that go nowhere & nothing happens... These aren't a problem with a knowledgeable user, or a user who is capable of modifying and removing those *dangling* pointers in files, but for a non-technical user it's not a good experience & reduces confidence and user experience.

My own box was upgraded that way so yes it'll work, but I'm not worried by such things, understand why and can easily skip over it (I also have clean install boxes to copy what should be there from should it really worry me; though a user could copy it from a VM, again this isn't end-user/newbie level tasks).

I followed the Lubuntu documentation on fixing many of these problems, but those guidelines were written for the *bionic* to *cosmic* upgrade cycle and were never updated, as users still reported issues in testing, so the upgrade never got officially supported (*the documentation isn't published anywhere except existing in raw format on the Lubuntu phab infrastructure*; *I've made reference to it many times, but it's not easy to find*)...  It took me time for *fix* my box; and I'd not suggest it for non-technical users, even though some have actually reported pretty good results (*they just ignore the issues once they ask for support & realize why & that we don't support that*). Result however vary depending on what packages & changes the user made post-install...

---

