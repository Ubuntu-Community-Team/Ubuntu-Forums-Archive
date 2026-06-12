---
title: "Porting games to other systems?"
date: 2009-07-14
forum: The Cafe
---

### Post by dragos240 on 2009-07-14
Hi, would it be possible to port a newer game from another system to an older system if both systems are 128 bit?

---

### Post by tqx on 2009-07-14
Do you want to port a PS3 game to the Dreamcast?

---

### Post by dragos240 on 2009-07-14
No, like a gamecube to dreamcast.

---

### Post by doas777 on 2009-07-14
if you can get source code and a compiler for the target architechure, then it is theoretically possible. or you could emulate instead of port.

---

### Post by Xzallion on 2009-07-14
Just because both games support 128bit address space, doesn't mean they are compatible.  Different video chipsets are used and different amounts of ram.  I'm not a hardware expert, but this would be no small feat, and you would have to have access to the source code.  Since Nintendo and third-party developers own the source and nintendo has licensed it, you aren't going to be able to get it.  Reverse engineering won't work either, since the data won't have any meaning to it, no logical names for functions, variables, etc.  There would simply be to much data to shift through to 'port' it.

Emulation would be the only option, but that creates more overhead that the aging architecture just doesn't have.

---

### Post by CharmyBee on 2009-07-15
Also the Dreamcast has a very weak GPU despite the hype and love that surrounds the fanboys of it. You'd have to think like developing a game for a Pentium II 300MHz computer, with a Riva TNT 16mb.
Though you could get the actual chipset itself, but the card itself was a market failure and is very rare (PowerVR Neon250)

---

### Post by ThisEndlessFall on 2009-07-15
> **CharmyBee said:**
> Also the Dreamcast has a very weak GPU despite the hype and love that surrounds the fanboys of it. You'd have to think like developing a game for a Pentium II 300MHz computer, with a Riva TNT 16mb.
Though you could get the actual chipset itself, but the card itself was a market failure and is very rare (PowerVR Neon250)

The Dreamcast's CPU is actually about equivalent to a Pentium 3 450Mhz. Games that were ported to the PC from the Dreamcast roughly needed a Pentium 3 800Mhz, 256Mb RAM, and a 32Mb graphics card. Anything below those specifications and you would get serious slowdown.

Also the Dreamcast's GPU is about equivalent to a 32Mb TNT2. The PowerVR 2(Neon 250) chipset uses hidden surface removal, which basically means it only draws what you can see on he screen, nothing more.

The Dreamcast was a fantastic console hurt mostly by a lack of RAM & DVD capability. It's a shame it didn't last any longer than 2001 in europe.

---

### Post by CharmyBee on 2009-07-15
> **ThisEndlessFall said:**
> The Dreamcast's CPU is actually about equivalent to a Pentium 3 450Mhz. Games that were ported to the PC from the Dreamcast roughly needed a Pentium 3 800Mhz, 256Mb RAM, and a 32Mb graphics card. Anything below those specifications and you would get serious slowdown.


The bad PC ports of Dreamcast games aren't a good example of showing off superiority of a Dreamcast vs a PC. Try Quake III Arena on the Dreamcast, which is regarded as one of the best pc-to-console ports ever, but shows alot of the shortcomings of the Dreamcast.

> **ThisEndlessFall said:**
> Also the Dreamcast's GPU is about equivalent to a 32Mb TNT2. The PowerVR 2(Neon 250) chipset uses hidden surface removal, which basically means it only draws what you can see on he screen, nothing more.

Hidden surface removal means nothing for benefit if the cpu still has to process the vertices. The GPU was made in mid-1998, a full year before the TNT2. PowerVR was never ahead of the industry. The Neon250 in this case is just a 'catch up chip' with more blending modes tacked on its direct predecessor and higher clock.

---

### Post by ThisEndlessFall on 2009-07-15
> **CharmyBee said:**
> The bad PC ports of Dreamcast games aren't a good example of showing off superiority of a Dreamcast vs a PC. Try Quake III Arena on the Dreamcast, which is regarded as one of the best pc-to-console ports ever, but shows alot of the shortcomings of the Dreamcast.


Hidden surface removal means nothing for benefit if the cpu still has to process the vertices. The GPU was made in mid-1998, a full year before the TNT2. PowerVR was never ahead of the industry. The Neon250 in this case is just a 'catch up chip' with more blending modes tacked on its direct predecessor and higher clock.

The PC ports like Virtua Tennis, Sakura Wars were not particulary bad. SuperH processors of the day, aka SH4 were significantly quicker than a say Pentium III running at the same Mhz. You quoted as saying think of porting to a PC with a 300Mhz Pentium 2. The SH4 in the Dreamcast is 4 times faster than a 266Mhz Pentium 2. This is a fact, Sega even used this in their marketing. 

I have played Quake III on the Dreamcast since it was released. I am also partly responsible for the modded DC Quake III that allows up to 8 players in a game VS the standard 4.

The Neon 250 was only slower than the TNT2 due to the fact of slower clock frequencies of the GPU and RAM. When this card is overclocked to an equivalent Mhz to a TNT2, it surpasses it by about 25% in the best scenario.

---

### Post by CharmyBee on 2009-07-15
> **ThisEndlessFall said:**
> This is a fact, Sega even used this in their marketing. 

Marchitecture doesn't count when it comes to reality. Is a PS2 really at least 3x the speed of a Pentium III 700MHz also? Ok I guess that doesn't count because it's NOT by SEGA.

I am a SEGA fan (as if the name and avatar doesn't say so already), and i'm being as optimistic as I can for the Dreamcast, it's just that realistic thinking isn't rational enough I guess.

---

### Post by ThisEndlessFall on 2009-07-15
> **CharmyBee said:**
> Marchitecture doesn't count when it comes to reality. Is a PS2 really at least 3x the speed of a Pentium III 700MHz also?

I am a SEGA fan, and i'm being as optimistic as I can for the Dreamcast, it's just that realistic thinking isn't rational enough I guess.

Is isn't "marchitecture", it is set in stone truth. 

Of course the PS2 is not 3x the speed of a Pentium III 700Mhz. I have also never heard anyone claim this. 

I have worked a lot with the DC homebrew scene. I know the strengths & weaknesses of the Dreamcast. It's biggest handicap is it's lack of RAM. If it had been outfitted to the specifications of the NAOMI, things may well have been quite different. Although against Sony's marketing power of the time, maybe not...

---

