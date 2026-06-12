---
title: "backporting - is it possible at all?"
date: 2006-07-14
forum: Ubuntu Backports
---

### Post by burlap on 2006-07-14
I've been a huge fan of backports since their beginnings (was it warty?). They perfectly balanced my need for bleeding-edge packages and safety of official release (I use Linux as my "production desktop"). 

But for now it seems that the possibility to backport is really small - the requirement to meet edgy's build-deps excludes packages that might build cleanly. 

I know that debian/ubuntu patches may change original dependencies (even if original project pages say libfoo => 1.2, debian/ubuntu might need libfoo 1.3), but isn't it better to test at the stage of compiling, not downloading build-deps? 

In general, it seems that most gnome and kde packages won't be possible to backport (new gnome/kde libs required), nor mono-based software (new package naming scheme) - and these are probably the "most wanted".

So I was wondering - do we need backports at all? I know it seems like a flame, but:
1. Non-geeks won't use backports anyway (unless someone who got their linux working set up backport repository for them)
2. Bleeding-edge software users will compile and run it anyway
3. Many debs are posted on the forums, so those not too eager to compile might test them and use "unofficial" backports
4. Dapper is supposed to be rock-solid, so it doesn't need any new software

On the other hand there are still some packages that are possible to backport and people want them... 

Why this flame? Right after dapper came out, two programs I used made new releases: beagle (0.2.7) and inkscape (0.44). Both are under heavy development and each new release brings tons of new features and fixes many bugs. I waited for them to hit edgy and when they did, I was hoping to see them backported. Unfortunately it's not possible. *[Beagle compiled cleanly, I'm thinking about compiling inkscape, but I could go for their autopackage instead (less effort...).]* 

I understand why this policy was adopted from the perspective of dapper developers, but I doubt whether it makes sense from the perspective of backports' target users.

---

### Post by mmcmonster on 2006-07-14
I think there are a lot of "non-geeks" that use Ubuntu.  At least compared to other Linux distributions. :-)  So don't under-rate the non-geek apeal.

As for there not being much that can be backported, that is unfortunately the way of life.  One of the best parts of GPL and other opensource applications is shared libraries.  Unfortunately, when an upgrade to a library is necessary, extreme care has to be taken to make sure things don't get broken.

Fortunately, Ubuntu puts out 2 complete distributions a year, so even if something doesn't get backported, you shouldn't have to wait more than 6 months. ;-)

That being said, I can't wait for the backport of rhythmbox to be released...

---

### Post by burlap on 2006-07-14
About non-geeks: I wanted to say that there were a lot of non-geek users (and numbers are growing, I hope), but they were not backport's target group. 

About libraries: my point is that there are packages that can be compiled cleanly with dapper libraries, although their edgy requirements include newer libraries. 

About rhythmbox: I don't think it's possible. Rhythmbox requires newer version of libnautilus-burn-dev. Just to support my point...

---

### Post by mmcmonster on 2006-07-14
Tell you the truth, I never created a .deb myself.  I was under the impression that when setting a dependency on a library, the programmer gives a known minimum lib version (and maybe a max version).

Do the Ubuntu people change those numbers?

I do agree with you that it's frustrating that there is so much stuff that will go into edgy that should be easy to backport except for the dependency hell that it would raise.

Well, October is only 3 months away... ;-)

---

### Post by burlap on 2006-07-14
> **mmcmonster said:**
> Do the Ubuntu people change those numbers?
If they do, they do it on purpose... 

I built debs (and earlier rpms) myself, it's not that difficult. It becomes difficult when it comes to mixing packages, upgrading and in general interactions with other parts of the system. If it were all that easy, backports would have been useless anyway...

> **mmcmonster said:**
> Well, October is only 3 months away... ;-)
I'm sure I'll upgrade to edgy. But I wanted to keep Dapper for a little longer for other people I "converted" to linux (as edgy is supposed to be, well, edgy), hoping that with backports they would be able to have stable system with reasonable mix of new features... Of course, I won't change my mind and for non-geeks keep dapper until edgy+1.

---

### Post by Erunno on 2006-07-14
I'm pretty new to Ubuntu and Linux so can anyone explain me why programs like ScummVM, DosBOX and WINE don't get backported asap ? From my newbish point of view they don't seem to depend on newer libraries and some of them can be compiled against older versions of certain libraries. Yet when I used the official repository to get ScummVM I was shocked that it was still the ancient 8.00 release. A huge step backwards compared to Windows where you can get the newest releases without much hassle.

I'm a little hesitant to use other repositories or downloaded .debs right now because as long as I don't know how a Linux system works I fear to break something unintentionally.

Cheers,
Erunno

---

