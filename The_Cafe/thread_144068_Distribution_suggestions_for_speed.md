---
title: "Distribution suggestions for speed?"
date: 2006-03-13
forum: The Cafe
---

### Post by tristure on 2006-03-13
Hi,

I use Kubuntu Breezy as my main OS, and I'm very satisfied with it. Nonetheless I do regret its relative slowness. It's not quite as fast as it should be.

So I'm currently trying out new distributions, to see if I can get KDE and more speed at the same time.

I have tried :
-Arch : good and fast, but no split KDE packages, and lacks modules for some of my hardware (I don't wan't to recompile my kernel... I've done that with Gentoo and had nothing but problems)

-Vector : REALLY fast, but no HAL, no split KDE packages, and arguable stability.

-Suse : not fast. Outdated KDE build. Still testing it because many people praise Suse when it comes to KDE...


Do you have any other suggestions of good distributions I might try for a fast and reliable KDE system? Right now the challenger is Vector, but I can't decide to use it for primary desktop yet...

Thanks for your suggestions.

---

### Post by aysiu on 2006-03-13
You could try other distros.

Or...

you could just keep Kubuntu and do this:

KMenu > System > Konsole

```
sudo apt-get update
sudo apt-get install kpersonalizer
kpersonalizer
``` Select under "effects" to use "fewer effects" (basically everything unchecked except desktop wallpaper and image previews).

If that doesn't do it for you, I'd recommend PCLinuxOS.

---

### Post by ssam on 2006-03-13
there are quite a few speed fixes in dapper.

---

### Post by LinuxSwede2 on 2006-03-13
DSM or vector.

I'm an old Slackhead so you can guess what i like best, Debianfreaks will prefer the other.

;)

---

### Post by LinuxSwede2 on 2006-03-13
[QUOTE=tristure]Hi,

I use Kubuntu Breezy as my main OS, and I'm very satisfied with it. Nonetheless I do regret its relative slowness. It's not quite as fast as it should be.

So I'm currently trying out new distributions, to see if I can get KDE and more speed at the same time.

