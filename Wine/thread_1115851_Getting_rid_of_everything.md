---
title: "Getting rid of everything"
date: 2009-04-04
forum: Wine
---

### Post by kernel89 on 2009-04-04
I wanted to remove the Wine completely, so I removed it from Add/Remove then I deleted the wine directory by force and made sure anything that had *wine in Synaptic was unchecked.

However, when I go to application/*wine is still there, along with the apps I installed. I don't know if these are simply the shortcuts that I can later easily remove, or if they are actually still there taking up space in my Hard Drive.

---

### Post by Bucky Ball on 2009-04-04
Try 

```
 sudo apt-get autoremove
```

in a terminal and see if that kills anything else. (Don't worry, will only get rid of orphaned things and redundant bits.)

---

### Post by hikaricore on 2009-04-04
> **Bucky Ball said:**
> Try 

```
 sudo apt-get autoremove
```

in a terminal and see if that kills anything else. (Don't worry, will only get rid of orphaned things and redundant bits.)

This has nothing to do with what the OP is asking...

> **kernel89 said:**
> I wanted to remove the Wine completely, so I removed it from Add/Remove then I deleted the wine directory by force and made sure anything that had *wine in Synaptic was unchecked.

However, when I go to application/*wine is still there, along with the apps I installed. I don't know if these are simply the shortcuts that I can later easily remove, or if they are actually still there taking up space in my Hard Drive.

These are just "shortcuts" that are left over.  The whole WINE/application menu thing isn't 100% reliable in the first place.
If you don't wish to see them just edit your applications menu and remove/disable them.  However if you didn't completely remove WINE,
and still have a .wine folder in your home directory, items in there could actually be taking up space.

The proper way to completely remove WINE in the future is:

> sudo apt-get remove --purge wine

---

### Post by kernel89 on 2009-04-04
I did * sudo apt-get remove --purge wine just to make sure I removed everything.

As for the shortcuts, how do I edit the application menu?

---

### Post by hikaricore on 2009-04-04
Right click on the applications menu and select edit.

---

### Post by Bucky Ball on 2009-04-04
> **hikaricore said:**
>   However if you didn't completely remove WINE,
and still have a .wine folder in your home directory, items in there could actually be taking up space.

The proper way to completely remove WINE in the future is:

[code]sudo apt-get remove --purge wine

If the .wine folder remains, will this last command remove it and anything else that remains of Wine?

---

