---
title: "Plastic vs Metal computer cases?"
date: 2009-02-21
forum: The Cafe
---

### Post by jamieh on 2009-02-21
I'm running three web servers in the basement. All three have identical hardware, but two have metal cases (White Antec case from ~2006), and one has a slightly older generic plastic case.

When I the air coming out the back of the PSU on all three, the two metal cased ones blow air that is quite cool.

However, the plastic cased one blows air like a furnace.

I'm not really liking all the "ALARM" labels in my lm-sensors command:

```
jamie@arcadefire:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +27.0°C                                    

w83627ehf-isa-0290
Adapter: ISA adapter
VCore:       +1.47 V  (min =  +0.00 V, max =  +1.74 V)   
in1:        +12.62 V  (min = +13.46 V, max = +13.46 V)   ALARM
AVCC:        +3.15 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
3VCC:        +3.15 V  (min =  +2.99 V, max =  +2.03 V)   ALARM
in4:         +2.04 V  (min =  +2.02 V, max =  +1.51 V)   ALARM
in5:         +1.61 V  (min =  +2.04 V, max =  +2.02 V)   ALARM
in6:         +4.25 V  (min =  +6.53 V, max =  +3.97 V)   ALARM
VSB:         +3.17 V  (min =  +4.08 V, max =  +2.02 V)   ALARM
VBAT:        +3.06 V  (min =  +1.52 V, max =  +3.76 V)   
in9:         +1.50 V  (min =  +0.50 V, max =  +2.04 V)   
Case Fan:   1028 RPM  (min =    0 RPM, div = 8)
CPU Fan:       0 RPM  (min =   83 RPM, div = 128)  ALARM
Aux Fan:    2033 RPM  (min = 2700 RPM, div = 4)  ALARM
fan5:          0 RPM  (min =    0 RPM, div = 16)
Sys Temp:    +26.0°C  (high = -101.0°C, hyst =  -6.0°C)  ALARM  sensor = thermistor
CPU Temp:    +26.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUX Temp:    +26.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +1.550 V
```

Are my temps okay or should I do something?

Thanks

---

### Post by spoons on 2009-02-21
Some of those voltages are all over the place. This might just be rubbish sensors or it might be the PSU failing, or just being crappy. It's a generic case so did you use the generic PSU? They are inefficient and of low quality, and may be the source of all the heat out the back. It's always a good idea to stay away from cheap *** PSU's and I'd recommend that you get a decent brand in there pronto, if only for the peace of mind that it won't blow up in your face.

---

### Post by Therion on 2009-02-21
Your temps look fine but whats UP with those voltages???

Methinks the PSU is a POS and your power is anything but "clean".  Time to spend a few bucks on a decent PSU.

---

### Post by Darkade on 2009-02-21
Your temp looks ok, I just'd like to add that metal cases, especcialy aluminum ones, are better to keep your system cool

---

### Post by Skripka on 2009-02-21
> **Darkade said:**
> Your temp looks ok, I just'd like to add that metal cases, especcialy aluminum ones, are better to keep your system cool

What is more important than mere material is airflow, and lots of it.  Fans clog-clean them...and if all else fails Buy a Lian-Li with lots of 120mm fans.  My LianLi mid-tower cam with 2X80mm fans and 2X120mm fans--keeps my system nice and cool even at full load.

---

### Post by jamieh on 2009-02-21
All three have Antec NeoPower 350W PSUs.

The only fans are the two in the power supply, and the one on the CPU. The case has zero fan mounts, but their are holes on the right side and back.

I'm thinking I should just trash the case and find a better one.
What do you recommend? Or are they all pretty much the same?

This is an always-on server, so cooling is a pretty high priority.

I have an Enermax PSU, I could replace it with that and see if it makes a difference.

---

