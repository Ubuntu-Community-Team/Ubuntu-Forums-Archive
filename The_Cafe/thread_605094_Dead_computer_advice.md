---
title: "Dead computer advice"
date: 2007-11-06
forum: The Cafe
---

### Post by Sabru on 2007-11-06
I wasn't sure what other section to post this in, since this is not directly related to Ubuntu.

I built a new PC running Ubuntu last year from new parts. Everything was working fine until this week when it started freezing up during normal use. The next day, it wouldn't boot up properly, and now when I turn it on, it won't show anything on screen, and I get a continuous tone from the little motherboard speaker. The fans and lights all still work though.

Does anyone know what could be causing this? I think it's probably a fried motherboard, but I guess there is a chance it could also be a bad PSU, or worse still, a bad PSU that fried the motherboard. Could it be even be something else like the RAM or CPU?

I have asked around, and will ask on some more forums, but I'm still not 100% sure about what part or parts I should replace. What would be the best course of action?

---

### Post by troymcdavis on 2007-11-06
.

---

### Post by Gremlinzzz on 2007-11-06
> **troymcdavis said:**
> Best course of action (full-disclosure--there is inappropriate language):

[http://www.youtube.com/watch?v=y5orss3fAEU](http://www.youtube.com/watch?v=y5orss3fAEU)

stupid video and lame music

---

### Post by Sabru on 2007-11-06
> Best course of action (full-disclosure--there is inappropriate language):

[http://www.youtube.com/watch?v=y5orss3fAEU](http://www.youtube.com/watch?v=y5orss3fAEU)

Haha, no, I love my computer too much.

---

### Post by -grubby on 2007-11-06
just hope your motherboard isn't fried. My first course of action would  be to change the PSU

---

### Post by Gremlinzzz on 2007-11-06
reset bios to default
check ram pull one stick out at a time and turn computer on if only one stick pull out and reset.
check harddrive on another computer

---

### Post by skoal on 2007-11-06
You only need a cpu, memory, and video card to POST - the startup boot screen *before* Grub when it checks all those doohickeys like memory and devices.

Odds are (and it sounds like) your fan went out on your video card and overheated. Swap with good parts (if available). First, video card, then memory, and finally the cpu.

If none of those 3 is the culprit, rip an electric cord from a lamp post, split the wire in two, and apply each wire on either side of your case until you see sparks fly and the green LED on your computer case begins to brighten.  That, or sell it on eBay as "like new".

\\//_

---

### Post by PatrickMay16 on 2007-11-06
Skoal! Long time no see. It's great to have you back with us.

Back on topic; I had a strangely similar problem recently with my own computar, but that was after I tampered with it. But anyway, I bought a new power supply, re-seated my CPU, RAM, cards, board, etc, and the computar is running like a champ.

I'd suggest trying a different power supply, to see if it will boot up with that. (if you have one spare.)
If you have spare CPUs, memory modules, video cards, or other things, try swapping those around, too. Maybe some other part has broken.

Good luck.

---

### Post by Sabru on 2007-11-07
Hi, thanks for the responses everyone. Unfortunately I do not have access to any spare parts, since everyone else I know uses a laptop. 

I guess I will have to buy a PSU *and* a new mobo or something.

---

### Post by inversekinetix on 2007-11-07
this site might help you

[http://www.pcmech.com/article/beep-codes/](http://www.pcmech.com/article/beep-codes/)

---

### Post by popch on 2007-11-07
The documentation that should have come with your motherboard should have documented the cause for the beeping and the blinkenlights (if any). If they have not supplied the doc on paper or CD, you can perhaps find it on the manufacturer's web site.

---

### Post by Bartender on 2007-11-07
> **popch said:**
> The documentation that should have come with your motherboard should have documented the cause for the beeping and the blinkenlights (if any). If they have not supplied the doc on paper or CD, you can perhaps find it on the manufacturer's web site.
Agreed.  If you can't find documentation, try googling "beep codes" and your motherboard.  
If beep code indicates RAM, set up the PC on a well-lit table in a room with a hard floor - no carpet.  RAM can be damaged from static electricity.
Shut off PC.  I usually unplug mine just to be sure.  Try one stick of RAM in the #1 slot, plug the PC in, restart, watch the screen for signs that it recognized some memory.  If no go, try another piece.
If you're running memory in a dual-channel configuration, you may have to go into BIOS and tell it that you're not running dual-channel for the purpose of testing.  Not sure about that part.

---

### Post by svtfmook on 2007-11-07
look at the manual for your motherboard under trouble shooting.  the tone you hear during POST is a debugging code.  match the code of the tone to the manual and go from there.  that will tell you where the problem starts.

i doubt it's a power supply problem, if it were, BIOS would not pick that up, not to mention, not everything would power up.  one of the rails would be bad, so something would not power.  but if you can get into BIOS, you can see what voltages are coming in.

a continuous tone like that tells me it's a CMOS failure.  reset CMOS by turning everything off, find the watch-like battery on the motherboard, remove it, put a paperclip on the battery's terminals, hold it there for 30 seconds, put the battery back in and try to boot the computer, atleast into BIOS.  if it lets you get into BIOS, but your still cannot boot up, change settings in BIOS, then shut down, then try to boot up again.  if the settings are different than what you set them to previously, replace the CMOS battery.

it could also be a bad ram module, if you have more than one, try taking one out, then swapping and see what happens.

if it were a hard drive, it would just display something like "no boot media"

anything else would not effect your system from booting.

---

