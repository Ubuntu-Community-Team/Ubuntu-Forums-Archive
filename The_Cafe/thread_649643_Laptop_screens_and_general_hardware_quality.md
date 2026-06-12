---
title: "Laptop screens and general hardware quality"
date: 2007-12-25
forum: The Cafe
---

### Post by Ebuntor on 2007-12-25
Hi everyone, Merry Christmas. :)

For some reason my laptop's screen suddenly has to stay at 90**° **so the screen will stay on. If I move it back a bit further it will turn off.
I assume this isn't a software problem and isn't related to Ubuntu in any way, that's why I didn't post in a support section. 

So my question is is anyone familiar with this problem? Is it common among laptops, just a simple hardware problem and could I fix it myself?

A few months back I also had a problem with the AC connection and I had to send it back to the manufacturer. If this is another hardware problem I think I just have a very low quality laptop and I'll start looking for a new one.

---

### Post by macogw on 2007-12-25
Could be a loose cable.

Pop off the rubber bits on the front and unscrew the screws under them.  Use a flat-head screwdriver to pop the front off (just slide it in the edge).  Unscrew the sides of the screen, and behind the screen there's a ribbon cable.  Make sure it's in nice n tight. Also check that the little cable is tightly attached to the circuit board at the bottom of the screen (should have a small plastic end and I think 2 little wires sticking out).  If that doesn't help, pop the board along the top of the keyboard (where the power button likely is) off using a flat screwdriver on the end and make sure the other end of the ribbon cable previously mentioned is properly attached to the motherboard (probably a large metal block on the end, press it down).

---

### Post by init1 on 2007-12-25
> **Ebuntor said:**
> Hi everyone, Merry Christmas. :)

For some reason my laptop's screen suddenly has to stay at 90**° **so the screen will stay on. If I move it back a bit further it will turn off.
I assume this isn't a software problem and isn't related to Ubuntu in any way, that's why I didn't post in a support section. 

So my question is is anyone familiar with this problem? Is it common among laptops, just a simple hardware problem and could I fix it myself?

A few months back I also had a problem with the AC connection and I had to send it back to the manufacturer. If this is another hardware problem I think I just have a very low quality laptop and I'll start looking for a new one.
It's never been a problem for me. What brand?

---

### Post by gn2 on 2007-12-26
> **Ebuntor said:**
> 
For some reason my laptop's screen suddenly has to stay at 90**° **so the screen will stay on. If I move it back a bit further it will turn off.
I assume this isn't a software problem 

It's very definitely not a software problem.

As has been suggested it could be a ribbon cable fault, it could also be a conventional cable.

The continued opening and closing can wear cables out.

They can usually be replaced if you can find a suitable replacement, eBay is a good place to look.

Exactly how the cable and connectors are accessed varies from laptop to laptop.

If you do disassemble a laptop, get a sheet of paper and tape the screws to it as you go with a description of exactly where it came from.
Taking pictures with a digital camera also helps.

You can usually find exploded diagrams for your laptop or detailed how-to's on the net.

---

### Post by popch on 2007-12-26
I second the notion that it is a hardware problem. It happened to one or two of my laptops. If the warranty is still applicable, that would be the obvious course of action.

The cause is either a cable worn out by metal fatigue or repetitive stress by bending at the hinge or by rubbing on an edge or something of that sort.

If you are lucky, you have a laptop which supplies the power for the screen over a sliding contact in a hinge. In that case, cleaning the contact could sufffice, provided you can locate it.

Sadly enough, most laptops live longer if they are not opened and shut so often.

---

### Post by mips on 2007-12-26
+1 for Hardware problem. Angle of the disply/hinges has nothing to do with software. My guesse would be a cable problem.

---

### Post by Ebuntor on 2007-12-26
Merry Christmas, thanks for your replies.

