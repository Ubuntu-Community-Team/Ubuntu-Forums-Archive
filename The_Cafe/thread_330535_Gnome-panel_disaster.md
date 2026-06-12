---
title: "Gnome-panel disaster"
date: 2007-01-03
forum: The Cafe
---

### Post by PatrickMay16 on 2007-01-03
I've always found gnome panel to be pretty glitchy.

I turned on my computer this today, and logged into gnome, and as usual after having to change screen resolution (I ran a game in wine last night which changed the resolution) something on the panel was messed up. In this case it was the system monitor thing. So I removed it from the panel and added it again, then got an error message: An error occurred, you may not be able to save changes to the panel. Clicking "view detailed" showed me "type mismatch: expected list, got string" or something.

Then I logged out and in again *and all my launchers and the menu were gone*. I had to spend about 20 minutes putting everything back. 

Anyone know a way of backing up the current configuration of the gnome-panel? It would save me having to put everything back manually if this should happen again.

---

### Post by 23meg on 2007-01-03
[https://wiki.ubuntu.com/PanelSwitcher](https://wiki.ubuntu.com/PanelSwitcher)

---

### Post by Sammi on 2007-01-03
Nice looking app. And I like what's it's supposed to do. I think mostly all gnome users have experienced the panel getting messed up at some point, and then having to rearange everything again.

Problem is that the I tried out the app and it didn't really work very well. Looks good, but it applied my configuration wrong after I had saved it and then chosen to apply it.

Then again, this should maybe be expected, because the apps seems to be in alpha or beta pre-release.

---

### Post by ComplexNumber on 2007-01-03
> **PatrickMay16 said:**
> 
Anyone know a way of backing up the current configuration of the gnome-panel? It would save me having to put everything back manually if this should happen again.
save the contents of */home/<your-username>/.gconf/apps/panel *

---

