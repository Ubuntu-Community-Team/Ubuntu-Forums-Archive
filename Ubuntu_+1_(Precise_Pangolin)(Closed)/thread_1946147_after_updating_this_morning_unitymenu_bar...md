---
title: "after updating this morning unity/menu bar.."
date: 2012-03-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by djbenny on 2012-03-24
i updated this morning, im not sure what the updates were and i dont know how to view which updates were installed though i think i saw something to do with the X server and ALSA but now the menu bar across the top has a big black line underneath it and when i scroll through the unity bar with my mouse the menu changes colour and even sometimes the entire screen flickers. Ubuntu 12.04 on Toshiba NB200

when i attempt to take a screenshot all the issues dont show on it for some reason so i cannot take a shot.

if theres any information i need to put on here let me know also how to find it might be useful..cheers

---

### Post by jayshomebrew on 2012-03-24
[http://ubuntuforums.org/showthread.php?t=1946145](http://ubuntuforums.org/showthread.php?t=1946145)

---

### Post by erikschmitz on 2012-03-24
I had this too... open a terminal and type

unity --reset

then reboot and see if you're sorted. it worked for me.

---

### Post by Rifester on 2012-03-24
> **erikschmitz said:**
> I had this too... open a terminal and type

unity --reset

then reboot and see if you're sorted. it worked for me.

Thanks!   This fixed it for me as well.

---

### Post by jahLux on 2012-03-24
> **Rifester said:**
> Thanks!   This fixed it for me as well.

Same here - THANKS LADS . . . . .

---

### Post by freedomAboveAll on 2012-03-25
> **erikschmitz said:**
> I had this too... open a terminal and type

unity --reset

then reboot and see if you're sorted. it worked for me.

Thank you for mentioning this option!  I ran it from the recovery console, and it fixed a problem I had.

My symptoms:  after morning updates, system would boot to login screen, but would not load Unity. System would sit and spin, or return to login screen.  

The only compiz option I had previously adjusted was to turn on the auto-hide feature for the dock under the Appearance options.

---

