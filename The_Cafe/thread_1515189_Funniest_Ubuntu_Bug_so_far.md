---
title: "Funniest Ubuntu Bug so far"
date: 2010-06-22
forum: The Cafe
---

### Post by Djalmahal on 2010-06-22
So when I click on Places>Download my ubuntu 10.04 opens a folder on the Desktop with audio files in VLC, happens again and again,LOL

---

### Post by MasterNetra on 2010-06-22
> **Djalmahal said:**
> So when I click on Places>Download my ubuntu 10.04 opens a folder on the Desktop with audio files in VLC, happens again and again,LOL

Must be unique for ya. Its not a distro-wide bug, never happened to me on either of my computers.

---

### Post by RichardLinx on 2010-06-22
Sounds more annoying then funny...

---

### Post by Djalmahal on 2010-06-22
Well honestly, it's one of the most harmless bugs I encounter, not nearly as annoying as my computer switching from Advanced Desktop effects to no Desktop effects for no apparent reason

---

### Post by prshah on 2010-06-22
> **Djalmahal said:**
> So when I click on Places>Download my ubuntu 10.04 opens a folder on the Desktop with audio files in VLC, happens again and again,LOL

> **ZorgTheDestroyer said:**
> to 'Places - any folder' it opens in a videoplayer. 

This is a known bug. Open "Computer" from the Places location, (or just run nautilus from the Alt+F2 "command" box). Now, navigate to your home directory, then right click any directory within it, and choose "Open With"-"Open with other application"; in the box that pops up, choose "File Browser".

From now on, it will open correctly.

Here's another way you can try; System-Preferences-File Management. If you can't find that option, press Alt+F2, and run ```
nautilus-file-management-properties
```

Then click the Behaviour tab, and select the option "Always open in browser windows", then click Close.

Now perform the earlier method again, and see if it "sticks"

If that doesn't work as well, right click any directory in your home directory, then choose Properties-Open With-File Browser-Close. If the "File Browser" option is not there, click on Add and locate "File Browser". If you still cannot find the option, at the bottom of the "Add Application" window, click on "Use a custom command" and give the command as ```
nautilus
```.

> **Djalmahal said:**
> my computer switching from Advanced Desktop effects to no Desktop effects for no apparent reason

This happens with Compiz segfaults (crashes). Check your log files for more details. It is usually related to a (misbehaving) compiz addon.

---

