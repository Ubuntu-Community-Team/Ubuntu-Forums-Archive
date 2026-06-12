---
title: "Ubuntu 13.04: Anyone know what the first entry is about?"
date: 2013-03-20
forum: Ubuntu Development Version
---

### Post by Baldrick_NZ on 2013-03-20
Sorry I meant the fourth entry!! Doh!

In the screengrab attached? It goes to 20%CPU with an app running. Anyway to get rid of it?

Cheers.

---

### Post by stinkeye on 2013-03-20
Is it Xorg?

---

### Post by Baldrick_NZ on 2013-03-20
> **stinkeye said:**
> Is it Xorg?

Not sure, how would I find out? Definitely a root property.

It does the same with LightDM as well, the following pic shows it with running a wine app... the third item down the list.

---

### Post by dino99 on 2013-03-20
you have the "guake" app installed (see synaptic)

---

### Post by Baldrick_NZ on 2013-03-20
> **dino99 said:**
> you have the "guake" app installed (see synaptic)

My counting is atrocious! First posted corrected. Thanks Dino99.

---

### Post by stinkeye on 2013-03-20
Look in system monitor.

---

### Post by denver on 2013-04-01
If you mean to say Xorg, well, that's your display server. You need that in order to have a graphical user interface :). If you kill it, you will be dropped to one of the VTYs (Virtual terminals, the ones you get if you press Ctrl+alt+F1). It usually runs on VTY 7 (Ctrl+Alt+F7).

It will consume CPU when rendering the display in some cases. If you have an app that renders to the screen, like a game or video player, sometimes you will see high CPU usage from X.

---

