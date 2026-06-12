---
title: "Soldier of Fortune Platinum Edition no sound in wine"
date: 2010-10-17
forum: Wine
---

### Post by jcer93705 on 2010-10-17
Hi guys I have soldier of fortune platinum running good under wine with latiest wine app but theres no sound. Can someone help me on this one? If i run another application under wine i have sound. Is there a solution to get the sound to work?

---

### Post by akoskm on 2010-10-17
> **jcer93705 said:**
> Hi guys I have soldier of fortune platinum running good under wine with latiest wine app but theres no sound. Can someone help me on this one? If i run another application under wine i have sound. Is there a solution to get the sound to work?

Download the **aoss** wrapper script and try to start the game like:
```

aoss wine <executable>

```
, replace the <executable> with the game's executable.
Hope this help.

---

### Post by jcer93705 on 2010-10-17
> **akoskm said:**
> Download the **aoss** wrapper script and try to start the game like:
```

aoss wine <executable>

```
, replace the <executable> with the game's executable.
Hope this help.


Where would I get that scrip and how to install it? Thanks

---

### Post by akoskm on 2010-10-17
> **jcer93705 said:**
> Where would I get that scrip and how to install it? Thanks

Open the terminal and type:
```

sudo aptitude install alsa-oss

```.

---

