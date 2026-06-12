---
title: "[public service announcement] don't spam lm-sensors with conky!"
date: 2009-02-16
forum: The Cafe
---

### Post by MaxIBoy on 2009-02-16
Okay, I recently glanced at the helpful lm-sensors entry in my Conky sidebar. I discovered to my horror that my laptop was well above critical temperature, and that the fan simply wasn't running. By blowing on the vents with a shop-vac, I could cool it down to 129°F, but it would eventually heat back up, and the fan wouldn't kick in. I restarted my computer, and in the BIOS screen, the fan ran fine, quickly bringing my laptop's temperature to normal. When I ran the OS, it was also fine.

After some experimentation, I discovered that if you run the "sensors" command too often, it will inhibit the fan from running (at least, it will on my Toshiba Satellite A205 S5864.) My Conky setup was running the command once for each core, once every 1.3 seconds.

So if you plan to include a CPU temperature readout in your Conky, use "execi" instead of "exec," and give it a nice long interval like 5 seconds.

Thank you.


If you have experiences contrary to mine, keep in mind that I've only seen this bug on one motherboard.

---

### Post by Daisuke_Aramaki on 2009-02-16
i have no experience with lm-sensors and conky. But i think you should also post this in the Post your .conkyrc thread!

---

