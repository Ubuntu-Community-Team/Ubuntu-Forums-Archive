---
title: "Darwin"
date: 2009-10-14
forum: The Cafe
---

### Post by Grifulkin on 2009-10-14
I'm just wondering if anyone has tried Darwin, I know that is it open source therefore you could try it if you wanted also I have seen an iso on it's website.  So I was just wondering if anyone has tried it and what they thought of it?

---

### Post by t0p on 2009-10-14
I didn't even know you *can* use Darwin without the rest of OSX to prop it up.  So is Darwin a complete operating system?

---

### Post by dragos240 on 2009-10-14
It might be just a kernel like Linux. Or it could be complete like BSD systems.
EDIT: It's called GNU-darwin.

---

### Post by Grifulkin on 2009-10-14
I think it was the rest of OSX sits on so in theory without any real knowledge I would say yes you can run it by itself.  Although I could be totally wrong, no idea.

---

### Post by schauerlich on 2009-10-14
> **t0p said:**
> So is Darwin a complete operating system?

Yes.

The problem is, it's not distributed precompiled by Apple. However, [the source is available on Apple's website](http://www.opensource.apple.com/).

There is a project called [PureDarwin](http://www.puredarwin.org/) that aims to make a useful OS out of the code Apple provides.

---

### Post by Warpnow on 2009-10-14
It used to be downloadable as a compiled binary I believe, and you could run it, but it was extremely barebones.

---

### Post by Frak on 2009-10-14
I've used PureDarwin, it's nice.

---

### Post by pookiebear on 2009-10-14
now if you could run the iphone SDK on it then I would be ALL over it.

---

### Post by dragos240 on 2009-10-14
You probably could.

---

### Post by Frak on 2009-10-14
> **dragos240 said:**
> You probably could.
No, you couldn't. Be cool, but it lacks some proprietary Apple frameworks.

---

### Post by dragos240 on 2009-10-14
With a lot of hacking you could. I don't have a clue how, but, people can port something to almost anything, even if they have to dig through binaries.

---

### Post by Frak on 2009-10-14
> **dragos240 said:**
> With a lot of hacking you could. I don't have a clue how, but, people can port something to almost anything, even if they have to dig through binaries.
It'd be the equivilent of making Wine again.

---

### Post by schauerlich on 2009-10-14
> **Frak said:**
> It'd be the equivilent of making Wine again.

Sounds like a plan.

---

### Post by earthpigg on 2009-10-14
> **EDavidBurg said:**
> > It'd be the equivilent of making Wine again.Sounds like a plan.

+1

...not that i would donate time/money/effort to this. so i suppose my "+1" is rather empty.

---

### Post by MaxIBoy on 2009-10-15
The reason it's unlikely an open-source, cross-platform OS X compatibility layer will be made, is because OS X has too little market share to make it worthwhile.

Does anyone else find this hilarious?

---

### Post by Grifulkin on 2009-10-15
> **MaxIBoy said:**
> The reason it's unlikely an open-source, cross-platform OS X compatibility layer will be made, is because OS X has too little market share to make it worthwhile.

Does anyone else find this hilarious?

Yeah I don't see the point either.

---

### Post by earthpigg on 2009-10-15
> **MaxIBoy said:**
> Does anyone else find this hilarious?

not sure where you are from but i suspect most North Americans are largely unaware that outside North America, OS X use is around the same as Linux use.

Apple computers are considered another ridiculous American Eccentricity -- like Deep Fried Chocolate Bars, Protestant Mega-Churches, and invading nations based on tossing a dart at a map of the middle east.

---

### Post by steev182 on 2009-10-15
With Carbon and Cocoa (and probably a load of other things) being proprietary, the likelihood of an OSX version of Wine is near 0.

---

### Post by RaZe42 on 2009-10-15
> **earthpigg said:**
> not sure where you are from but i suspect most North Americans are largely unaware that outside North America, OS X use is around the same as Linux use.

Apple computers are considered another ridiculous American Eccentricity -- like Deep Fried Chocolate Bars, Protestant Mega-Churches, and invading nations based on tossing a dart at a map of the middle east.

Exactly. No macs in Finland. :P

---

### Post by NoaHall on 2009-10-15
Quite a  few mac's in the uk. My grandparents have two, they think it's the best fun ever, they spend all day scanning pictures in and then printing them off again.

---

### Post by Dragonbite on 2009-10-15
Maybe if there was a Darwin port for Gnome or KDE it could be useful?

---

### Post by schauerlich on 2009-10-15
> **steev182 said:**
> With Carbon and Cocoa (and probably a load of other things) being proprietary, the likelihood of an OSX version of Wine is near 0.

As opposed to the windows APIs, which are open source...?

But, yeah, wine took a really long time and a lot of development to get to where it is (which is okay to decent support for uncomplicated apps), and it would take just as long to make an OS X wine-type program (Xine?).

---

### Post by schauerlich on 2009-10-15
> **Dragonbite said:**
> Maybe if there was a Darwin port for Gnome or KDE it could be useful?

There is. Read up on PureDarwin if you want more info.

---

### Post by Frak on 2009-10-15
> **Dragonbite said:**
> Maybe if there was a Darwin port for Gnome or KDE it could be useful?
Gnome and KDE have been running on Darwin for a looooooooooooooooooooooong time. The last Darwin distro that existed, OpenDarwin (now defunct), used Gnome as its default DM.

---

### Post by Warpnow on 2009-10-15
> **EDavidBurg said:**
> As opposed to the windows APIs, which are open source...?

But, yeah, wine took a really long time and a lot of development to get to where it is (which is okay to decent support for uncomplicated apps), and it would take just as long to make an OS X wine-type program (Xine?).

Pretty sure xine's already taken. ;)

---

### Post by schauerlich on 2009-10-15
> **Warpnow said:**
> Pretty sure xine's already taken. ;)

So it is. :)

---

### Post by Frak on 2009-10-15
I vote for "Tinara"

**T**his **I**s **N**ot **A** **R**ecursive **A**cronym

---

### Post by Xbehave on 2009-10-15
For those of interested in a mac emulator then look at few projects to look at [gnustep]("http://en.wikipedia.org/wiki/GNUstep") and [cocotron]("http://www.cocotron.org/"), they are analogous to winelib as they replace the relevant libs at run/compile time.

I think the low demand (most mac apps are available for windows) combined with the difficulty of emulating a closed API* (wine has been in development for longer than mac os X has existed), is why there is no complete osX emulator.

*Linux emulation for BSD/solaris is much easier.

---

### Post by schauerlich on 2009-10-15
> **Xbehave said:**
> For those of interested in a mac emulator then look at few projects to look at [gnustep]("http://en.wikipedia.org/wiki/GNUstep")

GNUstep is not meant to be wine-for-OS X. It's an implementation of OpenStep, the specification that Cocoa is based on, but incompatible with.

---

