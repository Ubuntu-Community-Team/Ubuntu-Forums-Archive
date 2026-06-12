---
title: "I should've never left Dapper"
date: 2006-10-27
forum: Testimonials &amp; Experiences
---

### Post by DigitalDuality on 2006-10-27
d

---

### Post by DoctorMO on 2006-10-27
niggle:

> product

Ubuntu isn't a product, it isn't covered by the goods of sales act because 1) Your liciencing the software from each development comunity under the GPL and 2) because it's free of charge.

bless.

---

### Post by P_Badger on 2006-10-27
Well, once I got edgy installed, from a clean install, I've found it to work like a charm. Boot up time is cut by half, everything is pretty and nice. But I do have to admit that the upgrade is pointless unless you're upgrading from a *clean* install of dapper. ; P (Which I've done, btw, just out of curiousity.) 

I've been told that upgrading is the plague of linux, and it's quite common for upgrades to screw up. Hopefully this'll change in time.

---

### Post by DoctorMO on 2006-10-27
Although upgrading from 2000 to XP or ME to XP wasn't exactly charmed. and I've known OS X to be a real pig since it tends to delete all your root files, no logs, websites or databases survive.

---

### Post by yelloguy on 2006-10-27
Very well said.  My thoughts exactly.

We went through so many Beta/RC cycles for this?  I can see all sorts of ndiswrapper problems being reported from Beta days but no one fixed those in release.

It seems ungrateful writing all this for a product that is essentially "free" (my time has a cost, though) but I wasn't asking for an upgrade.  They may have just pushed the release of Edgy a month or two to sort out all these terrible problems.

---

### Post by P_Badger on 2006-10-27
> **DoctorMO said:**
> Although upgrading from 2000 to XP or ME to XP wasn't exactly charmed. and I've known OS X to be a real pig since it tends to delete all your root files, no logs, websites or databases survive.

This is very much true, too. I lost a ton of stuff when upgrading from 98 to win2000. With linux I like to keep a separate partition for /home, so I didn't really lose anything of importance.

---

### Post by dbott67 on 2006-10-27
I think I'll hold off on the upgrade.  I always prefer the 'fresh install' method myself (although the **sudo apt-get dist-upgrade** feature seems like a nice easy way to do it --- if it works).

I'll wait a few weeks before I try to bugger up my system!

---

### Post by jacrider on 2006-10-27
I can't agree more.

Tried doing a distribution upgrade and lost Xorg.

Ended up having to do a clean install and that messed up so much software ... especially MythTV which I am probably not going to install as it was such a pain in the first place.

I would much rather see smaller, regular incremental upgrades done through the update manager.

I probably have spent 4 hours messing with this and still have a way to go as I don't have Twinview working.

Ugh.

I am committed to Ubuntu, I just found this upgrade frustrating.

---

### Post by RudolfMDLT on 2006-10-27
i have been trying to upgrade from the alternate cd for about 10 hours and:
[http://ubuntuforums.org/showthread.php?t=285759](http://ubuntuforums.org/showthread.php?t=285759)

Gave up and i've been downloading the web update for 7 hours straight. I have 59 min remaining.... AND NOW I READ THIS! Why!? [-o<

---

### Post by tubasoldier on 2006-10-27
Are you all serious? Were you not reading the forums before edgy came out? The fact that edgy is not going to be as supported as long as Dapper should be a HUGE clue for you! The fact that there is a thread dedicated to wireless cards that will no longer work under Edgy is another HUGE clue. The fact that there were threads with polls asking if Edgy should be delayed because of the wireless issues. DING DING DING! Yeah, another MASSIVE clue!

It is simple. The latest and greatest is not always the best. The same will apply when that waste of space Vista comes out. I wouldn't touch that pile of garbage with a 10 foot pole until they get to at least Service Pack 1.

The evidence was right before your eyes! The forums were FULL of warnings. But there were still people who "Couldn't Wait!" and who wanted to know "Will Edgy Be Released At Midnight?".  This attitude is rediculous. Of course its going to break. READ BETWEEN THE LINES!

As for me I'll stick with Dapper for a few more months. If i want a newer version of software I'll just compile it from sorce myself. Have fun fixing your systems.

---

### Post by DigitalDuality on 2006-10-27
d

---

### Post by MetalMusicAddict on 2006-10-27
As a rule of thumb I ALWAYS do a clean install. I would suggest you do one. I used the exact same xorg from my Dapper install as well.

---

### Post by Wolki on 2006-10-27
> **DigitalDuality said:**
> Take a look around the Ubuntu Forums lately and you'll see many installation and various related threads just cropping up with problems. Not just noob problems, but people that are pretty knowledgable about linux, about how to fix things when they break, and they're left clueless with Edgy.

Actually, I'm not surprised.
Warty to Hoary:
"Oh no! Warty was so good, why did the developers have to go and ruin it!"
Hoary to Breezy:
"I can't see why the developers have to go and fix things that aren't broken... Hoary was the best Linux ever, Breezy sucks completely."
Breezy to Dapper:
"So that's the super-stable polished Ubuntu? Why is it so much worse than Breezy then?"
Dapper to Edgy:
well, you know it.

And there always were knowledgable people among them. I fear it's part of life.

> Also let me state that doing a sudo apt-get dist-upgrade has worked for me many times before but it's always assumed much can go wrong as to compared to a clean install.


I've done dist-upgrades since Warty, and I've never had problems. (Not the same system, since  I had a complete hard disk failure during Hoary and a smaller one during Breezy). Usually even the development versions.

Some things can create lots of problems when dist-upgrading though. Outside repositories are likely the biggest problem - it's hard to test upgrade paths if people are running non-standart versions.

> **The Download**


Well, everyone's trying to getit at the same time... it will be slow. Either wait a few days, or upgrade a bit earlier.

> 
**Upgrading to Old Software?**
A minor annoyance for sure, but days before the Edgy upgrade I decided to go with Gaim 2.0 beta 4. Upon the Edgy upgrade, Ubuntu recognized this as older software that needed to be replaced by Gaim 2.0 beta 3. Can Ubuntu not see what version numbers software is before removing it? I guess that was an hour of my life well wasted. 

The Ubuntu packages are Epoch 1:, which is considered newer. Basic idea is that sometimes a new version has a lower number than the previous. To not confuse apt. a special number called epoch is prefixed to the version number. With GAIM, it appears this has happened once, thus its packages' version number starts with 1:. If someone creates a package, it has to have the same epoch, or will be considered older. 

> 
Even after going through the beta 4 install AGAIN, ubuntu still wants to replace it with beta 3 upon a sudo apt-get upgrade. So basically until they decide to put beta 4 in the repo's I have to go without updates.


You can either use a package with a correct epoch, or use pinning to keep a certain version on your system. See synaptic for how to pin.

**GUI File Manager Disaster**
Now here's the real kicker. I do have Nautilus installed, and Thunar, and Konqueror. All 3 file managers, while running as a regular user, or gksudo.. can only see my home directory. If i attempt to go above that directory, or even type “/” in Konq's address bar, i get a folder i've never seen before containing my Home directory and a media directory for removable media. But nothing else. In no way shape or form do I have a GUI way to reach /etc, /var, /usr, etc..[/quote]

You need to show hidden files. This is actually not an Ubuntu decision, it's a Kubuntu one. The symptoms you describe only happen to people who have kubuntu-desktop installed.

> Going through a terminal, I can view all directories just fine. But that's not the point of Ubuntu. Ubuntu is made to be easier than most distrobution. This isn't Gentoo. I shouldn't have to use the command line every single time I need to access a folder for administrative purposes.

I think the idea is that you shouldn't have to access a folder outside your home for administrative purposes ever. 
> 
How does it effect all file managers? As root? As a regular user?

There's a file called .hidden inside your / which contains the names of all files and folders that are supposed to be hidden. It will affect everyone who has read acess to the file.

> **Multimedia Woes**
Wow, and where to begin here. Mp3 support that I once had is now gone. As is mpg, avi, wmv, mov, you name it. Kdemultimedia will no longer preview video files in Konq any longer. They won't play in totem, kaffine, mplayer, not even good ol' trusty vlc. Thank god automatix2 to help out but even that didn't solve all my problems. Automatix has made it so VLC can now play avi's. I can now listen to my mp3s in beep media player. But not amarok. WMVs are completely unplayable in all media players now, and it even crashes VLC. Kaffeine and totem have been rendered completely useless. And DVDs will no longer play. And get this, not even OGGs play.

There's something else wrong. I can play stuff fine on several dist-upgraded computers, with every player I have installed (which are a lot). Make sure you have the right codecs installed (basically the gstreamer and xine extra codecs, and some small stuff like gstreamer-pitfdll)

> My conclusion, unless you're doing a clean install, don't bother with Edgy.

No problems here.

Usually problems with dist-upgrades come from people doing stuff the developers recommend not doing, like additional, possibly low-quality repositories, and automatic setup tools, or messing with system internals. This is not to say that mistakes don't happen, and developers might not catch some error with regards to dist-upgrades that only happen in certain circumstances.
I find edgy to be a relatively stable system, considering how short dthe development cycle was.

---

### Post by RudolfMDLT on 2006-10-27
After going through hell, I'm running edgy! Doing the web based install, not the cd or the clean install worked. Not perfectly and some mid-install tweaking was required but it's working. I don't have 3d yet but i'll fix that later! Honestly, stick to Dapper cause Edgy so far ain't worth it.
I'm sorry to say it and I never rant but this really was a waist of a day(14 hours in total to upgrade) and of money.

---

### Post by DoctorMO on 2006-10-27
Well not only was everyone warned it's an edgy release, not only is it in the name, but it's only been out for a day.

I won't get edgy for at least a month.

---

### Post by munroe on 2006-10-27
Did an install earlier today using the update manager GUI. I usually work in the terminal, but I wanted to see if the team could pull it off.

So far, no problems. The new boot up is speedy, the new icons and feel of the desktop is great, and Gnome is quicker. Can't complain about much. I've got an nVidia chip, that had 3d acceleration working, and I still have 3d acceleration working. No issues with X at all.

I had a small issue with my menu's not showing up, but that was related to my compiz/xgl install.

---

### Post by jackkerouac on 2006-10-27
I did a Update manager update yesterday and my X Server crashed. A little ...

```
sudo aptitude xserver-xorg-driver-radeon
```

... and everything was working fine.

Oh, I also had to install gnome-settings-daemon manually.

I run XGL, Beryl and kiba-Dock and it all runs just fine.

---

### Post by jdunn on 2006-10-27
> **DigitalDuality said:**
> 
My conclusion, unless you're doing a clean install, don't bother with Edgy. It's Ubuntu's single most worthless product. 

Awe, its not bad.  I'm a former Mandrake/Suse/Gentoo user and I started on Kubuntu with Dapper one month after its release.  I was happy with Dapper and I'm happy with Edgy (so far).  I've currently found fewer problems on Edgy (release day + 1) than I did when I started on Dapper.  Having said that, here are the issues I've found so far:

1)  I Can't seem to get DPMS to work, but it worked fine in Dapper.  I've noticed several rants in the forums about Edgy 'suspend' and 'hybernate' issues in the last 2 days so I suspect there is something wrong with power management that will soon be patched.

2)  Kaffeine is crap...what it was, what it has been, what it probably will always be.  Its too bad Kaffeine is the default video app in KDE.  In Dapper, Kaffeine 0.7.1 and 0.8.2 crashed on me very frequently.  In Edgy, Kaffeine started out working well but after I installed some other nonrelated packages, I noticed A/V is now out of sync.  The only way I can compensate is by adjusting an A/V offset every time I startup Kaffeine and play a DVD.  (You CAN NOT save the offset settings...One more reason why Kaffeine is a POS)

