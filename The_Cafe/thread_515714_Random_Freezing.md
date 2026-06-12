---
title: "Random Freezing"
date: 2007-08-02
forum: The Cafe
---

### Post by fwwarr on 2007-08-02
Hi

I'm having a strange freezing problem with my new computer. It has been working without the slightest hitch for about 2 weeks but since yesterday it freezes up after 5 minutes to an hour or so. The computer then doesn't respond to the keyboard or the mouse at all (no mouse movement). The audio output repeats the last half second of sound over and over.

I'm pretty sure it's not actually related to Ubuntu 7.04 (the only OS I have installed on the hard drive) because the freezing also happens when I boot from the live cd and even in the BIOS.

I'm also pretty sure it's not a temperature problem because I left it in the BIOS screen that monitors the system and cpu temps as well as the voltages, and when it froze, the cpu temp was 43C and the system temp was something under 40C. The voltages seemed normal too, although some of the voltages were slightly higher than the rated value, nothing big though.

I tried to run a memtest from the live cd, but the computer froze about 20% of the way into the 1st pass, no errors had been reported by then.

Here are the components I bought off tigerdirect.ca and put together myself:
Motherboard: Abit LG-95Z
Processor: Intel P4 640, 3.2GHz, 2MB L2 Cache, 800MHz FBS
Memory: Ultra 1024Mb, DDR2 PC2-4200, 533MHz
Graphics: Integrated Intel GMA950
PSU: Ultra 350W
Fans: 1x120mm rear fan @~1200rpm, 1x80mm side fan @~1700rpm with duct to direct air straight onto the (stock) cpu cooler.

Does anyone have any idea what the problem could be and how to fix it?

Thanks
Fred

---

### Post by tcpip4lyfe on 2007-08-02
Download Ultimate boot cd:

[http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

and do a memory burn test.

Im thinkingi ts probably a memory issue.

BTW this probably isn't the right place to post this and I image it
ll get moved.

---

### Post by smoker on 2007-08-02
i'd check the power supply, 350w may be struggling a bit, if you have a higher rated psu try swapping them round.

also, check the hard drive with the above mentioned app,

best of luck

---

### Post by fwwarr on 2007-08-02
Hi
Thanks for the suggestions.
I did the memtests from the ultimate boot cd, but they didn't find any errors.
Since I don't have an extra more powerful power supply, I just disconnected the side 80mm fan and the front usb ports. It's been running well now for a few hours so I'm thinking you were right about the psu struggling a bit. It must have been just a little too much. I think I'd better get a better power supply.
Thanks!

---

