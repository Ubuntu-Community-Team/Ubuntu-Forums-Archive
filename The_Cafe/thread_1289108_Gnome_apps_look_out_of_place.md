---
title: "Gnome apps look out of place"
date: 2009-10-12
forum: The Cafe
---

### Post by Sashin on 2009-10-12
After installing kde-minimal, I've found that gnome apps look really really bad. Does anyone know how to fix this and make them look more integrated?

---

### Post by Screwdriver0815 on 2009-10-12
simply install the package "gtk-qt-engine" and then go to the systemsettings, category "appearance" and choose "GTK-styles and Fonts" in the categories on the left-hand side (where you also can choose icons, windows, startup-screen). Then activate the option "use my KDE style in GTK applications". Restart KDE, done.

---

### Post by Xbehave on 2009-10-12
retheme the gtk theme to look similar to your qt theme (or pick one that works well in both).

Otherwise [this]("http://code.google.com/p/gtk-qt-engine/") is what you are looking for, i think its in ubuntu repos (i know it was included in kubuntu last time i used it (back on kde3)). You may also need a qt3->qt4 converter if the engine hasn't been updated, but qt3 apps such as konversation still look ok in qt4 so you may not.

---

### Post by Jimleko211 on 2009-10-12
The qt-gtk-engine has horrible rendering problems.  Install the qtcurve theme.  It doesn't look nearly as good as Oxygen, but it isn't horrible, and looks like it belongs in your desktop.

---

### Post by Screwdriver0815 on 2009-10-12
> **Jimleko211 said:**
> The qt-gtk-engine has horrible rendering problems.  Install the qtcurve theme.  It doesn't look nearly as good as Oxygen, but it isn't horrible, and looks like it belongs in your desktop.
how can I see the rendering problems?

[[IMG]http://img96.imageshack.us/img96/7964/screenjauntygimpopendia.png[/IMG]](http://img96.imageshack.us/i/screenjauntygimpopendia.png/)

can you explain it with this pic as example?

Thanks!

---

### Post by Jimleko211 on 2009-10-12
In that pick there aren't any.  I have experienced problems with Firefox and Open Office, however.  Try those.

---

### Post by Screwdriver0815 on 2009-10-12
> **Jimleko211 said:**
> In that pick there aren't any.  I have experienced problems with Firefox and Open Office, however.  Try those.
okay...

as I don't have Firefox, here just a pic of openoffice

[[IMG]http://img198.imageshack.us/img198/927/oo1v.png[/IMG]](http://img198.imageshack.us/i/oo1v.png/)

are there any rendering issues?

---

### Post by Sashin on 2009-10-12
Cool, this works well thanks.

---

### Post by Sashin on 2009-10-12
Actually no its not working, I get that thing in the appearance menu but it doesn't affect anything. I installed kcm-gtk but nothing happens when I change the gtk theme. Is there something else I'm missing?

---

### Post by Screwdriver0815 on 2009-10-12
> **Sashin said:**
> Actually no its not working, I get that thing in the appearance menu but it doesn't affect anything. I installed kcm-gtk but nothing happens when I change the gtk theme. Is there something else I'm missing?
you have to click "apply" after checking the thing in the appearance menu and after that a restart of the system.

---

### Post by Sashin on 2009-10-12
Nope didn't work.

---

### Post by lovinglinux on 2009-10-12
Are you logged into KDE or Gnome?

---

### Post by Sashin on 2009-10-12
Kde

---

### Post by Screwdriver0815 on 2009-10-12
> **Sashin said:**
> Nope didn't work.
hmm...

can you check in your homefolder, if there is a hidden file ".gtkrc-2.0-kde4"? If yes, rename it to .gtkrc-2.0 and try again (set the appearance settings and restart).

---

### Post by Sashin on 2009-10-12
That got the fonts working but not the actual theme, not even the fonts work in synaptic though.

---

### Post by Screwdriver0815 on 2009-10-12
> **Sashin said:**
> That got the fonts working but not the actual theme, not even the fonts work in synaptic though.
then sorry, I have no further idea, except follwing the advice of installing this qtcurve theme

---

### Post by lovinglinux on 2009-10-15
I have figured it out.

Go to System Settings and configure the GTK+ engine to QtCurve and apply.

Then rename the file **.gtkrc-2.0-kde4** in your home directory to **.gtkrc-2.0** then run the command below to copy the file to the root user:

```
sudo cp ~/.gtkrc-2.0 /root/.gtkrc-2.0
```

Reboot.

---

