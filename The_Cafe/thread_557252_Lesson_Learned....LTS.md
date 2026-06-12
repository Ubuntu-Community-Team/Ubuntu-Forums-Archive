---
title: "Lesson Learned....LTS"
date: 2007-09-22
forum: The Cafe
---

### Post by rbalfour on 2007-09-22
Today I learned a great Lesson. LTS doesn't mean Long Term Support. lol.
After helping a friend out today. I found out 6.06 doesn't have Firefox 2.x in the repo. I am sure there will be some "hard-core" user "try" to explain the reason, But I am too a "hard-core" user and I find this kind of dumb. Thought Ubuntu was trying to push into the Enterprise...dang, I have been pushing Ubuntu (6.06LTS) as that...but who wants to use old version of broken software. The next "LTS" that comes out, should be a bit MORE focused. Hey it's great to have the latest and greatest. But let's at least keep the LTS current. 

no using unsupported 3rd party apps to install a standard app in "other" OSes is not an option.

Anywhoo...I moved onto 7.04...I'll wait for Gold version of LTS *wink*

--------PRINT ME and POST ME--------------------

[SIZE="6"]ENTERPRISE is the GOAL![/SIZE]

--------PRINT ME and POST ME--------------------

---

### Post by Nano Geek on 2007-09-22
You do realize that LTS doesn't mean that it will include the latest packages, it means that you will get security updates for five years.

I believe that you can enable the Dapper Drake Backports repository though.

---

### Post by PilotJLR on 2007-09-22
Are talking about known broken software? Can you provide details???

As the previous poster mentions, the purpose of enterprise software is not to be bleeding edge, but rather use stable and tested versions.

---

### Post by karellen on 2007-09-22
LTS aims for stability, not for up-to-date packages

---

### Post by n3tfury on 2007-09-22
well, that was a rant for nothing.  second great Lesson of the day?

---

### Post by FuturePilot on 2007-09-22
Yes, it aims at stability and long term support. It doesn't mean it will have the latest version of a piece of software. If you really want Firefox 2 on Dapper try [Ubuntuzilla.]("http://ubuntuzilla.wiki.sourceforge.net/")

---

### Post by 23meg on 2007-09-22
And besides, not having the latest packages isn't a trait specific to LTS versions; it applies to every stable release. Once a release is stable, it only gets security updates and fixes for critical bugs, unless you use backports.

---

### Post by ThinkBuntu on 2007-09-22
> **rbalfour said:**
> Today I learned a great Lesson. LTS doesn't mean Long Term Support. lol.
After helping a friend out today. I found out 6.06 doesn't have Firefox 2.x in the repo. I am sure there will be some "hard-core" user "try" to explain the reason, But I am too a "hard-core" user and I find this kind of dumb. Thought Ubuntu was trying to push into the Enterprise...dang, I have been pushing Ubuntu (6.06LTS) as that...but who wants to use old version of broken software. The next "LTS" that comes out, should be a bit MORE focused. Hey it's great to have the latest and greatest. But let's at least keep the LTS current. 

no using unsupported 3rd party apps to install a standard app in "other" OSes is not an option.

Anywhoo...I moved onto 7.04...I'll wait for Gold version of LTS *wink*

--------PRINT ME and POST ME--------------------

[SIZE="6"]ENTERPRISE is the GOAL![/SIZE]

--------PRINT ME and POST ME--------------------
You are so right. Stable doesn't have to mean old. Packages should be upgraded to their latest stable releases, which would certainly include the version of Firefox you've mentioned.

---

### Post by Polygon on 2007-09-22
yep. Since firefox 2.0 came out after dapper, to avoid breaking other things in the system they didnt upgrade firefox.

Install it manually from mozilla or search for a deb on like getdeb.net if you really want it in dapper

---

