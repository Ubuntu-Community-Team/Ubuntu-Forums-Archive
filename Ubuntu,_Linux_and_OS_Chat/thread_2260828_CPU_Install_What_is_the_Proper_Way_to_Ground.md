---
title: "CPU Install: What is the Proper Way to Ground?"
date: 2015-01-14
forum: Ubuntu, Linux and OS Chat
---

### Post by Kurt_Alan on 2015-01-14
There are two schools of thought.

The first.  My buddy's apartment is carpeted. Therefore, I recommended he install his mobo's cpu in the kitchen (linoleum floor), plug his toaster oven into a grounded outlet, and clip his anti-static bracelet to that.

The second.  Before the install, just touch the oven (or computer case)--doesn't need to be plugged in; don't need an anti-static bracelet. Touching the case will be sufficient as long as you and the case have the same electrostatic potential.

I'm placing my bets on the first.  How about you?

P.S. I've never heard a definitive answer to this question.

---

### Post by Habitual on 2015-01-14
Aren't these grounded?
[IMG]http://www.mytobago.info/photos/electricity/duplexplugs.jpg[/IMG]

---

### Post by QIII on 2015-01-14
I've done bracelet to case for years.

---

### Post by d-cosner on 2015-01-14
I always just touch the case first. When I worked in IT I always had to hurry because I had 300 computers to take care of. I  remember putting the screws in a computer to hold the video card in place while the user was doing his work on the computer, that's how busy things got!

---

### Post by Mike_Walsh on 2015-01-14
I always work on my machines in the utility room. It has two double copper pipes running floor to ceiling beside the window, and this is where the house's main earth rod, & the house electrical system, connects to the pipework. 

I have a home-made antistatic bracelet, consisting of a 4 yard length of double core, braided, 22 swg insulated copper cable, with one end stripped back by nine inches (this wraps round my wrist), and the other end fastened to a giant crocodile clip; this goes securely onto the top end of the earth rod, and the whole thing is long enough to allow me to use the workbench in front of the big window.

That, together with having a flag-stone floor in the utility room, means that I've never had the slightest problem with static electricity.....regardless of how many times I've had my computers to bits over the years. I made it up nearly 30 years ago, after a conversation with an acquaintance who, at the time, worked for British Telecom's IT Division here in the UK.

And this was long before the current wide-spread public knowledge about the dangers of combining  static electricity and delicate electronic components...

It's served me faithfully for many years.


Regards,

Mike. ;)

---

### Post by Bucky Ball on 2015-01-14
> **d-cosner said:**
> I always just touch the case first. 

That's my modus operandi. Just grab the case. Have installed CPUs on carpets, stone floors, etc. I am no electrical engineer though, but have always just grounded myself against the case before dipping into it.

---

### Post by grahammechanical on 2015-01-14
> **Habitual said:**
> Aren't these grounded?
[IMG]http://www.mytobago.info/photos/electricity/duplexplugs.jpg[/IMG]


I do not think so. 2 pins = positive and negative supply. Need a third pin to be earth or ground. Need also 3 cable mains wiring with the earth or ground cable connected to earthing points. Usually, copper house pipes.

---

### Post by Bucky Ball on 2015-01-14
> **grahammechanical said:**
> I do not think so. 2 pins = positive and negative supply. Need a third pin to be earth or ground. Need also 3 cable mains wiring with the earth or ground cable connected to earthing points. Usually, copper house pipes.

There are three pins. I thought the round one at the bottom was earth. Like I said, I'm no electrician, though. :-k ;)

---

### Post by Mike_Walsh on 2015-01-15
Graham, like me, is probably used to the standard, 3 square pin layout that is currently used for plugs and sockets in the UK:-


[ATTACH=CONFIG]259244[/ATTACH]  [ATTACH=CONFIG]259245[/ATTACH]


I don't know Graham's age, but being born at the very start of the 'swinging Sixties', I can remember, where we used to live at that time, having round pin plugs & sockets, as was indeed standard in the UK at that time:-


[ATTACH=CONFIG]259246[/ATTACH]  [ATTACH=CONFIG]259247[/ATTACH]



At the beginning of the 1970's, we even had an adapter in the house that would take one round-pin plug, and one square-pin plug; this was at the beginning of the move to the current standard.

There's even a weird, space-saving design now, that has all three pins in a vertical line, one above the other:-


[ATTACH=CONFIG]259248[/ATTACH]

I believe it's actually a 'folding', travel plug.....to take up less space in your suitcase! 

However, they ALL have that most important of items.....the 3rd ground pin to earth the component or item in question.


Regards,

Mike.;)

---

### Post by Bucky Ball on 2015-01-15
Here's the Australian plug and socket. Different again. Think they're also used in New Zealand.

---

### Post by Mike_Walsh on 2015-01-15
Astounding, isn't it, Bucky? We've managed to pretty well standardise computer protocols globally, which is shrinking our planet almost daily.....yet we STILL can't standardise the very item which gives all our machines life!

Nearly EVERY country in the world still has a different output plug/socket arrangement to what is an otherwise universal electrical standard.


Regards,

Mike.

---

### Post by George_Hostler on 2015-01-15
> **grahammechanical said:**
> [QUOTE=Habitual;13207576]Aren't these grounded?
[IMG]http://www.mytobago.info/photos/electricity/duplexplugs.jpg[/IMG]I do not think so. 2 pins = positive and negative supply. Need a third  pin to be earth or ground. Need also 3 cable mains wiring with the earth  or ground cable connected to earthing points. Usually, copper house  pipes.[/QUOTE]

