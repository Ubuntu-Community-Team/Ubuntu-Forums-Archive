---
title: "set wireless to off at startup"
date: 2009-08-31
forum: System76 Support
---

### Post by mhedges48 on 2009-08-31
90% of the time I have my ethernet cable plugged in, so do not wish wireless to automatically start. How can I set it to where it is turned off as default at boot? And then I can just turn it on via network manager when I need it.

many thanks

---

### Post by Revolutionary101 on 2009-08-31
Just go over the the Networking Icon on the top panel (it should be right next to the time). Then right click it and deselect Enable Wireless. That should do it.

Hope it helps.

---

### Post by mhedges48 on 2009-08-31
Yes, I have been doing that. But then when the computer restarts wireless is turned back on again. On my previous computer I was able to fix this but can figure out how on Serval/Jaunty.

thanks

---

### Post by itendo on 2009-08-31
would going through the BIOS work for you? my dell 700m lappy has a toggle to boot with the wireless on/off

---

### Post by thomasaaron on 2009-08-31
Going through the BIOS is not an option on the Serval. You would think there would be a setting in gconf-editor for this, but I'm not finding it.

The easiest way is to run this command...

sudo modprobe -r iwlagn

...which removes the module that runs the wireless card.

You could also create some icons on your desktop to toggle it off and on via...

sudo modprobe -r iwlagn

...and...

sudo modprobe iwlagn

OR you could blacklist the module in /etc/modbrobe.d/blacklist.conf
by adding this line...

blacklist iwlagn

---

### Post by mhedges48 on 2009-08-31
thanks! works like a charm; i blacklisted it, and when I want to turn it back on, do the modprobe command

---

### Post by thomasaaron on 2009-08-31
Schweet. Let me know if I can be of further assistance.

---

