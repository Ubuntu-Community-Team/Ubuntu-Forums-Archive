---
title: "Linux for me"
date: 2013-08-11
forum: Ubuntu, Linux and OS Chat
---

### Post by Annq on 2013-08-11
I have been using Ubuntu for many years now, and it seems that I have spent most of my time fixing things (which I like to do, however, I need to move on to actually using it).   I love having it and like it way better than windows but am tired of both my Ubuntu machines crashing every few hours, while my windows and OS X hosts don't have that problem.  I recently installed Fedora as a VM on Windows 8 and it works without issue.  I am thinking about to swtiching my server and hosts to Fedora 19 on VMs out of exacerbation due to the unresolved crashes.  What I would like to know from experienced users is if I would probably have the same problem with Fedora.  If so, I will stick with Ubuntu or try another flavor.

Does anyone have some experience with both Ubuntu (xfce especially) and Fedora (xfce)?  I am not interested in windows and mac, so please don't point me to these OSs.

Thanks,
Anne

---

### Post by King Dude on 2013-08-11
I have had few bugs on my system, even though I'm running the development release with open source graphics driver and the experimental file system Btrfs. I am running Ubuntu 13.10 x64.

Perhaps you should describe your system for us?

---

### Post by SweetAurora on 2013-08-11
Switching would be a good thing, Ubuntu is more of a casual user desktop now and while it has a server version, that isn't Canonical's point of interest. Fedora makes for good server installs, but you will have to reload it every time a new version of Fedora comes out as Fedora has no easy upgrade system in place. But I have no idea if that carries over to the simpler server install. If you want a stable, long lasting server, try Debian. It's much like Ubuntu and no need to learn new commands! :)

---

### Post by coldraven on 2013-08-11
I've been using Ubuntu since version 8.04 and have never had a crash. 
It was the constant repairs to Windows that made me move to Linux.

---

### Post by The-Server-4dmin on 2013-08-11
I normally find that one release back is really stable. You should try that.

---

### Post by 1clue on 2013-08-11
Fedora is a community project, it will probably not be much more stable than Xubuntu.

