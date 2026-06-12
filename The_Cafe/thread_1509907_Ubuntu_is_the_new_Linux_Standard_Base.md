---
title: "Ubuntu is the new Linux Standard Base"
date: 2010-06-14
forum: The Cafe
---

### Post by chessnerd on 2010-06-14
I'm sorry about the lengthy explanation, feel free to use this summary:

I estimate the the Ubuntu marketshare is around 70%, and is rising, which means that Ubuntu is the de facto standard for Linux. In a way, this makes the Linux Standard Base unimportant.

So, should developers just focus on Ubuntu and forget about other distros?




---

For the last year or so, Ubuntu has been hovering around 50% marketshare according to most statistics websites, like StatOwl.com. However, I think this is inaccurate...

I was analyzing [distro marketshare over the last year]("http://statowl.com/operating_system_market_share_by_os_version_trend.php?1=1&timeframe=last_12&interval=week&chart_id=13&fltr_br=&fltr_os=&fltr_se=&fltr_cn=&limit%5B%5D=linux&interval=month") and I noticed that, for a while, Ubuntu last year was losing out to "Linux Unknown Distribution" This category is used when the websites collecting data can't figure out what distro the browser is running on. It is typically caused by a person installing a different browser, other than one from the repos. Suddenly, in October, it switched back. So I began to wonder, did Ubuntu actually gain a large chunk of the Linux market with 9.10 (Karmic) or did something else happen...

