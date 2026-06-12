---
title: "Ubuntu support duration"
date: 2013-06-26
forum: Ubuntu, Linux and OS Chat
---

### Post by Skara Brae on 2013-06-26
I am reading that Ubuntu 13.04 (and Xubuntu, too) will be supported for _*ONLY*_ nine months.

Why just 9 months? What after those 9 months? Installing (yet again) the new version? I thought one would be rid of installing a new version every time again (like with Windows), but it seems that Ubuntu (at least) is becoming just like MS Windows. Why not sticking with one version for several years; like LTS editions?

Only nine months. Isn't this, kind of, insane?

---

### Post by snowpine on 2013-06-26
The 9-month support versions are intended for people who like to upgrade every 6 months.

LTS versions are supported 5 years for people who don't like to upgrade every 6 months.

The choice is yours.

Windows is supported many years (XP has been supported since 2001, before Ubuntu even existed!!!) so I don't understand your "Ubuntu is becoming just like MS Windows" analogy at all.

---

### Post by varunendra on 2013-06-26
> **Skara Brae said:**
> Why just 9 months?................Only nine months. Isn't this, kind of, insane?

Perhaps this may explain why : [http://ubuntuforums.org/showthread.php?t=2156323&p=12701351#post12701351](http://ubuntuforums.org/showthread.php?t=2156323&p=12701351#post12701351)

**EDIT:**
I realized later that that post is perhaps unnecessarily long, so skip to the Third heading "Why is Standard Release Support Period is Short ?"

---

### Post by thiebaude on 2013-06-26
I guess the simple answer for the op would be that Ubuntu is released every 6 months.

---

### Post by sanderj on 2013-06-26
> **snowpine said:**
> 
Windows is supported many years (XP has been supported since 2001, before Ubuntu even existed!!!) so I don't understand your "Ubuntu is becoming just like MS Windows" analogy at all.

:)

---

### Post by Erik1984 on 2013-06-26
9 months sounds fair to me. I guess most people running the *non-LTS* want to upgrade after at most a few months after the next release. 13.10 will be release near the end of October. You can upgrade till somewhere in January 2014 without losing support.

---

### Post by Skara Brae on 2013-06-26
> **snowpine said:**
> Windows is supported many years (XP has been supported since 2001, before Ubuntu even existed!!!) so I don't understand your "Ubuntu is becoming just like MS Windows" analogy at all.
You are right. I wasn't being very correct there. I take back what I wrote there.

