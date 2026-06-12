---
title: "What do you do to tweak Ubuntu?"
date: 2007-11-09
forum: The Cafe
---

### Post by suupaabaka on 2007-11-09
What do you do to tweak your system? All I do at the moment is remove unwanted programs and drivers through synaptic, but I'm looking to get my hands dirty and beat the distro to fit my system like a second skin. :D

Let's all share our tips and techniques to get Ubuntu running like a Cheery Cheetah!

---

### Post by FG123 on 2007-11-09
I start by ripping out the bottom panel and stick AWN in its place (after activating Compiz Fusion and adding Emerald of course). Then I make the top panel about 90% transparent and use the Gnome Color Chooser to modify the panel text if necessary, so that it can be seen though the wallpaper.

Stick Conky on, add a few launchers and I'm satisfied, since it no longer looks like the amature Human crap that comes by default. :)

---

### Post by yabbadabbadont on 2007-11-09
After a very bad Gutsy experience, I re-installed Gentoo.  That's probably the most extreme example of "tweaking" Ubuntu.  ;)

---

### Post by ticopelp on 2007-11-09
On my laptop, I'm currently running Blackbox instead of GNOME / Nautilus. I'm trying to build a very stripped-down, distraction-free work environment by getting rid of all the extraneous eye-candy and desktop clutter. 

Of course, I've spent hours trying to configure it, so... don't ask me if this is really in aid of efficiency or not...

---

### Post by oldos2er on 2007-11-09
When I ran Feisty, I used these tweaks: [http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml)

 All of them work on Gutsy too, except for the concurrency=shell tweak. In order to get that one to work I had to mess around with dbus priorities.

---

### Post by Gremlinzzz on 2007-11-09
> **yabbadabbadont said:**
> After a very bad Gutsy experience, I re-installed Gentoo.  That's probably the most extreme example of "tweaking" Ubuntu.  ;)

Never tried Gentoo is it better than gutsy.:lolflag:you dont have to answer that question .

---

### Post by PurposeOfReason on 2007-11-09
> **Gremlinzzz said:**
> Never tried Gentoo is it better than gutsy.:lolflag:you dont have to answer that question .
The way I see it, many linux distributions will end up the same with me, the only thing that will be different would be how I install things. With Ubuntu, it's all mostly just ready. With gentoo, you build your fun bit by bit (if that is fun to you). I go for the happy medium of Archlinux.

---

### Post by yabbadabbadont on 2007-11-09
> **PurposeOfReason said:**
> The way I see it, many linux distributions will end up the same with me, the only thing that will be different would be how I install things. With Ubuntu, it's all mostly just ready. With gentoo, you build your fun bit by bit (if that is fun to you). I go for the happy medium of Archlinux.

The last time I checked, Arch didn't have nearly as large a package selection as does Gentoo.  Other than that, it seemed like a nice enough distribution.  I think that the next OS I install on this machine will probably be FreeBSD.  Like Arch, it offers both binaries and source compilation through the package manager.

---

### Post by Gremlinzzz on 2007-11-09
> **yabbadabbadont said:**
> The last time I checked, Arch didn't have nearly as large a package selection as does Gentoo.  Other than that, it seemed like a nice enough distribution.  I think that the next OS I install on this machine will probably be FreeBSD.  Like Arch, it offers both binaries and source compilation through the package manager.

So Gentoo is better than Arch?

---

### Post by yabbadabbadont on 2007-11-09
No, just different.  It is better than Arch *for me*, but it isn't better for everyone.

---

### Post by Gremlinzzz on 2007-11-09
> **yabbadabbadont said:**
> No, just different.  It is better than Arch *for me*, but it isn't better for everyone.

So Gentoo is differently better than Arch. how about Gutsy what was your nightmare experience.

---

### Post by yatt on 2007-11-09
> **Gremlinzzz said:**
> So Gentoo is better than Arch?Depends what you want. If you do it right, you probably cannot get a system that will out perform Gentoo (maybe an entirely compiled FreeBSD). However, it gives you every opportunity to fail.

The installer is only useful to people who can install Gentoo without an installer. Doing it without the installer takes most people over a week the first time, even though Gentoo comes with horribly thorough documentation.

Gentoo uses Portage to manager 'packages'. I use quotes, because on Gentoo you really just download a script that will compile the program for you. 

Gentoo is made for people that want to get their hands dirty. By dirty, I do mean they want to have to sacrifice a goat to get their system up and running.