Something else happened: [http://www.mozilla.com/en-US/firefox/3.5/releasenotes/](http://www.mozilla.com/en-US/firefox/3.5/releasenotes/)

Note the date. By June, many Ubuntu users must have installed 3.5 Beta 4, and 3.5 final at the end of the month, while running Jaunty, so the stats were skewed. After Karmic came out, people simply upgraded and then had the latest version in the again. No more FF3.5 skew.

Now, look at that graph again [here]("http://statowl.com/operating_system_market_share_by_os_version_trend.php?1=1&timeframe=last_12&interval=week&chart_id=13&fltr_br=&fltr_os=&fltr_se=&fltr_cn=&limit%5B%5D=linux&interval=month").

Note that, over the last few months, "Linux Unknown Distribution" has been increasing steadily against Linux Ubuntu. I don't think it really is. I think that more people are installing Ubuntu, and using another browser (mainly, Google Chrome and Chromium). So even though Ubuntu is doing better than ever against other distros, it isn't showing up in the stats.

How high is the real marketshare? I would estimate that it would be around 65%. Probably more like 70%. If you include derivatives, it's higher still. 

If this is true, it has some pretty startling implications. An Ubuntu marketshare of 70-75% would make it the de facto standard for desktop Linux. In that case, forget Linux Standard Base. When you have a marketshare above 70% you **become** the standard. 

If my guess is right, why should companies put out .rpm files when Ubuntu and its derivatives use .deb? Why even care about what the Linux Foundation says? Developers might as well just listen to Canonical and the Ubuntu Devs. Why not design programs and hardware to specifically support Ubuntu? The rest of the Linux market is marginal in comparison, after all.

I'm not trying to say that developers really should ignore the LSB, or that they shouldn't develop for Fedora, Arch, OpenSuSE, etc. but when you look at the facts, it's hard to see why more developers don't ignore them...

---

### Post by Timmer1240 on 2010-06-14
Im kinda glad theres a ton of different distros!Its fun to try them out!

---

### Post by chessnerd on 2010-06-14
> **Timmer1240 said:**
> Im kinda glad theres a ton of different distros!Its fun to try them out!

I agree, and I regularly try out distros in VirtualBox and via LiveCD. But it seems like most people don't stick with another distro, they only try them out.

I'm planning on testing (as in, installing) both Fedora 13 and OpenSuSE 11.3 later this summer, but I don't think it's very likely that I will stick with them. I'm sort of even hoping that one of them will "wow" me away from Ubuntu, but I doubt they will...

---

### Post by RATM_Owns on 2010-06-14
What? Forget about all other distros and focus on Ubuntu?
No. Just, no.

If you're saying that since it has the biggest market share in Linux, why not just give up on Mac, Linux, Solaris, etc. and focus on Windows?

---

### Post by Timmer1240 on 2010-06-14
I got crunchbang linux mint and windows xp in virtual box now.I really like crunchbang its lightweight mint I havent played with yet and xp just for the hell of it tiny xp it only draws 42 megs after install really fast.

---

### Post by 23dornot23d on 2010-06-14
Try Zorin OS out ..... (pretty unheard of but based on Ubuntu and Debian fast too)

I have tried most of the major distros at one time or another .....

But this is the first to work 100% with all my hardware and give me an environment thats

a breeze to use ......

---

### Post by Timmer1240 on 2010-06-14
The more distros there are the more creativity and great ideas will come to light other distros like Ubuntu will benefit!They all feed off each other!

---

### Post by Linuxforall on 2010-06-14
Google and IBM concur with you.

---

### Post by kamaboko on 2010-06-14
I think this link is a bit more accurate when it comes to estimating Ubuntu's market share.  

[http://www.workswithu.com/2009/07/24/measuring-ubuntus-market-share/]("http://www.workswithu.com/2009/07/24/measuring-ubuntus-market-share/")

I think one of the big problems is that people, including me, will download every distro flavor from a provider (e.g., ubuntu, kubuntu, etc.).  So does that count as one user, or is that two users?  Moreover, who's to say that I actually installed them?  I may have, but ended up not liking them and reverted back to another OS.  So does that still count as an Ubuntu user?  I doubt Shuttleworth even knows how many.  It's all a guesstimate.

---

### Post by Simian Man on 2010-06-14
[QUOTE=chessnerd]If my guess is right, why should companies put out .rpm files when Ubuntu and its derivatives use .deb? Why even care about what the Linux Foundation says? Developers might as well just listen to Canonical and the Ubuntu Devs. Why not design programs and hardware to specifically support Ubuntu? The rest of the Linux market is marginal in comparison, after all.[/QUOTE]

The thing is that all Linux's are so similar that supporting all of them is usually trivial.  It would actually be pretty hard to "design programs and hardware" that work on one distro but not another.  Packaging is trivial next to original development so that's not as big of an issue as you seem to think.

Another thing you didn't consider is that you're only talking about desktop Linux - ie people who use web browsers.  That's not even where Linux has a significant market-share in the first place!  In the corporate and server worlds, .rpm distros like RHEL, CentOS and Suse are, in my experience, more prevalent than Debian-based distributions.

So basically no, you don't have a good point.

---

### Post by chessnerd on 2010-06-14
> **Simian Man said:**
> The thing is that all Linux's are so similar that supporting all of them is usually trivial.  It would actually be pretty hard to "design programs and hardware" that work on one distro but not another.
There are still issues sometimes.  Opera 10.60 alpha still can't open maximized on my systems running Gnome under Ubuntu 10.04, but it works in XFCE.
I'm not saying companies should attempt to only have them work in Ubuntu only, but why not only test with Ubuntu? Why set aside resources to test with anything other than the de facto Linux standard?

> **Simian Man said:**
> Packaging is trivial next to original development so that's not as big of an issue as you seem to think.
Why, then, do many websites offering Linux software continue to offer it as a tarball? If packaging is so trivial, then it should be easy to offer .deb and .rpm files for software, drivers, etc. but even some big name projects like the Eclipse IDE only offer .tar.gz downloads on their websites. Why not offer a .deb version?

> **Simian Man said:**
> Another thing you didn't consider is that you're only talking about desktop Linux

Yes, I am only talking about desktop Linux. That was intentional.

---

### Post by RiceMonster on 2010-06-14
What Simian Man said.

> **chessnerd said:**
> There are still issues sometimes.  Opera 10.60 alpha still can't open maximized on my systems running Gnome under Ubuntu 10.04, but it works in XFCE.
I'm not saying companies should attempt to only have them work in Ubuntu only, but why not only test with Ubuntu? Why set aside resources to test with anything other than the de facto Linux standard?

Because Ubuntu is not the de facto Linux standard.

> **chessnerd said:**
> Why, then, do many websites offering Linux software continue to offer it as a tarball? If packaging is so trivial, then it should be easy to offer .deb and .rpm files for software, drivers, etc. but even some big name projects like the Eclipse IDE only offer .tar.gz downloads on their websites. Why not offer a .deb version?

Because distributions are expected to package it themselves.

EDIT:
I'd also like to ask you this: Why set aside resources to support Linux at all? I mean, Windows has 90% of the desktop market share!

---

### Post by Simian Man on 2010-06-14
> **chessnerd said:**
> There are still issues sometimes.  Opera 10.60 alpha still can't open maximized on my systems running Gnome under Ubuntu 10.04, but it works in XFCE.
I'm not saying companies should attempt to only have them work in Ubuntu only, but why not only test with Ubuntu? Why set aside resources to test with anything other than the de facto Linux standard?
Well in your example, you have a program that behaves differently under different window managers.  That won't be solved by only targeting one distro.  And I have run a lot of programs on a lot of different distributions and found that there are almost never problems like that.  The ones that do exist tend to be desktop-integration issues that people who don't care about Linux enough to test on a few distros will even get into.

> **chessnerd said:**
> Why, then, do many websites offering Linux software continue to offer it as a tarball? If packaging is so trivial, then it should be easy to offer .deb and .rpm files for software, drivers, etc. but even some big name projects like the Eclipse IDE only offer .tar.gz downloads on their websites. Why not offer a .deb version?
Yes, but Eclipse and its plugins are also packaged into rpms and debs by distributors and sometimes helpful users.  I have never needed to install Eclipse from the site.  If something is useful, people will package it and put it in repositories.  It's not like software packaging is rocket surgery or anything.

> **chessnerd said:**
> Yes, I am only talking about desktop Linux. That was intentional.
Yes, because as we all know people only ever buy hardware or use programs on home user PCs :rolleyes:.

---

### Post by note32 on 2010-06-14
i understand what your saying but ubuntu isn't the "de facto" i would think that linux itself along with all distros counts as one big market share for example ubuntu fedora opensuse centos arch ect.= linux so shouldn't it count as one? and ricemonster is right they don't need to make a package for a specific OS because thats why they have packaging teams for their own OS plus account for the people who dual boot as well

---

### Post by murderslastcrow on 2010-06-14
Linux will most likely succeed Ubuntu if anything were to happen. So no, I don't think we should just drop it all and focus on Ubuntu, despite the fact that it's really good- the diversity is good for everyone, from a security standpoint as well (even if it's an unnecessary addition to security to have dispersed users bases with different default programs).

No one's keeping us from using Ubuntu, why not keep everyone else on board? They contribute to upstream, too, you know.

---

### Post by utnubuuser on 2010-06-14
Ubuntu is Debian, isn't it?

---

### Post by JakeW on 2010-06-14
> **RATM_Owns said:**
> What? Forget about all other distros and focus on Ubuntu?
No. Just, no.

If you're saying that since it has the biggest market share in Linux, why not just give up on Mac, Linux, Solaris, etc. and focus on Windows?

Yea, every game developer did that on us pretty much.

---

### Post by 23dornot23d on 2010-06-15
not sure what happened there .... delete this one please

---

### Post by 23dornot23d on 2010-06-15
> **utnubuuser said:**
> Ubuntu is Debian, isn't it?

As you say its Debian based .... the way some speak its as if Ubuntu was the Grand Daddy
to all the rest ......

Its an Old Roadmap of the systems as they developed

[http://www.litrin.net/UserFiles/Image/Linux_roadmap.jpg](http://www.litrin.net/UserFiles/Image/Linux_roadmap.jpg)

Its all about this really [LINUX]("http://www.softlab.ece.ntua.gr/%7Esivann/pub/swf/switchlinux3.swf")

---

### Post by splicerr on 2010-06-15
> **chessnerd said:**
> Developers might as well just listen to Canonical and the Ubuntu Devs. Why not design programs and hardware to specifically support Ubuntu? The rest of the Linux market is marginal in comparison, after all.

I'm not trying to say that developers really should ignore the LSB, or that they shouldn't develop for Fedora, Arch, OpenSuSE, etc. but when you look at the facts, it's hard to see why more developers don't ignore them...

Developers usually listen to whomever signs their paycheck. As it happens to be a lot of the code in Ubuntu is actually developed by Red Hat employees. Novell also contributes quite a bit to the Linux ecosystem. Canonical not so much. This has earned both Canonical and Ubuntu a bad rep. Please a little less arrogance and a little more gratitude. Without Red Hat and Novell Ubuntu wouldn't even exist. Mark Shuttleworth understands this quite well. It's the Ubuntu users who need a little education on this subject.

---

### Post by Paqman on 2010-06-15
> **RiceMonster said:**
> 
Because Ubuntu is not the de facto Linux standard.


It most certainly is. If, as seems likely, there are more people using Ubuntu than all other distros combined, then it's certainly the de facto standard. It would be a strange decision to package for other distros and not Ubuntu these days.

> **splicerr said:**
> Canonical not so much. This has earned both Canonical and Ubuntu a bad rep.

Canonical is much smaller and newer. I think the rep is largely undeserved.

---

### Post by McRat on 2010-06-15
Like it or not, quantity has a quality all of its own.  I stole that from Joseph Stalin, but it applies.

I downloaded Ubuntu because it was the most common distro.  No other specific reason.  I doubt I'm unique.

This means there will most likely be more support for the product.  Not necessarily from Canonical, but the user base, hardware mfr, and app developers.

*in before the "But Windows Sells The Most":  It isn't working for my needs.*

---

### Post by handy on 2010-06-15
I hope that Ubuntu isn't truly seen as the GNU/Linux desktop standard. It really isn't good enough for the job. 

GNU/Linux needs to do a whole heap of improving before anyone starts talking about there being an existing public standard for the system on the desktop.

GNU/Linux is still rough as guts in so many areas that it really shouldn't be considered to be any more than a beta release (at best) as far as desktop systems are concerned.

---

### Post by McRat on 2010-06-15
> **handy said:**
> I hope that Ubuntu isn't truly seen as the GNU/Linux standard. It really isn't good enough for the job. GNU/Linux needs to do a whole heap of improving before anyone starts talking about there being an existing public standard for the system.

GNU/Linux is still rough as guts in so many areas that it really shouldn't be considered to be any more than a beta release (at best) as far as desktop systems are concerned.


I hear that alot, but I'm not sure what folk mean.

This computer I'm typing on is a Dec 2009 AMD64 Clone.  It would not run Win7.  Kept freezing at random.  Put Ubuntu on it, and it runs like charm, no problems at all.

I've put Ubuntu on 3 late model systems so far and no significant issues.

The only problems I've seen is with 64bit + Wireless N. But I have certainly had my share of wireless problems on WinTel stuff too, unless it was Win tested factory hardware, and that's WITH the Wireless mfr Win driver.

To compare Ubuntu to Windows to OS X, you'd need a neutral ground.

Start with a computer that was not tested for any of them.  Just a bag of parts from a catalog, like this one.

But Yes, OS X runs excellent with Apple Hardware, Win7 runs excellent on a Dell Workstation designed for Win7, and Ubuntu will run excellent on a new clone.

---

### Post by gradinaruvasile on 2010-06-15
> **Paqman said:**
> It most certainly is. If, as seems likely, there are more people using Ubuntu than all other distros combined, then it's certainly the de facto standard. It would be a strange decision to package for other distros and not Ubuntu these days.



Canonical is much smaller and newer. I think the rep is largely undeserved.


Well, Ubuntu certainly is the first distro for many newcomers to Linux to try. But it is developed by a company that has the goal of making money out of it. What if it doesnt work as expected? Ubuntu will dissapear because there is no development team as Debians to move it foward.

You can think of Red Hat/CentOS, but that is a de facto standard for servers mostly - and its reputation comes from extended testing and  proven reliability. That cannot be said about Ubuntu's half years half-baked releases.

Also, many peolpe here tend to overlook the fact that Ubuntu is a distro that has little to offer in terms of originality - it is based on Debian folks - without Debian (and the dedicated work of its developers - unpaid i might add, unlike Canonical's) Ubuntu has no chance of existing.

To make it clear - Ubuntu versions are developed from Debian unstable branch (and now testing as i heard) snapshots taken every six months.
This means that Ubuntu devs copy the Debian repositories when they released a stable version. Then they test/debug it for about 6 months and release it. The problem is that some times there are unresolved bugs remaining that can be quite severe.
Add the fact that users wont reinstall their systems every 6 months - they just upgrade it instead - and this means that sometimes the upgrade process leaves incorrect configurations for some components that were upgraded to new versions.

Some Debian users resent the fact that Ubuntu users usually tend to forget what i said above about Ubuntu's origins (and not think about the fact that Ubuntu depends on Debian for its existence).

And Linux is good as is - unless you dont want another Mac or Windows, let the distros be what they want - it is not that hard to make generic-Linux programs. They are many out there.
Some software makers say that the large number of distros/lack of standards is THE problem here - THE problem is that Linux it is not appealing to them because they dont see the profit in it for now (otherwise thay would have comitted resources to it and made their programs work just as many unpaid developers can).
Anyway Ubuntu has support from most developing Linux programs.


PS: I used Ubuntu since 7.10 (till 10.04) - i know from my own experience how stable it is. Now i use Debian Testing and its more stable than Ubuntu stable.

---

### Post by praveenthivari on 2010-06-15
> Ubuntu is the new Linux Standard Base

Even though I can see wat u meant by this but making Ubuntu a 'Linux Standard' just bcoz it has more market share, would b a huge mistake!!
As earlier posts point out, it's the practice more of 'microsoft' & 'mac' which start exerting and intervening in every process of setting some open standards established. Instead, of improving upon existing ones they try to put theirs as defacto standards. 
But I dont think ubuntu should b following tht. It is more of 'Inclusive'.

Though I would suggest tht, companies provide .deb and in addition an option of source files.( Just bcoz of my assumption tht most new linux users would use Ubuntu first and more advanced users, if they use something else ,can bulid from the source code.)

---

### Post by Johnsie on 2010-06-15
Ubuntu is just a collection of stuff from other distros (with a few minor tweaks)

Without those other distros Ubuntu wouldn't be able to exist.


Also, Linux had a chance to become popular but Apple snuck in because they were better organised and had more money to invest in advertising and hardware. Apples rise to mainstream shows that Microsoft Lock-in isn't what's stopping people moving to alternative systems. People are looking for a high quality, visually appealling that works well with their devices and has some high quality killer apps. Linux simply doesn't provide that and many of the applications look ugly. 

The Ubuntu/Linuxcommunity  cannot compete with the likes of Apple and Microsoft because the Linux community are disorganised, not artistic enough and have very little money.

---

### Post by handy on 2010-06-15
They may be your experiences McRat, though I consider there to be a very long list of people that are waiting for show stopper (let alone all of the other) problems to be solved in Ubuntu GNU/Linux.

Obviously, I personally think that GNU/Linux should grow a LOT before it thinks it is ready to say *I'm what you need*, to Joe/sephine average computer user. First impressions are often the most lasting. Too many problems still exist. 

Don't worry about comparing GNU/Linux to windows, windows has always had its problems, but it has also held something like 90% of the desktop market for over 15 years, which gives it an enormous amount of inertia as far as any force that wants to move it is concerned. 

The Apple computers have somewhat of a head start as they are basically a hardware company that also produces the systems that its hardware uses. It is somewhat of an unfair playing ground as far as Apple is concerned because of this. (I know Apple's systems have problems as we have been using them since the Mac+ days in our household, though compared to either GNU/Linux or windows - which I was a professional tech' for, for 10 years - they are negligible.)

There are far more situations & demands existing out there in the world of computer users than our own computer experience equips us to make valid broad sweeping generalisation with. imho Those that I made above are how it is from my experience. ;)

---

### Post by meho_r on 2010-06-15
> **chessnerd said:**
> ...

I estimate the the Ubuntu marketshare is around 70%, and is rising, which means that Ubuntu is the de facto standard for Linux. In a way, this makes the Linux Standard Base unimportant.
Strange conclusion. Read the definition of the term "standard".

> 
So, should developers just focus on Ubuntu and forget about other distros?

No^n, where *n*—>infinity


> **splicerr said:**
> Developers usually listen to whomever signs their paycheck. As it happens to be a lot of the code in Ubuntu is actually developed by Red Hat employees. Novell also contributes quite a bit to the Linux ecosystem. Canonical not so much. This has earned both Canonical and Ubuntu a bad rep. Please a little less arrogance and a little more gratitude. Without Red Hat and Novell Ubuntu wouldn't even exist. Mark Shuttleworth understands this quite well. It's the Ubuntu users who need a little education on this subject.
Well said.

If we ever come to that that a standard should be set, then that will/should definitelly not be Ubuntu. The most obvious candidates are good old (and I dare to say superior distros) like Debian or Slackware. Apart from being around for a long time and being "original", they are much more reliable and stable. Despite my love to Ubuntu, it simply isn't (and probably will never be) match for those giants.

---

### Post by teilnehmer on 2010-06-15
If I may throw in something - I can see how Ubuntu depends on Debian, and I have no interest in any one distro becoming a standard that makes other distros obsolete. But indeed, Ubuntu (and the K* and X* versions) ist the first Linux system that convincingly appealed to me as a non-technical user. I just checked the Debian homepage, and even to get the install CD, I need knowledge I don't have ([alpha][amd64][arm][armel][hppa][i386][ia64][mips][mipsel][powerpc][sparc][s390][source][multi-arch]... I suppose i386 is correct, but wow... what a choice even before the install). 

So, without talking about a standard, I concur with the thread-starter that Ubuntu plays (and will continue to play) an important role in bringing Linux to desktop PCs, more so than any other distro I'm aware of.

---

### Post by handy on 2010-06-15
> **teilnehmer said:**
> ...
I just checked the Debian homepage, and even to get the install CD, I need knowledge I don't have ([alpha][amd64][arm][armel][hppa][i386][ia64][mips][mipsel][powerpc][sparc][s390][source][multi-arch]... I suppose i386 is correct, but wow... what a choice even before the install). 

A self confessed non-technical user should be the potential user of a new system that does some research.

Do you expect to not have to do some study to learn:

1.) How to choose which system is most likely the best one for me to install?

2.) Does any new system I'm investigating provide the software I need to fulfil my requirements?

3.) Will it suit my hardware & what is my type of hardware called to start with?

4.) How do you install it?