3)  Edgy uses supermount for CDs.  I dislike supermount...but I guess its appealing for the linux newbies who just migrated from M$ Winblows.  Dapper didn't have supermount.

---

### Post by Aranel on 2006-10-27
Personally, I did a clean install, and everything's working flawlessly for me so far. Wireless was up in about a minute, printing was set up in a matter of seconds, codecs and stuff all work... The only qualm I have is that suspending to RAM just turns the system off (although hibernation works as advertised), and we were all warned beforehand of that. All in all, Edgy seems nothing short of awesome so far.

...But that's just me. :)

---

### Post by teet on 2006-10-27
I always try to dist-upgrade my way to the latest ubuntu version, but inevitably I end up doing a fresh install anyway.  I think a lot of the problems with dist-upgrading come from using programs (or compiling) outside of synaptic/apt-get to install things.  You can't really blame the ubuntu folks for that.

As long as you have a separate partition for /home, doing a clean install shouldn't be THAT big of a deal.  All your data and most all your settings should remain intact...all you have to do is reinstall applications/codecs/whatever.  Programs like easyubuntu or automatix make that a breeze.

-teet

---

### Post by Jorge on 2006-10-28
I installed Edgy beta and had a big problem with Evolution: eagerly, it ate all my memory resources (400+ RAM, plus 1.3 Gb of the swap). So I had to wipe out the system and make a fresh install on Dapper again.

