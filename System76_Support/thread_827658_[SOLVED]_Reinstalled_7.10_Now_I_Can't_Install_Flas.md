---
title: "[SOLVED] Reinstalled 7.10 Now I Can't Install Flashplayer Plugin"
date: 2008-06-13
forum: System76 Support
---

### Post by tuebinger on 2008-06-13
I reinstalled 7.10 on my Daru2 because I wanted to be able to use the suspend feature on my laptop (since suspend is not working in 8.04 yet).  Now for some reason I can't install the flashplayer plugin.  I get the following message when I try to install:

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

I had installed it on 7.10 before.  Am I forgetting something?

---

### Post by thomasaaron on 2008-06-13
Did you try...

sudo apt-get install flashplugin-nonfree

---

### Post by tuebinger on 2008-06-13
No, but that did the trick.  Thank you!

---

