---
title: "Erm.. what is happening to my laptop?"
date: 2008-05-06
forum: The Cafe
---

### Post by Mazza558 on 2008-05-06
It's gone very wierd. It's almost as I've been hacked. I'm using Gutsy and I haven't touched anything recently. Here's my symptoms:

- Emerald says it's using 4GB of RAM. I have 1 GB.

- I can't right-click properly. The right click menu flashes and then disappears.

-I can't add anything to the panel - it tells me "OAFIID:(name of applet) has encounted a problem" 

- Random pauses where I can't click anything.

This has never happened before.

---

### Post by Tatty on 2008-05-06
Have you tried checking for hardware problems?

memtest/fsck/badblocks etc?

---

### Post by Mazza558 on 2008-05-06
> **Tatty said:**
> Have you tried checking for hardware problems?

memtest/fsck/badblocks etc?

I'll have a look.

---

### Post by madjr on 2008-05-06
oh oh a virus :o

---

### Post by prshah on 2008-05-06
> **Mazza558 said:**
> 
-I can't add anything to the panel - it tells me "OAFIID:(name of applet) has encounted a problem" 


Try reinstalling the applets: (Do this from a virtual tty [Ctrl+Alt+F1])

```

sudo /etc/init.d/gdm stop
sudo aptitude reinstall gnome-applets
sudo /etc/init.d/gdm start

```

May also help to clear out your "/tmp", before restarting gdm.


Can't help with the rest; regrets.

---

