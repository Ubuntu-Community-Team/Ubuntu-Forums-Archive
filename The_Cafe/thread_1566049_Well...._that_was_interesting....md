---
title: "Well.... *that* was interesting..."
date: 2010-09-01
forum: The Cafe
---

### Post by neu5eeCh on 2010-09-01
I just completely borked Ubuntu on my small laptop.

Completely.

Noob that I am...

Nothing informative about this post, just thought I'd share that. I just re-installed. Figured that would be quicker that trying to repair whatever the h-ll I did. I tried repairing from LiveCD but was way out of my depth. I remember copying and pasting a couple of commands into my terminal. rm this... rm that...

Doh.

---

### Post by Rasa1111 on 2010-09-01
lol, doh! 

 well it's a lesson at least eh?...
 maybe.. lol

where did you get the commands from?

normally I wont use a command unless it is on a "professional" Ubuntu help site. 

 if youre not sure what it does, just paste it into google first..
that should tell you whether or not you should try it. 

Some people do put codes up to bork ppls systems for the "lulz" *doh!*
But on this forum, and most other Ubuntu help sites, it is not tolerated.

\at least Ubuntu is a breeze to reinstall..
unlike some others... 

 careful young grasshopper... lol

---

### Post by 73ckn797 on 2010-09-01
> **Rasa1111 said:**
> lol, doh! 

 well it's a lesson at least eh?...
 maybe.. lol

where did you get the commands from?

normally I wont use a command unless it is on a "professional" Ubuntu help site. 

 if youre not sure what it does, just paste it into google first..
that should tell you whether or not you should try it. 

Some people do put codes up to bork ppls systems for the "lulz" *doh!*
But on this forum, and most other Ubuntu help sites, it is not tolerated.

 careful young grasshopper... lol

This

---

### Post by KdotJ on 2010-09-01
> **VTPoet said:**
> I just completely borked Ubuntu on my small laptop.

Completely.

Noob that I am...

Nothing informative about this post, just thought I'd share that. I just re-installed. Figured that would be quicker that trying to repair whatever the h-ll I did. I tried repairing from LiveCD but was way out of my depth. I remember copying and pasting a couple of commands into my terminal. rm this... rm that...

Doh.

rm?

Lol yeah, never good news if that goes wrong

---

### Post by neu5eeCh on 2010-09-01
OK, I just remembered. I had just deleted all traces of pulse audio. I then entered the following two commands into the system because I was getting an autoaudiosink error:

rm -rf ~/.gconf/system/gstreamer
rm -rf ~/.gstreamer-0.10

Then I logged off. When I tried to log back in, I kept being returned to the login window. When I tried recovery mode and "startx", I received something like a 693 error. No matter what I did, I couldn't get past the login prompt. 

Meh.

---

### Post by Legendary_Bibo on 2010-09-02
Yeah I messed up plymouth one time because I decided to follow a guide so the plymouth screen wouldn't be in such a low res. I put a resolution in the files my card didn't even support so then at every boot up I was stuck with a black screen.

---

### Post by murderslastcrow on 2010-09-02
The issue with Linux is that it allows so much choice and customization that sometimes we go much further than necessary to tweak it just that tiny bit more to get it perfect.

We are truly fortunate creatures to be afforded such luxury.

---

### Post by mips on 2010-09-02
> **VTPoet said:**
> OK, I just remembered. I had just deleted all traces of pulse audio. I then entered the following two commands into the system because I was getting an autoaudiosink error:

rm -rf ~/.gconf/system/gstreamer
rm -rf ~/.gstreamer-0.10

Then I logged off. When I tried to log back in, I kept being returned to the login window. When I tried recovery mode and "startx", I received something like a 693 error. No matter what I did, I couldn't get past the login prompt. 

Meh.

Be carful when using rm especially with the -f flag. Rather uses rm -ir until you are familiar with rm. Also setup aliases for rm to use -i, -v so it's interactive or verbose. Even better make an alias so it moves files to trash rather than delete then, this way you can restore them easily.

[http://www.thegeekstuff.com/2009/06/how-to-linux-delete-directory-using-rmdir-rm-command/#more-551](http://www.thegeekstuff.com/2009/06/how-to-linux-delete-directory-using-rmdir-rm-command/#more-551)

---

### Post by neu5eeCh on 2010-09-02
> **mips said:**
> Be carful when using rm especially with the -f flag. Rather uses rm -ir until you are familiar with rm. Also setup aliases for rm to use -i, -v so it's interactive or verbose. Even better make an alias so it moves files to trash rather than delete then, this way you can restore them easily.

He said, as the Titanic disappeared beneath the waves. ;)

---