5.) How do I update/upgrade the system & software that I'm using?

There are more questions to be answered, & they are ALL the user/installers/maintainers responsibility. Not the responsibility of the system.

People that do think that it is the responsibility of the system should take the easy way out & just buy a Mac. ;)

---

### Post by wilee-nilee on 2010-06-15
You can pay with your time or your wallet.;)

---

### Post by teilnehmer on 2010-06-15
handy, 

I disagree - let me clarify. I'm very willing to learn stuff regarding Linux. It's an informed choice I made, leaving the well-known windows ground and entering unknown territory. 

So, of course it's my responsibility to learn the necessary stuff. 

Still, a system should pick users up from where they are. With your argument, you could just as well disregard GUI systems. "If people aren't willing to learn how to use a Unix system, well - buy a mac". But the system should make it as easy as possible for the user to learn how to use it. 

Ubuntu makes a good job there, really. Debian wouldn't be any less of a system if they could explain on the site how to decide which version to choose.

I think it's the wrong way round if the system must always stay like it is, and users have to gain the privilege to use it. It is vice versa.

---

### Post by handy on 2010-06-15
> **teilnehmer said:**
> 
handy, 

I disagree - let me clarify. I'm very willing to learn stuff regarding Linux. It's an informed choice I made, leaving the well-known windows ground and entering unknown territory. 