### Post by wolfen69 on 2009-02-22
[http://www.xoxide.com/allcases.html](http://www.xoxide.com/allcases.html)

airflow is the most important factor. i saw a study once where they setup up a case with different fan configurations and did tempurature readings. one test was with rear exhaust and front intake. another intake only, another was exhaust only. the best configuration for cooling was rear exhaust only, as it creates negative air pressure and forces air in through every nook and cranny. 

i have an 80mm front intake and a 120mm rear exhaust. this creates a little bit of negative pressure, keeping my temps very nice. also consider a case that has a front mesh grill to allow air to be sucked in through the whole front of the computer.

---

### Post by Skripka on 2009-02-22
> **jamieh said:**
> All three have Antec NeoPower 350W PSUs.

The only fans are the two in the power supply, and the one on the CPU. The case has zero fan mounts, but their are holes on the right side and back.

I'm thinking I should just trash the case and find a better one.
What do you recommend? Or are they all pretty much the same?

This is an always-on server, so cooling is a pretty high priority.

I have an Enermax PSU, I could replace it with that and see if it makes a difference.

Are machines these based on ATX or Extended-ATX boards?

My Lian Li mid-tower has a front 120mm intake, a side 120mm exhaust, an 80mm rear intake, and an 80mm chimney fan...in addition to the exhaust duct on my GPU

---

### Post by jamieh on 2009-02-22
> **Skripka said:**
> Are machines these based on ATX or Extended-ATX boards?

24-pin.

---

### Post by Chilli Bob on 2009-02-22
On a slightly different point, does anyone know if plastic cases cause more RF interference to nearby electrical equipment (TVs etc) than metal cases, which I would imagine give more shielding.

---

### Post by Kevbert on 2009-02-22
350W power supplies are a bit low on the juice, especially for such things as the new breed of display adapters. the higher the wattage the better.
Regarding cases. The older plastic cases will have some but not necessarily as much metal shielding as modern cases. Newer cases of either type in Europe have to meet more stringent EMC tests so that they don't interfere with other electrical equipment and aren't don't have problems with other electrical equipment nearby.

---

### Post by emshains on 2009-02-22
Plastic actually doesn't give that much heat away, metal, on the other hand, is a good heat conductor, so it gains and gives heat a lot better than plastic.

---

### Post by mcduck on 2009-02-22
> **Chilli Bob said:**
> On a slightly different point, does anyone know if plastic cases cause more RF interference to nearby electrical equipment (TVs etc) than metal cases, which I would imagine give more shielding.

Yes, they do. Actually selling computers with plastic cases isn't even legal here because of lacking RF shielding. (selling plastic cases as components, however, is legal, since it can be assumed that person building a computer himself knows what he's doing).

One other thing is the fact that all computer computers should be grounded together, and this is usually done simply by connecting them to the metal case. Bit hard to do on a plastic case.. ;)

Case being plastic versus case being metal hardly has any noticeable effect in the cooling itself, since the case is not usually used as heat sink and the cooling is done by air. So cooling performance is just a question of having proper airflow and cooling components. (Of course cases made from metal tend to be more expensive, and often better designed, than plastic cases are. And that would also mean having better cooling design..) 

For the first post, all temps seem fine (actually more than fine if they are correct).

For the alarms, just set the alarm levels to reasonable numbers. For example the alarm on in1 voltage is ridiculous, the levels are set to +13,46V&#8211;+13,46V when the power line in question is a +12V line and the tolerance by ATX standard is +/-5% (so correct voltage range for it is +11,4V&#8211;+12,6V). Little bit of overvoltage doesn't hurt here so the 12,62V you have is absolutely fine. I'd be worried if it goes above 13V.

Actually none of the set alarm ranges you have make any sense.. :D

Edit:

For reference, here are the default tolerances (as defined by ATX standard):
+5VDC: +/- 5 %
-5VDC (if used): +/- 10 %
+12VDC: +/- 5 %
-12VDC (if used): +/- 10 %
+3.3VDC: +/- 5 %
+5VSB: +/- 5 %
(-5V and -12V lines are not commonly used these days.)