### Post by bruce89 on 2007-09-22
```
bruce@Scooby-Dum:~$ apt-cache rdepends firefox
firefox
Reverse Depends:
  zekr
 |tiemu
 |sun-java6-plugin
 |sun-java5-plugin
 |mozilla-mplayer
  j2re1.4-mozilla-plugin
  flashplugin-nonfree
 |xfig-doc
 |wysihtml-el
 |wmnetselect
 |webhttrack
  ubuntustudio-desktop
 |tilp
  peercast-handlers
 |nip2
  mythbuntu-desktop
 |mozplugger
 |mozilla-venkman
 |mozilla-tabextensions
  mozilla-stumbleupon
  mozilla-plugin-pcmanx
 |mozilla-openoffice.org
 |mozilla-nukeimage
  mozilla-livehttpheaders
 |mozilla-imagezoom
 |mozilla-firefox-adblock
 |mozilla-diggler
  mozilla-ctxextensions
 |mozilla-bookmarksftp
 |mozilla-bonobo
 |mozilla-biofox
  mozilla-beagle
  monodevelop
  miro
  listen
 |lastfm
  junior-internet
  hunspell-uz
  hunspell-de-de
  hunspell-de-ch
  hunspell-de-at
 |gcjwebplugin-4.2
 |gcjwebplugin-4.1
  galeon
  firefox-webdeveloper
  firefox-webdeveloper
 |firefox-sage
  firefox-launchpad-plugin
  firefox-greasemonkey
  firefox-greasemonkey
  firefox-dom-inspector
  firefox-dom-inspector
 |fibusql
 |endeavour2
  education-standalone
 |centerim-utf8
 |centerim-fribidi
 |centerim
  yelp
  xubuntu-desktop
 |xdg-utils
  ubuntu-serverguide
  ubuntu-desktop
  ubufox
  packaging-guide
 |openoffice.org
  mozilla-firefox-locale-zu
  mozilla-firefox-locale-zu
 |mozilla-firefox-locale-zu
  mozilla-firefox-locale-zh-tw
  mozilla-firefox-locale-zh-tw
 |mozilla-firefox-locale-zh-tw
  mozilla-firefox-locale-zh-cn
  mozilla-firefox-locale-zh-cn
 |mozilla-firefox-locale-zh-cn
  mozilla-firefox-locale-tr-tr
  mozilla-firefox-locale-tr-tr
 |mozilla-firefox-locale-tr-tr
  mozilla-firefox-locale-sv-se
  mozilla-firefox-locale-sv-se
 |mozilla-firefox-locale-sv-se
  mozilla-firefox-locale-sl-si
  mozilla-firefox-locale-sl-si
 |mozilla-firefox-locale-sl-si
  mozilla-firefox-locale-sk
  mozilla-firefox-locale-sk
 |mozilla-firefox-locale-sk
  mozilla-firefox-locale-ru-ru
  mozilla-firefox-locale-ru-ru
 |mozilla-firefox-locale-ru-ru
  mozilla-firefox-locale-ro-ro
  mozilla-firefox-locale-ro-ro
 |mozilla-firefox-locale-ro-ro
  mozilla-firefox-locale-pt-pt
  mozilla-firefox-locale-pt-pt
 |mozilla-firefox-locale-pt-pt
  mozilla-firefox-locale-pt-br
  mozilla-firefox-locale-pt-br
 |mozilla-firefox-locale-pt-br
  mozilla-firefox-locale-pl-pl
  mozilla-firefox-locale-pl-pl
 |mozilla-firefox-locale-pl-pl
  mozilla-firefox-locale-pa-in
  mozilla-firefox-locale-pa-in
 |mozilla-firefox-locale-pa-in
  mozilla-firefox-locale-nso
  mozilla-firefox-locale-nso
 |mozilla-firefox-locale-nso
  mozilla-firefox-locale-nn-no
  mozilla-firefox-locale-nn-no
 |mozilla-firefox-locale-nn-no
  mozilla-firefox-locale-nl-nl
  mozilla-firefox-locale-nl-nl
 |mozilla-firefox-locale-nl-nl
  mozilla-firefox-locale-nb-no
  mozilla-firefox-locale-nb-no
 |mozilla-firefox-locale-nb-no
  mozilla-firefox-locale-mn
  mozilla-firefox-locale-mn
 |mozilla-firefox-locale-mn
  mozilla-firefox-locale-mk-mk
  mozilla-firefox-locale-mk-mk
 |mozilla-firefox-locale-mk-mk
  mozilla-firefox-locale-lt
  mozilla-firefox-locale-lt
 |mozilla-firefox-locale-lt
  mozilla-firefox-locale-ku
  mozilla-firefox-locale-ku
 |mozilla-firefox-locale-ku
  mozilla-firefox-locale-ko
  mozilla-firefox-locale-ko
 |mozilla-firefox-locale-ko
  mozilla-firefox-locale-ka-ge
  mozilla-firefox-locale-ka-ge
 |mozilla-firefox-locale-ka-ge
  mozilla-firefox-locale-ja-jp
  mozilla-firefox-locale-ja-jp
 |mozilla-firefox-locale-ja-jp
  mozilla-firefox-locale-it-it
  mozilla-firefox-locale-it-it
 |mozilla-firefox-locale-it-it
  mozilla-firefox-locale-hu-hu
  mozilla-firefox-locale-hu-hu
 |mozilla-firefox-locale-hu-hu
  mozilla-firefox-locale-he-il
  mozilla-firefox-locale-he-il
 |mozilla-firefox-locale-he-il
  mozilla-firefox-locale-gu-in
  mozilla-firefox-locale-gu-in
 |mozilla-firefox-locale-gu-in
  mozilla-firefox-locale-ga-ie
  mozilla-firefox-locale-ga-ie
 |mozilla-firefox-locale-ga-ie
  mozilla-firefox-locale-fy-nl
  mozilla-firefox-locale-fy-nl
 |mozilla-firefox-locale-fy-nl
  mozilla-firefox-locale-fr-fr
  mozilla-firefox-locale-fr-fr
 |mozilla-firefox-locale-fr-fr
  mozilla-firefox-locale-fi-fi
  mozilla-firefox-locale-fi-fi
 |mozilla-firefox-locale-fi-fi
  mozilla-firefox-locale-eu
  mozilla-firefox-locale-eu
 |mozilla-firefox-locale-eu
  mozilla-firefox-locale-es-es
  mozilla-firefox-locale-es-es
 |mozilla-firefox-locale-es-es
  mozilla-firefox-locale-es-ar
  mozilla-firefox-locale-es-ar
 |mozilla-firefox-locale-es-ar
  mozilla-firefox-locale-en-gb
  mozilla-firefox-locale-en-gb
 |mozilla-firefox-locale-en-gb
  mozilla-firefox-locale-el
  mozilla-firefox-locale-el
 |mozilla-firefox-locale-el
  mozilla-firefox-locale-de-de
  mozilla-firefox-locale-de-de
 |mozilla-firefox-locale-de-de
  mozilla-firefox-locale-da-dk
  mozilla-firefox-locale-da-dk
 |mozilla-firefox-locale-da-dk
  mozilla-firefox-locale-cs-cz
  mozilla-firefox-locale-cs-cz
 |mozilla-firefox-locale-cs-cz
  mozilla-firefox-locale-ca
  mozilla-firefox-locale-ca
 |mozilla-firefox-locale-ca
  mozilla-firefox-locale-bg-bg
  mozilla-firefox-locale-bg-bg
 |mozilla-firefox-locale-bg-bg
  mozilla-firefox-locale-be
  mozilla-firefox-locale-be
 |mozilla-firefox-locale-be
  mozilla-firefox-locale-ar
  mozilla-firefox-locale-ar
 |mozilla-firefox-locale-ar
  mozilla-firefox-locale-af
  mozilla-firefox-locale-af
 |mozilla-firefox-locale-af
  liferea
  libgecko2.0-cil
  gobuntu-desktop
  firefox-themes-ubuntu
  firefox-libthai
  firefox-gnome-support
  firefox-dev
  firefox-dbg
 |epydoc-doc
  epiphany-browser
  edubuntu-desktop
  devhelp
```

