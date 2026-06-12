---
title: "GAZV5 No longer charges the battery"
date: 2009-06-17
forum: System76 Support
---

### Post by ctsdownloads on 2009-06-17
Really frustrated as I am totally lost as to why this has happened. Old battery in slot, it never charges and stays at a full 76% charged. Just received battery replacements today from System76 for my GAZV5 and the brand new battery....blinks the indicator like before....but also, is not charging.

No dropping, shaking or physical events to the notebook at all. Batteries are fully inserted and mechanisms are fully latched. I have a second new battery that came today, too. Don't think this is a battery issue any longer and am leaning toward the charging portion of the motherboard going belly up. Really baffled as NOTHING at all has happened to the notebook. It never leaves my office...

I own other massively older and cheaper notebooks that have been beaten to death that have never shown this problem before. What is going on?

---

### Post by jdb on 2009-06-18
> **ctsdownloads said:**
> Really frustrated as I am totally lost as to why this has happened. Old battery in slot, it never charges and stays at a full 76% charged. Just received battery replacements today from System76 for my GAZV5 and the brand new battery....blinks the indicator like before....but also, is not charging.

No dropping, shaking or physical events to the notebook at all. Batteries are fully inserted and mechanisms are fully latched. I have a second new battery that came today, too. Don't think this is a battery issue any longer and am leaning toward the charging portion of the motherboard going belly up. Really baffled as NOTHING at all has happened to the notebook. It never leaves my office...

I own other massively older and cheaper notebooks that have been beaten to death that have never shown this problem before. What is going on?

The charging control circuit is built into the battery.
The only part the motherboard plays is reading the state of the battery over a bus that the battery is connected to.
If you have tried another charger then it is probably a bad connection between the charger & battery.

jdb

---

### Post by thomasaaron on 2009-06-18
We've also solved this problem in the past by resetting the cmos. If we've not already tried that, send an email to support(at)system76(dot)com for instructions.

---

### Post by eddietours on 2009-06-18
Hey Thom that was for me ;)the cmos fix

---

### Post by ctsdownloads on 2009-06-18
> **jdb said:**
> The charging control circuit is built into the battery.
The only part the motherboard plays is reading the state of the battery over a bus that the battery is connected to.
If you have tried another charger then it is probably a bad connection between the charger & battery.

jdb

Assuming the plugin adapter can still power the notebook just fine with damage to the part that charges the battery, this makes sense. But one would think that if it was not charging the battery(s) (new and old), that it would be unable to power the notebook, no? :)

---

### Post by ctsdownloads on 2009-06-18
> **thomasaaron said:**
> We've also solved this problem in the past by resetting the cmos. If we've not already tried that, send an email to support(at)system76(dot)com for instructions.

Emailing now - thanks Tom. I have been in the BIOS and it is pretty basic with no control over anything short of boot order. So resetting the CMOS makes sense. Never done this on a notebook, but have been doing this with desktops since the early '90's...so I imagine it should easy enough.

---

### Post by jdb on 2009-06-18
> **ctsdownloads said:**
> Assuming the plugin adapter can still power the notebook just fine with damage to the part that charges the battery, this makes sense. But one would think that if it was not charging the battery(s) (new and old), that it would be unable to power the notebook, no? :)

I think I miss-understood, I was thinking the battery wasn't charging.
Is it just the reading that is bad but the battery is really fully charged?


jdb

---

### Post by ctsdownloads on 2009-06-18
> **jdb said:**
> I think I miss-understood, I was thinking the battery wasn't charging.
Is it just the reading that is bad but the battery is really fully charged?


jdb


Notebook is getting power to run daily operations as long I keep it plugged in, provides LED indicator of charging as does the GNOME battery icon. However, while the notebook is getting power to run, the battery is NOT charging. ;)

---

### Post by thomasaaron on 2009-06-18
If you run on battery power, will the charge percentage drop?
If so, will it then charge back up to 75%?

---

### Post by ctsdownloads on 2009-06-18
> **thomasaaron said:**
> If you run on battery power, will the charge percentage drop?
If so, will it then charge back up to 75%?


Great question. Yes, with the original battery, it ran down completely (bad I know) but needed to test for troubleshooting purposes.


And both new batteries no charge to them at all nor are they able to charge, either. 

So it breaks down as following:

[LIST]
[*]Notebook is able to be powered by adapter.
[*]Old and new batteries are not charging.
[*]Old battery was also able to be discharged.
[/LIST]

Sent off that email for the CMOS help, guess this is the next step?

---