For temperatures and core voltages check correct values for your CPU here: [http://users.erols.com/chare/elec.htm]("http://users.erols.com/chare/elec.htm"). (It's the "Max Case temp", this doesn't mean computer case but the processor casing.

---

### Post by insane_alien on 2009-02-22
> **emshains said:**
> Plastic actually doesn't give that much heat away, metal, on the other hand, is a good heat conductor, so it gains and gives heat a lot better than plastic.

this would only matter if you were using the case as a heat sink.

if you work through the calculations for heat transfer around 1% of the heat transfer is by conduction through the case metal cases would not be much better at only 1.25%.

the convective airflow through the case carries off about 99% of the heat in either case. infact, if you insulate the case heavily(but allow an unimpeded exhaust and intake) you internal temperatures will not change by very much at all. a few degrees at best.

---

### Post by stefangr1 on 2009-02-22
I think the temperatures reported by sensors are not reliable (In your case, why are they all 26.0C...). I get:

Sys Temp:    +12°C  (high =  +103°C, hyst =   +43°C)
CPU Temp:  +32.5°C  (high = +80.0°C, hyst = +75.0°C)
AUX Temp:   +3.5°C  (high = +80.0°C, hyst = +75.0°C)

and I don't have my computer in the refigurator. :)

Maybe even more important than the IO-board / CPU temperatures are probably the temps of your harddisks. Temperatures over 50C are already harmful for a hdd, and you probably don't want to risk data loss. You can (usually, if supported by your disks) check this with 'hddtemp'.

As for plastic vs. metal: Aluminium is the best regularly applied material, as it has good heat transportation capabilities. Plastic, on the other hand does not transport heat very well so it's far less suitable.

---

### Post by mcduck on 2009-02-22
> **stefangr1 said:**
> I think the temperatures reported by sensors are not reliable (In your case, why are they all 26.0C...). I get:

Sys Temp:    +12°C  (high =  +103°C, hyst =   +43°C)
CPU Temp:  +32.5°C  (high = +80.0°C, hyst = +75.0°C)
AUX Temp:   +3.5°C  (high = +80.0°C, hyst = +75.0°C)

and I don't have my computer in the refigurator. :)

Maybe even more important than the IO-board / CPU temperatures are probably the temps of your harddisks. Temperatures over 50C are already harmful for a hdd, and you probably don't want to risk data loss. You can (usually, if supported by your disks) check this with 'hddtemp'.

As for plastic vs. metal: Aluminium is the best regularly applied material, as it has good heat transportation capabilities. Plastic, on the other hand does not transport heat very well so it's far less suitable.

It *can* give correct readings, but it doesn't automatically know all motherboards and calculate correct readings for the data sent from the sensor chip. Usually you have to do the configurations yourself (comparing the values reported by BIOS or ACPI with the values lm-sensors gives) before the temperature values are correct.

I'd say that more often than not values reported by lm-sensors are wrong unless it's been configured by hand to use correct formulas to calculate the temepratures. Quite often it actually even uses wrong sensors for wrong data readings by default..

---

### Post by jamieh on 2009-02-22
> **stefangr1 said:**
> You can (usually, if supported by your disks) check this with 'hddtemp'.

I got 32 °C.
I guess the temps are fine, but I should probably find a better power supply.

---

### Post by zakany on 2009-02-22
Remember to balance the air flow in and out. Those 12VDC fans won't maintain much of a delta-P so you need to suck as much as you blow...er, or something like that.

---

### Post by Skripka on 2009-02-22
> **jamieh said:**
> 24-pin.

My question was more along the lines of form factor, and how large the main boards are--and if you need a fulltower, or if an ATX mid-tower would do...the difference being a $100-$200 or so for a nice case.

---

### Post by insane_alien on 2009-02-22
> **zakany said:**
> Remember to balance the air flow in and out. Those 12VDC fans won't maintain much of a delta-P so you need to suck as much as you blow...er, or something like that.

You don't really need to worry here, it'll all balance out as the lower the pressure in the case the more that will be sucked in and vice versa.

otherwise you'd end up with either a perfect plenum or a perfect vacuum in the case and as neither of those actually exist outside of theoretical ideals, i think we're pretty safe.

---

### Post by mcduck on 2009-02-22
> **zakany said:**
> Remember to balance the air flow in and out. Those 12VDC fans won't maintain much of a delta-P so you need to suck as much as you blow...er, or something like that.

Actually 1 fan sucking air out of the case creates exactly the same airflow as 1 fan sucking air out + 1 fan blowing air in. You just get more noise with two fans than you get with one.

Also, since axial fans are really bad at producing pressure differences and only work for creating air flow, it's usually better to just suck air out of the case. You won't be able to create any meaningful overpressure in the case anyway, and fans at the back of the case create less audible noise. Fans at the front are only useful if the case design doesn't create enough airflow around hard disks located in front of the case.

---

### Post by mcduck on 2009-02-22
> **jamieh said:**
> I got 32 °C.
I guess the temps are fine, but I should probably find a better power supply.

Really, the voltages are quite fine. You just have badly configured MIN and MAX values for voltages in lm-sensors. Just take a look at the VSB, for example. It has MIN configured to +4,08V and MAX configured to +2,02V. youa re pretty much bound to get errors with that kind of limits.. :D

(The correct values would be MIN +3,14V and MAX +3,47V, your current VSB of +3,17V is safely inside this range.)

---

### Post by Skripka on 2009-02-22
> **mcduck said:**
> Actually 1 fan sucking air out of the case creates exactly the same airflow as 1 fan sucking air out + 1 fan blowing air in. You just get more noise with two fans than you get with one.



But where is that airflow going to and coming from?  

A front intake fan helps cool HDDs with fresh colder air, a side exhaust helps pull air over and between PCi cards, a rear intake or exhaust helps move air over the CPU HSF...etc

---

### Post by WatchingThePain on 2009-02-22
Hi,

If you touch an aluminium case it will feel cooler as it conducts heat away like a heatsink, so they are a bit better than plastic. When you buy a case some are specially engineered for airflow to be maximum which is the key point. Also look at options like extra fans, and check the speeds. I have seen some really bad cases which offer very little ventilation.

Some hardware, TV cards for example seem to generate a lot of heat. Blow all the dust out with an air duster, copper fan or better on the cpu (Like zalman or ninja).

Crazy interlude: My pal once drilled holes in a freezer , wrapped his pc in plastic and put the base unit in the freezer. He achieved a pretty good overclock speed!.

---

### Post by mcduck on 2009-02-22
> **Skripka said:**
> But where is that airflow going to and coming from?  

A front intake fan helps cool HDDs with fresh colder air, a side exhaust helps pull air over and between PCi cards, a rear intake or exhaust helps move air over the CPU HSF...etc

When you suck air out of the case new air will flow inside from any available holes you have in your case. You don't need to do anything about it.

And like I said, extra fans blowing air into the case are only useful in situations when the case design doesn't create enough airflow in a certain spot. In a well-designed case all airholes are located so that highest airflow will automatically occur in the places where it's needed.

For example, if you have a very basic case, with one exhaust fan near the top behind the case, and a ventilation hole low in the case front, air will automatically flow in from the front hole, around your hard disks located right behind the intake, then to your graphics card and over the north- & south bridges, next to CPU cooler and finally out of the case. This happens simply because A) as long as you have holes in the case new air will flow in to replace the air the exhaust fan removes from the case and B) air moves using as direct route as possible.

