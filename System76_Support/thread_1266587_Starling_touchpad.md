---
title: "Starling touchpad"
date: 2009-09-14
forum: System76 Support
---

### Post by ShowMeGrrl on 2009-09-14
Is it possible to turn the Starling touchpad off when I am using a USB mouse? How?

---

### Post by bodam on 2009-09-15
> **ShowMeGrrl said:**
> Is it possible to turn the Starling touchpad off when I am using a USB mouse? How?

Try this:

If you go to a terminal and enter this command. This is how I do it on the Serval...
 	Code:
 	sudo modprobe -r psmouse 
...it will disable your mousepad.

To re-enable it...
 	Code:
 	sudo modprobe psmouse

---

### Post by WarLokk on 2009-09-17
You can also go to "Mouse" under Preferences and one of the Tabs has an option to turn off the Touchpad.
 
I don't have my computer here with me at the office, but I know I just did this the other night.
 
Hope it helps if you wanted a more GUI approach

---

### Post by ShowMeGrrl on 2009-09-17
> **WarLokk said:**
> You can also go to "Mouse" under Preferences and one of the Tabs has an option to turn off the Touchpad.
 
I don't have my computer here with me at the office, but I know I just did this the other night.
 
Hope it helps if you wanted a more GUI approach
Thanks much WarLokk. It was very easy to do and worked. Now I no longer have to worry about inadvertent brushes of the touchpad as I'm typing, producing bizarre and unintended results!

---

