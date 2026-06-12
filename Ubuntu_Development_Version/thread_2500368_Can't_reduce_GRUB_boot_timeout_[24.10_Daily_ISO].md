---
title: "Can't reduce GRUB boot timeout [24.10 Daily ISO]"
date: 2024-08-31
forum: Ubuntu Development Version
---

### Post by enricobe on 2024-08-31
Hello,
the GRUB timeout is set to 30 seconds. I want to reduce it to 2 seconds because I always boot the first entry.

I opened the grub file with nano
```
[FONT=monospace][COLOR=#000000]
sudo nano /etc/default/grub[/COLOR]
[/FONT]
```

Changed the Timeout value (which was strangely set to 0 by default) to 3.

```
[FONT=monospace][COLOR=#000000]GRUB_DEFAULT=0 [/COLOR]
GRUB_TIMEOUT_STYLE=hidden 
GRUB_TIMEOUT=3 
GRUB_DISTRIBUTOR='Kubuntu' 
GRUB_CMDLINE_LINUX_DEFAULT='quiet splash' 
GRUB_CMDLINE_LINUX=""
[/FONT]
```

then run 
```
[FONT=monospace][COLOR=#000000]
sudo update-grub[/COLOR]
[/FONT]
```

but nothing changed. The grub timeout is still 30 seconds.. I tried different values, but nothing seems to work.
Am I editing the correct file? It may be a bug or some configuration issues?

As written in the thread title, I'm running Kubuntu 24.10 installed from the Daily ISO so it may be expected.

---

### Post by currentshaft on 2024-08-31
It's "GRUB_RECORDFAIL_TIMEOUT" now AFAIK.

---

### Post by enricobe on 2024-09-01
> **currentshaft said:**
> It's "GRUB_RECORDFAIL_TIMEOUT" now AFAIK.

Thank you very much! Adding GRUB_RECORDFAIL_TIMEOUT=2 to the /etc/default/grub worked perfectly

---

