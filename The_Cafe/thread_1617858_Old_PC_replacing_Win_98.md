---
title: "Old PC: replacing Win 98"
date: 2010-11-09
forum: The Cafe
---

### Post by ubunterooster on 2010-11-09
Okay, I'm being handed an old PC that I will stick Linux on. The problem is I have to share it with a 15 year old cousin. I know many OSs that would work on this PC, but I need it to also be usable for someone that is not tech-minded. 


```
IBM Aptiva
4GB hard drive
184MB RAM
450 Mhz
```
I have used Lubuntu, Legacy, Puppy, Quirky, antiX, and Toutou Linux
in the past. If you have alternatives or opinions, they would be appreciated.

---

### Post by pricetech on 2010-11-09
I haven't used Lubuntu, but I understand it's lightweight so I'd probably try it since it's a derivative.

Puppy would get my vote though.  I've used it on old boxen before and always been pleased.  The interface is kinda plain, but it usually just plain works.

Good luck and have fun with it whatever you decide.

---

### Post by Austin25 on 2010-11-09
[Tinycore]("http://www.tinycorelinux.com/")?

---

### Post by ubunterooster on 2010-11-09
> **pricetech said:**
> I haven't used Lubuntu, but I understand it's lightweight so I'd probably try it since it's a derivative.

Puppy would get my vote though.  I've used it on old boxen before and always been pleased.  The interface is kinda plain, but it usually just plain works.

Good luck and have fun with it whatever you decide.
The saving on shutdown makes puppy (and variants) a bit awkward for everyday use for most people, IMO.

---

### Post by sidzen on 2010-11-09
[[SIZE=3]Zenwalk[/SIZE]]("http://www.zenwalk.org")  fits the bill.  Must, repeat, [COLOR=Red]must[/COLOR] prepare the hard drive by writing zeros to it prior to install.  Standard or Core (do not use Live).
Max out the RAM.
Best wishes!

---

### Post by ubunterooster on 2010-11-09
> **Austin25 said:**
> [Tinycore]("http://www.tinycorelinux.com/")?
That might work; depending on how I connect to internet.

---

### Post by TriBlox6432 on 2010-11-09
SliTaz.

---

### Post by smellyman on 2010-11-09
[AntiX]("http://antix.mepis.org/index.php?title=Main_Page")

---

### Post by ubunterooster on 2010-11-09
> **sidzen said:**
> [[SIZE=3]Zenwalk[/SIZE]]("http://www.zenwalk.org")  fits the bill. I haven't tried Zenwalk in a *long* time; I liked it >  Must, repeat, [COLOR=Red]must[/COLOR] prepare the hard drive by writing zeros to it prior to installWait, I don't remember ever having to do that. How do I?

---

### Post by kaldor on 2010-11-09
> **ubunterooster said:**
> 
IBM Aptiva
4GB hard drive
184MB RAM
450 Mhz


OpenSuSE with KDE 4.5 of course.

---

### Post by floborg on 2010-11-09
I first starting using Linux on a Windows 98 (1st Ed) machine from 1998.  This was 3 years ago, and Puppy functioned quite well.  This machine had a 400 MHz PII processor w/224 MB of RAM.  Too little RAM for the whole base squash file to get copied to RAM, but the OS was in no way bogging down the system.

With Puppy, you have the added benefit of not having to repartition or reformat your whole hard drive.  You can install one of the XFCE SFS files to make the desktop environment more friendly to your cousin.

---

### Post by Austin25 on 2010-11-09
> **ubunterooster said:**
> Wait, I don't remember ever having to do that. How do I?
Here. 
[COLOR=Red][SIZE=4]DO NOT TRY THIS ON YOUR DESKTOP!!!
DO NOT EVEN USE IT ON AN INSTALLED ENVIRONMENT.[/SIZE]
[COLOR=Black]This is meant specifically for writing zeros to the hard drive. It will wreck it if you still have anything on there.
[/COLOR][/COLOR]```
sudo dd if=/dev/zero of=/dev/sda
```

---

### Post by TNT1 on 2010-11-10
> **smellyman said:**
> [antix]("http://antix.mepis.org/index.php?title=main_page")

+1

---

### Post by ubunterooster on 2010-11-10
> **Austin25 said:**
> Here. 
[COLOR=Red][SIZE=4]DO NOT TRY THIS ON YOUR DESKTOP!!!
DO NOT EVEN USE IT ON AN INSTALLED ENVIRONMENT.[/SIZE]
[COLOR=Black]This is meant specifically for writing zeros to the hard drive. It will wreck it if you still have anything on there.
[/COLOR][/COLOR]```
sudo dd if=/dev/zero of=/dev/sda
```
Thank-you for the command and info

