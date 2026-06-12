---
title: "How can Ubuntu pretend to be stable as based on Debian Testing or Sid?"
date: 2010-03-04
forum: The Cafe
---

### Post by tamiii on 2010-03-04
Hi there,

I've been looking at ubuntu and debian for quite a while now and I figured out ubuntu 9.10 was based on debian Sid (which is the most unstable version of debian) while the next ubuntu 10.4 will be based on debian Testing (which is between debian stable and sid in terms of stability).

Just a simple question: how the ubuntu developers do to make a stable release based on a buggy debian while debian developers take much more time to release a very stable release?

---

### Post by mastablasta on 2010-03-04
Fix the base so it's less buggy and build on that?!

---

### Post by snowpine on 2010-03-04
There's no question Debian Stable is more stable than Ubuntu. :) However, most desktop users do not want old applications like Firefox 3.0, Openoffice 2.4, etc. Therefore Ubuntu is very popular in this niche. Ubuntu's 6-month cycle is a good compromise between up-to-date features and stability.

---

### Post by wojox on 2010-03-04
I think Ubuntu has a few ex Debian developers including Mr. Shuttleworth himself.

---

### Post by tamiii on 2010-03-04
So actually if I want the most stable version of ubuntu right now I should go for the 8.04 LTS and upgrade to the 10.04 at the end of this summer?

---

### Post by J_Stanton on 2010-03-04
> **tamiii said:**
> So actually if I want the most stable version of ubuntu right now I should go for the 8.04 LTS and upgrade to the 10.04 at the end of this summer? i would wait until 10.04 comes out and do a clean install.  yes, the devs take unstable and work on it to make it relatively stable by release. but a few months after release, by doing updates immediately, you have a pretty rock solid system.

---

### Post by Tamlynmac on 2010-03-04
> J_Stanton
would wait until 10.04 comes out and do a clean install. yes, the devs take unstable and work on it to make it relatively stable by release. but a few months after release, by doing updates immediately, you have a pretty rock solid system.

May I also suggest testing prior to installation. Which would assure system compatibility and functionality prior to installing on one's primary HDD. 

I do agree with J_Stanton, that a fresh install is the preferred installation procedure. Only difference is I'd test before committing. Just my $0.02

* The above response is only my opinion and not meant for debate.

---

### Post by Sef on 2010-03-04
Moved to Community Cafe.

---

### Post by Tibuda on 2010-03-04
Also this "stable" is not the opposite of "buggy", but the opposite of "rolling release".

---

### Post by Twitch6000 on 2010-03-04
> **J_Stanton said:**
> i would wait until 10.04 comes out and do a clean install.  yes, the devs take unstable and work on it to make it relatively stable by release. but a few months after release, by doing updates immediately, you have a pretty rock solid system.

Not any longer they are going to use testing this time.

---

### Post by NightwishFan on 2010-03-04
Debian is such an excellent project. I tend to use Ubuntu simply because everything is packaged so much simpler for it. (Such as Nvidia drivers + rt/lowlatency kernel).

As for Sid, if you use it full time you realize there aren't many on the surface problems. Testing is generally more up to date than the latest Ubuntu. (It always is for me)

---

### Post by snowpine on 2010-03-04
There is a misconception about Debian Unstable/Sid that it contains only buggy beta software. That just isn't true. All of the packages/applications are the stable, upstream versions. The reason they're in Unstable is that they haven't been thoroughly tested yet *by the Debian team in the context of the Debian distro*.

For example Debian Sid has Iceweasel (Firefox) 3.5.8, not some wild & crazy beta version.

---

### Post by Zoot7 on 2010-03-04
TBH I find even Debian Sid is more "stable" than Ubuntu. 

There's the odd wave of breakage every now and again but I never had anything I couldn't fix or anything to the degree of breakage I got when upgrading to the last two releases of Ubuntu.

---

### Post by snowpine on 2010-03-04
I agree with Zoot7 and in fact use sidux (based on Debian Sid) as the main OS on one of my computers. No problems whatsoever. It replaced Karmic Koala, which I did not find to be an enjoyable experience.

---

### Post by Zoot7 on 2010-03-04
> **snowpine said:**
> It replaced Karmic Koala, which I did not find to be an enjoyable experience.
I went back to my old strategy of using Testing and building the packages from the Sid repo from source once again.

Karmic was by no means pleasent for me either, nor was Jaunty. 
I had to compile Alsa from source to get working sound in Jaunty and pull down the source for a good portion of the Gnome desktop from the Debian Sid repos and recompile it myself to get the functionality back after removing that parasitic app Pulseaudio in Karmic. 
I realize that my experience is somewhat unique to me, and not necessarily common to *everyone* else, but honestly should I have to do this on a so-called "Noob Friendly" distro?

---

### Post by Xbehave on 2010-03-04
Check he post history guys obvious troll is obvious.

Tamiii if you have ubuntu so much don't use it, nobody is forcing you to. I quite like the balance of currentness and stability it has.

---

