---
title: "Skype without pulseaudio - Ubuntu 10.04"
date: 2011-09-30
forum: Tutorials
---

### Post by benneton on 2011-09-30
Hi,

Pulseaudio and Skype - NOT GOOOOD! (well, not good for me)

If you don't want to use Skype with pulseaudio you can follow this step by step tutorial:

1. edit /etc/pulse/client.conf (change  "autospawn = yes" TO  "autospawn = no")
2. killall -KILL pulseaudio
3. open skype (no pulseaudio in Options > Sound devices - USE DEVICE WHICH SUITS YOU BETTER)
4. Apply and quit Skype
5. create /usr/bin/skype_start.sh

```

#!/bin/bash
#/usr/bin/skype_start.sh
pulseaudio --kill & LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype &
sleep 10  
pulseaudio --start

```6. chmod +x /usr/bin/skype_start.sh
7. skype_start.sh AND VOILA
8. create launcher on panel and add an skype icon!!! :D

This is just temporary solution, but it works for me!

Hope it helps!

---

