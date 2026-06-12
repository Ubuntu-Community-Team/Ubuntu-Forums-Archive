---
title: "X2GO can't run GUI apps through sudo account"
date: 2015-05-29
forum: Security
---

### Post by coolbrinkman on 2015-05-29
So I recently purchased a VPS running server 14.04. I settled on using X2GO to remote desktop into the server, and XFCE as the desktop, but am running into some trouble.
I have disabled logging in with the root account, and granted my second account 'sudo' permissions.
When I view the server desktop with X2GO, and want to run say 'gufw' (which has an icon in the settings manager), I get no dialog asking me to login as root so that it can be ran.
Using 'sudo gufw' through terminal works of course, but that is defeating the purpose of using X2GO.
I've installed gksudo, thinking it would restore the login dialog, but still no luck.

Is this a desktop environment issue, or am I missing a setting?

---

