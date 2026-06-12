---
title: "(Daru1,8.10) Where's Suspend, Hibernate?"
date: 2008-11-02
forum: System76 Support
---

### Post by MarkID on 2008-11-02
I upgraded to 8.10.  Everything seems to be fine.  But there's no button for suspend, hibernate, restart.  It's not that suspend and hibernate don't work.  When I click on the logout button I get a choice of logout and switch user; there's no option for suspend or hibernate.

---

### Post by gaussian on 2008-11-02
> **MarkID said:**
> I upgraded to 8.10.  Everything seems to be fine.  But there's no button for suspend, hibernate, restart.  It's not that suspend and hibernate don't work.  When I click on the logout button I get a choice of logout and switch user; there's no option for suspend or hibernate.

In Intrepid (along with the new Gnome version) they separated the log-out stuff from the power-management stuff. Just right-click on the upper panel, choose "add to panel" and the "shutdown"-button. It should have hibernate and suspend.

---

### Post by kindofabuzz on 2008-11-18
> **gaussian said:**
> In Intrepid (along with the new Gnome version) they separated the log-out stuff from the power-management stuff. Just right-click on the upper panel, choose "add to panel" and the "shutdown"-button. It should have hibernate and suspend.

Nope. Tried what you said and I don't have a hibernate/suspend either.

---

### Post by hanspb on 2008-11-19
On my system it's to the far right on the top panel, along with my user name.

---

### Post by gaussian on 2008-11-19
> **kindofabuzz said:**
> Nope. Tried what you said and I don't have a hibernate/suspend either.

Try running gconf-editor from command line and search for keys "can-suspend" and "can-hibernate". If they for some reason are false, toggle them to true.

---

### Post by braddock on 2009-01-10
> **gaussian said:**
> Try running gconf-editor from command line and search for keys "can-suspend" and "can-hibernate". If they for some reason are false, toggle them to true.

I have the same issue after a clean install of 8.10, but using a home directory partition from 8.04.

Searching for "can-suspend" and "can-hibernate" in my gconf-editor cannot find any keys.

How can I suspend?

I find it hard to believe that Gnome/Ubuntu have reinvented a Windows Registry Hell.

---

### Post by braddock on 2009-01-10
Okay, found the "Shut Down" applet in "Add to Panel", and now I can suspend.

I have two power buttons on my panel - a red round one for logout, and a round grey one for "power" and suspend, etc.
thanks.

---

