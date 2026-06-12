---
title: "Ubuntu 9.04: Streamlined Release"
date: 2008-06-29
forum: Ubuntu Brainstorm
---

### Post by Redrazor39 on 2008-06-29
The development of Ubuntu 9.04 or whatever version comes after Intrepid Ibex should focus on streamlining and putting together Ubuntu as a whole. Redundancies should be removed and Ubuntu should be slimmed down. This would make Ubuntu faster and smaller.

I'm not saying remove GNOME or anything or even to just fix the UI, I'm saying dig deep into Ubuntu's code that's between the Linux kernel and the Desktop Environment and streamline that into one cohesive whole that is small, fast, efficient, and stable.

Instead of focusing on adding new features, just update the current software (current as of the release of Intrepid Ibex) and streamline it. This way, it won't be another Hardy full of incomplete betas and pre-releases. 9.04 should focus on stability, speed, and being small and fast. Look at what Apple is doing with Snow Leopard. They added the features in Leopard and now they're streamlining them in Snow Leopard. I'm not saying copy Apple by any means. I'm saying they've got a good idea and we can do it to, and take it two steps further. That's what we should be doing. Having our own ideas as well as taking the ideas of other companies two or three steps forward for ourselves.

2009.04.??
Ubuntu 9.04: Streamlined Release.

---

### Post by smartboyathome on 2008-06-29
You would have to talk to the individual projects for this. That is the only way it would happen. :(

---

### Post by Redrazor39 on 2008-06-29
yea, or we would have to settle for canonical or the ubuntu devs streamlining what they've got themselves. It's kinda like how ubuntu is 699MB and xubuntu is 544MB. That's a difference between desktop environments, but what about the stuff in between the kernel and the DE? The stuff that makes Ubuntu, Ubuntu.

---

### Post by smartboyathome on 2008-06-29
There isn't much between the kernel and the DE. It wouldn't have any noticable effect. Also, Hardy WAS to make the image smaller by taking out repetitive programs.

---

### Post by Redrazor39 on 2008-06-29
Oh, I see. Well, what hardy was supposed to do didn't really work.

Anyway, I'm no developer, but what I am saying is to set the focus for Ubuntu devs to streamline Ubuntu together for the 9.04 release.

---

### Post by Shin_Gouki2501 on 2008-06-30
something like this?
[http://www.golem.de/0806/60714.html](http://www.golem.de/0806/60714.html)
or for our english fellows:
[http://translate.google.de/translate?u=http%3A%2F%2Fwww.golem.de%2F0806%2F60714.html&sl=de&tl=en&hl=de&ie=UTF-8](http://translate.google.de/translate?u=http%3A%2F%2Fwww.golem.de%2F0806%2F60714.html&sl=de&tl=en&hl=de&ie=UTF-8)
:)

---

### Post by Redrazor39 on 2008-07-01
I think so! Basically I'm saying combine all the default parts of ubuntu into one, single, streamlined package and make it as small as possible (NO redundancies, except for recovery) and require developers to build their software well into the system, while still allowing it to be removed and restoring ubuntu to the condition before installing that software, but keeping everything else.

It would be hard, but it would be great!

---

### Post by bruce89 on 2008-07-01
> **Redrazor39 said:**
> I think so! Basically I'm saying combine all the default parts of ubuntu into one, single, streamlined package and make it as small as possible (NO redundancies, except for recovery) and require developers to build their software well into the system, while still allowing it to be removed and restoring ubuntu to the condition before installing that software, but keeping everything else.

I don't think people realise, but developers write their programs not aiming at any distribution, all they care is that their source compiles and works.

---

### Post by nhandler on 2008-07-01
This is a nice idea, but it would be very difficult to accomplish. The applications included with Ubuntu for the most part were not created by Canonical or the Ubuntu devs. They were made by third party developers. These packages then got added in Debian, and we then synced/merged the package into the Ubuntu repositories. The only changes that we make to the packages are minor changes to enable it to run well on Ubuntu. We try to leave the major code changes to the upstream developer.

So if we want to slim down Ubuntu, we would have to convince all of the upstream developers to slim down their applications. This would involve large changes to the code, and would likely create lots of new bugs.

As a result, I highly doubt that Ubuntu will be able to be slimmed down too much.

---

### Post by Redrazor39 on 2008-07-02
:(

Oh, well. I was hoping that Ubuntu could be more like BSD in this respect and have a release that slims it down and puts it all together into one interlocked piece. Maybe this could happen slowly over multiple releases?

---

### Post by madjr on 2008-07-02
for 8.10

they are planning to get it to boot faster and be more memory efficient (and probably further slim it down a bit).

This happened after they showcased ubuntu netbook remix.

now they want to add many of that efficiency to regular ubuntu. :)

i think they will do good

---

### Post by Redrazor39 on 2008-07-02
Hooray! This is what I wanted! I love efficiency! :)

---

### Post by madjr on 2008-07-03
> **Redrazor39 said:**
> Hooray! This is what I wanted! I love efficiency! :)

