---
title: "Arch Linux, RAM"
date: 2006-04-15
forum: The Cafe
---

### Post by hizaguchi on 2006-04-15
Ok, so I installed Arch Linux on a whim the other night.  It's been an, umm, educational experience since I'm pretty new to Linux, but I've got Xorg going and all of my basic stuff working.  So I started up Fluxbox and did "free -m" and saw that I'm only using 20 megs of RAM to run my basic desktop, while Fluxbox in Ubuntu uses like 65.

So my question is, what is the reason for this fairly huge difference?  Is it the fact that I still havn't gotten a bunch of stuff working, like openGL and the right drivers for most things?  Once I get those loading will the memory usage be closer to Ubuntu?  Or are there some things in Ubuntu that I could take out to knock its resourse usage down closer to Arch?

I like Ubuntu better so far.  Apt is faster and easier (for me, anyhow) than pacman.  Plus I've got ALOT of configuring left to do to get everything working the way Ubuntu does automatically.  Its worth it if I can still end up using such little memory, but if Arch is just going to end up being ram hungry too once I get the basic stuff completely working then I'd might as well just reinstall Ubuntu.

Anybody more experienced that can help me understand where my ram is going in Ubuntu?

---

### Post by endersshadow on 2006-04-15
It may be that you're looking at Virtual Memory in Ubuntu and Residential Memory in Arch (Residential Memory is accurate in terms of actual memory used by that process).  Also, your Arch installation probably is bare bones right now, so you don't have all sorts of shared libraries loaded up and all that.  I've installed Arch on another partition, as well, and it's certainly educational :)

---

### Post by hizaguchi on 2006-04-15
I dunno about the memory types.  I'm getting my memory usage from running "free -m" at the command line and adding up the usage in the 2nd two lines (+/- buffers/cache and swap), so unless that command works differently on Arch I think I'm comparing them correctly.  The performance difference confirms that too.  Arch running Fluxbox, Firefox, and a few terminals is using 50 MB and is very responsive on my system.  Ubuntu doing the same is up closer to 100 MB and starts using swap space and slowing down.

You're right about it being bare bones.  I've not even got my sound working right now and it's slow going because I'm having to do alot of reading the wiki and documentation to even know which general direction to head in.  Which is why I worry that I'll spend all this time getting my system set up and then I'll be using just as much memory as Ubuntu.  Sure, I'll of learned plenty in the process, but I'd rather do my learning as I have time instead of all at once just to get a fully functional system going.  I mean, it would definately be worth it if the performance is still going to be this great.  But I'm having a hard time cracking down on fixing my problems when I'm not sure what to expect when I'm done and that Ubuntu disk is sitting on the desk saying "boot me up and I'll have your system fully functional in a couple hours."  :)

I guess what I really wonder is, is there any real difference in starting with Ubuntu and taking the time to remove unnecessary fluff, and starting with Arch and taking the time to add necessary stuff?  When I finally get it all to where I want it to be, are the systems going to be pretty much the same, performance wise?

---

### Post by endersshadow on 2006-04-15
Yeah, I've found with Arch that the documentation, well, sucks.  While it certainly takes less time installing Gentoo, one thing that they've done right is documented well.  Arch's documentation leaves a bit to be desired...but I'm wading through it :)

---

### Post by xXx 0wn3d xXx on 2006-04-15
Well, is Arch slower in terms of opening applications ? Ubuntu tries to use any avaible memory for applications. The apps use this memory as cache, making your system faster. It then gives back the cached memory when it is needed. Most likely, Arch does not do this. Just because you have more ram doesn't mean a faster system.

---

### Post by midwinter on 2006-04-15
I've found Arch much faster, can't really pinpoint why though. :confused: 

Pacman is great and the distro is very up to date.  I'm a big fan. :)

---

### Post by endersshadow on 2006-04-15
[QUOTE=MasterChief1234]Well, is Arch slower in terms of opening applications ? Ubuntu tries to use any avaible memory for applications. The apps use this memory as cache, making your system faster. It then gives back the cached memory when it is needed. Most likely, Arch does not do this. Just because you have more ram doesn't mean a faster system.[/QUOTE]

No, Arch is a faster distribution all around.  There are a lot of reasons for this, but a bunch of them being tailored configurations and a barebones system to build upon.  Granted, Arch is a faster distribution *at default* than Ubuntu, but Ubuntu can be tailored to be just as fast as Arch.

---

### Post by hizaguchi on 2006-04-15
I spent a while tonight trying to track down where all of that extra RAM is going in Ubuntu.  So I did a server install of Dapper and just installed x-window-system-core and fluxbox.  The result was using 70 megs to run just Fluxbox, but everything works right off the bat.

Then I installed Arch again, got xorg and fluxbox, and then tried to set up as much of my hardware as I knew how.  Got my video driver, sound is working, installed my touchpad driver, and updated my xorg.conf to tell it to use all these goodies.  Started up fluxbox, ran free -m... 18 megs.

I read some more on the Arch Linux wiki.  I think I huge part of the difference is that Xorg 7 is modular.  Installing the most basic xorg I know how in Ubuntu doesn't take that modularity into account and installs the whole thing, complete with all the stuff I'll never use.  But installing xorg in Arch just gets the most basic packages.  I bet that's a big part of the difference.

---

### Post by briancurtin on 2006-04-16
[QUOTE=hizaguchi]I guess what I really wonder is, is there any real difference in starting with Ubuntu and taking the time to remove unnecessary fluff, and starting with Arch and taking the time to add necessary stuff?  When I finally get it all to where I want it to be, are the systems going to be pretty much the same, performance wise?[/QUOTE]not really much of a difference. i chose the arch route. i dropped ubuntu to get arch going and i have it running very well. it is very fast and very responsive. while i admit to not doing much to my ubuntu install back when i had it, i feel arch is going in a direction more suited to me so i tried it out and i love it.

---

### Post by hizaguchi on 2006-04-16
^ I'm feeling the same way.  I'm really new to Linux, and Ubuntu was the distro that let me get rid of Windows completely without missing out on much, but Arch is so fast and light (a big deal with 128 MB of memory) that it's well worth a little setup trouble.  Besides, I'm learning alot from it.

And Gnome is only using 42 megs... that's a big plus. :)

---

