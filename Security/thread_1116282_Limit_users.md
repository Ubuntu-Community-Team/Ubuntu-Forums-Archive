---
title: "Limit users"
date: 2009-04-04
forum: Security
---

### Post by Superdude_123 on 2009-04-04
I'd like to know how I can make or add an other user, and limit its ability to change configurations on the system. Basicly, I'd want to let the user add and run games on their account, however, stop them from doing system wide things or going to the windows partition. I'd also like to let them use firefox and all other installed software, but not let them change any system stuff (like any thing in /boot/grub, or /etc/some_system_component)

---

### Post by mikewhatever on 2009-04-05
You can restrict/edit user accounts from System->Admin->Users and Groups, the only problem is with installing games.

---

### Post by albinootje on 2009-04-05
> **mikewhatever said:**
> You can restrict/edit user accounts from System->Admin->Users and Groups, the only problem is with installing games.
You could make a new group called "gamers" and then set up sudo for that group "gamers" which allows usage of apt-get and synaptic package manager for them.
The minor drawback of that is that they will also be allowed to remove software.

---

### Post by bodhi.zazen on 2009-04-05
Both of those suggestions are good starting points. If you need more then that you will need to look at something like apparmor.

---

