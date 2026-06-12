---
title: "Swfdec can now play YouTube videos"
date: 2007-03-16
forum: The Cafe
---

### Post by maniacmusician on 2007-03-16
[http://digg.com/linux_unix/Open_Source_Flash_Player_Swfdec_can_finally_decode_Youtube_videos_now](http://digg.com/linux_unix/Open_Source_Flash_Player_Swfdec_can_finally_decode_Youtube_videos_now)

Does anyone know about this? I'd never even heard of it before now. Apparently, it's far more advanced than gnash and can actually play youtube videos and the like. And it's apparently open source as well, so it looks to be pretty cool.

Question; why had I not heard of this before now?

---

### Post by eriqk on 2007-03-16
Beats me. Never heard of it either, but it seems there's a libswfdec and a swfdec gstreamer module in the edgy repos.

Groet, Erik

---

### Post by Rinnan on 2007-03-16
I'm going to try to compile this when I get home.  Hopefully it will just go in.

Anyone have any idea what the prerequisites were?  I remember that there was a tool that worked on Debian/Ubuntu systems such that if you knew the name of the missing file (the linker would spit that out upon failing to find it) you could locate the packge which had it.

---

### Post by NotPhil on 2007-03-16
> **Rinnan said:**
> I remember that there was a tool that worked on Debian/Ubuntu systems such that if you knew the name of the missing file (the linker would spit that out upon failing to find it) you could locate the packge which had it.Was it [apt-file]("http://www.howtoforge.com/apt_file_debian_ubuntu")?

---

### Post by Rinnan on 2007-03-16
apt-file -- I think that's it!  Okay, built it and installed it.

So far, no luck at all in terms of running flash software.

I usually get two big vertical bars instead of content.  Although sometimes it "sorta" looks right (YouTube videos have the ending as if you'd already watched the video, but the videos don't play, as one example).  Some ad banners appear, but very distorted.  All in all, a failure so big I can only assume that I did something wrong installing it.  I used mostly Ubuntu default -dev packages.

I guess I'll wait for the next version, or at least a .deb package which means that an expert of Debian and/or Ubuntu looked at it and did it (hopefully) right.

---

### Post by maniacmusician on 2007-03-16
> **Rinnan said:**
> apt-file -- I think that's it!  Okay, built it and installed it.

So far, no luck at all in terms of running flash software.

I usually get two big vertical bars instead of content.  Although sometimes it "sorta" looks right (YouTube videos have the ending as if you'd already watched the video, but the videos don't play, as one example).  Some ad banners appear, but very distorted.  All in all, a failure so big I can only assume that I did something wrong installing it.  I used mostly Ubuntu default -dev packages.

I guess I'll wait for the next version, or at least a .deb package which means that an expert of Debian and/or Ubuntu looked at it and did it (hopefully) right.
bummer. It's obviously possible, as he seems to have done it, but its too bad that it was a no go for you.

---

### Post by Rinnan on 2007-03-17
Little more experimentation...

swfdebug (apparently a debugger for flash files), which is compiled with the rest of the project, runs a few things that swfplayer or the browser plugin (which probably uses swfplayer) does not.  Not least of which, Extreme Stick Death 3.  Brings back memories.  Still no youtube but working on it.

Castle Defense, hops around buggily but shows something as opposed to nothing under swfdebug.  

The youtube player isn't any different under swfdebug.

Anyone else have more luck?  Next step, SVN...

---

### Post by maniacmusician on 2007-03-17
> **Rinnan said:**
> Little more experimentation...

swfdebug (apparently a debugger for flash files), which is compiled with the rest of the project, runs a few things that swfplayer or the browser plugin (which probably uses swfplayer) does not.  Not least of which, Extreme Stick Death 3.  Brings back memories.  Still no youtube but working on it.

Castle Defense, hops around buggily but shows something as opposed to nothing under swfdebug.  

The youtube player isn't any different under swfdebug.

Anyone else have more luck?  Next step, SVN...
oh, you hadn't tried SVN? 

I'm pretty sure the youtube support was only in SVN.

---

### Post by %hMa@?b&lt;C on 2007-03-17
what!!!!! I had never even heard of this.  They need to help out the gnash devs!

---

### Post by cowlip on 2007-03-17
> **jeffc313 said:**
> what!!!!! I had never even heard of this.  They need to help out the gnash devs!

The guy who coded the Youtube stuff seems to be doing just  that :)

---

### Post by Rinnan on 2007-03-19
Okay, progress report.  I used "git" to get the latest, cutting edge version.  Youtube plays fine (although search by dragging the little search knob does not work).  Sound and video sound and look good, and are synced.  Some flash games crash the entire browser instantly.  I'll report more as I see it.

I'd like to add (EDIT!) that since this is open source software, it correctly integrates into the rest of the system.  For example, using flashplugin-nonfree, the volume control keys on my laptop did not control the volume of flash videos.  It was going through maybe oss emulation or whatever.  Now it correctly integrates and the volume is controlled correctly by the volume-control laptop keys.

Already it works better than the original for my purposes (youtube).  Hopefully the rest will come soon (like playing some of my favorite flash games, such as winterbells).  Until then, I can live without the extras and now have an entirely free system except for the wireless card and BIOS.

---

### Post by maniacmusician on 2007-03-19
sweet, that's good news. I may install it when a working, stable version gets into the repos.

---

### Post by Company on 2007-03-19
First of all, the version in the repos is 0.3, where you'll be lucky if it plays any Flash file at all, but it'll certainly not even come close to playing Youtube.

