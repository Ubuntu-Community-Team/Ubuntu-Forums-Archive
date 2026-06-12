---
title: "Run script on USB Media Insertion"
date: 2012-04-07
forum: Server Platforms
---

### Post by CyberAxe on 2012-04-07
I'd like to setup the server (Ubuntu Server 11.04) so if you plug in a Compact Flash card (well between 1 and 4 CF cards at a time)

Whats the best way to get the event of the media being inserted into the reader?

What my ultimate goal is to run a script, mount the card, move all the photos into a date sorted folder on a samba share, then do the same for the other cards inserted via other readers, then once its moved all the files from them all it makes several system beeps to indicate completion and possibly send an email or send a message via XMPP.

Any suggestions would be appreciated, thanks.

---

### Post by Cheesemill on 2012-04-07
You need to write a custom udev rule.

[http://www.banquise.org/hardware/how-to-automatically-run-a-script-after-inserting-a-usb-device-on-ubuntu/](http://www.banquise.org/hardware/how-to-automatically-run-a-script-after-inserting-a-usb-device-on-ubuntu/)

---

