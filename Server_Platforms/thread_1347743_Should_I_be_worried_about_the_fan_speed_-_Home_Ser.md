---
title: "Should I be worried about the fan speed? - Home Server"
date: 2009-12-06
forum: Server Platforms
---

### Post by garfonzo on 2009-12-06
Hi Folks,

I have a Ubuntu file server for my home (just shares files, nothing fancy at all) which sits in our garage where it is always quite cool. It is a desktop PC I bought to use specifically for a file server. When I set it up about a year ago, I removed both side panels and the front cover of the tower to allow maximum air flow. I went a bit further and set up a small house fan which sits about two feet away from the open side and blows air into the system and replaced the case fan with a bit bigger one to draw out hot air. The effect is that there is always cool air moving across the motherboard. 

My concern is, for the past year the case fan (which is audible when you walk into the garage) has always had a consistent pitch (as in, the RPM is constant). I have noticed now, however, that the RPM is going up and down. Its lowest RPM is the 'norm' and then it will go up (spins faster) for roughly 30 seconds, then return to normal. It has been doing this for the past few days. If I were to liken it to a piano pitch, I'd say it goes up a half-tone, then down again (from C to a C#, then back down). Okay, that's a bizarre metaphor. 

Any thoughts? Should I be worried? No big deal? Just a fan dying?

Thanks,

Garfonzo

---

### Post by jdriessen on 2009-12-06
it is possible that your computer is full of dust and causing the temprature of the computer to rise and fall irregularly.
if you're uncertain as to whether the temperature of the components in you computer are at safe levels you can monitor them, there are several utilities available to you that you can use under linux (excuse me for being vague, but I can't remember of the top of my head what they are called).

---

### Post by jflaker on 2009-12-06
Bring the server down and open the case....If you are a bit of a cowboy, fire up the leaf blower for a few seconds and clean the case in one shot....If you want to surgically dust, a few cans of compressed air should do....

Clean the vents and keep them clear of dust....My bet is you have dust elephants inside.

---

### Post by trundlenut on 2009-12-06
by removing the side panels and the front your case fan is probably doing nothing to cool the machine.  It was designed to force air through a specific pathway in the machine to provide cooling, it can't do that now.  From what I understand simply removing the casing from a computer can cause temperatures to go up as you lose the movement of air over things like heatsinks.

Could be that the fan is on the way out.  What are the actual temperatures of the CPU, MB etc?  Can you also monitor fan speeds?

---

### Post by garfonzo on 2009-12-06
I'm confused... How does removing the panels, and blowing a 12inch house fan directly on the motherboard (way more air than a computer fan can produce), and another fan pulling air out of the case (thereby causing air to move across the motherboard) result in higher temperatures?

On another note, I ran lm-sensors:

```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +2.0Â°C  (crit = +80.0Â°C)

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +17.0Â°C
Core1 Temp:  +16.0Â°C

it8716-isa-0290
Adapter: ISA adapter
in0:         +1.07 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.18 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.30 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +2.94 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +3.01 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +1.89 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +1.15 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +2.83 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:        +3.04 V
fan1:       2184 RPM  (min = 3245 RPM)  ALARM
fan2:       2463 RPM  (min = 3245 RPM)  ALARM
fan3:          0 RPM  (min =    0 RPM)
temp1:        +2.0Â°C  (low  = +127.0Â°C, high = +82.0Â°C)  sensor = thermal diode
temp2:      +127.0Â°C  (low  = +127.0Â°C, high = +82.0Â°C)  ALARM  sensor = thermistor
temp3:      +127.0Â°C  (low  = +127.0Â°C, high = +82.0Â°C)  ALARM  sensor = thermistor
cpu0_vid:   +0.700 V

```

As far as I can tell, everything looks OK temperature wise. Anyone see any red flags? Are those "ALARM" areas to be worried about?

Thanks

---

### Post by ian dobson on 2009-12-06
Hi,

Have a look at the lm-sensors package. With the sensors command you can watch the CPU temperature/fan speed. There is also a program fancontrol which can be configured to maintain a specific temperature by controlling the fan speed.

Regards
Ian Dobson

---

### Post by trundlenut on 2009-12-06
look at the heatsinks on say the CPU, they are designed for air flow in a specific way.  Just blowing a large volume of air isn't going to guarantee good cooling.  Also you need to look at where the hot air goes, is it being taken away or just blown around.  If you consider a fan blowing into a box you will get all kinds of eddies and random flows build up.  even if you take one side away then you will set up a prefential pathway that may lead to some areas getting a lot of air flow and some areas probably naff all air flow.  Think what would happen if the air flow is perpendicular to the fins on a heat sink, you will not get good cooling as the flow of air will effectively be over a smaller area than if the flow was parallel to the fins.

My main server has I think about 9 fans in it which are fitted to provide a constant flow of air through the machine and are comlimented by various shrouds and bits of plastic to control and channel the air flow over the drives, memory and CPU to provide good cooling.  Because of this the cpus run at about 38 degrees C despite having 5 scsi drives and the fact that it sits under a worktop in the corner of my kitchen.

Though looking at your lm-sensors output something doesn't seem quite right about the temperatures, one is at 2 degrees and two are 127.  Also both fans appear to be running below their minimum speed.  I would have a look at the manual for the motherboard and see if you can find out what sensors are present.

---

