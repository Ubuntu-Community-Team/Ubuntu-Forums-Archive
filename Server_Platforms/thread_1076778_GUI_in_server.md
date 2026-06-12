---
title: "GUI in server"
date: 2009-02-21
forum: Server Platforms
---

### Post by Don1500 on 2009-02-21
OK, I started up Xfce on my server, and as I had read and should have noted, it is not that helpful in server. Saying that, it has caused me nothing but trouble since I put it in. How do I get it out?

---

### Post by R.Bucky on 2009-02-21
I have not done that before... Anyways, it should be removed with ```
apt-get remove xfce
```

---

### Post by Perryg on 2009-02-21
An alternative would be to put the gnome desktop in.

sudo apt-get install gnome-desktop

Then there is always webmin for the faint at heart.

---

### Post by Don1500 on 2009-02-21
> **R.Bucky said:**
> I have not done that before... Anyways, it should be removed with ```
apt-get remove xfce
```

Tried that, 

```
Reading Package Lists...Done
Building dependency tree
reading state information...Done
E: Couldn't find package Xfce 
don@maggie:~$
```

That's why I opened this thread, the obvious didn't work.

---

### Post by Perryg on 2009-02-21
> **Don1500 said:**
> Tried that, 

```
Reading Package Lists...Done
Building dependency tree
reading state information...Done
E: Couldn't find package Xfce 
don@maggie:~$
```

That's why I opened this thread, the obvious didn't work.

Try this:

drop to terminal totally outside of the gui.

sudo apt-get purge xfce4   

Purge will get rid of the program and all of its whisker files.

Anyway if this does not work you need to see what version number it is.  just xfce will not do it because that is not the full name.

---

### Post by Don1500 on 2009-02-21
OK, the full name is xfce4, now how do I get out of the GUI to run in text mode again?
Thanks for the help so far. We're getting there.

---

### Post by Perryg on 2009-02-21
> **Don1500 said:**
> OK, the full name is xfce4, now how do I get out of the GUI to run in text mode again?
Thanks for the help so far. We're getting there.

Under system - administration - services.

Take the tick off of start graphical login manager or something like that. 

You may need to reboot but this will put you in a shell without the GDM.  Do the code and you will not have a GUI at all.  If you decide you would like one I strongly suggest the gnome desktop.  Works without problems.

---

### Post by Don1500 on 2009-02-21
> **Perryg said:**
> Under system - administration - services.

Take the tick off of start graphical login manager or something like that. 

You may need to reboot but this will put you in a shell without the GDM.  Do the code and you will not have a GUI at all.  If you decide you would like one I strongly suggest the gnome desktop.  Works without problems.

Fired up without the GUI!! Thanks!

---

### Post by Perryg on 2009-02-21
> **Don1500 said:**
> Fired up without the GUI!! Thanks!

No problem.  Enjoy and like I said if you feel you need or would like the desktop, go with the gnome desktop.  It may not be as pretty and fancy but it does not cause the problems the others do.

---

