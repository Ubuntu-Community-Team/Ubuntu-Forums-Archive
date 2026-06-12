---
title: "Applele Macbook Pro (Intel Core Duo) - i386 or ... ?"
date: 2006-01-10
forum: The Cafe
---

### Post by Derek Djons on 2006-01-10
Some of you might have been checking the Live postings about Apple's Keynotes 2006. A bunch of cool Apple related products have been announced and released. Also the new Apple notebook. It's the successor of the Powerbook. So his era is over. The new Macbook Pro offers quite some stunning high tech power.

Frontpage: [http://www.apple.com](http://www.apple.com)
General Information: [http://www.apple.com/macbookpro/](http://www.apple.com/macbookpro/)
Tech specs: [http://www.apple.com/macbookpro/whatsinside.html](http://www.apple.com/macbookpro/whatsinside.html)

We all know that Linux / Ubuntu is supporting: PowerPC, i386 and AMD64.

Since Intel Core Duo is a relative new product I was curious if there will be a new type of Ubuntu specially made for the Core Duo or is it gonna be able to run optimized on the i386 type releases?

---

### Post by mstlyevil on 2006-01-10
[QUOTE=Derek Djons]Some of you might have been checking the Live postings about Apple's Keynotes 2006. A bunch of cool Apple related products have been announced and released. Also the new Apple notebook. It's the successor of the Powerbook. So his era is over. The new Macbook Pro offers quite some stunning high tech power.

Frontpage: [http://www.apple.com](http://www.apple.com)
General Information: [http://www.apple.com/macbookpro/](http://www.apple.com/macbookpro/)
Tech specs: [http://www.apple.com/macbookpro/whatsinside.html](http://www.apple.com/macbookpro/whatsinside.html)

We all know that Linux / Ubuntu is supporting: PowerPC, i386 and AMD64.

Since Intel Core Duo is a relative new product I was curious if there will be a new type of Ubuntu specially made for the Core Duo or is it gonna be able to run optimized on the i386 type releases?[/QUOTE]

It will run both cores on a i386-smp kernel, the same as all other dual cores. Poofy has a posting on this in the how-to's. My guess is you would run it on the same kernel as you would any other Intel dual core for optimised speed.

Edit

Here is the link to Poofy's thread on How to pick the kernel that is right for you.

[http://www.ubuntuforums.org/showthread.php?t=85917]("http://www.ubuntuforums.org/showthread.php?t=85917")

According to this I would use the i686-smp kernel.

---

### Post by xequence on 2006-01-10
Wow, for once theyre new product doesent start with an "i" :)

---

### Post by somuchfortheafter on 2006-01-10
sorry but shouldnt the duo chips be able to run on i686 smp ? i mean its dual processing and it should be using the 686 based instruction set right? also I am strongly considering the purchase of one of these for my next machine, they look awesome.

---

### Post by mstlyevil on 2006-01-10
[QUOTE=somuchfortheafter]sorry but shouldnt the duo chips be able to run on i686 smp ? i mean its dual processing and it should be using the 686 based instruction set right? also I am strongly considering the purchase of one of these for my next machine, they look awesome.[/QUOTE]

Yeah, I edited my post to reflect that. I wasn't sure because I run the K7 kernel.

---

### Post by ssam on 2006-01-10
i wouldn't assume that just because the cpu is supported that ubuntu will work straight away.

they may not use an ordinary intel motherboard, it may retain apple components. for example powerpc macs use open firmware instead of BIOS. if this has been kept (BIOS would probably be a step backwards), then GRUB probably wont boot it. it may need yaboot ported to x86.

i expect we'll know quite soon though.


added: word on the street is BIOS

---

### Post by Derek Djons on 2006-01-10
[QUOTE=mstlyevil]It will run both cores on a i386-smp kernel, the same as all other dual cores. Poofy has a posting on this in the how-to's. My guess is you would run it on the same kernel as you would any other Intel dual core for optimised speed.

Edit

Here is the link to Poofy's thread on How to pick the kernel that is right for you.

[http://www.ubuntuforums.org/showthread.php?t=85917]("http://www.ubuntuforums.org/showthread.php?t=85917")

According to this I would use the i686-smp kernel.[/QUOTE]

Thanks mstlyevil for shining a light on this. We all have to wait untill february till this baby will see daylight. I'll have to keep putting money aside till december of 2006 :( but I hope it will be worth the waiting. Probably all child-deceases will be bugged out of it at that time ;)

At my work (Apple Centre) the nice thing is that using an external Harddrive I can install Ubuntu Linux on it and see how it functions all without upsetting my manager that Mac OS X is being dumped. I hope that this thing will hit the shop in february.

---

### Post by mstlyevil on 2006-01-10
[QUOTE=ssam]i wouldn't assume that just because the cpu is supported that ubuntu will work straight away.

they may not use an ordinary intel motherboard, it may retain apple components. for example powerpc macs use open firmware instead of BIOS. if this has been kept (BIOS would probably be a step backwards), then GRUB probably wont boot it. it may need yaboot ported to x86.

i expect we'll know quite soon though.[/QUOTE]

You might be right on this but i have a sneaking suspicion that Apple is just using a standard Intel Mother Board with a mod chip added to save cost. The mod chip of course is what locks OSX to Mactels only but from a financial point of view using current mother boards will add a lot of money to their bottom line. They will still charge a premium price but have a lower overhead leading to increased profits. Since Apple has shifted focus and made profits the top priority, it makes it a more likely scenario to just use standard x86 parts.

---

### Post by ssam on 2006-01-11
maybe it is not BIOS. there is some mention on forums of [EFI]("http://www.intel.com/technology/efi/"), Extensible Firmware Interface.

i am not sure if this is the same as the efi that [elilo]("http://sourceforge.net/projects/elilo") boots. its not clear if grub can boot on efi.

lots of info at [http://en.wikipedia.org/wiki/Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface).

---

### Post by curuxz on 2006-01-11
does this mean the death of PPC? and will osX now run on PC's since they will have to port it. I think apple have made a massive mistake throwing in with intel. This could spell their death

---

### Post by ssam on 2006-01-11
[QUOTE=curuxz]does this mean the death of PPC? and will osX now run on PC's since they will have to port it. I think apple have made a massive mistake throwing in with intel. This could spell their death[/QUOTE]

there are plenty of other people using powerpc. IBM servers, embeded stuff, games consoles, pegasos, etc.

it will probably will be posible to run os x on non apple hardware, but it may not be easy. if the developer previews are anything to go by there will be methods in place to stop you doing it. a similar task to getting linux running on the xbox. you would also need to have a hardware set up similar to the intel macs. same chipsets etc. there wont be drivers for any old bit of hardware.

apple are smart enough to know that if mac os x works partially on generic PCs with a bit of work it may make be try it, who may then go on to buy a mac. it people running mac os x on non apple machines becomes a problem they'll make sure mac os x 10.5 won't.

the other question is will linux/windows run on the new macs. i guess probably, but not straight away. the developer preview machines could dual boot windows, but i looks like the release verison have a very different boot system, EFI.

---

