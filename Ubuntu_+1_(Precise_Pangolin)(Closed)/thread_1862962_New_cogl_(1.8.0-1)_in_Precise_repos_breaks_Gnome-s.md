---
title: "New cogl (1.8.0-1) in Precise repos breaks Gnome-shell"
date: 2011-10-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-10-17
The newest update cogl (1.8.0-1) in Precise repos breaks Gnome-shell.
It will lead into a desktop with no panels.
I think clutter and/or mutter dies.

So, like usually, downgrading to previous version (1.8.0-1~svn1) solves this issue.
Or even better, do not upgrade yet if you are using Gnome-shell.

I have Gnome-shell from Ricotz Testing PPA (Precise) and it died too.

---

### Post by Quackers on 2011-10-17
As ever, thanks for the heads-up :-)

---

### Post by ronacc on 2011-10-17
too late I had already pulled the trigger and shot a hole in my foot before I read this :(

---

### Post by paul_in_london on 2011-10-17
> **ronacc said:**
> too late I had already pulled the trigger and shot a hole in my foot before I read this :(

+1. This was on the VM I use at work, so not a huge deal and I'll back up the cogl-related packages when I get home tonight before I upgrade. Thanks from me too for the heads-up Harry.

---

### Post by ricotz on 2011-10-17
> **Harry33 said:**
> The newest update cogl (1.8.0-1) in Precise repos breaks Gnome-shell.
It will lead into a desktop with no panels.
I think clutter and/or mutter dies.

So, like usually, downgrading to previous version (1.8.0-1~svn1) solves this issue.
Or even better, do not upgrade yet if you are using Gnome-shell.

I have Gnome-shell from Ricotz Testing PPA (Precise) and it died too.

You are probably just missing these packages which arent pulled in automatically yet:

gir1.2-coglpango-1.0, libcogl-pango0

---

### Post by ronacc on 2011-10-17
thanks ricotz that fixed it , but warning to others when I tried to install both at once from synaptic , gir1.2-coglpango-1.0 threw a conflict with libcogl-pango0 so Installed libcogl-pango0 first then gir1.2-coglpango-1.0 . that went with no conflicts . looking at the dependencies for gir1.2-coglpango-1.0 it both depends and conflicts with libcogl-pango0 .

---

### Post by Harry33 on 2011-10-17
> **ricotz said:**
> You are probably just missing these packages which arent pulled in automatically yet:

gir1.2-coglpango-1.0, libcogl-pango0

Thanks Rico.
Yes, I noticed this in changelog:
> Split libcogl-pango out of the main libcogl package

Anyway the new cogl should depend on cogl-pango.

---

### Post by Harry33 on 2011-10-17
... or even better ...
clutter should depend on cogl-pango.

---

### Post by paul_in_london on 2011-10-17
Fine here too now thanks guys.

First updated/upgraded using aptitude and then:

```
sudo aptitude install gir1.2-coglpango-1.0 libcogl-pango0
```

without any problems. :)

---

### Post by ventrical on 2011-10-17
> **ronacc said:**
> thanks ricotz that fixed it , but warning to others when I tried to install both at once from synaptic , gir1.2-coglpango-1.0 threw a conflict with libcogl-pango0 so Installed libcogl-pango0 first then gir1.2-coglpango-1.0 . that went with no conflicts . looking at the dependencies for gir1.2-coglpango-1.0 it both depends and conflicts with libcogl-pango0 .
 
That worked great here.
 
thanks

---

