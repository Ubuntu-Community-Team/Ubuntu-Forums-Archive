---
title: "A malicious client may be eavesdropping on your session"
date: 2009-06-07
forum: Security
---

### Post by ianmillington on 2009-06-07
UNR 9.04.

I have uninstalled firestarter and configured the firewall with GUFW, using "pre-configured" option - I have it running at startup as well.

However, when loading firefox the following error message is seen

"Could not grab keyboard"

"A malicious client may be eavesdropping on your session"

It didn't happen before I set up GUFW. Can anyone offer any explanation as to why it is happening and, importantly, what I need to do to fix it?

Thanks

---

### Post by duanedesign on 2009-06-07
from what i can tell this warning sounds a bit scarier than it needs too.

see [https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/134474](https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/134474)

"That error is displayed by gksu (a graphical su front end, used by programs like Synaptic(GUFW)) If you happen to change window just as it's starting it can cause this error. Try just starting Synaptic(GUFW) as you would normally and not clicking anything until it asks you for your root password.
??If it still happens then you should worry about the possibility of their being some form of key logger or similar installed. This is very unlikely, but it's a good thing that gksu make sure it will only work when it has total control over the keyboard."

---

### Post by ianmillington on 2009-06-08
Thanks for that

I had wondered about that, and was given a big clue when on one occasion I started the machine up and was asked for the user password to start the firewall. I have now left it as enabled but for Gufw not to actually start up (which I have read elsewhere on this forum is actually better due to gufw running as root)and the error message has gone.

---

### Post by VirLibTau on 2011-05-20
This malicious client error turned out to be a mouse button that was stuck on my mouse.
When I unstuck the button problem went away. Ya!

---

