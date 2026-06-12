---
title: "Wine + Jack = crash"
date: 2008-12-11
forum: Wine
---

### Post by psychok9 on 2008-12-11
I run Ubuntu 8.10 amd64 updated.
And i've installed Jackd for record with recordmydesktop World of Warcraft videos... and Wine crash if i select Jack audio driver. :confused:
Tips?

Thank you!

```
Inserted commands:
sudo ln -s /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so
A script with:
#load pulseaudio jack modules
#!/bin/bash

pactl load-module module-jack-sink
pactl load-module module-jack-source

For work jack togeteher pulse audio...

```

---

