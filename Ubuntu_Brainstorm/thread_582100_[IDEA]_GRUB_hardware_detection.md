---
title: "[IDEA] GRUB hardware detection"
date: 2007-10-19
forum: Ubuntu Brainstorm
---

### Post by Garyu on 2007-10-19
[https://blueprints.launchpad.net/ubuntu/+spec/grub-hw-detect](https://blueprints.launchpad.net/ubuntu/+spec/grub-hw-detect)

I have filed this blueprint a while ago. I hope someone could add this into Hardy Heron.

My proposal is that since hardware always (well, almost) works well on Live-CD and fresh installs, that there is added an option in the GRUB boot manager to reconfigure hardware. Sometimes when you load nVidia drivers or do other stuff to the system you loose X or you loose sound or other functionality. So it would be nice to have an option to just reconfigure everything automatically.

Even nicer, if it could be specified in a sub-menu to 
1) reconfigure sound
2) reconfigure graphics
3) ...whatever...

---

### Post by Zdravko on 2007-10-20
Hmm, with so many demands I am unsure whether this will make it in Hardy. But who knows. Wonders happen all the time...

---

### Post by Garyu on 2007-10-20
> **Zdravko said:**
> Hmm, with so many demands I am unsure whether this will make it in Hardy. But who knows. Wonders happen all the time...

But wouldn't this be REALLY simple to add? I mean, it's done every time you start the LiveCD and every time you do a fresh install. Should be that difficult to just keep those settings and put it as a startup option...

---

### Post by smartboyathome on 2007-10-20
There COULD be a portion that boots like normal, but instead of pulling up a GUI it pulls up a terminal and executes a script(s) that reconfigures everything.

---

### Post by r3m0t on 2007-10-20
What if I accidentally uninstalled xorg-server for example? I don't think it would be very useful if it wouldn't reliably boot, independent of the status of my current system.

In other words, it would more or less need to store the whole LiveCD on your hard drive.

---

### Post by smartboyathome on 2007-10-20
That would take too much space for some. Instead, how about just lock the important packages from uninstallation?

---

### Post by FrankQuist on 2007-10-21
> **r3m0t said:**
> What if I accidentally uninstalled xorg-server for example? I don't think it would be very useful if it wouldn't reliably boot, independent of the status of my current system.

In other words, it would more or less need to store the whole LiveCD on your hard drive.
It could prompt for the LiveCD (Ubuntu already knows to recognize it as a package repository).If there's internet, it could retrieve any package..

---