Want to rebuild all the above packages?

Firefox 1.5 -> 2.0 was boring, the only reason people think it's a big jump us Mozilla's stupid version numbering policy. The internal Gecko version number went from 1.8 to 1.8.1 between 1.5 and 2.0, this is a better indication of how much happened.

---

### Post by az on 2007-09-22
> **ThinkBuntu said:**
> You are so right. Stable doesn't have to mean old. Packages should be upgraded to their latest stable releases, which would certainly include the version of Firefox you've mentioned.

So then, every release should be an LTS.

I think that would be great, but it is not feasable at this point.  That would sacrifice developer time.  I would prefer development moves forward faster than trying to make everything work together on the binary level.

---

### Post by ThinkBuntu on 2007-09-22
> **az said:**
> So then, every release should be an LTS.

I think that would be great, but it is not feasable at this point.  That would sacrifice developer time.  I would prefer development moves forward faster than trying to make everything work together on the binary level.
Debian already takes care of it. Just grab the package when it hits Debian Testing, and continue to update periodically as the package becomes more stable (same version, pretty much). Only make the backports-style upgrades available for major apps.

---

### Post by ryno519 on 2007-09-22
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by bruce89 on 2007-09-22
> **ryno519 said:**
> ```
sudo apt-get update
sudo apt-get dist-upgrade
```