So, of course it's my responsibility to learn the necessary stuff. 

Then you actually agree with me then. :)

> **teilnehmer said:**
> 
Still, a system should pick users up from where they are. 

How can a system know where a user is up to & therefore adjust itself to pick them up from that point?  Sorry, but that really doesn't make sense.

> **teilnehmer said:**
> 
With your argument, you could just as well disregard GUI systems. 

Sorry, you have lost me again?

> **teilnehmer said:**
> 
"If people aren't willing to learn how to use a Unix system, well - buy a mac".  

Some would argue that the underlying BSD based core of the Mac's OS X, is more Unix based than the Linux kernel is.

> **teilnehmer said:**
> 
But the system should make it as easy as possible for the user to learn how to use it. 

Some systems make it easier than others for people to learn. Which is why I used the Mac's system (OS X) as an example (it being the easiest system I have come across in over 25 years of computer experience) in the post that you are replying to. 

On the other hand, there are plenty of systems that require you to have a certain level of knowledge before you will be able to use it. Which is fine, use what you can & don't feel ripped off because you haven't done the work to learn how to use something.

> **teilnehmer said:**
> 
Ubuntu makes a good job there, really. Debian wouldn't be any less of a system if they could explain on the site how to decide which version to choose.

Different systems expect/require different levels of requisite knowledge. If a person doesn't know what x86, x86_64, i386, & the like means & thinks that the 5 minutes required to find out by searching the web is too much trouble then it may be considered that they aren't ready to use the particular system in question.

