---
title: "distro recomendation for 42MB PowerPC MAC"
date: 2010-07-10
forum: The Cafe
---

### Post by goseph on 2010-07-10
Hi guys!

I am looking for a reasonably simple to get up and running GNU or BSDish distro that will work on an ancient PowerBook 1400CS (42 MB RAM).

I have looked around and seen Puppy Linux as a possibility but apparently that is not really designed for permanent dual booting HD install (I'd like to keep the old Mac OS).

Any other interesting ideas?

Here she is for further details, if interested: [http://www.everymac.com/systems/apple/powerbook/stats/mac_powerbook1400cs_117.html](http://www.everymac.com/systems/apple/powerbook/stats/mac_powerbook1400cs_117.html)

---

### Post by acreeth on 2010-07-10
Well, you need to find a distro that supports PowerPC, which will be the hardest part by far.  I doubt there are any distros left that actively support it, since all macs have used intel for a number of years now.  Sorry this isn't much help, maybe someone else knows an old PowerPC distro that might work. Between the low specs and PPC processor I think it's going to be a nightmare.

---

### Post by NightwishFan on 2010-07-10
Debian Stable. Though 42mb is a bit steep, I would ensure you install a bare window manager like Fluxbox and not a whole desktop environment. (When you get to the package selector in the installation push "space" to disable installing the Desktop Environment. Then when done, log in to the command line and run:
```
sudo aptitude install slim xorg fluxbox xterm midori
```

---

### Post by Redo on 2010-07-10
I'd still stick with the Puppy Linux idea, it'll run better than any distro you'll find with those specs. I'm not sure about the specific install process, but the Puppy installer does use GRUB if I'm not mistaken. So a quick partition resize and you should be set to dual boot from the hard drive.

I used to run it on my grandma's Pentium based system. But with 42 megs of ram even puppy may weep a little bit :p. You won't find a better option though.

---

### Post by NightwishFan on 2010-07-10
Got Debian to run in 64mb of ram (on i386) but not 32, so somewhere between there is the limit.
[http://ubuntuone.com/p/9GE/](http://ubuntuone.com/p/9GE/)

---

### Post by 3rdalbum on 2010-07-10
NOTE: Please, nobody suggest Puppy, DSL, Tiny Core or any distribution that is not compiled for PowerPC!

That amount of RAM is going to be a problem. NetBSD or Debian, stripped to the bone with a light window manager, may just be able to run. You could almost certaibly have a CLI system on that anyway,

---

### Post by Redo on 2010-07-10
> **3rdalbum said:**
> NOTE: Please, nobody suggest Puppy, DSL, Tiny Core or any distribution that is not compiled for PowerPC!

Sorry about that! I had assumed (incorrectly) Puppy Linux was compiled for PPC based on the op's assertion that he was considering it. Even though I had used Puppy quite a bit for a few months last year, I never thought twice about seeing if it was PPC friendly too.

---

### Post by MasterNetra on 2010-07-10
Found a list. Maybe this might help ya?

[http://penguinppc.org/about/distributions.php](http://penguinppc.org/about/distributions.php)

Update: Hmm maybe not what doesn't seem to be anything that will run on it.

Also side note why don't you donate that to a museum and at least get this: 

[http://www.amazon.com/Apple-iBook-Laptop-600-MHz-PowerPC/dp/B00005RI8Q/ref=sr_1_15?s=pc&ie=UTF8&qid=1278816418&sr=1-15](http://www.amazon.com/Apple-iBook-Laptop-600-MHz-PowerPC/dp/B00005RI8Q/ref=sr_1_15?s=pc&ie=UTF8&qid=1278816418&sr=1-15)

or you can cough up another hundred or so for a used:

[http://www.amazon.com/Apple-MacBook-MB881LL-13-3-Inch-Laptop/dp/B001QCWQNK/ref=sr_1_17?s=pc&ie=UTF8&qid=1278816418&sr=1-17](http://www.amazon.com/Apple-MacBook-MB881LL-13-3-Inch-Laptop/dp/B001QCWQNK/ref=sr_1_17?s=pc&ie=UTF8&qid=1278816418&sr=1-17)

---

### Post by forrestcupp on 2010-07-10
How about TheDumpOS?  ;)

---

### Post by sandyd on 2010-07-10
> **forrestcupp said:**
> How about TheDumpOS?  ;)
:lolflag:

---

### Post by stmiller on 2010-07-10
Typical old world mac installs require a macos install disc to setup bootx. As in MacOS 9 disc. It's sort of a nightmare but possible.

[http://penguinppc.org/bootloaders/bootx/](http://penguinppc.org/bootloaders/bootx/)

---

### Post by goseph on 2010-07-12
Wow thanks for the response guys!

I think I will probably give the Debian install a go, I am quite excited about the possibility of getting the mighty Debian rolling on this hunk of iron. Thanks for the Bootx tip as well - I will post back here if it works :)

One question about Debian - would it be worth using an older version of Debian than the current stable, just for the potentially lower hardware requirements? I speculate wildly that the Debian written 10 years ago say would be more sparing with memory than Lenny. Or is installing an unsupported OS just crazy talk?

Goseph

---

### Post by ibuclaw on 2010-07-12
Have a look at this link:
[http://distrowatch.com/search.php?architecture=powerpc](http://distrowatch.com/search.php?architecture=powerpc)

That's probably the most comprehensive list you'll find.

Regards. :)

---

### Post by ibuclaw on 2010-07-12
> **Redo said:**
> Sorry about that! I had assumed (incorrectly) Puppy Linux was compiled for PPC based on the op's assertion that he was considering it. Even though I had used Puppy quite a bit for a few months last year, I never thought twice about seeing if it was PPC friendly too.

You were probably thinking about Yellow Dog Linux...

---

### Post by NightwishFan on 2010-07-12
Personally I would use the current stable one, but yes, the older Debian may be much lighter on resources.

---

### Post by Shining Arcanine on 2010-07-12
> **goseph said:**
> Hi guys!

I am looking for a reasonably simple to get up and running GNU or BSDish distro that will work on an ancient PowerBook 1400CS (42 MB RAM).

I have looked around and seen Puppy Linux as a possibility but apparently that is not really designed for permanent dual booting HD install (I'd like to keep the old Mac OS).

Any other interesting ideas?

Here she is for further details, if interested: [http://www.everymac.com/systems/apple/powerbook/stats/mac_powerbook1400cs_117.html](http://www.everymac.com/systems/apple/powerbook/stats/mac_powerbook1400cs_117.html)
Try Gentoo Linux. It should work well after the system has compiled. If you do not want to wait for your PowerPC to compile its own software, you could speed-up the compilation process by using distcc:

[http://www.gentoo.org/doc/en/distcc.xml](http://www.gentoo.org/doc/en/distcc.xml)

---

### Post by Old_Grey_Wolf on 2010-07-12
I had a G3 PPC MAC a few years ago. I got a Linux OS to run on it. At that point, it looked good.

Then I started trying to find applications to make it useful for my grandchildren. For example, I tried to find a flash player that would run on the PCC version of the OS. I couldn't find one at the time. Flash was an important application for them. They needed it for on-line games, cartoon network shows, and so forth. 

Like all OS selections, you need to look at the supported applications, or their alternatives. 

It has been a few years since I played with a PPC MAC; however, I doubt the the problem with application support has gone away. 

Anyway, have fun. Enjoy learning from your experience. :)

---

### Post by jerenept on 2010-07-12
> **Shining Arcanine said:**
> Try Gentoo Linux. It should work well after the system has compiled. If you do not want to wait for your PowerPC to compile its own software, you could speed-up the compilation process by using distcc:

[http://www.gentoo.org/doc/en/distcc.xml](http://www.gentoo.org/doc/en/distcc.xml)

Good call... though it may be easier to buy a new computer

---

### Post by Shining Arcanine on 2010-07-13
> **Old_Gray_Wolf said:**
> I had a G3 PPC MAC a few years ago. I got a Linux OS to run on it. At that point, it looked good.

Then I started trying to find applications to make it useful for my grandchildren. For example, I tried to find a flash player that would run on the PCC version of the OS. I couldn't find one at the time. Flash was an important application for them. They needed it for on-line games, cartoon network shows, and so forth. 

Like all OS selections, you need to look at the supported applications, or their alternatives. 

It has been a few years since I played with a PPC MAC; however, I doubt the the problem with application support has gone away. 

Anyway, have fun. Enjoy learning from your experience. :)

You could try Gnash or Lightspark for that:

[http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)
[http://en.wikipedia.org/wiki/Lightspark](http://en.wikipedia.org/wiki/Lightspark)

Neither is perfect, but it is better than nothing.

---

### Post by Old_Grey_Wolf on 2010-07-14
> **Shining Arcanine said:**
> You could try Gnash or Lightspark for that:

[http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)
[http://en.wikipedia.org/wiki/Lightspark](http://en.wikipedia.org/wiki/Lightspark)

Neither is perfect, but it is better than nothing.

I tried gnash but it didn't work well enough. Lightspark didn't exist back when I had a PPC, and I think it is still in Beta at this time.

The OP may be able to use them though. :)

---

