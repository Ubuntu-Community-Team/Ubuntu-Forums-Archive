---
title: "Wine, iTunes, And My Blood Pressure"
date: 2010-07-21
forum: Testimonials &amp; Experiences
---

### Post by temporos on 2010-07-21
*Preface:* This is not a question.  It's more a journal of my quest to dig the canal between the ocean of Linux and the inland iTunes reservoir...

* * *

It's been a long, **long** road.  Well, more accurately, it's been akin to having my wisdom teeth surgically extracted without anesthetic and with rusty dental tools.  I don't know first-hand what that would feel like, but I imagine it would be similar to attempting to make iTunes and Linux play nice.

When I first adopted Linux (Slackware, at the time), I was using iTunes 4.  I know; it was a long time ago, eh.  Anyway, I had read a lot of articles online about how iTunes would not work under Wine.  So, my first attempt to run it was via a virtual Windows machine running in Slackware.  The virtual machine ran well, and Windows seemed to have no problems, but iTunes crashed every time it loaded.

My next attempt was to load it using Wine, at which so many other (more experienced) users had failed.  It actually seemed to work... for about two days until Apple release a minor update.  Then it stopped working.  I have never gotten an iTunes release to run on Wine since then.

I've attempted many things since then to get iTunes to run in Linux.  In the past several years, my taste in Linux flavours has changed from Slackware to Ubuntu to Gentoo and back to Ubuntu.  I've tried both virtual Windows machines on every distribution, and every subsequent combination of both Wine and (functional) iTunes.  No joy there, obviously (otherwise I wouldn't be writing this).

The main reason I wanted iTunes to work, was because I have an iPod.  I'm a huge fan of their portable media players, because let's face it, Apple knows how to design really nice hardware.  Unfortunately, I'm not a fan of their software, so just getting a Mac is out of the question.  Linux is my preference for OS, and iPod is my preference for portable music.  I know you can now sync iPod in Lucid, but it doesn't handle backups and apps, which 
I use extensively in iTunes on my Windows box.

At this point, I fear my only option is to find a new portable music player: one that is compatible fully with Linux (and Rhythmbox).  I already have my eye on the Google Nexus One for my next cell phone, and according to the reviews, it has a wonderful music player built-in.  I've also read that it's fully syncable (is that a word?) with common Linux applications.  That makes sense, since Android is a Linux-based OS (although Mac OS is, too, so it's no guarantee).

Anyone have any questions, comments, or snide remarks?  I'd like to know what people think about the whole Linux vs portable devices thing.

Cheers.

---

### Post by aysiu on 2010-07-21
I ditched iPods for Sandisk players long ago for precisely this reason.

Oddly enough, I have now switched to Mac OS X so I could use an iPod Touch or iPhone with iTunes if I wanted, but I happen to like using a Sandisk player for music and my Android phone for everything else.

---

### Post by rollin on 2010-07-21
> **temporos said:**
> 

My next attempt was to load it using Wine, at which so many other (more experienced) users had failed.  It actually seemed to work... for about two days until Apple release a minor update.  Then it stopped working.  I have never gotten an iTunes release to run on Wine since then.



The only comment I'd add is the piece above doesn't suprise me! For whatever reason version X of an .exe may only work with wine version X, any changes to the formula and the whole thing falls over! When you say it stopped working though, what happened? Just for example, I've managed to get around "screen won't load after installation" type stuff by using the "emulate a virtual desktop" setting in Wine configuration. You get a blue screen to the pixel size you specify prior to the app loading but it seemed to work in the past. 

Short of prodding Wine until it works, checking versions of iTunes and wine etc at their website AppDB to see if someone has achieved a magical combination... The only other option could be Crossover Linux?! There is a free trial version and it might work...

---

### Post by Riffer on 2010-07-21
Did you know that there is iPod syncing now for Linux.  There are threads explaining what package you need to use RythmBox (or your fav media player) To add music to your iPod.

---

### Post by JailHouseRock on 2010-07-21
Maybe you could try Floola, I have been using it on windows for a long while and I love it. It lets me manage my iPod without that nasty stinking iTunes.

[http://www.floola.com/home/](http://www.floola.com/home/)

I haven't gotten around to try it on Ubuntu yet, but I figure it should work just as well as it does on windows.

Good luck!

---

### Post by warjowuch on 2010-07-21
Or try rockbox firmware on your iPod. I might be much more accessible from your linux pc

---

### Post by temporos on 2010-07-21
> **warjowuch said:**
> Or try rockbox firmware on your iPod. I might be much more accessible from your linux pc

No, I'm done dealing with iPod.  Getting iPod and Linux to work together is like trying to make a diamond by squeezing coal in your hand.  It's not going to happen.

[QUOTE=Riffer]Did you know that there is iPod syncing now for Linux.[/quote]

Um... yeah.  I mentioned that in my OP.  I think you missed the part where I talked about how I use **apps** on iPod, as well.

Like I said, at this point, I'm looking into other capacitive touch-screen options.

---

### Post by e24ohm on 2010-07-21
> **aysiu said:**
> I ditched iPods for Sandisk players long ago for precisely this reason.

Oddly enough, I have now switched to Mac OS X so I could use an iPod Touch or iPhone with iTunes if I wanted, but I happen to like using a Sandisk player for music and my Android phone for everything else.

I second that idea - I am not sure when I started converting my items over, but I am a big fan of the ogg format. It is simple and effective, and in addition, the standard for html5 (at this point).

I started out, and still use SanDisk Sanza since it was one of the very few players that support ogg; however, the avi play back has given me problems. It appears to not use a standard avi codex, yet using the conversion software I am able to get videos loaded on the device.

OTQ (off topic qustion) - Does the Android support ogg video, or does the browser support html5? If that is the case, then problems have been solved for video play back...just use .ogv files with html5 code.

thanks.

---

### Post by JailHouseRock on 2010-07-21
I wish there was a player that could equal the iPod classic 160GB, but I have seen no yet and I don't fancy touch screens much. A player that plays all audio formats, has a big storage, good interface, good battery life and allows me to put music on it without too much hassle, is there really no market for that? I find it odd that (as far as my research goes) Apple is the only one to properly satisfy my needs albeit not all of them.

---

### Post by asdfoo on 2010-07-22
has anyone thought about writing a letter to Steve Jobs?  he responds to some customers.

If I owned an ipod, I'd write him and ask that they look into making iTunes for Linux.

Failing that, put someone smart enough (I'm sure Apple has many smart programmers) to work on identifying problems with iTunes under Wine by giving the person access to iTunes source code for debugging under Wine.   

Alternatively, Apple could pay Codeweavers who do commercial contract support for Wine to spend their time debugging iTunes.

Unfortunately, I think their greatest fear would be the people who buy a mac because itunes works properly there would no longer do so - but that's a bit monopolistic isn't it?

---

### Post by Ginsu543 on 2010-07-22
For what it's worth, I am running iTunes 9.2.1 in a Windows XP client using VirtualBox on my Ubuntu 10.04 to sync my iPhone 3GS (upgraded to iOS 4.0.1) as I type this. With this setup, iTunes is stable and works as it should, as long as you install the PUEL version of VirtualBox (with USB support) and not the open-source one.

---

### Post by soldier1st on 2010-07-22
this is one of the reasons i stay away from apple products is that in order to access it you can't simply drag and drop, you are forced to use there software and it of course works fine for a mac but it is just functional enough for windows but it is not in linux without doing some workarounds and true some linux software can sync certain things but it can't fully do the job and probably never will, if you email steve jobs i would not be surprised if he laughed at you for even thinking of possible official linux support and would write you off. the good thing about something like an mp3 player is that your not forced to use a certain software if you don't want to just to access it and you can drag and drop which is very handy.

---

### Post by Macskeeball on 2010-07-22
Because temporos never explicitly said it (although he came much closer to it in a later post), the iPod in question is an iPod touch. Therefore, Rockbox won't work and there are also more thngs to handle than with a clickwheel iPod.

Now to reply to various people.

> **temporos said:**
> *Preface:*I already have my eye on the Google Nexus One for my next cell phone, and according to the reviews, it has a wonderful music player built-in.
I've not used Android much myself, but from what I've heard on various tech podcasts is that media playback is one of Android's shortcomings. Google is no longer selling the Nexus One online, but you can still get it through a carrier.

> **temporos said:**
> I've also read that it's fully syncable (is that a word?) with common Linux applications.  That makes sense, since Android is a Linux-based OS (although Mac OS is, too, so it's no guarantee).
Mac OS X is not based on Linux. It uses the mach kernel, not the Linux kernel, and is built on top of Darwin which has a BSD subsystem. Linux is Unix-like. OS X is Unix-based.

[quote=e24ohm]OTQ (off topic qustion) - Does the Android support ogg video, or does the browser support html5? If that is the case, then problems have been solved for video play back...just use .ogv files with html5 code.

thanks.[/quote]
As far as I know, Google doesn't support Ogg Theora out of fear of submarine patents, but as open a platform as Android is it wouldn't surprise me if there were a way to add support to it- ether through an app or rooting and using a custom ROM. As far as open formats for video, Google backs [WebM](http://www.webmproject.org) and the VP8 codec, which they own.

[quote=asdfoo]has anyone thought about writing a letter to Steve Jobs? he responds to some customers.

If I owned an ipod, I'd write him and ask that they look into making iTunes for Linux.

Failing that, put someone smart enough (I'm sure Apple has many smart programmers) to work on identifying problems with iTunes under Wine by giving the person access to iTunes source code for debugging under Wine. 

Alternatively, Apple could pay Codeweavers who do commercial contract support for Wine to spend their time debugging iTunes.

Unfortunately, I think their greatest fear would be the people who buy a mac because itunes works properly there would no longer do so - but that's a bit monopolistic isn't it?[/quote]

I suspect that, in the case of Windows, Apple chose to port iTunes to a competing OS because it opened up such a large number of people to sell iPods too. In the case of desktop Linux, the marketshare is at most about equal to Mac OS X. Therefore they're not "forced" to port iTunes and don't want to give people a reason to switch to Linux if they've been holding off because of iTunes. That's just my own speculation, however.

---

### Post by gunfyter on 2010-07-22
> **Macskeeball said:**
> 


I suspect that, in the case of Windows, Apple chose to port iTunes to a competing OS because it opened up such a large number of people to sell iPods too. In the case of desktop Linux, the marketshare is at most about equal to Mac OS X. Therefore they're not "forced" to port iTunes and don't want to give people a reason to switch to Linux if they've been holding off because of iTunes. That's just my own speculation, however.

BINGO!    If you can run iTunes on Linux... what possible reason could there be to own a Mac?

Ain't gonna happen ... no how -- no way....

This is why I dual boot Lucid/XP and XP/Mint (Isadora).     

I can run Quicken2009 under Lucid through Code-Weavers Crossover... or on the XP boot.   Turbo-Tax ...  Pretty much need Windows or a Mac.   Ready to migrate to GNU-Cash from Quicken but I have a lot of data to translate.

---

### Post by temporos on 2010-07-22
> **Macskeeball said:**
> the iPod in question is an iPod touchThat's correct.  I probably should have said that outright, but as I was really just posting my experience, it didn't seem necessary.


> **Macskeeball said:**
> Google is no longer selling the Nexus One online, but you can still get it through a carrier.Hoo boy...  Know of any other good touch-screen phones?  I'm looking for a device that can do music, web, e-mail, video, phone, you-name-it?  Basically an iPhone, but not an Apple product... for obvious reasons.

---

### Post by Macskeeball on 2010-07-22
> **temporos said:**
> Hoo boy...  Know of any other good touch-screen phones?  I'm looking for a device that can do music, web, e-mail, video, phone, you-name-it?  Basically an iPhone, but not an Apple product... for obvious reasons.

Let's see... the best Android phones currently are:
-Verizon: Motorola Droid X or HTC Droid Incredible
-Sprint: EVO 4G
-All carriers: Samsung Galaxy S (goes by different names on different carriers).

Avoid Android phones on AT&T if possible; they're crippled. The Droid X and the EVO have big screens (4.3") which you may or may not want. Also, I've heard that games are sorely lacking in Android due to the fragmentation of devices making it difficult to develop for.

---

### Post by Macskeeball on 2010-07-22
> **gunfyter said:**
> BINGO!    If you can run iTunes on Linux... what possible reason could there be to own a Mac?

Oh, there would still be reasons. Off the top of my head, there's the rest of the iLife suite (iPhoto, iMovie, Garageband, iWeb, iDVD) of which iTunes is just one part- and they all work together. You get a lot of the major commercial software you'd find on Windows, plus surprisingly polished apps (often free) by smaller developers, plus Unix under the hood, plus simple yet powerful automation tools like AppleScript, Automator, and OS X Services, plus the ability to also run Linux and Windows if you so desire (multiboot or in a VM). Every OS has its own strengths and weaknesses. I use all three major OSes, BTW.

What I'm trying to say is that porting iTunes to Linux wouldn't kill all reason to use a Mac, but it would remove a major obstacle for switching to Linux (from either Mac or Windows) for a lot of people. Apple and Microsoft want to keep Linux desktop usage small for as long as they can. They don't want to remove obstacles to its growth when they don't have to.

---

### Post by temporos on 2010-07-22
> **Macskeeball said:**
> Let's see... the best Android phones currently are:
-Verizon: Motorola Droid X or HTC Droid Incredible
-Sprint: EVO 4G
-All carriers: Samsung Galaxy S (goes by different names on different carriers).

Avoid Android phones on AT&T if possible

Well, I'm in Canada, so the choices here for carriers are different.  I've heard that the EVO and Droid weren't nearly up-to-par as the iPhone.  I find it difficult to believe that there's no comparable device on the market.  So far, the closest I've seen was the Nexus One.

I'll be looking into T-Mobile phones.  I found out that my carrier here uses the same RF band.

---

### Post by Macskeeball on 2010-07-22
> **temporos said:**
> Well, I'm in Canada, so the choices here for carriers are different.  I've heard that the EVO and Droid weren't nearly up-to-par as the iPhone.  I find it difficult to believe that there's no comparable device on the market.  So far, the closest I've seen was the Nexus One.

I'll be looking into T-Mobile phones.  I found out that my carrier here uses the same RF band.

If you're talking about T-Mobile USA, they call their version of the Samsung Galaxy S the [Samsung Vibrant](http://galaxy-s.t-mobile.com/). I'm ignorant of cell phones in Canada, but for others, what carrier are you on?

Also, [www.howardforums.com](www.howardforums.com) is a great cell phone community and they have a section for Canada and a forum for Android. You might want to ask there too.

---

