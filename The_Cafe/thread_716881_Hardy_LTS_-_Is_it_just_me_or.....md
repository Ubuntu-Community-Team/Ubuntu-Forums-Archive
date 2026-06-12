---
title: "Hardy LTS - Is it just me or...."
date: 2008-03-06
forum: The Cafe
---

### Post by conphara on 2008-03-06
does anyone else think that releasing a LTS version of Ubuntu in April is a bad idea?

Don't get this the wrong way. The decision about making Hardy a LTS release was made some time ago. But it seems to me that it would have made a lot more sense releasing a LTS version this coming October instead, especially considering the following:

It seems that Firefox 3 won't be released in a final state until some time in may. The beta 4 will come out in March 10-14, and beta 5 late March which means that the RCs will be released during April. Therefore there's a strong sense that Hardy will have a Firefox 3 Release Candidate (1 or 2).

OpenOffice 3 will, according to the release schedule, be released in September. And OO3 will be a major upgrade adding a lot of new (important) features.

Gnome 2.22 is, as I see it, a work-in-progress. Switching the main Gnome apps to GVFS isn't finished (Evolution, Rhythmbox and others). And even though Nautilus has been ported to GVFS, it looks like it needs a lot more testing. 

I dont know if I'm right about this, but it seems that the integration of PulseAudio also needs more work.

It just seems that making Ibex a LTS would have been a better choice. 
The selling points would be more clearer:
Firefox 3 (Final)
OpenOffice 3
Gnome 2.24
Linux 2.6.26
Ekiga 3
Gimp 2.5+

At least the new Kubuntu LTS will be released in October simply because of KDE4, its hard to grasp why they don't move the date. It's *only* 6 months.

---

### Post by aimran on 2008-03-06
LTS doesn't mean it should be using the latest uptodate software :). What's more important is stability rather than usability/bling.

Newer versions of the mentioned programs might be buggy/unstable.

---

### Post by CaptainCabinet on 2008-03-06
I'm sure the people behind the release know what they're doing.
The sooner the better I say. :)

---

### Post by mips on 2008-03-06
> **aimran said:**
> LTS doesn't mean it should be using the latest uptodate software :). What's more important is stability rather than usability/bling.

Newer versions of the mentioned programs might be buggy/unstable.

+1 and I think that is the general idea behind a LTS release. Very same reason Kubuntu KDE4 will not be a LTS release.

---

### Post by rubinstein on 2008-03-06
Hardy is not that bad, the only thing that I see with my configuration is a pulseaudio mess, my sound stutters and blubbers. But apart from that, it is really stable, and we still have one and a half month till it is released, so there should be hopefully enough time to make it really nice.

---

### Post by 23meg on 2008-03-06
> **aimran said:**
> LTS doesn't mean it should be using the latest uptodate software :). What's more important is stability rather than usability/bling.

LTS does in most cases mean it should be using the latest up to date software, especially regarding the particular software the OP has cited, because the software you ship in a product with a 3-5 year lifecycle needs to be supportable all along that period, and if you ship old versions whose support will expire upstream sometime within that period, you end up with the burden of maintaining them yourself. Add to that the fact that Ubuntu traditionally tries to stick with upstream to the greatest extent possible, and the fact that you'll be losing a lot of competitive edge by including old versions of popular desktop apps and technologies in a release that you'll support for 3 years on the desktop, and you get the picture.

The OP has a point: lots of new stuff arrived in an untimely manner for an LTS release. There will be a point release of Hardy (8.04.1) in May, and it will include lots of fixes from various upstreams, and possibly the final version of Firefox 3 if it doesn't make it.

---

### Post by macogw on 2008-03-06
There's a possibility that Hardy will be released with FF2 and then in June's 8.04.1 release updated to FF3 final.  As to the other stuff, it's prety darned stable.  The biggest problems you'll find right now are to do with the build farm being hit hard by uploads and not getting all the packages done and out quickly enough so you end up with most packages compiled...and then one dependency being held up in the queue so you can't update.  Screens & Graphics isn't done.  ACPI was recently fixed, and it's working great.  I'm about to go report a Network Manager bug that should be a very easy fix and only crops up with a VPN.  The actual apps are stable.  Nautilus has been holding up very well.  I think it's going to be a good release.

