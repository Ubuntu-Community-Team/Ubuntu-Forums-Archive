---
title: "new comp parts not working"
date: 2005-04-14
forum: The Cafe
---

### Post by questionasker on 2005-04-14
ive recently purchased some new parts to build myself a beter computer. but ive run into some problems...

ive got a fujitsu siemens D1675 mother baord, a celeron 2.0 gig processor, 512 MB memory (184 pin DDR), 128MB Nvidia Geforece fx 5200 video card, onboard sound and ethernet, and a *sighes* 10 Gig western digital HD.

when i hook everything up, and turn on the power, the cpu fan, fan of teh video card, and the power supply fan all come on. 
the CD rom drive activity light comes on a stays on, with nothing happening. the monitor will not initialize, so i cant see if the bios is being started up or not...


i would really appriciate any help, im getting tired of using /\/\$ on the family comp... thanks in advance.

---

### Post by poofyhairguy on 2005-04-14
[QUOTE=questionasker]ive recently purchased some new parts to build myself a beter computer. but ive run into some problems...

ive got a fujitsu siemens D1675 mother baord, a celeron 2.0 gig processor, 512 MB memory (184 pin DDR), 128MB Nvidia Geforece fx 5200 video card, onboard sound and ethernet, and a *sighes* 10 Gig western digital HD.

when i hook everything up, and turn on the power, the cpu fan, fan of teh video card, and the power supply fan all come on. 
the CD rom drive activity light comes on a stays on, with nothing happening. the monitor will not initialize, so i cant see if the bios is being started up or not...


i would really appriciate any help, im getting tired of using /\/\$ on the family comp... thanks in advance.[/QUOTE]


I had that happen once. The CPU was a bunk. Had to send it back and get a new one....

---

### Post by escuchamezz on 2005-04-14
could be any of the main components - memory, motherboard, processor or most likely a missed connection.

---

### Post by questionasker on 2005-04-14
[QUOTE=escuchamezz]could be any of the main components - memory, motherboard, processor or most likely a missed connection.[/QUOTE]
 im gonna try unpluggin everything and going over them again to make sure i didnt miss any...

the processor was a retail, sealed one from newegg.com. the fan does come on, but i guess that doesnt mean the cpu is working...

---

### Post by Whiffle on 2005-04-14
[QUOTE=questionasker]im gonna try unpluggin everything and going over them again to make sure i didnt miss any...

the processor was a retail, sealed one from newegg.com. the fan does come on, but i guess that doesnt mean the cpu is working...[/QUOTE]
 my motherboard has a series of lights on the back that tell what is going on, pretty handy for problem solving.  some do it through beeps too...anything like that on yours?

---

### Post by questionasker on 2005-04-15
[QUOTE=Whiffle]my motherboard has a series of lights on the back that tell what is going on, pretty handy for problem solving.  some do it through beeps too...anything like that on yours?[/QUOTE]
 nope, no lights, and ive read that the beeps on this particualr mobo dont beep either...

i read that you have to enable screens because by default, they are shipped from teh factory as off...

shall try some more tinkering, thanks for the replies...

---

### Post by skoal on 2005-04-15
Since you can't POST with your computer:

1. Check to make sure the AGP card is really in.  You can look alongside the bottom of the gold pins and see if any are exposed outside of the slot.  AGP cards need to be seated firmly in their slot.
2. Check your mobo manual for proper installation of memory.  Some mobos need to be populated in certain order (or pairs) first before you can populate the others.
3. Plug in the P4 power connector from the PS to the mainboard.  Don't connect anything else to mobo except cpu, memory, and agp card.  Those 3 are all you need to post.
4. Check to see if any screws are under the mobo, shorting to ground.  Also, use the felt washers with the screws to secure the mobo to the case.
5. Some chipsets/mobos just flat out don't 'like' certain video cards.  If you have access to another one, try that instead.

---

### Post by questionasker on 2005-04-15
[QUOTE=skoal]Since you can't POST with your computer:

1. Check to make sure the AGP card is really in.  You can look alongside the bottom of the gold pins and see if any are exposed outside of the slot.  AGP cards need to be seated firmly in their slot.
2. Check your mobo manual for proper installation of memory.  Some mobos need to be populated in certain order (or pairs) first before you can populate the others.
3. Plug in the P4 power connector from the PS to the mainboard.  Don't connect anything else to mobo except cpu, memory, and agp card.  Those 3 are all you need to post.
4. Check to see if any screws are under the mobo, shorting to ground.  Also, use the felt washers with the screws to secure the mobo to the case.
5. Some chipsets/mobos just flat out don't 'like' certain video cards.  If you have access to another one, try that instead.[/QUOTE]
 1. yup, securely seated.
