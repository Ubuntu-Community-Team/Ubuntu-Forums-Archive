---
title: "Adobe flash no longer supporting Linux?"
date: 2012-09-12
forum: The Cafe
---

### Post by Sonoran Desert Rat on 2012-09-12
Hello, I'm a newbie. I just went to install Adobe Flash for Chromium and got this message on the download screen:

NOTE: Adobe Flash Player 11.2 will be the last version to target Linux as a supported platform. Adobe will continue to provide security backports to Flash Player 11.2 for Linux.

Is there a thread about this somewhere? I tried searching and can't find one.

---

### Post by wojox on 2012-09-12
> **Sonoran Desert Rat said:**
> 

Is there a thread about this somewhere? I tried searching and can't find one.

Oh yes here you go [Adobe Abandons Flash on Linux]("http://ubuntuforums.org/showthread.php?t=1929659")

---

### Post by heminder on 2012-09-12
Meh. Flash is obsolete, with HTML5 supposed to be taking over. Assuming that Google doesn't try to do some shady do-hickery.

---

### Post by eylisian on 2012-09-12
The way Flash videos peg my CPU I'll be a happier person when it finally is replaced.

---

### Post by vexorian on 2012-09-12
We are **trying** to deprecate it.

As long as flash can't run in iOS and google has a grab over it through pepper, I am gonna say that we have to battle google's power if we want flash to be *really* deprecated.

---

### Post by Sonoran Desert Rat on 2012-09-12
> **wojox said:**
> Oh yes here you go [Adobe Abandons Flash on Linux]("http://ubuntuforums.org/showthread.php?t=1929659")

Thank you. :)

I read that a program called totem works. Is it, or something else, a good substitute?

edit: after reading that thread I'm installing firefox.

---

### Post by cariboo on 2012-09-12
> **Sonoran Desert Rat said:**
> Thank you. :)

I read that a program called totem works. Is it, or something else, a good substitute?

edit: after reading that thread I'm installing firefox.

Flash is still available through the flashplugin-installer available in the repositories, why try to install it by hand?

As a new user, I'd suggest you install the ubuntu-restricted-extras meta-package from the repositories, that stops you from having to search for installable codecs.

---

### Post by Sonoran Desert Rat on 2012-09-12
I'm taking your advice. :)

---

### Post by krishna.988 on 2012-09-13
> **Sonoran Desert Rat said:**
> I'm taking your advice. :)

Flash is stopped for Linux, as Flash is getting integrated to IE 10 in Windows 8.. and they did'nt want to support non-windows platform except Mac...

---

### Post by tienlbhoc on 2012-09-13
in the future, all web will change to html5, like youtube have option html5 view (google please),and now, we still install flash.
If Adobe flash no longer supporting Linux, no have any problem.

---

### Post by mr john on 2012-09-13
I don't buy that it's deprecated. Flash can still do alot of things that html can't. Also, alot of legacy sites will continue to use flash.

---

### Post by krishna.988 on 2012-09-13
> **mr john said:**
> I don't buy that it's deprecated. Flash can still do alot of things that html can't. Also, alot of legacy sites will continue to use flash.

