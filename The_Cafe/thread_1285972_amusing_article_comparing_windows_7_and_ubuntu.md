---
title: "amusing article comparing windows 7 and ubuntu"
date: 2009-10-08
forum: The Cafe
---

### Post by Teber on 2009-10-08
i just happened upon this article with does have entertainment value. i will venture no opinion. perhaps we'd better not spend too much typing on this one? 

[http://www.tomshardware.com/reviews/xp-mode-ubuntu,2434.html]("http://www.tomshardware.com/reviews/xp-mode-ubuntu,2434.html")

---

### Post by s3MA00RRNY on 2009-10-08
People are probably going to be unpleasantly surprised when they find their shiny new OS doesn't come with the XP environment emulation.

---

### Post by Chronon on 2009-10-08
The author of that article seems to ignore that you could just install VirtualBox on the Windows 7 host and proceed in the same way as he showed for Ubuntu.

---

### Post by Hyporeal on 2009-10-08
> **Chronon said:**
> The author of that article seems to ignore that you could just install VirtualBox on the Windows 7 host and proceed in the same way as he showed for Ubuntu.

The point of the article is to get XP virtualization on a next-gen OS at minimal cost. The technique it presents can be used in Windows (and MacOS if I'm not mistaken) but a free OS like Ubuntu clearly maximizes the savings. In any case, the author is not going to be bothered to show how to do it in every conceivable environment so why not choose a popular free OS like Ubuntu?

I really like this article. I had no idea that VirtualBox had made this much progress in recent years. I may have to rethink my current dual-boot setup.

---

### Post by Chronon on 2009-10-08
I guess it's just the tack that the article takes.  It starts off talking about XPM and how it's a cool feature, but isn't available in most versions of Windows 7.  

It ends this section with:> One way or another, you are probably going to have to pay Microsoft some amount of money if you want XPM...

The apparent objection being that if you want to run a virtualized XP on your Windows 7, it's going to cost you.

Discussion then leaps to talking about Ubuntu with XP as a VirtualBox guest, picking up from the last quote with this:
> ...or not. If you're open to using Linux , you too can have a fast and secure next-gen OS with full XP compatibility, all for free!

The structure of it just makes it seem a bit disingenuous to me.  Virtualization is a moot point of comparison as it can be done (free of cost) from a Linux, Windows or Mac host system.  The point that the article eventually seems to aim toward is that you can run XP inside of a free host OS.  The whole XPM business just seems like a red herring to me.

---

### Post by Exodist on 2009-10-08
Toms Hardware is more often dead on. Good article.

I wonder how well games would run in a XP Virtual Box?

---

### Post by blur xc on 2009-10-08
> **Exodist said:**
> Toms Hardware is more often dead on. Good article.

I wonder how well games would run in a XP Virtual Box?

I've been using Vbox for a few months now, and the rate of improvements is staggering.  BUT- there are still some drawbacks, especially related to what I need it for-

Adobe Lightroom- though not Vbox's fault:  You can't have your Lightroom catalog on another disk (like my external drive), and pass it over through a shared folder.  Shared folders are treated like network drives or paths (don't know the correct terminology), and for some lame reason, Adobe made it so Lightroom can't have the catalog file on a network.  I don't know how professionals in a company setting w/ multiple users get around that one...  RAW disk access sounds like a potential solution, but is very dangerous right now- especially for me.

Sandisk Sanza Fuse- Again, maybe not so much a fault of Vbox:  The sanza media converter and firmware updater won't see the music players from the inside of the virtual machine, even though you can access them outside of the sanza software on  the vm.  Has to do w/ some kind of USB vm goofy-ness (it's a valid technical term, I looked it up)...

Lego Digital Designer- my kids use it, and it seems as though the 3d graphics emulation doesn't cut it.  Maybe there's still a way to get it to work, but I don't know it.  It hangs on the install when it gets to the 'detecting hardware' step...

Itunes- at least that works.  So, of the four reasons I need windows around, only one works in Vbox- the rest I still have to dual boot for.  It's irritating, and I end up not doing those things I need to dual boot for, because that's a PITA.

As vbox development moves along, I hold out hope that these things get fixed along the way...and I can reclaim that chunk of my hdd and add that space to my /home partition...


BM

---

