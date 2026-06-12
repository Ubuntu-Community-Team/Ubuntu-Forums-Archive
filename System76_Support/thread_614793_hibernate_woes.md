---
title: "hibernate woes"
date: 2007-11-16
forum: System76 Support
---

### Post by subbuss on 2007-11-16
Hibernate "works" on my Gutsy (system76 gazelle vallue) laptop -- but would be good to fix the remaining problems.

1. The wifi radio switch is off most of the times and I have to bring it up with the Fn-F2 command.

2. The battery / power management setup gets all screwed up.  The battery applet always shows 'zero' power and doesn't recognize whether I am on AC or on battery power.  Without knowing how much battery power I have, I have run out of juice and powered down completely a few times while I was in the middle of something.  So, I have not taken to being conservative and plugging in my laptop as much as possible when I have come out of hibernate.

Any leads / help in fixing problem number 2 will be appreciated.

Thanks,
Subbu.

---

### Post by thomasaaron on 2007-11-16
Subbu,

Give me a call at Support on Monday.

Best,
Tom

---

### Post by AusIV4 on 2007-11-18
What version of the Gazelle Value is this? I had the same problems on my Gazv3 in Feisty, but Gutsy seems to have smoothed everything out.

---

### Post by thomasaaron on 2007-11-18
The battery monitor problem sounds like a loose connection. Can you make the monitor flip-flop by jiggling the connection (any of the connections, actually: a/c outlet, wires going into/out of the transformer, jack going into the computer).

---

### Post by subbuss on 2007-11-20
I dont think it is any physical connection ... because consistently, the battery applet shows information correctly when it is booted up, but every time it comes out of hibernate, it shows zero battery and the power management is non-functional.  so, wonder if it is some apic settings that are not being properly restored?

---

### Post by jhisch on 2007-12-08
I can confirm the second problem (Gutsy, Dell 640m). 
I hibernated on battey power and wake up on AC without battery. Now I have a red battery symbol in my gnome-panel and 'cat /proc/acpi/battery/BAT0/info' says:
```
present:                 yes
design capacity:         0 mAh
last full capacity:      0 mAh
battery technology:      rechargeable
design voltage:          0 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  0 mAh
capacity granularity 2:  0 mAh
model number:            
serial number:           0
battery type:            
OEM info:
```

cat /proc/acpi/battery/BAT0/state:
```
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            1 mA
remaining capacity:      0 mAh
present voltage:         0 mV
```

The other way round (hibernate on AC, wake up on battery) also produces a weired battery-icon.

Any idea how to fix this?

---

