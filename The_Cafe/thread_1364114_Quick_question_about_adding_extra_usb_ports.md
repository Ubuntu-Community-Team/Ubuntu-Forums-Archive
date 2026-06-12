---
title: "Quick question about adding extra usb ports"
date: 2009-12-25
forum: The Cafe
---

### Post by blueshiftoverwatch on 2009-12-25
I was adding extra USB ports to my computer.

The motherboard has 2 slots that are specifically labeled on the motherboard for use with USB, and they're both in use.

But theirs another slot that is exactly the same as a USB port slot, the extra USB port adapters fit in. Only it's labeled "front panel connectors". The motherboard on the schematic isn't exactly the same as the one I have.

Based on my knowledge of computers, if something isn't supposed to go in a certain slot it's designed so that it doesn't fit. So therefore, if something fits in a certain slot 99% of the time it's okay to put it in there, right?

---

### Post by SuperSonic4 on 2009-12-25
If it;s the same colour as your usb slots go for it (usb is blue on my mobo) but firewire also uses the same style of connector but is a different colour for me

wouldn't it be easier to get a USB pci card?

---

### Post by alphaniner on 2009-12-25
You have PCI slots that are labeled for USB???  What is the make/model of your mobo?

---

### Post by SuperSonic4 on 2009-12-25
Don't think so, that was just a suggestion on my part.

I'm guessing the OP means the 10 plug connector which, IIRC, has pin 1 mising

---

### Post by blueshiftoverwatch on 2009-12-25
> **SuperSonic4 said:**
> If it;s the same colour as your usb slots go for it (usb is blue on my mobo) but firewire also uses the same style of connector but is a different colour for me
It's the same color. But it's a different style. The connectors labeled USB have this black wall thing around them, this is just naked pins sitting up. What my concern is, will something get fried if it turns out it's not supposed to go there. Or will it just not work?
> **SuperSonic4 said:**
> wouldn't it be easier to get a USB pci card?
Probably, but the one I have came with the motherboard. So I'm just going with that. Otherwise I don't really need the extra USB ports enough to warrant buying one. I'd just unplug something noncritical (like my USB cell phone charger) when it's not in use.
> **SuperSonic4 said:**
> I'm guessing the OP means the 10 plug connector which, IIRC, has pin 1 mising
Yeah, it has 4 pins and than 3 pins below it (or ontop of it, depending on how your looking at it). With one missing on the end.

---

### Post by SuperSonic4 on 2009-12-25
Chances are if you're wrong it won't work with no other effect.

Do you know the make and model of your keyboard? My USB from the front panel is 10-pin but you've described an 8 pin

---

### Post by Skripka on 2009-12-25
> **blueshiftoverwatch said:**
> It's the same color. But it's a different style. The connectors labeled USB have this black wall thing around them, this is just naked pins sitting up. What my concern is, will something get fried if it turns out it's not supposed to go there. Or will it just not work?



Check your documentation.  It sounds like you're wanting to put USB into the front panel I/O header.  Some mainboards/boxes are designed to have USB connectors on the front panel.

---

### Post by Skripka on 2009-12-25
> **SuperSonic4 said:**
> Chances are if you're wrong it won't work with no other effect.

Do you know the make and model of your keyboard? My USB from the front panel is 10-pin but you've described an 8 pin

If he plugs a USB connector into the front panel I/O header-the machine shouldn't even boot.

---

### Post by blueshiftoverwatch on 2009-12-25
> **SuperSonic4 said:**
> Do you know the make and model of your keyboard? My USB from the front panel is 10-pin but you've described an 8 pin
I think you mean motherboard, and it's an MSI 790FX-GD70.

---

### Post by blueshiftoverwatch on 2009-12-25
Both the slots labeled for USB and for the front panel connector have 9 pins. I miscounted.

5 on top and 4 on the bottom.

---

### Post by alphaniner on 2009-12-25
Ok, I get it now.  You're talking about headers.  What is the label of the connector you are thinking about using?  IE JUSB, JCOM, etc.

---

### Post by SuperSonic4 on 2009-12-25
JAUD is for audio so a USB port won't work

J1934 is a 1394 connector - used for firewire

JFP1 is for LEDs and switches

So I do not think it would work

---

### Post by blueshiftoverwatch on 2009-12-25
> **SuperSonic4 said:**
> JFP1 is for LEDs and switches

So I do not think it would work
JFP1 and 2. So your probably right.

---

### Post by alphaniner on 2009-12-25
Same here.  I dl'ed the manual for the board and there are only two USB headers.  The only thing that looks remotely similar is the 1394 header, and if a USB panel was connected there and a USB device plugged in, it would fry something.  At least according to every warning on every mobo I've ever had.


Edit:
[QUOTE="The Manual"]**Front Panel Connectors: JFP1, JFP2**
These connectors are for electrical connection to the front panel switches and LEDs.
The JFP1 is compliant with Intel® Front Panel I/O Connectivity Design Guide.[/QUOTE]

---

