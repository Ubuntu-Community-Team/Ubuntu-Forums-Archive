---
title: "Is it safe to stop apt-mirror, then resume download?"
date: 2009-02-23
forum: Server Platforms
---

### Post by PryGuy on 2009-02-23
Good day!
I use apt-mirror to create Ubuntu repo on my production machine, so I have to reboot/shutdown/whatever from time to time. Is it safe to stop apt-mirror and resume download later? I'm afraid I'll get some packages broken... :-k

Thank you in advance!

---

### Post by PryGuy on 2009-02-25
Anybody?

---

### Post by netztier on 2009-02-25
> **PryGuy said:**
> Good day!
I use apt-mirror to create Ubuntu repo on my production machine, so I have to reboot/shutdown/whatever from time to time. Is it safe to stop apt-mirror and resume download later? I'm afraid I'll get some packages broken... :-k

Thank you in advance!

From my experience with it, you can stop it when it's running - AFAICR partial downloads are stored in a temporary directory and only moved to the archive when fully downloaded and integrity-checked. 

regards

Marc

---