2. only one stick, in DIMM slot 1
3. "...P4 power connector from the PS to the mainboard..." what do you mean, i have a celeron, not a P4.
4. no screws, no felt washers, although i might try taking the motherboard off completely and re-mounting it.
5. tried another, same result...

thanks for the reply.

---

### Post by questionasker on 2005-04-15
btw- if anyone wants to know why im posting this here, its because i really want to run Ubnutu on this new machine... see what it can do...

---

### Post by skoal on 2005-04-15
[QUOTE=questionasker]3. "...P4 power connector from the PS to the mainboard..." what do you mean, i have a celeron, not a P4.[/QUOTE]

Doesn't matter if you have a P4 or a P4 celeron.  In a lot of P4 motherboard designs, you still need this auxillary 4-pin connector to POST.  That connector provides auxillary power (mainly) to your AGP slot.  All P4 *based* system designs require the 2x2 connector which uses the 'extra' minimum 8A it provides.  There is also a 1x6 connector used on some Intel chipset based mobos used mainly in servers.

Do you have a P4 (v2.03) certified power supply?  Look for the 2x2 connector on your mobo somewhere near your CPU.  If you're not using this connector, get yourself an ATX 2.03 ('P4 Ready') power supply first, then eliminate other hardware possibilities.

---

### Post by questionasker on 2005-04-15
[QUOTE=skoal]Doesn't matter if you have a P4 or a P4 celeron.  In a lot of P4 motherboard designs, you still need this auxillary 4-pin connector to POST.  That connector provides auxillary power (mainly) to your AGP slot.  All P4 *based* system designs require the 2x2 connector which uses the 'extra' minimum 8A it provides.  There is also a 1x6 connector used on some Intel chipset based mobos used mainly in servers.

Do you have a P4 (v2.03) certified power supply?  Look for the 2x2 connector on your mobo somewhere near your CPU.  If you're not using this connector, get yourself an ATX 2.03 ('P4 Ready') power supply first, then eliminate other hardware possibilities.[/QUOTE]
 ok, i was really hoping to use my old powersupply unit, i guess its not new enough, i dont have the P4 connect...

wheres a good place to get a cheap one?

---

### Post by skoal on 2005-04-15
[QUOTE=questionasker]wheres a good place to get a cheap one?[/QUOTE]

Yes, sir.  That's a good question.  I bought a $20 P4 PSU a few years ago, couldn't return it, and bought a $150 P4 PSU instead.

I'd give you my old PSU for free, but I tied it's cords to a 30 foot rope about a year ago.  I cast it overboard when I go fishing in rough waters.  By the way, you'd be surprised how many catfish you can reel in using lures cut from burnt green ATI7500  fab.

I wish I could make a good suggestion for you, but the Power Supply is one thing I don't throw pennies at.  Spending 150 dollars on one like me is probably overkill (if not stupid).  I spent $270 on my case too.  Looks nice, but unlike gold, scratches and fist marks take the 'shine' off it.

I would spend at least $40 on a PSU though.  Do you have any stores nearby you can return it to if this doesn't solve your POST problem?  Go with Enermax or Antec if you can.  You won't regret it.  Hopefully...

Let me know if you're still having problems getting it to post. PM me if you need to.

---

### Post by baza41 on 2005-04-15
Do you have to flash the board first?

---

### Post by jdong on 2005-04-15
[QUOTE=skoal] I would spend at least $40 on a PSU though. Do you have any stores nearby you can return it to if this doesn't solve your POST problem? Go with Enermax or Antec if you can. You won't regret it. Hopefully...[/QUOTE]

I echo that statement. Don't go too cheap on the PSU. It's not uncommon for a cheap PSU to fry/brown the motherboard and other components.


And 99% of the times, the cheap ones will also be so loud that you need earplugs to be in the room! I personally have an Antec.

---

### Post by questionasker on 2005-04-28
[QUOTE=jdong]I echo that statement. Don't go too cheap on the PSU. It's not uncommon for a cheap PSU to fry/brown the motherboard and other components.


And 99% of the times, the cheap ones will also be so loud that you need earplugs to be in the room! I personally have an Antec.[/QUOTE]
 ok, thanks for all the help.
a new power supply did the trick.

although i had to opt for a cheaper one due to money limits, its not loud at all and seems to be pushing everything jsut fine.

---

