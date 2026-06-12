---
title: "MeeGo desktop in Lucid x64?"
date: 2010-06-02
forum: The Cafe
---

### Post by murderslastcrow on 2010-06-02
Anyone know if the MeeGo DE is available to install? I'd really like to have it as an alternative in my GDM so I can have it on my TV and tablet, just for the sake of testing it out and seeing if it's better for some things.

I assume it's open source, so it shouldn't be too difficult to use, especially when Dell ships a version of Netbook Remix with Moblin's DE in it.

Anyone done this yet or have information on how I could, most easily do so?

---

### Post by murderslastcrow on 2010-06-03
Lol, I guess this is the time for me to make a PPA.

---

### Post by cariboo on 2010-06-03
I downloaded the img file from [here]("http://meego.com/downloads/releases/1.0/meego-v1.0-netbooks"), this is for the netbook version, which is 32-bit. I didn't see anything listed for 64-bit. I haven't tried it yet, but it's on my list of things to do.

---

### Post by DeadSuperHero on 2010-06-03
Technically speaking, every part of MeeGo is open source. So, it should be able to build given enough tweaking.

But, it's one of those "Not really supported by Intel" type of things. They support Intel chips, possibly x86, and ARM. No word on whether AMD will ever work with it, which bums me out.

---

### Post by amitabhishek on 2010-06-04
> **DeadSuperHero said:**
> They support Intel chips, possibly x86, and ARM. No word on whether AMD will ever work with it, which bums me out.

Me too! My both notebooks are AMD powered :(!

And why on Earth can't they release an .iso image!!!

---

### Post by mickie.kext on 2010-06-04
Well, Atom is 32-bit only in-order P.O.C of a procesor. I dont think there will be oficial 64-bit build any time soon. 

They optimised it for LPIA as far as I can see, which pretty much turns me off MeeGo. I really not like seeing Intel work anything with Linux beyond drivers for their hardware. They would really like to bring it back to 1991 when kernel used every (miss)feature of x86 CPUs. But we do not have Digital now to port it to Alpha and abstract intelism.

---

### Post by DeadSuperHero on 2010-06-04
You'd think, though, that someone would be at least smart enough to use a 64-bit kernel, and try porting over as many native 64-bit libraries as possible. That would at least make the actual porting of MeeGo itself a lot simpler.

---

### Post by ve4cib on 2010-06-04
But MeeGo is primarily intended for embedded/mobile devices.  You don't typically find a 64-bit CPU in a mobile or a netbook, so I can understand why 64-bit support is low on their list of priorities, especially right now when the project is just starting.

---

### Post by zekopeko on 2010-06-04
> **DeadSuperHero said:**
> Technically speaking, every part of MeeGo is open source. So, it should be able to build given enough tweaking.

But, it's one of those "Not really supported by Intel" type of things. They support Intel chips, possibly x86, and ARM. No word on whether AMD will ever work with it, which bums me out.

Why wouldn't AMD chips work?

AFAIK for Moblin you had to have a processor that supports SSE3 instruction set.
Here is a list of AMD processors that support that: [http://en.wikipedia.org/wiki/SSE3#CPUs_with_SSE3](http://en.wikipedia.org/wiki/SSE3#CPUs_with_SSE3)

So I don't see why AMD chips wouldn't be supported.

EDIT: Looks like I was wrong. Moblin needed **S**SSE3 not SSE3.
[http://meego.com/devices/netbook/supported-hardware-platforms](http://meego.com/devices/netbook/supported-hardware-platforms)

---

### Post by murderslastcrow on 2010-06-04
I'm only interested in the desktop environment- I assume it's open enough to support Ubuntu daemons and such, since Banshee is their default media player and it looks pretty nice. I can't imagine they're only supporting specific applications, since they show so many applications working with it.

I imagine, given the source, it won't be too difficult to modify that package, unless it wraps around specific drivers only available on integrated Intel graphics chips. If that's the case, I might as well make my own.

---

### Post by tgm4883 on 2010-06-04
> **mickie.kext said:**
> Well, Atom is 32-bit only in-order P.O.C of a procesor. I dont think there will be oficial 64-bit build any time soon. 

They optimised it for LPIA as far as I can see, which pretty much turns me off MeeGo. I really not like seeing Intel work anything with Linux beyond drivers for their hardware. They would really like to bring it back to 1991 when kernel used every (miss)feature of x86 CPUs. But we do not have Digital now to port it to Alpha and abstract intelism.

Not true. My Netbook at a 64-bit Atom processor, but the UNE is only released in 32-bit :(

---

### Post by murderslastcrow on 2010-06-04
Oh yeah, I've been hearing about those dual-core Atoms, lately. I think they're trying to compete with the new high-powered ARMs that've been coming out recently. This certainly is an interesting market to watch, especially since Linux-based offerings are the only options in some areas.

I'm actually really glad Linux has finally found its niche here. MeeGo looks amazing.

---

### Post by mickie.kext on 2010-06-04
> **tgm4883 said:**
> Not true. My Netbook at a 64-bit Atom processor, but the UNE is only released in 32-bit :(

Hmm... I am pretty sure that all netbook models of Atom have -64 extensions disabled via microcode (which means that architecure is 64-bit capable, just Intel likes to cripple it for later up-sell) but desktop (or so called Nettop) models have -64 extension enabled. So you could have a desktop model in that netbook. 

*looking...* 

Yeah, I am right [http://en.wikipedia.org/wiki/Intel_Atom](http://en.wikipedia.org/wiki/Intel_Atom)

> Atom implements the x86 (IA-32) instruction set; x86-64 is so far only activated for the desktop Diamondville and desktop and mobile Pineview cores. The Atom N2xx and Z5xx series Atom models cannot run x86-64 code.[16]

---

### Post by tgm4883 on 2010-06-05
> **murderslastcrow said:**
> Oh yeah, I've been hearing about those dual-core Atoms, lately. I think they're trying to compete with the new high-powered ARMs that've been coming out recently. This certainly is an interesting market to watch, especially since Linux-based offerings are the only options in some areas.

I'm actually really glad Linux has finally found its niche here. MeeGo looks amazing.

> **mickie.kext said:**
> Hmm... I am pretty sure that all netbook models of Atom have -64 extensions disabled via microcode (which means that architecure is 64-bit capable, just Intel likes to cripple it for later up-sell) but desktop (or so called Nettop) models have -64 extension enabled. So you could have a desktop model in that netbook. 

*looking...* 

Yeah, I am right [http://en.wikipedia.org/wiki/Intel_Atom](http://en.wikipedia.org/wiki/Intel_Atom)

Nope, I have a mobile Pineview core. It's an N450 in my HP mini 210

---

### Post by zekopeko on 2010-06-05
> **tgm4883 said:**
> Nope, I have a mobile Pineview core. It's an N450 in my HP mini 210

Pineview is 64-bit enabled. The problem are the older N and Z series that apparently aren't 64-bit enabled.

---

