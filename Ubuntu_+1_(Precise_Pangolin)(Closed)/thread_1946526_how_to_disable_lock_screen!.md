---
title: "how to disable lock screen!"
date: 2012-03-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by nanog on 2012-03-25
the fact that i cannot disable "lock screen" is driving me nuts. i have multiple boxes with "disable lock screen" checked in gocnf2 and yet still have a locked screen after a few minutes of inactivity.  the system settings "lock screen" toggle is grayed out and unresponsive.

---

### Post by dcstar on 2012-03-25
> **nanog said:**
> the fact that i cannot disable "lock screen" is driving me freaking nuts. i have multiple boxes that have "disable lock screen" checked in gocnf2 and yet still have a locked screen after a few minutes of inactivity.  the "lock scren" toggle is grayed out in system settings.

Did you actually try clicking on the "Off"?

---

### Post by nanog on 2012-03-25
oh...yes.  

does anyone know which conf or system file now controls lockout in precise?

---

### Post by cariboo on 2012-03-25
System Settings->Brightness and Lock.

---

### Post by nanog on 2012-03-27
cariboo, as i stated previously i know exactly where the toggle is located:

>  the system settings "lock screen" toggle is grayed out and unresponsive.

i have the appropriate key disabled in gconf2 but lock screen is still disabled. did ubuntu move this functionality to a new config key/variable?


i have a feeling that an update borked permissions. sudo works fine.

---

### Post by nanog on 2012-03-31
I am going to answer my own question. Gconf is deprecated and many keys are non-functional. Moreover,  the unity systems-settings gui interface becomes completely useless if the user's dconf profile is corrupt (as will likely happen to many users following upgrade). At this point even an extremely experienced user like myself is left scratching their head.

The dconf-editor is your friend.

sudo apt-get install dconf-editor

click org (WTF gnome?) => click gnome=> click plugins => click power => untick the  "active" key

for command line aficionados this can be done using the gsettings utility.

Rant: Gnome has managed to convert a simple key editor (gconf2) into one of the most ridiculous and least user friendly collection of keys I have ever seen. 

Grrrrr.

---