they will do what they can in the small time frame along with a million other stuff...

so, just don't expect miracles :lolflag:

---

### Post by teishu on 2008-07-04
I totally agree that the next release should be focused on efficenty...:)

---

### Post by nitePhyyre on 2008-07-15
> **Cheater said:**
> We try to leave the major code changes to the upstream developer.

And you run a company with this mentality?  Sometimes I am amazed that linux even runs. It seems that all anyone ever does with this OS is pass the buck. lol

---

### Post by smartboyathome on 2008-07-15
> **nitePhyyre said:**
> And you run a company with this mentality?  Sometimes I am amazed that linux even runs. It seems that all anyone ever does with this OS is pass the buck. lol

You just don't get Linux, then. Ubuntu is just a "distrobution" (aka distro) of programs compiled on top of the Linux kernel. They don't fix anything themselves usually, but have upstream fix it due to them knowing the code better.

---

### Post by mc4100 on 2008-07-16
> **Redrazor39 said:**
> Hooray! This is what I wanted! I love efficiency! :)
It would be nice if their was some sort of "efficiency" release but, for now, you can do it yourself:
There's loads of guides on disabling unwanted services (like printing if you don't own a printer, etc.,), enabling concurrent booting, preloading libraries into memory and tuning your filesystem, there's even packages like "debfoster" for removing unwanted stuff to free space. (You want to take your time though, and really know what you're doing, because you might end up breaking things. Always look at the comments before you do anything, in-case people have noted errors or breakages)

---

### Post by hayre on 2008-09-08
As just a quick look around ubuntu with GOOGLE you will see many, many people with the same problems with hardy that I have had.  I want the fancy eye candy with which my NVIDIA card is capable, but I can't get it to work (two monitors).  After more than a week at struggling reading other posts, rewriting xorg.conf about 30 times I got it to work - for a while.  

I wanted monodevelop which needs lots and lots of other packages.  When I was installing them my Xwindows froze.  When I rebooted I got a little cirlce thingy which never stops.  I decided to just reinstall hardy.  After all - I had (finally) a working xorg.conf file!  Well, after the re-install, that won't work and I've begun rewriting it over and over.  This is too hard!  I may or may not have shot myself in the foot over the mono stuff, but I should be able to at least get back to a stable system running two monitors!  

So for my 2 cents, I would like to suggest much easier implementation of the NVIDIA stuff.

Thanx for reading.  Sorry it was so long to say so little.  (Bit frustrated around here).

Johnny

---

### Post by smartboyathome on 2008-09-09
1) NVIDIA is proprietary, so unless they release the source, it will be hard to do anything with the drivers. Its sad, but true. I see ATI as being superior on Linux in the future since it does have open source drivers, but until the open source drivers are up to spec with the proprietary ATI driver, then I am afraid NVIDIA will still be better and proprietary. :(

2) Back up your xorg.conf before you install, but also realize multiple monitors aren't the best on Linux yet from what I have experienced.

---

### Post by lunkupe on 2008-09-10
I think we should have a media centre edition...so that u do not neccesarily have to boot the whole os to listen to music..a good example would be on the media direct that is on dell

---

### Post by Ripfox on 2008-09-10
> **lunkupe said:**
> I think we should have a media centre edition...so that u do not neccesarily have to boot the whole os to listen to music..a good example would be on the media direct that is on dell

There was a project for Ubuntu Multimedia Center but the web page died last I checked...:(

---

### Post by Ripfox on 2008-09-10
double post sorry

---

### Post by Uchiha_madara on 2008-09-10
> **madjr said:**
> for 8.10
[SIZE="2"][B][I]
they are planning to get it to boot faster and be more memory efficient (and probably further slim it down a bit).

This happened after they showcased ubuntu netbook remix.

now they want to add many of that efficiency to regular ubuntu. :)

i think they will do good[/I][/B][/SIZE]

Wow ...... Amazing .....

i hope to be more efficient with the VGA adapters, sound cards & the hardwares in General....:guitar:

---

### Post by MadsRH on 2008-09-10
> **lunkupe said:**
> I think we should have a media centre edition...so that u do not neccesarily have to boot the whole os to listen to music..a good example would be on the media direct that is on dell

[https://wiki.ubuntu.com/UbuntuMediaCenterTeam]("https://wiki.ubuntu.com/UbuntuMediaCenterTeam")
[B]
//MadsRH[/B]

---

