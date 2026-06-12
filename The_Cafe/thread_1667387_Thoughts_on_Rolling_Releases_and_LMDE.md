---
title: "Thoughts on Rolling Releases and LMDE?"
date: 2011-01-14
forum: The Cafe
---

### Post by slooksterpsv on 2011-01-14
All,

I'm curious on what you guys think about Rolling Releases. I know most of the pros/cons - I think such as:
P1. You're running the latest software without having to reformat or that.
C1. Programs may crash more often.

So I'm considering doing LMDE 64-bit just cause it's a rolling release, cause I like running the latest, even if it's unstable.

So how do you guys feel?

---

### Post by sandyd on 2011-01-14
> **slooksterpsv said:**
> All,

I'm curious on what you guys think about Rolling Releases. I know most of the pros/cons - I think such as:
P1. You're running the latest software without having to reformat or that.
C1. Programs may crash more often.

So I'm considering doing LMDE 64-bit just cause it's a rolling release, cause I like running the latest, even if it's unstable.

So how do you guys feel?
its not as unstable as you think.
Im running KDE 4.6 RC2 on Gentoo (its considered a rolling release...). 
But then again, it might be more stable only because I compile everything.

However, I like rolling releases. Their good in the fact that you get to get the newest software, which mostly means less bugs

---

### Post by slooksterpsv on 2011-01-14
> **sandyd said:**
> its not as unstable as you think.
Im running KDE 4.2 RC2 on Gentoo (its considered a rolling release...). 
But then again, it might be more stable only because I compile everything.

However, I like rolling releases. Their good in the fact that you get to get the newest software, which mostly means less bugs

KDE 4.2 RC2 is old, isn't 4.6 out now? I know 4.5.1 is out.

---

### Post by smellyman on 2011-01-14
LMDE is still Debian, so it isn't close to the latest.  Especially now since Squeeze is frozen and in typical Debian fashion, the long wait is on for it to become "stable".

Arch is much better to have the latest software.

---

### Post by NightwishFan on 2011-01-14
I am not against them but I will never use a strict rolling model. I tend to define unstable the Debian way with something that changes a lot being "unstable". To be honest I think that is the correct definition for it, as all software has bugs. Regardless, my reasons for using time based releases over rolling are:
[LIST]
[*]I do not need the latest software. Generally what I do I can backport or compile.
[*]I like knowing a piece of software I use will be available for a chunk of time.
[*]Generally a distributor can make certain pieces of software work well together that the newest versions might not.
[*]You can very release times for specific purposes, such as Ubuntu LTS/Non-LTS.
[/LIST]
Basically it is more flexible for me to have a time based release.

---

### Post by Nytram on 2011-01-14
I prefer to have the latest software which is why I use Arch. I've been using it around 6 months now and not had any issues with instability, the only difficult/time-consuming part was the initial install.

---

### Post by Tibuda on 2011-01-14
Another Arch user here. You are fine with a rolling release if:
1. You don't use the "testing" repositories (corresponds to "unstable" in Debian, not "testing"), unless you want to contribute to test packages before they go public;
2. You update at least once a week, because big upgrades are messy, which is also true if you update Ubuntu every six months;
3. You do some research before updating core packages like X, glib and the kernel. Arch home page usually has some announcements about potential upgrade problems.

I have tried LMDE. It looks like a great combo: rolling release + out-of-the-box system. I switched back to Arch, because the Debian Testing repositories are not as updated as Arch repos, and not as complete (package-wise) as Ubuntu and Arch repos.

---

### Post by Warpnow on 2011-01-14
Aptosid (formerly Sidux) is another awesome rolling release debian.

---

### Post by smellyman on 2011-01-14
> **Warpnow said:**
> Aptosid (formerly Sidux) is another awesome rolling release debian.

and is more up to date than LMDE since it is based on unstable.

I used it in the past and never ran into issue.

---

### Post by johntaylor1887 on 2011-01-14
I tried LMDE, and after I got everything set up, I did updates, rebooted, and the whole install was fubar'ed. I may try again it in the future though.

---

### Post by CraigPaleo on 2011-01-14
> **slooksterpsv said:**
> KDE 4.2 RC2 is old, isn't 4.6 out now? I know 4.5.1 is out.

4.5.5 is out. I'm running 4.6 RC2. I don't think Sandyd's rolling release has rolled in over a year.