### Post by cascade9 on 2009-12-25
> **blueshiftoverwatch said:**
> But theirs another slot that is exactly the same as a USB port slot, the extra USB port adapters fit in. Only it's labeled "front panel connectors". The motherboard on the schematic isn't exactly the same as the one I have.
 
 Based on my knowledge of computers, if something isn't supposed to go in a certain slot it's designed so that it doesn't fit. So therefore, if something fits in a certain slot 99% of the time it's okay to put it in there, right?

Just cause it 'fits' doesnt mean it works. Seen a few thinsg that have pinouts that fit, but that doesnt make them work at all. 

> **blueshiftoverwatch said:**
> Yeah, it has 4 pins and than 3 pins below it (or ontop of it, depending on how your looking at it). With one missing on the end.

Funny idea of 'fits' USB is a 5x2 pinout (with 1 blocked) and thats 4x2 pinout (with one blocked) 
 
 > **Skripka said:**
> Check your documentation. It sounds like you're wanting to put USB into the front panel I/O header. Some mainboards/boxes are designed to have USB connectors on the front panel.
  
Yep, its the speaker/alternate power LED/suspend LED/buzzer connector. I cant recall whos cases that was made to work on, but I've seen it before. 

> **Skripka said:**
> If he plugs a USB connector into the front panel I/O header-the machine shouldn't even boot.

I've seen crazier combos work in the past and still boot, but theres a very good chance your right. 

@ blueshiftoverwatch- Its not going to work. As to if it would fry something, hey, who knows? But its really not worth the risk. 

Even if the manual that came with the motherboard has a different layout, JFP1 and JFP2 will do exactly the same thing on your revision. BTW, is it a diferent layout to the one of the MSI page? 

[http://www.msi.com/index.php?func=downloaddetail&type=manual&maincat_no=1&prod_no=1740](http://www.msi.com/index.php?func=downloaddetail&type=manual&maincat_no=1&prod_no=1740)

---

### Post by blueshiftoverwatch on 2009-12-25
I actually just opened the physical manual a few minutes before you posted. Generally I don't read official documentation because it's either lacking (to make room for multiple languages) or doesn't really explain stuff as well as people on a forum do.

Although I didn't know it would actually fry anything. You wouldn't think they'd make something in a configuration that a USB extension could be plugged into if it wasn't supposed to be plugged into it.

---

### Post by alphaniner on 2009-12-25
> **blueshiftoverwatch said:**
> You wouldn't think they'd make something in a configuration that a USB extension could be plugged into if it wasn't supposed to be plugged into it.

No offense, but that assumption (that whole post, really) is the prefect example of an epic fail waiting to happen.

---

### Post by cascade9 on 2009-12-25
> **blueshiftoverwatch said:**
> I actually just opened the physical manual a few minutes before you posted. Generally I don't read official documentation because it's either lacking (to make room for multiple languages) or doesn't really explain stuff as well as people on a forum do.

Although I didn't know it would actually fry anything. You wouldn't think they'd make something in a configuration that a USB extension could be plugged into if it wasn't supposed to be plugged into it.

It might 'fit' but it doesnt 'match' How coudl something that needs 9 pins work on a 7 pin connection? 

Chalk it up to expereince, and remember to check your manual, or at least count your pinouts next time ;)

---

### Post by blueshiftoverwatch on 2009-12-25
> **cascade9 said:**
> It might 'fit' but it doesnt 'match' How coudl something that needs 9 pins work on a 7 pin connection? 

Chalk it up to expereince, and remember to check your manual, or at least count your pinouts next time ;)
Both the front panel connectors and USB connectors have 9 pins. I just miscounted the first time.

Thanks for the responces. I'll take that extra USB port out of my computer before I put it back together, power it on, possibly fry something, and will try to be more cautious with this stuff in the future.

And with that, I guess </thread>

---

### Post by cascade9 on 2009-12-25
> **blueshiftoverwatch said:**
> Both the front panel connectors and USB connectors have 9 pins. I just miscounted the first time.

Thanks for the responces. I'll take that extra USB port out of my computer before I put it back together, power it on, possibly fry something, and will try to be more cautious with this stuff in the future.

And with that, I guess </thread>

Umm..no, you counted right the 1st time. JFP2 has 7 pins. 

Lemmie guess, you counted the 9 pins from JFP1 in the manual? Well that is the connector for your normal power switch/reset switch/hdd led. Besides that, the USB port wont plug into that (pin 9 blocked on USB, pin 10 blocked on JFP1)

---

### Post by Ginsu543 on 2009-12-25
Perhaps I'm going against the flow here, but I believe that the "front panel connectors" the OP is talking about **are** USB headers (not JFP2, etc.), designed for computer cases that have USB ports on the front panel. The motherboard in my main rig has two such headers. They have nine pins, in exactly the same configuration (5 in the first row, 4 in the second) as the other USB headers. If your computer case does not have USB ports built-in to the front panel (if you do, then there should be a cable you are supposed to connect to the "front panel connectors"), you should be able to use the same headers to make USB connectors available in the back of your computer case using the appropriate adapter.

---

### Post by alphaniner on 2009-12-25
He specifically said that the headers he was thinking about using were JFP1&2.  The mobo only has two USB headers, which he is already using.  Case closed.

---

