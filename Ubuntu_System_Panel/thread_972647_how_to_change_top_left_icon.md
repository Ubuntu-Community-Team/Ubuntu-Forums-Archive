---
title: "how to change top left icon?"
date: 2008-11-06
forum: Ubuntu System Panel
---

### Post by bartre on 2008-11-06
hi I was just wondering if there was any way to change the top left icon in ubuntu.
and if so, how would i change it?

---

### Post by Malac on 2008-11-07
If you mean the usp button icon then right-click and choose Preferences.
Under the Main tab are the options for the main menu.
 
Hope this helps.

---

### Post by OrangeCrate on 2008-11-07
> **bartre said:**
> hi I was just wondering if there was any way to change the top left icon in ubuntu.
and if so, how would i change it?

Put your new icon in your home folder, and label it "start-here.png"

Then, open your terminal, and type the following command:

```
gconf-editor
```

When you execute this command, a "Configuration Editor" window will open. You will need to go down the list on the left to get to "apps". Then...

apps > panel > objects > object_0 (or it may be another number - check all of them to find the right one for Main Menu.)

Second, in the right pane, check the box for "Use Custom Icon". Then go up, and right click:

Custom Icon > Edit Key

In the value box type:

/home/USERNAME/start-here.png

Once you have entered this into the box, click OK. If you followed all steps correctly, then you should see your icon on your Main Menu.

---

