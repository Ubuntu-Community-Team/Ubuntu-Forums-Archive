---
title: "running desktop off inverter was working now wont work"
date: 2011-08-26
forum: The Cafe
---

### Post by sdowney717 on 2011-08-26
the inverter runs the fridge, lights, power tools, the PC  monitor etc... and used to run the PC power supply. 3000 watt 6000 peak MSW.
Now when I plug in the PS cord I get aloud zap and spark at the plug and the inverter output goes dead. Have to turn inverter off then on to reset the power.
The inverter still runs everything else fine.
Strangely, IF I plug in the PS PC to a regular wall outlet, there is no zap, no spark sound and it works normally.

Could the PS of the PC have a ground fault short?

---

### Post by morgan141 on 2011-08-26
> **sdowney717 said:**
> the inverter runs the fridge, lights, power tools, the PC  monitor etc... and used to run the PC power supply. 3000 watt 6000 peak MSW.
Now when I plug in the PS cord I get aloud zap and spark at the plug and the inverter output goes dead. Have to turn inverter off then on to reset the power.
The inverter still runs everything else fine.
Strangely, IF I plug in the PS PC to a regular wall outlet, there is no zap, no spark sound and it works normally.

Could the PS of the PC have a ground fault short?

Why do you want to run a computer through an inverter? :confused: I guess a better question is, what country are you from?

---

### Post by sdowney717 on 2011-08-26
I am in the US on the east coast in the path of Irene and the computer is on my boat.

---

### Post by morgan141 on 2011-08-26
> **sdowney717 said:**
> I am in the US on the east coast in the path of Irene and the computer is on my boat.

Ah, that makes sense :). Sorry I was a little confused as to when you'd have a DC source in your house, but that makes sense.

I'm not really sure what to suggest, I'm afraid I'm no electrical engineer (I'm a physicist :p). Power supplies are very sensitive to fluctuations in the source though, you don't happen to have an oscilloscope at hand? :D

---

### Post by sdowney717 on 2011-08-26
No, but the computer had some very large mud dauber nests and when cleaning out the dried mud some fell into the slots of the PS but I dont know if it matters.

Strange thing is plug it into the inverter and it is like a short, but plug into shore power no sparks.
perhaps the neutral to ground is shorting in the PS, as another wasp nest inside it.:P

These mud daubers made a mud nest 3 inches long and 2 inches wide sitting next to the add on USB PCI card and one on top of the hard drive. I cleaned that off.

---

### Post by morgan141 on 2011-08-26
> **sdowney717 said:**
> No, but the computer had some very large mud dauber nests and when cleaning out the dried mud some fell into the slots of the PS but I dont know if it matters.

Strange thing is plug it into the inverter and it is like a short, but plug into shore power no sparks.
perhaps the neutral to ground is shorting in the PS, as another wasp nest inside it.:P

These mud daubers made a mud nest 3 inches long and 2 inches wide sitting next to the add on USB PCI card and one on top of the hard drive. I cleaned that off.

Erm, I would say that is significant yes!

I don't know what a mud dauber is (I'm from the UK and I don't think they are around in Europe) but I suspect it damaged the PSU. Even if you get it working off your inverter you risk damaging components in the computer, hell even an electrical fire. 

Replace the PSU immediately, it's not worth the risk.

---

### Post by LowSky on 2011-08-26
Mud inside a PC... yeah not good.

Remember a computer uses electricity. electricity and water, especially salt water is bad for a computer. 

Never heard of a Mud dauber.. We just call them Wasps (no real distinction in breeds) up here in NY.

---

### Post by XubuRoxMySox on 2011-08-26
I wonder if that is "normal" for some inverters or something.

I took my desktop with me for a couple of weeks in an 18-wheeler because my laptop died and I had to finish school (online) while on the road with Papa. It sparked and zapped and scared the heck out of me every time, but it ran okay. I would only run it for just the time I needed to do some schoolwork and keep up with a few contacts whenever we could find some wifi.

Maybe your boat and Papa's truck aren't all that different. Except my inverter was only 800 watts attached to a 12-volt battery.

Be safe out there dodging the hurricane!

---

### Post by Inodoro Pereyra on 2011-08-26
It's not because of the mud dauber (whatever that is).

