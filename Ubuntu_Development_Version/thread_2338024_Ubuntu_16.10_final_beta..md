---
title: "Ubuntu 16.10 final beta."
date: 2016-09-23
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2016-09-23
Anyone know when it's due?  I have been looking since the 22nd.

Henry

---

### Post by VMC on 2016-09-23
The above top "sticky" release schedule shows :[TABLE]
[TR]
[TD="bgcolor: #E47A7A"]**22**
[/TD]
[TD]September 22nd
[/TD]
[TD][IMG]https://wiki.ubuntu.com/moin_static193/light/img/icon_eek.png[/IMG] Final Beta Freeze, [IMG]https://wiki.ubuntu.com/moin_static193/light/img/icon_eek.png[/IMG] Final Beta
[/TD]
[/TR]
[/TABLE]

---

### Post by Hewjr100 on 2016-09-23
True but today is the 23rd.

Henry

---

### Post by mc4man on 2016-09-23
> **Hewjr100 said:**
> Anyone know when it's due?  I have been looking since the 22nd.

Henry
You can look till the cows come home, you'll not find that in Ubuntu as it doesn't do alpha's, beta's, release candidate's anymore.
 You'll notice on the release sched. page none of the above are Ubuntu links with the exception of ReleaseCandidate which if followed would describe as 
> During the week leading up to the final release, **the images** produced are all **considered** release candidates


---

### Post by simonsaysthis on 2016-09-24
I wonder though if Ubuntu Mate Beta 2 is delayed. They do usually announce the Beta versions as they did with Alpha and Beta 1

---

### Post by acheronuk on 2016-09-24
Kernel driver issues, I believe.

So that needs fixing and the images re-spun and tested.

---

### Post by PaulW2U on 2016-09-24
> **simonsaysthis said:**
> I wonder though if Ubuntu Mate Beta 2 is delayed. They do usually announce the Beta versions as they did with Alpha and Beta 1
There's a delay with all flavours, a problem with the kernel I understand. A comment on IRC by one of the release team suggests that it could now be Monday before the beta is released.

---

### Post by jbicha on 2016-09-24
> **mc4man said:**
> You can look till the cows come home, you'll not find that in Ubuntu as it doesn't do alpha's, beta's, release candidate's anymore.
 

My understanding is that the Final Beta is mandatory for flavors that want to participate in the final release.

---

### Post by mc4man on 2016-09-24
> **jbicha said:**
> My understanding is that the Final Beta is mandatory for flavors that want to participate in the final release.

Yeah, the flavors do these named 'pre-releases', Ubuntu is just yesterday's, today's, tomorrow's image, ect. So I'd gather there is more significance for Ubuntu to the various freeze dates  rather than the state of on any particular alpha, beta, rc date

---

### Post by jbicha on 2016-09-24
My understanding is that's it's mandatory for Ubuntu (Unity, Server, etc.) too.

But yes, if you want to try pre-release Ubuntu, I highly recommend you just grab a daily image and not worry about getting a named milestone.

---

### Post by mc4man on 2016-09-24
> **jbicha said:**
> My understanding is that's it's mandatory for Ubuntu (Unity, Server, etc.) too.

But yes, if you want to try pre-release Ubuntu, I highly recommend you just grab a daily image and not worry about getting a named milestone.

