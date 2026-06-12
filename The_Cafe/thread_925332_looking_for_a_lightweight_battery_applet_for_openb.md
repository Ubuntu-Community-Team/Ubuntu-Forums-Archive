---
title: "looking for a lightweight battery applet for openbox"
date: 2008-09-20
forum: The Cafe
---

### Post by markp1989 on 2008-09-20
title says it all, im looking for a **small** program that will just sit in the notification area of fbpanel and just tell me how much charge there is in the battery, any sugestions?


Thanks Markp1989

---

### Post by notwen on 2008-09-20
if none turn up, you could always consider a conky script to do this very thing.  =]

---

### Post by spupy on 2008-09-20
Alas, i haven't found this kind of program. I'm still using gnome-power-manager. It is good because it has menu with suspend/hibernate and hibernates your laptop when the battery is critical.

---

### Post by mips on 2008-09-20
[http://ph.ubuntuforums.com/showpost.php?p=5798851&postcount=26](http://ph.ubuntuforums.com/showpost.php?p=5798851&postcount=26)

The above post will probably solve your problem.

Not familiar with fbpanel.

Also look at noteo, lithium, xbat, ibam, wmapm, wmapmload, wmbattery, wmbatteries, wmacpiload-ac, conky

---

### Post by markp1989 on 2008-09-20
thats almost what i wanted, just takes up more space then i hoped


id like it just to say "charging %" and "discharging %" with out the other stuff 


see screen shot

---

### Post by urukrama on 2008-09-20
> **mips said:**
> Also look at noteo

That is what I was going to suggest: [http://bavardage.awardspace.com/noteo/](http://bavardage.awardspace.com/noteo/)

---

### Post by markp1989 on 2008-11-29
> **markp1989 said:**
> thats almost what i wanted, just takes up more space then i hoped


id like it just to say "charging %" and "discharging %" with out the other stuff 


see screen shot

sorted out  , changed acpi -b to "acpi | cut -c17-31"
only problem is that it cuts the  % sign of when running on battery power

so i wrote a small script to check if the batter is charging or discharging, then cut the acpi out put accordingly , 

```
#!/bin/bash
if acpi | grep -qw discharging; then
acpi | cut -c17-32
else
acpi | cut -c17-29 
fi
```
 
i saved that file as .battery.sh

just added 
```

Plugin {
type=genmon
config {
Command = ~./battery.sh
PollingTime = 10
TextSize= small 
TextColor=black
}
}
```

to my fbpanel config

---

