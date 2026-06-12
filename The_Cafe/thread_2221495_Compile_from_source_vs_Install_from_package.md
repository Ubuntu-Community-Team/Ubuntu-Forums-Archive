---
title: "Compile from source vs Install from package"
date: 2014-05-02
forum: The Cafe
---

### Post by Danny_Barbz on 2014-05-02
Do you guys prefer to compile everything from the source or just install a package?  What advantages does one option have over the other?

---

### Post by HermanAB on 2014-05-02
If the package is supported by Canonical, then there is no advantage to compile it yourself.  The binary will be exactly the same.

If the package is not supported, then the advantage to compiling it yourself is self evident...

---

### Post by 3rdalbum on 2014-05-02
If I wanted to **** around with my computer, I'd be using Linux From Scratch or Gentoo.

I don't want to just **** around, for me computing is a means to an end not an end in itself. Therefore I use Ubuntu which makes things easy, and I use prebuilt packages.

I *can* compile, but when there is a package available it's a total waste of effort to compile it myself.

---

### Post by mips on 2014-05-02
> **HermanAB said:**
> If the package is supported by Canonical, then there is no advantage to compile it yourself.  **The binary will be exactly the same**.

Technically that is incorrect. When you compile from source you can specify parameters specific to your cpu which would not be the same as using the default compile values.

---

### Post by ajgreeny on 2014-05-02
> **mips said:**
> Technically that is incorrect. When you compile from source you can specify parameters specific to your cpu which would not be the same as using the default compile values.
Yes, but is it *really* worth all the time and effort needed to do it that way?

I'm sure Arch, Gentoo and LFS are extremely good distros but I don't have the time to spend compiling all the packages plus dependencies needed for a system that I can use for just about everything that I will ever need, when I can simply click a few times in synaptic (my preferred package manager) or use a simple command ```
sudo apt-get install packagename
```

Sorry; for me there is no real contest.

---

### Post by monkeybrain20122 on 2014-05-02
> **HermanAB said:**
> If the package is supported by Canonical, then there is no advantage to compile it yourself.  The binary will be exactly the same.

If the package is not supported, then the advantage to compiling it yourself is self evident...

Not exactly. e.g k3b from the repo doesn't rip dvd because there is no libdvdread (or libdvdnav) support. vlc from repo doesn't play certain files because the canonical build is compiled against libav, whereas these formats will play if you compile against real ffmpeg. For 13.10 Ubuntu's official support is up to version 2.08, but even ppa builds for 2.12 do not have vdpau enabled because the system libraries are too old to support that, you can get this feature if you compile it yourself against an up to date ffmpeg.

Edited: Oh and if you use audacity in 14.04 you pretty much have to compile if you want support for common non free formats because the Ubuntu build has ffmpeg disabled.

---

### Post by monkeybrain20122 on 2014-05-02
> **ajgreeny said:**
> Yes, but is it *really* worth all the time and effort needed to do it that way?



Well, depends. I of course don't compile everything, but for a few packages I prefer to compile myself, e.g octave, vlc and mplayer. These are pretty straight forward to compile, especially vlc, doesn't really take a lot of time and effort (for mplayer there is e.g andrew.46's guide on this forum)

Edited: Also repo versions tend to be out of date. If you run LTS for more than a year pretty much everything is old, and I don't care whether Canonical 'supports it" (and what do I need canonical support for something like vlc?). I would either find a ppa or compile to get up to date. Yeah ppa is a great feature that makes a lot of compiling unnecessary with a big thanks to the maintainers.

---

### Post by su:bhatta on 2014-05-02
If there is a package available, then I have never compiled. 

Only ever compiled the one application that I had to compile. 
Never have forgotten the name 'steeldriver' for his help in that regards ! Now a Mod , huh !

And, from that experience, i keep away from compiling, if there is a way :)

But it's good to know how to compile, the extra bit is knowledge and understanding how Linux world operates.

---

### Post by linuxyogi on 2014-05-02
I dont compile if there's a package available. I dont trust PPAs unless they are maintained by the app devs themselves. I strongly feel that the vlc people should maintain a PPA for at least the LTS versions offering the latest.

---

### Post by monkeybrain20122 on 2014-05-02
> **linuxyogi said:**
> I dont compile if there's a package available. I dont trust PPAs unless they are maintained by the app devs themselves. I strongly feel that the vlc people should maintain a PPA for at least the LTS versions offering the latest.

Videolan has two ppas. One is the stable build which only offers the version that is the same as whatever you get in the repo (not sure what the point is, maybe you get some minor bug fixes), I remember at one point the current version at the time (2.1.0?) was available for 13.10 in the vlc stable ppa, but they soon removed it and replaced it with 2.0.8, which is the repo version. It also has a nightly or daily build ppa which provides the beta which is often buggy and broken. So to get up to date build you either have to compile yourself or use a third party ppa. 

As to not trusting ppa, I don't really have a problem. There are  widely used ones which offer up to date packages and a lot of flexibilities even though they are not maintained by the devs., like webupd8 and a few ppas maintained by mc4man who is a forum moderator here. PPA is one of the most attractive features of Ubuntu.Otherwise I would equally well use Debian.

---

### Post by philinux on 2014-05-03
No brainer. Never had to compile anything for ubuntu.

When I was a programmer writing bespoke high level cobol then obviously you had to compile it.

---