---

### Post by steveneddy on 2007-11-09
> **yabbadabbadont said:**
> After a very bad Gutsy experience, I re-installed Gentoo. 

AHHHHH!! - I** knew** you were one of those!

I knew it........

one day they will come back in their true form and suck the brains from the top of our skulls.......

**fuscia** is your neighbor, or something....right?

---

### Post by suupaabaka on 2007-11-09
I've always wondered if there's a noticeable increase in speed with distros tailored to your machine's specifications...

Yabbadabadont and anyone else who might use Gentoo: Do you see much of a discrepancy between Gentoo and Ubuntu performance?

---

### Post by bionnaki on 2007-11-10
no, not really. maybe bootup time is a few seconds quicker, but normal usage is about the same. Desktop environments make more of a difference (KDE vs. Openbox, for example).

---

### Post by professor fate on 2007-11-10
> **oldos2er said:**
> When I ran Feisty, I used these tweaks: [http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml)

 All of them work on Gutsy too, except for the concurrency=shell tweak. In order to get that one to work I had to mess around with dbus priorities.

Great link!  Thanks.

---

### Post by yatt on 2007-11-10
> **suupaabaka said:**
> I've always wondered if there's a noticeable increase in speed with distros tailored to your machine's specifications...

Yabbadabadont and anyone else who might use Gentoo: Do you see much of a discrepancy between Gentoo and Ubuntu performance?

Meh.