I have tried :
-Arch : good and fast, but no split KDE packages, and lacks modules for some of my hardware (I don't wan't to recompile my kernel... I've done that with Gentoo and had nothing but problems)

-Vector : REALLY fast, but no HAL, no split KDE packages, and arguable stability.

-Suse : not fast. Outdated KDE build. Still testing it because many people praise Suse when it comes to KDE...


Do you have any other suggestions of good distributions I might try for a fast and reliable KDE system? Right now the challenger is Vector, but I can't decide to use it for primary desktop yet...

Thanks for your suggestions.[/QUOTE]

If you are up for it, a FreeBSD install with KDE flies in comparison and you get the same updated system. It's a tad difference but the documentation is... Well if Ubuntu documentation is great, which it is, then i don't know what to call FreeBSD documentation... Complete perhaps.

I hear good things about DragonflyBSD and other flavors too but i'm not accustomed to them enough to make any other recommendations except that PC-BSD is the BSD version of Linspire.

---

### Post by John.Michael.Kane on 2006-03-13
tristure Not that i would want you give up on ubuntu. here is a list of small distros. hope they offer the speed you seek.
[http://distrowatch.com/](http://distrowatch.com/)
[http://cyti.latgola.lv/ruuni/index_en.html](http://cyti.latgola.lv/ruuni/index_en.html)
[http://www.vectorlinux.com/](http://www.vectorlinux.com/)
[http://www.vectorlinux.com/](http://www.vectorlinux.com/)
[http://www.stibs.cc/stx/](http://www.stibs.cc/stx/)
[http://www.puppylinux.org/](http://www.puppylinux.org/)
[http://featherlinux.berlios.de/](http://featherlinux.berlios.de/)
[http://www.delilinux.de/](http://www.delilinux.de/)
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

Side note you can give this a try [https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28lowmem%29](https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28lowmem%29)

---

### Post by Lovechild on 2006-03-13
I'll go with another option: Fedora Core 5, it just feels faster - I know there's an overhead for various security features but it just feels so smooth it's incredible.

---

### Post by LinuxSwede2 on 2006-03-13
[QUOTE=Lovechild]I'll go with another option: Fedora Core 5, it just feels faster - I know there's an overhead for various security features but it just feels so smooth it's incredible.[/QUOTE]

So it's nice? How about stability? I've been thinking about trying it out and if it's your opinion that it's worthwhile i'll try it out.

---

### Post by Lord Illidan on 2006-03-13
I am using Fedora Core 5 test 3 atm. It doesn't feel that fast to me. It looks nicer than Ubuntu out of the box, though, with nicer fonts, yes. But I miss apt.

What about Zenwalk Linux?

---

### Post by Bandit on 2006-03-13
Breezy with the updates seems to be one of the better KDE releases out. KDE 3.5.1 seemed faster then most I have tried. But over all KDE is little slower due to all its features. If you want a faster DE then try Gnome. Gnome on breezy is much faster then KDE. At least it has always been with me.
But if thats not fast enough then try Windowmaker, XFCE or Blackbox.
Cheers,
Joey

---

### Post by basketcase on 2006-03-13
Damn small linux
Vector Linux seemed pretty quick to me when I played with it.

---

### Post by Joeb on 2006-03-13
You could also turn on  DMA transfers (using hdparm) for your hard drive and enable prelinking.  Either one or both will give you a pretty good speed improvement.  Search the forums for details.

---

### Post by woedend on 2006-03-13
i haven't played with FC5 too much, but FC4 was the slowest distro i've ever used.  The fastest i've ever used is straight debian.  Might I suggest debian sid?  A little buggy, but it really is fast.  Ubuntu for me has always been very fast as well.

---

### Post by ComplexNumber on 2006-03-13
> but FC4 was the slowest distro i've ever used you obviously haven't used suse :D. i'm using fedora and suse, and fedora is _way faster_ than suse for almost every single operation (booting up, loading the DE, opening applications, etc). from my expereince, suse is the slowest of them all. the fastest is one like vector that can be custom built for speed, has few daemons running, and blackbox as a window manager.

---

### Post by Jucato on 2006-03-13
Umm... forgiving me for being a newb.

1. what do you mean by split KDE packages?
2. does/will FC 5 have a live CD/live CD installer? I'm presuming FC uses KDE? does FC 5 have a 1 CD install option? (I'm not keen on downloading multiple CDs)
3. Same 3 questions for SuSE (openSuSE or SuSE eval)

I'm also kinda window shopping for good KDE distros. :D

@tristure: have you tried SimplyMEPIS? I find that it has a better looking default KDE than Kubuntu (please don't flame me :D)

---

### Post by ComplexNumber on 2006-03-13
[quote=Fenyx]Umm... forgiving me for being a newb.

1. what do you mean by split KDE packages?
2. does/will FC 5 have a live CD/live CD installer? I'm presuming FC uses KDE? does FC 5 have a 1 CD install option? (I'm not keen on downloading multiple CDs)
3. Same 3 questions for SuSE (openSuSE or SuSE eval)

I'm also kinda window shopping for good KDE distros. :D

@tristure: have you tried SimplyMEPIS? I find that it has a better looking default KDE than Kubuntu (please don't flame me :D)[/quote] 
1) split KDE packs - in fedora (a non kde friendly distro), the multimedia, graphics, network packages aren't split. in kde friendly distros such as suse, the multimedia is split into multimedia-kscd, multimedia-juk, etc. same for the grahics and the network 'conglomerates'.

2) i don't know. FC does have kde, but its nothing more than a begrudging token gesture to the kde folk. its as crippled on fedora as gnome on suse used to be...and thats A LOT. fedora are working on having a core section that fits on 1 cd, then having the extras on the other 4 or 5 cd's.

3) ditto

---

### Post by rado_london on 2006-03-13
Why not Slackware 10.2? I like the speed but it is so annoying to be configured so its up to you.

---

### Post by John.Michael.Kane on 2006-03-13
rado_london some of the distro's I listed are slackware based..

---

### Post by fuscia on 2006-03-13
you can compile fluxbox to enable kde. then, start fluxbox and, in fluxbox, start kicker and kdesktop. it runs faster than full blown kde. if i'm not mistaken, fluxbox provides full support for kde. even if it doesn't, you could always switch over for kde for the few things you would need to do.

---

### Post by rado_london on 2006-03-20
[QUOTE=SD-Plissken]rado_london some of the distro's I listed are slackware based..[/QUOTE]

Sorry mate I didnt see your post.

---

### Post by s|k on 2006-03-20
Slackware?

---

### Post by benplaut on 2006-03-20
Dapper server install w/ a nice lightweight window manager

---

### Post by Kurt` on 2006-03-20
I'm glad nobody has suggested Gentoo yet :cool: 

Slackware had a smaller footprint and ran faster than a Stage 1 Gentoo install... :-|

---