You're probably correct, I see it presented that way on the mailing list. However I  don't actually see a named beta iso for Ubuntu, seems to just lead to a daily image (yesterday - ...  /daily-live/20160922/yakkety-desktop-amd64.iso
(- maybe looking in wrong places?
In the somewhat distant past I recollect actual named iso's for alpha, beta, rc, ect.

---

### Post by jbicha on 2016-09-24
> **mc4man said:**
> However I  don't actually see a named beta iso for Ubuntu

That's because the Final Beta scheduled for this week has not been released yet (for any Ubuntu flavor). When it is released, there will be announcements to the [ubuntu-release]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-release") and [ubuntu-devel-announce]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce") lists.

Maybe Monday.

---

### Post by ventrical on 2016-09-26
All images of opt-ins are currently froze at Sept. 21 with exception of Ubuntu Desktop at Sept. 22.

Regards..

---

### Post by simonsaysthis on 2016-09-26
> **ventrical said:**
> All images of opt-ins are currently froze at Sept. 21 with exception of Ubuntu Desktop at Sept. 22.

Regards..

Saw that too. Any reason why the daily builds have stopped?

---

### Post by ventrical on 2016-09-26
> **simonsaysthis said:**
> Saw that too. Any reason why the daily builds have stopped?

I did an update/upgrade and it completely shot my system.. so I had to use BusyBox to run fsck /dev/sda1 to fix it. Most of the unity8 stacks are in real bad shape. This late in the cycle .. I dunno .. maybe some kernel problems. I expect large updates to roll in for the next few weeks.  Hopefully we will fair better on unity8 with 17.04.

 In all fairness .. a lot of focus on  xenial bug fixes  and snappy , snapcraft etc.. so there is a full plate.

regards..

---

### Post by arnold8969 on 2016-09-26
I'm using 16.10 since may 18. Since the Beta there are almost No Updates anymore. Strange ! 
I do not have Unity8.

---

### Post by simonsaysthis on 2016-09-26
> **ventrical said:**
> I did an update/upgrade and it completely shot my system.. so I had to use BusyBox to run fsck /dev/sda1 to fix it. Most of the unity8 stacks are in real bad shape. This late in the cycle .. I dunno .. maybe some kernel problems. I expect large updates to roll in for the next few weeks.  Hopefully we will fair better on unity8 with 17.04.

 In all fairness .. a lot of focus on  xenial bug fixes  and snappy , snapcraft etc.. so there is a full plate.

regards..


Well a bit of pressure at the ranch is maybe not a bad thing. I presume if Shuttleworth didn't promise Unity 8 can be downloaded with 16.10 for everyone to try it out it probably would have been pushed out again. So now the heat is on to get everything read in time. I wonder if there are too many resources behind mobile and touch.

---

### Post by PaulW2U on 2016-09-26
> **arnold8969 said:**
> I'm using 16.10 since may 18. Since the Beta there are almost No Updates anymore. Strange ! 
The beta has **not** yet been released. From [https://lists.ubuntu.com/archives/ubuntu-release/2016-September/003909.html](https://lists.ubuntu.com/archives/ubuntu-release/2016-September/003909.html)
> In the meantime, the archive remains in beta freeze state and the release
team will do what we can to keep the archive freeze from impacting yakkety
development unnecessarily, but some delays should be expected while we work
to finish getting the beta into a releasable state.
Updates will resume once the beta is released.

---

### Post by ventrical on 2016-09-26
> **simonsaysthis said:**
> Well a bit of pressure at the ranch is maybe not a bad thing. I presume if Shuttleworth didn't promise Unity 8 can be downloaded with 16.10 for everyone to try it out it probably would have been pushed out again. So now the heat is on to get everything read in time. I wonder if there are too many resources behind mobile and touch.

Developers have bills to pay and mouths to feed. Usually the xx.10 releases have some problems between cycles. (Only exception was with maveric meerkat 10.10) Also I think they are doing a top down, bottom up rebuild of unity8 so we have a rolling, working store and Libertine containers for nVidia boxes as well as Intel.

Regards..

---

### Post by simonsaysthis on 2016-09-28
I think everything is rolling again :KS

---

### Post by PaulW2U on 2016-09-28
> **arnold8969 said:**
> I'm using 16.10 since may 18. Since the Beta there are almost No Updates anymore. Strange !
So [Beta 2]("https://lists.ubuntu.com/archives/ubuntu-announce/2016-September/000212.html") was released earlier today, some six days later than expected.

As predicted (by me) there have been **many** updates. :)

---

### Post by simonsaysthis on 2016-09-28
So disappointed. For some reason the Final Beta still doesn't boot from USB with EFI boot on Lenovo Thinkpad. Is there a way of still installing it in UEFI mode?

---

### Post by simonsaysthis on 2016-09-28
> **simonsaysthis said:**
> So disappointed. For some reason the Final Beta still doesn't boot from USB with EFI boot on Lenovo Thinkpad. Is there a way of still installing it in UEFI mode?

Ok I see this is a known bug in all flavours. Guess will have to be patient then...

---

### Post by ventrical on 2016-09-28
> **PaulW2U said:**
> So [Beta 2]("https://lists.ubuntu.com/archives/ubuntu-announce/2016-September/000212.html") was released earlier today, some six days later than expected.

As predicted (by me) there have been **many** updates. :)

Uh.. but not for unity8.

Regards..

---

### Post by mh2721 on 2016-09-28
> **simonsaysthis said:**
> So disappointed. For some reason the Final Beta still doesn't boot from USB with EFI boot on Lenovo Thinkpad. Is there a way of still installing it in UEFI mode?

Yup, same here, although, I have a desktop with a gigabyte motherboard (z170x-gaming5) and just a blank screen when booting with EFI (no, this motherboard does not have IOMMU setting).
I can boot from legacy mode, but I have no mouse or keyboard (mouse is invisible, and nothing from the keyboard).

Will this be fixed, or is it the end of the road with Ubuntu for me?

---

### Post by ventrical on 2016-09-29
We have to stay in there and keep updating. I am still trying to find out whats going on with all of this  this late in the cycle. There is a lot of breakage. Sometimes that can be a good thing.

Regards..

---

### Post by simonsaysthis on 2016-09-29
> **mh2721 said:**
> Yup, same here, although, I have a desktop with a gigabyte motherboard (z170x-gaming5) and just a blank screen when booting with EFI (no, this motherboard does not have IOMMU setting).
I can boot from legacy mode, but I have no mouse or keyboard (mouse is invisible, and nothing from the keyboard).

Will this be fixed, or is it the end of the road with Ubuntu for me?

Ok so this was my solution.

1. Do a clean install of 16.04
2. Don't update anything post-installation and add any repos
3. Go to terminal and type sudo do-release-upgrade -d

I also tried it from 16.04 where I had already done all the latest upgraded and added all the extras but it gave me problem. So far everything is working fine since I ungraded from a raw install

---

### Post by mh2721 on 2016-09-29
> **simonsaysthis said:**
> Ok so this was my solution.

1. Do a clean install of 16.04
2. Don't update anything post-installation and add any repos
3. Go to terminal and type sudo do-release-upgrade -d

I also tried it from 16.04 where I had already done all the latest upgraded and added all the extras but it gave me problem. So far everything is working fine since I ungraded from a raw install

Thanks for this..Forgot to mention that I use kubuntu, but this happens in all "flavors" of Ubuntu 16.10

So, I did the upgrade, and it seemed to work,  I got to the desktop, but the mouse is invisible, but the keyboard works.   Thanks for the suggestion.

---

### Post by simonsaysthis on 2016-09-30
> **mh2721 said:**
> Thanks for this..Forgot to mention that I use kubuntu, but this happens in all "flavors" of Ubuntu 16.10

So, I did the upgrade, and it seemed to work,  I got to the desktop, but the mouse is invisible, but the keyboard works.   Thanks for the suggestion.

Could you maybe try installing synaptics firmware afterwards or try reconfiguring synclient? Just pondering

---

### Post by mh2721 on 2016-09-30
> **simonsaysthis said:**
> Could you maybe try installing synaptics firmware afterwards or try reconfiguring synclient? Just pondering

I won't be able to do this now because I am trying out other distro's.  When the final is released I will see where I stand.  Thanks for the help/suggestions.

---

### Post by simonsaysthis on 2016-10-03
> **mh2721 said:**
> I won't be able to do this now because I am trying out other distro's.  When the final is released I will see where I stand.  Thanks for the help/suggestions.

Ok cool. Hope to see you back on Ubuntu soon. Good luck

---

### Post by mh2721 on 2016-10-07
> **simonsaysthis said:**
> Ok cool. Hope to see you back on Ubuntu soon. Good luck

I hope!  Progress is being made, with the Oct 7 daily build, I can now boot from the iso!  But, when I get
to the desktop, the mouse is still invisible.  I am hopeful it will be fixed by final.

EDIT: seems like the mouse problem is with the 4.8.x kernel, I installed 4.8 and 4.8.1 in neon and the mouse is invisible, if I go back to 4.4.0 I am ok,  I am also ok on kernel 4.7.6.
I installed 4.7.6 into kubuntu 16.10 oct 8 build, and I have a mouse.  so, I will just stick with neon because it has kde 5.8

---

