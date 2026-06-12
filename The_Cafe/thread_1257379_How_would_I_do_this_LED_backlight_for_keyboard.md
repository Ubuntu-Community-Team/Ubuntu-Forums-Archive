---
title: "How would I do this: LED backlight for keyboard"
date: 2009-09-03
forum: The Cafe
---

### Post by billdotson on 2009-09-03
I don't want a full-fledged backlit keyboard (if I did I would have paid the outrageous price for one) but I am trying to find a solution to my "can't see my keyboard in the dark so I have to play my games with bright fluorescent lights on". I was thinking of just buying an LED strip and putting it at the top of the keyboard but I am not sure.

[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&Item=170371020203&Category=58019]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&Item=170371020203&Category=58019")
There is that kind of thing on ebay but it says it is for a vehicle. I just want to find one I can plug into a wall socket (United States) or run off batteries.. Either that or a cold cathode tube, but the same thing there, I don't know where I would find one to just plug into a wall socket or run off of a battery.

Would anyone have an idea where I could find this or am I going to have to resort to buying LEDs, a switch  and some batteries and rigging this up myself with some solder and electrical tape?

Thanks

---

### Post by tgalati4 on 2009-09-03
You can probably pull 500 mA of power from a keyboard before it will stop working.  You can get decent light from a red LED at 12 mA.  That's 40 LED's.  You can probably get by with 20 LED's spaced under the keyboard wired in parallel with an appropriate resistor to knock the 5 volts down to 2.2 V.  You could also wire them in series (in pairs for 2.5 V each) then wire those pairs in parallel until you get to 20.  You may still need a resistor to drop the current to 12 mA.

Simpler is to get a small desk lamp and a 10 or 15 watt bulb.

---

### Post by joey-elijah on 2009-09-03
not sure whether you're asking re: a desktop keyboard or a laptop? 

I have a backlit DT keyboard (tho i don't play games) and it certainly wasn't that expensive. 

I paid about £20 for it (so around $30) though i doubt it's a gorgoues or trendy as some! It does have a cool button that dims the light though... 

OBVIOUSLY, doing it yourself is a) more fun and b) gonna be cheaper. You could probably get something to power off batteries easily. 