If you want stability and low maintenance, try something based on an enterprise linux, like CentOS.  That will keep you in the RedHat realm you seem to have already chosen, get you highly tested and stable software (since it's based on RedHat Enterprise Linux), and still be free.

Another alternative would be some Suse variant.  Don't know what the equivalent of CentOS would be for that, but surely there is one.

The main disadvantage to this approach AFAICT is that the distro you're using focuses almost entirely on removing commercial software from an Enterprise-oriented distro.  I haven't been on CentOS forums, not sure how much support there is.

---

### Post by alphacrucis2 on 2013-08-11
The crashing issues could be related to driver/hardware compatibility problems. A distro running as a VM will see a different view of the hardware than the native OS so there is no guarantee that fedora wont have trouble running native just because it runs ok in a VM. That said fedora 19 has a more recent kernel than the current u 13.04 so it might help. I find both Ubuntu 13.04 and fedora 19 work well with my hardware using the proprietary nvida graphics driver. One thing i found with fedora 19 with gnome shell - adding a bunch of extensions is a must, whereas ubuntu with unity is more immediately useable out of the box. Once GS is suitably tweaked I don't have any prefereence for one over the other. I haven't tried xfce so I don't have anything to say on that.

---

### Post by Ninja&gt;Master on 2013-08-12
I've been running Ubuntu + LXDE (Lubuntu) for a while now and its running flawlessly. I don't know why you are getting into so much trouble :/.

---

### Post by grahammechanical on 2013-08-12
Looking back over the years it seems that every time Microsoft released a new version some journalist was advising against upgrading until after the first service pack came out. Is any OS ever complete? Especially in Linux. I think that the Ubuntu fixed release schedule might be great for moving the distribution forward but not so great for finishing it. It will never be finished will it? This is life in Linux.

You may find yourself in a similar situation once you have been using some other distribution a number of years. Does it really matter if you use something other than Ubuntu? Life is too short and filled with too much pain to turn our choice of a Linux distribution into an act of war.

Regards.

---

### Post by zealibib slaughter on 2013-08-12
I agree with sweetaurora debian stable branch is exactly that, completely stable and rock solid.  For a server it is great.[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1841591")

---

### Post by 1clue on 2013-08-12
Waiting on a major release until the bugs shake out is just prudence.  Some companies wait until the next major release before they adopt the prior one.  Some of my customers (yes, plural) still use XP and refuse to upgrade until "something better comes out."  I'm talking about fortune 500 companies.

Using something other than Ubuntu:
There's a lot of FUD out there about other distros.  They're generally not that much harder to install than Ubuntu.  They're generally set up and ready to go out of the box, unless you get an "expert" distro like Gentoo or LFS.

People here should go try out Fedora and Debian and a few other mainstream distros.  I'm not advocating that they abandon Ubuntu, I'm just saying they should play around with other distros, see what's out there.  Last time I loaded Debian I was amazed at how much difference there isn't.

Ubuntu users seem to think that Ubuntu is the only distro that's easy to set up and use.  This is extremely not true.  The basic desktop installation of Ubuntu is simpler than most other distros, at least if you follow all the defaults, but that's about it.  It takes you 5 minutes of "human" time to install Ubuntu instead of 15 on some other distro.  Set it up, let it go and go do something else for awhile.

Some of you guys are using old hardware, but most probably have something recent.  Load up VirtualBox or something, try out another distro and see how it goes.  It'll take you an afternoon to get up and running, and you can see what it's all about.

---

### Post by malspa on 2013-08-12
> **Annq said:**
> Does anyone have some experience with both Ubuntu (xfce especially) and Fedora (xfce)?

> **1clue said:**
> Fedora is a community project, it will probably not be much more stable than Xubuntu.

Agreed.

Long-time Ubuntu user here, but only for desktops, not server. And I also spent some years using Fedora, but not with Xfce -- GNOME and KDE only. So I can't comment on those things.

All that being said, I have not had problems with Ubuntu crashing on my computers, so it does seem like a hardware compatibility issue.

I like Fedora but there are some drawbacks like the short support period, and stability can be an issue, it's just the nature of the beast. But I still think it's a great distro to run; just happens that I decided to go in another direction after F18.

I do use Xfce in Debian Wheezy and in another distro. I really think that either Debian Stable Xfce or Xubuntu would be a good way to go, as long as everything works out with the hardware.

---

### Post by mamamia88 on 2013-08-12
Hell I'm using arch which is a rolling release that comes out with new updates constantly and I've never had any major breakage.   I'm sorry you're having such bad luck.   I would try to determine first if it's a hardware compatability issue before switching to other distros.  Because if it's not supported by linux fully yet it won't matter what distro you use.   Then if you find out it isn't a hardware compatability issue you might want to try either a distro which is more up to date then ubuntu like arch or something that is older than ubuntu like debian stable.   One fixes bugs as they come  while the other just sticks to older bug free versions of packages.

---

### Post by ssam on 2013-08-12
no linux distro should be crashing regularly.

some distros are described as stable (e.g. debian, rhel/centos), but that is a measure of how often things change. you can install debian stable and know that no packages will undergo large upgrades. so if you have scripts that expect specific versions of things, they will keep working. the extreme other end is distros like fedora, where you will get whole new kernels as normal updates.

this does not make debian less likely to crash than fedora. fedora may have a newer kernel that fixes some important bug and reduces crashes for you.

I'd recommend doing memory and disk checks, [https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware) , avoiding the closed source drivers and reporting bugs for any issues that remain.

---

### Post by monkeybrain20122 on 2013-08-12
> **1clue said:**
> Fedora is a community project, it will probably not be much more stable than Xubuntu.

If you want stability and low maintenance, try something based on an enterprise linux, like CentOS.  That will keep you in the RedHat realm you seem to have already chosen, get you highly tested and stable software (since it's based on RedHat Enterprise Linux), and still be free.

.

Actually I am very impressed with Fedora, it combines cutting edge with stability much better than Debian or Ubuntu. Fedora is not a rolling release but practically it is like one but very stable, you get the latest and greatest but not a horrible buggy mess like Debian experimental. In Ubuntu you can get that level of freshness and usability only if you enable a lot ppas (but ppas are more flexible as you can selectively upgrade or downgrade things by enabling or purging them, there are no such options when things are upgraded through the main repos)

 I however prefer apt-get to yum and Fedora doesn't have a good software manager like synaptic or muon (Yumex is the best so far, but not even close), also there are some oddities one need to get used to like overly strict Selinux policies and the fact that there are less precompiled software in Fedora than in Ubuntu (so one is expected to compile more from source) and there are less readily available tutorials and guides. Fedora also sometimes breaks compatibility with third party software because of its rapid changes, e.g need to use rpmrebuild to repuild some packages like google earth in order to install. All these can be problematic to new users, Ubuntu is definitely more suitable as a first Linux distro.

Also I like Unity, it is one plus for Ubuntu. 

At the moment Ubuntu has a slight edge over Fedora but I am very comfortable with it and can use it as my main system if I need to (say if Mir breaks my display)

As for Centos, unless you run a server I wouldn't recommend it for a normal desktop, it is too old and a lot reasonably up to date software (not bleeding edge) would not even install there (especially multimedia)

---

### Post by monkeybrain20122 on 2013-08-12
> **malspa said:**
> 
I like Fedora but there are some drawbacks like the short support period, and stability can be an issue, it's just the nature of the beast. But I still think it's a great distro to run; just happens that I decided to go in another direction after F18.



Well actually it has longer support than Ubuntu unless you use LTS. :)

You are missing out if you stop after F18, F19 is one of the best releases recently(since F15/F16). I installed it the day after it came out and it has been remarkably bug free (can't say the same about Ubuntu, usually I wait a month or two to install the latest Ubuntu for bugs to be ironed out) F18 was great once you get over the shocking installer, but it is fixed in F19. F18 took a bit long to boot, but F19 is very fast, about the same or may be slightly faster than Ubuntu 13.04.

---

### Post by malspa on 2013-08-12
> **monkeybrain20122 said:**
> Well actually it has longer support than Ubuntu unless you use LTS.
True. I don't use non-LTS, though.

> **monkeybrain20122 said:**
> You are missing out if you stop after F18, F19 is one of the best releases recently(since F15/F16). I installed it the day after it came out and it has been remarkably bug free (can't say the same about Ubuntu, usually I wait a month or two to install the latest Ubuntu for bugs to be ironed out) F18 was great once you get over the shocking installer, but it is fixed in F19. F18 took a bit long to boot, but F19 is very fast, about the same or may be slightly faster than Ubuntu 13.04.
Good to know. Well, I'd decided to go in another direction with my other distros. I ran Fedora from F14 thru F18 and it was great and everything but I've kinda lost interest for the moment.

---

### Post by 1clue on 2013-08-12
Hey guys,

I'm not dissing fedora or ubuntu or anything else.

There are lots of different types of distros, each with different intent.  One of my distros is Gentoo, which is source-based rolling release.  The epitome of accidents waiting to happen, but I like it.

There are several things that affect stability in Linux.
[LIST=1]
[*]Kernel version:  The newer the kernel major version the more cool features and the newer hardware supported, but the more chance of bugs.
[*]Release cycle or type.  I'll discuss that after this list.
[*]Testing.  If a distro has a lot of support for testing, in means the release cycle is longer and the software tends to be a bit older, in favor of stability.
[*]Updates.  If the distro is slow for feature updates and sort-of-fast for security updates, that tends to make a more stable.
[*]Focus of the distro.  If a distro is focused on Enterprise use, then they will have a really long development cycle, they will have a huge paid testing staff and really good tests.  They'll also tend to have a lot of the configuration already done for you, or a GUI configuration tool.
[/LIST]

Release cycle: You have some basic types, this list is probably not exhaustive:
[LIST=1]
[*]Rolling release.  No new major versions of the distro are ever really released.  They'll number the CDs for sanity, but anyone who keeps updating will always have the latest thing.
[*]Short cycle:  Tend to focus on latest greatest like rolling release, but a bit more sane in terms of stability.  Some testing to get the big bugs out.
[*]Medium cycle:  Tend to find a balance between stability and new functionality.  This is the mainstream user and where Ubuntu is.
[*]Long cycle:  Tend to aim more at stability and less on features.  <rant>They'll leave a really tool off their list just because of one tiny technical detail that never gets resolved.</rant>
[*]Also, the consistency of the release cycle:  Ubuntu is almost militant in that they have a specific time between releases.  I don't think this is very rational.  Most distros get something stable, release it as a major version and then start working on the next one.  They wait until it's good before they release it.
[/LIST]

The OP sounded like he/she was looking for something more enterprise related.

All this stuff is a balance.  Each of us has different requirements or desires for features and stability.  I use several different distros because each of my boxes has a separate set of requirements.  I use Ubuntu where I just want it up and fast, and reasonably new features.  I use Gentoo when I want to play but don't so much care if I have to wipe it off and start over because I did something stupid.  I use a CentOS for stability in a server where I lose money if it's not running.

All that said, you could and many people DO use Ubuntu for stable servers.  It's up to you.  I'm just making recommendations.

---

### Post by will1982 on 2013-08-12
My ubuntu machine is more stable than the windows one.
The only thing that crashes is the stuff *I*&#8203; made

---

### Post by KBD47 on 2013-08-12
If you don't like fixing things, you should be using Debian Stable or Ubuntu LTS 12.04 release. I recommend the Ubuntu spin LXLE which has the LTS support.

---

### Post by Annq on 2013-08-12
> **SweetAurora said:**
> Switching would be a good thing, Ubuntu is more of a casual user desktop now and while it has a server version, that isn't Canonical's point of interest. Fedora makes for good server installs, but you will have to reload it every time a new version of Fedora comes out as Fedora has no easy upgrade system in place. But I have no idea if that carries over to the simpler server install. If you want a stable, long lasting server, try Debian. It's much like Ubuntu and no need to learn new commands! :)

Thanks, Sweet,

Good advice.  I am going to try Debian in a VM to see how it works for me.

---

### Post by Annq on 2013-08-12
> **King Dude said:**
> I have had few bugs on my system, even though I'm running the development release with open source graphics driver and the experimental file system Btrfs. I am running Ubuntu 13.10 x64.

Perhaps you should describe your system for us?

King Dude,

I'm running XFCE 13.04, Raring Ringtail on a 64-bit desktop computer.  It crashes randomly.  I can't find the problem.  It doesn't seem to matter what is running.

Another one I was running was a dual boot XFCE 13.04, Raring Ringtail on a 64-bit laptop, along side Windows 8.  The session randomly restarted only when I used it.   I've had Ubuntu on this machine for years and have only had this problem with ratty.  Yesterday, in frustration, I jetisoned it in favor of a Fedora 19 VM.  We'll see how that goes.  

My other machine is a 64-bit Windows 8 with a Fedora 19 VM.

Thanks,
Anne

---

### Post by Annq on 2013-08-12
> **coldraven said:**
> I've been using Ubuntu since version 8.04 and have never had a crash. 
It was the constant repairs to Windows that made me move to Linux.

coldraven,

That is hard for me to fathom.  I've been enjoying Ubuntu for years and crash my hosts often.   I can't image not ever having a crash.

---

### Post by Annq on 2013-08-12
> **1clue said:**
> Waiting on a major release until the bugs shake out is just prudence.  Some companies wait until the next major release before they adopt the prior one.  Some of my customers (yes, plural) still use XP and refuse to upgrade until "something better comes out."  I'm talking about fortune 500 companies.

I do use XP on two of my boat anchors (really really old laptops).  They are good for dedicated cameras and other things.    

> 
Using something other than Ubuntu:
There's a lot of FUD out there about other distros.  They're generally not that much harder to install than Ubuntu.  They're generally set up and ready to go out of the box, unless you get an "expert" distro like Gentoo or LFS.

People here should go try out Fedora and Debian and a few other mainstream distros.  I'm not advocating that they abandon Ubuntu, I'm just saying they should play around with other distros, see what's out there.  Last time I loaded Debian I was amazed at how much difference there isn't.

Ubuntu users seem to think that Ubuntu is the only distro that's easy to set up and use.  This is extremely not true.  The basic desktop installation of Ubuntu is simpler than most other distros, at least if you follow all the defaults, but that's about it.  It takes you 5 minutes of "human" time to install Ubuntu instead of 15 on some other distro.  Set it up, let it go and go do something else for awhile.

Some of you guys are using old hardware, but most probably have something recent.  Load up VirtualBox or something, try out another distro and see how it goes.  It'll take you an afternoon to get up and running, and you can see what it's all about.

I think I'll try out several flavours on VMs to see how they compare.  I don't want to abandon Ubuntu because its been great over the years, however its time to compare it with some new ones.

---

### Post by Annq on 2013-08-12
> **mamamia88 said:**
> Hell I'm using arch which is a rolling release that comes out with new updates constantly and I've never had any major breakage.   I'm sorry you're having such bad luck.   I would try to determine first if it's a hardware compatability issue before switching to other distros.  Because if it's not supported by linux fully yet it won't matter what distro you use.   Then if you find out it isn't a hardware compatability issue you might want to try either a distro which is more up to date then ubuntu like arch or something that is older than ubuntu like debian stable.   One fixes bugs as they come  while the other just sticks to older bug free versions of packages.
mamamia,

I'm having trouble diagnosing the problem.  But I haven't been focused on hardware because my hosts are fairly new.  Something to look at before punting Ubuntu.

A

---

### Post by Annq on 2013-08-12
> **ssam said:**
> no linux distro should be crashing regularly.

some distros are described as stable (e.g. debian, rhel/centos), but that is a measure of how often things change. you can install debian stable and know that no packages will undergo large upgrades. so if you have scripts that expect specific versions of things, they will keep working. the extreme other end is distros like fedora, where you will get whole new kernels as normal updates.

this does not make debian less likely to crash than fedora. fedora may have a newer kernel that fixes some important bug and reduces crashes for you.

I'd recommend doing memory and disk checks, [https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware) , avoiding the closed source drivers and reporting bugs for any issues that remain.

ssam,

Yes.  That's the type of advice I've been looking for.  Any links towards eliminating the problem will at least give me something new to go on.

This is my first post to this site.  I must admit that I didn't expect so many replies and such great support.  

Thanks

---

### Post by Annq on 2013-08-12
> **monkeybrain20122 said:**
> snip... I however prefer apt-get to yum and Fedora doesn't have a good software manager like synaptic or muon ...

I also prefer apt-get over yum and have not yet seen a match for synaptic.

---

### Post by Annq on 2013-08-12
> **1clue said:**
> Hey guys,

I'm not dissing fedora or ubuntu or anything else.

There are lots of different types of distros, each with different intent.  One of my distros is Gentoo, which is source-based rolling release.  The epitome of accidents waiting to happen, but I like it.

There are several things that affect stability in Linux.
[LIST=1]
[*]Kernel version:  The newer the kernel major version the more cool features and the newer hardware supported, but the more chance of bugs.
[*]Release cycle or type.  I'll discuss that after this list.
[*]Testing.  If a distro has a lot of support for testing, in means the release cycle is longer and the software tends to be a bit older, in favor of stability.
[*]Updates.  If the distro is slow for feature updates and sort-of-fast for security updates, that tends to make a more stable.
[*]Focus of the distro.  If a distro is focused on Enterprise use, then they will have a really long development cycle, they will have a huge paid testing staff and really good tests.  They'll also tend to have a lot of the configuration already done for you, or a GUI configuration tool.
[/LIST]

Release cycle: You have some basic types, this list is probably not exhaustive:
[LIST=1]
[*]Rolling release.  No new major versions of the distro are ever really released.  They'll number the CDs for sanity, but anyone who keeps updating will always have the latest thing.
[*]Short cycle:  Tend to focus on latest greatest like rolling release, but a bit more sane in terms of stability.  Some testing to get the big bugs out.
[*]Medium cycle:  Tend to find a balance between stability and new functionality.  This is the mainstream user and where Ubuntu is.
[*]Long cycle:  Tend to aim more at stability and less on features.  <rant>They'll leave a really tool off their list just because of one tiny technical detail that never gets resolved.</rant>
[*]Also, the consistency of the release cycle:  Ubuntu is almost militant in that they have a specific time between releases.  I don't think this is very rational.  Most distros get something stable, release it as a major version and then start working on the next one.  They wait until it's good before they release it.
[/LIST]

The OP sounded like he/she was looking for something more enterprise related.

All this stuff is a balance.  Each of us has different requirements or desires for features and stability.  I use several different distros because each of my boxes has a separate set of requirements.  I use Ubuntu where I just want it up and fast, and reasonably new features.  I use Gentoo when I want to play but don't so much care if I have to wipe it off and start over because I did something stupid.  I use a CentOS for stability in a server where I lose money if it's not running.

All that said, you could and many people DO use Ubuntu for stable servers.  It's up to you.  I'm just making recommendations.
Thanks for that.   I didn't know what a "rolling release" was along with some of the other terms being thrown around in this thread.

---

### Post by Annq on 2013-08-13
> **KBD47 said:**
> If you don't like fixing things, you should be using Debian Stable or Ubuntu LTS 12.04 release. I recommend the Ubuntu spin LXLE which has the LTS support.
I actually really like fixing things.  Its when I can't that bothers me.  I only have two host machines with Ubuntu and they only break when I use them.  All my other OSs are stable.  I have windows XP, windows 7 and 8, Fedora 19, OS X Mountain Lion, and iOS and Android devices.  My iPad even has perl, vim and other essential tools.  The only things broken are my 13.04 Ubuntu machines.  Since I didn't have a problem with other releases (I started with hardy, 8.04) I was wondering if I was the only one.  

From what I've read in this thread I'm leaning toward Ubuntu LTS, Debian or CentOS for servers and others for development.

A

---

### Post by mamamia88 on 2013-08-13
> **Annq said:**
> mamamia,

I'm having trouble diagnosing the problem.  But I haven't been focused on hardware because my hosts are fairly new.  Something to look at before punting Ubuntu.

A

Didn't realize you were running it on a vm.  In that case it's probably not a hardware issue if the host is running fine.   Maybe you aren't dedicacating enough resources too it?  Maybe running something lighter like lubuntu in the vm will solve your problems?  And why are you running linux vms?

---

### Post by 1clue on 2013-08-13
Annq,

No problem.  I think a large portion of Linux users everywhere stick with whatever they tried first because the learning curve was so steep, and they don't want to go through that again.  It took me years to figure out some of this stuff, and it took virtualization for me to really start trying out different distros.

ssam made good points above.  No Linux should be crashing regularly, either an app or the whole OS.  A kernel panic is serious business.

For that matter, that's true for ANY operating system.  I only use Linux and Mac personally, but for work I use several flavors of Windows as well.  Your logs should never have errors, and should seldom have warnings.  You should check them every now and then, and clear them every now and then, and see how your system is doing.  For any number of reasons, including security and stability.

I get really angry at my coworkers sometimes, they see an error on a critical server and don't do anything about it.  Then the system goes down and I'm trying to figure out what broke, and there's all these errors that have been there for months with nobody doing anything.  When the server is broken, you need to know what changed, not what's been broken forever.

One thing I disagree with ssam about is proprietary drivers.  At any point the free driver and the proprietary driver are in different phases of development.  The proprietary driver is made by the company that made the hardware, and it probably knows more about the device than the Open Source guys did, but it might not interface well with the current version of Linux.  They don't always update the driver very often.  On the other hand the opposite is often true for the free driver, they know the Linux side pretty well but they might not have good support for the hardware.  In my experience sometimes the Open Source driver is better, and other times the proprietary one is better.  You can't just research once and be done with it, you have to look every now and then.  At least if you aren't happy with the one you're using.  :)

---

### Post by Annq on 2013-08-13
> **mamamia88 said:**
> Didn't realize you were running it on a vm.  In that case it's probably not a hardware issue if the host is running fine.   Maybe you aren't dedicacating enough resources too it?  Maybe running something lighter like lubuntu in the vm will solve your problems?  And why are you running linux vms?
Nope, I'm not running Ubuntu on a VM.  Its on a dedicated machine and also on a dual boot machine.  So it may very well be a hardware problem.  I'm running Fedora on a VM.  No issues there.

---

### Post by Annq on 2013-08-13
> **1clue said:**
> Annq,

No problem.  I think a large portion of Linux users everywhere stick with whatever they tried first because the learning curve was so steep, and they don't want to go through that again.  It took me years to figure out some of this stuff, and it took virtualization for me to really start trying out different distros.

ssam made good points above.  No Linux should be crashing regularly, either an app or the whole OS.  A kernel panic is serious business.

For that matter, that's true for ANY operating system.  I only use Linux and Mac personally, but for work I use several flavors of Windows as well.  Your logs should never have errors, and should seldom have warnings.  You should check them every now and then, and clear them every now and then, and see how your system is doing.  For any number of reasons, including security and stability.

I get really angry at my coworkers sometimes, they see an error on a critical server and don't do anything about it.  Then the system goes down and I'm trying to figure out what broke, and there's all these errors that have been there for months with nobody doing anything.  When the server is broken, you need to know what changed, not what's been broken forever.

One thing I disagree with ssam about is proprietary drivers.  At any point the free driver and the proprietary driver are in different phases of development.  The proprietary driver is made by the company that made the hardware, and it probably knows more about the device than the Open Source guys did, but it might not interface well with the current version of Linux.  They don't always update the driver very often.  On the other hand the opposite is often true for the free driver, they know the Linux side pretty well but they might not have good support for the hardware.  In my experience sometimes the Open Source driver is better, and other times the proprietary one is better.  You can't just research once and be done with it, you have to look every now and then.  At least if you aren't happy with the one you're using.  :)
I never look at my logs unless I'm having problems.  That's good practice checking it regularly.  I have a feeling it may be a graphics driver problem.

A

---

### Post by mamamia88 on 2013-08-13
> **Annq said:**
> Nope, I'm not running Ubuntu on a VM.  Its on a dedicated machine and also on a dual boot machine.  So it may very well be a hardware problem.  I'm running Fedora on a VM.  No issues there.

Ah you using the word hosts through me off.  Well if it's a dualboot machine and the problems only happen on one os then you  can somewhat rule out hardware.  But it couldn't hurt to run some diagnostics.

---

### Post by King Dude on 2013-08-13
> **Annq said:**
> King Dude,

I'm running XFCE 13.04, Raring Ringtail on a 64-bit desktop computer.  It crashes randomly.  I can't find the problem.  It doesn't seem to matter what is running.

Another one I was running was a dual boot XFCE 13.04, Raring Ringtail on a 64-bit laptop, along side Windows 8.  The session randomly restarted only when I used it.   I've had Ubuntu on this machine for years and have only had this problem with ratty.  Yesterday, in frustration, I jetisoned it in favor of a Fedora 19 VM.  We'll see how that goes.  

My other machine is a 64-bit Windows 8 with a Fedora 19 VM.

Thanks,
Anne
How does it crash exactly? Does it give you an error? Does the computer itself turn off or restart?

---

### Post by 1clue on 2013-08-13
I'm running Xubuntu 13.04, don't get crashes except when I know it was something stupid I did.  Then it's not a reboot but an app that crashes.  I have caused a couple resource deadlocks and had to power the box off though, which plays hell on my RAID array.  Not even ssh was responding.

---

### Post by 1clue on 2013-08-13
> **Annq said:**
> I never look at my logs unless I'm having problems.  That's good practice checking it regularly.  I have a feeling it may be a graphics driver problem.

A


Graphics drivers are probably my most common issue, but when it works it should work solidly.  There was a point when I had a card that wasn't supported well by either the Open Source drivers or the proprietary drivers, and that was hell.  But right now I don't see a lot of complaints for any video drivers, mostly just people trying to get set up.

All you guys, start looking at your logs.  Figure out what they mean and how to fix the errors.

If you're into Linux because it's fun, then go have fun:  Figure out how your machine boots, trace the whole thing all the way through.  Figure out what's going on in your logs.  Figure out what the configuration options are for the core software on your system.

If you REALLY want to nerd out, go install a source-based distro like Gentoo.  I thought I was an expert until I loaded that.  Just reading the installation documentation is really educational.  Run it for awhile and you get familiar with your hardware in ways you would never have imagined.  And you'll stop being quite so afraid of broken things.

---

### Post by mastablasta on 2013-08-14
i have bugs, but not crashes. it is possible that the error is not in hardware but bad or wrong drivers. knowing why it crashes would help solve the problem.

---

### Post by Artemis3 on 2013-08-14
Linux doesn't crash, certainly not like windows. There is a problem you have there, probably "driver" (kernel module) related.
Or you might have faulty ram. Try memtest, and wait half an hour or so until at least 1 complete pass occurs, preferably 2 o 3.

Do you have ATI/AMD video? This is a common cause, as they don't provide good support in Linux, and getting it to work just right can be tricky (if at all possible, depending on model). This situation can also occur with other components, such as wifi etc.

---

### Post by 1clue on 2013-08-14
> **Artemis3 said:**
> Linux doesn't crash, certainly not like windows...

I hate to be disagreeable but this is completely false.  It's called a kernel panic.  It's the equivalent of the blue screen of death in windows.

Both of these things should never happen, but all sorts of things can cause them, both hardware and software.  FWIW it's the same types of things in both operating systems that does it too.

---

### Post by Annq on 2013-08-14
> **King Dude said:**
> How does it crash exactly? Does it give you an error? Does the computer itself turn off or restart?

The screen freezes, and I cannot connect via ssh.  Keyboard not responsive.

---

### Post by Annq on 2013-08-15
Update:

I am going through several errors in dmesg and will fix them one-at-time to determine whether one of these errors is pointing to the freezing/crashing problem.  This is a single-boot 64-bit physical host with Ubuntu Xfce Desktop 13.04.

Error Message 1:

mtrr_cleanup: can not find optimal value
please specify mtrr_gran_size/mtrr_chunk_size

Solution 1.1:
(See: [http://askubuntu.com/questions/244473/how-and-why-should-i-specify-mtrr-gran-size-mtrr-chunk-size](http://askubuntu.com/questions/244473/how-and-why-should-i-specify-mtrr-gran-size-mtrr-chunk-size))

Edited the boot command line to set sizes as per the above URL. 

Two days and no freeze/crash.  

Will follow-up to state whether or not this fixed the problem.

13-08-22 Update: System still freezing but less often.

I think it may be a monitor/graphics problem.  Set fixed resolution in NVIDIA settings.  No crashes, but turning off monitor when not in use.

13-08-24 Update: Updated NVIDIA Driver to latest version.

[SOLVED]

No more crashing/freezing.  

In the meantime, I tried other Linux flavours and found Ubuntu to be the best for me both for desktop (Xfce) and for server.  

Thanks for all the help.

Anne

---

