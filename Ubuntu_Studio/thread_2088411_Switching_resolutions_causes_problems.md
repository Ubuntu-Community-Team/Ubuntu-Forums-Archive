---
title: "Switching resolutions causes problems"
date: 2012-11-26
forum: Ubuntu Studio
---

### Post by Ali_Barba on 2012-11-26
Hi, 

I got USt 12.04 LTS 32-bit and an ATI graphics card (HD4770) installed. I use the official ATI driver for Linux, with the Catalyst Control Center. 

The funny thing is that I can only start the user version of the CCC, but you cannot change resolutions or refresh rates there. It shows the message "You must log in as super-user blah-blah ..." in order to change the resolution. No idea how to do that. I thought I was logged in with an administrator account already, but whenever I click on the "CCC (Administrative)" it will not even start ! 

Now I can change the resolution via the Xfce Settings pane > Video/Display, which I did (switched from 1600x1200 down to 1152x864). 

But the problem is that even after a restart, the programs seem to think that my resolution was STILL 1600x1200, while it is lower now, and I can see only a part of the screen, the rest gets cut off on the sides. 

How can I resolve this issue, other than by switching back to 1600*1200 ?

And how can I log in as a "superuser" (whatever that is meant to be - I am the only user of my PC and I want to be in FULL CONTROL of it and not being barred from adjusting my resolution by the nanny-OS !).

---

### Post by Ali_Barba on 2012-11-26
SOLVED: The second monitor (shut down at the time, but still connected to the PC) was set to 1600x1200, and this setting affects the first monitor, though the first was set to 1152x864. Makes sense ? Nope.

---

### Post by jejeman on 2012-11-26
When you use commands: sudo or gksudo
you became the super user.
For example:
for CLI programs
```
sudo nano some_file
```
for GUI programs
```
gksudo gedit some_file
```

---