That won't do very much.
```

gksudo update-manager -c
``` is what you're after.

---

### Post by DjBones on 2007-09-23
i agree, that the stable version of ubuntu should contain the stable packages of the programs (at the current time).
but the way the repositories work is that they are snapshots of debian's in six month intervals, so it makes it difficult to add and subtract these things lol

not quite such a big deal, i wouldn't think many enterprises would use dapper over redhats support and debians stability. good idea though haha

---

### Post by rbalfour on 2007-09-23
hmmmm.....all the replies I expected.

1) 6.06 LTS* should be the name.
   *) only security updates and patches

of

1B) 6.0.6 LTS (Long term security)

2) I am not asking for beta-ware / RC1/2/3/4/whatever, but production versions.
Business doesn't wait.

3) we are *WAY* past this is a geek-only distro. Sun/Dell/Ubuntu Mobile (ohh) and if Bleeding edge is keeping up with *commercial* operating systems, then it needs to be done.

4) Let's not forget, the whole *reason* for Ubuntu. Linux for the masses! 

5) i am not slamming Ubuntu, When I came from FC3 to Ubuntu 5.10, that was it for me. There was nothing better and i still believe there isn't.

6) think little more about John Q. Public.

7) Backports, bah. 6.06 LTS should be in the lime light all the time. It's suppose to be the "crown jewel" here.

8) see point 6.

---

### Post by zugu on 2007-09-23
rbalfour, I completely understand your disappointment. There is a similar thread [here]("http://ubuntuforums.org/showthread.php?t=446095"), about the availability of Firefox 3 on Dapper.

I heard many users replying to the problem you described with slightly incorrect stock answers like "LTS is for servers", or "LTS is meant to be stable and that's why we don't get newer versions of packages". Unavailability of newer packages in Dapper is not a Dapper only problem, it's a problem of the whole Ubuntu project. And Dapper is not a "server-ony" operating systems, it is still supported on the desktop (the support period is three years from the release).

When I switched to Ubuntu I expected to use Dapper for three years, and to be able to find newer versions of packages in the repositories in this time. Unfortunately, I found out that I need to upgrade my system every six months in order to gain access to newer versions of basic software like Firefox.

The dapper-backports repositories are almost empty, and critical software like Firefox will not be backported because "it will break things". The moment I learned about this I switched back to Windows XP, where I get security patches from Microsoft AND I can install whatever version of Firefox I like.

Of course, you can grab Firefox 2 for Dapper from third-party repos, or you can compile it yourself if you have the knowledge, but it puts your OS at danger. Why do you think the backports people didn't backport it in the first place? Also, the package manager on your system will not be aware of compiled versions of anything.

