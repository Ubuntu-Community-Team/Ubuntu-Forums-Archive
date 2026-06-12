---
title: "Fingerprint reader on 13.04 (gnome 3 PPA)"
date: 2013-03-07
forum: Security
---

### Post by ratdude747 on 2013-03-07
I recently did some modifications to my Dell Latitude D630, which included the addition of a fingerprint strip.

I currently run Ubuntu 13.04 with gnome 3.8 via PPA... and I've been having all sort of fits trying to get the fingerprint reader to work right.

First off, I installed fprintd, which made the fingerprint login option show up in the user accounts window. I go through, register my right index finger, and it says I can go ahead and login, etc. with the fingerprint. However, even after a reboot, it only prompts for passwords, never a fingerprint. Nor does it respond to a finger swipe. 

Is there some other package I forgot to install? :confused:

---

### Post by trundlenut on 2013-03-07
IIRC you need to mess around with PAM to get it to work correctly (although it is a while since I had a laptop with the fingerprint reader and so I'm not sure what has changed).  Also even after you log in with your fingerprint you still need to enter your password to unlock the keyring so I gave up using it as it was a faff more than anything else.

---

### Post by ratdude747 on 2013-03-07
Aha!

Fixed it.

I needed to install libpam-fprintd as well. I did that and all is well.

---

