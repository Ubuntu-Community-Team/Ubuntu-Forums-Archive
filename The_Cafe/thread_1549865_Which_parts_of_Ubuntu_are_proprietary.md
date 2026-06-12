---
title: "Which parts of Ubuntu are proprietary?"
date: 2010-08-10
forum: The Cafe
---

### Post by JailHouseRock on 2010-08-10
As I was randomly nosing around on Wikipedia I discovered that Launchpad as well as the Ubuntu One are proprietary, which kind of shocked me and made me wonder what else in and surrounding Ubuntu is proprietary. 

I know that Ubuntu contains ATI and NVIDIA drivers by default, but I couldn't find any list of what proprietary software Ubuntu contains by default.

And even though I don't mind using things like ubuntu-restricted-extras since I am the one agreeing on the terms of use. But it also makes me wonder what proprietary software can be found in the default repositories. 

I'm sorry if this is a stupid question, but I really couldn't find it anywhere.

---

### Post by phrostbyte on 2010-08-10
Launchpad isn't anymore.

There may be some proprietary hardware firmware on the CD. And there is plenty more where that can from in the repository usually in the "restricted" or "multiverse" repos.

---

### Post by LowSky on 2010-08-10
Just take a step back and realize the even open-source software can have restrictions to use as well, all depending on the license it is created under.

---

### Post by JailHouseRock on 2010-08-10
> **phrostbyte said:**
> Launchpad isn't anymore.

There may be some proprietary hardware firmware on the CD. And there is plenty more where that can from in the repository usually in the "restricted" or "multiverse" repos.

Good to hear about Launchpad, I wasn't aware of that.

> **LowSky said:**
> Just take a step back and realize the even open-source software can have restrictions to use as well, all depending on the license it is created under.

I know that, but since those are licenses I can agree on I have no problem with them. 

And I just want to inform myself here because it's an interesting subject. I haven't been able to find a source that will supply me with the information I need.

---

### Post by phrostbyte on 2010-08-10
There is this virus scanner type program for Linux called "vrms". It might be able to to tell you what "proprietary software" infections you have on your computer. :lolflag:

I'm not joking btw. You can apt-url it [here]("apt:vrms").

It's a bit strict, some CC licensed stuff has been known to be "caught" by it. It might miss some things too.

---

### Post by JailHouseRock on 2010-08-10
That's actually pretty useful as well as funny. It seems my machine is relatively 'clean'.

---

### Post by regala on 2010-08-10
> **phrostbyte said:**
> Launchpad isn't anymore.

hahahahaha, ye quite funny pal ! the "opening" of Launchpad was the funniest thing Canonical did these last years; yes it is opensource, yes it is distributed under terms compatable with GPL, but this stops here. Providing a poorly packaged (by this, I mean tarballing crappy code with a README containing irrelevant or obsolete instructions to get the thing dirtily installed on a box, is poor packaging, poor distributing, and worse, mocking a community) is in no way opensourcing it.

if I were you, I wouldn't glout on this fiasco (can you point me a list of other-than-Launchpad project sites using Launchpad ?)

-- 
Mathieu

---

### Post by Perfect Storm on 2010-08-10
There's no obligations to how to use/install/whatever just because it's open. And source codes do comes in tarball, just take a look at any open source homepage application/library how they package it.

---

