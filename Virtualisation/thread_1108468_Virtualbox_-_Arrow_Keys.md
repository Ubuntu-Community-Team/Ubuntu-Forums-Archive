---
title: "Virtualbox - Arrow Keys"
date: 2009-03-27
forum: Virtualisation
---

### Post by Mehall on 2009-03-27
Using Crunchbang just now, but had the problem in others too.

When using Virtualbox, my arrow keys (and some like home, pg up, etc.) don't work.
Using a laptop.

---

### Post by tmbltx on 2009-03-29
I'm also having this problem.

My host is Ubuntu 8.10 (intrepid) amd64 and is completely updated including the newest package for Virtualbox.  I have tried with various guests: Slackware 12.2, DSL 3.4.12, and Debian 5.0 amd64.  My keyboard is a very basic usb keyboard made by Rosewill.

With all guests the arrow keys on my keyboard do not work - not during boot, at the command line, or in the gui.  Pressing the right arrow key seems to act as the delete key, but none of the other three seem to do anything at all.

If I turn numlock off I am able to use 2, 4, 6, and 8 as the arrow keys, but for ease of use I would MUCH rather figure out how to make the arrow keys work.

---

### Post by wendall911 on 2009-05-12
Try adding -evdevkeymap ... should fix the issue.

---