There are basically 2 kinds of power inverters: Pure Sine Wave, and Pseudo Sine Wave. Pure sine wave inverters are way more expensive than pseudo sine wave ones.

Pure sine wave inverters will run anything you connect to them (well, **most** anything) without a problem, as the wave form they deliver is as close as the normal power grid waveform as can be expected (good quality units can have a distortion of less than 1%). 

Pseudo sine wave inverters (you may find them under different names, all pointing to the fact that the output waveform is not a sine wave), deliver a more or less square wave at their output. That square wave is adequate for running things like a fridge (as you already found out), because fridge motors are not picky, as long as they get an AC signal, or a laptop (although they may cause some PS overheating), because the electronics are protected by the batteries, but, when you try to use then on a desktop, or a TV set, the power supply has a very tough time trying to filter the high harmonics content of the incoming signal, and part of those harmonics will pass through, and cause all sort of issues. 

I could bet you money that, if you open up your computer PS, you will find at least one bloated capacitor, or any other sign that one or more components are nearing the end.

Bottom line: don't ever plug a desktop PC, or a normal TV set, etc, to a pseudo sine wave inverter. You can consider yourself very lucky that the PS wasn't more resilient, or the damage could've happened to the MoBo, or the hard drive. Either get a good quality, pure sine wave inverter, or get a laptop computer (preferably with a car charger, or keep an eye on the PS temperature), and a 12V TV set.

Finally, I hope this is understandable, and I apologize if it isn't. English is not my native language... :)

And good luck with Irene!!! :)

---

### Post by sdowney717 on 2011-08-26
yes could be bad the PS.
I think a UPS made for the PC would work, let inverter power the UPS which powers the PC.
The inverter runs the TV ok.
Bothers me that the inverter used to run the PC ok, so either the PS damaged by inverter or on its last legs. It is an old 300 watt PS, likely about 8 years old.

[IMG]http://pestcontrolcanada.com/INSECTS/bymudd_s.jpg[/IMG]
> Mud daubers are black and yellow, thread-waisted, solitary wasps that build a hard mud nest, usually on ceilings and walls, attended by a single female wasp. They are not social wasps but may be confused with them. They do not defend their nests and rarely sting. During winter, you can safely remove the nests without spraying.



I have never been attacked or stung by these.
typical nest, mud is dry and filled with hollow channels. The wasps catch a lot of spiders to feed to the young.

Wow , that is a huge picture!

---

### Post by Inodoro Pereyra on 2011-08-26
Yes, some UPS systems would work, but I can't guarantee you all of them will.

IMHO, you'd be much better off buying a cheap laptop or netbook, and leaving the inverter for other things. 

Thanks for the pics. Now I know what you meant.

---

### Post by Tibuda on 2011-08-26
> **dixiedancer said:**
> I wonder if that is "[color="purple"]**normal**[/color]" for some inverters or something.

I took my desktop with me for a couple of weeks in an 18-wheeler because my laptop died and i had to finish school (online) while on the road with papa. It sparked and zapped and scared the heck out of me every time, but it ran okay. I would only run it for just the time i needed to do some schoolwork and keep up with a few contacts whenever we could find some wifi.

Maybe your boat and Papa's truck aren't all that different. Except my inverter was only 800 watts attached to a 12-volt battery.

Be safe out there dodging the hurricane!

**[size="3"][color="purple"]Robin[/color][/size]**

ftfy

---

### Post by sdowney717 on 2011-08-26
ok, replaced PS with one from a Compaq and it now works fine with the inverter. So something wrong with the PS.
I did not think I was crazy.

Hurricane prediction will be down to cat1 for us. Happy cause it would be exciting to experience a worse storm, but sad when it hits you personally.

---

### Post by XubuRoxMySox on 2011-08-26
> **Tibuda said:**
> ftfy

??? Not familiar with that abbreviation, "ftfy."

---

### Post by dave01945 on 2011-08-26
> **dixiedancer said:**
> ??? Not familiar with that abbreviation, "ftfy."

fixed that for you

---

### Post by mips on 2011-08-27
> **sdowney717 said:**
> 
I have never been attacked or stung by these.
typical nest, mud is dry and filled with hollow channels. The wasps catch a lot of spiders to feed to the young.

They are pretty common over here as well. Also never been stung by one but they do make me nervous when flying around inside the house.

---