---

### Post by snowpine on 2011-01-15
I prefer time-based to rolling release for one simple reason: When I log into my work computer Monday morning, I want it to work the exact same way it worked Friday afternoon. 

I do have one "hobby" computer at home that is running Debian Unstable.

Also, for the record, Debian Testing/Unstable is not what I'd consider "rolling release." Rather, it is part of the development process towards the next stable release. It's no different than running Ubuntu 11.04 beta. The fact that "Ubuntu 11.04 beta has the latest software" doesn't mean that "Ubuntu is a rolling release distro," and the same is true for Debian.

Arch is definitely the way to go if you're looking for rolling release, in my opinion. :)

---

### Post by snowpine on 2011-01-15
I prefer time-based to rolling release for one simple reason: When I log into my work computer Monday morning, I want it to work the exact same way it worked Friday afternoon. 

I do have one "hobby" computer at home that is running Debian Unstable.

Also, for the record, Debian Testing/Unstable is not what I'd consider "rolling release." Rather, it is part of the development process towards the next stable release. It's no different than running Ubuntu 11.04 beta. The fact that "Ubuntu 11.04 beta has the latest software" doesn't mean that "Ubuntu is a rolling release distro," and the same is true for Debian.

Arch is definitely the way to go if you're looking for rolling release, in my opinion. :)

---

### Post by Timmer1240 on 2011-01-15
Im testing out Linux mint debian gnome in virtualbox and I must say Im impressed with it so far!Im seriously thinking of installing it and running it as my main OS I like the Idea of never having to reinstall!Seems to be pretty good system!

---

### Post by WorfSOM on 2011-01-15
> **snowpine said:**
> I prefer time-based to rolling release for one simple reason: When I log into my work computer Monday morning, I want it to work the exact same way it worked Friday afternoon. 



I feel the same way. I am prepared to put up with older software if it guarantees stability.

---

### Post by handy on 2011-01-15
I've had Arch installed on No.1 box, since March 2008. It is the same install that is upgraded usually once a day. There have only been a few problems in that time & the solutions to those problems came very quickly. 

Been using the development packages for the AMD/ATi GPU that I'm using (including the kernel) for over 15 months. There has only been a couple of times that I had to wait a short time for a bug to be fixed so I could keep on using the dev' driver stack.

Overall I'm incredibly impressed with how stable & trouble free my system has been & that's using the aforementioned dev' packages!

I love the Arch rolling release system, as I'm a very lazy computer user these days & using the RR system is the easiest way that I have found to maintain a computer system.

That said, some people would find the RR system to be a very uncomfortable way to manage their system. 

Courses for horses.

---

### Post by kaldor on 2011-01-15
> **slooksterpsv said:**
> All,

I'm curious on what you guys think about Rolling Releases. I know most of the pros/cons - I think such as:
P1. You're running the latest software without having to reformat or that.
C1. Programs may crash more often.

So I'm considering doing LMDE 64-bit just cause it's a rolling release, cause I like running the latest, even if it's unstable.

So how do you guys feel?

If you want the latest, do not bother with LMDE. LMDE gives the latest in STABLE software packages. If you want bleeding edge, go to Arch.

If you're a Sadist, go for Fedora Rawhide.

---

### Post by handy on 2011-01-15
> **kaldor said:**
> If you want the latest, do not bother with LMDE. LMDE gives the latest in STABLE software packages. If you want bleeding edge, go to Arch.

If you're a Sadist, go for Fedora Rawhide.

Masochist. :)

---

### Post by NightwishFan on 2011-01-15
> **handy said:**
> Masochist. :)

:lolflag:

---

### Post by ilovelinux33467 on 2011-01-15
I love rolling releases. I am dual booting Arch and my primary distro (openSUSE) on my laptop and Arch is great. However on my servers I prefer time based releases.

---

### Post by kaldor on 2011-01-15
> **handy said:**
> Masochist. :)

Yeah, that ^^

---

### Post by Shippou on 2011-01-15
IMHO, this is a troll-prone question. I am not saying that the OP is a troll, but this is a troll-prone question.

Anyways, my thoughts.

I am using a rolling-release system (Arch, to be exact) because:
1. I don't like the hassle of reinstalling;
2. I want (in a way) bleeding-edge software (e.g., I am typing this using Firefox 4 beta 8);
3. I like updating my box on an average of once a month.