I've added a [small FAQ]("http://www.advogato.org/person/company/diary.html?start=35") to my blog today, so there's some answers to questions.> **Rinnan said:**
> Sound and video sound and look good, and are synced.  Some flash games crash the entire browser instantly.Could you post the URLs please? Swfdec is supposed to never ever crash since people care about their browser. So such issues are top priority for me.> **jeffc313 said:**
> what!!!!! I had never even heard of this.  They need to help out the gnash devs!Nah. They should help me. I play Youtube, not them. :p
In reality, we're working together fine but each decided to continue going our own way.

---

### Post by maniacmusician on 2007-03-19
@Company; yeah, I know the version in the repos is old, which is why I said "when a working, stable version" gets into the repos.

Great job on this so far though.

---

### Post by Rinnan on 2007-03-19
@Company -- okay, a little rundown of my favorites :)

"Winter Bells" by Orisinal
[http://www.ferryhalim.com/orisinal/g3/bells.htm](http://www.ferryhalim.com/orisinal/g3/bells.htm)
Crashes immediately after "load", takes browser down with it.

"Extreme Stick Death 3"
[http://thetravisty.com/Flash_Cartoons/swf/Extreme_Stick_Death_3.htm](http://thetravisty.com/Flash_Cartoons/swf/Extreme_Stick_Death_3.htm)
Intro plays "X", then "I", then "A", but never gets to the "O".  Extreme browser death.

"Defend Your Castle!" by XGen Studios
[http://www.xgenstudios.com/play/castle/](http://www.xgenstudios.com/play/castle/)
Game intro plays, then you are let into the stage into screen.  This goes instantly (with a click) to your UNTIMELY DEFEAT! ;(  After a few more clicks lead you to VICTORY (with no game inbetween), it brings your browser down.

More tests upon request...

---

### Post by nwillis on 2007-03-19
Rinnan,
Could you post a .deb or a binary?

n

---

### Post by ssam on 2007-03-19
todays blog entry from the swfdec dev
[http://www.advogato.org/person/company/diary.html?start=35](http://www.advogato.org/person/company/diary.html?start=35)

people might want to wait for the release be for getting git versions

---

### Post by Rinnan on 2007-03-19
> **nwillis said:**
> Rinnan,
Could you post a .deb or a binary?

n

Okay, here are the three files that I ended up putting in /usr/lib/mozilla-firefox/plugins

[http://www.thepurr.org/libswfdec.tar.bz2](http://www.thepurr.org/libswfdec.tar.bz2)

I take no responsibility, etc., etc., etc.  I installed quite a few libraries' -dev packages to get this to compile, who knows which libraries you need to run it.  
I wish now I had taken notes, but, alas, did not.  Give it a shot and report :)

EDIT ADD: I am running on Feisty Fawn.

Although I'm sure installing binaries is easier, since I don't remember exactly what the dependencies are, it might actually be easier to install from source, using git, because then the automake/configure/build process itself will give clues as to the dependencies.

---

### Post by Company on 2007-03-20
You need at least /usr/lib/libswfdec-0.4.so.1 in addition to the plugin.

And the current git should not crash anymore on the 3 SWFs you posted. Of course, that doesn't mean they'll work perfectly, but they don't crash. :)

---

### Post by cowlip on 2007-03-22
[SWFDec has been officially released ]("http://www.advogato.org/person/company/diary.html?start=36")

[quote="Company"]22 Mar 2007 »

    It's done.[ Swfdec 0.4.3]("http://lists.freedesktop.org/archives/swfdec/2007-March/000134.html") is out, so for everyone that couldn't or didn't want to dig into the dirty world of unreleased code, grab the releases of [Swfdec ]("http://swfdec.freedesktop.org/download/swfdec/0.4/swfdec-0.4.3.tar.gz")and [Swfdec-Mozilla]("http://swfdec.freedesktop.org/download/swfdec-mozilla/0.4/swfdec-mozilla-0.4.3.tar.gz"). It will probably take a while before this hits the big distributions, since there's legal issues with the video plugins and Debian and Ubuntu are still busy releasing.

    For this release I've done all the easy tasks in Youtube playback, so **you can play/pause, rewind and watch the slider on the seek bar. You still can't seek or change the volume, but that has to wait. But you can right-click, select Properties and save the video you're watching. So there, a feature that's not in the official player.**

    A big thanks to all the people who've encouraged me, filed bugs or submitted patches, wrote articles or blog posts about swfdec and otherwise kept me busy for the last week. It's been an interesting experience although I still think I suck at marketing and public relations. Somehow Christian does a much better job pimping my stuff.

    The only thing I've figured out is that even though lots of people are interested in Flash in many different forms, there's a very small amount of people actually hacking on making Free Flash a reality. Even though the technologies used in Flash are what everyone wants. I wonder why that is?[/quote]

Does anyone know if the One Laptop Per Child project may switch from Gnash to swfdec with this development?  This article says gnash still crashes a lot plus it can't play youtube yet: [http://www.desktoplinux.com/news/NS6090685837.html](http://www.desktoplinux.com/news/NS6090685837.html)

> 
Highlights of this stable build, according to Bender, include:

    * A working mesh network
    * An updated Web browser that scales on the high-resolution screen, making for an improved web experience
   ** * Gnash, the FOSS Flash player (still somewhat unstable), is pre-installed; Adobe's Flash 9 is also known to work but is not packaged or installed as part of the build**
    * A touch-pad driver fix for jumping cursor: The touch pad should be more usable, and the tablet is enabled on B2 systems
    * Boot time has improved due to a scheduler fix

---

### Post by lulin on 2007-03-23
I compiled it on Feisty PPC. It works, but youtube-videos lag like hell. Still impressed ;-)

---

