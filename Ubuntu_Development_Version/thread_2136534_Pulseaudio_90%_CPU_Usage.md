---
title: "Pulseaudio: 90% CPU Usage?"
date: 2013-04-17
forum: Ubuntu Development Version
---

### Post by jlacroix on 2013-04-17
I just started testing Raring today, and I noticed that Pulse Audio is always using 90% of my CPU. At no point does it drop below 90%. I have a T430 laptop. Is anyone else experiencing this?

---

### Post by P-I H on 2013-04-18
Yes, 
Updated the system this morning. After reboot Pulseaudio takes 100% of one cpu core. However this is an Ubuntu installation.

---

### Post by Abandon on 2013-04-18
Same problem here on Ubuntu 13.04. A killall does not help because it keeps coming back. My first core is 100% and temperatures are rising.

---

### Post by jalmargyyk on 2013-04-18
Same issue here. Seems that pulseaudio has received a bugfix update a few hours ago.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1167192]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1167192")

---

### Post by Abandon on 2013-04-18
Yes, In the meanwhile I have removed Pulsaudio. You also loose ubuntu-desktop, indicator-sound, libcanberra-pulse, pulseaudio-module-bluetooth, pulseaudio-module-gconf and pulseaudio-module-x11. I use (terminal) alsa-mixer now for sound adjustments and try installing above packages later on the day.

---

### Post by zika on 2013-04-18
> **Abandon said:**
> Yes, In the meanwhile I have removed Pulsaudio. You also loose ubuntu-desktop, indicator-sound, libcanberra-pulse, pulseaudio-module-bluetooth, pulseaudio-module-gconf and pulseaudio-module-x11. I use (terminal) alsa-mixer now for sound adjustments and try installing above packages later on the day.Wasn't it easier just to stop pulseaudio...?

---

### Post by Abandon on 2013-04-18
I tried killall and that didn't work. I didn't try the stop but maybe I should have ;-)

---

### Post by zika on 2013-04-18
> **Abandon said:**
> I tried killall and that didn't work. I didn't try the stop but maybe I should have ;-)
It respawns itself if You do not tell him not to...
```
:~$ cat .pulse/client.conf
autospawn = no
```
```
pulseaudio --kill
```

---

### Post by baizon on 2013-04-18
Got the same issue with xubuntu 13.04, since the last update.
Screenshot: [http://i.imgur.com/kO0x81b.png]("http://i.imgur.com/kO0x81b.png")

Edit:
Dev, already solving the issue: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1170313]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1170313")

---

### Post by JMB74 on 2013-04-18
Fix uploaded to build.

[https://launchpad.net/ubuntu/raring/+source/pulseaudio/1:3.0-0ubuntu6](https://launchpad.net/ubuntu/raring/+source/pulseaudio/1:3.0-0ubuntu6)

---

### Post by zika on 2013-04-18
Seems fixed. Thank You for HU...

---

### Post by Abandon on 2013-04-18
Yes, updates received, deleted the .pulse/client.conf and voila ;-) Thx for your input about stopping pulseaudio. Always happy to learn something new.

---

### Post by jlacroix on 2013-04-18
Appears to be working here as well after I updated.

---

