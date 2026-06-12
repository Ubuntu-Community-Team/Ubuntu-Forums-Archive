---
title: "Upgrade to 15.04 is terrible. Avoid."
date: 2015-05-12
forum: Ubuntu, Linux and OS Chat
---

### Post by kmd on 2015-05-12
Hi, 

It's not my habit to rant on forums, but I have no choice after upgrading ubuntu 14.10 to 15.04. It's just terrible. Many programs I regularly use are experiencing problems, and this on two separate computers (!), a dell laptop and a i7 desktop computer. I have been using ubuntu for quite some years now (>10.04), upgrading was always a transparent and a hassle-free process. Until 15.04.

- Boot time is much longer, on both computers.
- Both computers feel much much much slower. 
- Banshee: It will launch but very slow and with sqlite errors (still unresolved)
- Spotify complains about missing libraries (quickly resolved), it will not launch until proper libraries are installed.
- Zim, which I use daily often won't launch, very frustrating, reboot necessary, no errors in terminal, just nothing. On both computers btw.
- There was a problem with the laptop's lid being closed and using external monitors, the laptop went in 'sleep' mode all the time (resolved by modifying some systemd settings)
- Xorg is not very stable, reboot often required after things just 'hang'
- Firefox is feels slower.
- Overall user experience degraded in my view
- Other issues I forget to mention here...

I therefore recommend to avoid upgrading to 15.04.

Kind regards,
Michael

---

### Post by QIII on 2015-05-12
Not a support request.  Moved to Ubuntu, Linux and OS Chat.

It is a bit hasty to assume that your experience reflects the experiences of everyone else.

---

### Post by kmd on 2015-05-12
I'm not assuming anything. I'm merely reproducing my experience with ubuntu, after upgrading to 15.04, which has been much more frustrating than I have ever experienced.
Kind regards.
Michael.

---

### Post by neu5eeCh on 2015-05-12
Seems like a continuation of this:

[http://ubuntuforums.org/showthread.php?t=2276862](http://ubuntuforums.org/showthread.php?t=2276862)

But, yes, I no longer upgrade. Decided against that several iterations ago.

---

### Post by sammiev on 2015-05-12
I will upgrade from one version to another for testing but my main OS is always a fresh install.

I enjoy starting off with a fresh clean install.

---

### Post by craig10x on 2015-05-12
I don't know...i have a toshiba laptop that is about 4 years old with intel graphics and an i3 sandy bridge and on this hardware i clean installed 14.04, upgraded to 14.10 when it went final and now upgraded again to 15.04 and all went 100% perfect with everything intact, running normal, all my data and apps and settings in place and it even cleaned out unnecessary files at the end of the upgrade (last step before re-booting into new system)...so i can't figure why he has so much problems...For me, upgrading has been fantastic...

I always back up my data on an external flash drive and burn an iso of the new version in case of a need to clean install (just as a back up) but never had to use them for these upgrades...they seem to work VERY WELL these days...
What doesn't work as good is when you upgrade using the live iso, i found that could be troublesome...but "in place' upgrading on the hard drive using the Software Updater...fantastic experience so far...

---

### Post by monkeybrain20122 on 2015-05-12
> **VTPoet said:**
> Seems like a continuation of this:

[http://ubuntuforums.org/showthread.php?t=2276862](http://ubuntuforums.org/showthread.php?t=2276862)

But, yes, I no longer upgrade. Decided against that several iterations ago.

+1

---

### Post by monkeybrain20122 on 2015-05-12
> **craig10x said:**
> I don't know...i have a toshiba laptop that is about 4 years old with intel graphics and an i3 sandy bridge and on this hardware i clean installed 14.04, upgraded to 14.10 when it went final and now upgraded again to 15.04 and all went 100% perfect with everything intact, running normal, all my data and apps and settings in place and it even cleaned out unnecessary files at the end of the upgrade (last step before re-booting into new system)...so i can't figure why he has so much problems...For me, upgrading has been fantastic...
.

Yes, but your hardware is not really cutting edge(no offence, mine is around that age) so chances are there won't be a lot surprises. Also you said elsewhere that your setup is as vanilla as possible, no ppa, no proprietary driver, no tweaking config and install everything strict from the USC, that would certainly make upgrading not as problematic.

Also it is still quite early, upgrade or clean install, I will advise waiting about a month before moving to 15.04. I think the only valid reason one would upgrade or use a new release when the first opportunity arises is to file bug reports, but that would be better achieved by installing in a spare hard drive or test partition. :) There are known bugs on launchpad, you are lucky if they don't hit you. Two hit me, one I have workaround,--menu greyed out for some applications e.g vlc,-- posted the workaround to sticky already, the other still not,--synaptic cannot find things from time to time.

---

### Post by craig10x on 2015-05-13
Quite true...well i do use one ppa (Chrome) but i always uncheck it before doing the upgrade... ;)

But yeah, stock ubuntu, no proprietary driver or fancy tweaking...other then changing the size of the icons on the unity dock :D
I'm SURE that has a lot to do with it...but i am going to stick with that "formula" as it seems to work well for upgrading...
I actually usually do it a few days BEFORE the actual final release (in other words, during the last couple of days of development) to avoid the "rush" ;)

---

### Post by jamesdesbyrne on 2015-05-13
Just as a quick aside, I recently went from 14.04 to 15.04 so I thought I'd do out my bullet points.

- It was simple and easy to upgrade (I did a re-install I might add, just wanted to flatten the laptop. Was a bit of a mess buts that's just my file management)
- Its definitely quicker, both the OS and its applications such as Firefox, Android Studio, spotify  etc
- Setting up my development environment was real easy using umake (+1 for that awesome feature)


Overall I've found it to be a major upgrade on 14.04 and I am looking forward to 15.10 to see what it brings :) .

---

### Post by MartyBuntu on 2015-05-13
"upgrade fever"

Honestly, I don't know why most people don't stick with LTS releases.

---

### Post by monkeybrain20122 on 2015-05-13
> **MartyBuntu said:**
> "upgrade fever"

Honestly, I don't know why most people don't stick with LTS releases.

Old and outdated software and the oft repeated advise that the preferred way to upgrade your software would be to upgrade (I mean 'upgrade' in the broad sense including clean install) to a new release.

---

### Post by EmpireITtech on 2015-05-15
As others have stated as well - that's why I *always *just go with a fresh install for any "production" machines. That's the beauty of Linux, fresh installs are so easy =]

I will say that I did a 14.10 > 15.04 upgrade on a laptop that I use for connecting to my TV and downloading movies/music/etc on, and everything worked perfect after reboot so maybe you're just having a bad experience.

---

### Post by benrob0329 on 2015-05-15
I did a fresh install of Ubuntu Mate 15.10 on my (new, middle of the road) laptop. However, when i was running Unity, I did an upgrade. everything worked fine. Unity was just slow on my hardware, so I went with a lighter wait distro.

BTW I'm now using the Cinnamon Desktop.

---

### Post by monkeybrain20122 on 2015-05-15
> **benrob0329 said:**
> I did a fresh install of Ubuntu Mate 15.10 on my (new, middle of the road) laptop. However, when i was running Unity, I did an upgrade. everything worked fine. Unity was just slow on my hardware, so I went with a lighter wait distro.

BTW I'm now using the Cinnamon Desktop.

Is this a typo? You do realise that 15.10 is pre-alpha, right?

---

