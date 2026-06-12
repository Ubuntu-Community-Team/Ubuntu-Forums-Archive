---
title: "Leave power cord connected when working on computer"
date: 2009-09-11
forum: The Cafe
---

### Post by lindsay7 on 2009-09-11
From another thread there was a debate on which is the better and safer way to work on computers.

1. Disconnect the power cord when opening the case and working on your computer. This done to prevent electircal shock and or damage to componets.

2. Leave the power cord in the computer and attached to the wall socket to provide a ground to the machine when working on your computer. This is done to provide a ground for static discharge.

What is your opinion?

---

### Post by chessnerd on 2009-09-11
Well, I've never heard of using a power cable as a ground before, but I doubt the benefit of a ground would be safer to the user than no power running. Case and point:

I once had to disconnect a broken fan from a computer's power supply. No big deal, right? Well, the cable for the fan happened go inside the power supply case (poorly designed in my opinion, but that's what I had to work with). Before doing this I unplugged the computer and then tried to run it over and over again to empty the capacitors. Then I VERY CAREFULLY removed the cable without touching anything else inside the power supply. After that I connected the new fan to the motherboard so I wouldn't have to put myself at risk again. If the power supply was active during this I would probably be dead and even with the capacitors supposedly drained I was nervous the whole time because a power supply case is not a place you want to mess around in.

---

### Post by mcduck on 2009-09-11
> **chessnerd said:**
> Well, I've never heard of using a power cable as a ground before, but I doubt the benefit of a ground would be safer to the user than no power running. Case and point:

I once had to disconnect a broken fan from a computer's power supply. No big deal, right? Well, the cable for the fan happened go inside the power supply case (poorly designed in my opinion, but that's what I had to work with). Before doing this I unplugged the computer and then tried to run it over and over again to empty the capacitors. Then I VERY CAREFULLY removed the cable without touching anything else inside the power supply. After that I connected the new fan to the motherboard so I wouldn't have to put myself at risk again. If the power supply was active during this I would probably be dead and even with the capacitors supposedly drained I was nervous the whole time because a power supply case is not a place you want to mess around in.
If you leave the power cord plugged in you of course shut down the main power, using the switch in the PSU.. I don't think anybody would actually recommend touching your computer's components with power turned on. :D

The grounding will still work, but there's no risk of getting shocked as long as you don't start messing with the insides of the PSU itself (which you should never do unless you are a qualified electrician)

---

### Post by lindsay7 on 2009-09-11
From the limited discussions on this tread and the other one which prompted this post, it seems that Europeans are comfortable leaving the power cord attached and North Americans are not.

Instructions that come with pci cards and add on drives always talk about removing the power cord before opening the case to add these components. I have never seen instructions for adding computer parts suggest leaving the power cord attached to the computer and plugged into the outlet, even if the power switch turned off.

---

### Post by gordintoronto on 2009-09-11
I leave the power cord attached if possible, with the power off, of course.

I had one funny experience: I was installing a PCI audio card, and as soon as I plugged it in, the computer powered up!  I had to change a BIOS setting to shut down the computer with that PCI card installed.

By the way, the highest voltage inside a computer case, excluding the power supply itself, is 12 volts.  I doubt if 12 volts has ever done any damage to a human being.

---

### Post by Whiffle on 2009-09-11
I leave it attached.  The benefit of having ground is a valid reason to leave it connected (especially if you're connecting a grounding strap to it or grounding yourself to the case).  Additionally, the only voltages you'll find outside of the PSU are 3.3V, 5V, and 12V, for the most part, and they aren't nearly enough to shock you.  Maybe...*maybe* if you licked your motherboard with it running, you'd feel something.

---

### Post by benj1 on 2009-09-11
> **Whiffle said:**
> Maybe...*maybe* if you licked your motherboard with it running, you'd feel something.

what ever floats your boat ;)

---

### Post by subdivision on 2009-09-11
I usually disconnect the power cord so I can get the machine out from under my desk. Otherwise I've got to sit underneath which is extremely uncomfortable.
 
