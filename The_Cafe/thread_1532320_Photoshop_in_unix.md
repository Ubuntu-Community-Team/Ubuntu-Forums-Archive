---
title: "Photoshop in unix"
date: 2010-07-16
forum: The Cafe
---

### Post by ofde on 2010-07-16
Could someone explain me why there is Photoshop for Mac and not for linux? If I am not wrong, mac is a system comes from Unix, too.
Greetings.

---

### Post by nothingspecial on 2010-07-16
Mac does come from unix

Linux is unix like

adobe haven`t made one

Hope that clears it up

---

### Post by RiceMonster on 2010-07-16
The actual graphics and windowing system you see on Mac OSX is proprietary and not available on any other OS. So really, an OSX app cannot run on Linux.

As for why there is no Linux version, Adobe probably simply does not see any value or real chance of earning profits from a Linux version due to the low usage of it on the desktop, and the cost of developing and supporting it.

---

### Post by forrestcupp on 2010-07-16
> **RiceMonster said:**
> The actual graphics and windowing system you see on Mac OSX is proprietary and not available on any other OS. So really, an OSX app cannot run on Linux.

That.

1. MacOS X is not Unix - just a small part of it is

2. Linux is not Unix.

---

### Post by Dustin2128 on 2010-07-16
meh, you can probably run it in wine or a vm if you really need it. When you must pay 400$ for photo editing software, there's adobe. For everything else, there's gimp.

---

### Post by bug67 on 2010-07-16
I love GIMP!  The path tool works so buch better than in PS for me.  And check this, I have GIMP running on my OS X boxes under X 11.  :P

---

### Post by samalex on 2010-07-16
Actually I always wondered this because Adobe Photoshop 3.0 was available for Unix in the mid-90s.  Here's an article from Business Wire, Aug 8, 1995 announcing it:
[http://www.thefreelibrary.com/Adobe+Announces+Adobe+Photoshop+3.0+for+Silicon+Graphics+Workstations...-a017146573](http://www.thefreelibrary.com/Adobe+Announces+Adobe+Photoshop+3.0+for+Silicon+Graphics+Workstations...-a017146573)

> Adobe Announces Adobe Photoshop 3.0 for Silicon Graphics Workstations and Sun SPARC/Solaris Workstations; New Version Allows Designers to Utilize the Power of their UNIX Systems Throughout the Entire Image Editing and Production Process.

So they used to offer it for Unix, so why not Linux now?  There's surely more Linux users now who'd buy Photoshop then Unix users who would've bought it in 1995.  Granted it was $995 back then, but still...  

Sam

---

### Post by yaaarrrgg on 2010-07-16
I have heard that barns used to be painted red because red barn paint was the cheapest.  Red barn paint was the cheapest, because it was the most common color for barns.  It's a circularity in the markets.  :)

---

### Post by lisati on 2010-07-16
> **samalex said:**
> Actually I always wondered this because Adobe Photoshop 3.0 was available for Unix in the mid-90s.  Here's an article from Business Wire, Aug 8, 1995 announcing it:
[http://www.thefreelibrary.com/Adobe+Announces+Adobe+Photoshop+3.0+for+Silicon+Graphics+Workstations...-a017146573](http://www.thefreelibrary.com/Adobe+Announces+Adobe+Photoshop+3.0+for+Silicon+Graphics+Workstations...-a017146573)



So they used to offer it for Unix, so why not Linux now?  There's surely more Linux users now who'd buy Photoshop then Unix users who would've bought it in 1995.  Granted it was $995 back then, but still...  

Sam

Maybe they haven't ported it from Unix to Linux yet. Although Unix provided some of the initial inspiration, Linux and Unix aren't the same thing.

---

### Post by murderslastcrow on 2010-07-16
Most versions of Photoshop work fairly well in Wine. It'd probably be more profitable to focus on Adobe's compatibility in Wine and get it perfect. Then Adobe won't even have to go to the trouble of developing for Linux to get Linux share.

However, if Adobe officially supported Linux, that would be ideal, and it may be coming soon as Adobe is aware of and supports Linux with many of its products already.

However, if you have enough RAM to devote to it, Adobe products perform fairly well in Virtual Machines. Again, if it's just Photoshop you want, GIMP's probably going to cover you outside of non-destructive layer effects and CMYK support (it has CMYK separation for when you're done, but not as you go, so whatever you think is more important).

Of course, there's always Pixel.

---

### Post by Cam! on 2010-07-16
I would love to see a Linux-native version of Photoshop, but realistically, it won't happen. At the same time, I don't understand why people think GIMP is a worthy alternative.

---

### Post by 4hm on 2010-07-16
GIMP is only a worthy alternative when you spend the time to set it up the way you would like it.  There are a lot of plugins that you can add to GIMP to get it up to par with photoshop.  I'm running both GIMP and PS on my Macbook Pro, and I hardly ever use PS.  My project files are almost completely .xcf

GNU/Linux is not UNIX.  If you look-up Linux Torvolds and Richard Stallmen you'll see why.

Adobe is almost the antithesis of what both of them were looking to create.  They are a corporation who pays programmers to write programs the code of which they put under lock-n-key.  That might be the reason they don't put out a Linux version, but I prefer to think of it as why Linux users would prefer that they didn't.

---

### Post by mamamia88 on 2010-07-17
isn't one of the main reasons apple is as sucessful as it is because of early parnterships with adobe?

---

### Post by lykwydchykyn on 2010-07-17
Not that I'm an expert on porting applications, but considering that the Photoshop code base has, during its history, supported:
 - Mac OS classic
 - Solaris
 - Irix
 - DOS-based Windows
 - NT-based Windows
 - OS X

And currently supports the latter two (which are exceptionally disparate platforms), I would have to conclude that either the majority of the code base is platform-neutral or the coders at Adobe are masochists.

I'm not saying I could port the thing in a weekend, but I suspect that a multi-billion-dollar company could put a few of its 8660 employees to work on it and have it ready in a reasonable amount of time, if it wanted to.

---

### Post by forrestcupp on 2010-07-17
> **mamamia88 said:**
> isn't one of the main reasons apple is as sucessful as it is because of early parnterships with adobe?It's kind of ironic that they're totally snubbing them with Flash now.

> **lykwydchykyn said:**
> 
I'm not saying I could port the thing in a weekend, but I suspect that a multi-billion-dollar company could put a few of its 8660 employees to work on it and have it ready in a reasonable amount of time, if it wanted to.
They could, but they probably wouldn't even make back the money they spent to have a few devs port it.  

One thing you're not thinking about is that it doesn't just end with a simple port.  As soon as they port it, immediately they have to start offering continued support for it that will never end.  They'll have to constantly test, develop patches and updates, and start the process all over when an upgrade comes out.  Porting software requires a huge commitment and dedicating a team of devs specifically for that port.  There's no way they'd make their money back when it came to all that.

They *could* do it, but they won't.  Just remember what it took for them just to have a port of the Flash player.  Photoshop is much, much more complicated than a Flash player.

---

### Post by donkyhotay on 2010-07-17
> **forrestcupp said:**
> They *could* do it, but they won't.  Just remember what it took for them just to have a port of the Flash player.  Photoshop is much, much more complicated than a Flash player.

And adobe doesn't offer phone support for flash player on *any* OS which makes it less of a risk for them since that applies to linux as well. Even without worrying about support they didn't want to do a linux port for some time.

---

### Post by ST3ALTHPSYCH0 on 2010-07-17
There are other things here that appear to be overlooked. 
 NT based windows and OSX platforms have some continuity through the lines, so there's not a lot of recoding to support the next release (i.e. most thinigs that run on XP will run on 7, drivers excluded; most things from leopard (I assume) will run on snow leopard) just to offer binaries to cover most of the Linux user based they'd have to release .deb *and* .rpg; then there's no guarantee that it would work on all distros... and someone who's paid hundreds for software is going to expect it to work, and will demand support if it doesn't. That's another thing, how many users who insist on a free OS and free office productivity software are going to *pay* for graphics software?
End result: there's not enough potential user base for the amount of effort and money to be expended.

---

### Post by forrestcupp on 2010-07-17
> **ST3ALTHPSYCH0 said:**
> just to offer binaries to cover most of the Linux user based they'd have to release .deb *and* .rpg; then there's no guarantee that it would work on all distros... and someone who's paid hundreds for software is going to expect it to work, and will demand support if it doesn't.

I agree with the heart of what you're saying, but there are ways around this particular point.  They could just make a .run script that will install all of the binaries, files, and included dependencies into the /home folder.  That way, they can be ignorant of all directory structures and dependencies.

Doing it that way isn't as nice as being distro specific, but you could have one installer that would work on any distro.  They would just have to compile separate binaries to work on the different architectures, like 32-bit, 64-bit, etc.

But you're definitely right that they wouldn't be able to recupe the money they would invest into it.

---

### Post by lykwydchykyn on 2010-07-17
> **forrestcupp said:**
> It's kind of ironic that they're totally snubbing them with Flash now.


They could, but they probably wouldn't even make back the money they spent to have a few devs port it.  

One thing you're not thinking about is that it doesn't just end with a simple port.  As soon as they port it, immediately they have to start offering continued support for it that will never end.  They'll have to constantly test, develop patches and updates, and start the process all over when an upgrade comes out.  Porting software requires a huge commitment and dedicating a team of devs specifically for that port.  There's no way they'd make their money back when it came to all that.

They *could* do it, but they won't.  Just remember what it took for them just to have a port of the Flash player.  Photoshop is much, much more complicated than a Flash player.

I'm sure we can all agree it's probably not feasible from a business standpoint right now; but my point is that, if it became worthwhile I suspect transporting this codebase to yet another platform won't be a technical impossibility.

---

### Post by forrestcupp on 2010-07-18
> **lykwydchykyn said:**
> I'm sure we can all agree it's probably not feasible from a business standpoint right now; but my point is that, if it became worthwhile I suspect transporting this codebase to yet another platform won't be a technical impossibility.

Yeah, if it became worthwhile to them, I'm sure they could probably get something out pretty quickly.  I agree with that, Liquid Chicken. ;)

---

### Post by samalex on 2010-07-19
> **lisati said:**
> Maybe they haven't ported it from Unix to Linux yet. Although Unix provided some of the initial inspiration, Linux and Unix aren't the same thing.

Linux <> Unix, this I know...  my point was that at one time Adobe ported Photoshop to operating systems that didn't have a majority of the OS market share, so why not now.  I can't help but think Unix users were a very small percent of those who bought Photoshop in 1995, but today I can see many Linux users buying a Linux version of Photoshop if it were available (I would...).  I could also see more graphic and web design shops switching to Linux if Photoshop were available for it.

Don't get me wrong, I like Gimp, but for me and others who have 10+ years of experience on Photoshop it would be nice to have it as an option.

Sam

---

### Post by Junkieman on 2010-07-19
> **ofde said:**
> Could someone explain me why there is Photoshop for Mac and not for linux? If I am not wrong, mac is a system comes from Unix, too.
Greetings.

Spend some time to learn GIMP. Sure the floating window layout seems strange coming from the PS MDI interface, but once used to the layout, you focus on the power of the tools, and that's when GIMP really shines!

The docs ([http://docs.gimp.org/2.6/en/](http://docs.gimp.org/2.6/en/)) are great to learn the GIMP, pick a section that interests you and have fun :D

---

