---
title: "Wine menu gone"
date: 2009-05-12
forum: Wine
---

### Post by Ravernomina on 2009-05-12
hello.. I installed wine 1.1.21 today so i can play my favourite game age of mythology. Now when i got to Applications their is no wine menu. When i go into System>preferences>main menu, Their is no wine option their... can any 1 please help me get the wine menu... please TYVM!!!
    Ravernomina

---

### Post by DeadlyAura on 2009-05-12
Right click on the Ubuntu icon in the top left next to your applications menu.

Then click "Edit Menus"

The menu editor will pop up and you will be able to enable Wine so long as it is installed properly.

---

### Post by Ravernomina on 2009-05-12
yea i tried that its not their :l

---

### Post by DeadlyAura on 2009-05-12
Actually, my apologies, I didn't see that you had already tried that. My guess would be to make sure that Wine is installed and functioning correctly.

Open terminal and type:
```

winecfg

```

and see if Wine Config will open.

---

### Post by rcayea on 2009-05-12
> **DeadlyAura said:**
> Actually, my apologies, I didn't see that you had already tried that. My guess would be to make sure that Wine is installed and functioning correctly.

Open terminal and type:
```

winecfg

```

and see if Wine Config will open.



Try this: 

If you deleted wine from your Applications menu then look in home folder -> .config/menus/applications.menu (.config is a hidden folder, when in home folder go Ctrl+h if not visible

You should see an entry like this (i added the red
Code:

</Menu>
<Menu>
<Name>wine-wine</Name>
[COLOR="Red"]<Deleted/>[/COLOR]
</Menu>
</Menu>

Remove what's in red, and save

---

### Post by Ravernomina on 2009-05-12
hey that worked TYVM :)

---

### Post by rcayea on 2009-05-12
No problem! Glad it worked.

---

### Post by 73ckn797 on 2009-08-19
Found this thread and it fixed my menu problem also.

THANKS.

---