---

### Post by ubunterooster on 2010-11-10
> **smellyman said:**
> [AntiX]("http://antix.mepis.org/index.php?title=Main_Page")
Will look into that

---

### Post by ubunterooster on 2010-11-10
> **kaldor said:**
> OpenSuSE with KDE 4.5 of course.
Sure! I'll try it first! :lol:

---

### Post by Austin25 on 2010-11-10
> **ubunterooster said:**
> Thank-you for the command and info
Sorry, I needed to put a disclaimer on there for anybody who came across it. It's in the Code of Conduct. I shouldn't have even posted that command if you didn't need it.

---

### Post by lykwydchykyn on 2010-11-10
In the interest of locating a suitable distro, I wonder what do you and your cousin actually plan to DO on this computer?  Web browsing?  Email? Games?  Homework?  Hacking into the DOD?

Pretty much any distro, once properly installed and configured, is more or less easy to *use*.  It's the maintenance/configuration/installation part that varies.

That said, tinycore is fast and a lot of fun to hack around on, though the repositories are kind of rudimentary.

---

### Post by ubunterooster on 2010-11-10
> **lykwydchykyn said:**
> In the interest of locating a suitable distro, I wonder what do you and your cousin actually plan to DO on this computer?  Web browsing?  Email? Games?  Homework?  Hacking into the DOD?

Pretty much any distro, once properly installed and configured, is more or less easy to *use*.  It's the maintenance/configuration/installation part that varies.

That said, tinycore is fast and a lot of fun to hack around on, though the repositories are kind of rudimentary.
The maintenance/configuration of tiny core is not what I think is at all simple. The PC will be used for Word processing and likely light online games

---

### Post by teet on 2010-11-10
I would suggest windows 98 with the most recent version of internet explorer it will support :)

I am only sort of kidding...I've installed many a "light" distro in my day and never found any as functional as windows 98.  The problem with these old machines always seems to be the lack of ram needed to run modern browsers...although I don't think any of my "old" machines had 184 mb of ram.

-teet

---

### Post by ubunterooster on 2010-11-10
I have been given the impression that the PC already is known to have malware in it. And without install discs I would rather just install putting Linux on it. (And I'm not going to mention how much I adore all MS products {except keyboards; I like MS keyboards} )

---

### Post by NightwishFan on 2010-11-10
I give my vote to Puppy. It packs a wallop. Or Debian Stable with xfce/lxde. (I would say fluxbox, however you will have manually configure start-up programs such as nm-applet or wicd (recommended))

---

### Post by ubunterooster on 2010-11-10
Puppy seems to be the likely winner for now.

---

### Post by TNT1 on 2010-11-10
> **smellyman said:**
> [AntiX]("http://antix.mepis.org/index.php?title=Main_Page")

> **ubunterooster said:**
> Will look into that

Try it, it's built on mepis/debian stable, anmd I've had it running in a workable way on a PII with only 64mb RAM... I now have a PIV with 512mb RAM, that was running win 95 running antix. (oh and you can run kde/gnome/whatever on antix as well...

---

### Post by ubunterooster on 2010-11-10
AntiX and Puppy are the likely candidates. I'll see how they work when the PC arrives

---

### Post by cpmman on 2010-11-10
Persistent Puppy crows.

```
crow 2  (kr)
intr.v. crowed, crow·ing, crows
1. To utter the shrill cry characteristic of a **** or rooster.
2. To exult loudly, as over another's defeat; boast. See Synonyms at boast1.
3. To make a sound expressive of pleasure or well-being, characteristic of an infant.
n.
1. The shrill cry of a ****.
2. An inarticulate sound expressive of pleasure or delight.
```

---

### Post by TeoBigusGeekus on 2010-11-10
I know I'm a bit late, but consider Arch as well.
I have a P4 at 3GH with 1Gb of ram in which I'm using Arch with Openbox(standalone): after boot up, htop reports 3% cpu usage and 7% (70MBs) ram usage.

---

### Post by ubunterooster on 2010-11-10
> **cpmman said:**
> Persistent Puppy crows.

```
crow 2  (kr)
intr.v. crowed, crow·ing, crows
1. To utter the shrill cry characteristic of a **** or rooster.
2. To exult loudly, as over another's defeat; boast. See Synonyms at boast1.
3. To make a sound expressive of pleasure or well-being, characteristic of an infant.
n.
1. The shrill cry of a ****.
2. An inarticulate sound expressive of pleasure or delight.
```
*presses like*

---

