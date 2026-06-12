---
title: "Extremely low temperatures recorded on intel core 2"
date: 2008-04-04
forum: The Cafe
---

### Post by th3james on 2008-04-04
Hi guys

Just built myself a new computer, intel core 2 e8200, 2GB ddr3 1333MHz Ram, on an asus p5kc mobo. The machine is nice, runs really quick, but i'm still thinking bout over clocking it, so used lm-sensors to view the temperatures, and here are the temperature results:

Sys Temp:    +24.0°C  (high = +91.0°C, hyst = +12.0°C)  sensor = thermistor
CPU Temp:     +4.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode

Somehow i refused to believe that my CPU is +4.0°C with stock cooling and two case fans, so i looked in the bios, to find that it too is reporting the same thing, as is the asus utility in windows. The highest i've seen it go to is 10°C
Any ideas what could be wrong? Motherboad fault, CPU fault?
Maybe i just lucked out on a super cool CPU :lolflag:

---

### Post by Lord Illidan on 2008-04-04
Seems like a sensor fault to me.

---

### Post by LaRoza on 2008-04-04
Get yourself an IR thermometer and find out.

Here is the one I have:

[http://www.radioshack.com/product/index.jsp?productId=2103171&cp=&sr=1&origkw=thermometer&kw=thermometer&parentPage=search](http://www.radioshack.com/product/index.jsp?productId=2103171&cp=&sr=1&origkw=thermometer&kw=thermometer&parentPage=search)

---

### Post by stoodleysnow on 2008-04-04
The hyst= number for the CPU sensor looks too high to me.

---

### Post by az on 2008-04-04
> **th3james said:**
> Hi guys

Just built myself a new computer, intel core 2 e8200, 2GB ddr3 1333MHz Ram, on an asus p5kc mobo. The machine is nice, runs really quick, but i'm still thinking bout over clocking it, so used lm-sensors to view the temperatures, and here are the temperature results:

Sys Temp:    +24.0°C  (high = +91.0°C, hyst = +12.0°C)  sensor = thermistor
CPU Temp:     +4.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode

Somehow i refused to believe that my CPU is +4.0°C with stock cooling and two case fans, so i looked in the bios, to find that it too is reporting the same thing, as is the asus utility in windows. The highest i've seen it go to is 10°C
Any ideas what could be wrong? Motherboad fault, CPU fault?
Maybe i just lucked out on a super cool CPU :lolflag:

I have found that lm-sensors can need to be calibrated, or offset.  Usually, there is an offset for certain components and that is known by manufacturers, but unknown by the developers of lm-sensors until someone files a bug report.

I reckon your reading is precise, but not accurate.  It's precise in the sense that it will properly measure changes in temperature with high sensitivity and reliability, but it will be off by a constant value, hence not accurate.  Once you correct for that, you are good to go.

---

### Post by th3james on 2008-04-04
Yeah, looks like its accurate relative to its low start point, i reckon i'll measure the temp with the IR thing and adjust.
Although, would this not mean that the motherboard does not know the temp, and therefore will incorrectly adjust the fans, meaning potential overheating?

---

### Post by mcduck on 2008-04-04
> **th3james said:**
> Yeah, looks like its accurate relative to its low start point, i reckon i'll measure the temp with the IR thing and adjust.
Although, would this not mean that the motherboard does not know the temp, and therefore will incorrectly adjust the fans, meaning potential overheating?

Your motherboard should already know what it's own sensors do, and this is completely separate from what different sensor reading programs might tell you, or what operating system you run. 

The only issue you are having is that lm-sensors doesn't have pre-configured settings for your motherboards sensor chip, and because of that it doesn't interpret the values correctly. That's actually quite common, and the configuration file for lm-sensors allows creating different functions to interpret the sensor values. The problem is that you'll of course have to get the right values from somewhere so that you know the correct offset/multiplier needed to calculate correct values. You could try comparing values reported by lm-sensors to those you see in BIOS (if your BIOS has sensor readings).

---

### Post by th3james on 2008-04-05
BIOS is reporting the same values as every bit of software I've tried, so i figure its not a software problem, its faulty hardware (or at least incorrectly configured hardware)

---