---

### Post by justin whitaker on 2008-03-06
> **23meg said:**
> The OP has a point: lots of new stuff arrived in an untimely manner for an LTS release. There will be a point release of Hardy (8.04.1) in May, and it will include lots of fixes from various upstreams, and possibly the final version of Firefox 3 if it doesn't make it.

Good to hear...although if it will really be that close, then I would delay the 8.04 release.

Which is more important: holding to an arbitrary deadline, or producing the best LTS version yet? If Ubuntu releases 8.04, then there is a respin 30 days later, it will look like Canonical just wanted to get the damn thing out the door....like Microsoft and Vista. 

Keep in mind, I am running Hardy now. I think it will be stable enough by April...but let's, in to paraphrase a song from the 80's "take our time and do it right."

:)

---

### Post by gn2 on 2008-03-06
> **justin whitaker said:**
> 
Which is more important: holding to an arbitrary deadline, or producing the best LTS version yet?

Producing the best version is more important.

Remember that 6.06 wasn't 6.04.

---

### Post by ung/xunil on 2008-03-06
> **gn2 said:**
> Producing the best version is more important.

Remember that 6.06 wasn't 6.04.
I was going to say this :)

Dapper was delayed 2 months for stability, 2 extra months to solve more bugs before the final release. 

Dapper worked much better than Breezy. Edgy was a lot worst than Dapper in bugs - imho. Those 2 extra months did made big a difference.

+1

---

### Post by mozetti on 2008-03-06
I understand that all those programs that the OP mentioned are important to the distro. That being said, if you start factoring in all the other "important" software, you'd never release an LTS for two reasons:

1) It would *never* be the right time -- "software x is coming ... then software y is coming ..."

2) Everyone has their own opinions on what "important" software is, so you get the "why don't we wait for software x, too?" requests.

If 8.04 ships with FFx 2 or FFx 3 RC2, you can always get FFx 3 in from the repos (backports in the worst case scenario) when it's available.

---

### Post by 23meg on 2008-03-06
[QUOTE=justin whitaker]
Which is more important: holding to an arbitrary deadline, or producing the best LTS version yet? If Ubuntu releases 8.04, then there is a respin 30 days later, it will look like Canonical just wanted to get the damn thing out the door....like Microsoft and Vista.
[/QUOTE]

Vista is a red herring, since Ubuntu follows a [time based release model]("https://wiki.ubuntu.com/TimeBasedReleases"), and is developed in an open and distributed way, unlike Windows. Vista being delayed had to do with Microsoft as the sole author of the software being unable to meet certain deadlines; it was an internal matter. When developing an operating system with FOSS, you're dependent on the schedules, politics, methodologies, you name it, of hundreds of independent projects. The comparison just doesn't work.

A respin of a proprietary, in-house developed OS that has a "whenever we want to" release schedule a month after release would look bad. But it's more than acceptable for an openly developed OS with a fixed six month release cycle.

---

### Post by justin whitaker on 2008-03-06
> **23meg said:**
> Vista is a red herring, since Ubuntu follows a [time based release model]("https://wiki.ubuntu.com/TimeBasedReleases"), and is developed in an open and distributed way, unlike Windows. Vista being delayed had to do with Microsoft as the sole author of the software being unable to meet certain deadlines; it was an internal matter. When developing an operating system with FOSS, you're dependent on the schedules, politics, methodologies, you name it, of hundreds of independent projects. The comparison just doesn't work.

A respin of a proprietary, in-house developed OS that has a "whenever we want to" release schedule a month after release would look bad. But it's more than acceptable for an openly developed OS with a fixed six month release cycle.

23, I have to disagree with you there.

It doesn't really matter what we think of time based release cycle, or whether the comparison between Ubuntu and Vista is valid or not: what matters is what happens when CNET, Ziff-Davis, Forbes, Wired, and all the other press types get their hands on it. 

Reviewers and end users are going to approach it using their existing mental framework...and if the release  is buggy, or for some reason does not contain the latest software, then Ubuntu is going to be reported widely as not living up to the hype. 

