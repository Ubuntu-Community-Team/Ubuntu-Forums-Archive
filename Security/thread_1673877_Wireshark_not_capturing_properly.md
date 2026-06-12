---
title: "Wireshark not capturing properly"
date: 2011-01-23
forum: Security
---

### Post by mgoodwin6 on 2011-01-23
Was trying to use wireshark to pen test my network and I can't get it to work properly.  When capturing on my main wireless card wlan0 atheros ath9k the program freezes after a short while and I can't even access the web anymore.  Not to mention it stops capturing.  I have to disconnect and reconnect to get back on the web.  Not sure what is going on here.  I get the following output in terminal:

(wireshark:2240): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.26.0/gobject/gsignal.c:3081: signal name `depressed' is invalid for instance `0x2142cb68'

In addition I get a bunch of Malformed Packet errors also.

Here are the specs on my machine:

2007 Macbook 2ghz Intel C2D
1.5gb Ram
Ubuntu 10.10 Maverick
Airport extreme wireless card (Atheros chipset using ath9k drivers)
Wireshark v 1.2.11

Please help.  Not sure what I'm possibly doing wrong.  But then again I've been wrong before...:)

---

### Post by adrien214 on 2011-02-24
It's funny you know... I have an atheros wifi card and it wasn't working either... juts not packet would be seen... then it started to function out of the blue =) That's the thrill of magic !

---

