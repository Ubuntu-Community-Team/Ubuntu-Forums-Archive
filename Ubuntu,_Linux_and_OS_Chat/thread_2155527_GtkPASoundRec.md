---
title: "GtkPASoundRec"
date: 2013-06-18
forum: Ubuntu, Linux and OS Chat
---

### Post by Nobbler on 2013-06-18
Here is a simple sound recorder program I wrote using PulseAudio and a Gtk front end!

[IMG]http://i41.tinypic.com/2ps16yr.jpg[/IMG]

I was looking for ways to record sound card output and came across an easy command line interface on the PulseAudio wiki, however I found it too cumbersome to switch back and forth between the terminal. I found it was trivial to add support for microphones, and with the power of PulseAudio you can also record individual applications

Here is a screenshot:

[IMG]http://i42.tinypic.com/2qjzoxy.jpg[/IMG]


Right now the code is in a "minimally functional state", and there is also no packaging, but if you would like to try compiling it you can find the code here: [https://github.com/GtkPASoundRec/gtkpasoundrec](https://github.com/GtkPASoundRec/gtkpasoundrec)

You will need at least the following: g++, pulseaudio, Gtk+-3.0, gnome/dbus/dconf (for keybindings support)

I'm running 12.10, and it compiles for me, but you may need to install devlopment packages

I have tons of ideas for how it can be extended, and if you have feedback or suggestions, send me a message, or feel free to fork the code

Cheers

Examining the dbus interface in d-feet:

[IMG]http://i40.tinypic.com/35ksugo.png[/IMG]

---

### Post by Toz on 2013-06-18
Not a support question. Moved to Ubuntu, Linux and OS Chat.

---