### Post by Tibuda on 2010-03-04
Just come to mind: Debian stable is also based on Debian testing.

---

### Post by snowpine on 2010-03-04
> **danielrmt said:**
> Just come to mind: Debian stable is also based on Debian testing.

Whoa, heavy maaan!

---

### Post by 23meg on 2010-03-04
> **tamiii said:**
> 
Just a simple question: how the ubuntu developers do to make a stable release based on a buggy debian while debian developers take much more time to release a very stable release?

Here's how:

[http://mdzlog.alcor.net/2009/03/08/ubuntu-is-based-on-debian-unstable/](http://mdzlog.alcor.net/2009/03/08/ubuntu-is-based-on-debian-unstable/)

---

### Post by Zoot7 on 2010-03-04
> **danielrmt said:**
> Just come to mind: Debian stable is also based on Debian testing.
Haha, touche. ;)

---

### Post by saulgoode on 2010-03-04
> **danielrmt said:**
> Just come to mind: Debian stable is also based on Debian testing.
True. But Debian testing typically goes through about 12 months of development before feature freeze, followed by another six months of integration testing afterward, before being released as stable.

---

### Post by XubuRoxMySox on 2010-03-05
Y'know, it's kinda like a seesaw (teeter-totter). You put the fulcrum wherever it works for whoever is using it.

My biggest complaint with Ubuntu is its claim to be "beginner friendly" while still including Beta software - turning Linux newbies into laboratory rats without their knowledge and consent. I think beginners need stability more than the latest stuff (so move the fulcrum to favor stability for those users). After they've gained some experience and are ready (and willing) to take some risk and explore, let them do it with eyes open and informed choice. 

-Robin

---

### Post by uRock on 2010-03-05
> **tamiii said:**
> Hi there,

I've been looking at ubuntu and debian for quite a while now and I figured out ubuntu 9.10 was based on debian Sid (which is the most unstable version of debian) while the next ubuntu 10.**0**4 will be based on debian Testing (which is between debian stable and sid in terms of stability).

Just a simple question: how the ubuntu developers do to make a stable release based on a buggy debian while debian developers take much more time to release a very stable release?

Easy, they made it stable, added whipped cream, then released it.

---

### Post by uRock on 2010-03-05
> **dixiedancer said:**
> turning Linux newbies into laboratory rats without their knowledge and consent. 

What!? We/they consent when they install Ubuntu. Is your case not true for mostly everyone using a 64bit processor? I guess PC makers shouldn't be selling 64bit processors until there is a stable non-beta version of Adobe Flash?

I guess you could throw that accusation at Windows for allowing people to install Windows 7 being that it has so many problems, it must still be considered beta, right?

---

### Post by XubuRoxMySox on 2010-03-05
LOL, no, that's not quite what I'm saying. I'm just say'n that it's scary *enough* for newbies to try out a whole 'nother OS without including unproven software that gives *even experienced Linux users* fits when it doesn't play nice on their 'puter. The stuff is great when it works! But I think it's a mistake to put it in a distro aimed at newbies until it is proven, patched, or at least has a work-around that newbies can handle, that's all.

-Robin

---

### Post by markbuntu on 2010-03-06
Ubuntu 8.04 is extremely stable now but that took about 6 months. I would not expect Lucid to do any better than 8.04 so if you want a stable Ubuntu you need to wait a few months on the LTS releases and maybe skip the ones in between. I had a really bad time with Intrepid, Jaunty was better and Karmic so-so. I still use Hardy as my main install and all those others will go bye bye when I move to lucid in about 6 months.

Ooooo....I just got updated to the new lucid wallpaper on my other machine, very nice.

---

### Post by woodmaster on 2010-03-06
as a n00b not too long ago, I found Karmic relatively n00b friendly.  My issues were: X crashes, pulseaudio causing crashes, printer driver hard to find.  I did my research coming in and knew there may be problems putting Linux on a computer built for Windows.  I sucked it up and worked through them and it's now running like a well oiled machine.  Not even considering upgrading to Lucid as yet, they have nothing that I see to attract me to it.

---

### Post by uRock on 2010-03-06
I am testing Lucid on my Netbook and it looks and runs great. I plan to upgrade all of my machines to it when it goes to Beta testing. I have nothing against Debian, but I would never recommend Deb to a newcomer. Ubuntu does mostly everything for the new person.

---

### Post by angryfirelord on 2010-03-09
> **tamiii said:**
> Hi there,

I've been looking at ubuntu and debian for quite a while now and I figured out ubuntu 9.10 was based on debian Sid (which is the most unstable version of debian) while the next ubuntu 10.4 will be based on debian Testing (which is between debian stable and sid in terms of stability).

Just a simple question: how the ubuntu developers do to make a stable release based on a buggy debian while debian developers take much more time to release a very stable release?
I wouldn't call Debian Sid "buggy". Sid is a rapidly moving base of software, but it includes the latest released software. Alpha and beta software usually end up in the experimental branch. For instance, Sid doesn't even have the latest KDE because they don't want all of the overhang with the new bugs.

---

