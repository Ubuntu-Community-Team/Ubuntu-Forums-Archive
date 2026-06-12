---
title: "Linux for aging hardware eh? meh....."
date: 2007-12-14
forum: Testimonials &amp; Experiences
---

### Post by jabeez on 2007-12-14
Well being the local/family IT guy, I've got a decent supply of older towers and components. Recently my old roommate was looking for a computer to do just the very basic surfing/music/video/email, and I thought for sure I could cobble up a decent enough Linux-run machine that would cost him next to nothing. Well, the best I could come up with was a Celeron 1.2 Ghz with 256 ram and a 3dfx video card (even though I have 768 MB of ram that is somehow incompatible with these POS Dell/HP machines). Anywho, I thought for sure a lighter-weight 'Buntu would run fine on such a machine, but alas getting any recent version to even boot proved to be a chore. I finally got Geubuntu installed on a Celeron 800 with 192 ram, but even though it is supposed to be great on aging machines, it is SLOOOWWWWW (can't even watch YouTube vids).

Well, sorry for the rant but after spending a whole night on trying to get ONE machine up and running to a decent degree and failing miserably, I am just left wondering, is there something I'm missing or is Linux getting to the point where you really need a modern'ish machine to run decently? I didn't have high hopes from 2 old Celeron based machines, but seriously, this seemed the perfect opportunity to advance Linux as the OS for old hardware, but it looks like I should just install XP and have it be sluggish AND work/have 3D. I guess I could go the Slackware/Arch/build-from-scratch and maybe do better, but for as much time as it would take to get such installed and useable, we'd be better off just buying new hardware. Any thoughts?

---

### Post by kpkeerthi on 2007-12-14
Well. Geubuntu is GNOME+E17 blended seamlessly. So I would say it is probably not the lightest.
I would suggest Arch + fluxbox if you can setup-from-scratch. Its not hard. Refer to the Beginners guide in the wiki. First time it took me a good 5 hours to setup my laptop with all the packages I need for a "desktop" everyday use. But I hardly took 2 hours to transform my desktop with Arch.

If you want more out-of-the-box experience with the goodness of ubuntu, try fluxbuntu.

---

### Post by drummingpariah on 2007-12-14
There's also xubuntu, which includes the same apps and kernel, but with xfce as the window manager.

Try disabling sounds, and see exactly what vid drivers you're using.  Most of the time, one of those two is the reason for slowness.  It could also be bad ram, or an improperly setup swap.

---

### Post by Rhubarb on 2007-12-14
I'm running fluxbuntu on an old Celeron 566MHz 512MB RAM machine at the moment.  Once it's up and running it goes very fast.  I think it should be able to run with less than 256MB of RAM no problems.
[http://www.fluxbuntu.org/](http://www.fluxbuntu.org/)

---

### Post by Perfect Storm on 2007-12-14
I agree with the others. You have to pick the right Distro and/or DE/WM which aimed (can) to run on low specs computers.

If you checked the minimum requirements for Ubuntu/kubuntu, you wouldn't waisted your time ;)

minimum requirements for Ubuntu/kubuntu;

    *  700 MHz or better processor
    * 3GB of available disk space
    * 256MB of memory (RAM)
    * CD-ROM drive
    * Ethernet interface
    * VGA graphics interface 

minimum requirements for Xubuntu;

    *  500 MHz or better processor
    * 1.5GB of available disk space
    * 192MB of memory (RAM) for installation but only 128 MB of RAM to run from the installation CD
    * CD-ROM drive
    * Ethernet interface
    * VGA graphics interface 

Also choosing the right lightweighted libs will have an impact.

Damn small linux could also be an option. [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by chewearn on 2007-12-14
Well, I have Ubuntu in a Celeron PC for a year now; it's slow, but not to the point of being unusable.  It used to run Windows 2000; ubuntu is less clunky though I have kept most things at default, like the wallpaper, themes, etc.
```

    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 247MB
     *-cpu
          product: Intel(R) Celeron(TM) CPU                1000MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.11.1
          size: 1150MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci
          description: Host bridge
          product: VT8601 [Apollo ProMedia]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8601 [Apollo ProMedia AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: CyberBlade/i1
                vendor: Trident Microsystems
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 6a
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=32

```

---

### Post by Perfect Storm on 2007-12-14
RAM is essential, AstalaVista. That's why your runs better than his.

---

### Post by gn2 on 2007-12-14
I had no end of problems trying to get Xubuntu 7.10 running acceptably on my PIII laptop. (500mhz 192mb RAM)
The laptop just wouldn't play nice on 7.10 so I replaced it with Xubuntu 7.04 which runs much better.

Given that there is only support for 7.04 until October 2008, I decided to look around for another distro and settled on Zenwalk.

Runs faster than Xubuntu 7.04 and I'm delighted with it.

Zenwalk seems to be far more old hardware friendly than Ubuntu.

---

### Post by CJ56 on 2007-12-14
I would definitely agree with gn2. Zenwalk is a beautiful distro, very fast, very light, very stable. Not as easy to tweak as Ubuntu and not as user-friendly, but really excellent once it's up and running.

---

### Post by DJiNN on 2007-12-14
I've been playing around with lightweight distros (on many older machines of a similar spec to the one you've built) for quite a few months now, and my experience has been to pretty much forget most of the Buntus.... they're great, but on such a machine as that they'll just make the whole experience an unhappy one. :)

If it's a Debian distro that you're after, then i can heartily recommend "[antiX]("http://antix.mepis.org")". It's lightweight, but very full in features. It's based on Mepis (Debian/Ubuntu) and you can either stay with the Mepis repos or switch to Debian sid, so there's choice there. The WM is Fluxbox, although others can be easily installed, and it's just damned fast on older machines.

There's also a great little distro called "[TinyFlux]("http://pcfluxboxos.wikidot.com/tinyflux")" which is somewhat different because it's RPM based, but it's light & fast, and works really well on older machines. It's also using Fluxbox and has a good selection of programs.

If you fancy a different (read: Slackware) experience, then [Wolvix]("http://www.wolvix.org") will probably do VERY well. Small, and works incredibly well on slower/older machines etc, as does [Zenwalk]("http://www.zenwalk.org"). Both are Slack based, both are excellent, and both install quickly & easily on older machines with limited resources. 

This is by no means an exhaustive list of smaller distros, just my "Pick of the Bunch" at the moment, and what i've found (recently) to work well on slower machines.  :)

DJiNN

---

### Post by armandh on 2007-12-14
I have 7.04 running on a 800 P-III 100fsb 256 meg ram and it plays dvds with out apparent skips. less mem makes ubuntu such a dog. a 733 / 133 P-III  I810 chip shared mem mobo ran dvds like crap.

crusing around the bottom end of the requirements shows up what hardware was crud to begin with.

---

### Post by RedSquirrel on 2007-12-14
I found the following links helpful when running Ubuntu on old hardware:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

K.Mandla has a collection of speed tips as well. They are worth looking into:

[http://kmandla.wordpress.com](http://kmandla.wordpress.com)
[http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/](http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/)

---

### Post by mmb1 on 2007-12-14
While the buntu family may not be suitable, you would still most likely have good results with puppy linux, Damn Small, or even Vector Linux

---

### Post by rexmundy on 2007-12-14
I've got Ubuntu 6.10 running well on an old box with the Xfce desktop and it's doing fine. However, if you're having problems with Ubuntu stuff then you should try Mepis Antix. I have both on one machine and I use Antix for most things because it's really fast. Personally I would go for the older version as opposed to the new 7.0 one.

---

### Post by jabeez on 2007-12-15
Hey all, thanks for all the replies/info/suggestions!! I never even tried U/K Buntu, I knew those would be slow, I only tried the "llighter" X and Geu versions. The dilemma I have and why I was hoping a Buntu would work is because I'm giving it to someone with NO linux experience. For myself I would like to try out some of the lesser knowns that may require extra tweaking, but for him I was hoping for Buntu simplicity. I have discs for pretty much every version since Hoary, I guess I was just being stubborn hoping I could get "the latest and greatest (well, maybe greatest)" working....

I guess what I'm wondering after reading around the tubes is why (at least with the Buntu's) does support for older hardware seem to get dropped with every release, even though that is one of the main selling points is that it runs well on older hardware? Maybe have two versions, one with older hardware support still included?

Not that I'm complaining, the devs have given us, literally, a fantastic OS and I'm very greatful, just wondering about the reasons. Thanks again for all the suggestions, as soon as I get my friend set up I definately want to look into some of these alternative (lesser known) distros. Cheers!!!

---

### Post by DJiNN on 2007-12-15
Hey jabeez, if you definitely want to stick with a Ubuntu derivative, then antiX could well be the one that you're looking for. It's based on Mepis (Which is itself based on Ubuntu) and although it uses the Mepis or Debian repos (your choice) it's almost like using Ubuntu but with a different front end. 

Other than that, take a look at [FluxBuntu]("http://www.fluxbuntu.org") as it's based on Gutsy, but with a MUCH lighter footprint (using Fluxbox) it's easily installable, and best of all, it uses the Ubuntu repos. Should install & run quite well on the machine that you described.  :)

