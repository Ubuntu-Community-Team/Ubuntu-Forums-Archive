---
title: "Shutdown"
date: 2009-11-13
forum: Security
---

### Post by ST3ALTHPSYCH0 on 2009-11-13
This actually works to my advantage, but it seems to be a security flaw overall. When you try to shutdown from a DE you are informed that administrator authorization is required when others are logged in. However, if you simply log out, you can choose shutdown from the log in screen and it doesn't matter who's logged in. Can anyone explain this?

---

### Post by undecim on 2009-11-13
I'm guessing GDM is authorized to shut down the computer without the root password. This really isn't a security flaw, because anyone who has physical point-and-click access to GDM could just use the power button anyways, and its better to have the computer properly shut down.

---

### Post by ST3ALTHPSYCH0 on 2009-11-13
I'll accept that answer. In my case it's beneficial for my wife to be able to shutdown the system if I forget to log out anyway. The only reason I could see it being a security flaw would be the ability to reboot with a live CD, but, as you say, a hard reboot could accomplish the same end.

---

### Post by movieman on 2009-11-14
I would guess that GDM runs as root, so it doesn't need privilege escalation to reboot.

Also, if someone is logged in, they may be doing something that they don't want to lose just because someone walked past and selected 'reboot' :).

---

### Post by QLee on 2009-11-14
> **ST3ALTHPSYCH0 said:**
> This actually works to my advantage, but it seems to be a security flaw overall. When you try to shutdown from a DE you are informed that administrator authorization is required when others are logged in. However, if you simply log out, you can choose shutdown from the log in screen and it doesn't matter who's logged in. Can anyone explain this?

Not a security flaw, GDM is configurable to allow or disallow regular users to shutdown the system from the login screen.

---

### Post by ST3ALTHPSYCH0 on 2009-11-14
Ah, I didn't realize that you could reconfigure to disallow that. Not a flaw, and definitely a convenience at this home!

---

