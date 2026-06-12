---
title: "PanP5 - Screen gone blank and stays blank, even on restart"
date: 2013-11-22
forum: System76 Support
---

### Post by iiullah on 2013-11-22
Hi all, a few minutes back, the display on my until-now-trusty PanP5 suddenly went blank. Restarting did not solve it (tried several times), and it's more than just a "blank screen", the entire display seems *turned off* even though the power light comes on, I can hear the disk spinning, and the fan is blowing. Plugging in an external display doesn't work either. I have tried the old trick of pulling the battery, holding down the power key for some time, and then putting the battery back and restarting, but that doesn't work either. There seems to have been no precursory symptoms (although the screen briefly flashed off and on once earlier this morning). So, is my video card shot? Or could it be something else? If it's the video card, then what are my options in terms of buying a new one? Is it better to consider a new laptop?


FWIW, I'm totally backed up to the cloud via Ubutnu One, so I'm able to keep working on my desktop for the time being.

Thanks in advance for advice/help!

~Isaac

---

### Post by isantop on 2013-11-22
Does the system work from an external monitor?

---

### Post by iiullah on 2013-11-23
Hi there. Thanks for your reply... Unfortunately it doesn't work from an external monitor either. I'm now pretty sure that the video card is dead. I'm going to crack it open later today just to be sure that its not as simple as a loose connection somewhere. I'll report back here after that....

---

### Post by iiullah on 2013-11-26
Well, sadly, it seems that the motherboard is indeed shot. So, farewell PanP5. I was able to harvest the HDD from it, however, and am now just waiting for an external USB 3.0 enclosure so I can get back to work. Although I would dearly love to buy another Sys76 laptop, it's unfortunately beyond my financial means to so. All I could afford is an Acer C720 Chromebook ($250), which I just ordered. With some luck, I'll be able to configure the OS on my salvaged HDD so I can boot the C720 off of it, and be back in my same system. From all I've read, the C720 supports USB booting in its legacy BIOS mode, and a few choice kernel patches will get a "vanilla" Ubuntu system playing with all it's hardware. I imagine I'll also have to somehow uninstall the Sys76 Driver and the propietary graphics drivers first. If I can get it to work so that I can plug it in and boot into it, then that's the best solution I can hope for...

So long Sys76, and thanks for all the fish!

---

### Post by isantop on 2013-11-27
The System76 driver won't affect the Chromebook. You would need to remove the proprietary drivers, though. You would want to boot to recovery mode and remove them from the command line.

---

