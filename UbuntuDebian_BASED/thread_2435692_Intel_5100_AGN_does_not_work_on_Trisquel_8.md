---
title: "Intel 5100 AGN does not work on Trisquel 8"
date: 2020-01-24
forum: Ubuntu/Debian BASED
---

### Post by autumncheney on 2020-01-24
[COLOR=#0C0D0E][FONT=&amp]I recently installed Trisquel 8 on a Thinkpad X200T with an Intel 5100 AGN card, and the WiFi did not work after my initial installation. I searched across various other forums for instructions to enable Trisquel to use the card, and I attempted to follow their instructions, but to no avail.
[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=&amp]My networking hardware switch is set to on, I have the necessary firmware in the /lib/firmware directory, and I did load the iwlwifi module using modprobe, but the WiFi still does not work, and ifconfig and rfkill do not even show a wireless controller (rather, it only shows the ethernet and loopback systems). Also, according to lshw, the network card is unclaimed.

I am aware that the firmware-iwlwifi is non-free, but I can't use a free WiFi device right now. I know that using it contradicts Trisquel's philosophy, but I know that I can still install it.
[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=&amp]Would somebody please help me? Thank you![/FONT][/COLOR]

---

### Post by howefield on 2020-01-24
Moved to the "*Ubuntu/Debian BASED*" forum.

---