### Post by YokoZar on 2006-07-15
> **Erunno said:**
> I'm pretty new to Ubuntu and Linux so can anyone explain me why programs like ScummVM, DosBOX and WINE don't get backported asap ? From my newbish point of view they don't seem to depend on newer libraries and some of them can be compiled against older versions of certain libraries. Yet when I used the official repository to get ScummVM I was shocked that it was still the ancient 8.00 release. A huge step backwards compared to Windows where you can get the newest releases without much hassle.
For Wine you can go here:

[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

> I'm a little hesitant to use other repositories or downloaded .debs right now because as long as I don't know how a Linux system works I fear to break something unintentionally.Well, the packages at WineHQ are made by the same person who makes them for Ubuntu (me) - they're simply copied over to the development tree every once and a while.  At worst, the only thing you'll break by using them is Wine :)

---

### Post by Erunno on 2006-07-15
Thanks, much appreciated ! :)

Does a signature key exist for this particular wine repository ? Synaptic is making me nervous with this constant reminders about the hazzards of unsigned packages. ;) 

Still, this does not explain why it takes so long to backport other packages. Plus, I'd like to ask you why this new wine versions aren't put into the backport repository.

Cheers,
Erunno

---

### Post by YokoZar on 2006-07-18
> **Erunno said:**
> Thanks, much appreciated ! :)

Does a signature key exist for this particular wine repository ? Synaptic is making me nervous with this constant reminders about the hazzards of unsigned packages. ;) Well, the packages are all signed by me, but you need to go out of your way to add my key to your trusted database.  It's probably not a good idea to add keys like that anyway :)

> Still, this does not explain why it takes so long to backport other packages. Plus, I'd like to ask you why this new wine versions aren't put into the backport repository.
Because I'm lazy.

---

### Post by Metacarpal on 2006-07-20
> **burlap said:**
> So I was wondering - do we need backports at all? I know it seems like a flame, but:
1. Non-geeks won't use backports anyway (unless someone who got their linux working set up backport repository for them)
2. Bleeding-edge software users will compile and run it anyway
3. Many debs are posted on the forums, so those not too eager to compile might test them and use "unofficial" backports
4. Dapper is supposed to be rock-solid, so it doesn't need any new software

The answer?  Backports are there for me, and people like me.  I'm not bleeding edge, but I am a geek.  I've not learned enough Linux yet to feel comfortable compiling my own installs, and I like the word stable.  It seems so reliable, ya know?

But at the same time, I'm a fan of latest-and-greatest.  If there's a better package available, I want it - provided it's known-good.  Sure, right now my backport repository's getting a break because of the issues you've cited, but that'll probably change in the future.  So I'm leaving it enabled.

Besides - even if the backports don't come through often, it doesn't hurt to have the gateway for them open, just in case. :)

---

### Post by Erunno on 2006-07-21
> **burlap said:**
> 2. Bleeding-edge software users will compile and run it anyway
3. Many debs are posted on the forums, so those not too eager to compile might test them and use "unofficial" backports
4. Dapper is supposed to be rock-solid, so it doesn't need any new software

Windows' software installation system allows to install bleeding edge software the same way as old one through their automatic installers. I reckon that there are users who aren't total newbies and know how to handle a computer but are not proficient and interested enough to use a compiler. Plus, installing software from repositories is preferable to me as I can use the auto-update mechanism, I can perform clean removals and don't have to hunt down new versions on forums. The "grandma"-user that some seem to fear will break the system shouldn't be able to activate the backport repository in the first place. 

It's really disheartening that backports seem de-facto to be not supported at all :(

---

### Post by burlap on 2006-07-21
> **Erunno said:**
> Windows' software installation system allows to install bleeding edge software the same way as old one through their automatic installers.

There are projects that offer linux binaries too - and whether it's rpm, deb, autopackage or other format, you can also call them "installers". The point is that linux is NOT windows (many people seem to overlook that fact), and preferred way to install software is - at least for desktop - to use package repositories. And of course you pointed out most of the reasons why. 

I can't code myself, so my only way to evaluate if a package breaks anything is using it. If it doesn't compile with default libraries - I give up (unless the program I'm compiling is the only one that needs the new library and uninstalling repository libraries doesn't brake any dependencies). There are packages that are not "stable" no matter which version is used (dapper version of beagle crashed as often as 0.2.7) and packages I won't touch with a 60 feet pole (like kernel - I used to run custom 2.4, but 2.6 is just too much).

> **Metacarpal said:**
> Sure, right now my backport repository's getting a break because of the issues you've cited, but that'll probably change in the future.  So I'm leaving it enabled.
I'm leaving it enabled too. But are these issues going to change?

---