I did a bit of research and I found lots of people have had a similar problem. [This]("http://emperor.tidbits.com/TidBITS/Talk/1008/") is the best site I found. [http://emperor.tidbits.com/TidBITS/Talk/1008/](http://emperor.tidbits.com/TidBITS/Talk/1008/)

> As someone who sells laptop parts for a living, I can tell you that the LCD is made up of three parts: the screen itself, the backlight (light bulb), and the inverter. 

The inverter is a circuit board that increases the voltage so that the backlight can light the screen. It is much more likely that this is the problem, but it is not always the case. The inverter can be replaced by someone who knows what they're doing, while the backlight is much more difficult to replace. 
I too can still faintly see the desktop. The difference is my screen will work all the time at 90**° **but I found that if I move the screen back **very** slowly it will still stay on. 
So could that too can be problem with the inverter or a cable? 

My laptop is a Fujitsu Siemens Amilo Pa 1510.
And yes, luckily the warranty still is applicable. 

I don't think it's a very good idea to open it up thought. First I'm pretty sure I'll lose my warranty if they find out and second I'm not familiar with laptop hardware, pc's yes but a laptop is a completely different (and more complex) world IMO.

---

### Post by popch on 2007-12-26
The cable connecting the display to the laptop is frayed or broken. If you see stuff on your display but dimly, the lamp behind your screen does not get any electrical power. 

Do not try to open the display. Bring the PC back and have it repaired under the terms of your warranty. If you have private data on the hard disk, remove the disk before bringing the PC back.

---

### Post by mips on 2007-12-27
> **Ebuntor said:**
>  The difference is my screen will work all the time at 90**° **but I found that if I move the screen back **very** slowly it will still stay on. 
So could that too can be problem with the inverter or a cable?

It's a cable problem, willing to bet money on it ;)

---

### Post by Ebuntor on 2007-12-27
> **popch said:**
> The cable connecting the display to the laptop is frayed or broken. If you see stuff on your display but dimly, the lamp behind your screen does not get any electrical power. 

Do not try to open the display. Bring the PC back and have it repaired under the terms of your warranty. If you have private data on the hard disk, remove the disk before bringing the PC back.

Ok, thanks, I'll do that. About the hard disk, don't think that's a good idea with my warranty. Besides do you think most repair services are familiar with Linux distros and the EXT3 filesystem?

---

### Post by popch on 2007-12-27
> **Ebuntor said:**
> (...) About the hard disk, don't think that's a good idea with my warranty. Besides do you think most repair services are familiar with Linux distros and the EXT3 filesystem?

The hard disk usually is easily accessible. The part of the case holding it has the appropriate symbol and the screws can be used with a normal screwdriver. That's different from other parts of the case which you are not supposed to open. Hence, you can argue that it is a user serviceable part.

However, removing the hard disk is only worth your while if you have data or documents there you do not want anyone else to see. In that case, I would like to see the repair shop or manufacturer who refuses to repair your display when you took the appropriate measures to protect the privacy of your data.

Knowing the file system is not really necessary for the shop to look at your data. Booting the PC with a live CD and running as root is usually sufficient to do so.

---

### Post by gn2 on 2007-12-27
> **Ebuntor said:**
> 
I too can still faintly see the desktop. 

It's definitely inverter/backlight related then.

Loose connection or worn wiring from the motherboard to the inverter or perhaps (but unlikely) the inverter itself.

The switch that controls the screen off function can also be sticky and play up.

But I reckon it's the inverter wiring.

Inverter faults are the major cause of screen difficulties on laptops and can usually be rectified very easily.

---

### Post by mips on 2007-12-27
> **gn2 said:**
> It's definitely inverter/backlight related then.

Loose connection or worn wiring from the motherboard to the inverter or perhaps (but unlikely) the inverter itself.

The switch that controls the screen off function can also be sticky and play up.

But I reckon it's the inverter wiring.

Inverter faults are the major cause of screen difficulties on laptops and can usually be rectified very easily.

How do you get to that conclusion?
> I too can still faintly see the desktop. [COLOR=Red]The difference is my screen will work all the time at 90**° **but I found that if I move the screen back **very** slowly it will still stay on.[/COLOR] 

Seems to indicate it works fine if he does not rapidly change the angle of the display/lid.

---

### Post by gn2 on 2007-12-27
> **mips said:**
> How do you get to that conclusion?

Because if the main cable to the screen was damaged there would be no display at all.
The OP has stated that the screen is faintly visible at all angles which means it can only be a fault with the inverter, the backlights or their wiring.
The fact that it is intermittent and angle related points to it being the inverter/backlight cabling or at a longshot the switch for the screen off on lid close.

---

