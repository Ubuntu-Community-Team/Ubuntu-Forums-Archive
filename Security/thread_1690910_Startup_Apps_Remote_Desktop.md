---
title: "Startup Apps: Remote Desktop"
date: 2011-02-19
forum: Security
---

### Post by visual1ce on 2011-02-19
In System -> Preferences -> Remote Desktop, Allow other users to view your desktop is not checked but in System -> Preferences -> Startup Applications, Remote Desktop (GNome Remote Desktop Server) is ticked.

In any case I don't want to my desktop to be accessible and I guess I was surprised to see that Remote Desktop is checked as a startup programme even though remote desktop is disabled... Should I simply uncheck Remote desktop in startup programmes or is there a reason why it is checked? It runs a programme called vino-server...

---

### Post by An Sanct on 2011-02-19
If you don't wish it to run on start up, un-check it.

If at any point you change your mind, check it back, there should be no problems if you do so.

---

### Post by rookcifer on 2011-02-20
Uninstall that junk if you don't use it.  Search for vino in the package manager (in order to get the exact name of the package) and run:

sudo apt-get remove package_name

If you don't want to do that, at least make sure it isn't any longer listening by:

sudo netstat -autpnl

---

