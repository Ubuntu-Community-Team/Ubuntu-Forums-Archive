---
title: "Firefox dependency"
date: 2007-04-21
forum: Repositories &amp; Backports
---

### Post by Lollingsgrad on 2007-04-21
I have just attempted to uninstall Firefox (I am considering replacing it with another browser) using the package manager, and noticed that the package manager also wanted to uninstall ubuntu-desktop (not a good idea!). Given the controversy over Microsoft bundling/integrating Internet Explorer with its operating system, isn't it a bad idea for Ubuntu to do the same? Wouldn't it be better for ubuntu-desktop to simply not depend on Firefox? It's only a recommended dependency right now anyway.

For the record my system is Feisty Fawn desktop, AMD 64 architecture.

---

### Post by meng on 2007-04-21
ubuntu-desktop is just a metapackage, it just lists a whole bunch of dependencies so that instead of having to type:

sudo apt-get install firefox rhythmbox totem evolution ....
(not a real command, but you get the idea)

you could just type:
sudo apt-get install ubuntu-desktop

so, if you really must uninstall firefox, then you can remove ubuntu-desktop without breaking anything.

But if you're not short on disk space, then I recommend you don't uninstall firefox, and just use your preferred browser instead.

The Windows/IE bundling is a completely different issue.

---

### Post by Lollingsgrad on 2007-04-21
> **meng said:**
> so, if you really must uninstall firefox, then you can remove ubuntu-desktop without breaking anything.

Okay, thanks. Will this in any way inhibit my ability to obtain future updates? For example, when upgrading distribution.

> **meng said:**
> The Windows/IE bundling is a completely different issue.

Would you mind expanding on this?

---

### Post by meng on 2007-04-21
1. Yes, if you uninstall ubuntu-desktop it will screw up the upgrading. You would need to reinstall ubuntu-desktop before upgrading. Hence my advice to keep firefox, even if you aren't going to use it.
2. I was just pointing out that the firefox link to ubuntu-desktop is not bundling, in that firefox is not an intrinsic part of the OS, you can remove it without breaking the system. Whereas you just can't uninstall IE from Windows, it's a part of the OS.

---

