---
title: "Can anyone tell me what this means?"
date: 2020-11-15
forum: Server Platforms
---

### Post by adam94 on 2020-11-15
[ATTACH=CONFIG]287366[/ATTACH]

Seems related to Nzbget but I've no idea what's causing it. Completely hangs the system and I have to reboot. It's ubuntu server 20.04.1

---

### Post by webaake on 2020-11-15
Seems to be the kernel. Try an older kernel.

---

### Post by Frogs Hair on 2020-11-15
Moved to ***Server Platforms***.

---

### Post by ajgreeny on 2020-11-15
Which version of VirtualBox are you using as host?
Have you tried a different kernel, eg, one of the earlier ones that is probably already on the system, such as 5.4.0-51?

---

### Post by adam94 on 2020-11-16
Currently have virtual box 5.2.44. Is it worth upgrading instead of using an earlier kernel looks like [COLOR=#000000][FONT=Menlo]5.9.8-* is the newest one[/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-11-16
Current version is 6.1.16.
6.0.x or 5.2.x are EoL since July: [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