### Post by neu5eeCh on 2010-09-02
> **murderslastcrow said:**
> The issue with Linux is that it allows so much choice and customization that sometimes we go much further than necessary to tweak it just that tiny bit more to get it perfect.

I was just trying to get recordmydesktop to *record sound*. I still have not succeeded. It seems that with Linux, sound recording functionality is still very 1990's, extremely hit or miss. If it works flawlessly on you system, go buy a lotto ticket. If it doesn't, the road will be bloody and bruising.

Here's the weirdest thing though. When I re-installed Ubuntu, I did it twice. The first time, I didn't reformat. The second time, I did. Even though my home folder was on a separate partition, one of the two re-installs "deleted" the contents of my desktop (on a separate partition) but nothing else. However, the contents of my desktop included an 80 Gig library of music from my IPOD. (Fortunately, I keep backups in triplicate.)

But here's where it goes really weird. Even though I could not, for the life of me, recover the desktop folders, disk usage still reported the presence of my music collection. I could not find it, not in trash, nowhere. I even used scalpel, but to no avail. According to the percentage of the disc used, the files were still present?

I eventually reformatted the drive. I only lost half a document. Very little.

---

### Post by TNT1 on 2010-09-02
> **murderslastcrow said:**
> The issue with Linux is that it allows so much choice and customization that sometimes we go much further than necessary to tweak it just that tiny bit more to get it perfect.


...perfect, or just to see what happens...

But yeah, I find myself often having to adjust, re-install, stuff, but my parents, and wife, using exact same version of Ubuntu, never a problem.... I like to fiddle;)

---

### Post by David Andersson on 2010-09-02
> **mips said:**
> Rather uses rm -ir until you are familiar with rm. Also setup aliases for rm to use -i, -v so it's interactive or verbose. Even better make an alias so it moves files to trash rather than delete then, this way you can restore them easily.


**Yes** "rm -i" is a good idea, to feel a bit safer. **But**. No, naming an alias "rm" that does "rm -i" is no good idea. It will bite you bad when you use a system where that alias is not defined. If you want an alias for "rm -i" (or one that moves files to a thrash) name it something else, like "myrm" or "del".

---

### Post by 73ckn797 on 2010-09-03
> **murderslastcrow said:**
> The issue with Linux is that it allows so much choice and customization that sometimes we go much further than necessary to tweak it just that tiny bit more to get it perfect.

We are truly fortunate creatures to be afforded such luxury.


This can get one into many problems that are not inherent with Ubuntu when left alone.

---

### Post by Irihapeti on 2010-09-03
Often the best learning comes from dealing with mistakes.

At least, that's my experience. I find it beats crying about it, anyway :).

---

### Post by Legendary_Bibo on 2010-09-04
I think it's the only way to truly learn how to use Linux. You can follow any amount of guides and what not, but not all of them are universal for anyone, and it takes a bit of screw ups to truly learn from it, and it seems as though you never forget how to fix those problems. You may forget specific commands, but others may remember them.

---

### Post by 73ckn797 on 2010-09-04
> **Irihapeti said:**
> Often the best learning comes from dealing with mistakes.

At least, that's my experience. I find it beats crying about it, anyway :).

It does create opportunities to learn. More when one tinkers.

---

### Post by hotrodder on 2010-09-04
When first starting using Linux I borked and reinstalled so many times I became an expert on installing Linux of all flavors.

---

### Post by neu5eeCh on 2010-09-04
> **73ckn797 said:**
> It does create opportunities to learn. More when one tinkers.

Wish I'd had more time to just fix the problem, but I learned just as much reinstalling 10.04 (which was **not**, contrary to what others have said, blissfully easy or easier than windows). 

I ran into an Ubuntu bug that took me half the night to recognize as a bug. Enabling codecs for mplayer doesn't always work as advertised.

[Bug #543157 in gnome-codec-install (Ubuntu): “Totem can't locate codecs h.264 and mpeg4”]("https://bugs.launchpad.net/ubuntu/+source/gnome-codec-install/+bug/543157") 

I major bug, if you ask me.

The other hiccup was re-installing VirtualBox (needed for my scanner). Christ, that took me another three or four hours. Turns out it isn't enough to add oneself to the *vboxusers* and *lp* groups if one wants to use USB in a virtual XP install. Tucked away in a teeny, tiny corner of the Internet is a suggested third group: *users*. 

Yeah, I know, it's obvious once you know.

I still prefer Linux to Windows - hands down.

---

### Post by wkhasintha on 2010-09-04
I having a [snag with my themes]("http://ubuntuforums.org/showthread.php?t=1560754") since sometimes now. Started threads and no help received , only option left is to reinstall ubu but reinstalling all the softwares will be a nightmare , hence I'm gonna endure till the 10.10 stable release to a new fresh install.

---

