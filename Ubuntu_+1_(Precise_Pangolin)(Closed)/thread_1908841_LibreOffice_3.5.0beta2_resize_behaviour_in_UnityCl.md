---
title: "LibreOffice 3.5.0beta2 resize behaviour in Unity/Classic"
date: 2012-01-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by keithpeter on 2012-01-14
Hello All

3.5.0beta2 is installed and working now thanks to earlier thread.

Anyone else seeing odd behaviour when resizing LibreOffice windows using the mouse on the bottom right corner?

Details...

Attempting to resize the window using the mouse on bottom right corner in Writer (24 inch monitor) results in a display of the File menu. Mouse pointer has changed to the 'resize' icon

In Unity 5 there is also an amber rectangle the same size as the window, which remains as the window is moved. I have not been able to resize Office windows in Unity 5

In Gnome Classic (no effects) I still get the File menu when attempting to resize, but it is possible to resize by mouse by clicking *exactly* on the corner.

---

### Post by lucazade on 2012-01-14
I get the same resize issue also in oneiric

---

### Post by PaulW2U on 2012-01-14
I did see some odd effects but I changed to Gnome Shell shortly after getting LO back again.

In Gnome Shell resizing the LO window also produces some strange effects such as a very narrow corrupted column of the spreadsheet grid to the **right** of the scrollbar which disappears when resizing is stopped. The main toolbar is sometimes blank when resizing. It's as if the program window can't be redrawn quickly enough.

---

### Post by howefield on 2012-01-14
Same effect in 11.10 with Libre Office 3.4.4

In addition an orange outline to the window which stays on screen till LO is closed.

---

### Post by keithpeter on 2012-01-14
Hello All

It's a known bug see [#749986]("https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/749986") and a lot of duplicates!

I have not seen this at all in 11.10 or in 12.04 before the 3.5 beta upgrade, so I'm joining the bug report. 

I think that this old bug needs to be fixed for the LTS or if it can't get fixed, then the corner resize needs to be disabled as suggested in the bug report. It would look really bad if someone new to Ubuntu/Linux with a large screen tried to resize and got this strange behaviour.

---

