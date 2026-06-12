---
title: "word wrap toggle for Gedit"
date: 2007-10-26
forum: Ubuntu Brainstorm
---

### Post by tempest on 2007-10-26
Not sure if this should go here or to the gnome folks. Can we get a word wrap toggle on the toolbar or one of the menus so that it is not necessary to open the preferences each time. I use Gedit for a lot of programming and am always flipping wordwrap on and off. :)

---

### Post by Twintop on 2007-10-26
/seconded

I know the Ubuntu Developers work closely with the Gnome Developers. I'd try to write up the blueprint for it and also submit it as an idea on Gnome's development board.

I don't see how this would be a very time consuming thing to add...I might just have to try writing a patch and submitting it to them, since I would use this too.

---

### Post by tempest on 2007-10-26
Thanks for the suggestion, I will do that. I would go ahead and try to do this myself, but do not know how yet. I have been using Ubuntu for a few years, but just getting started with development on Linux. I figured it would be a worth while suggestion.

---

### Post by 23meg on 2007-10-26
You may want to implement this in the form of a plugin.

---

### Post by peterquistgard on 2008-07-03
Here is what I use to turn on / off word wrap. This code assumes that you don't use the "split words" option (because I don't). I'm sure you can figure out how to include that if you need to.

Create a new External Tool (Tools > External Tools > New) with the commands given below, and add a shortcut key.

```
x=`gconftool-2 -g /apps/gedit-2/preferences/editor/wrap_mode/wrap_mode`

[ $x = "GTK_WRAP_NONE" ] && gconftool-2 -s -t string /apps/gedit-2/preferences/editor/wrap_mode/wrap_mode GTK_WRAP_WORD || gconftool-2 -s -t string /apps/gedit-2/preferences/editor/wrap_mode/wrap_mode GTK_WRAP_NONE
```

---

### Post by Javier Paniagua on 2008-08-27
Thanks guys!

23meg and peterquistgard pointed me to the obvious :)

This is a tiny plugin to have a 'View/Toggle text wrap' menu entry.

You can use this and 'Edit Shortcuts' plugin to, well, set a shortcut to toggle text wrap on and off.

---

### Post by David Tomic on 2008-08-27
> **Javier Paniagua said:**
> 
You can use this and 'Edit Shortcuts' plugin to, well, set a shortcut to toggle text wrap on and off.

Thanks Javier ... works a treat! :)

---

### Post by AlesZib on 2008-12-13
> **peterquistgard said:**
> Here is what I use to turn on / off word wrap. This code assumes that you don't use the "split words" option (because I don't). I'm sure you can figure out how to include that if you need to.

Create a new External Tool (Tools > External Tools > New) with the commands given below, and add a shortcut key.

```
x=`gconftool-2 -g /apps/gedit-2/preferences/editor/wrap_mode/wrap_mode`

[ $x = "GTK_WRAP_NONE" ] && gconftool-2 -s -t string /apps/gedit-2/preferences/editor/wrap_mode/wrap_mode GTK_WRAP_WORD || gconftool-2 -s -t string /apps/gedit-2/preferences/editor/wrap_mode/wrap_mode GTK_WRAP_NONE
```

Thanks! I got it to work.

---

### Post by kostmo on 2008-12-29
> **23meg said:**
> You may want to implement this in the form of a plugin.

I have created a plugin that allows easy word-wrap toggling with separate settings for each open tab.  It is posted here:
[http://launchpadlibrarian.net/20557857/per-buffer-text-wrap.tar.bz2](http://launchpadlibrarian.net/20557857/per-buffer-text-wrap.tar.bz2)

---

### Post by manuelb on 2009-04-16
> **kostmo said:**
> I have created a plugin that allows easy word-wrap toggling with separate settings for each open tab.  It is posted here:
[http://launchpadlibrarian.net/20557857/per-buffer-text-wrap.tar.bz2](http://launchpadlibrarian.net/20557857/per-buffer-text-wrap.tar.bz2)

Nice one, with CTRL+R as a shortcut too, thank you!

---