Really those alphanumeric combinations I mentioned in the previous paragraph are core to system identity. 

I understand why it is expected that a user should have familiarised themselves with their definition. All of us struck those terms for the first time at some stage. I don't think that it was a high percentage of us that blamed those that used the terminology for speaking over our heads at the time... :)

---

### Post by teilnehmer on 2010-06-15
@handy: Hmm, okay, maybe our opinions don't differ that much, actually. 

> **handy said:**
> 
Some systems make it easier than others for people to learn. 


Agreed. My main point is that Ubuntu is way easier than, say, Debian. As you explain, this can well be based in a different target audience. This greater ease to use Ubuntu means it will appeal to a wider range of newbie users, maybe becoming the "standard" way of entering Linux territory. 
In that regard, *Ubuntu picks people up from earlier on the road, whereas Debian (and others) wait further down the road. 

Maybe my first post sounded as if I *expected* Debian to become more simple. This was not my intention, and I don't feel ripped of because I can't use it. 
Your reply, to me, sounded like I was expected to learn these terms, and prefering Ubuntu due to its ease of use was somehow not a good reason. 

[QUOTE=handy]
People that do think that it is the responsibility of the system should take the easy way out & just buy a Mac.[/QUOTE]

Ubuntu is an easiER way, and therefore will gain a large market share as more users dare the jump. Which is a good thing.