You might want to use some BSD distro, where you have a base system that doesn't change too often, and you can install anything on top of it, just like in Windows or Mac OS X.

Everyone praises Ubuntu for software availability, except that this is nothing to be praised, it's Ubuntu's biggest problem.

---

### Post by Polygon on 2007-09-23
you guys dont really get it, if ubuntu just ported every single program that got a new version back to dapper chances are something will break. the whole point of the testing phase is to add new features and then test it and fix any problems with the current repository of packages. If they just randomly upgrade any package that gets updated then when something does break, everyone will slam ubuntu for not making sure that everything works together properly

point is, if you want the latest packages and software (mostly), use the latest release of ubuntu. you can easily upgrade using the update manager.

if you want a stable release that is STABLE, which means that you use outdated packages because those outdated packages have been tested with the operating system as a whole and dont cause any problems, and want SECURITY Updates for its supported lifespan, then use a LTS release.

---

### Post by zugu on 2007-09-23
That is because Ubuntu is not trying to be an operating system. It tries to be everything. That's an impossible approach, because it's impossible to satisfy every taste and need. So I say the Ubuntu community should focus on a base system that gets released every two years. That is called A PLATFORM. Of course, there's nothing wrong with security updates, Windows XP gets them for 6 years now, and it's basically the same as the Windows XP released back in 2001.

Just take a look at Firefox: we have the base browser and a plethora of extensions. In the Apple world, we have an operating system and lots of applications that can be attached to the OS in any way the user likes. Same for Windows. I just described three pieces of software that are very successful, and we can "blame" a great part of their success on their modularity, flexibility and backwards compatibility.

Ubuntu is STIFF. And every six months we give the developers another stiff release. How about we give them A PLATFORM to develop on? Cause I feel that something that changes every six months cannot be called a platform. Especially when it locks users in old versions of software.

---

### Post by 23meg on 2007-09-23
> **zugu]So I say the Ubuntu community should focus on a base system that gets released every two years. That is called A PLATFORM.[/QUOTE]

Well, there's something that gets released every two years: a LTS version. Would you call that a platform? It doesn't change anything said:**
> **Lifehacker: You mentioned long-term support in the release cycle. Recently there have been some criticisms saying that the release cycle is too short. Obviously the six-month release cycle is drastically different than that used by commercial operating systems. In your opinion, what are the advantages and disadvantages of this compressed development cycle, and do you think as Ubuntu matures in the future you will stick with this six month cycle or will you extend it?**

Mark Shuttleworth: To understand the Ubuntu release cycle you should think of two separate cycles that are superimposed onto one another. The first cycle is a regular six-month release, and we consider those releases production-ready. There are people who deploy them in the data center and there are people who deploy them in production, on desktops. They focus primarily on the integration of the latest cutting-edge stable code. These are all stable, upstream components that have security updates and fixes available for them and they are safe to deploy. The emphasis is on the fact that they really are current. Those are only supported for 18 months and we will only make maintenance changes and improvements to those releases for 18 months. Every four of those releases we designate as "LTS." This is the second cycle that is roughly a two-year process. You get a much longer maintenance commitment for those releases. This allows people to pick and choose. If they only want to stay on [operating systems] which are only going to be released every two or so years and supported for three to five years, then they can stick to the LTS releases. If they want to maintain a cutting-edge focus they will move from six-month release to six-month release. We do put a lot of emphasis on the upgrade process. You don't have to reinstall, you can simply upgrade. We're having increasingly good results with people who move from one release to the next.

---

### Post by zugu on 2007-09-23
Dear 23meg, you either can't see my point (and that would be a shame, because I believe you to be an intelligent person) or you don't want to see my point.

Having Dapper in feature freeze, just like the other versions released until now, doesn't make it a platform. A platform is something that allows me to build on top of it, both as a user and as a developer.

Compare it to building a PC by yourself. Nearly unlimited choices.Whereas with Ubuntu it's like buying an Apple and sticking with the initial hardware configuration due to a vendor design (read "lock-in") decision.

---

