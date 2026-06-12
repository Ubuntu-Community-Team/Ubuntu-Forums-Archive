---
title: "best distro for old laptop"
date: 2009-08-24
forum: The Cafe
---

### Post by terry_gardener on 2009-08-24
i might be installing linux on a old laptop shortly and would like to know which is the best to install. 

system specs that i know of. 

p3 700mhz 
384mb ram 
dont know which sound and video chipsets it has because it is not my laptop.

it will be mainly used for internet (facebook and other normal serving), music. 

the distro has to be easy to use as they have never used linux before, and it needs to be able to run reasonably well, and hopefully debian based as i have only really used ubuntu. 

what would your suggestions be.

---

### Post by Warpnow on 2009-08-24
install a commandline ubuntu and then type

sudo apt-get install lxde wicd

I've used ubuntu + LXDE on a pentium 2 and it was quite snappy. IceWM is also a good option.

---

### Post by &#32 Greg on 2009-08-24
Or instead of a commandline Ubuntu to LXDE, there's the new Masonux.

Personally, I'd run Arch or Crux or Gentoo. Slitaz and TinyCore would also be good choices.

---

### Post by snowpine on 2009-08-24
AntiX is arguably the fastest "out of the box" Debian-based distro. I am also a big fan of CrunchBang. Either of those would "just work" with lots of applications and codecs pre-installed.

If you want to do a minimal install for your friend, use Debian or Ubuntu, it doesn't really matter if you're doing a lightweight windows manager sort of thing. Either Ubuntu+LXDE or Debian+LXDE would be fine with those specs.

Those would be my suggestions if you want to stay under the Debian umbrella.

---

### Post by HappinessNow on 2009-08-24
> **terry_gardener said:**
> i might be installing linux on a old laptop shortly and would like to know which is the best to install. 

system specs that i know of. 

p3 700mhz 
384mb ram 
dont know which sound and video chipsets it has because it is not my laptop.

it will be mainly used for internet (facebook and other normal serving), music. 

the distro has to be easy to use as they have never used linux before, and it needs to be able to run reasonably well, and hopefully debian based as i have only really used ubuntu. 

what would your suggestions be.Macpup Opera or other Puppy variety.

---

### Post by Gen2ly on 2009-08-24
Crunchbang Linux

---

### Post by Hogosha on 2009-08-24
wouldn't this be the definition of a machine ready for Xubuntu?

---

### Post by celthunder on 2009-08-24
I'd suggest arch if you were willing to move outside of the debian based distros, within ubuntu distro's maybe xubuntu XFCE doesn't take much to run.

---

### Post by snowpine on 2009-08-24
> **Hogosha said:**
> wouldn't this be the definition of a machine ready for Xubuntu?

Only if you think Xubuntu is the "best distro for old laptop." ;)

I personally find it not that fast compared with other Xfce distros (Debian, Sidux, Arch, etc).

Interesting comparison: [http://distrowatch.com/weekly.php?issue=20090427#feature](http://distrowatch.com/weekly.php?issue=20090427#feature)

I would absolutely recommend Xubuntu for someone with a fast computer who happens to like Xfce, but not for older hardware.

---

### Post by utnubuuser on 2009-08-24
+1 Crunchbang

or

Sidux XFCE

---

### Post by cmay on 2009-08-24
FreeDOS ,MINIX, puppy linux , damn small linux. vector linux , tiny core. maybe a BSD variant. these are the distributions i install on my oldest computers i fix for the fun of it. anything faster than these on real old hardware i think is hard to come by or maybe too tricky to install for me to bother trying. 

i ran MINX on 100 mzh processor wiht only 16 mb ram once for a whole month before the PC powersupply burned down. i had puppy linux running on a 100 mzh and 32 mb ram but it would not install . it did boot however. slow but it did afterall. 

 for a usable system a bit more ram and more power and puppy or even if it can handle vector or crunch bang is what i would reccomend if the system is powerfull enough. else use windows 95 or one of the other small distros that are light on ressurces. or a hobby OS like minix or FreeDos.  

anythin over 128 mb ram i would just install debian lenny on using lxde or openbox. of the processor is something like from 700 mzh and up. the old computer i use right now i had debian lenny on for long time and it has 600 mzh processor and 128 mb ram and it runs great.

---

### Post by bodhi.zazen on 2009-08-24
Wolvix, SLAX, or Zenwalk =)

IMO these Slackware variants run very nicely on older hardware without the "hassle" of Arch or Gentoo.

The problem with DSL and Puppy linux, although they run fast, they are clunky.

Recently I have enjoyed SliTaz

[http://www.slitaz.org/en/](http://www.slitaz.org/en/)

Nice listing : [http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by murderslastcrow on 2009-08-24
!# (Crunchbang) would work really well with this. However, if you want sheer speed, go for DSL (Damn Small Linux), since it can run on as little as 64 MB of RAM. I have a 112 MB RAM, 600 Mhz PC running like a dream on it. It's comparable to Windows 95 in speed vs processing power.

But a lot more modern than that, obviously. If you take this route, you may want to use the version that includes GTK2 libraries. It's based on Debian, and will require minimal text-based work to get installed on the hard drive.

---

### Post by crystal88_ on 2009-08-24
try fluxubuntu... worth trying, just give it a go. (I mean fluxubuntu and not ubuntu + fluxbox.. the first one is said to be faster)

---

### Post by Muppeteer on 2009-08-24
I'd say stick arch over ubuntu. Not to start a war or anything, but ubuntu is getting a bit bloated. Better off with a minimal install and only have what you need. Then build a custom kernel to keep the resources low.

---

### Post by snowpine on 2009-08-24
> **crystal88_ said:**
> try fluxubuntu... worth trying, just give it a go. (I mean fluxubuntu and not ubuntu + fluxbox.. the first one is said to be faster)

Bad choice... Fluxbuntu is based on Ubuntu 7.10 (Gutsy) which has reached its "end of life" and is no longer supported. No security updates, and the repositories are closed. AntiX is similar, but is still an active project.

---

### Post by Dr. C on 2009-08-24
I would actually try Ubuntu seriously.

---

### Post by kk0sse54 on 2009-08-24
Crux :twisted:

Edit: Scratch that, I wouldn't classify crux as easy to use. Perhaps Slitaz or Debian Lxde?

---

### Post by Grifulkin on 2009-08-24
I have an older laptop, not as old as yours and mine runs Ubuntu just fine.  But what I would do personally, minimal install then install lxde, and chrome for a browswer and wicd for a network manager, so there aren't any gnome dependencies and build it up from there, and it should run very smothly.

---

### Post by cascade9 on 2009-08-24
> **snowpine said:**
> Only if you think Xubuntu is the "best distro for old laptop." ;)

I personally find it not that fast compared with other Xfce distros (Debian, Sidux, Arch, etc).

Interesting comparison: [http://distrowatch.com/weekly.php?issue=20090427#feature](http://distrowatch.com/weekly.php?issue=20090427#feature)

I would absolutely recommend Xubuntu for someone with a fast computer who happens to like Xfce, but not for older hardware.

 +1. I've got a p3-866 with 384MB and its not as fast with xubuntu on it as it was with debian Xfce. I dont use it that much, but my flatmate, who does, complains about flash performance in particular, and general slugishness.

---

### Post by terry_gardener on 2009-08-25
i would like to thank everyone for there suggestions.

---

