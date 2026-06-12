---
title: "ups advice? i need some :)"
date: 2007-03-26
forum: The Cafe
---

### Post by pixeldotz on 2007-03-26
so i'm thinking about getting a UPS so i don't have to worry about the wiring in my house killing my equipment, so i thought i'd ask if anyone had any advice on getting one based on what i want to connect to it.

pc with 3 hdds and a burner and one external usb (external usb runs on power plug so it would need to be hooked into the UPS)

17" flatpanel.

xbox360
xbox


does anyone know what voltage/amp i would need or somewhere i could get a calculation for the size i would need?


thanks for any help :)

---

### Post by mips on 2007-03-27
I would suggest you start by recording the power consumption of all the devices you want to connect to the ups and post them here. Wattage would be good.

Then tell us how long you require the ups to carry the load and I will make a recommendation based on the info you provided.

---

### Post by pixeldotz on 2007-03-27
to tell you the truth a few minutes (5 at the most really) is all i need for my pc to stay up.

the other devices will be connected to the ups as a means to avoid a short or damaged electronics if i'm playing my xbox/360 and my power blinks out.



**psu**
AC Input:	110-240V
Max Power Rating:	380 W

**monitor.**
On Mode  	   	42 watt (max)
DPMS Mode 	  	< 2 watts
Power Type 	  	Built-in

**cable modem**
9 watts
input power north america
105 - 120 VAC 60hz

xbox 360
draws 160 watts of power
xbox
draws about 74 with a 130 watt power supply

now that i think of it, i don't think i really need to have my xbox360 plugged into the ups, i'll just get a surge protector or something for it. :)

---

### Post by slimdog360 on 2007-03-27
well then about a kilowatt.
edit: Im guessing you would be safe with around a 750W UPS

---

### Post by mips on 2007-03-27
[http://www.apc.com/tools/ups_selector/index.cfm](http://www.apc.com/tools/ups_selector/index.cfm)

With no extra capacity a 1500va ups will give you 10mins runtime


I used to have a 1400va that powered 2xPCs and 2x21¨ monitors and that gave me about 20mins time.

---

### Post by pixeldotz on 2007-03-27
would this work?

[http://www.bestbuy.com/site/olspage.jsp?skuId=8022935&st=UPS&type=product&id=1157067061643](http://www.bestbuy.com/site/olspage.jsp?skuId=8022935&st=UPS&type=product&id=1157067061643)

or this?

[http://www.compusa.com/products/product_info.asp?pfp=BROWSE&N=200082+404087+11&Ne=500000&product_code=51875748&Pn=Enhanced_Series_ES1500C_UPS](http://www.compusa.com/products/product_info.asp?pfp=BROWSE&N=200082+404087+11&Ne=500000&product_code=51875748&Pn=Enhanced_Series_ES1500C_UPS)

---

### Post by mips on 2007-03-27
Yes they should work.

BUT, keep in mind that not all ups´ are equal. the cheaper models do not have all the fancy electronics that give you clean power. But at the end of the day you would be better off than without a ups.

APC brand is a good one. have years of experience with them.

---

### Post by pixeldotz on 2007-03-27
i think ill be getting the APC one from bestbuy.

just had one questions,

why does the Opti from compusa say

1400VA, 980watts

and the APC say

1500VA (865W)

wouldn't the higher VA mean higher wattage or am i totally off on this one?

---

### Post by pixeldotz on 2007-03-27
thanks you guys. i appreciate the help i'll feel so much better once i get this UPS. just for kicks here's a complete breakdown of all the wattage ill be drawing.

pc. 380
mon. 44 (compensate for the 2 extra watts)
modem. 9
router. 3.4
____________
          436.4

xbox. 130
xbo360. 160
____________
             190

total.
726.4 (865W APC brand should be perfect)

that's 6 devices total. i can plug my tv and my receiver into the surge-only protected devices.

thanks again. now to search for some linux APC/UPS software for ubuntu.

---

### Post by gurgle on 2007-03-27
^^ for software, check out linuxeq.com 

they have some UPS software on tehre.

---

### Post by mips on 2007-03-27
> **pixeldotz said:**
> 
wouldn't the higher VA mean higher wattage or am i totally off on this one?

Yes, you are correct. i have no idea how they got to those values

---

### Post by mips on 2007-03-27
> **pixeldotz said:**
> 
thanks again. now to search for some linux APC/UPS software for ubuntu.

[http://www.apcupsd.org/](http://www.apcupsd.org/)
[http://www.mscs.dal.ca/~selinger/ups/backups.html](http://www.mscs.dal.ca/~selinger/ups/backups.html)

Or just google Linux APC

---

### Post by Bigbluecat on 2007-03-27
I use APCUPSD with my APC UPS. Works very well. There is a How To on these forums for installation instructions.

---

### Post by pixeldotz on 2007-03-27
very helpful on people in the general section :)

i think i'm re-evaluating my situation and might be getting the OPTI. the 1050 joule rating sits better with my for lightning protection whereas the apc one only has 564.

the opti might not have all the bells and whistles like an LCD display but it does seem to offer more than the APC.

---

### Post by pixeldotz on 2007-03-29
thanks for all the help guys. i bought APC brand one after and it's handling everything very nicely.

pc/cable.modem/router/lcd.monitor/usb.external.hdd

and the UPS is registering that it idles at about 70watts. when booting up it jumps to about 90watts.

this was a great buy, thanks you guys.

---

### Post by mips on 2007-03-29
Glad to hear you are happy with your purchase :)

---

### Post by pixeldotz on 2007-03-29
yeah, i just wish that new plastic smell would hurry and clear my room already. you know, not a burning smell but a new plastic smell. :lolflag:

---

### Post by tgalati4 on 2007-04-08
Don't go crazy testing runtimes on consumer-grade UPS units.  That plastic smell is probably the heatsinks getting toasty.  To save costs, cheaper units have minimal heat sinks and will heat up and even melt the case during a long battery run (30 minutes).  I prefer used, tossed out business-grade units with all-metal cases.  Then just replace the batteries and you are good to go.

I have done comparisons between the two types and I have melted a few--including shooting flames out of the MOSFETs (otherwise known as flame-emmiting transistors).

Good luck.

---