I think it will be inevitable that Vista comparisons will be made...while you see it as a red herring, I don't think most of the general public sees it that way. 

Ubuntu has gone from just another Linux desktop to the poster child, the representative, of Desktop Linux, usually mentioned in the same sentence as XP and OSX. 

So that's why I urged caution. 

I hope that makes sense.

---

### Post by 23meg on 2008-03-06
There's not much we can do about people who will refuse to make an effort to understand why things are done the way they are done. 

If the release is delayed, a certain set of people will complain. If it's released on time, and a point release follows, a separate set of people will. If it's released on time, no point release follows, and some outstanding bugs remain unfixed, another set will.

My point is that time based releases will always inevitably involve compromises. There's no way to make everyone happy, and keep on schedule at the same time.

---

### Post by igknighted on 2008-03-06
I don't think there is anything wrong with releasing Hardy in April as planned, and I disagree with the OP about the LTS.  The Ubuntu LTS is really only relevant for servers, as desktop users will always want or need the latest applications.  And really, what of the applications listed are truly relevant for servers?  Not too much.  And I really don't see anything on the horizon that is worth waiting for in the server department, aside from the new Samba release (Samba 4), which is in alpha and doesn't have a clear timetable for release.

Oh, and don't count on anything coming through backports.  Ubuntu has never to this point backported major applications, so don't count on it starting now.

---

### Post by p_quarles on 2008-03-06
> **igknighted said:**
> I don't think there is anything wrong with releasing Hardy in April as planned, and I disagree with the OP about the LTS.  The Ubuntu LTS is really only relevant for servers, as desktop users will always want or need the latest applications.  And really, what of the applications listed are truly relevant for servers?  Not too much.  And I really don't see anything on the horizon that is worth waiting for in the server department, aside from the new Samba release (Samba 4), which is in alpha and doesn't have a clear timetable for release.

Oh, and don't count on anything coming through backports.  Ubuntu has never to this point backported major applications, so don't count on it starting now.
That's not the case. For home users, yes, LTS is largely unimportant. LTS is aimed at enterprise usage, and enterprise usage includes both servers and workstations.

---

### Post by zachtib on 2008-03-06
now that I think about it, I think the OP has a point, 8.10 sounds like it would have made a good LTS release, with new versions of several of Ubuntu's key packages (and don't forget NetworkManager 0.7, which looks like it won't make hardy).  With all those improvements, people may have been able to stick with the release on the desktop for a few release cycles without feeling the need to upgrade.

Anyways, I'm still looking forward to Hardy.  I've been keeping my server on LTS releases only, so I finally get to upgrade it :)

---

### Post by macogw on 2008-03-06
The respin is generally go get all the updates to that point out on the disk, instead of waiting 5 hours to download them all.  That's what 6.06.1 and 6.06.2 were.

---

### Post by unityofsaints on 2008-03-06
> **conphara said:**
> 

It just seems that making Ibex a LTS would have been a better choice. 
The selling points would be more clearer:
Firefox 3 (Final)
OpenOffice 3
Gnome 2.24
Linux 2.6.26
Ekiga 3
Gimp 2.5+

At least the new Kubuntu LTS will be released in October simply because of KDE4, its hard to grasp why they don't move the date. It's *only* 6 months.

There is a good reason why Hardy is LTS: Dapper users were told 2 years ago that there would be another LTS two years down the road- not 2 years + 6 months.

Secondly, these apps you mention are actually a good reason why Canonical SHOULDN'T hang on till October!

- OpenOffice 3 will be a huge step forward and still buggy as hell in 6 months (IF it will be out at all by then)
- Ubuntu is design to sync in with each new Gnome release, so Gnome 2.22 WILL be ready in time. Nothing to be gained by waiting for .24
- The Kernel version matters little. Canonical will always go with whatever is stable at the time, since the Kernel has been developed on a consistent basis since god-know-when it doesn't matter much if 2.6.24 or .26 or .28 is included, since it will always be "outdated" in the minds of some by the time release comes around.
- AFAIK Gimp still follows the evens = stable, odds = release mantra so waiting until .25 gets going would give you a less stable Gimp!
- Ekiga 3? Who cares? I don't know of anyone using it, as far as I can see it's just included because it's part of the Gnome desktop and FOSS unlike Skype, the more popular choice.
- Firefox 3 beta 3 is already more stable than FF2 as it is and there will be another few releases between now and the release of Hardy. Believe it or not I've been using it since Alpha 7 (that's 4 major development releases ago!) and it's never given me as many crashes as 2.xx.

