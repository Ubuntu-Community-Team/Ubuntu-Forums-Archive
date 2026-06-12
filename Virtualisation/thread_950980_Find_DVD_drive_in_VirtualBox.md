---
title: "Find DVD drive in VirtualBox ?"
date: 2008-10-17
forum: Virtualisation
---

### Post by Drakkor on 2008-10-17
I have XP as guest on Ubuntu Hardy machine, and I want to burn a DVD in XP.
But it does not find a DVD writer ! Any ideas ?  Thanks :)

---

### Post by Shazaam on 2008-10-18
Do you have the drive set up in VBox?
Start VBox, highlight the XP guest and go to Settings>CD/DVD-ROM, make sure the top box is checked and it shows your drive (host drive).

---

### Post by Drakkor on 2008-10-18
OK,as you can see in the first screenshot, the my XP host dvd is mounted,but then when I run XP,it seems to be greyed-out ! :confused:

---

### Post by Shazaam on 2008-10-19
Don't quote me but I think that since it is greyed out in picture 2 means the drive is already mounted. Try burning the dvd in your XP guest.

---

### Post by stinger30au on 2008-10-19
save the dvd info as an .iso file


have a shared directory between linux and ubuntu via guest addition software


burn the .iso using K3B from ubuntu



i do it all the time

---

