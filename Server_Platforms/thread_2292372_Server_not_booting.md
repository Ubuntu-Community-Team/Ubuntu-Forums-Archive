---
title: "Server not booting"
date: 2015-08-27
forum: Server Platforms
---

### Post by fallen4 on 2015-08-27
Hi guys, new here and to ubuntu so bear with me. Got a pc with ubuntu server supposedly installed, 

specs

[COLOR=#000000]Processor: [/COLOR][[COLOR=#000000]Intel Xeon E3 1230V2 3.3GHz LGA 1155 Boxed Processor[/COLOR]]("http://www.microcenter.com/product/400271/Xeon_E3_1230V2_33GHz_LGA_1155_Boxed_Processor")[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]MOBO: [/COLOR][[COLOR=#000000]SUPERMICRO MBD-X9SCM-F-O LGA 1155 Intel C204 Micro ATX Intel Xeon E3 Server Motherboard[/COLOR]]("https://www.amazon.com/gp/product/B004WKRDA4/ref=oh_aui_detailpage_o05_s00?ie=UTF8&psc=1")[COLOR=#000000]
[/COLOR]
[COLOR=#000000]RAM: [/COLOR][[COLOR=#000000]Crucial 16GB Kit (8GBx2) DDR3L 1600MT/s (PC3-12800) DR x8 ECC UDIMM 240-Pin Server Memory CT2KIT102472BD160B[/COLOR]]("https://www.amazon.com/gp/product/B008EMA5VU/ref=oh_aui_detailpage_o04_s00?ie=UTF8&psc=1")
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]HDs: (3x) [/COLOR][[COLOR=#000000]WD Red 3 TB NAS Hard Drive: 3.5 Inch, SATA III, 64 MB Cache - WD30EFRX[/COLOR]]("https://www.amazon.com/gp/product/B008JJLW4M/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1")
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]SSD: Chronos 60GB [/COLOR]


First time booting the machine and i get booting into the shell, when i exit can't boot from nas drive, which led me to check the boot options. Was left even more confued after. 

Pictures attached as referenced.

Assistance wit is will be greatly appreciated.

Thanking you in advance.

---

### Post by howefield on 2015-08-27
Thread moved to the "*Server Platforms*" forum.

---

### Post by fallen4 on 2015-08-27
If anyone can help me with this, it would truly be appreciated, at a lost atm.

---

### Post by v3.xx on 2015-08-27
I'm not so good at this, but ..

First observation is 4core & 2threads per.  Sounds like one fast processor.  I have a similar Xeon.

What I do not have is UEFI and this sounds like it may have something to do with your problem.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uefi&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uefi&sa=Search&cof=FORID:9)

Any thoughts on that?

---

### Post by SeijiSensei on 2015-08-27
The server version has no graphical interface, so if that's the issue, it is running as designed.

Also shouldn't the machine be booting from the SSD?

---

### Post by fallen4 on 2015-08-27
Hey thanks for the reply, read some of the articles there, surface to say even more confused now. Could change to legacy boot but no idea how to go from their looking at the boot options (see the pics). Setup is completely new to me so im at a lost.

---

### Post by fallen4 on 2015-08-27
> **SeijiSensei said:**
> The server version has no graphical interface, so if that's the issue, it is running as designed.

**Also shouldn't the machine be booting from the SSD**?

Exactly what im thinking, not seeing the option in the boot menu. Bought the machine as is, hence my confusion. The plan was to install another OS, so was expecting to boot into the current OS, check it out etc, and move from their, didnt expect to meet these issues, and at a lost how to move forward. 

Anyone have any ideas.

---