My personal reasons for using Arch over Ubuntu (or other distros) is*:
1. Ubuntu is bloated, IMHO.
2. I want to know almost everything that is installed in my box.
3. I want a lean and mean system, that does not consume much RAM or HD space.
4. I want full control over my system.

Actually, I also considered switching to Gentoo, but the hassle of compiling everything is just not worth it (considering also the fact that my Internet connection is not like that of Japan's, or US at the least). This is also the same reason I abandoned the idea of LFS, though I am very intrigued by the idea of doing it.


*Please note: I am not a troll. Sorry for the comparisons.

---

### Post by slooksterpsv on 2011-01-15
> **Shippou said:**
> IMHO, this is a troll-prone question. I am not saying that the OP is a troll, but this is a troll-prone question.

Anyways, my thoughts.

I am using a rolling-release system (Arch, to be exact) because:
1. I don't like the hassle of reinstalling;
2. I want (in a way) bleeding-edge software (e.g., I am typing this using Firefox 4 beta 8);
3. I like updating my box on an average of once a month.

My personal reasons for using Arch over Ubuntu (or other distros) is*:
1. Ubuntu is bloated, IMHO.
2. I want to know almost everything that is installed in my box.
3. I want a lean and mean system, that does not consume much RAM or HD space.
4. I want full control over my system.

Actually, I also considered switching to Gentoo, but the hassle of compiling everything is just not worth it (considering also the fact that my Internet connection is not like that of Japan's, or US at the least). This is also the same reason I abandoned the idea of LFS, though I am very intrigued by the idea of doing it.


*Please note: I am not a troll. Sorry for the comparisons.

Shippu, no it was a serious question that's why I asked. I love to be on the bleeding edge of the newest software. I may need to look into Arch now, I've had others post, but reading your post about Arch makes me want to try it now.

Alrighty I'm off to download arch, vm it, if it works well, here it comes on an 80GB Partition

---

### Post by Timmer1240 on 2011-01-15
> **kaldor said:**
> If you want the latest, do not bother with LMDE. LMDE gives the latest in STABLE software packages. If you want bleeding edge, go to Arch.

If you're a Sadist, go for Fedora Rawhide.

I guess I like the Idea of the latest Stable packages over bleeding edge so Id rather go with LMDE for now Im running it now and really liking it so far its not any harder than Ubuntu!

---

### Post by stmiller on 2011-01-15
I think rolling releases are the future of desktop distros. I'm all for it. With Ubuntu updating to a new release every 6 months it's not that far away from a rolling release as it is.

For servers, having a set release ever xx years makes sense, though.

/opinion

---

### Post by CraigPaleo on 2011-01-15
> **stmiller said:**
> I think rolling releases are the future of desktop distros. I'm all for it. With Ubuntu updating to a new release every 6 months it's not that far away from a rolling release as it is.

For servers, having a set release ever xx years makes sense, though.

/opinion

Exactly. I've seen mentioned here several times that people don't like time-based releases because they have to reinstall. Why do people feel that way? All you have to do is a distribution upgrade. The only difference is that it does it all at once.

---

### Post by CraigPaleo on 2011-01-15
> **slooksterpsv said:**
> Shippu, no it was a serious question that's why I asked. I love to be on the bleeding edge of the newest software. I may need to look into Arch now, I've had others post, but reading your post about Arch makes me want to try it now.

Alrighty I'm off to download arch, vm it, if it works well, here it comes on an 80GB Partition

Give Sabayon, and PCLinuxOS a try as well - also rolling releases.


__________________
_**Pardus at [Distrowatch]("http://distrowatch.com/pardus")**_

---

### Post by johntaylor1887 on 2011-01-16
I'm happy just to use regular ubuntu and use ppa's, and don't mind reinstalling once or twice a year to get new things. I tried LMDE and thought it was fantastic until an update completely hosed the system. I'm not saying it's bad or anything, it's just that my first impression wasn't good. But I know it works for a lot of people and could turn out to be the next "big distro". There's a lot of potential for lmde as long as it's done *right*.

---

### Post by handy on 2011-01-16
> **ilovelinux33467 said:**
> I love rolling releases. I am dual booting Arch and my primary distro (openSUSE) on my laptop and Arch is great. However on my servers I prefer time based releases.

There is a server release for Arch, but I wouldn't use it either. Not because I don't trust it, but because I don't need it, I have other solutions here to serve my needs.

[http://arch-stable.wholebean.info/default.html](http://arch-stable.wholebean.info/default.html)

---

### Post by handy on 2011-01-16
> **stmiller said:**
> I think rolling releases are the future of desktop distros. I'm all for it. With Ubuntu updating to a new release every 6 months it's not that far away from a rolling release as it is.

For servers, having a set release ever xx years makes sense, though.

/opinion

There has been talk from Canonical of Ubuntu going rolling release, we will just have to wait & see if that does eventuate.

---

### Post by CraigPaleo on 2011-01-16
> **handy said:**
> There has been talk from Canonical of Ubuntu going rolling release, we will just have to wait & see if that does eventuate.

I heard they are considering a rolling release for apps only. The system would still be updated every six months, which isn't a bad idea.



__________________
**Pardus at [Distrowatch]("http://distrowatch.com/pardus")**

---

### Post by handy on 2011-01-16
> **CraigPaleo said:**
> I heard they are considering a rolling release for apps only. The system would still be updated every six months, which isn't a bad idea.

I see problems with that model as the dependencies have to be updated too. Therefore the system needs to be updated as required.

I think that the best solution would be RR system for the desktop & a LTR that only had security updates & such as it does now. This would make businesses feel more secure & servers be more secure.

It would also bring a choice to Ubuntu users.

---

### Post by Spice Weasel on 2011-01-16
> **handy said:**
> I see problems with that model as the dependencies have to be updated too. Therefore the system needs to be updated as required.

I think that the best solution would be RR system for the desktop & a LTR that only had security updates & such as it does now. This would make businesses feel more secure & servers be more secure.

It would also bring a choice to Ubuntu users.

So you are thinking RHEL and Fedora Rawhide, but both are free of charge?

---

### Post by handy on 2011-01-16
> **Spice Weasel said:**
> So you are thinking RHEL and Fedora Rawhide, but both are free of charge?

No, I wasn't thinking of them at all. 

I was thinking of a possible future for Ubuntu.

Monetary cost never crossed my mind.

---

### Post by Spice Weasel on 2011-01-16
I meant a similar situation to how Fedora and RHEL are developed but for Ubuntu. Of course, the LTS version would not cost money like RHEL does.

So the main version is rolling release, and every few years or so (the current LTS is every 2 years, right?) the current RR version is forked and as many bugs fixed as possible until it is stable.

The problem with this is a release schedule like this is the main reason Ubuntu forked from Debian all of those years ago. Shuttleworth wanted a operating system similar to Debian but with a steady release schedule.

---

### Post by handy on 2011-01-16
Arch has a steady release schedule, it rarely misses a day without a system upgrade. :)

---

### Post by sandyd on 2011-01-16
> **slooksterpsv said:**
> KDE 4.2 RC2 is old, isn't 4.6 out now? I know 4.5.1 is out.
typo :D.
I meant KDE 4.6 RC2

---

### Post by Shippou on 2011-01-16
> **slooksterpsv said:**
> Shippu, no it was a serious question that's why I asked. I love to be on the bleeding edge of the newest software. I may need to look into Arch now, I've had others post, but reading your post about Arch makes me want to try it now.

Alrighty I'm off to download arch, vm it, if it works well, here it comes on an 80GB Partition

Looks like I've (apparently) converted an Ubuntu user to Arch. :lol:

Be careful, however, as Arch are for intermediate to advanced users. I admit I consider myself as an intermediate user, but not that advanced. I do encounter problems with Arch (e.g., I didn't have an Internet connection for the first three days of my installation because I can't figure out how to configure the necessary files), but I think this is because mostly of my limited knowledge about the system. Fortunately, so far, I am okay with what I have.

And oh yeah, one of the disadvantages of being bleeding-edge: I had no flashplugin for maybe about 4 months because of Flash vulnerability. I am running the 64-bit version of Arch, and because of the said vulnerability, flashplugin was removed from their official repos until a new version for 64 bit was released by Adobe this last November, if I remember correctly.

BTW, I've installed Arch in my box last [2010-06-25 01:10] (according to sudo head /var/log/pacman.log, and never had a reinstall since. :)

---

