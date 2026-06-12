---
title: "Virtual Box and trouble"
date: 2007-10-29
forum: Virtualisation
---

### Post by Revfisk on 2007-10-29
I'd appreciate your help if any of you know what to do.

I tried installing virtual box based on a recommendation on the forum, but the cpu was interrupted mid install.  Now, none of my dpkg functions work.  I cannot use the synaptic mangaer nor updates.  I keep getting the same error, "e: Viritual box needs to be installed but I cannot find the archive".

Any thoughts?  I'm lost.  I'm really new to this and way over my head.  Is Ubuntu so easy to destroy that I did it that fast?  I hope not.  :)

---

### Post by bodhi.zazen on 2007-10-29
Open a terminal and enter this command :

```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

Then you can re-install VirtualBox if you like, during the install, to accept the license, use the tab key to select "OK" and the Enter key to proceed :)

---

### Post by Revfisk on 2007-10-29
Wow.  Two hours of pain and death, over in a flash.  THANKS!  Sorry to post in the wrong place.:lolflag:

---