---

### Post by RiceMonster on 2010-06-15
> **Paqman said:**
> It most certainly is. If, as seems likely, there are more people using Ubuntu than all other distros combined, then it's certainly the de facto standard. It would be a strange decision to package for other distros and not Ubuntu these days.

This is only in the home desktop market, which is a very small market for Linux.

> **Paqman said:**
> Canonical is much smaller and newer. I think the rep is largely undeserved.

No. Mandriva, who has less money and employees, and Gentoo, who is entirely voltunteer based have been shown to contribute more upstream code.

---

### Post by seenthelite on 2010-06-15
I think that it is a good thing to have different distro's to try on your system. One main reason being how they install on your hardware. One example I have is on one of my computers using Nvidia driver 195.36.24, with Fedora 13 it works perfectly Ubuntu not so good especially at boot. Fedora's implementation of the Gnome desktop is equal to Ubuntu's imo.

---

### Post by handy on 2010-06-15
Speaking of Fedora, I hear that many well versed Linux distro users consider Fedora to be the easiest distro to use these days.

---

### Post by amauk on 2010-06-15
One operating system cannot hope to cater for all use cases

The day there is one "standard" linux distro, is the day that Linux only caters for a single use case

Variety and choice breeds competition and innovation

When one distro develops a new (or improved) way of doing things, others may follow and improve further

Of course, API standards are important
hence the LSB, and freedesktop.org

KDE developed DCop
Gnome (and others) got on board, developed further
Standard DBus interface evolved

Redhat develops NetworkManager
other distros like it, adopt and improve it

Ubuntu develops Upstart for starting services in parallel
other distros like it, adopt and improve it

Compiz sparks people's imaginations with desktop compositing
KDE (and as of V3, Gnome) adopt compositing as a core part of their environments

Different distros attract different people
Different people have different ideas
all ideas benefit everybody

One distro to rule them all would be a huge step backwards, and is not in the spirit of open source and free software

---

### Post by Dragonbite on 2010-06-15
> **chessnerd said:**
> 

So, should developers just focus on Ubuntu and forget about other distros?

If this is true, it has some pretty startling implications. An Ubuntu marketshare of 70-75% would make it the de facto standard for desktop Linux. In that case, forget Linux Standard Base. When you have a marketshare above 70% you **become** the standard. 

If my guess is right, why should companies put out .rpm files when Ubuntu and its derivatives use .deb? Why even care about what the Linux Foundation says? Developers might as well just listen to Canonical and the Ubuntu Devs. Why not design programs and hardware to specifically support Ubuntu? The rest of the Linux market is marginal in comparison, after all.

