---
title: "What's happening with quality?"
date: 2013-03-07
forum: Ubuntu Development Version
---

### Post by balloons on 2013-03-07
I wanted to cross-post this from the quality mailing list. I know there are many threads here talking about what's going on and I would like to talk breifly about what we as a quality community are doing atm. Look for some announcements coming soon to help test the new stuff we've heard about this week. :guitar:

--------------

Some of you may be wondering what all is next, given talk of the rolling release, mir, ubuntu touch, etc. Well, simply put, we have wonderful new toys for us to test! Ubuntu touch is a new emerging platform for ubuntu. There's a slew of app developers writing new applications for ubuntu that we want to install best practices in and help test there stuff. Then there's that new display server MIR -- we'll want to get involved with it as well and test. Finally, should a rolling release happen, we can match our cadence with the development teams and help drive new stuff into the rolling model, as well as expand our potential testing audience.

Here's what we do know:
-- Beta 1 is coming, and we'll be helping to test it
-- A rolling release is being considered (before or after 13.04, etc), and we've started a conversation about it's consequences (to quality) should it happen (please, open more threads here on the mailing list if the UDS session didn't raise all the points)
-- Ubuntu touch, and mir is here and we'll be diving in to help test

So, keep your testing hats on, it's going to be a fun ride testing on the new platform.. Don't have a phone or tablet? You can still help! The apps being written will also run on the desktop, and there's lots of new tests to write and run.

---

### Post by ventrical on 2013-03-07
Thanks for the heads up Nick.!

regards,
ventrical

---

### Post by grahammechanical on 2013-03-08
Hi guitara

I am glad that you have not forgotten us on U+1. I listened in on a couple of sessions on UDS-online. As you know some of us are already running a virtual rolling release by converting each stable release as it is finalised into a development branch and then doing daily updates.

I wonder if the devs are aware of the large number of kernel updates that come through onto the development branch. Quantal will not get many kernel updates during its lifespan but my Raring install already has 1 x kernel 3.5 (deleted the rest), 7 x kernel 3.7, and 10 x kernel 3.8. Imagine the number of kernels that will come down the pipe over 12 months or 24 months. Normally I flush all these previous kernels away by starting each development cycle with a fresh install of the latest stable release which I then convert. As, someone in the hangout pointed out many ordinary users who are installing the development branch have a limited skill set. They will need help in housekeeping. Just I a thought that I wanted to share.

Oh, by the way. Some of us have already jumped in and are testing MIR. And we quickly get bored. We are looking more ways to do stuff under MIR.

Regards.

---

### Post by kansasnoob on 2013-03-08
Hi Nicholas. I've not forgotten about this:

[http://ubuntuforums.org/showthread.php?t=2105055&page=4&p=12463934#post12463934](http://ubuntuforums.org/showthread.php?t=2105055&page=4&p=12463934#post12463934)

There are disturbing changes in the upgrade/replace installer options:

[http://ubuntuforums.org/showthread.php?t=2105055&page=4&p=12465489#post12465489](http://ubuntuforums.org/showthread.php?t=2105055&page=4&p=12465489#post12465489)

But there are also a gazillion holes in my plan. I totally left out LVM and encrypted installs, and also someone recently mentioned a borked reinstall with a separate /home partition but I didn't have time to do any follow-up testing to see if it was a bug or user error :(

If at all possible I'll try to give this more time after Raring  Beta 1 testing. Actually since we're talking about major changes in the dev cycle this would be an excellent time to bring up the need for the installer team to be more "public" about what's happening :)

---

### Post by VinDSL on 2013-03-08
> **grahammechanical said:**
> As you know some of us are already running a virtual rolling release by converting each stable release as it is finalised into a development branch and then doing daily updates.
Heh!  :D

```
vindsl@Zuul:~$  ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
Oct 13 2011

vindsl@Zuul:~$ cat /var/log/installer/media-info
Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)

```

Some of us have been running a "virtual rolling release" since Ubu OO...

---

### Post by craig10x on 2013-03-08
Is that how you guys do it? Just upgrade to the next development branch when the one you have been running, goes final?
So, then i take it, VinDsl, that you have been running the same install since 11.10 right up to 13.04 thus far, without ever re-installing?
If that's the case, you have been running a "virtual rolling release" all along...

I have to say, personally, this is the first time i ever ran ubuntu while it was in development, and i have been amazed at how reliable the updates have been...
I get the sense that ubuntu IS really ready for going rolling release... :D

---

### Post by VinDSL on 2013-03-08
> **craig10x said:**
> So, then i take it, VinDsl, that you have been running the same install since 11.10 right up to 13.04 thus far, without ever re-installing?

If that's the case, you have been running a "virtual rolling release" all along...
Yep!  Started off as an experiment, for lack of a different word.  Or, maybe a silly game...

I was curious to see how long I could keep "rolling" Ubuntu, before it ended up "hitting the wall".

A few times, I thought I was gonna have to do a fresh install, but I've always managed to work my way through it.

Anyway, so far, so good...  ;)

---

### Post by kansasnoob on 2013-03-08
> **craig10x said:**
> Is that how you guys do it? Just upgrade to the next development branch when the one you have been out goes final?
So, then i take it, VinDsl, that you have been running the same install since 11.10 right up to 13.04 thus far, without ever re-installing?
If that's the case, you have been running a "virtual rolling release" all along...

I have to say, personally, this is the first time i ever ran ubuntu while it was in development, and i have been amazed at how reliable the updates have been...
I get the sense that ubuntu IS really ready for going rolling release... :D

In Raring that's been particularly easy. I don't think I've had any update totally bork things if I pay attention and not use the "proposed" updates when unwise.

But we do also need to test the installer(s) to check for bugs.

---

### Post by balloons on 2013-03-09
> **kansasnoob said:**
> Hi Nicholas. I've not forgotten about this:

[http://ubuntuforums.org/showthread.php?t=2105055&page=4&p=12463934#post12463934](http://ubuntuforums.org/showthread.php?t=2105055&page=4&p=12463934#post12463934)

There are disturbing changes in the upgrade/replace installer options:

[http://ubuntuforums.org/showthread.php?t=2105055&page=4&p=12465489#post12465489](http://ubuntuforums.org/showthread.php?t=2105055&page=4&p=12465489#post12465489)

But there are also a gazillion holes in my plan. I totally left out LVM and encrypted installs, and also someone recently mentioned a borked reinstall with a separate /home partition but I didn't have time to do any follow-up testing to see if it was a bug or user error :(

If at all possible I'll try to give this more time after Raring  Beta 1 testing. Actually since we're talking about major changes in the dev cycle this would be an excellent time to bring up the need for the installer team to be more "public" about what's happening :)


This is interesting -- let me talk with the team on Monday. Thanks for pointing this out.

---

### Post by balloons on 2013-03-09
> **VinDSL said:**
> Heh!  :D

```
vindsl@Zuul:~$  ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
Oct 13 2011

vindsl@Zuul:~$ cat /var/log/installer/media-info
Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)

```

Some of us have been running a "virtual rolling release" since Ubu OO...

Nice! I re-installed during precise to help test. I think I had been running since natty before that. And yes, I'm essentially running ubuntu stable for only a couple weeks after releases before switching over and keeping the rolling release going.

---

### Post by grahammechanical on 2013-03-09
@craig10x

this is the code that I used to change a fresh 12.10 install into Raring

```
sudo sed -i 's/quantal/raring/g' /etc/apt/sources.list
``` followed by
```
 apt-get update && sudo apt-get dist-upgrade
```

I do not know if something like that will work in May of this year. The repositories have to be available and have to have a name that can be referenced. Up until now the repositories have the code names of the releases. Continue testing. Some of us think it is fun. I am not sure that I am there yet.

---

### Post by craig10x on 2013-03-09
Thanks for the "heads up" on that (how to upgrade)...normally i wait for a final release of ubuntu to install, but after checking out a live session of 13.04 i noticed that two annoying  bugs i had with 12.10 were gone in 13.04, so i just couldn't resist getting involved in the development!  But since installing, i have been VERY impressed by the reliability of the updates...I've had far fewer problems "rolling" with this then i had when i ran Linux Mint's LMDE (the rolling release version)...

---

### Post by screaminj3sus on 2013-03-09
compiz has regressed significantly late in the cycle :(

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1141079](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1141079)

---

### Post by kevpan815 on 2013-03-09
The only Cell Phone and Tablet that I have are Apple IOS Devices, for which I am assuming that Ubuntu will NOT be available on them, and even if it was available I would NOT be allowed to test it as I am already Testing IOS Beta's on it and I am only allowed 1 Cell Phone on my Restricted Sprint 2 Year Cell Phone Contract so buying a Samsung Galaxy S3 to go along with my Apple IPhone 5 is NOT Possible at the moment.

---

### Post by VinDSL on 2013-03-09
> **screaminj3sus said:**
> compiz has regressed significantly late in the cycle :(

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1141079](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1141079)
I know your bug has been confirmed, so I'm not disputing it.  That said...

I'm been having great luck with Compiz lately!

Here's VLC on my "virtual rolling release"...  ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-9-mar-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-9-mar-2013-1.png")[/INDENT]


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-9-mar-2013-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-9-mar-2013-2.png")[/INDENT]


I'm fully updated, as of 30 minutes ago...

**EDIT**

BTW, if you look closely, you'll see that the Banshee section in Conky says "Error".

That's actually the title of the dubstep song I'm listening to, in the background, NOT an error.  LoL!

**EDIT 2**

n/m

I reread the bug and, indeed, there are problems with the "Fullscreen Interface".

I disabled window shadowing for VLC, in Compiz, and everything started working in "Fullscreen" mode... until the Unity Launcher popped up.  Then, all bets were off.

You can 'reset' everything by right-clicking the screen, but as soon as the Launcher pops up, it knocks this_or_that out of action.

I'll add a "me too" in Launchpad...

---

### Post by balloons on 2013-03-12
> **guitara said:**
> This is interesting -- let me talk with the team on Monday. Thanks for pointing this out.

kansasnoob, I asked about this and the short version of the story is the 'downgrade' was an unintended interaction with the installer. As you know, downgrading packages doesn't really work out so well, as it's not a supported thing (certainly not at a system level) to do so. If you wanted to rollback to an earlier release, i'd suggest just re-installing and reusing your /home directory. I hope that helps!

---