Whichever one you choose, i hope it turns out well & your friend is pleased. 

DJiNN

---

### Post by linuxlizard on 2007-12-16
check out pcfluxboxos. I run that on my p3 700 mhz laptop with 192 mb ram and it flies.

---

### Post by jabeez on 2007-12-21
Well I tried Fluxbuntu 7.10 on the Celeron 1.3/256 ram machine, and it installed (took FOREVER), but on reboot I get a black screen. I'm guessing it's the PCI Voodoo graphics card, is anyone using a PCI graphics card? I finally gave up and started to install Arch, but couldn't get X to start there either. Grrrr, and of course the thing has no AGP slot........

And to clarify, I know Linux can run on old hardware and run well, it just seems you have to choose a less-than-newb friendly distro. Oh well, at least we have that option! Cheers!!

---

### Post by Dojan5 on 2007-12-21
> **jabeez said:**
> Well being the local/family IT guy, I've got a decent supply of older towers and components. Recently my old roommate was looking for a computer to do just the very basic surfing/music/video/email, and I thought for sure I could cobble up a decent enough Linux-run machine that would cost him next to nothing. Well, the best I could come up with was a Celeron 1.2 Ghz with 256 ram and a 3dfx video card (even though I have 768 MB of ram that is somehow incompatible with these POS Dell/HP machines). Anywho, I thought for sure a lighter-weight 'Buntu would run fine on such a machine, but alas getting any recent version to even boot proved to be a chore. I finally got Geubuntu installed on a Celeron 800 with 192 ram, but even though it is supposed to be great on aging machines, it is SLOOOWWWWW (can't even watch YouTube vids).

Well, sorry for the rant but after spending a whole night on trying to get ONE machine up and running to a decent degree and failing miserably, I am just left wondering, is there something I'm missing or is Linux getting to the point where you really need a modern'ish machine to run decently? I didn't have high hopes from 2 old Celeron based machines, but seriously, this seemed the perfect opportunity to advance Linux as the OS for old hardware, but it looks like I should just install XP and have it be sluggish AND work/have 3D. I guess I could go the Slackware/Arch/build-from-scratch and maybe do better, but for as much time as it would take to get such installed and useable, we'd be better off just buying new hardware. Any thoughts?

I don't think that that machine was anything to have in that case.
When i run WinXP PRO it runs like, from pressing the button to where windows is stable and ready to use at most 20 minutes.
Today i measured the time with my Kubuntu, same computer (Wich means 256MB RAM 160GB HDD 800MHZ Processor) and Kubuntu only took 2 minutes from pressing the button to actually being stable.
SO, in that case your computer really must have been stuffed to the limit, if not above. Else i don't know :S

---

