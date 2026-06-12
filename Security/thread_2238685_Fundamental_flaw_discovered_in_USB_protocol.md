---
title: "Fundamental flaw discovered in USB protocol"
date: 2014-08-09
forum: Security
---

### Post by SeijiSensei on 2014-08-09
I came across this article on the BBC site last night:  [http://www.bbc.com/news/technology-28701124](http://www.bbc.com/news/technology-28701124)

> It is not uncommon for USB sticks to be used as a way of getting viruses and other malicious code onto target computers.  Most famously, the Stuxnet attack on Iranian nuclear centrifuges was believed to have been caused by an infected USB stick.  However, this latest research demonstrated a new level of threat - where a USB device that appears completely empty can still contain malware, even when formatted. The vulnerability can be used to hide attacks in any kind of USB-connected device - such as a smartphone.

Apparently they exploited the feature in USB devices where they inform the operating system of their identities.  

> In one demo, shown off at the Black Hat hackers conference in Las Vegas, a standard USB drive was inserted into a normal computer.  Malicious code implanted on the stick tricked the machine into thinking a keyboard had been plugged in.  After just a few moments, the "keyboard" began typing in commands - and instructed the computer to download a malicious program from the internet.

I'm surprised it's taken so long for someone to discover this vulnerability.  It doesn't sound like something the operating system can thwart either.

---

### Post by TheFu on 2014-08-09
Almost every external port used in computing has a negative security aspect.
I've seen USB hacking with HID devices for about 8 yrs and charging-based attacks for 5 yrs.

DisplayPort, Firewire, PCMCIA and any other DMA connection is dangerous too.

In general, whenever marketing says "easier" that means non-secure with computers.  
RFID - nonsecure.  
NFC - nonsecure.
WPS - nonsecure.
I'm worried about the Google/Yahoo! announced email encryption effort too.

I can think of only 1 thing that is more secure AND easier - ssh with keys (and anything based on that technology like rsync).

Since DefCon is happening, look for lots of new hack methods to be announced in the next week or so.

---

### Post by pfeiffep on 2014-08-09
So the old adage "the only secure computer is one that is unplugged and not connected" stands.

---

