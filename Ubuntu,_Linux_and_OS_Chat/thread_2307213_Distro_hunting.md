---
title: "Distro hunting"
date: 2015-12-22
forum: Ubuntu, Linux and OS Chat
---

### Post by user1397 on 2015-12-22
I am looking for a distro that has the following criteria:


[LIST]
[*]easy / fast to install with a GUI installer
[*]easy / fast package management (binary packages)
[*]rolling release, preferably fully rolling release
[*]not have to constantly monitor the distro's website or mailing lists for potential huge breakages (I'm cool with occasionally having to look up info but wouldn't like constant risky breakage)
[*]64 bit
[*]good implementation of KDE plasma (although I don't necessarily care if that is installed by default, as long as I can easily install it)
[*]good support and not be some obscure distro with 5 users and very little app support
[/LIST]

As you can see, this rules out ubuntu, arch, and a whole host of other distros (fedora, gentoo, slackware, a bunch of derivatives of all these, etc)

The potential candidates I've found so far are possibly manjaro, antergos, debian testing or unstable, and opensuse tumbleweed, although I'm not 100% if these meet my criteria (hence my posting here).

Thanks!

---

### Post by yoshii on 2015-12-23
i'm not really sure, but i think maybe some of the recent Linux Mint versions are rolling releases.  
have you searched on [http://distrowatch.com](http://distrowatch.com) ?

---

### Post by kc1di on 2015-12-23
Linux mint LMDE may work for you.

Other than that I'd go with Debian Testing
Though Ubuntu LTS would be the best candidate. 
Current LTS 14.04 and then 16.04 , but I'd wait a bit till any kinks get worked out. 
PCLinuxOS is another possibility, it keeps a very stable base, but upgrades major apps quickly. 
(note:  there is no perfect Distro, You'll just have to try some and see which ones come the closest)

---

### Post by buzzingrobot on 2015-12-23
OpenSuse Tumbleweed?  

The "fully rolling" requirement is at odds with the "not have to constantly monitor" requirement, with the possible exception of PCLinuxOS. 

LMDE is currently based on Debian Stable, i.e., not rolling.

The "new" KDE is still seeing many rapid releases, and porting of some packages to the new structure is still in progress. A rolling release should get you the newest fixest from KDE quickly, but it might also get you the newest bugs just as quickly. I've no evidence, but I suspect the number and volume of KDE updates is challenging the ability of many distros to keep up.

Fedora's Rawhde, while not touted as a rolling release, is its development platform and is, in practice, rolling. That means, among other things, that you will get things like the odd-numbered Gnome development releases.

---

### Post by Dennis N on 2015-12-23
> **ubuntuman001 said:**
> The potential candidates I've found so far are possibly manjaro, antergos, debian testing or unstable, and opensuse tumbleweed, although I'm not 100% if these meet my criteria (hence my posting here).

Thanks!
Manjaro is a good candidate for your criteria. I'm currently evaluating Manjaro (the XFCE version) as a rolling release to see how well the concept works in practice. So far, it's 3 months into this ongoing trial. It has had a lot of updates in that time, but I've experienced no breakages yet - it just keeps working. I have no experience with the KDE version, however. Try it and see. Manjaro has the fastest-working GUI package manager that I have seen.

---

### Post by user1397 on 2015-12-30
> **yoshi2 said:**
> i'm not really sure, but i think maybe some of the recent Linux Mint versions are rolling releases.  
have you searched on [http://distrowatch.com](http://distrowatch.com) ?I have searched on that site, quite extensively, and I am aware of several candidates.  I was just trying to see some opinions here.  The Linux Mint rolling edition is based off of debian stable now, so it is not bleeding edge and therefore does not fit my criteria.

> **kc1di said:**
> Linux mint LMDE may work for you.

Other than that I'd go with Debian Testing
Though Ubuntu LTS would be the best candidate. 
Current LTS 14.04 and then 16.04 , but I'd wait a bit till any kinks get worked out. 
PCLinuxOS is another possibility, it keeps a very stable base, but upgrades major apps quickly. 
(note:  there is no perfect Distro, You'll just have to try some and see which ones come the closest)Like I said, LMDE is now based on debian stable so it is not bleeding edge anymore and frankly i don't even understand the point of it anymore.  And why did you suggest ubuntu? It is not rolling release at all...  

I considered PCLinuxOS but what I don't like about it is it seems like it's not a distro with a large community and seems like there isn't a bunch of support for it like there is for other more mainstream distros.

> **buzzingrobot said:**
> OpenSuse Tumbleweed?  

The "fully rolling" requirement is at odds with the "not have to constantly monitor" requirement, with the possible exception of PCLinuxOS. 

LMDE is currently based on Debian Stable, i.e., not rolling.

The "new" KDE is still seeing many rapid releases, and porting of some packages to the new structure is still in progress. A rolling release should get you the newest fixest from KDE quickly, but it might also get you the newest bugs just as quickly. I've no evidence, but I suspect the number and volume of KDE updates is challenging the ability of many distros to keep up.

Fedora's Rawhde, while not touted as a rolling release, is its development platform and is, in practice, rolling. That means, among other things, that you will get things like the odd-numbered Gnome development releases.I'm considering opensuse tumbleweed as i said in my first post.  And yes, I know it's asking a bit much since fully rolling usually equates with having to monitor your system more in case of breakages, but I don't mean I wouldn't do any monitoring, I just don't want an excessive amount of monitoring.  

Fedora rawhide seems a bit too unstable for me from what I read, but i guess I'll check it out.

> **Dennis N said:**
> Manjaro is a good candidate for your criteria. I'm currently evaluating Manjaro (the XFCE version) as a rolling release to see how well the concept works in practice. So far, it's 3 months into this ongoing trial. It has had a lot of updates in that time, but I've experienced no breakages yet - it just keeps working. I have no experience with the KDE version, however. Try it and see. Manjaro has the fastest-working GUI package manager that I have seen.Thanks for the input.  One thing I didn't really like about manjaro when I was reading about it was that although based on Arch, it had evolved to its own distro.  I tend to like to stick to the "major" distros since they are more proven and stable and have better documentation and support etc.  But I keep hearing great things about manjaro so maybe I'll give it a try anyway.

---

### Post by kevdog on 2015-12-31
Honestly -- although it doesn't meet your criteria -- just install Arch.  It will take you about 3-4 hours.  I've done it several times and I think I have the installation down to about an hour.  Rolling release -- only broke on me once but that honestly was my fault -- hard drive died or something.  Stable.  Sometimes however its good for someone to set up your desktop.  Basic installs KDE, Gnome 3, Cinammon etc.  Need to customize.

---

### Post by Bucky Ball on 2015-12-31
Arch or 'roll' Ubuntu yourself by installing the 16.04 LTS daily and do that every day. 16.04 is so bleeding edge it's not even released yet. 

If you want total bleeding edge, minimal install the daily linux kernel and a desktop environment (or is that not minimal enough?), update/upgrade it daily.

---

### Post by 1clue on 2016-01-01
I use Gentoo as my only rolling release distro.  It's not easy or fast to install so doesn't fit in your list, I'd just like to reinforce the previous statement that "rolling release"+"not having to monitor" are unrealistic if not impossible in the same system.

The very fact of rolling release means that updates come out as soon as or shortly after the upstream package becomes available.  By definition that means there's not a whole lot of information about security or stability yet. There WILL be issues, and you'd best be on top of it if security means anything to you.

It's my opinion, but I think that rolling release, while it gives you the latest greatest software, also requires a lot of hands-on maintenance that can't be easily delegated to a script.

A good place to start is to have a stable gui platform as your desktop (I use Ubuntu) and then use your rolling release distro as a server that you access from your desktop.  You can do remote X if the network is fast enough, so you get much of the benefits of the rolling release without the risk of being put out of business when your rolling release box tanks.

---

### Post by Geoffrey_Arndt on 2016-01-01
Well, why not just install the best . . . Ubuntu 16.04 LTS, and if needed, install a few key PPA's.    Best of all Worlds . . . besides, what other distro would the real UbuntuMan001 install?

(it'll be sorta like having a "rolling release" until April anyway).  :lolflag:

---

### Post by user1397 on 2016-01-01
> **kevdog said:**
> Honestly -- although it doesn't meet your criteria -- just install Arch.  It will take you about 3-4 hours.  I've done it several times and I think I have the installation down to about an hour.  Rolling release -- only broke on me once but that honestly was my fault -- hard drive died or something.  Stable.  Sometimes however its good for someone to set up your desktop.  Basic installs KDE, Gnome 3, Cinammon etc.  Need to customize.Honestly, I'm still considering it as an option.  I was trying out manjaro and antergos on virtualbox, and the default installs come preloaded with a bunch of programs I don't want, so maybe I really should just invest the time into arch...

> **Bucky Ball said:**
> Arch or 'roll' Ubuntu yourself by installing the 16.04 LTS daily and do that every day. 16.04 is so bleeding edge it's not even released yet. 

If you want total bleeding edge, minimal install the daily linux kernel and a desktop environment (or is that not minimal enough?), update/upgrade it daily.the idea of running ubuntu as a rolling distro seems highly unstable to me.  my understanding is that even though arch or gentoo are rolling, they're pretty stable considering all things cause they do at least some testing before releasing an update, whereas ubuntu daily or debian unstable is more like the developers just releasing updates as fast as possible with very minimal or no testing (I might be wrong, this is just my impression)

> **1clue said:**
> I use Gentoo as my only rolling release distro.  It's not easy or fast to install so doesn't fit in your list, I'd just like to reinforce the previous statement that "rolling release"+"not having to monitor" are unrealistic if not impossible in the same system.

The very fact of rolling release means that updates come out as soon as or shortly after the upstream package becomes available.  By definition that means there's not a whole lot of information about security or stability yet. There WILL be issues, and you'd best be on top of it if security means anything to you.

It's my opinion, but I think that rolling release, while it gives you the latest greatest software, also requires a lot of hands-on maintenance that can't be easily delegated to a script.

A good place to start is to have a stable gui platform as your desktop (I use Ubuntu) and then use your rolling release distro as a server that you access from your desktop.  You can do remote X if the network is fast enough, so you get much of the benefits of the rolling release without the risk of being put out of business when your rolling release box tanks.I hear ya.  I am in a constant state of flux about whether I really want rolling release or not.  One day I'm 100% certain I want it, and the next day I'm like "bah what's the point?" haha.

I would maybe try that other idea but I don't have another comp right now so its kinda hard :P

> **Geoffrey_Arndt said:**
> Well, why not just install the best . . . Ubuntu 16.04 LTS, and if needed, install a few key PPA's.    Best of all Worlds . . . besides, what other distro would the real UbuntuMan001 install?

(it'll be sorta like having a "rolling release" until April anyway).  :lolflag:
hehe. Read my reply above for my stance on ubuntu daily.  And yea, would be a bit hypocritical for me to run something other than ubuntu wouldn't it? :)

---

### Post by 1clue on 2016-01-01
> **ubuntuman001 said:**
> I hear ya.  I am in a constant state of flux about whether I really want rolling release or not.  One day I'm 100% certain I want it, and the next day I'm like "bah what's the point?" haha.

I would maybe try that other idea but I don't have another comp right now so its kinda hard :P


A rolling release WILL take more of your time.  Rolling releases are a very hands-on experience compared to non-rolling.  It can be pretty stable if the distro is always rolling, like Gentoo or Arch.  I agree with bleeding-edge Ubuntu or Debian, it's not the same thing.

It all depends on what you want to do with the box.  I run literally dozens of Linux boxes, some are VM hosts, some are standalone and some are VM guests.  Each one has a distro chosen specifically for that box.  I use 3 distros fairly regularly, and maybe 4 more on one or two boxes each.

> 
hehe. Read my reply above for my stance on ubuntu daily.  And yea, would be a bit hypocritical for me to run something other than ubuntu wouldn't it? :)


<rant>
Absolutely no disrespect intended, but:

I absolutely cannot understand this.  People keep saying this as though it actually matters what distro you use. There is no prize for sticking with one distro.  There's no cost to you or to anyone else because you used one distro over another.  I use several distros, and I like all of them for their own strengths and dislike them for their weaknesses. Ubuntu does not pay anyone to use their version of the operating system. Canonical provides Ubuntu for their own for-profit reasons, as is described on the home page. You and I get to use it for free, which is awesome. The reason it's more polished than most Linux distros is because Canonical pays people to polish it. They need something relatively stable to put their commercial software on.

I'm not in any way bashing Ubuntu, or Canonical or any other distro.  As I said I use and like a lot of them, and I use them in my work which means for-profit.  There is no ethical conundrum here. I install commercial software on some of my Linux boxes of all variants. Sometimes the distro is dictated by the software that must go on it.  Oracle database is a prime example.

I've been using Linux since about 1996. The distro I started with (mkLinux) no longer exists and you probably couldn't find the hardware it was tailored for anyway (early ppc macs).  I didn't fully understand how distros work or what makes one different from the other until I hopped around for a bit, especially with multiple installs which were all current simultaneously.

Don't stop using Ubuntu unless you really hate it.  But don't hesitate to dip a toe in somebody else's pond either.  If you decide to leave a distro for any reason, do so without angst or remorse, and expect none from the people who continue to love it.  Come back if you want to, you'll find people happy to see you.
</rant>

---

### Post by user1397 on 2016-01-01
> **1clue said:**
> A rolling release WILL take more of your time.  Rolling releases are a very hands-on experience compared to non-rolling.  It can be pretty stable if the distro is always rolling, like Gentoo or Arch.  I agree with bleeding-edge Ubuntu or Debian, it's not the same thing.

It all depends on what you want to do with the box.  I run literally dozens of Linux boxes, some are VM hosts, some are standalone and some are VM guests.  Each one has a distro chosen specifically for that box.  I use 3 distros fairly regularly, and maybe 4 more on one or two boxes each.Thanks for your insights. I constantly try out different distros in VMs cause right now I only have one comp, but I would love to have at least one more comp to be able to safely play around with other distros on bare metal instead of clunky VMs.

I have windows on my comp and I don't want to get rid of it just in case I need it for school/work, though I spend more time usually on my kubuntu partition.

I got a question for you, why do you personally choose gentoo over arch (or something else) for your rolling release distro?


> <rant>
Absolutely no disrespect intended, but:

I absolutely cannot understand this.  People keep saying this as though it actually matters what distro you use. There is no prize for sticking with one distro.  There's no cost to you or to anyone else because you used one distro over another.  I use several distros, and I like all of them for their own strengths and dislike them for their weaknesses. Ubuntu does not pay anyone to use their version of the operating system. Canonical provides Ubuntu for their own for-profit reasons, as is described on the home page. You and I get to use it for free, which is awesome. The reason it's more polished than most Linux distros is because Canonical pays people to polish it. They need something relatively stable to put their commercial software on.

I'm not in any way bashing Ubuntu, or Canonical or any other distro.  As I said I use and like a lot of them, and I use them in my work which means for-profit.  There is no ethical conundrum here. I install commercial software on some of my Linux boxes of all variants. Sometimes the distro is dictated by the software that must go on it.  Oracle database is a prime example.

I've been using Linux since about 1996. The distro I started with (mkLinux) no longer exists and you probably couldn't find the hardware it was tailored for anyway (early ppc macs).  I didn't fully understand how distros work or what makes one different from the other until I hopped around for a bit, especially with multiple installs which were all current simultaneously.

Don't stop using Ubuntu unless you really hate it.  But don't hesitate to dip a toe in somebody else's pond either.  If you decide to leave a distro for any reason, do so without angst or remorse, and expect none from the people who continue to love it.  Come back if you want to, you'll find people happy to see you.
</rant>
I fully agree, I was totally kidding when I said that! I give 0 ***** :P

---

### Post by 1clue on 2016-01-01
Sorry for the rant.

I like Gentoo's community better. About the only down side of Gentoo forums is that there's been an ongoing argument about systemd that occasionally bleeds into unrelated threads.  As you get familiar with Open Source you'll come to value the community surrounding a project or group of projects as much as the project itself.

When you get your next machine, make sure it has good support for virtualization.  In my experience VMs run almost as fast in a VM as on bare metal, and in some scenarios faster if guest drivers for your hardware are substandard.  Most modern hardware has support for virtualization, so you'd almost have to actively avoid virtualization support.  I also recommend something that can use ecc memory and lots of it.

About the only reason you might need to be on the bare metal is if you are a hard-core gamer or maybe video editing.  Even so if you have vt-d support you should be able to donate the hardwae directly to the guest, donate x number of cores and be good.

---

### Post by matt_symes on 2016-01-02
IMO Gentoo has the best documentation, apart from freeBSD, closely followed by arch.

No disrespect meant to the documentation maintainers. It's just that Gentoo's documentation is far more technical and i like that.

---

### Post by QDR06VV9 on 2016-01-02
> **matt_symes said:**
> imo gentoo has the best documentation, apart from freebsd, closely followed by arch.

No disrespect meant to the documentation maintainers. It's just that gentoo's documentation is far more technical and i like that.
:d+1

---

### Post by kevdog on 2016-01-02
I've never tried Gentoo linux however I'd love to.  However -- as it would seem right now -- that's a large time commitment. I do however however several Arch installs on two machines - one Virtual and one "bare metal".  (Oh mac book pro's are sweet for VM arch installs -- but I digress)..Arch isn't a big time commitment at all, and I've only once found them to crash or not boot -- and the reason was that I didn't consult the main Arch page when some big package was going to be installed.  That was my fault.  Other than that, I've need a few pointers from the Arch forums but usually the system runs pretty great.  I've got Cinammon and KDE plasma as Window Managers, so I'm not one of those guys running a completely stripped down desktop like i5.  Rarely if ever do I need to compile a package with the distro, however I will tell you I try to limit use of packages in the AUR since oftentimes after a while the package maintainer disappears and then you can't get a newer version -- think of the AUR like a ppa repository -- they are installation scripts for packages that aren't officially supported by the Arch install people.  There are definitely not as many packages within the mainline repository of Arch as Ubuntu, however they are bleeding edge.  For the most part, I haven't found a package I've needed however I have installed debtap (which is a program), that makes it possible to install .deb (Debian Ubuntu files) within Arch if ever in a jam.  I did this since I was just curious if it would work, and surprisingly the one package I tried as a test (Wickr) did install without any problem.  Wickr is now in the AUR so I just switched to that package.

---

### Post by 1clue on 2016-01-02
Not sure if we're welcome discussing the benefits of 2 advanced distros on this thread.  I'm willing to talk about this all day, but not sure if the OP thinks this is helpful.

I use arch and gentoo docs interchangeably.  There are differences (arch is newer software and systemd-based, gentoo lets you choose which init system you use as one example) but really they are very close otherwise.

The biggest thing is that Arch wants the forum to be quiet as a mouse, and Gentoo has a very helpful and verbose forum much like Ubuntu's. I've seen lots of questions from arch users on Gentoo forums, and on linuxquestions too.  IMO restricting the forum the way Arch does is not conducive to a healthy user base. You need to install Arch successfully before you can join the forum, and though I have successfully installed Arch and have my account I've never posted to their forum.  I post elsewhere, even if I couldn't find the answers on their docs sites or Gentoo's or even upstream.  IMO the forum is the most valuable asset in a distro.  The software is often very slightly changed from upstream, and the distros (like Ubuntu, Redhat/Fedora, Suse, etc) which are more deeply developed are done so with commercial for-profit resources.  In any case, they each have a forum and they use that forum as a knowledge base.  Most Linux forums have no advertising, or limited to a very few products.  It takes resources (money, time, etc) to maintain a forum.  Why do you think a commercial entity would do such a thing for no cost? It's because the things we post here are valuable.

Keep in mind that I use Linux in my job, for profit.  I install and write commercial software which can run on Linux.  I've contributed to Open Source.  I very firmly believe that commercial software and FOSS can and should coexist, and that it can be done without violating anyone's license agreements and without moral conundrums. I mention this because there's a lot of confusion about what FOSS is and a lot of opinions within the FOSS community which are not all completely compatible.

The main reason for mentioning the financial backing is because it's one of the things that drives a distro.  Every distro has some sort of financial backing. Some have very little and base mostly everything on volunteers or even one person. Others have a big company and others have crowd funding. The goals of the financial backing largely determine the direction of the distro. The OP (and everyone else) should take that backing and the community surrounding the distro into account before settling on any distro.

---

### Post by 1clue on 2016-01-02
@kevdog,

If you can install arch you can install gentoo.

---

### Post by vellon on 2016-01-02
> **1clue said:**
> 
The biggest thing is that Arch wants the forum to be quiet as a mouse, and Gentoo has a very helpful and verbose forum much like Ubuntu's. I've seen lots of questions from arch users on Gentoo forums, and on linuxquestions too.  IMO restricting the forum the way Arch does is not conducive to a healthy user base. You need to install Arch successfully before you can join the forum, and though I have successfully installed Arch and have my account I've never posted to their forum.  I post elsewhere, even if I couldn't find the answers on their docs sites or Gentoo's or even upstream.  IMO the forum is the most valuable asset in a distro.


Interesting. As a long-time Arch user, it seems to me to have a very healthy user base, and that has been the case for years, without the schisms of other distros. It is true that the Arch forums are not exactly chatty, but they are to the point and without extraneous noise. That suits me, and many others, and it is not like Arch hides its approach and expectations.

---

### Post by rosswmcgee on 2016-01-03
I use ubuntu lts 14.04. I have used debian, and mint. I am unsure why distrowatch shows mint, and debian with more users while ubuntu keeps losing. I had to ditch mint

on my wife's computer, and installed ubuntu 14.04lts, now all our computers use Ubuntu 14.04lts. I can use so many different options with ubuntu, although I used unity 

for a long time, switched back to Mate, because it has toolbar options that I enjoy.

---

### Post by 1clue on 2016-01-03
> **vellon said:**
> Interesting. As a long-time Arch user, it seems to me to have a very healthy user base, and that has been the case for years, without the schisms of other distros. It is true that the Arch forums are not exactly chatty, but they are to the point and without extraneous noise. That suits me, and many others, and it is not like Arch hides its approach and expectations.

This is exactly the sort of thing I'm talking about. Before you adopt a distro, you need to check out things like the community.  If you like it, it's good.  If you don't then try something else.  I checked out the forum and found it unpleasant, and you found it good.  It does not mean arch is a bad distro or that either of our opinions are wrong, it just means I don't like the community.  I don't generally make a big fuss about it, there are a lot of things I like about the distro. My opinion of the forums generally drives my preference of Gentoo over Arch, which was the question posed to me.

Peace.

---

### Post by mastablasta on 2016-01-05
> **rosswmcgee said:**
>  I am unsure why distrowatch shows mint, and debian with more users while ubuntu keeps losing. I had to ditch mint

It's not showing users. it's showing interest in distro. so you can be interesting in something but not using it. like for example I am interested in a new and bigger family car, but I am actually using an old small city car hwere all of us have to cramp inside...


> **1clue said:**
> This is exactly the sort of thing I'm talking about. Before you adopt a distro, you need to check out things like the community.  If you like it, it's good.  If you don't then try something else.  I checked out the forum and found it unpleasant, and you found it good.  It does not mean arch is a bad distro or that either of our opinions are wrong, it just means I don't like the community.  I don't generally make a big fuss about it, there are a lot of things I like about the distro. My opinion of the forums generally drives my preference of Gentoo over Arch, which was the question posed to me.

Peace.

so people first check the community on windows to decide if they will upgrade or use windows or not? :) I never even visited any windows community. still first thing I do is check support. documentation etc. how well it's all layed out, how easy it is to setup, are things automated with sane defaults or do you need to unnecessarily set everything up and spend a week just to install the OS...

---

### Post by Kale_Freemon on 2016-01-10
Another one, that I really liked when I used it, is SolydK. It's a semi-rolling release distro that is similar to LMDE in that it uses Update Packs to release updates every so often. Very stable, I never had an issue with it. Comes with KDE preinstalled and looks beautiful. Well maintained and has an awesome community behind it.

[http://solydxk.com/](http://solydxk.com/)

At the very least, it's worth looking at.

---

### Post by 1clue on 2016-01-10
> **mastablasta said:**
> so people first check the community on windows to decide if they will upgrade or use windows or not? :) I never even visited any windows community. still first thing I do is check support. documentation etc. how well it's all layed out, how easy it is to setup, are things automated with sane defaults or do you need to unnecessarily set everything up and spend a week just to install the OS...

[LIST=1]
[*]Very few people shop for operating systems and then install Windows.  They buy a computer and Windows is on it.  They may choose Mac OS vs Windows, but again they're choosing as one would pick Ford vs Chevy or BMW vs Mercedes.  Almost nobody builds a computer from scratch and then installs Windows on it after agonizing Windows vs Mac vs Solaris vs 6 different Linux variants vs FreeBSD.
[*]The choice of whether or not to upgrade Windows is very different from the choice to install it in the first place.
[*]"The community" of a linux distro often includes the documentation and support.  A traditional non-sponsored distro usually has "support" as the forum, exactly.  The documentation was written by volunteers who use the OS, not by paid employees the way Ubuntu and RedHat and Suse do it.
[*]How easy a distro is to set up is a valid decision point, but not everyone holds that to be near the top of the list.  My favorite distro is Gentoo, if ease of installation were important then I probably would never have installed it.
[/LIST]

Everyone has different priorities, and different ideas of how things should be done.  If we all wanted the same things and had the same priorities, the entire world would be using exactly one desktop OS.  I relish the idea that we all want things to work differently, and in fact I personally install a number of distros on systems I own or manage, based on the needs of the system and my preferences on how things should be done.

I do things differently than you do, but that doesn't make the way you do things wrong.  It simply reinforces the fact that everyone is different and has different needs and preferences, and we should be happy about that.

---

### Post by sammiev on 2016-01-10
> **Kale_Freemon said:**
> Another one, that I really liked when I used it, is SolydK. It's a semi-rolling release distro that is similar to LMDE in that it uses Update Packs to release updates every so often. Very stable, I never had an issue with it. Comes with KDE preinstalled and looks beautiful. Well maintained and has an awesome community behind it.

[http://solydxk.com/](http://solydxk.com/)

At the very least, it's worth looking at.

+1 But it's not cutting edge.

---

### Post by vasa1 on 2016-01-11
> **mastablasta said:**
> ...
so people first check the community on windows to decide if they will upgrade or use windows or not? :) I never even visited any windows community. still first thing I do is check support. documentation etc. how well it's all layed out, how easy it is to setup, are things automated with sane defaults or do you need to unnecessarily set everything up and spend a week just to install the OS...

I checked various linux communities as well as "official" support and documentation. One issue with official stuff is that there may be an element of puffery in there. The positives will be played up and the negatives played down. This is "interesting": [http://www.wilderssecurity.com/threads/microsoft-warns-windows-7-has-serious-problems.382728/](http://www.wilderssecurity.com/threads/microsoft-warns-windows-7-has-serious-problems.382728/)

---

### Post by ChuangTzu on 2016-01-12
I would suggest that if you want a rolling release then use a distro that is designed to be rolling.  ie: Arch or Gentoo or their derivatives.  The other distros, may have a rolling feature but they are more designed as a "not yet ready" model.  Manjaro helps some to enter Arch, however, it also has its short comings.  For instance, slower on updates, does not teach the user how to solve problems that will arise with rolling distros etc...

---

### Post by user1397 on 2016-02-18
In case anyone cares and was wondering what I finally decided, I decided I don't really need a rolling release system because it doesn't affect my computing at all for 99% of the programs I have installed, and those few programs that I might need the latest version of I can just find a ppa for them.

Every other criteria I laid out is met by kubuntu, so I guess I shall stick with kubuntu for now.  One little gripe I used to have with kubuntu and many other distros is the default packages installed.  There were many programs installed by default that I would never use, so I thought it was a bit annoying that I had to have these and would have rather built app my system from the ground up, or at least installed desktop apps from a small default base.  Anywho, I discovered that it's actually pretty easy to remove all the apps I don't use from the default install, so this doesn't really bother me anymore.  I do wish kubuntu would not come pre-installed with certain things but it's really not much of a hassle to get rid of the stuff I don't want.

Either way, I read all your posts/advice and played around with several distros before settling back with charming little kubuntu, so thanks everyone for the input :P

---

### Post by Bucky Ball on 2016-02-18
Do a Ubuntu minimal install, don't choose a machine profile, reboot, you will be at a cursor, log in and issue:

> sudo apt-get install kde-plasma-desktop

[See here.]("https://help.ubuntu.com/community/InstallingKDE") You might need a login manager too but reboot and see what happens. 

The skin and bones of Kubuntu and not much more. I guess it would be similar to Kubuntu-core, if there was one (see Xubuntu-core and Lubuntu-core).

From [here]("https://wiki.debian.org/KDE"):
> KDE Plasma Desktop:  This is a minimalist plasma desktop (You have to install all end-user applications later).

---

### Post by user1397 on 2016-02-18
> **Bucky Ball said:**
> Do a Ubuntu minimal install, don't choose a machine profile, reboot, you will be at a cursor, log in and issue:



[See here.]("https://help.ubuntu.com/community/InstallingKDE") You might need a login manager too but reboot and see what happens. 

The skin and bones of Kubuntu and not much more. I guess it would be similar to Kubuntu-core, if there was one (see Xubuntu-core and Lubuntu-core).

From [here]("https://wiki.debian.org/KDE"):Ah yes, I've thought about doing that, although the mini.iso doesn't support UEFI booting.

Although, I guess I could use the server iso...hmm why didn't I think of that earlier! :O

Oh and just to note, the package is just called plasma-desktop, not kde-plasma-desktop (I think it used to be called that but not sure anymore).  Either way thanks for mentioning this!

---

### Post by sudodus on 2016-02-18
Yes, if you start from an Ubuntu Server iso file (and install no server package, only what you would install from mini.iso), you get almost exactly the same result as if you start from mini.iso. And you can do it in UEFI mode :-)

---

### Post by user1397 on 2016-02-18
I'm trying it out right now in virtualbox to test it out :)

---

### Post by Bucky Ball on 2016-02-18
> **ubuntuman001 said:**
> I'm trying it out right now in virtualbox to test it out :)

Top notch. Let us know how it rolls. :D

I attempted a mini.install one day about four years ago and haven't done any other kind since. Love it. 

Oh, tell I lie, I did do a Xubuntu-core install on my new desktop a couple of weeks ago, but that is pretty close to the mini.

---

### Post by patrikmellq on 2016-02-18
When i join CentOS forum i ask how long support they have for each release and mod reply 10 years.
So there no need to update to new version on Rolling basis.

Cheers

---

### Post by user1397 on 2016-02-18
> **patrikmellq said:**
> When i join CentOS forum i ask how long support they have for each release and mod reply 10 years.
So there no need to update to new version on Rolling basis.

Cheers
Not sure what you're trying to say here...people who look for rolling release distros don't necessarily care about long term support or extreme stability, it's just a different user base.

---

### Post by user1397 on 2016-02-22
> **Bucky Ball said:**
> Top notch. Let us know how it rolls. :D

I attempted a mini.install one day about four years ago and haven't done any other kind since. Love it. 

Oh, tell I lie, I did do a Xubuntu-core install on my new desktop a couple of weeks ago, but that is pretty close to the mini.
So, I went ahead and tried it in virtualbox, and to keep things as clean as possible, every package I installed with the -no-install-recommends argument.

I've gotta say, even though I installed all the apps I wanted, I felt like there were bits missing here and there that made the system function cohesively.  It was also a lot more work than just installing a default kubuntu installation and then removing what you don't want.  Obviously doing it that way you don't remove everything that you don't need, because it is very hard to hunt down every single package and library that you don't need, except for obvious big apps that you can see easily. So there are disadvantages here as well. 

Overall though, it is probably easier and more headache-free to just install the full desktop and remove select apps at your choosing.

Anyone had a similar experience?

---

### Post by Bucky Ball on 2016-02-22
I will add this: A mini install, or at least your first one or two, tend to 'mature' over time. Those missing bits are found and you work out how to get a solid system. By the time you're on your third or fourth it takes not long to get the system as you want it (even less if you are upgrading from release to release cos it already is).

Have fun. :)

---

### Post by 1clue on 2016-02-22
Start a log of the packages you either add to a mini or remove from a full install.  This gives you a base to work from, even though the exact packages you need for any given install will change you'll at least have a base for what works right.

You could create this as a script (sudo apt-get install ...) but over time the names of packages will change, some packages cease to exist and others are replaced by some other project.  Easier to use but harder to maintain, if you get what I'm saying.

---

### Post by user1397 on 2016-02-23
> **Bucky Ball said:**
> I will add this: A mini install, or at least your first one or two, tend to 'mature' over time. Those missing bits are found and you work out how to get a solid system. By the time you're on your third or fourth it takes not long to get the system as you want it (even less if you are upgrading from release to release cos it already is).

Have fun. :)Good point, I shall keep this in mind!

> **1clue said:**
> Start a log of the packages you either add to a mini or remove from a full install.  This gives you a base to work from, even though the exact packages you need for any given install will change you'll at least have a base for what works right.

You could create this as a script (sudo apt-get install ...) but over time the names of packages will change, some packages cease to exist and others are replaced by some other project.  Easier to use but harder to maintain, if you get what I'm saying.That is actually a good idea, I've thought of doing that in the past but I guess I forgot about it as an option this time around.  Once I do have a base package list I could easily write a little script.  Thanks for the idea!

---

