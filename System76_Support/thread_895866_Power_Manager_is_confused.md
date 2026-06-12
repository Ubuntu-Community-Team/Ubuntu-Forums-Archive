---
title: "Power Manager is confused"
date: 2008-08-20
forum: System76 Support
---

### Post by elusivespoon on 2008-08-20
Since I upgraded to Hardy the power manager has been acting strangely. Sometimes it disappears to reappear later. And other times it just gives inaccurate information. Most notably it gives a "Fully Charged" notice when the laptop is not plugged in and charging. The battery charge level is usually accurate. It's mostly just confused about whether it's plugged in or not. 

This is on a Daru2.

---

### Post by thomasaaron on 2008-08-20
Look here...
[http://ubuntuforums.org/showthread.php?t=772722&highlight=power+management](http://ubuntuforums.org/showthread.php?t=772722&highlight=power+management)

You will need to add acpi=noirq as a kernel option to calm your power management.

Your suspend will not work either in Hardy. This is a known bug and is being worked on.

---