But why no support in linux???:(

---

### Post by Starlight on 2012-09-13
I've noticed that the Pepper-based Flash on Chrome on Linux works so much better and smoother than the NPAPI-based Flash on other browsers, like Chromium on Firefox. I'm not sure why the difference is so huge, but the NPAPI-based Flash horribly lags when moving the mouse cursor. Each time I move the mouse overy some Flash thing, everything there just stops until I stop moving the mouse. o_O 

Since Firefox won't support Pepper, then maybe it would be possible to write some kind of Pepper plugin wrapper (similar to nspluginwrapper maybe?) that would make it possible to run Pepper plugins on NPAPI browsers? I don't really know how it works so it might be impossible...

---

### Post by krishna.988 on 2012-09-13
> **Starlight said:**
> I've noticed that the Pepper-based Flash on Chrome on Linux works so much better and smoother than the NPAPI-based Flash on other browsers, like Chromium on Firefox. I'm not sure why the difference is so huge, but the NPAPI-based Flash horribly lags when moving the mouse cursor. Each time I move the mouse overy some Flash thing, everything there just stops until I stop moving the mouse. o_O 

Since Firefox won't support Pepper, then maybe it would be possible to write some kind of Pepper plugin wrapper (similar to nspluginwrapper maybe?) that would make it possible to run Pepper plugins on NPAPI browsers? I don't really know how it works so it might be impossible...

I use chromium but by default it uses adobe flash plug-in. how to install the pepper flash plug-in?

---

### Post by forrestcupp on 2012-09-13
I don't really get what everyone is scared about. We have Flash 11.2, and about every important website out there that uses Flash only requires v.10 or earlier. They're not all going to change that out of spite for the Linux users just because Adobe stops supporting us. None of the big game sites, YouTube, Hulu, BBC, etc., even require v.11, and they've been that way for a very long time. With things going the html5 route, I highly doubt if they're going to finally decide after all these years to switch to a newer version of the futureless Flash.

What's everyone so worried about? It couldn't be security, because Adobe is going to keep giving us security patches to 11.2.

> **heminder said:**
> Meh. Flash is obsolete, with HTML5 supposed to be taking over. Assuming that Google doesn't try to do some shady do-hickery.Flash is not obsolete until nothing uses it anymore. As of right now, *a lot* of things still use it, and I'm not just talking about ads.

---

### Post by Jakin on 2012-09-13
As forrestcupp says; I've not run into a single site anywhere requiring me to upgrade past where i am (flash 11.2). When i was on flash 10, nothing required me to update (only reason i am on 11.2, was because when i upgraded ubuntu thats what it had, otherwise im sure i wouldn't had noticed)- so no worries, i sure never did.

As for HTML 5, i dearly want to believe in it. It has great performance on my machines WHEN IT WORKS. I had been tryin out the html5 player on youtube for months, and it has issues, i dunno if its the player, or my browser, or just plain the youtube site itself, but it crashes or something on random videos- sometimes you reload and it works, sometimes it doesn't. 
Far from ready...

---

### Post by Starlight on 2012-09-13
> **krishna.988 said:**
> I use chromium but by default it uses adobe flash plug-in. how to install the pepper flash plug-in?

I've never tried. There are some instructions online, but it seems kind of complicated. 


> **forrestcupp said:**
> I don't really get what everyone is scared about. We have Flash 11.2, and about every important website out there that uses Flash only requires v.10 or earlier. They're not all going to change that out of spite for the Linux users just because Adobe stops supporting us. None of the big game sites, YouTube, Hulu, BBC, etc., even require v.11, and they've been that way for a very long time. With things going the html5 route, I highly doubt if they're going to finally decide after all these years to switch to a newer version of the futureless Flash.

What's everyone so worried about? It couldn't be security, because Adobe is going to keep giving us security patches to 11.2.

It depends on whether these "security updates" also involve fixing bugs. On my computer, Flash on Linux seems to be horribly buggy, and games are almost unplayable because of that. If I want to play a game, I need to use Chrome with Pepper-based Flash, then everything works well. Even the Windows version of Flash on Wine works 1000 times better than normal Flash on Linux.

---

### Post by neu5eeCh on 2012-09-13
> **heminder said:**
> Meh. Flash is obsolete, with HTML5 supposed to be taking over. Assuming that Google doesn't try to do some shady do-hickery.

And yet, somehow, the future keeps showing up and still Flash dominates.  Just *which* future are you counting on?

---

### Post by Jakin on 2012-09-13
> **Starlight said:**
> On my computer, Flash on Linux seems to be horribly buggy, and games are almost unplayable because of that. If I want to play a game, I need to use Chrome with Pepper-based Flash, then everything works well. Even the Windows version of Flash on Wine works 1000 times better than normal Flash on Linux.

Im not having that issue at all. 
As for example: I had recently started using Fogger with 32bit flash workaround (on a 64bit machine with ubuntu 12.04amd64) to play SimCity Social. It works smooth in normal, as well as fullscreen. However on windows 7(64bit) with the absolute newest update of flash, the same game, and on the same machine; it plays horribly slow, unless i am fullscreen.

(i use this as example because this is one thing i have been using, that i can compare to the performance on windows; Not seeing it with anything else i use requiring flash between the two platforms)

EDIT: Its already hard to compare, but nor my ubuntu, or my windows7 has anything extra running that don't need to be (services)

---

### Post by vexorian on 2012-09-13
Flash has never given me major problems in ubuntu to be honest. As in 7 years worth of never experiencing the bugs that supposedly infest the experience.

