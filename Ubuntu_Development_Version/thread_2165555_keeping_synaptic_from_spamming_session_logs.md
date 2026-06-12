---
title: "keeping synaptic from spamming session logs"
date: 2013-08-05
forum: Ubuntu Development Version
---

### Post by mc4man on 2013-08-05
If you happen to make use of session logs, (.xsession-errors, .cache/upstart/gnome-session.log, ect) & use synaptic then you'd have noticed every time synaptic starts it writes 100 or so lines concerning 'Gtk-WARNING **: GtkNotebook 0x10eb4b0 is mapped but visible child GtkLabel 0x10ff1b0 is not mapped' or similar.

To stop this - open synaptic > settings > preferences > enable the option under Appearance (show package properties in main window), click 'apply'

---

