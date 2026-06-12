---
title: "Galago UltraPro galu1 battery replacement"
date: 2017-12-20
forum: System76 Support
---

### Post by moschops on 2017-12-20
After a couple of years of not using it (I went to the Mac side and came back) I find my Galago UltraPro battery doesn't hold a charge for more than about 15 minutes.  It never did last that long - maybe 2.5 hours tops when new - but this is ridiculous.  I contacted System76 and they advised I replace it but they no longer supply that battery.  

There is an old thread on this forum with links to a UK company and ebay seller too.

System76 said check eBay but I found that you can buy the battery on Amazon which is probably a bit safer for returns.

The UltraPro is really just a rebadged Clevo W740SU and you can search on that or the part number which is 6-87-W740S-42E - it should be a 53Wh or 4800mah battery.  

There are a few companies selling it (maybe they are on eBay too) with free shipping at around $69.

[https://www.amazon.com/Batterymarket-Replacement-Schenker-6-87-W740S-42E-W740BAT-6/dp/B06XYXXTN7](https://www.amazon.com/Batterymarket-Replacement-Schenker-6-87-W740S-42E-W740BAT-6/dp/B06XYXXTN7)

You have to partially disassemble the laptop to install the battery, this is not a slot in part.  There is a video on how to open up your laptop here although not specifically about replacing the battery: [https://www.youtube.com/watch?v=OchC8ZzKdKI](https://www.youtube.com/watch?v=OchC8ZzKdKI)

Some people ordering batteries online report them being DOA or not working after a while - I chose the Batterymarket seller on Amazon because they claim a 100% satisfaction guarantee.  If I have any issues I'll report back on this thread.

---

### Post by moschops on 2017-12-28
Well I got my new battery from Batterymart and it was easy to fit. Unfortunately although the system boots and runs the indicator in Ubuntu 17.10 is permanently stuck at Estimating. Checking the device itself via the upower command it tells me the battery is at 0%. 

Some people suggest the only way around this is to remove the Bios backup battery and let the BIOS erase its memory. I will try that if letting the battery drain and then recharge doesn't work.

---

### Post by moschops on 2017-12-28
After contacting System76 I unplugged the main battery and removed the CMOS battery - under the keyboard on the left hand side - let it sit for a few minutes (pressing the power button just in case there was an residual power in capacitors, probably not necessary). On restart the battery indicator was now showing it at 40% and the battery stats from the upower command was valid again. 

System76 pointed me at this article [http://support.system76.com/articles/battery/](http://support.system76.com/articles/battery/) which also mentions deleting the battery stats files to cause Linux to retrain the battery life calculations:

> Useful Commands
upower -i /org/freedesktop/UPower/devices/battery_BAT0
This will show the information that your computer can read about the battery.

sudo rm /var/lib/upower/*
If the battery life indicator is inaccurate, this will remove the stored statistics. After a few charge/discharge cycles the indicator should be more accurate.


---