### Post by 23meg on 2007-09-23
I understand your point, but I'm under the impression that you're misplacing the problem (not just in this thread). It's not possible to start solving a problem without defining it well, thus I'm asking you a question. To rephrase, what exactly is it that keeps you from building on top of an Ubuntu LTS release?

---

### Post by Erunno on 2007-09-23
I'm curious how the Ubuntu maintainers will handle the Firefox 1.5 situation since support has been discontinued upstream. Are they going to keep their own separate branch and keep developing patches by themselves? From what I've read that's no small undertaking as especially browser patches are often very complex.

---

### Post by zugu on 2007-09-23
It's not that I can't build, I can play with the official repositories all day long. And then say "yay, apt-get is awesome".

It's just that my choices are *extremely* limited. There's a whole bunch of software lying around, but quantity doesn't impress me. New software brings along fixed bugs, improved security, and most importantly, NEW FEATURES. Of all these, it's just the security issues that get fixed in Ubuntu releases.

In Windows or Mac OS X I can start with the base OS and then start to add various tools and full-featured applications. When a newer release is available, I just remove the old one and install the newer one, upgrade or run both versions concurrently. In Ubuntu I'm STUCK. That's it.

The latest stable release of OO.org is stable enough and has been thoroughly tested. Yet Ubuntu has to spend a lot in order to "integrate" it into the distribution and the users have to wait until the developers "fix things".

If Linux was a platform, the OpenOffice.org latest release would just install, in no time, straight from the official site. And not only in Ubuntu, but also in Debian, SuSE, Fedora and any distribution.

Sometimes I wonder why are they bothering to offer packages, they should just release the source code and be done with it, since not only we have developers, but also packagers, a new species of coders.

Ubuntu is incompatible with itself. Everything is incompatible with everything. There is a very very small subset of compatible packages, and those are the particular releases.

Oh and how am I misplacing things? OP was complaining (albeit in a veiled manner) about the unavailability of newer software for Dapper. I tried to explain him that things like that happen because the core design philosophy of packaging and releasing in Ubuntu is wrong. The frustration he experienced is nothing but proof that such a model can bring headaches.

---

### Post by zugu on 2007-09-23
> **Erunno said:**
> I'm curious how the Ubuntu maintainers will handle the Firefox 1.5 situation since support has been discontinued upstream. Are they going to keep their own separate branch and keep developing patches by themselves? From what I've read that's no small undertaking as especially browser patches are often very complex.

They had two choices:

1) upgrade to Firefox 2 - impossible because of the deep integration of Firefox into Ubuntu
2) maintain their own branch - a very, very difficult task, yet the only choice, considering 1).

Since I see no FF2 in Dapper, their choice is obvious. Should the development model of Ubuntu had been different, they would have had upgraded to FF2 and be done. But instead they will have to do Mozilla's work.

---

### Post by mcduck on 2007-09-23
> **zugu said:**
> It's not that I can't build, I can play with the official repositories all day long. And then say "yay, apt-get is awesome".

It's just that my choices are *extremely* limited. There's a whole bunch of software lying around, but quantity doesn't impress me. New software brings along fixed bugs, improved security, and most importantly, NEW FEATURES. Of all these, it's just the security issues that get fixed in Ubuntu releases.

In Windows or Mac OS X I can start with the base OS and then start to add various tools and full-featured applications. When a newer release is available, I just remove the old one and install the newer one, upgrade or run both versions concurrently. In Ubuntu I'm STUCK. That's it.

The latest stable release of OO.org is stable enough and has been thoroughly tested. Yet Ubuntu has to spend a lot in order to "integrate" it into the distribution and the users have to wait until the developers "fix things".

If Linux was a platform, the OpenOffice.org latest release would just install, in no time, straight from the official site. And not only in Ubuntu, but also in Debian, SuSE, Fedora and any distribution.

Sometimes I wonder why are they bothering to offer packages, they should just release the source code and be done with it, since not only we have developers, but also packagers, a new species of coders.

