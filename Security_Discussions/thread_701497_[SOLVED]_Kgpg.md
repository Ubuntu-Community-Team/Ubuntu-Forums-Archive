---
title: "[SOLVED] Kgpg"
date: 2008-02-19
forum: Security Discussions
---

### Post by Fate Reconciled on 2008-02-19
I just installed Kgpg in order to create my own encryption keys. However, when I try to run Kgpg from Applications ->> Accessories, nothing happens!

Also, when I try to run the app via Konsole I get this:

~$ ERROR: KUnique Application: Can't determine DISPLAY. Aborting.

The setup wizard was doing fine until I accidentally closed midways through the configuration. I've tried complete removal and reinstalling still to no avail.

So here's the ultimate question: What the hell is goin' on?! :x

---

### Post by Dr Small on 2008-02-19
Sounds like some problem with DISPLAY, but I don't know anything about KDE apps. By the way, you can configure gpg and make your keys right from the command line:
[http://ubuntuforums.org/showthread.php?t=680292](http://ubuntuforums.org/showthread.php?t=680292)

Dr Small

---

### Post by Fate Reconciled on 2008-02-19
Yeah, I've read up on the command line method already, but I just wanted a GUI to make it a bit easier. I actually saw a similar case that mentioned a conflict in DISPLAY and disabling it, but it was in German. So kinda hard to discern, haha.

---

### Post by Fate Reconciled on 2008-02-19
Just checked your link. Seahorse works great. Thanks.

---

