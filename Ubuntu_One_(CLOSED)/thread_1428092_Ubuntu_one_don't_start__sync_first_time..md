---
title: "Ubuntu one don't start / sync first time."
date: 2010-03-12
forum: Ubuntu One (CLOSED)
---

### Post by markinf on 2010-03-12
After I had a lot of problems I uninstalled UbuntuOne and did that instructions (purge, deleted the key from seahorse, rm ~/.cache/ubuntuone, rm ~/.local/share/ubuntuone) etc and Installed again Ubuntu ONe to attempt to fix my problem doing a clean Install.

However right know, when I launch ubuntu one it goes directly to the Ubuntu One Web Page, but when I press sign in, it just hangs.

Any Idea of what it could be?

---

### Post by cpmman on 2010-03-12
I had the same yesterday - but when I logged into my account via the web I found about 12 occurrences of my machine logged!  Deleted the excess and reconnected via Ubuntuone and it synchronised OK.

Problem you may have now is that the Launchpad site has crashed - I don't know if that affects Ubuntuone.

---

### Post by iansyngin on 2010-03-12
[http://ubuntuforums.org/showthread.php?t=1425454](http://ubuntuforums.org/showthread.php?t=1425454)

---

### Post by joshuahoover on 2010-03-12
> **markinf said:**
> After I had a lot of problems I uninstalled UbuntuOne and did that instructions (purge, deleted the key from seahorse, rm ~/.cache/ubuntuone, rm ~/.local/share/ubuntuone) etc and Installed again Ubuntu ONe to attempt to fix my problem doing a clean Install.

However right know, when I launch ubuntu one it goes directly to the Ubuntu One Web Page, but when I press sign in, it just hangs.

Any Idea of what it could be?

The good news is that we know about the issue and are trying to fix it. The bad news is that we're still trying to nail down the exact cause. You can track our progress at the following bug: [https://launchpad.net/bugs/537525](https://launchpad.net/bugs/537525)

Apologies for the inconvenience. We appreciate your patience as we get this one fixed.

Joshua

---

### Post by iansyngin on 2010-03-12
cowboy fix is doing the trick..fair play ;)

---

### Post by markinf on 2010-03-13
> **joshuahoover said:**
> The good news is that we know about the issue and are trying to fix it. The bad news is that we're still trying to nail down the exact cause. You can track our progress at the following bug: [https://launchpad.net/bugs/537525](https://launchpad.net/bugs/537525)

Apologies for the inconvenience. We appreciate your patience as we get this one fixed.

Joshua

Cool now it's working 100%.
Thanks guys \o/

---

### Post by joshuahoover on 2010-03-15
> **markinf said:**
> Cool now it's working 100%.
Thanks guys \o/

Good to hear and thank you and everyone else facing this issue for your patience! We are working on a more permanent fix but the workaround we put in on the server side is OK for now.

Thank you,

Joshua

---

