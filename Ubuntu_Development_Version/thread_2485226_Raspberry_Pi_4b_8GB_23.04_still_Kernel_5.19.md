---
title: "Raspberry Pi 4b 8GB 23.04 still Kernel 5.19"
date: 2023-03-23
forum: Ubuntu Development Version
---

### Post by hdizzle2 on 2023-03-23
Hiya,

I saw the news the other day that kernel 6.2 was going into 23.04 builds now and so I pushed my pi to latest dev of lunar and it seems to have remained on kernel [COLOR=#B39DDB][FONT=Consolas]5.19.0-1015-raspi[/FONT][/COLOR]

Am I doing something wrong or has 6.2 just not been put into the pi image yet?

---

### Post by hdizzle2 on 2023-03-23
Eh to answer my own question when looking at the daily build image manifest [https://cdimage.ubuntu.com/daily-preinstalled/current/lunar-preinstalled-desktop-arm64+raspi.manifest](https://cdimage.ubuntu.com/daily-preinstalled/current/lunar-preinstalled-desktop-arm64+raspi.manifest) 

I can see that it has a slightly older kernel then the 5.19 I had with kinetic, so I'm guessing I kept my kernel from kinetic in the upgrade and 6.2 isn't in for the Pi image yet (nor 6.1 for that matter)

I can't seem to find any guide to compile rpi kernel in ubuntu either :/ [https://github.com/raspberrypi/linux/tree/rpi-6.2.y](https://github.com/raspberrypi/linux/tree/rpi-6.2.y)

---

### Post by hdizzle2 on 2023-03-28
I ended up just going back to Raspbian which is currently using kernel 6.1.20 with the option of 6.2.8 if I want.

---