Ubuntu is incompatible with itself. Everything is incompatible with everything. There is a very very small subset of compatible packages, and those are the particular releases.

Oh and how am I misplacing things? OP was complaining (albeit in a veiled manner) about the unavailability of newer software for Dapper. I tried to explain him that things like that happen because the core design philosophy of packaging and releasing in Ubuntu is wrong. The frustration he experienced is nothing but proof that such a model can bring headaches.
It's not wrong, it's just not what _you_ want. That doesn't still make it 'wrong'.

Also, keep in mind that on Windows and Mac the developers are only concerned about the reliability of the OS itself and if the programs you use cause problems it's your problem, not theirs. You can install any version of any software but while doing that you are completely on your own.

On Ubuntu you get support not only the OS but also a set of applications. This is only possible if the support is limited to certain versions of the software. If this isn't what you want, you are using wrong Linux distribution. And nothing is stopping you from installing any version of any program by yourself. It's just not possible by anybody to guarantee you a stable system that way.

Also I don't get what you say about incompatibility. It's not true, all the software works. It's just that it's up to you to install what you want if you are not satisfied with what Ubuntu gives you. Demanding Ubuntu developers to provide every version of every software for every Ubuntu version, and then to give support and try to keep everything stable & bug free would be insane. Even big companies can't do that.

---

### Post by insane_alien on 2007-09-23
the types of tasks the LTS is destined for is where the computer is going o be doing the same thing day in day out for a couple of years at least. it will not require new feature because it will already be doing everything it is supposed to be doing. all it has to do is do it securely. this is the niche LTS releases were made to fill. 

this might not be the want of a home user who wants to experiment with new shiny stuff. in that case, the 6 month releases are there or if thats not bleeding edge enough, there are a few rolling releases that will keep everything up to date.

that is not to say they are better. in my forays into gentoo there were a few times where my system became unusable after a new version of a program. you can see why this would be a problem on a production machine or server?

---

### Post by 23meg on 2007-09-23
> **mcduck said:**
> It's not wrong, it's just not what _you_ want. That doesn't still make it 'wrong'.

Also, keep in mind that on Windows and Mac the developers are only concerned about the reliability of the OS itself and if the programs you use cause problems it's your problem, not theirs. You can install any version of any software but while doing that you are completely on your own.

On Ubuntu you get support not only the OS but also a set of applications. This is only possible if the support is limited to certain versions of the software. If this isn't what you want, you are using wrong Linux distribution. And nothing is stopping you from installing any version of any program by yourself. It's just not possible by anybody to guarantee you a stable system that way.

Also I don't get what you say about incompatibility. It's not true, all the software works. It's just that it's up to you to install what you want if you are not satisfied with what Ubuntu gives you. Demanding Ubuntu developers to provide every version of every software for every Ubuntu version, and then to give support and try to keep everything stable & bug free would be insane. Even big companies can't do that.

I was typing what was basically a more bloated version of this concise post when I read it, so I'll discard that now. The second paragraph is more or less the difference you're omitting, zugu.

---

### Post by stalker145 on 2007-09-23
This is absolutely spot on!! Ubuntu advertised **L**a**T**est **S**oftware (LTS) when they brought out 6.06, didn't they?



BWAAAAAHAHAHAHAAA!!!

Actually, it says [right where you download it from]("http://www.ubuntu.com/getubuntu/download") that it is Long-Term Support.

As it was mentioned before, who would want to rewrite all those dependencies just to get a couple of "up to date" programs?

Grab the debs, build it yourself. There *are* options.

---

### Post by koenn on 2007-09-23
Let's get a few things out of the way.
 > **rbalfour said:**
> .
ENTERPRISE is the GOAL!

> **rbalfour said:**
> 
2) ... Business doesn't wait.

Businesses do NOT like changes to their IT systems. The common practise for corporate desktops is to design a standard desktop and that's what everyone will use untill it's time to migrate to a new standard. There are many reasons behind this, too many to cover here, but it usually comes down to "if it works, don't change it". That's where Ubuntu's LTS fits in : It doesn't change, except if need be, eg for security fixes and serious bugs (if any). The LTS support periods match the usual hardware replacement cycles in a business - in 3 (to 4)  years, a desktop PC is written off and replaced, which is often combined with a migration to a newer OS version.  

