---
title: "New Glib WARN, Gtk-Message, Gtk-Warning messages?"
date: 2011-11-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-11-08
When running "unity --replace&" and keeping the console running, I have noticed a couple of new messages have become very constant here. They show repeatedly for mostly any launched GUI app. I have verified that, sometimes, when the Interface seems to stutter a little in some GUI apps, you can see hundreds of these messages are passing by in the console.

WARN  2011-11-08 09:57:07 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
Gtk-Message: Failed to load module "canberra-gtk-module"
(npviewer.bin:31026): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64
(npviewer.bin:31026): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

These 4 repeat over and over. In first searches for bug reports I couldn't find all these messages (generally only the first) and has an answer. 

Anyone else seeing this?

Regards,
Effenberg

---

### Post by effenberg0x0 on 2011-11-08
Some advance:

Changed Window Theme to Ambiance inside Gnome-Tweak-Tool (Don't know why it was set to blank, although the settings panel was showing Ambiance).
Purged current PP Firefox and installed Firefox Aurora 9.0a2
Reinstalled Flash 64 .so from Adobe
Reinstalled libcanberra-gtk3-dev libcanberra-gtk-dev

Now I only get the first one repeating over and over:
WARN  2011-11-08 10:53:08 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

---