Adding extra holes to case sides, or having messy cables, too crowded hard disk racks or other badly designed features will of course mess with this basic design. in that case you may need to use extra fans to make sure that some components have enough moving air around them.

---

### Post by Skripka on 2009-02-22
> **mcduck said:**
> When you suck air out of the case new air will flow inside from any available holes you have in your case. You don't need to do anything about it.

And like I said, extra fans blowing air into the case are only useful in situations when the case design doesn't create enough airflow in a certain spot. In a well-designed case all airholes are located so that highest airflow will automatically occur in the places where it's needed.

For example, if you have a very basic case, with one exhaust fan near the top behind the case, and a ventilation hole low in the case front, air will automatically flow in from the front hole, around your hard disks located right behind the intake, then to your graphics card and over the north- & south bridges, next to CPU cooler and finally out of the case. This happens simply because A) as long as you have holes in the case new air will flow in to replace the air the exhaust fan removes from the case and B) air moves using as direct route as possible.

Adding extra holes to case sides, or having messy cables, too crowded hard disk racks or other badly designed features will of course mess with this basic design. in that case you may need to use extra fans to make sure that some components have enough moving air around them.

The 2 catches being:

-That with todays massive GPU bricks (which stretch from the I/O panel to the HDD cages)-free airflow through the case from bottom-front to top-back, over bridges, and PCi  is severely hampered.

-By the time air gets over the HDDs and bridges in front, it has already picked up a great deal of heat and therefore lost a great deal of cooling capacity-before it ever reaches CPU, GPU, or memory.  It is hard to cool a CPU down when the air over the CPU is close to the temp of the CPU already.

---

### Post by mcduck on 2009-02-22
> **Skripka said:**
> The 2 catches being:

-That with todays massive GPU bricks (which stretch from the I/O panel to the HDD cages)-free airflow through the case from bottom-front to top-back, over bridges, and PCi  is severely hampered.

-By the time air gets over the HDDs and bridges in front, it has already picked up a great deal of heat and therefore lost a great deal of cooling capacity-before it ever reaches CPU, GPU, or memory.  It is hard to cool a CPU down when the air over the CPU is close to the temp of the CPU already.

I agree with the second part, high-end graphics cards tend to create problems with the simplest possible cooling solutions unless the case is large enough. With more basic graphics cards this isn't a problem.

But the first part isn't really true, hard disks and motherboard components don't really generate that much heat. And definitely not enough to heat the air anywhere near CPU temperatures. :)

---

### Post by Skripka on 2009-02-22
> **mcduck said:**
> I agree with the second part, high-end graphics cards tend to create problems with the simplest possible cooling solutions unless the case is large enough. With more basic graphics cards this isn't a problem.

But the first part isn't really true, hard disks and motherboard components don't really generate that much heat. And definitely not enough to heat the air anywhere near CPU temperatures. :)

Well,it is difficult to trust lm-sensors, but my HDDs are usually 30-32C, my south bridge around 46C, my Nvidia can go north of 80C under load-presumning a 22C ambient temp outside the box.... and my AMD6400 has a critical temp of just 65C-so every little bit helps...without either a good case like my LianLi and a Zalman after-market cooler I'd be up a creek and overheating at idle.

---

