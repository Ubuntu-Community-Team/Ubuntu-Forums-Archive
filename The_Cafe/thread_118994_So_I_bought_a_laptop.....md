---
title: "So I bought a laptop...."
date: 2006-01-18
forum: The Cafe
---

### Post by DaMasta on 2006-01-18
off ebay. It's a parts laptop but I plan on breathing new life into this puppy. It's a Armada M700, P3 500mhz. No hd, hd case, optical drive, batter, power cord, or modem/nic. 64mb built in ram. Got it for $70 after shipping. Screen, keyboard and mobo are good. Well, I'm assuming the mobo is good, it gets to the bios at least. Now, the drives and battery should be a piece of cake. Adding memory should be one as well. I'm only concerned with adding the modem/nic. Anyone ever done this? Is there a door to access it a la the memory and hd? Or do I have to crack open the case?

---

### Post by Derek Djons on 2006-01-18
Some manufacturers have multiple version based on a series. The Ethernet NIC is then often placed on the motherboard (so it's build in). I doubt you will be able to install some kind of NIC module onto the motherboard.

The best thing for you would be buying a PCMCIA Ethernet Card. 

One question though... Why are you planning to spend so much money on such an old machine. I mean buying all the spare parts one at a time will cost you as much as buying an old complete notebook with maybe the same specs or slighty less. But it will be a complete one.

---

### Post by BSDFreak on 2006-01-18
[quote=DaMasta]off ebay. It's a parts laptop but I plan on breathing new life into this puppy. It's a Armada M700, P3 500mhz. No hd, hd case, optical drive, batter, power cord, or modem/nic. 64mb built in ram. Got it for $70 after shipping. Screen, keyboard and mobo are good. Well, I'm assuming the mobo is good, it gets to the bios at least. Now, the drives and battery should be a piece of cake. Adding memory should be one as well. I'm only concerned with adding the modem/nic. Anyone ever done this? Is there a door to access it a la the memory and hd? Or do I have to crack open the case?[/quote]

Found these specs for it 

> 
[LIST]
[*] Processor: [Intel Pentium]("http://www.digit-life.com/articles/compaqarmadam700/#") III 500 MHz
[*] Memory: 128 MBytes (expandable to 576 MBytes (in fact to 256                   MBytes).
[*] Hard disc: [Toshiba]("http://www.digit-life.com/articles/compaqarmadam700/#") MK1214GAP 11.2 GBytes
[*] CD-Rom drive: 24x (removable)
[*] FDD can be used as built-in or as external via an LPT port                   (the cable ships with the notebook)
[*] Matrix: 14.1" TFT LCD SVGA
[*] Video: ATI Rage Mobility P AGP 8Má SDRAM (resolution on a built-in                   monitor up to 1024X768 at 32bit, on an external monitor up to                   1024X768 at 64K colors)
[*] Sound: ESS Maestro, 2 built-in speakers, microphone
[*] Modem: integrated V.90 standard 56K fax/modem (ITU V.90, 56K                   [data]("http://www.digit-life.com/articles/compaqarmadam700/#"), 14.4K fax)
[*] Network: 10/100 Intel Pro/100+ MiniPCI, Full Duplex supported
[*] Integrated ports: 2 PCMCIA II slots, IrDA, PS/2 keyboard/mouse,                   COM, LPT, VGA, [USB]("http://www.digit-life.com/articles/compaqarmadam700/#"), TV-out
[*] Keyboard: 102 keys
[*] EasyPoint IV(TM) 3D Pointing Stick
[*] Dimensions: 31.5X24.9X2.8 cm
[*] Weight: 2.2 kg
[/LIST]

If there isn't any ports on your version then I'd get an USB nic that's supported, PCMCIA nic's are well supported for the most part but they tend to be a bit more pricey.

---

### Post by DaMasta on 2006-01-18
[QUOTE=Derek Djons]One question though... Why are you planning to spend so much money on such an old machine. [/QUOTE]
I should get this put together completely for less than $300. That includes a 40g hd, maxing the ram at 576, and the other things that I mentioned. I thought that was pretty good. Plus, as a poor college student with alot of debt, piecing it together is the only option I have.

---

### Post by DaMasta on 2006-01-18
[QUOTE=BSDFreak]Found these specs for it 
If there isn't any ports on your version then I'd get an USB nic that's supported, PCMCIA nic's are well supported for the most part but they tend to be a bit more pricey.[/QUOTE]
Well, I found [this]("http://cgi.ebay.com/COMPAQ-ARMADA-M700-modem-56k-ethernet-lan-card-combo_W0QQitemZ8752461096QQcategoryZ31534QQrdZ1QQcmdZViewItem") on ebay. So I'm guessing I can install it, correct?:confused:

---

### Post by BSDFreak on 2006-01-18
[quote=DaMasta]Well, I found [this]("http://cgi.ebay.com/COMPAQ-ARMADA-M700-modem-56k-ethernet-lan-card-combo_W0QQitemZ8752461096QQcategoryZ31534QQrdZ1QQcmdZViewItem") on ebay. So I'm guessing I can install it, correct?:confused:[/quote]

Yup, that should work just fine. :)

I'd probably put FreeBSD on it because of the speed but 500mhz and 500+mb mem is good enough to run most things. Wasn't too long ago i was using a 500mhz original athlon with 256mb to run Slackware, XP and FreeBSD.

---

### Post by mips on 2006-01-18
[QUOTE=DaMasta]I should get this put together completely for less than $300. That includes a 40g hd, maxing the ram at 576, and the other things that I mentioned. I thought that was pretty good. Plus, as a poor college student with alot of debt, piecing it together is the only option I have.[/QUOTE]

For $300 you can get a pretty decent PIII spec Thinkpad on ebay, in working condition.

Why was the the laptop broken up for parts ? You might find you go through the hassle of collecting all the parts, spending $300 only to find out the MB is cooked, hence the parts breakup.

Sorry, dont mean to rain on your parade, just want to make you aware of possible problems...

---

### Post by mips on 2006-01-18
These should be good reference points:
[http://h20000.www2.hp.com/bc/docs/support/UCR/SupportManual/TPM_125403-007/TPM_125403-007.pdf](http://h20000.www2.hp.com/bc/docs/support/UCR/SupportManual/TPM_125403-007/TPM_125403-007.pdf)
[http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=96235&submit.y=7&submit.x=7&lang=en&cc=us](http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=96235&submit.y=7&submit.x=7&lang=en&cc=us)
[http://h20000.www2.hp.com/bizsupport/TechSupport/DocumentIndex.jsp?contentType=SupportManual&lang=en&cc=us&docIndexId=179111&taskId=101&prodTypeId=321957&prodSeriesId=96235](http://h20000.www2.hp.com/bizsupport/TechSupport/DocumentIndex.jsp?contentType=SupportManual&lang=en&cc=us&docIndexId=179111&taskId=101&prodTypeId=321957&prodSeriesId=96235)
[http://h20141.www2.hp.com/hpparts/partsdirectory/](http://h20141.www2.hp.com/hpparts/partsdirectory/)

Will help with identifying part numbers and installation procedures etc.

---

### Post by cityismine on 2006-01-20
I agree, for $300 bucks you can get a completely working, decent laptop on ebay. Then you don't have to go through the trouble of collecting and assembling components. Plus components in laptops are smaller, so they cost slightly more than conventional pc components.

---

### Post by DaMasta on 2006-01-20
Allow me to reiterate:
[QUOTE=DaMasta]Plus, as a poor college student with alot of debt, piecing it together is the only option I have.[/QUOTE]

---

