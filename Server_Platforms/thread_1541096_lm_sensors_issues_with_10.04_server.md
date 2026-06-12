---
title: "lm_sensors issues with 10.04 server"
date: 2010-07-28
forum: Server Platforms
---

### Post by paped on 2010-07-28
Hi, I have a small home server based on an atom ITX motherboard and I used to find lm_sensors very useful in previous 8 and 9.x Ubuntu for checking fan speed temperature etc. But since installing 10.04 I cannot seem to get lm_sensors to work I have done a sensors detect and added the modules to the /etc/modules file but all I get is this output:

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +15.0Â°C  (crit = +90.0Â°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +16.0Â°C  (crit = +90.0Â°C)

No fan speeds, voltages etc and the temperatures shown I do not believe, as previous they have always been around 40 to 50 degrees so unless 10.04 comes with a free cooling feature they cannot be right?

Is anyone else having these issues or knows of a fix for this, as I have trying to sort this for weeks trying various posted things but nothing seems to work?

---

### Post by CharlesA on 2010-07-28
It's due to the sensors on the mobo. I've got a 10.04 server install on an Asus mobo that shows fan speeds and voltages.

The same install on a Gigabyte mobo only shows the same thing you see.

---

### Post by kevinthecomputerguy on 2010-07-29
Its been hit and miss for me. Its consistently off by 30 + degrees temp for me. But my servers and non pentium non amd even, so I guess i am getting what i am paying for :- )

---

