---
title: "admin  in synoptic"
date: 2011-03-06
forum: Server Platforms
---

### Post by macstl on 2011-03-06
I loaded gnome on 10.19 server and when i try to use synatic pkg mgr. it won,t accept my admin pw. However if i exit gnome and use sudo halt , it accepts my admin pw. I don't remember it asking for anything when i installed gnome. What to do?

Should i reload gnome. if so how do I remove gnome?

---

### Post by sergio-bobillier on 2011-03-06
Why would you install gnome on a server? Ubuntu server is meant to be run without GUI because you don't want to throw resources in that in a server machine. I would suggest you to use apt and dpkg to manage your packages on the server.

apt allows you to search for packages by name, install, remove and see which ones you have installed, pretty much what synaptic does without the GUI.

Anyway if you already have gnome installed try gksu with is the GUI version of sudo for gnome like so:

gksu "synaptic"

This may do the trick.

---