Having a very "standard" Dapper installation I took the risk again, as soon as a stable version of Edgy was released (yesterday :)). I downloaded the alternate CD an upgraded right away.

So far (one day) the results are amazing: faster firefox, faster gnome, cleaner looks, better fonts, and an overall best performance. I had my wireless working, sound OK, suspend to RAM much faster...

I believe the secret lies in how "standard" is the version you are upgrading from: if your system has been too much tune-up or hacked, you will have problems. So, for newcomers to Edgy: I suggest a fresh install unless you  haven't change a lot of the original system.

---

### Post by Opsidian on 2006-10-28
I started testing Edgy awhile back and really haven't had to many issues on the T23 ThinkPad, actually have had more things work with Edgy then in Dapper. However it's not called Edgy just because it sounds good, there is a reason that you can't order a Edgy CD at the moment.

---

### Post by SunnyRabbiera on 2006-10-28
I always go for the stable, that way no issues.
unless its in debian, as there all bets are off.

---

### Post by DigitalDuality on 2006-10-28
d

---

### Post by Somniis on 2006-10-28
I, too, had to re-install Dapper in order to upgrade to Edgy.  Not a huge loss, as there wasn't much important on the previous install that I can't redo.  Edgy runs great, now.  :)

---

### Post by Lem on 2006-11-05
My upgrade went quite smoothly. Waited a while after the launch though. Invoked the software upgrade manager rather than traditional apt-get upgrade. (Took about 2 hours on a 3.5Mb pipe)
Only issues were that compiz stopped, but I was going to switch to beryl anyway, and that the fonts get screwed up.
The latter was the most annoying, but I've now cured it (See How-To's)

I spent a few days lamenting the loss of Dapper, but I'm now an Edgy convert.

Boot screens are nice, and there a number of nice little new bits here and there, and totem finally plays widescreen movies at the right aspect ratio on my widescreen monitor.

---

### Post by hoagie on 2006-11-05
I've upgraded using the command given by the ubuntu team, I don't rember it now...Everything worked fine even though it took 14 hours to donwlload and another 2 hours to install the whole distribution. Artwork fine, drivers fine, multimedia fine, stable as rock (that's why I love Linux), memory usage improved and I love the new firefox 8)

---

### Post by hellmet on 2007-01-22
I've always wondered why we had this 6 month cycle.
a 1-1/2 year one would do lots of good for all.
We'd stick to one Release for long enuff to be stable,
and we could also have lots of new features, bug fixes, etc
with each new release. 6months is too less a time to be able
to come up with 'edgy' work

---