I'm not trying to say that developers really should ignore the LSB, or that they shouldn't develop for Fedora, Arch, OpenSuSE, etc. but when you look at the facts, it's hard to see why more developers don't ignore them...

That is so Microsoft-like.  

Because it's the "largest" it is the defacto-standard? That may be "true", but does that mean it is the "best"? Isn't that what got us some sites which are IE focused, using things "standard" in IE because it was the "defacto-standard"?

Why not stick with Windows, because even MORE developers develop for it and it has the LARGEST user base and *IS* the defacto-standard!

How many of those Ubuntu numbers are servers running in Enterprises?  They don't browse on their own, so how are they counted?  What about embedded devices?  

Maybe more of those "Unknown" are Androids, which according to that chart is increasing and will overtake it someday considering it is pre-installed on a larger number of devices than Ubuntu.  The chart doesn't show as big of a difference when you break it down between Corporate and Residential.

The strength in Linux is in there diversity of choices.  Release first, release often.

---

### Post by Paqman on 2010-06-15
> **RiceMonster said:**
> This is only in the home desktop market, which is a very small market for Linux.


True. Ubuntu is starting to make pretty good headway in the server market though. I've not seen any figures, but i'd expect it's still a long way off Red Hat.


> 
Mandriva, who has less money and employees, and Gentoo, who is entirely voltunteer based have been shown to contribute more upstream code.

I think I have more money in my wallet than Mandriva has in their bank account.

Seriously though, both have also been around a lot longer, and have been able to build up the upstream relationships. Maybe Ubuntu should contribute more upstream, I know they certainly want to.

---

### Post by Linuxforall on 2010-06-15
Ubuntu's contribution is to make desktop Linux feasible to the world and in that they have done a mighty fine job, let Fedora do the cutting edge work and Ubuntu spread linux.

---

### Post by RiceMonster on 2010-06-15
> **Paqman said:**
> Seriously though, both have also been around a lot longer, and have been able to build up the upstream relationships. Maybe Ubuntu should contribute more upstream, I know they certainly want to.

But if they're shown to contribute less with a set time span, what does being new have to do with it? If they want to, why don't they?

---

### Post by varunendra on 2010-06-15
> **chessnerd said:**
> But it seems like most people don't stick with another distro, they only try them out. I do stick with Slax (ready to use PXE server, smaller than Ubuntu to load into RAM), DSL (50+MB? Damn! Plays Media Files too? Damn-Damn!!). Planning to stick with CentOS/Debian for my server (Only because of its reputation apparent on net, the same reason why I stuck with Ubuntu for my Desktop).

> **murderslastcrow said:**
> No one's keeping us from using Ubuntu, why not keep everyone else on board? They contribute to upstream, too, you know.
+1

> **utnubuuser said:**
> Ubuntu is Debian, isn't it?
+1

> **Paqman said:**
> It would be a strange decision to package for other distros and not Ubuntu these days.
I agree, totally!! But there are other distros which are popular because of things that don't need adding additional packages.
They do little, but do it best!

> **handy said:**
> GNU/Linux needs to do a whole heap of improving before anyone starts talking about there being an existing public standard for the system on the desktop.
+1

> **McRat said:**
> This computer I'm typing on is a Dec 2009 AMD64 Clone.  It would not run Win7.  Kept freezing at random.  Put Ubuntu on it, and it runs like charm, no problems at all.
Put DSL on it, it'll become even more charming! :)

> **gradinaruvasile said:**
> You can think of Red Hat/CentOS, but that is a de facto standard for servers mostly - and its reputation comes from extended testing and  proven reliability. That cannot be said about Ubuntu's half years half-baked releases.
+1 (well... the 'half-baked' terminology doesn'y seem so convincing ;))

> **teilnehmer said:**
> But indeed, Ubuntu (and the K* and X* versions) ist the first Linux system that convincingly appealed to me as a non-technical user........... ..... ........... .......So, without talking about a standard, I concur with the thread-starter that Ubuntu plays (and will continue to play) an important role in bringing Linux to desktop PCs, more so than any other distro I'm aware of.That's like bringing a weeping child to the school, making the school less scary somehow. However, later the same child may wish to have advanced & discrete studies! Then what?

> **wilee-nilee said:**
> You can pay with your time or your wallet.;)
lol. I wonder though if paying with time is making me bankrupt or even more richer?? ;)


My original opinion: **Ubuntu is undoubtedly GREAT!!!!!!!....... (infinity),** _but diversity & choice is better_. And I say it with experience. When I need another one, I need only that one!

---

### Post by MCVenom on 2010-06-15
> **Dragonbite said:**
> Maybe more of those "Unknown" are Androids, which according to that chart is increasing and will overtake it someday considering it is pre-installed on a larger number of devices than Ubuntu.

Just wanted to point out that for some strange reason (probably having to do with Webkit) some sites mistakenly identify the Android Browser as being Safari on a Mac/iPhone/or simply an Unknown Safari-running Platform. :P

