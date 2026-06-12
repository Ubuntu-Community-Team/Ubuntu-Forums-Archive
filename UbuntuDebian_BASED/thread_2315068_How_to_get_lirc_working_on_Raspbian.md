---
title: "How to get lirc working on Raspbian"
date: 2016-02-25
forum: Ubuntu/Debian BASED
---

### Post by quadrplax on 2016-02-25
I have a Raspberry Pi 2 and I recently wired up an IR receiver. It works fine with mode2 and I was able to create a remote with irrecord. However, I'm having a hard time getting that remote to actually do anything. I can't even get irw to work. I've tried various things like running lircd --nodaemon and I get the following error when I try to use irw:
```
lircd-0.9.0-pre1[1225]: lircd(default) ready, using /var/run/lirc/lircd
lircd-0.9.0-pre1[1225]: accepted new client on /var/run/lirc/lircd
lircd-0.9.0-pre1[1225]: could not get file information for /dev/lirc
lircd-0.9.0-pre1[1225]: default_init(): No such file or directory
lircd-0.9.0-pre1[1225]: Failed to initialize hardware

```
This makes it look like it's trying to use "/dev/lirc". There is no /dev/lirc, only /dev/lirc0, which hardware.conf is set to. Any clue why irw won't work yet irrecord will?

---

### Post by howefield on 2016-02-26
Thread moved to a support forum.. "*Ubuntu/Debian BASED*"

---

### Post by quadrplax on 2016-02-26
Ok, found a stupid fix that works, created a symbolic link:
[COLOR=#252525][FONT=monospace]```

ln -s /dev/lirc0 /dev/lirc

```[/FONT][/COLOR]

---

