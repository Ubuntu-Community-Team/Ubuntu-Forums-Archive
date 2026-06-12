---
title: "messed up again"
date: 2007-12-16
forum: Virtualisation
---

### Post by drmaxmad on 2007-12-16
hi.....

i have changed the screen refresh rate to some thing that is ot supported by my monitor and so i am unable to see GUI....my logon screen looks mess...how can i get it back....

---

### Post by scottmuz on 2007-12-16
Your X-Org conf file should have been backed-up.
Look in directory  /etc/X11

---

### Post by drmaxmad on 2007-12-16
thanks for the help man but i am damn new so little explanation will be helpful...but thanks again...........just how can i get it without getting into GUI

---

### Post by scottmuz on 2007-12-18
Sorry for not getting back earlier my broadband was down for a day.

I assume you get to a login without X running. If so login with your normal
user and password and then enter on the command line:

cd /ect/X11
ls -1tr xorg*

Note the last 2nd last xorg file listed (assuming xorg.conf is the last) do:
sudo cp xorg.conf xord.conf.bad
sudo cp <2nd last file> xorg.conf

Then enter 
sudo init 6
to reboot your PC. Hopefully GUI should then be fixed.

---

