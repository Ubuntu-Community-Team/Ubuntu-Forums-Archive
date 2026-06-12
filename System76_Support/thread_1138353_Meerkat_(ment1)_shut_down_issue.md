---
title: "Meerkat (ment1) shut down issue"
date: 2009-04-26
forum: System76 Support
---

### Post by Collin White on 2009-04-26
After upgrading to Jaunty I've noticed that Shut Down doesn't completely shut down.

My user account logs off, the screen shows the Ubuntu splash with the scrolling bar, then the screen goes blank and the blue light on the power button goes out, I can still hear the fan going and the power button becomes unresponsive.  I have to resort to physically unplugging the box to get it to completely power off so that I can restart it.

I've tried the System76 Driver option but it says that Ubuntu handles all drivers or something to that effect.  Is there a repository that I need to enable?

Any thoughts on this?

---

### Post by jdb on 2009-04-26
> **Collin White said:**
> After upgrading to Jaunty I've noticed that Shut Down doesn't completely shut down.

My user account logs off, the screen shows the Ubuntu splash with the scrolling bar, then the screen goes blank and the blue light on the power button goes out, I can still hear the fan going and the power button becomes unresponsive.  I have to resort to physically unplugging the box to get it to completely power off so that I can restart it.

I've tried the System76 Driver option but it says that Ubuntu handles all drivers or something to that effect.  Is there a repository that I need to enable?

Any thoughts on this?

Try holding the button down for 20 seconds or so.

jdb

---

### Post by thomasaaron on 2009-04-26
Yes. Unplugging it shouldn't be necessary.

Also, is there a suspend or hibernate cycle involved in the mix? Or does this happen when shutting down after a fresh reboot?

---

### Post by Collin White on 2009-04-26
Trying different things, I've noticed that when I go to Shut Down it starts a 60 second timer.  When I let the timer run out on its own it shuts down fine.  When I press the Shut Down button to immediately begin the shut down process is when it has the issue.

---

### Post by Collin White on 2009-04-26
> **thomasaaron said:**
> Yes. Unplugging it shouldn't be necessary.

Also, is there a suspend or hibernate cycle involved in the mix? Or does this happen when shutting down after a fresh reboot?

Shutting down after a fresh reboot.

---

### Post by KRTW on 2009-04-26
I'm having the same problem with my pangolin after the jaunty upgrade. The system hangs on shutdown even after a fresh reboot. I let it stay at the blank screen for over 15 minutes before manually shutting it down with the power button.

---

### Post by thomasaaron on 2009-04-27
I just tested this on our shop meerkat. It has no problems shutting down. However, it has a fresh install.

Most likely the upgrade was while Ubuntu's servers were under a lot of stress and you guys got corrupted upgrades. (We don't get this on the Pangolin either.)

I'd recommend doing a fresh install.

---

### Post by KRTW on 2009-04-28
Thanks thomasaaron, seems like that fixed it.

---

