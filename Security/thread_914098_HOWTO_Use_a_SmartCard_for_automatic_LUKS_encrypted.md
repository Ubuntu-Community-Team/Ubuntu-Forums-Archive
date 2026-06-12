---
title: "HOWTO: Use a SmartCard for automatic LUKS encrypted disk unlock"
date: 2008-09-08
forum: Security
---

### Post by madscientist159 on 2008-09-08
I have written a HOWTO for use of an inexpensive SmartCard as an LUKS unlock device here: [https://wiki.ubuntu.com/SmartCardLUKSDiskEncryption](https://wiki.ubuntu.com/SmartCardLUKSDiskEncryption)

From what I can tell, this is secure if:
1. You lose the computer (simply treat the old AUT1 key as compromised and create another)
2. You lose the SmartCard
Just don't lose both at the same time! :)

I am also working on a way to get KDE and KDM to recognize the SmartCard and unlock or login to the computer, and will update the Wiki page when I am finished.

Any comments or suggestions are welcome...

Tim

---

### Post by Rocket2DMn on 2008-09-11
I have approved this post, but since this guide is on another website, I moved it from Tutorials & Tips to Security Discussions.  Please see [http://ubuntuforums.org/showthread.php?t=677396](http://ubuntuforums.org/showthread.php?t=677396) for more information about posting in the T&T forums area.  Thank you.

---

### Post by madscientist159 on 2008-09-11
> **Rocket2DMn said:**
> I have approved this post, but since this guide is on another website, I moved it from Tutorials & Tips to Security Discussions.  Please see [http://ubuntuforums.org/showthread.php?t=677396](http://ubuntuforums.org/showthread.php?t=677396) for more information about posting in the T&T forums area.  Thank you.

Thank you for doing that--being somewhat new in posting to these forums, I didn't know where to put that post. #-o

The KDE and KDM integration instructions are now up on the Wiki page.

---

