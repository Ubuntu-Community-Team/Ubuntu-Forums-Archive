---
title: "BIOS Hacking"
date: 2011-01-31
forum: Security
---

### Post by Lawliet1 on 2011-01-31
I've been doing research on root-kits and found that they can infect motherboards, graphics cards, and almost anything else that plug into your motherboard. [I]John Heasman, a security expert, warns of threats that involve rootkits that survive HD reformatting by hiding in your BIOS. Has anyone ever encountered this form of compromise or is it just a cautionary tale about future rootkits?   
[/I]

---

### Post by hansdown on 2011-01-31
Hi Lawliet1.

I wouldn't worry too much. 

After the CIH (chernobyl) virus in 1998, write protected bios are now the norm.

[http://arstechnica.com/security/news/2009/03/researchers-demonstrate-bios-level-rootkit-attack.ars](http://arstechnica.com/security/news/2009/03/researchers-demonstrate-bios-level-rootkit-attack.ars)

---

### Post by Lawliet1 on 2011-01-31
@hansdowm

The main concern with rootkits in BIOS and other hardware are the flash prone firmware in those devices. Firmware allows code in ROM that isn't deleted or altered when the power is shut off. Those codes can be altered when you update/flash the firmware. That is the most noteable ways into the system. However, it is extremely complicated to do that, but it's something that should concern people/ Thank you for the link. 

 "Flashing a system&#8217;s BIOS requires administrative control, but that could first be obtained through a more &#8216;innocent&#8217; virus that could reside on the hard disk drive. Once an attacker has admin rights, the rootkit could be flashed onto the BIOS and would remain effective even if the original virus on the hard disk were removed. Even a complete format wouldn&#8217;t rid the system of the virus. 
 "You would need to reflash the Bios with a system that you know has not been tampered with," he said. "But if the rootkit is sophisticated enough it may be necessary to physically remove and replace the Bios chip." 



 There is defense against such an attack, however, as the researchers say that a password or physical lock against BIOS flashes could block the install of the rootkit. 
 "The best approach is preventing the virus from flashing onto the Bios," said Sacco. "You need to prevent flashing of the bios, even if it means pulling out jumper on motherboard."

---

