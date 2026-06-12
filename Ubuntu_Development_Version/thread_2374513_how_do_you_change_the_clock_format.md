---
title: "how do you change the clock format?"
date: 2017-10-16
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2017-10-16
I want it to show month, day, year, and time in 12 hour period
Right now it says
Mon 17:35

---

### Post by RobGoss on 2017-10-16
What version of Ubuntu are you using?

---

### Post by mc4man on 2017-10-16
Settings > Details > Date & Time

---

### Post by RobGoss on 2017-10-16
You can also **Right click** at the top right hand were you see your clock it will also bring up the settings also

---

### Post by sdowney717 on 2017-10-16
well, it helped using settings date and time menu. Right click clock, i dont see any options to change the format.
I was running 16.04, and  I think it showed an expanded date and time. I am on the 17.10 version now.

---

### Post by RobGoss on 2017-10-16
>  well, it helped using settings date and time menu.  

Were you able to change the format?

Do you see the time in the right hand corner of your desktop?

---

### Post by sdowney717 on 2017-10-16
> **RobGoss said:**
> Were you able to change the format?

Do you see the time in the right hand corner of your desktop?

No, the time is in the middle.
All I can change is from 24 to 12 hour time.

---

### Post by mc4man on 2017-10-16
format only - scr. 1 
date - scr. 2 (dconf-editor
Or maybe the gnome tweak tool can also present
See no option to add year, not needed in gnome-shell as it's timeless..

---

### Post by RobGoss on 2017-10-16
When you go into the settings you should see **Time & date **and **Clock,** click on** clock **and there are all the options you need to change. Please see the screen shot below

---

### Post by sdowney717 on 2017-10-16
> **mc4man said:**
> format only - scr. 1 
date - scr. 2 (dconf-editor
Or maybe the gnome tweak tool can also present
See no option to add year, not needed in gnome-shell as it's timeless..

Thanks, that did it, now looks like i remembered, Simply did this 
sudo apt-get install dconf-tools
then ran dconf-editor
then followed your picture header text that leads to the clock setting.

---

