---
title: "Setting Up Printer"
date: 2013-03-19
forum: System76 Support
---

### Post by Cliff Bentley on 2013-03-19
In my newbiness, I went on-line looking for answers on how to connect our printer. So much on-line info, I don't know where to start. So I come here with some questions to get started.

I tried to go to "[COLOR=#0000cd]Printers - localhost[/COLOR]" >> "[COLOR=#0000cd]Add[/COLOR]" >> "[COLOR=#0000cd]Network Printer[/COLOR]" >> "[COLOR=#0000cd]Find Network Printer[/COLOR]" >> "[COLOR=#0000cd]Host[/COLOR]" field >> entered "[COLOR=#0000cd]*canon*[/COLOR]" >> then the "[COLOR=#0000cd]Find[/COLOR]" button. Not surprisingly, this printer dialog was expecting a URI or an IP address in the Host field. This is a home network, and this Ratel found the router by itself when I first turned it on in January. So I'm not necessarily familar with the various IP addresses on our little net. (I guess it's time.) The printer is on and works for the Windows PCs in this home. Here are some questions to get me started:
1) Do I need to install [COLOR=#0000cd]nmap[/COLOR] or something to find my printer's URI/IP so that I can use "[COLOR=#0000cd]Printers - localhost[/COLOR]"? Or, do I already have a command in bash or some other Ubuntu tool?
2) The printer is a [COLOR=#800000]Canon MX700[/COLOR]. Will I need to download/install drivers first? Suggestions as to which?

Let's start there. Once I get past this stage I'll probably get stuck and come back with more questions. Thanks in advance for the good help that comes from this forum.

---

### Post by pdc on 2013-03-19
Cliff: that is six year old printer; and six years is a long time in computing........Canon now provide good linux support; back then, things were just starting;

first thing would be install drivers: 

so two possible solutions that involve a small amount of cash:

1) buy a new printer: the Canon MG2100 series is on sale in many places for about $US40......over a year or two ink may cost much more if you do a lot of printing; there is full linux support for this current range of MG printers from Canon
2) buy and install turboprint; [http://www.turboprint.info/](http://www.turboprint.info/) (it is easy to do); and it will auto-configure your MX700; [http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_MX700](http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_MX700) ............free in linux means free as in speech, not free as in beer..so these folks put food on the table by doing this linux support

..........software fixes on linux likely involve complicated solutions where you have to kid the computer you are using an MP510 or something......

---

### Post by isantop on 2013-03-20
If you buy a new printer, I'd recommend HP though, as every single printer they sell is fully compatible with Ubuntu and they require minimal configuration.

---

### Post by jaylittle on 2013-03-22
I'd recommend Brother myself.  They provide deb packages for all of their printer drivers and most of those are included in Ubuntu's repositories already.  In addition they don't screw you with drivers on the Windows side like HP does.

---

