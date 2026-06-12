---
title: "Compiz screwed up my Top toolbar"
date: 2008-02-17
forum: Virtualisation
---

### Post by zeroenna on 2008-02-17
I ran this command "compiz --replace gconf" in order to get my cube function running and i've lost the top toolbar that has the maximize, minimize and exit buttons as well as the name of the application I am running.  I don't know how to back out but I'd like to if someone could help please.

---

### Post by alan34 on 2008-02-17
Try

compiz --replace -c emerald &

If you do not have emerald installed go

System - Administration - Synaptic Package Manager

Search for emerald and install.

Emerald is the window decorator for compiz, top buttons etc.

To make it the default go

System - Preferences - Session and add the command above

---

### Post by gare on 2008-09-09
I also lost top tool bar on every window.

In my case, selecting this option brought it back: 

System > Preferences > 
Advanced Desktop Effects Settings, Window Decoration

---

