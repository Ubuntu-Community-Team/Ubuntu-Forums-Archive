---
title: "Can only open one terminal at a time.  Starling Netbook"
date: 2009-06-16
forum: System76 Support
---

### Post by Ryzol on 2009-06-16
I have gnome-terminal installed. I click on it it from the gui, it opens. I click on it again from the gui to open a 2nd terminal, and it will not open. I can launch a 2nd gnome-terminal from the commandline, but I want to be able to launch as many as I wish from the gui. How do I do this?

---

### Post by swisstone198 on 2009-06-16
Does it show "starting terminal" in the windows list?

If you add the launcher to the desktop do you get the same results?

---

### Post by Ryzol on 2009-06-16
Ok this gets weirder. I only have this problem when I try to launch gnome-terminals from my favorites group. I can launch as many gnome-terminals as I want if I try to launch it from the accessories group. I checked their properties, the launchers in both groups run the exact same command.

It does not show starting terminal, instead it switches me to an already opened terminal. I don't know about a launcher on the desktop, I'm running the default Starling netbook UI, which doesn't use a desktop. Instead, it's basically one big menu. However, I did switch it to the desktop layout to test this, and it opened many terminals both from favorites, and from a desktop launcher.

I'm starting to think this is a bug.

---

### Post by swisstone198 on 2009-06-16
If you edit your menu and remove terminal then add back in does this still show same issues?

---

### Post by Ryzol on 2009-06-16
> **swisstone198 said:**
> If you edit your menu and remove terminal then add back in does this still show same issues?
Yes.

---

### Post by thomasaaron on 2009-06-17
That's strange behavior, and it's probably a bug that should be reported against Ubuntu Netbook Remix. But have you considered opening one gnome terminal and then using File > New Tab to open several tabs.

I've always found that more convenient than having multiple windows open. Plus, it is less RAM and CPU intensive.

---

