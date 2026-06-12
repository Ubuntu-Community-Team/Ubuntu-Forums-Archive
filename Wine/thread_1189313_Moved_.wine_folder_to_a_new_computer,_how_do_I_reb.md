---
title: "Moved .wine folder to a new computer, how do I rebuild Applications-&gt;Wine-&gt;Programs"
date: 2009-06-16
forum: Wine
---

### Post by James Paige on 2009-06-16
I recently moved to a new computer. I copied my old .wine folder from my home dir on the old computer to my home dir on the new computer. Wine works. My virtual C drive is the same as it used to be, and I can run all my wine programs. However, when I go to the Applications menu, and then to the Wine submenu, the Programs submenu does not contain anything except Accessories->Notepad.

How do I re-populate Applications->Wine->Programs ?

I tried re-installing one of my programs, and it did not appear.

If I go to Applications->Wine->Uninstall Wine Software, I can still see the names of all the programs I have installed, so I know my wine registry still knows about all of them.

Does anybody have any ideas?

---

### Post by jhoeijao on 2009-06-16
> **James Paige said:**
> I recently moved to a new computer. I copied my old .wine folder from my home dir on the old computer to my home dir on the new computer. Wine works. My virtual C drive is the same as it used to be, and I can run all my wine programs. However, when I go to the Applications menu, and then to the Wine submenu, the Programs submenu does not contain anything except Accessories->Notepad.

How do I re-populate Applications->Wine->Programs ?

I tried re-installing one of my programs, and it did not appear.

If I go to Applications->Wine->Uninstall Wine Software, I can still see the names of all the programs I have installed, so I know my wine registry still knows about all of them.

Does anybody have any ideas?

Click System>Preferences>Main Menu. In the Main Menu window look for Wine and expand it, then expand Programs then check your desired programs.

---

### Post by James Paige on 2009-06-16
> **jhoeijao said:**
> Click System>Preferences>Main Menu. In the Main Menu window look for Wine and expand it, then expand Programs then check your desired programs.

I tried System>Preferences>Main Menu, but there is nothing in there under Wine except for accessores->notepad.

I did not copy over my entire home folder from the old computer to this new one, I only copied over things I specifically expected to need on the new computer.

I read some other threads that said I needed the files in .local/share/desktop-directories so I copied those over too, but that made no difference at all.

---

### Post by dacha on 2009-06-17
Copy some/all of the contents of ~/.config, ~/.local/share/applications and ~/.local/share/icons too.

You might need to log out and log back in before the changes take effect.

---