So, it's perfectly reasonable to call such a release  "Long Term Support" - because the* software* will be supported (i.e. made available, be maintained, get fixed, ... ) for a long time (compared to the shorter support spans of other ubuntu releases). 


And for those who fear that running the same software for 3 years is more than they can stand (presumably : home users), there's a new release every 6 months. Now, if you think that 6 months is too long for your average home user, that's something else ...

---

### Post by mikewhatever on 2007-09-23
What a funny thread. Some people, I'd say a lot, are never satisfied, never will be. Give then good free software supported for 18 months, no, they want longer support. Give them LTS, no, they want newer software. Instead of saying 'thank you developers, my Ubuntu works great', people say 'I am stuck!', 'Ubuntu is incompatible with itself'. The more is done, the louder they complain. Don't think it's been mentioned here yet, but I've also seen complains of Ubuntu being too brown. Give me give me give me, a never satisfied attitude. How odd ):P.

---

### Post by Wolki on 2007-09-23
> **zugu said:**
> Having Dapper in feature freeze, just like the other versions released until now, doesn't make it a platform. A platform is something that allows me to build on top of it, both as a user and as a developer.

So if I target the dapper platform with a custom firefox extension (1.5 compatible, obviously), it's ok for an update to break my rollout?

An update (within a stable version) should never break compatibility, and never introduce new bugs. Otherwise, you couldn't upgrade on production machines without heavy testing *ever*. Not a good thing.

---

### Post by happysmileman on 2007-09-23
Would a simple option (during install and/or in settings manager) to enable backports fix this complaint?

Not sure if such an option exists, but I think it should be made more visible

---

### Post by karellen on 2007-09-23
> **mikewhatever said:**
> What a funny thread. Some people, I'd say a lot, are never satisfied, never will be. Give then good free software supported for 18 months, no, they want longer support. Give them LTS, no, they want newer software. Instead of saying 'thank you developers, my Ubuntu works great', people say 'I am stuck!', 'Ubuntu is incompatible with itself'. The more is done, the louder they complain. Don't think it's been mentioned here yet, but I've also seen complains of Ubuntu being too brown. Give me give me give me, a never satisfied attitude. How odd ):P.

+ from me. but I don't find this odd, it's just the human nature ;)

---

### Post by insane_alien on 2007-09-23
> **mikewhatever said:**
> What a funny thread. Some people, I'd say a lot, are never satisfied, never will be. Give then good free software supported for 18 months, no, they want longer support. Give them LTS, no, they want newer software. Instead of saying 'thank you developers, my Ubuntu works great', people say 'I am stuck!', 'Ubuntu is incompatible with itself'. The more is done, the louder they complain. Don't think it's been mentioned here yet, but I've also seen complains of Ubuntu being too brown. Give me give me give me, a never satisfied attitude. How odd ):P.

the statistics are skewed here. you only hear about the ones that are complaining. the people that love it are content just using the software and don't feel the need to go post. especially since this is primarily a support forum.

---

### Post by 23meg on 2007-09-23
> **zugu said:**
> They had two choices:

1) upgrade to Firefox 2 - impossible because of the deep integration of Firefox into Ubuntu
2) maintain their own branch - a very, very difficult task, yet the only choice, considering 1).

Since I see no FF2 in Dapper, their choice is obvious. Should the development model of Ubuntu had been different, they would have had upgraded to FF2 and be done. But instead they will have to do Mozilla's work.

They'll just backport fixes from 2.x for as long as is possible, and as has been said, the 1.5 to 2 transition in Firefox isn't such a huge leap, so it will probably be possible for a very long time, probably until the expiration of Dapper's support.

[https://wiki.ubuntu.com/DapperFirefoxSupport](https://wiki.ubuntu.com/DapperFirefoxSupport)
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/89704](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/89704)

---

