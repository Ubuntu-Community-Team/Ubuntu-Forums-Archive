---
title: "LTSP in wireless environment"
date: 2007-04-25
forum: Server Platforms
---

### Post by sgabor42 on 2007-04-25
Hi!

I would like to install LTSP on a Feisty server. But my client machines are wireless, so network boot is not possible. But my clients has hard disks, so I shoiuld able to boot locally and  setup wireless . But anyone has any idea how can I boot locally an LTSP client?

---

### Post by sgabor42 on 2007-04-27
No one has any idea?

---

### Post by saadakhtar on 2007-05-14
as you know that this has only been tested with wired connections since the system has option to boot using a legacy Ethernet driver but i would assume that this would only be possible if you could get your client pc's to boot and load wlan drivers and then boot off network using the wlan card.
Consider the issues in this:

this setup will need to use a static conf file. meaning that your default ssid will need to be the same. encryption might be an option (wep, wpa psk) but that would be more complicated. thin client uptime might be effected.

these are some of the issues but personally i would like to proceed with it too. if anyone out there has tried this than please let us know and probably help....

---