If the cord was long enough that I didn't have to do that I would still probably unplug it. Better to err on the side of caution in my opinion.

---

### Post by mcduck on 2009-09-11
> **Whiffle said:**
> I leave it attached.  The benefit of having ground is a valid reason to leave it connected (especially if you're connecting a grounding strap to it or grounding yourself to the case).  Additionally, the only voltages you'll find outside of the PSU are 3.3V, 5V, and 12V, for the most part, and they aren't nearly enough to shock you.  Maybe...*maybe* if you licked your motherboard with it running, you'd feel something.

The only voltage you'll find outside the PSU, after you've turned the PSU off using it's own power switch, is simple 0V.

If your PSU doesn't have a power switch you definitely should unplug it from the wall when messing with insides of the system. Not to protect yourself, but to protect the hardware.

---

### Post by Chronon on 2009-09-11
Uh. . use a grounding strap?  I don't really get how grounding the circuit is going to prevent static charge on your body from discharging through a circuit element.  What you want to do is to connect yourself to ground so that you don't have a large voltage compared to the circuit you're working on.  Grounding the circuit and touching it with a finger that has a (few) thousand volts worth of surface charge built up on it doesn't sound like a good idea to me.

---

### Post by SaintDanBert on 2009-09-11
> **lindsay7 said:**
> From another thread there was a debate on which is the better and safer way to work on computers.

1. Disconnect the power cord when opening the case and working on your computer. This done to prevent electircal shock and or damage to componets.

2. Leave the power cord in the computer and attached to the wall socket to provide a ground to the machine when working on your computer. This is done to provide a ground for static discharge.

What is your opinion?

I vote Plugged-in with Power-off for most in-case workings, but there
are exceptions and cautions.

First, a lesson.  In the US, we talk about "chassis ground" and "safety ground" or "signal ground" and similar.  Elsewhere, there is a huge distinction between various "ground" connections and "Earth" (as in dirt).
The third wire of your power cord connects the power supply chassis to the
house wiring [what elsewhere calls "mains"] bare copper ground wire.
This wire goes to your breaker panel. There is a large conductor that
connects that breaker panel to Earth for your electrical service.

Static electricity wants to find Earth by the path of least resistance
-- Ohm's law type resistance.  Since your power supply is bolted to your
computer case, touching that case provides a direct path to Earth
through your power cord. When unplugged, any static has no place to go
except to jump around and through everything searching for a path to Earth. In the rare case when something does go wrong electrically, your
cord also provides a path to Earth for any other stray currents that
might want to do harm.

Remember, it is not the VOLTAGE that does the damage. It is the CURRENT.
When current passes through any RESISTANCE [your body] you get heat.
Think about a toaster or space heater. While the computer may only have
5 and 12 volts DC in most places, even 100 milli-amps may be lethal given
the correct path through your body. [see [http://en.wikipedia.org/wiki/Electric_shock]](http://en.wikipedia.org/wiki/Electric_shock])

In my training as electronics technician, we were taught to work with one hand, wear rubber sole shoes and work on an insulating mat. Any contact with live circuits would be limited to that one hand and arm.

As always, if you don't know -- REALLY KNOW -- what you are doing, then
hire someone who does.

~~~ Saint 0;-D

---

### Post by lindsay7 on 2009-09-11
This is from the Dell web site.

> Safety First &#8212; For You and Your Computer

Working inside your computer is safe&#8212;if you observe the following precautions.
caution.gif (709 bytes) 	CAUTION FOR YOUR PERSONAL SAFETY AND PROTECTION OF YOUR EQUIPMENT

Before starting to work on your computer, perform the following steps in the sequence indicated:

   1. Touch an unpainted metal surface on the computer chassis, such as the power supply, before touching anything inside your computer.

      While you work, periodically touch an unpainted metal surface on the computer chassis to dissipate any static electricity that might harm internal components. Also avoid touching components or contacts on a card and avoid touching pins on a chip.
   2. Turn off your computer and all peripherals.

   3. Disconnect your computer and peripherals from their AC power sources. Also, disconnect any telephone or telecommunication lines from the computer. Doing so reduces the potential for personal injury or shock.

   4. If you are disconnecting a peripheral from the computer or are removing a component from the system board, wait 5 seconds after turning off the computer before disconnecting the peripheral or removing the component to avoid possible damage to the system board.

In addition, Dell recommends that you periodically review the safety instructions in your System Information Guide.



Also, from


[http://www.tips4pc.com/Articles/Computer%20Maintenance/how_to_open_a_computer_case_safe.htm](http://www.tips4pc.com/Articles/Computer%20Maintenance/how_to_open_a_computer_case_safe.htm)






How To Open A Computer Case Safely with the correct tools
	 

   1. Remove all power cords that are connected to the computer case.
   2. This includes network cables, modems, printers, everything...Wait a few seconds as the power leaves the mainboard.
   3. Make sure your hands are clean and definitely DRY. Remove all jewelry.

---

### Post by gn2 on 2009-09-11
I disconnect the power cord for safety reasons.
AFAIK the hazard to your components is static discharged from you to the components, so before touching any components, I grab the chassis firmly with both hands.
And I don't work in a carpeted room.....

---

### Post by Chronon on 2009-09-11
> **gn2 said:**
> I disconnect the power cord for safety reasons.
AFAIK the hazard to your components is static discharged from you to the components, so before touching any components, I grab the chassis firmly with both hands.
And I don't work in a carpeted room.....

Why not keep yourself tethered to it?

[http://en.wikipedia.org/wiki/Antistatic_wrist_strap](http://en.wikipedia.org/wiki/Antistatic_wrist_strap)

---

### Post by mcduck on 2009-09-11
> **lindsay7 said:**
> This is from the Dell web site.

As you may have noticed, the Dell guide actually tells you to *first* touch the case metal to ground yourself, and *then* to pull of the power cord..

Just touching the case metal won't do that much unless the charge has somewhere to go. That somewhere being ground through the power cord.

But in the end both ways work just fine as long as you pay attention to what you are doing and don't start rubbing the internals of your system with synthetic fabrics, cats or other highly static things.. :D

---

### Post by Hyporeal on 2009-09-11
> **SaintDanBert said:**
> While the computer may only have
5 and 12 volts DC in most places, even 100 milli-amps may be lethal given
the correct path through your body. [see [http://en.wikipedia.org/wiki/Electric_shock](http://en.wikipedia.org/wiki/Electric_shock)]

According to the linked Wikipedia article, the resistance of skin ranges from about 1000 Ohms (wet) to 100,000 Ohms (dry). In order to achieve 100 mA at 12 V, you would have to create an effective resistance no greater than 120 Ohms through your body. That doesn't sound plausible to me.

---

### Post by lindsay7 on 2009-09-11
mcduck, I agree.

In the US homes that are built to code provide 115 volts service with three prong connection at the wall outlets. One live is 115 volts to the common or second power line.  The third line is the system ground (usually a driven metal rod into the earth at the power service location).  With good service the common line and the system ground have the same ground potential. But this is not always the case as the common line and system ground can be of different potentials to ground.  This can be seen as a voltage between the common and the system ground.

Anyway, what I do is disconnect the computer from the wall outlet by removing the power cord and then ground the computer case to the system ground point to discharge any static.

---

### Post by lindsay7 on 2009-09-11
Hypreal, what you are not taking into account is a ground fault in the system with the 115v in the US. Other countries run their systems at 230 volts.  A "bolted" ground fault is one directly to ground and would cause the circuit breakers to trip. If the ground fault is a high resistance type, then their would be a currant leakage to ground. If a person gets involved with type of ground fault they could either complete the circuit to ground as a series or parallel resistance component in the system and could put them at risk.

---

### Post by gn2 on 2009-09-11
> **Chronon said:**
> Why not keep yourself tethered to it?

No need, I don't work in a carpeted area and don't wear clothing made from synthetic materials.

---

### Post by benj1 on 2009-09-13
> **Chronon said:**
> Uh. . use a grounding strap?  I don't really get how grounding the circuit is going to prevent static charge on your body from discharging through a circuit element.  What you want to do is to connect yourself to ground so that you don't have a large voltage compared to the circuit you're working on.  Grounding the circuit and touching it with a finger that has a (few) thousand volts worth of surface charge built up on it doesn't sound like a good idea to me.

the grounding strap grounds you so you dont have a static charge, its attached to the pc frame (if the pc is plugged in), not any of the circuits because its attached to the earth cable and so should ground though that, not anything important.

the idea of leaving it plugged in, but switched off is so the pc is always grounded so you shouldnt get any static build up.

---

### Post by red_Marvin on 2009-09-13
As long as you make sure that the voltage difference between you and the chassis is 0 it should be ok, that is what matters.

---

### Post by Chronon on 2009-09-13
> **benj1 said:**
> the grounding strap grounds you so you dont have a static charge, its attached to the pc frame (if the pc is plugged in), not any of the circuits because its attached to the earth cable and so should ground though that, not anything important.

the idea of leaving it plugged in, but switched off is so the pc is always grounded so you shouldnt get any static build up.

Circuit ground and chassis/safety ground are not directly tied together and it's preferable to connect to the latter; you are correct.  It's only important (for preventing electrostatic discharge) to dump excess charge so that your potential is close to that of the circuit elements.  Any conductive mass that's large enough will serve as an effective ground for this purpose.  The chassis, with the power cable connected certainly fits this bill.  I would guess that a typical computer chassis would probably work as a ground as well even when disconnected from the wall.

Preventing static discharge is the only reason I would ground myself.  This really only applies to working on open circuits (i.e. turned off).  Grounding yourself is not a safety precaution for you, it's for the components.  You're actually better off floating with hot than allowing it to find ground through you (e.g. Van de Graaff generator).

---

### Post by alienclone on 2009-09-13
i have plugged in and unplugged memory, vid cards, and nic cards with my pc ON many many times with no problems.

---

### Post by tom66 on 2009-09-13
I've never used an antistatic thing. 

I've fried two video cards... But apart from that everything else survived!

Oh, and running the computer without the power cable to drain the caps sometimes isn't adequate. The PSU has an undervoltage circuit which'll cut off long before the caps are drained. There's usually a couple of 200 volt caps in there, those are the ones you need to be careful of. Short them out with a screwdriver or similar well-insulated tool and you'll be fine (though don't do this lots because it shortens the life of the caps.)

---

### Post by ssam on 2009-09-13
[uk wall sockets]("http://images.google.co.uk/images?q=uk+wall+socket") typically have on/off switches. if you switch it off the appliance is still grounded, but there is no 240 volts.

whats the resistance of the body? can 12 volts get enough current over that resistance? also isn't max of 24 volts on a motherboard, between the +12V and -12V.

---

### Post by Barrucadu on 2009-09-13
> **ssam said:**
> [uk wall sockets]("http://http://images.google.co.uk/images?q=uk+wall+socket") typically have on/off switches. if you switch it off the appliance is still grounded, but there is no 240 volts.

You mean some other countries don't have switches on their sockets?

---

### Post by Old_Grey_Wolf on 2009-09-13
> **red_Marvin said:**
> As long as you make sure that the voltage difference between you and the chassis is 0 it should be ok, that is what matters.

I agree with you. 

For the readers of this thread:
Even if you and the computer had 1000 volts of charge, it wouldn't matter as long as you and the computer have the same voltage. Current only flows if there is a difference in voltage. A ground strap works by keeping the voltage the same. Touching an unpainted surface does as well, if done frequently enough in the right environment.

I wouldn't recommend connecting a ground strap to the power supply capacitor though. The difference in your initial voltage and the capacitor's initial voltage is very significant. It could result in a large current. :)

Think of voltage as the pressure in a water supply, and current as the movement of the water between systems with different pressures.

---

### Post by NovaAesa on 2009-09-13
I got zapped by a few thousand volts from my computer when I decided it would be a good idea to plug in a UV flourescent lamp into one of the 5V molex cables... while the whole thing was still turned on.

---

### Post by pwnst*r on 2009-09-13
unplug, use grounding strap.

done.

---

### Post by NinjaNumberNine on 2009-09-13
I think the safest way to do anything on the computer is run it without power- very energy efficient and no viruses- guaranteed. (For all you Windows nuts) With Linux, there are no crashes, guaranteed. Also you won't notice any changes if the power goes out. :D

---

### Post by toupeiro on 2009-09-13
I generally leave it plugged in, but flip the master power switch on the PSU off, because its more convenient.  When you've worked on hardware long enough, you get comfortable with the amount of risk you are willing to take.  For example, I'll leave the power cord plugged in with the PSU off, on a kitchen counter, before I will work without an ESD strap even on a grounded workbench.  The general statistic (and I'll try to find it, but I read it sometime ago) is that 90% of all hardware failures, whether immediate or gradual, are caused by ESD.

---

### Post by hessiess on 2009-09-13
Unless you opened the PSU, none of the exposed components with a computer have a high enough potential difference to drive a lethal current though the relatively high resistance of the human body. It is far more lickly that you will damage components from static or shorting, so leaving the power cord connected but the PSU off is actually better as it keeps everything grounded.

---

### Post by doorknob60 on 2009-09-13
I do, but just for convinience. I turn the switch off of course though, unless I'm being real lazy or just forgetful (if I'm just plugging in a PCI card that came loose or something then I don't bother).

---

### Post by zman58 on 2009-09-13
NEVER ever work on a PC that is plugged into a live power outlet. Always unplug it. If you are worried about grounding then get a grounding strap on both you and the PC chassis. It is generally unsafe to work on any electrical appliance while plugged into a live outlet.

Of course if you are in the mood for taking a risk and feel you know "exactly" what you are doing then anything goes.

Generally you should not have to worry about static discharge if you make sure you are touching part of the computer chassis while inserting parts or touching any electrical components. That is because as you touch the chassis you become at the same potential voltage as the chassis--so reduce or eliminate the chance of producing a static shock.

---

### Post by CharmyBee on 2009-09-13
I always unplug before I do anything, like even plugging in the power for a side panel fan. My older brother loves to tempt and do stupid things like insert memory just seconds after power off with the cord still in.

---

### Post by lisati on 2009-09-13
> **Barrucadu said:**
> You mean some other countries don't have switches on their sockets?

Most of the places I've lived in have had switched power outlets. The only exception I can think of was a one-bedroom flat back in the early 1990s that had a couple of unswitched outlets in the bedroom. Judging by the appearance I think they were put in when the place was built (possibly in the 1960s) Changing one of them over to a double switched outlet was easy enough, but I probably wouldn't do it these days, I think the regulations have changed since, making doing it of dubious legality without proper certification.

The main thing is safety, of both gear and person: to paraphrase an earlier post, "volts jolts, but mills (milliamps) kills". 

p.s. I haven't ever used an anti-static strap. The only thing I've had do anything near failing was an old 5.25" floppy drive that I temporarily had in my old desktop, but that was probably due more to age and wear and tear.

---

### Post by tom66 on 2009-09-14
Heh, I've pulled memory out of a PC because I was frustrated with it. The PC shut off and there was a shower of sparks to accomodate it. (The PC was old and not in use, and it still works.)

---

### Post by JillSwift on 2009-09-14
I leave the power cable plugged in to the back of the machine for the ground.
However, for safety from the 110 volts, I unplug the power cable from the wall.

... :confused:

Wait... something seems wrong here...

---

### Post by Regenweald on 2009-09-14
I was recently removing a video card from a machine that was plugged into a UPS but turned off. There were sparks and some smoke and that burnt plastic smell. i was terribly afraid that i had fried the Mobo and proc since the card had no power connection and the only link to the PSU was the mobo.

Turns out it was just the PSU that blew and i still have no idea what happened. Mobo and proc were fine, to my surprise and relief. So totally unplugged for me from now on.

---