> And yet, somehow, the future keeps showing up and still Flash dominates. Just *which* future are you counting on? Flash still "dominates", but it is hardly growing and the tendency is towards less flash stuff. The major reasons to use flash (like youtube) already have HTML5 or silverlight alternatives (or are locked in silverlight). There are many old games still running in flash, but they are old games. It seems that for newer things, developers are less likely to try flash (it would be a very bad move to spend days working on a web game that does not run in iOS)

---

### Post by Starlight on 2012-09-13
> **Jakin said:**
> Im not having that issue at all. 
As for example: I had recently started using Fogger with 32bit flash workaround (on a 64bit machine with ubuntu 12.04amd64) to play SimCity Social. It works smooth in normal, as well as fullscreen. However on windows 7(64bit) with the absolute newest update of flash, the same game, and on the same machine; it plays horribly slow, unless i am fullscreen.

(i use this as example because this is one thing i have been using, that i can compare to the performance on windows; Not seeing it with anything else i use requiring flash between the two platforms)

EDIT: Its already hard to compare, but nor my ubuntu, or my windows7 has anything extra running that don't need to be (services)

Hmm this is strange then. I always have this problem on Linux no matter which distro I use. Maybe it's something to do with my video drivers? I have a Radeon video card with the open source drivers installed (the official drivers don't like Gnome Shell, or maybe Gnome Shell doesn't like them?). This problem appears in every browser I've tried. Only Chrome with Pepper-based Flash works well and the problem doesn't appear. Even Chromium with normal, non-Pepper Flash has that problem.

---

### Post by Jakin on 2012-09-13
> **Starlight said:**
> Hmm this is strange then. I always have this problem on Linux no matter which distro I use. Maybe it's something to do with my video drivers? I have a Radeon video card with the open source drivers installed (the official drivers don't like Gnome Shell, or maybe Gnome Shell doesn't like them?). 


I definately agree with the ATI proprietary drivers not liking Gnome3 or Gnome shell, i don't know why.. 
I am using KDE 4.9 anyway, and opensource drivers... (Radeon 880g card) As for my understanding of how the flash plugin works on linux- it doesn't use hardware acceleration (maybe im wrong)? 

Could be any number of things as to why we have difference experiences...

---

### Post by forrestcupp on 2012-09-13
> **Jakin said:**
> As for my understanding of how the flash plugin works on linux- it doesn't use hardware acceleration (maybe im wrong)? 

It used to be like that, but they've added hardware acceleration in the current version. But people who have the "blue man" problem in Flash videos have to turn off acceleration to fix it.

I have an Intel GPU, and I don't have any problems with anything. I love Intel GPUs in Linux. I don't need anything more powerful because I use consoles if I want to play games.

---

### Post by krishna.988 on 2012-09-13
Why none of them are not supporting Linux..Netflix, flash etc etc..always remove or stop spporting Linux..What's wrong in this world???

---

### Post by Jakin on 2012-09-13
> **krishna.988 said:**
> Why none of them are not supporting Linux..Netflix, flash etc etc..always remove or stop spporting Linux..What's wrong in this world???


DRM i suspect :P

---

### Post by Starlight on 2012-09-13
> **Jakin said:**
> I definately agree with the ATI proprietary drivers not liking Gnome3 or Gnome shell, i don't know why.. 
I am using KDE 4.9 anyway, and opensource drivers... (Radeon 880g card) As for my understanding of how the flash plugin works on linux- it doesn't use hardware acceleration (maybe im wrong)? 

Could be any number of things as to why we have difference experiences...

Hmm it's all getting weirder and weirder. :O I don't have KDE installed now, but I've checked in LXDE and I still have that problem with Flash. And when I use Flash in fullscreen mode, the problem disappears! I've also tried disabling Flash hardware acceleration, but it didn't fix anything.

---

### Post by Lyfang on 2012-12-08
> **krishna.988 said:**
> I use chromium but by default it uses adobe flash plug-in. how to install the pepper flash plug-in?
 I'm using Pepper Flash with Chromium on Lubuntu 12.10, see how to install: [http://ubuntuforums.org/showpost.php?p=12388167&postcount=19](http://ubuntuforums.org/showpost.php?p=12388167&postcount=19)

---

### Post by sdowney717 on 2012-12-09
> **forrestcupp said:**
> It used to be like that, but they've added hardware acceleration in the current version. But people who have the "blue man" problem in Flash videos have to turn off acceleration to fix it.


Last week I moved to 12.04 64 bit ubuntu.
I was able to re enable hardware acceleration for flash without the colors turning weird.
I have Nvidia drivers.

(To see go full screen video and right click couple times to show the tiny menu)

---