If you're really feeling humourous there's always... 
[http://lifehacker.com/394368/make-your-own-illuminated-keyboard](http://lifehacker.com/394368/make-your-own-illuminated-keyboard)

and i'm suepr tempted to hack my eee and do this: 
[http://www.popsci.com/diy/article/2008-05/eee-pc-school-add-keyboard-backlight-under-15](http://www.popsci.com/diy/article/2008-05/eee-pc-school-add-keyboard-backlight-under-15)

---

### Post by Skripka on 2009-09-03
> **joey-elijah said:**
> not sure whether you're asking re: a desktop keyboard or a laptop? 

I have a backlit DT keyboard (tho i don't play games) and it certainly wasn't that expensive. 

I paid about £20 for it (so around $30) though i doubt it's a gorgoues or trendy as some! It does have a cool button that dims the light though... 

OBVIOUSLY, doing it yourself is a) more fun and b) gonna be cheaper. You could probably get something to power off batteries easily. 

If you're really feeling humourous there's always... 
[http://lifehacker.com/394368/make-your-own-illuminated-keyboard](http://lifehacker.com/394368/make-your-own-illuminated-keyboard)

and i'm suepr tempted to hack my eee and do this: 
[http://www.popsci.com/diy/article/2008-05/eee-pc-school-add-keyboard-backlight-under-15](http://www.popsci.com/diy/article/2008-05/eee-pc-school-add-keyboard-backlight-under-15)

Heck my G15 keyboard is backlit, and has other bells and whistles...and it was not that expensive even a few years ago when new.

---

### Post by joey-elijah on 2009-09-03
> **Skripka said:**
> Heck my G15 keyboard is backlit, and has other bells and whistles...and it was not that expensive even a few years ago when new.

Thanks for breaking it to me gently :P

---

### Post by billdotson on 2009-09-03
[http://www.newegg.com/Product/Product.aspx?Item=N82E16823126034&Tpk=g15%20backlit]("http://www.newegg.com/Product/Product.aspx?Item=N82E16823126034&Tpk=g15%20backlit")

I consider $90 pretty steep. I have a $20 Microsoft Comfort Curve Keyboard that works just fine, I just need a way to put LED lighting around it so I can use it in the dark. I can't stand having my fluorescent lights on at 3 in the morning, especially when I am playing a game. I don't really feel like opening up the keyboard and messing with it unless I knew exactly what I was doing. I was thinking just having  a few LEDs mounted on the underside of the desk would be enough light.

However, it would be nice to have an illuminated keyboard setup. I am wondering if the scroll lock part on the circuit board in my keyboard would provide enough key from the circuit board inside my keyboard would provide enough voltage to power the lighting as well as the keyboard without any issues.


This guy here used electroluminescent wire to make a backlit keyboard. He isn't using the keyboard's power but is connecting the EL wires to a molex connector inside his PC case. Also, maybe you can tell, but the light is actually coming out from holes he drilled in between the keys. My keyboard doesn't have spaces in between the keys like that, but I don't understand why EL wire wouldn't just glow around the keys anyway.

I'd have to figure out the power calculations for the the EL wire running off of USB and see if that could work. I don't have a crappy USB keyboard to test and I don't think I could try it out with PS/2 (is PS/2 data only or something like that?) I really want to get this project done before September 15th as there is a PC game that comes out then and I can't run it by playing with all the lights in my room on :) 
[http://www.overclock.net/computer-peripherals/10375-keyboard-mod-guide-final-version.html]("http://www.overclock.net/computer-peripherals/10375-keyboard-mod-guide-final-version.html")

---

### Post by aldld on 2009-09-04
If you have a keyboard tray under your desk, maybe you could put some LEDs on the underside of the desk, above the keyboard.

---

### Post by Exodist on 2009-09-04
> **billdotson said:**
> I don't want a full-fledged backlit keyboard (if I did I would have paid the outrageous price for one) but I am trying to find a solution to my "can't see my keyboard in the dark so I have to play my games with bright fluorescent lights on". I was thinking of just buying an LED strip and putting it at the top of the keyboard but I am not sure.

[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&Item=170371020203&Category=58019]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&Item=170371020203&Category=58019")
There is that kind of thing on ebay but it says it is for a vehicle. I just want to find one I can plug into a wall socket (United States) or run off batteries.. Either that or a cold cathode tube, but the same thing there, I don't know where I would find one to just plug into a wall socket or run off of a battery.

Would anyone have an idea where I could find this or am I going to have to resort to buying LEDs, a switch  and some batteries and rigging this up myself with some solder and electrical tape?

Thanks

The Saitek Eclispe are only about $30-$35USD.
I have had mine for about 4 years and I love it.
[http://www.saitek.com/uk/prod/eclipse.htm](http://www.saitek.com/uk/prod/eclipse.htm)

---

### Post by aldld on 2009-09-04
> **Exodist said:**
> The Saitek Eclispe are only about $30-$35USD.
I have had mine for about 4 years and I love it.
[http://www.saitek.com/uk/prod/eclipse.htm](http://www.saitek.com/uk/prod/eclipse.htm)

I'm using the Saitek Eclipse K140, which is backlit, but I would not recommend it because the keys are very sticky. I will be getting a new keyboard as soon as I can.

---

### Post by tom66 on 2009-09-04
Remember Ohms law V=I/R, so you put the voltage down to 2.2V, you can draw almost 1.13A of current. An LED hits full brightness at around 16 mA. I'd say 70-71 LEDs. 

Pull the current for the keyboard from USB, though. A failure in one of the LEDs could destroy the PS/2 port, whilst the USB ports are well protected against short-outs.

Additionally, I'd like to note that when I was customising my laptop I had the option of a backlit keyboard, for £19.99. Not a bad price, all things considered.

---

### Post by Exodist on 2009-09-04
> **aldld said:**
> I'm using the Saitek Eclipse K140, which is backlit, but I would not recommend it because the keys are very sticky. I will be getting a new keyboard as soon as I can.

I have the older KU 0418. Its the oldest and best.

Keys are not sticky, many typest seem to like them as well.
I normally dont liek posting links to commerical sales sites. But here is a newegg link to the one I have. It gets a 4/5star rating out of 1790+ reviews. Also has nicer photos of the keyboard.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16823175103](http://www.newegg.com/Product/Product.aspx?Item=N82E16823175103)

---

### Post by aldld on 2009-09-04
> **Exodist said:**
> I have the older KU 0418. Its the oldest and best.

Keys are not sticky, many typest seem to like them as well.
I normally dont liek posting links to commerical sales sites. But here is a newegg link to the one I have. It gets a 4/5star rating out of 1790+ reviews. Also has nicer photos of the keyboard.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16823175103](http://www.newegg.com/Product/Product.aspx?Item=N82E16823175103)

Thanks. I'll be sure to consider that one ;)

---

### Post by billdotson on 2009-09-05
The pieces of EL wire use an inverter box (and some need something called a.driver) so I don't know how that would work with 5v USB. I also don't know where I would find out how many volts and current would go through the scroll lock LED connector on the keyboard circuitboard. USB devices pull power as needed correct? I'll post some pictures later to better explain but basically it is going to involve: EL wire or EL sheet, drilling small holes between the keys, running the electrical calculations and hooking the EL material up to a power source (hopefully the scroll lock key). 

The EL sheet sounds like it could be promising and it would work well if you could cut out holes in it (so the keys could still press the matrix) without messing it up.

---

### Post by billdotson on 2009-09-06
The best option it seems is to buy what is called a custom EL sheet. [http://electroluminescence-inc.com/customPattern.htm]("http://electroluminescence-inc.com/customPattern.htm") I could pop out all the keys, cut holes in the sheet so each key could still press the matrix and then hook it up to a power source. That would make it so I didn't have to drill light holes in the keyboard. I would just have to be certain that the film wouldn't be too thick as to not let the keys go down far enough to hit the matrix.

Now for the power. All the inverters I have seen up to this point take a 12v DC source and convert it into AC for use by the EL material. Using a 5v source when 12v is needed would either make it not work at all or not be as bright. However, I just found this: [http://www.supertex.com/feature_hv853.html]("http://www.supertex.com/feature_hv853.html") By looking at the datasheet and product summary it seems as if that may be a good option. However, I do not know how to read the schematics in the datasheet. I know the squiggly is a resistor but the other stuff like Vdd I have no clue.

Depending on how big that thing is and how many volts and amps come out of the connector on the keyboard circuit board for the scroll lock LED I might be able to house that inverter inside the keyboard and wire it directly into where the scroll lock LED was located.

And actually I just found this too: [http://www.nerdkits.com/videos/backlight/](http://www.nerdkits.com/videos/backlight/)

Sounds interesting. I don't know how I would fit that circuit inside the keyboard though, it looks moderately big. This will be the first electronic project I have done since soldering LEDs together to make a wiimote sensor. This actually sounds like I will have to learn some new stuff to do this :) . I don't know if I will be able to have this set up in time for me to play Batman Arkham Asylum though... I may just have to make a short term solution and wire up some LEDs under my desk.

---

### Post by Exodist on 2009-09-07
This website is fairly good. I bought my black lights from them. They also got some keyboards a little cheaper and more PC mod stuff you may want.

[http://www.xoxide.com/keyboards.html](http://www.xoxide.com/keyboards.html)

---