Yes, it is grounded. The round pin that fits into the round or "D" shaped hole in the wall outlet is your grounding pin. It is this pin that connects to the case. Unless miswired, the wider pin is the neutral, the narrower 120 VAC (Volts A.C.).

First, check to make sure that the ground pin works. Set your VOM to AC scale greater than 120 VAC. Stick one prong of the VOM probe to the outlet round ground slot. Stick the other to the smaller rectangular slot. You should see roughly 120 VAC. This means the ground is connected. Remove probe from 130 VAC hot slot to wider neutral slot. You should see 0 Volts. Measure across neutral and hot. You should see roughly 120 VAC. If socket is not grounded, then the next steps won't work.

I leave the computer box plugged into the outlet, switch off the power supply from the external on-off switch by the power supply. Then touch my hands to the metallic chassis of the computer cabinet to bleed off any static electricity on my body. Then without moving or walking (you don't want to gain static electricity you just bled off), pick up the CPU that I previously placed close to me and install it in the socket.

If you don't have a power supply that can be totally turned off or aren't comfortable, you can put a small diameter jumper wire with about 3/4 inch of insulation removed to one of the mounting screws provided it has a functioning ground. A continuity check between the outlet plate mounting screw, hot and neutral will verify whether it is grounded. Put remove insulation on the other end and place under one of the case screws. This should bleed off any static electricity from the case.

Older homes and facilities built before the mid 1960's may only have ungrounded outlets. Some have ungrounded outlet boxes. Some, people have later installed 3 prong outlets, but the ground pin may not be grounded as there is no grounding wire in the wiring. A quick check with the VOM or physical inspection by removing the outlet cover plate will verify this.

---

### Post by lisati on 2015-01-15
A thought before the pedants jump in: even though most would probably know what is being referred to, the terms "positive" and "negative" only really work if you're using DC. All of the electrical outlets in my place use AC.

> **Bucky Ball said:**
> Here's the Australian plug and socket. Different again. Think they're also used in New Zealand.

Same scheme here in New Zealand. Two of the prongs are for "live" and "return" (terminology?) and the third, when in use, is for "ground/earth." When I was visiting Surfers Paradise back in 1997, my video gear and laptop purchased in New Zealand worked like a charm in the Australian hotel.

---

### Post by Kurt_Alan on 2015-01-15
> **George_Hostler said:**
> Yes, it is grounded. The round pin that fits into the round or "D" shaped hole in the wall outlet is your grounding pin. It is this pin that connects to the case. Unless miswired, the wider pin is the neutral, the narrower 120 VAC (Volts A.C.).

First, check to make sure that the ground pin works. Set your VOM to AC scale greater than 120 VAC. Stick one prong of the VOM probe to the outlet round ground slot. Stick the other to the smaller rectangular slot. You should see roughly 120 VAC. This means the ground is connected. Remove probe from 130 VAC hot slot to wider neutral slot. You should see 0 Volts. Measure across neutral and hot. You should see roughly 120 VAC. If socket is not grounded, then the next steps won't work.

I leave the computer box plugged into the outlet, switch off the power supply from the external on-off switch by the power supply. Then touch my hands to the metallic chassis of the computer cabinet to bleed off any static electricity on my body. Then without moving or walking (you don't want to gain static electricity you just bled off), pick up the CPU that I previously placed close to me and install it in the socket.

If you don't have a power supply that can be totally turned off or aren't comfortable, you can put a small diameter jumper wire with about 3/4 inch of insulation removed to one of the mounting screws provided it has a functioning ground. A continuity check between the outlet plate mounting screw, hot and neutral will verify whether it is grounded. Put remove insulation on the other end and place under one of the case screws. This should bleed off any static electricity from the case.

Older homes and facilities built before the mid 1960's may only have ungrounded outlets. Some have ungrounded outlet boxes. Some, people have later installed 3 prong outlets, but the ground pin may not be grounded as there is no grounding wire in the wiring. A quick check with the VOM or physical inspection by removing the outlet cover plate will verify this.




The question: Which grounding method? is now answered.  The answer is: Both.  Only touching the case is not sufficient if the case is not grounded. But wearing an anti-static bracelet is not necessary when touching a grounded case, immediately before handling a CPU, IF you do not walk and re-accumulate ESD (If moving around, wear the bracelet).

@George_Hostler
Question: You said, "First, check to make sure that the ground pin works. Set your VOM to AC scale greater than 120 VAC. Stick one prong . . . "

Would that be the red positive or the black negative prong?

---

### Post by mips on 2015-01-16
> **lisati said:**
> A thought before the pedants jump in: even though most would probably know what is being referred to, the terms "positive" and "negative" only really work if you're using DC. All of the electrical outlets in my place use AC.


Yeah people should be using the terms Neutral, Live & Earth/Ground.

---

### Post by UsrBinSomething on 2015-01-16
If the room is carpeted, I put newspaper down and I touch the case. I have it plugged into the ground and make sure the power is switched off. I always make sure other people aren't poking around inside the case and touching things.

---

### Post by tgalati4 on 2015-01-16
To properly ground a clean room for dealing with sensitive electronics (like building a spacecraft), one should drill three holes in the room about 8 feet apart.  Drive a 10' copper-coated steel pole into each hole.  Attach a heavy-gauge copper wire to each with copper clamps and attach to a copper strip around the room.  Don't forget to drill watering holes near each pole, since the ground needs to be moist for the grounding rods to function properly.

Or just touch the case.

---