IMO Canonical is right on in making this one LTS.

---

### Post by Sef on 2008-03-06
> Dapper was delayed 2 months for stability, 2 extra months to solve more bugs before the final release. 

Dapper was delayed 6 weeks so more work could be done on language packs.

---

### Post by CaptainCabinet on 2008-03-06
> **unityofsaints said:**
> There is a good reason why Hardy is LTS: Dapper users were told 2 years ago that there would be another LTS two years down the road- not 2 years + 6 months.

Secondly, these apps you mention are actually a good reason why Canonical SHOULDN'T hang on till October!

- OpenOffice 3 will be a huge step forward and still buggy as hell in 6 months (IF it will be out at all by then)
- Ubuntu is design to sync in with each new Gnome release, so Gnome 2.22 WILL be ready in time. Nothing to be gained by waiting for .24
- The Kernel version matters little. Canonical will always go with whatever is stable at the time, since the Kernel has been developed on a consistent basis since god-know-when it doesn't matter much if 2.6.24 or .26 or .28 is included, since it will always be "outdated" in the minds of some by the time release comes around.
- AFAIK Gimp still follows the evens = stable, odds = release mantra so waiting until .25 gets going would give you a less stable Gimp!
- Ekiga 3? Who cares? I don't know of anyone using it, as far as I can see it's just included because it's part of the Gnome desktop and FOSS unlike Skype, the more popular choice.
- Firefox 3 beta 3 is already more stable than FF2 as it is and there will be another few releases between now and the release of Hardy. Believe it or not I've been using it since Alpha 7 (that's 4 major development releases ago!) and it's never given me as many crashes as 2.xx.

IMO Canonical is right on in making this one LTS.

Well said! :)
I think we should all be trusting Canonicals decision to release it when it's been announced. They know what they're doing. 
There's not much point complaining as well because we can't change the release date. :)

---

### Post by zachtib on 2008-03-06
I guess at this rate, hardy can be nice and stable so that 8.10 can have lots of bleeding-edge stuff.  Meaning, everything that the OP listed can make it into 8.10, and people that want a more stable selection of packages can stick with hardy

---

### Post by mips on 2008-03-07
> **macogw said:**
> The respin is generally go get all the updates to that point out on the disk, instead of waiting 5 hours to download them all.  That's what 6.06.1 and 6.06.2 were.

Besides the respins I think they should offer xdeltas as well. Why download the entire cd again when you only need a portion of it.

---

### Post by tdrusk on 2008-03-07
I think all will be fine. I prefer using older versions of programs if they are more stable. Look at Debian Etch. It's rock solid.

---

### Post by plun on 2008-03-07
> **tdrusk said:**
>  Look at Debian Etch. It's rock solid.

Well, and "rock boring"...but of course there must be a balance.

I prefer a rock solid Debian ground (as it is) but with newest 
application/kernel level, the Ubuntu way.

Lots of Debian users are going to switch over to Lenny or has already done it because Etch is so old now.  I have not checked latest roadmap for Lenny.

I also believe that Debian and Ubuntu must be closer to each other in long term.   Debian is "Ubuntus mother" and will be.

---

### Post by Extreme Coder on 2008-03-07
Can't help but agree with the OP..
but there's nothing we can do ;)

---

### Post by 23meg on 2008-03-07
> **mips said:**
> Besides the respins I think they should offer xdeltas as well. Why download the entire cd again when you only need a portion of it.

You can [use rsync]("https://help.ubuntu.com/community/RsyncCdImage").

---

### Post by macogw on 2008-03-07
> **tdrusk said:**
> I think all will be fine. I prefer using older versions of programs if they are more stable. Look at Debian Etch. It's rock solid.
And crashes on hardware made in 2006 or later.  If I ever reinstall Etch on this laptop, I'll have to find some way to keep it running long enough to compile a modern kernel.

---

