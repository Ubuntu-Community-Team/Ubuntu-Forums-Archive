---
title: "Hard-drive and motherboard tempurature monitoring."
date: 2007-12-11
forum: Server Platforms
---

### Post by alasdair.mccall on 2007-12-11
Hi Guys,

How can I monitor the motherboard and hard-drive heat on my monitor-less server? I just want to be able to check it ever now and then via the console.

Many thanks, sorry if I missed the post regarding this seemingly simple question.

Alasdair.

---

### Post by lha on 2007-12-11
Use hddtemp and lm-sensors.

---

### Post by PetePete on 2007-12-11
try
cat /proc/acpi/thermal_zone/THRM/temperature

---

### Post by tgalati4 on 2007-12-11
On my Intel MB, that gives me the MB temperature.  To get the actual CPU temperature you might need to install lm-sensors and run:

>sudo sensors-detect

answering Yes to most or all of the questions.

Once installed:

>sensors | grep "what you are specifically interested in"

Also xsensors gives you graphical display that you can use in a remote sension.

---

