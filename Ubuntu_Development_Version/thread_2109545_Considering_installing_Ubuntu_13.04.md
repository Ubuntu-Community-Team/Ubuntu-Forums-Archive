---
title: "Considering installing Ubuntu 13.04"
date: 2013-01-27
forum: Ubuntu Development Version
---

### Post by craig10x on 2013-01-27
It's running so nice for me on live session (downloaded latest daily build) even has kernel 3.8 which has some very nice improvements in power management and performance that i have noticed on my new Toshiba laptop with intel i3 core processor....

I know i should really wait until final release, when i was planning on replacing my 12.10 install with 13.04...
Then i thought, maybe i should install it as a dual boot for now...

From those that have been testing, do you think it's stable enough at this point for daily usage or should i just wait until April?

All feedback appreciated! :D

---

### Post by Bucky Ball on 2013-01-27
Because it's stable today it doesn't mean something won't break in the next update. That's what testing versions are all about. 

Installing on another partition and keeping a stable release in case of breakages is a good idea.

---

### Post by VinDSL on 2013-01-27
> **craig10x said:**
> From those that have been testing, do you think it's stable enough at this point for daily usage [...]

All feedback appreciated! :D
It's too stable IMO.  Either that, or I've gotten too adept at fixing problems.

Hrm...

Yoko Ono once said, you can't unknow what you know.

If you're new to testing, then you'll probably have some fun.  Otherwise, it'll be a snooze...

---

### Post by kevpan815 on 2013-01-27
You could try a Dual Boot Scenario. For example: I usually Dual Boot 13.04 with Windows 8 RTM (Release to Manufacturing Build).

---

### Post by rrnbtter on 2013-01-27
Greetings,
Thus far an absolute delight. This is the best I have ever had it.  That being said, I don't update my wife's computer until I know that everything is working ok on mine. We both have the same basic needs and use much the same software.  Word of caution! Some PPA's wont work with this release since they haven't been updated yet.  There may be some software that doesn't yet have a 13.04 candidate.  You will have to wait for the release which may be the same day as the Beta release and possibly even later.  If you are already testing everything you need and it is working you should be fine. Or not!
Its testing!

---

### Post by craig10x on 2013-01-27
Well, the only "outside" stuff i install on ubuntu (that isn't in the software center) are deb files for google chrome and a deb file 
I have for installing the REAL oracle java 7 (not the open source version) and both of these seem to run fine when installed in 13.04 live session...both of these debs do put ppas into the software updater for updated versions...

I am actually in the live session as i type this (lol)...

My thought was, if i was going to install, safer to dual boot with 12.10 since that way i would have a definite reliable back up to use...

Appreciate the input so far and anyone else that would like to comment, would love your impressions... ;)

And i take it that no one has experienced breakages or major set backs so far?

I haven't really ever installed testing versions before, only reason i am tempted with 13.04 is because the improvements i have noted on my computer w/intel is fairly dramatic (in a positive way of course..lol)

---

### Post by Bucky Ball on 2013-01-27
> **craig10x said:**
> 

My thought was, if i was going to install, safer to dual boot with 12.10 since that way i would have a definite reliable back up to use...



Good plan. ;)

---

### Post by cariboo on 2013-01-27
I had a weird Unity/Compiz crash last night where a couple of applications closed, chromium and thunderbird moved to different work spaces, and menu's disappeared. I haven't been able to duplicate it yet, so no bug report.

---

### Post by kansasnoob on 2013-01-28
> **kevpan815 said:**
> You could try a Dual Boot Scenario. For example: I usually Dual Boot 13.04 with Windows 8 RTM (Release to Manufacturing Build).

+1!

I take multi-booting to extremes:

[ATTACH]230739[/ATTACH]

There really is a rhyme to my reasoning. I perform SRU testing, some of which requires testing on bare metal as opposed to a VM, and sometimes I want to test two lateral installs - one with certain PPA's and the other without :D

But, you should never depend on stability from a testing release. In fact that's more true now than ever because no Alpha discs exist for most of the flavors ;)

---

### Post by craig10x on 2013-01-28
Well, i gave it some thought and on wednesday i am going to install 13.04 as a dual boot!  I'll be keeping my fingers crossed that the install will be ok and that things stay smooth until April 25th which at that time i would re-install the final version...

I came to the conclusion (and as you guys here pointed out) that it would be best to keep the 12.10 going with it so that i have a stable back-up in case there are problems...

Hopefully, there won't be...

---

### Post by Bucky Ball on 2013-01-28
You won't need to install the final version. Just keep updating and you will be there anyway. Enjoy the learning curve.

If you consider this solved please mark it that way from Thread Tools to help others and post a new thread with a descriptive title in the appropriate section for any other issues, questions, problems, etc. Good luck with it and wise choice to keep 12.10 as a stable install.

---

### Post by offgridguy on 2013-01-28
> **kansasnoob said:**
> +1!

I take multi-booting to extremes:

[ATTACH]230739[/ATTACH]

There really is a rhyme to my reasoning. I perform SRU testing, some of which requires testing on bare metal as opposed to a VM, and sometimes I want to test two lateral installs - one with certain PPA's and the other without :D

But, you should never depend on stability from a testing release. In fact that's more true now than ever because no Alpha discs exist for most of the flavors ;)
Love the screenshot, gives me some ideas, thanks.

---

### Post by craig10x on 2013-01-29
Thanks Bucky Ball and if i run into anything along the way that i need assistance on, i will make a new thread... ;)

---

### Post by ckunzler on 2013-01-29
I'd go ahead and install it if you're not too worried about having something go wrong. Make sure you back up your data, of course. Perhaps you might be able to help if any issues arise.

---

### Post by grahammechanical on 2013-01-30
I have been using a development branch as my daily work OS for more than 18 months. But I always have another Ubuntu as my stand-by OS and I always keep my data in a separate /home partition attached to my stand-by Ubuntu (12.04 at present).

During the testing of Quantal I had to use my Stand-by Ubuntu to do my daily work as there was a period of several days when Quantal became unusable and a fresh install proved impossible.

I also have another Raring install that I will use for specific tests as I do not want to mess up the Raring install that I consider my daily work OS.

Regards.

---

### Post by fantab on 2013-01-30
I have only used LTS version as my stable Ubuntu... and use Development Release as my general OS.  I agree with the #15 that Quantal was PITA.

---

### Post by mruffalo on 2013-02-01
I've been using Kubuntu 13.04 since around November I think, and it hasn't been entirely smooth. There have been a few package updates that have broken important functionality, and these are always fixed very quickly after submitting a bug report. Still, though, it can be very irritating to (e.g.) not have a battery gauge, not have application menu bars, or be unable to use VMware Workstation because of a kernel header incompatibility. At least (unlike Quantal) there haven't been any video driver regressions that made my laptop completely unusable.

Using btrfs as my filesystem has been absolutely essential -- my systems are configured to take snapshots of the root and home subvolumes on every boot, and rolling back to a previous snapshot is quite easy after booting from a live CD/USB drive. After that, I usually delay aptitude full-upgrading for a day or two and then try again to see if things are still broken.

---