Even with Gentoo on old sysvinit booted faster than Ubuntu (I know Upstart isn't meant to speed things up, but running things in parallel makes a big difference). I guess you can argue big deal, as even if it reboot every day, it is still only 1/100000000th of the time your computer is actually up.

Things compile a bit faster, which is nice if you are in a programming course. Wasting less time sword fighting would be a bonus. Although, I wouldn't really want to run Gentoo on a laptop. 

I'd say no in all real cases. If you are some kind of system admin or a hard core developer, I could see the change worth it. Otherwise all those little increases are completely overshadowed by the time Portage takes to compile.

---

### Post by Metacarpal on 2007-11-10
> **yatt said:**
> Gentoo is made for people that want to get their hands dirty. By dirty, I do mean they want to have to sacrifice a goat to get their system up and running.

That's why I'm not running Gentoo right now - lack of goat.  All I have is this lousy android sheep.

That, and I'm on a laptop.  Insofar as I can tell, the only thing harder to get running on a laptop than Gentoo would be RedHat/Fedora/CentOS.

---

### Post by professor fate on 2007-11-10
My neighbor has an annoying dog.  Will that do in place of a goat?

---

### Post by Metacarpal on 2007-11-10
> **professor fate said:**
> My neighbor has an annoying dog.  Will that do in place of a goat?

Place a milk carton in front of the dog.  If the dog attempts to eat the milk carton, then it is close enough to a goat for your purposes.

---

### Post by akiratheoni on 2007-11-10
> **yatt said:**
> Things compile a bit faster, which is nice if you are in a programming course. Wasting less time sword fighting would be a bonus.

+1 for xkcd reference :-D

Anyway, to be on topic, I don't really do anything... I just make sure my resolution's all nice and dandy and that's pretty much it. I don't tweak GNOME a whole lot.

---

### Post by Frak on 2007-11-10
> **yabbadabbadont said:**
> After a very bad Gutsy experience, I re-installed Gentoo.  That's probably the most extreme example of "tweaking" Ubuntu.  ;)
I installed Arch, I just like the raw reworking better than a "can of soup". I would use Gentoo if it weren't for my extreme dislike for portage.

---

### Post by reidbold on 2007-11-10
Ditch the taskbar for awn, drag the thing on top to the left, where I won't see it as much. Launchers for firefox, audacious, terminal, and away I go from there. 



Gentoo runs dandy on my laptop. It's fun! You guys are just spoiled by network-admin. It's not any faster though, don't buy the hype. --funroll-loops and all that. I contest you can get gentoo running in 90 minutes from minimal install cd, xwindows is another story:confused:

---

### Post by yabbadabbadont on 2007-11-10
As others have said, there isn't any real runtime performance improvement with Gentoo.  Although I've heard people with very old hardware say that it helps.  The main thing I like about it is that with USE flags, I can easily include/exclude any optional features a package may have.  So I end up with a system that has only what I want, with the minimum of required dependencies installed.  You also don't have to worry about installing the development version of a package (they are all development versions ;)).  Also, it is very easy to get newer versions of programs, even if they aren't yet listed in the portage tree.  It took all of ten minutes (OK maybe 20) for me to modify the fluxbox ebuild so that it pulls the source from the live svn repository instead of using the released versions.  And it is fully integrated into portage (through my local overlay), so it is easy to update to the newest svn code or to completely uninstall it if I wish.

---

### Post by MadsRH on 2008-01-07
Has no one mentioned [**Ubuntu Tweak**]("http://ubuntu-tweak.com/").
It seems to be just what I was looking for and properly is for every Linux newbie. :grin:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

[IMG]http://ubuntu-tweak.com/wp-content/uploads/2007/12/ubuntu-tweak-024-2.png[/IMG]

---

### Post by Praadur on 2008-01-07
My tip is to share my obsessive nature when it comes to unnessescary things laying around on my drive.

I use the following script to keep an eye on what packages I've recently installed (so I can do a proper clean up if I wish to get rid of something):

```
#!/bin/sh
# /usr/sbin/pkgbydate
s -lrt /var/lib/dpkg/info/*.list
```

I hate it set as executable, so I can just type 'pkgbydate' at the command-line.  I find this to be very handy as it allows me to keep an eye on what I'm doing with my system, and it's a surprisingly accurate timeline system, too.

Another thing I'd recommend is getting deborphan (sudo apt-get deborphan), run it in a terminal once you have it and use 'apt-cache search name' to find out what each does, and remove anything that doesn't sound vital to the system.

Finally, I tend to use programs that share libraries, so I tend to prefer four applications that share on library as opposed to one application that installs four libraries, and I tend to shuffle software due to that (it's one of the reasons I went from Banshee to Exaile, for example).

Another thing I'd recommend is getting a system information report tool like [conky](http://conky.sourceforge.net/) which can tell one lots of important things without devouring the CPU (though others have probably mentioned this).  I use it mostly to keep an eye on my HDD, I don't like it getting past the 60-70 per cent filled mark because the more full a drive is, the better the chance it could fragment.  Rare in ext3 I admit but possible.  Conky is also a nice way to keep an eye on system temperature, to make sure one's fans are kicking in at the right time and such, and that's very useful too.

Though I expect someone's already mentioned conky...

It can be helpful to run 'gconf-editor' every once in a while, just to step through all the entries and nose at the settings to make sure everything is as I like it.

And most recently I used a bunh of patches submitted around forums to get keyconfig working in Firefox (I still have the xpi and I'll share if anyone wants it) so I could bind a key to Perfect Menu and thus access all my important dropdown menu entries via Alt+F, thus getting rid of the space-wasting menu bar.  It's not strictly Linux but it does help to improve my Linux experience.

After wracking my brain for a bit, the only other thing I could think of is that I tend to use the top command in the terminal to watch out for overly system intensive programs.  If I find a program that's chewing up a lot of memory and/or CPU, I'll likely head off in search of a replacement that's less intensive.  Taking a noe at top occasionally can be handy, especially if one's computer slows down for any reason.  Via top I found out that artsd was quite the resource killer, so I ended up renaming the artsd binary to artsd-backup and creating a blank file in its place.  I haven't had any loss of system stability of this and the only negative aspect is (as expected) that I don't get alert sounds in KDE apps, but that's really not a big deal when compared to the gain in resources.

Hm, anything else, anything...

I add repositories to my sources.list often and that sources.list is usually the first thing restored on a new installation.  I have all sorts of things in there, such as the wine repos to the *very* helpful Medibuntu and KPlayer repos (very good for codecs and a nice place to painlessly get w64codecs from).  If anyone watches a lot of video files (such as fansubbed anime and so on), then I'd heartily recommend checking those out, as it makes it so much easier to get one's player to be compatible when one comes across an unfriendly format.  I even have my MPlayer playing RMVB, MKV, and MP4 files flawlessly now.

That's really all I can think of for now, mostly because I'm really tired and my brain doesn't work too well under such conditions.  I'll see if I can come up with anything else later.

---

### Post by Zero Prime on 2008-01-07
> **MadsRH said:**
> Has no one mentioned [**Ubuntu Tweak**]("http://ubuntu-tweak.com/").
It seems to be just what I was looking for and properly is for every Linux newbie. :grin:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

[IMG]http://ubuntu-tweak.com/wp-content/uploads/2007/12/ubuntu-tweak-024-2.png[/IMG]

I like that.  It reminds me of TweakUI

---