> **varunendra said:**
> Perhaps this may explain why : [http://ubuntuforums.org/showthread.php?t=2156323&p=12701351#post12701351](http://ubuntuforums.org/showthread.php?t=2156323&p=12701351#post12701351)
Thank you, varunendra, that was interesting to read.

I have been reading about the difference between the way Ubuntu and other distros are and the way that, f.e., Debian is. I find the Debian system, where one updates one single version, more user friendly; I have read about problems upgrading from one Ubuntu version to the next, which I luckily never had.

I have always stayed with a LTS edition. If 12.04 hadn't had Unity, I would have gotten 12.04.

Thing is: I am just a very "conservative" guy. I don't like changes. Too often I have seen how changes "broke" my computers - yes, I am talking about Windows now. Even though Ubuntu is Linux, I wouldn't want to "change" to a new edition every n-months. To me, a computer is a means to reach things, not the thing to reach itself (i.e. being busy with upgrading my OS every N-months; I have more pleasant things to do with/at my computers than than, hence the LTS editions).

---

### Post by Peripheral Visionary on 2013-06-26
> **Skara Brae said:**
> 

I have always stayed with a LTS edition. If 12.04 hadn't had Unity, I would have gotten 12.04.


I too stick with LTS releases.  But Unity is too much for my old hardware, and my first Linux was Xfce, so I'm on Xubuntu 12.04.  It's as rock-stable, responsive, and fast as 10.04 was.  Sticking to LTS releases is a great long-term solution for "casual users," and Xubuntu is a great solution for those with older computers.

---

### Post by sanderj on 2013-06-26
> **Peripheral Visionary said:**
> I too stick with LTS releases.  But Unity is too much for my old hardware, and my first Linux was Xfce, so I'm on Xubuntu 12.04.  It's as rock-stable, responsive, and fast as 10.04 was.  Sticking to LTS releases is a great long-term solution for "casual users," and Xubuntu is a great solution for those with older computers.

How do you handle new hardware that's only supported in newer Linux / Ubuntu versions?

---

### Post by snowpine on 2013-06-26
> **Skara Brae said:**
> I have been reading about the difference between the way Ubuntu and other distros are and the way that, f.e., Debian is. I find the Debian system, where one updates one single version, more user friendly; I have read about problems upgrading from one Ubuntu version to the next, which I luckily never had.

I have always stayed with a LTS edition. If 12.04 hadn't had Unity, I would have gotten 12.04.

Thing is: I am just a very "conservative" guy. I don't like changes. Too often I have seen how changes "broke" my computers - yes, I am talking about Windows now. Even though Ubuntu is Linux, I wouldn't want to "change" to a new edition every n-months. To me, a computer is a means to reach things, not the thing to reach itself (i.e. being busy with upgrading my OS every N-months; I have more pleasant things to do with/at my computers than than, hence the LTS editions).

You sound like a perfect candidate for the LTS releases.

You would probably also enjoy these distros, which have stable software and long support cycles: Debian, Slackware, CentOS, Scientific Linux.

---

### Post by varunendra on 2013-06-26
> **sanderj said:**
> How do you handle new hardware that's only supported in newer Linux / Ubuntu versions?

By -
[LIST=1]
[*]Installing backported modules from within repository
[*]Compiling "compat" driver packages
[*]Installing newer kernels from within repository (like "linux-generic-lts-raring" package in 12.04)
[*]Installing an even newer kernel from kernel ppa mainline
[/LIST]

...in the incremental order of possible bad side effects or breaking functionality, all of which are still better than changing OS every 6 or 9 months *(given the fact that once you installed some proprietary stuff on it, a distro-upgrade is almost guaranteed to result in a broken OS)*. That is really a pure geeky stuff, something absolutely not recommended for production systems or for those who just want a working system without wasting a lot of time in making it work.

Although I'd agree that there are still some ultra modern hardware items in the market, always, that will still work ONLY with the latest release. But that is not a very frequent case, and such (very few) users only need to compromise until the release of the next LTS.

So the point is, if someone has that kind of hardware, they do have some solutions as mentioned above which solve most of such cases and the latest release is not necessarily the only solution. But yes, it IS an easier and quicker solution if the user can wait until the next LTS.

---

### Post by grahammechanical on 2013-06-26
Mark Shuttleworth wanted to do away with the interim releases altogether and just have LTS releases every two years (with 5 years support) and a development version that was daily updated from one release to another. Mark wanted Raring to start that rolling development process. There was need for a change in the way Ubuntu was developed and released and a compromise was reached. See two of Mark's blogs on this subject.

[http]("http://www.markshuttleworth.com/archives/1246")[://www.markshuttleworth.com/archives/1228]("http://www.markshuttleworth.com/archives/1228")

[http://www.markshuttleworth.com/archives/1246](http://www.markshuttleworth.com/archives/1246)

I am reminded of a line from an old song. "but it's all right now, I learned my lesson well. You see, ya can't please everyone, so ya got to please yourself." (Garden Party Rick Nelson). Don't be surprised When Mark does exactly that.

Regards.

---

### Post by mastablasta on 2013-06-27
current way seems like a good idea. the only think bothering me is AMD dropping support for 12.04.2 release which IMO should be supported by their legacy driver. 

at the moment i am on 12.04 i plan to upgrade probably when 14.04.1 comes out.

i do not liek ocnstant brekagaes, but i would go with short life clycle releas ein case i had a new hardware. at least until LTS got some components enabled with hardware enablement point release.

---

### Post by monkeybrain2012 on 2013-06-27
If they want more people to use LTS then I hope they do backport updates more meaningfully instead of expecting people to stick with an old, broken system for 5 years.  Case in point, Unity 5 have many bugs which are fixed in 6 and 7 but in Precise they are still ugraded only to a newer version of Unity5. What is the point of offerning an upgrade which is known to be broken? Maybe they will fix that in August when 12.04.3 comes put, or maybe not.

---

### Post by monkeybrain2012 on 2013-06-27
> **varunendra said:**
> 

So the point is, if someone has that kind of hardware, they do have some solutions as mentioned above which solve most of such cases and the latest release is not necessarily the only solution. But yes, it IS an easier and quicker solution if the user can wait until the next LTS.

So are you saying that people should buy their hardware based on Ubuntu's release cycle?  

If the interim releases are reasonably stable like 13.04 then there shouldn't be a problem. Fedora has short support cycles (some say it is perpetual beta), it is more bleeding edge than Ubuntu yet manage to be quite stable, I think Canonical should be able to manage that (One reason Mark S cited to justify the new "rolling" approach is that testing and quality assurance has become a lot more reliable now) What I don't want is the Debian model, It offers basically only choices between "stable" release which is too old and almost guaranteed not to work with newer hardware and "unstable" which is so unstable that it is almost guaranteed to break,

---

### Post by varunendra on 2013-06-27
> **monkeybrain2012 said:**
> So are you saying that people should buy their hardware based on Ubuntu's release cycle?

I'm unable to understand how you concluded that from the quoted part of my post (or entire post), but yes, this would be a good idea if we are going to buy a new system and are sure to use Ubuntu on it.

My response was regarding the "latest" hardware in the market, and if someone can't wait until its support is included in the default updates, and doesn't want to make 'extra' efforts to make it work, then why not choose a hardware that is already supported?

> If the interim releases are reasonably stable like 13.04 then there shouldn't be a problem.
Not a problem for people who don't mind re-installing and configuring everything from scratch. But definitely a problem for those who don't want to do that every 6 or 9 months.

Like I pointed out in my earlier post, if you have installed anything proprietary and/or from PPAs, a distribution upgrade is almost certainly going to break or at least cause some breakage in functionality. That's why most of us here always recommend a 'clean install' instead of upgrade.

I haven't used Fedora or Debian, so can't comment on them or any comparison with them.

---

### Post by buzzingrobot on 2013-06-27
Reducing the non-LTS support period must have an impact on resource use.  That would free people to work on other areas, or free Canonical to reduce staff.

A Fedora release is, I think, supported until the second following release comes out.  I.e, Fedora 19 will be supported until Fedora 21 comes out.  Since Fedora targets a 6-month release cycle, that's one year.

Debian 7 is, at the moment, and by Debian standards, reasonably up to date.  But, two years from now, it won't be. 

CentOS, Scientific, etc., are all de-trademarked builds of Red Hat Enterprise Linux. I used CentOS for an extended period as  a desktop.  It's as advertised:  solid and reliable.  The downside is that, while Red Hat is very, very good at bug fixes for RHEL (which then are rolled into CentOS), including backporting and/or creating many kernel fixes, the core components of RHEL 6, the current release, (at least the components relevant to desktop use, like GTK)  are showing their age.  I eventually was unable to use the applications I needed because they required newer libraries, etc. RHEL 7, due out later this year (probably) will be more or less a hybrid of the last few Fedora releases, so should be up to date.

---

### Post by mastablasta on 2013-06-27
Fedora is not really used in businesses where the money is. imagine having different hardware liek 10000 desktops and the doing upgrade on them every 6 months... it's a nightmare. which is why companies prefer stable environment. and sometimes you don't need latest package to do your work.

i have WinXP at work with ms office 2007, IE8. current office is 2013 i believe, while the current OS is windows 8, and IE is at 11 or maybe 12 i don't know as i really don't follow those. yet any major software upgrade (let alsone OS upgrade) seems very very far away (unless my computer breaks)

---

### Post by MadmanRB on 2013-06-27
I do feel it a shame that support for interim releases are shorter now, considering Ubuntu has a rather uneven track record on releases.
In fact here is my honest (if not blunt) opinions on each release since I first started using it:
13.04 raring	 = great
12.10 quantal = okay
12.04 LTS precise = decent though unstable at times
11.10 oneiric = great (actually it was more stable then 12.04)
11.04 natty	 = crap
10.10 maverick = decent
10.04 LTS lucid = fantastic 
9.10 karmic	= decent
9.04 jaunty = crap
8.10 intrepid = good	
8.04 LTS hardy = fantastic
7.10 gutsy = crap
7.04 feisty = crap
6.10 edgy = good
6.06 LTS = good

so yeah ubuntus track record is rather mixed.
To be honest I find Raring more stable then Precise, 12.04 is very buggy for a LTS.
If i will use 13.04 I just hope that 13.10 isnt crap.
But since 13.04 broke the tradition of uneven number + .04 is crap pattern, I bet 13.10 will be a big poo stain to make up for it.
Not saying it will but ubuntu has a pattern for mucking it up every so often.

---

### Post by buzzingrobot on 2013-06-27
> **mastablasta said:**
> Fedora is not really used in businesses where the money is. imagine having different hardware liek 10000 desktops and the doing upgrade on them every 6 month...

Well, no, but I took it this thread was focusing on individual home users.

Red Hat makes its money from selling support subscriptions for RHEL, which Fedora seeds, more or less. It is to both Red Hat's and it's customers' advantage that RHEL remain as stable as possible.  Hence, Red Hat seldom adds new code to RHEL simply to add a new feature or capability. That's why it's attractive to enterprise users:  Put it on all the machines in the server room, buy support contracts, call RH if and when something breaks.

---

### Post by monkeybrain2012 on 2013-06-28
They cut short the support of 13.04 and then bring in huge changes in 13.10, it looks like the next while is going to be bumpy.
[http://www.omgubuntu.co.uk/2013/06/mir-display-server-to-ship-default-in-ubuntu-13-10](http://www.omgubuntu.co.uk/2013/06/mir-display-server-to-ship-default-in-ubuntu-13-10)

Either they are really reckless or Mir is really great. I don't want to, but when push comes to shove I can reinstate 12.04 when 13.04 reaches eol ( I have cloned the whole thing and update regularly) ,  or switch to some other distros.

---

### Post by MadmanRB on 2013-06-28
Well I am not worried about Mir, as it will have a fallback to x most likely.
Mir wont ever fully replace x as long as older cards are still in use.
It would be stupid to go full Mir, heck it will take years before that ever happens.
Even if Mir creeps in there will still probably be a x fallback.
People still use proprietary cards too, gaming is growing on linux so Mir wont fill in any gaps in that area for some time.

---

### Post by monkeybrain2012 on 2013-06-28
> **MadmanRB said:**
> Well I am not worried about Mir, as it will have a fallback to x most likely.
Mir wont ever fully replace x as long as older cards are still in use.
It would be stupid to go full Mir, heck it will take years before that ever happens.
Even if Mir creeps in there will still probably be a x fallback.

As far as 13.10 goes it is probably ok., but the plan is to remove X fallback in 14.04. 

[http://fridge.ubuntu.com/2013/06/27/mir-plans-in-13-10/](http://fridge.ubuntu.com/2013/06/27/mir-plans-in-13-10/)

---

### Post by MadmanRB on 2013-06-28
Well if 14.04 sucks its all over for ubuntu for choosing something so unready.
Hopefully this Mir stuff will become accepted and adapted, I am sure if you are running free drivers like myself things will be okay.
But those on gaming cards will probably be left in the dust unless Ubuntu gets a x fallback.

---

### Post by buzzingrobot on 2013-06-28
If those who know think Mir is ready for 13.10, I have no basis for disagreeing. Focused development can move faster than the often time-available scattered development we sometimes see in FOSS.

If I understand, Mir in 13.10 will not support proprietary video drivers, so the X fallback will be used. That's a bit like the Nouveau/proprietary split, since Nouveau could (can?) kill the boot with certain kernels.

Wayland vs Mir vs X is a fuss that I'm not interested in. Competition drives better products.  I'll use the best one.

---

