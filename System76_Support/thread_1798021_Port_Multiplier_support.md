---
title: "Port Multiplier support?"
date: 2011-07-05
forum: System76 Support
---

### Post by benenglish on 2011-07-05
Do System76 desktop systems with eSATA ports generally (and specifically the Wild Dog variant I'm considering purchasing) support port multipliers?

I've had some problems with my current enclosure and am thinking of replacing it with [this one]("http://www.icydock.com/goods.php?id=123") or [this one]("http://www.wiebetech.com/products/specsheets/RTX_400_SV_spec.php") at the same time as I purchase my next computer, probably within the next couple of weeks.  Port multiplier support is a must.

Anybody know?

TIA for any help.

Ben

---

### Post by benenglish on 2011-07-07
Anybody from System76 out there?  I need to make a purchase in the very near future.  TIA.

---

### Post by Rob_H on 2011-07-27
I am also interested in this. Considering purchasing an external hard drive enclosure and need to know if the eSATA interface on the Meerkat Ion Nettop has Port Multiplier w/ FIS-based switching support. System76?

---

### Post by luwenliang0611 on 2011-07-28
These things looked pretty good, and some that I can learn, and I hope to learn more on it!

---

### Post by benenglish on 2011-08-09
Just following up - 

After exchanging emails with Carl at System 76, he informed me that the system I was considering used the Intel H67Express chipset which, according to kernel.org, supports PMP.  AHCI must be set and their chart is confusing (it appears that command-based switching is all I can get, but I'm not after peak performance in this case so that doesn't bother me) but based on our emails and my best guess, I went ahead and ordered.

Chart here:  [https://ata.wiki.kernel.org/index.php/SATA_hardware_features](https://ata.wiki.kernel.org/index.php/SATA_hardware_features)

Naturally, in default config only one drive of the four in my JBOD box is recognized.  Nothing is ever easy, is it?

I'm talking to fine support at the JBOD supplier and they're researching it for me.  This isn't a killer issue for me; I have a Windows machine I could connect the JBOD to, thus enabling me to connect to it over the network.  However, I would have much preferred direct access and one less computer on my home network.

Just thought I'd try one more time asking here, this time rephrasing my question with better specifics.

To wit - 

I have this:  [http://www.wiebetech.com/products/specsheets/RTX_400_SV_spec.php](http://www.wiebetech.com/products/specsheets/RTX_400_SV_spec.php)

It's connected to a brand new Wild Dog, all default settings still in place.  Per System76, per kernel.org, and per the Intel specs for the DH67CL mobo, port multiplication should work.

However, the computer sees only one of the four installed drives, which is by far the most common apparent failure mode when PMP is not supported.

Question:  Can anyone from System76 give me any clues as to how to make this combination work the way everyone's spec sheets seem to indicate it should?

TIA for any help.

Ben

---

### Post by Rob_H on 2012-02-05
Well, I took a risk and bought a four-drive enclosure for the Meerkat Ion Nettop and... got burned. Only the first drive is visible in Ubuntu and the activity LED for the second drive is constantly lit from the moment the BIOS splash screen appears. I'm assuming this means no port multiplier support, but if anyone knows of any magical BIOS setting that will solve this, I'd be very grateful.

---

