---
title: "Laptop power consumption"
date: 2009-09-21
forum: The Cafe
---

### Post by tom66 on 2009-09-21
Run this:

```

cat /proc/acpi/battery/BAT0/state

```

Whilst the battery is discharging, and report back your power consumption figures. 

```

present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            1897 mW
remaining capacity:      2713 mWh
present voltage:         11235 mV

```

Oddly, mine only reports about 2 watts idle, is this normal? I was able to push it up to 4.3 watts by playing a game on max detail (Blood Frontier), running super PI to 2^25 digits, turning on the keyboard backlight, turning on the WiFi and turning up the screen brightness, but it still seems way too low...

---

### Post by LowSky on 2009-09-21
yeah thats way off

---

### Post by koleoptero on 2009-09-21
My laptop battery shows a discharge time of several thousand days. So I assume that all these are not very reliable.

---

### Post by tom66 on 2009-09-21
Still, it does accurately give my battery life of 2.5 hours.

---

### Post by The Toxic Mite on 2009-09-21
> **tom66 said:**
> Still, it does accurately give my battery life of 2.5 hours.
 
2:30 hours = total bull-honky :|

---

### Post by tom66 on 2009-09-22
What do you mean? Vista shows the same. And Dell said it has about 2.5 hours life with basic battery on there specification sheet.

---

### Post by bodyharvester on 2009-09-22
i get the no file or directory message. this is supposed to be entered in the terminal, right?

---

### Post by mikewhatever on 2009-09-22
> **bodyharvester said:**
> i get the no file or directory message. this is supposed to be entered in the terminal, right?

The command is cat /proc/acpi/battery/BAT1/state in may case. I'd also suggest using powertop for a more reliable reading.

---