---

### Post by Paqman on 2010-06-15
> **RiceMonster said:**
> If they want to, why don't they?

I don't know, but I suspect there isn't just one answer. Their devs could all be working on stuff that has no upstream, or they could have taken design decisions that create a delta between their code that upstream aren't interested in, or lots of other stuff.

I heard an interesting interview with Jorge Castro from Canonical on the [Ubuntu UK Podcast]("http://podcast.ubuntu-uk.org/") just the other day. He was talking about the complexity of building healthy upstream relationships. Check it out.

---

### Post by MisfitI38 on 2010-06-15
> **Simian Man said:**
> The thing is that all Linux's are so similar that supporting all of them is usually trivial.  It would actually be pretty hard to "design programs and hardware" that work on one distro but not another.  Packaging is trivial next to original development so that's not as big of an issue as you seem to think.

Another thing you didn't consider is that you're only talking about desktop Linux - ie people who use web browsers.  That's not even where Linux has a significant market-share in the first place!  In the corporate and server worlds, .rpm distros like RHEL, CentOS and Suse are, in my experience, more prevalent than Debian-based distributions.

So basically no, you don't have a good point.
Agreed completely.
With open source, the distro is a non-issue. Even binary blobs are distro-agnostic, only relying on kernel version and hardware spec.

---

### Post by MisfitI38 on 2010-06-15
> **Paqman said:**
> It most certainly is. If, as seems likely, there are more people using Ubuntu than all other distros combined, then it's certainly the de facto standard. It would be a strange decision to package for other distros and not Ubuntu these days.


'Package for Ubuntu'? 
Distribution developers do the packaging for their own repositories. 
This in itself makes this whole issue a moot point.

---

### Post by madjr on 2010-06-15
i just want ALL linux software to be easy to install (binaries/ppas) in ubuntu, that's all

---

### Post by Paqman on 2010-06-15
> **MisfitI38 said:**
> 'Package for Ubuntu'? 
Distribution developers do the packaging for their own repositories. 
This in itself makes this whole issue a moot point.

You've never come across an app that wasn't in the repos? World of Goo? Handbrake? Virtualbox? Chrome?

---

### Post by Queue29 on 2010-06-15
> **MisfitI38 said:**
> Agreed completely.
Even binary blobs are distro-agnostic, only relying on kernel version and hardware spec.

This could not be further from the truth. Binary blobs are 100% distro specific. Take a look at skype for example, or Flash. The binary blobs have to be repackaged for every distro, and only the major distros (read: Ubuntu, Fedora, and Suse) are targeted.

---

### Post by koenn on 2010-06-15
> **Dragonbite said:**
> That is so Microsoft-like.  

Because it's the "largest" it is the defacto-standard? That may be "true", but does that mean it is the "best"? Isn't that what got us some sites which are IE focused, using things "standard" in IE because it was the "defacto-standard"?

Why not stick with Windows, because even MORE developers develop for it and it has the LARGEST user base and *IS* the defacto-standard!
this.

If you're going to pick an existing distro ad standard, it should be one that gets everything right, both in design and in implementation (and does so in a way that does not make it impossible for others to comply with the standard). 
I would doubt that Ubuntu does everything right.

That said, maybe the LSB also did not get  everything right.

---

### Post by MisfitI38 on 2010-06-15
> **Paqman said:**
> You've never come across an app that wasn't in the repos? World of Goo? Handbrake? Virtualbox? Chrome?
Source?
Who cares?

---

### Post by RiceMonster on 2010-06-15
> **Queue29 said:**
> This could not be further from the truth. Binary blobs are 100% distro specific. Take a look at skype for example, or Flash. The binary blobs have to be repackaged for every distro, and only the major distros (read: Ubuntu, Fedora, and Suse) are targeted.

You can install flash from the tarball on any distro.

---

### Post by MisfitI38 on 2010-06-15
> **Queue29 said:**
> This could not be further from the truth. Binary blobs are 100% distro specific..
[Really?]("http://www.nvidia.com/object/unix.html")

---

### Post by Paqman on 2010-06-15
> **MisfitI38 said:**
> Source?
Who cares?

Not the point. You suggested that all packaging was done by the distros, which is not the case.

---

### Post by Dragonbite on 2010-06-15
> **RiceMonster said:**
> You can install flash from the tarball on any distro.

This is ultimately what allows any Linux distro to be made to do virtually whatever you want!  The advantage with the different Linux Distros is that they "drop you off" closer to your desired setup and usually give you the tools (package manager) to get the rest of the way yourself.

---

### Post by GeoPirate on 2010-06-15
If anything it would make more sense to involve google.  Chrome OS and android are increasing visibility for linux more than ubuntu will ever be able to.

---

### Post by Chame_Wizard on 2010-06-15
Ubuntu the new LSB?Good luck with it(It wouldn't be available without Debian).):P

Linus Torvalds & Linux Foundation are making the decisions.:popcorn:

---