### Post by SeijiSensei on 2014-05-03
Almost the only time I compile anything these days is if I want to use features in a new version of the software not available in the repository version. Most of the time this applies to servers. For instance, I compiled version 3.3 of Squid with [SSLBump]("http://wiki.squid-cache.org/Features/SslBump") on CentOS since the repos only had 3.1.  On desktop computers, I nearly always use the repo versions.  I have compiled ffmpeg and mplayer from source on occasion, especially after the mplayer/mplayer2 and ffmpeg/libav forks.

---

### Post by Sir_Ismicoo on 2014-05-03
I used to compile from source a lot back in my Slackware days. If you have older hardware, by which I mean very old, then compiling software on your computer can give a reasonable speed boost. The down side to compiling on very old hardware is how long it takes.

These days I simply use the distribution's package manager to install the binaries as I don't find the cost / reward ratio good enough to do anything else. And to be frank, I no longer have the patience to wait for the compiles; even on an 8 core beast of a laptop.

---

### Post by oldos2er on 2014-05-04
> **Danny_Barbz said:**
> Do you guys prefer to compile everything from the source or just install a package?  What advantages does one option have over the other?

As has been pointed out, the package manager offers updates and upgrades that are far easier to implement than compiling.

I've done a fair bit of compiling just for my own edification mainly,  but there have been a very few apps I compiled because either the version available in the repositories was too old, or it didn't exist. I compiled ffmpeg using [FakeOutdoorsman's excellent guide]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu") which is very easy to follow; if you can copy and paste you can do it.

---

### Post by DuckHook on 2014-05-04
I've compiled Gentoo and Arch, which was an indulgence motivated by curiosity and a desire for self-education. I've also had to compile video drivers for bleeding-edge video cards that behaved badly when using the older drivers bundled with the then current distro. But aside from these two reasons, I haven't found the need or motivation to compile anything else.

On a related note, I strongly advise against compiling for new users. Although many wish to jump into doing such things in the initial rush of enthusiasm, the lack of support and the sheer technical hurdles make it a frustrating and demoralizing exercise. Unless you are stuck with an odd piece of HW that fortuitously comes with Linux source (a rare confluence of circumstances), then I recommend that new users stick to the tested binaries in the repositories (or get compliant HW).

---

### Post by monkeybrain20122 on 2014-05-04
Well I just found out that vlc in the 14.04 repo STILL has vdpau disabled. Haven't checked the ppas but if you need this feature you probably have to compile. I hate crippled applications, whether Canonical or Debian 'supports' them is of no interest to me.

---

### Post by LastDino on 2014-05-05
I would if I could, but probably for only something that I really really need. Generally I stick with what Synaptic can give me, which is more than often, more than enough for my miserly desktop.

---

### Post by EnglishElectricAndy on 2014-05-05
A similar topic was discussed some time ago on one of the Linux Reddits. Might have been /r/linux4noobs.

From memory, the general consensus was to stick with packages, even from those contributors who were experienced Linux sysadmins.

This phrase cropped up a few times: "Dependency Hell".

---

### Post by SeijiSensei on 2014-05-05
Dependencies can be an annoying problem if you compile.  The command "sudo apt-get build-dep package_name" can help a lot with this.  When building mplayer, I found that command would generally install all the required -dev packages I needed.  But sometimes you just have to study the complaints during ./configure and keep adding packages until configure is happy.

---

### Post by gerowen on 2014-05-05
I prefer to install a package.  I enjoy all the Linux-y goodness and having the freedom to get technical if I have to, but I use my computer to get work done, and in the old days it was frustrating to try and install some software only to have them give you source code instead of a package, because you knew the next 3 hours of your life was going to be spent looking up and installing dependencies.  It also makes it easier to uninstall software.  You don't have to keep a copy of the source around so you can "make uninstall".  I think that is part of what makes Ubuntu so popular.  They built on the ease of the .deb package but included more up to date software versions than Debian stable so 3rd party software vendors had something up to date to build on, and end users don't have to spend all their time compiling every time there's a software update.

---

### Post by SantaFe on 2014-05-05
I stick with Synaptic Package Manager for most everything except Firefox.  That I compile myself. ;)

---

### Post by monkeybrain20122 on 2014-05-06
> **SantaFe said:**
> I stick with Synaptic Package Manager for most everything except Firefox.  That I compile myself. ;)

May I ask why?

---

### Post by buzzingrobot on 2014-05-06
> **Sir_Ismicoo said:**
> I used to compile from source a lot back in my Slackware days. If you have older hardware, by which I mean very old, then compiling software on your computer can give a reasonable speed boost. The down side to compiling on very old hardware is how long it takes.



I'm late to this, but I had similar experience with Slackware years ago. Hardware was considerably less capable.  Often, you needed to build locally, with everything tweaked to coax the last bit of speed out of your CPU, before something would work acceptably. The performance difference could be quite obvious.  Today, though, that kind of fine tuning is much less useful and the results much less obvious.  

Remember, too, that code running on desktops, from the viewpoint of the code, spends most of its time idly waiting for the human to do something. You could work hard to optimize your code so it is faster at sitting there waiting on you.

When you build from source you also take on responsibility for future bug fixes and updates, and integrating your binaries into the system you are using:  Making sure it isn't replaced by updates, making sure it doesn't break something else, etc.

---

### Post by SantaFe on 2014-05-06
> **monkeybrain20122 said:**
> May I ask why?
You may! :D



Okay,  I'm lazy.  I know how to do Firefox, and I can disable things like webspeech, which I don't need or use.  I figure, let others do the compiling & I'll do the using. ;)

---