### Post by aeiah on 2010-08-10
if you want a fully free operating system, have a look at [http://www.gnewsense.org](http://www.gnewsense.org)

currently its based off ubuntu, although by the looks of things they want to base it off debian in future, because it'll be easier to separate the free and none-free. according to gnewsense, ubuntu installs non-free software by default, although i don't know specifically which bits are non-free. debian doesn't, but contains non-free repositories (much like ubuntu, with its 'restricted' and 'multiverse' repos i guess)

---

### Post by aeiah on 2010-08-10
hmm, this may be interesting to some, from the gobuntu wiki (an attempt to make a free version of ubuntu):
> 
Gobuntu 8.04.1 is the final release of Gobuntu. The project has merged back to mainline Ubuntu, so there is no need for a separate distribution. Also, Ubuntu cannot reach the level of gNewSense since it has restricted + multiverse repositories, but it should aim to incorporate changes from gNewSense to the extent possible.

The new "Free software only" installation option in the normal Ubuntu (press F6 in the boot menu twice) basically achieves what Gobuntu is aiming for, as long as the general goal of having "clean" main and universe repositories is fulfilled (which is goal of the Ubuntu as a whole). Given that many goals Gobuntu has are goals of Ubuntu in general also, and the fact that gNewSense is anyway doing the work that can also benefit Ubuntu (knowledge of problematic packages), the mission of Gobuntu is a bit up in the air. There's discussion initiated by Mark Shuttleworth on the gobuntu-devel mailing list, continuing also in May. Feel free to participate in the discussion so that some conclusion of what'll be done can be made.


---

### Post by endotherm on 2010-08-10
short answer, whatever proprietary parts you install into it. 
the default ubuntu install has little or no proprietary software in it, but it does give you the option to install encumbered software like nvidia drivers, MM codecs, flash, etc at your whim.

---

### Post by nrs on 2010-08-10
> **LowSky said:**
> Just take a step back and realize the even open-source software can have restrictions to use as well, all depending on the license it is created under.
Not really. If there are restrictions on use it's not really open source / free software. Copyleft licenses have a _***distribution***_ restriction: you can't fork a copyleft project and then distribute a proprietary copy. But there is no usage restrictions. You can even develop an in-house proprietary solution.

---

### Post by MCVenom on 2010-08-10
> **aeiah said:**
> if you want a fully free operating system, have a look at [http://www.gnewsense.org](http://www.gnewsense.org)

currently its based off ubuntu, although by the looks of things they want to base it off debian in future, because it'll be easier to separate the free and none-free. according to gnewsense, ubuntu installs non-free software by default, although i don't know specifically which bits are non-free. debian doesn't, but contains non-free repositories (much like ubuntu, with its 'restricted' and 'multiverse' repos i guess)

> **aeiah said:**
> hmm, this may be interesting to some, from the gobuntu wiki (an attempt to make a free version of ubuntu):

Both are kinda outdated; the most current Ubuntu based 'GNU-compliant' distro is [Trisquel.]('http://trisquel.info/')

Also, Fedora, IMO is a great Linux distro that's, as far as I know 99.9% free and open source. However, the GNU/FSF people aren't fond of the remaining .1%: 

[QUOTE=http://www.gnu.org/distros/common-distros.html]**Fedora**

  Fedora does have a clear policy about what can be included in the distribution, and it seems to be followed carefully.  The policy requires that most software and all fonts be available under a free license, but makes an exception for certain kinds of nonfree firmware. Unfortunately, the decision to allow that firmware in the policy keeps Fedora from meeting the free system distribution guidelines.
[/QUOTE]

---

### Post by JailHouseRock on 2010-08-10
I see I sparked some discussion here, but I can assume there's no public record of what proprietary software is used in ubuntu? 

Also, what is and what is not open source about Launchpad, I've heard conflicting things here, could someone clear this up for me?

---

### Post by zekopeko on 2010-08-10
> **JailHouseRock said:**
> I see I sparked some discussion here, but I can assume there's no public record of what proprietary software is used in ubuntu?

AFAIK almost everything shipped on the liveCD is free except some firmware code.

> Also, what is and what is not open source about Launchpad, I've heard conflicting things here, could someone clear this up for me?

Last time I checked all of Launchpad was FOSS.

---

### Post by JailHouseRock on 2010-08-10
Thanks for your reply, if you are right then my initial thoughts were correct (that the amount of proprietary software is limited to drivers/firmware).

And regarding Launchpad I should just have checked Wikipedia where the *transition* to free software is explained.

[http://en.wikipedia.org/wiki/Launchpad_%28website%29#Transition_to_Free_Software](http://en.wikipedia.org/wiki/Launchpad_%28website%29#Transition_to_Free_Software)

That explains the confusion between you guys here.

---

### Post by koenn on 2010-08-10
> **JailHouseRock said:**
>  ... I can assume there's no public record of what proprietary software is used in ubuntu? 


There is. 
Each program has a license, and the text of the license is included in the distribution. 
You can find them in /usr/share/doc/*/copyright

You can review them and make up your own mind as to which parts you consider 'proprietary'


this might help to browse them:
```
ls -1 /usr/share/doc |while read D; do echo $D; grep -i license $D/copyright;echo;echo;done |less
```

---

### Post by JailHouseRock on 2010-08-10
Thank you koenn, that is very helpful. Possibly a lot of work, but at least it's available at one spot. 

Also proves once again I should dive more into the structure of Linux/Ubuntu, but that's another story.

---

### Post by BuffaloX on 2010-08-10
> **phrostbyte said:**
> There is this virus scanner type program for Linux called "vrms". It might be able to to tell you what "proprietary software" infections you have on your computer. :lolflag:

I'm not joking btw. You can apt-url it [here]("apt:vrms").

It's a bit strict, some CC licensed stuff has been known to be "caught" by it. It might miss some things too.

Just tried it.
Doesn't catch Ubuntu one but flags Conky?

---

### Post by zekopeko on 2010-08-10
> **BuffaloX said:**
> Just tried it.
Doesn't catch Ubuntu one but flags Conky?

UbuntuOne client is fully open source. Don't know what the deal is with Conky.

BTW IIRC vrms measures compliance with the Debian Free software guidelines not the FSF/RMS's.

---

### Post by JailHouseRock on 2010-08-10
> **BuffaloX said:**
> Just tried it.
Doesn't catch Ubuntu one but flags Conky?

The Ubuntu One service is not opensource, the client and protocol are, hence it was not detected.

---

### Post by lisati on 2010-08-10
> **phrostbyte said:**
> 
It's a bit strict, some CC licensed stuff has been known to be "caught" by it. It might miss some things too.

Virtual RMS? :D

---

### Post by JailHouseRock on 2010-08-10
> **lisati said:**
> Virtual RMS? :D

So says the man page lol. Quite hilarious.

---

### Post by BuffaloX on 2010-08-11
> **zekopeko said:**
> UbuntuOne client is fully open source. Don't know what the deal is with Conky.

BTW IIRC vrms measures compliance with the Debian Free software guidelines not the FSF/RMS's.

> **JailHouseRock said:**
> The Ubuntu One service is not opensource, the client and protocol are, hence it was not detected.

Makes sense thanks.

---

### Post by regala on 2010-08-11
> **Artificial Intelligence said:**
> There's no obligations to how to use/install/whatever just because it's open. And source codes do comes in tarball, just take a look at any open source homepage application/library how they package it.

sorry but no. this is not an explanation. And yes I know how software is distributed, do take me for a tool. the instructions to install are vague, only relevant to Ubuntu (once, it couldn't be installed on any other system than the stable Ubuntu of the moment, imopssible on the development version of the next release...) and nearly impossible to adapt to any other GNU/Linux distro. Do you think other projects work this way ?
oh, and I seem not to be able to install it on my Ubuntu using the usual way, isn't it weird ?

---

### Post by matthew.ball on 2010-08-11
No, not weird. You're just doing it wrong.

---

### Post by NCLI on 2010-08-11
> **regala said:**
> sorry but no. this is not an explanation. And yes I know how software is distributed, do take me for a tool.
You don't need to ask for that.

> the instructions to install are vague, only relevant to Ubuntu (once, it couldn't be installed on any other system than the stable Ubuntu of the moment, imopssible on the development version of the next release...) and nearly impossible to adapt to any other GNU/Linux distro. Do you think other projects work this way ?
oh, and I seem not to be able to install it on my Ubuntu using the usual way, isn't it weird ?
The people who package software for different distributions are used to stuff like that. Just because you don't know how to work with the source code doesn't mean they don't ;)

Also, what do you mean by "the usual way"? There are many ways to compile software, depending on how the compiler it's written for. I'd imagine you're also lacking quite a few dependencies, since this is a web server application.

---

### Post by Bachstelze on 2010-08-11
> **NCLI said:**
> 
The people who package software for different distributions are used to stuff like that.


How do you know? I would bet a lot of money you haven't even looked at the code or the build system.

[https://dev.launchpad.net/Getting](https://dev.launchpad.net/Getting)

> Note that right now, Launchpad can only be built and run on Ubuntu Hardy, Jaunty, Karmic or Lucid. That's not a design decision, it's just a consequence of the fact that, until now, all its developers have been running Ubuntu. We'd be happy to see Launchpad work on other platforms too; perhaps starting with Debian GNU/Linux would be easiest, since Debian and Ubuntu are similar and many Debian developers use Launchpad anyway.

Porting Launchpad on another platform would require quite a lot of work, much more than your usual open source project. Is that a problem? No, but it's a fact. And since you said in another thread that disagreeing with a fact is being stupid, the conclusion is obvious.

---

### Post by NCLI on 2010-08-11
> **Bachstelze said:**
> How do you know? I would bet a lot of money you haven't even looked at the code or the build system.

[https://dev.launchpad.net/Getting](https://dev.launchpad.net/Getting)



Porting Launchpad on another platform would require quite a lot of work, much more than your usual open source project. Is that a problem? No, but it's a fact. And since you said in another thread that disagreeing with a fact is being stupid, the conclusion is obvious.
I don't remember disagreeing with the fact that it is hard to port, just that it is deliberately unusually hard to port, nor will I retract my comment about the people who port packages for different distributions being used to this sort of thing. I'm fairly certain that most companies which open-source code they've made for their own distro aren't interested in investing time to make sure it's compliant with competing distros. After all, that really isn't their problem. If Red Hat or Novell were interested in porting Ubuntu One, I'm sure they could do so with a minimum of effort.

Lastly, I haven't looked at the code, nor the build system, that much is true. On the other hand, I would bet a lot of money that not many people in this thread have. I'm arguing from what I can read on the "Getting" page, and what I know about packaging.

---

### Post by regala on 2010-08-17
> **NCLI said:**
> You don't need to ask for that.


I guess I deserve it for the sake of mistyping at least :)

> 
The people who package software for different distributions are used to stuff like that. Just because you don't know how to work with the source code doesn't mean they don't ;)


Oh, I do know how "it" works, the problem I encountered was that I was unable to write an ebuild for Gentoo to install it on that distro. Do you know why ? because Launchpad was released as a big code-drop (the thing why everyone in the community trashes Google  at every Android release). In fact, I do know how to install most software from source, the fact and the matter is, Launchpad is unless you patch it monstruously uninstallable on anything but Ubuntu. which shows how you really care for Open Source...


> Also, what do you mean by "the usual way"? There are many ways to compile software, depending on how the compiler it's written for. I'd imagine you're also lacking quite a few dependencies, since this is a web server application.

In fact I can read a README file, but reading it was desperating(*). I don't care, if Canonical doesn't either about real acceptance and widespread of its own product. Targetting only Ubuntu is so typical of rockstar-shining-awesome guys that work for such an awesome project without which free software wouldn't even exist. Dont need your self-centered conception of free software either.

(*) desperating because dependencies are not the problem. so much has to be done which is not taken care of by the build system that it's desperating. What should be a good incentive to you, is the fact that no Ubuntu or Canonical developer even cares about packaging it. I cant find a package to do this. I thought creating Ubuntu packages was easy or at least devs are quite specialists to it, no ?

---

### Post by matthewbpt on 2010-08-17
> **regala said:**
> I guess I deserve it for the sake of mistyping at least :)



Oh, I do know how "it" works, the problem I encountered was that I was unable to write an ebuild for Gentoo to install it on that distro. Do you know why ? because Launchpad was released as a big code-drop (the thing why everyone in the community trashes Google  at every Android release). In fact, I do know how to install most software from source, the fact and the matter is, Launchpad is unless you patch it monstruously uninstallable on anything but Ubuntu. which shows how you really care for Open Source...




In fact I can read a README file, but reading it was desperating(*). I don't care, if Canonical doesn't either about real acceptance and widespread of its own product. Targetting only Ubuntu is so typical of rockstar-shining-awesome guys that work for such an awesome project without which free software wouldn't even exist. Dont need your self-centered conception of free software either.

(*) desperating because dependencies are not the problem. so much has to be done which is not taken care of by the build system that it's desperating. What should be a good incentive to you, is the fact that no Ubuntu or Canonical developer even cares about packaging it. I cant find a package to do this. I thought creating Ubuntu packages was easy or at least devs are quite specialists to it, no ?

An open source project is not obliged to release code that works on all platforms, and they aren't obliged to release it in a form which is easily understandable to anyone but themselves. Canonical develop Launchpad for their own platform and release the code they develop with an open source license and that's all they need to do. If you want to make it work on another platform you are free to do so. Anyone who wants to has the opportunity to do this, so I can't see what's the problem. Why do you feel they owe it to you to release THEIR software the way YOU want them to?

---

