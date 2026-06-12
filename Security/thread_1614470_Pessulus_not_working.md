---
title: "Pessulus not working"
date: 2010-11-05
forum: Security
---

### Post by scuccii on 2010-11-05
I've currently installed Pessulus in attempts to block other user profiles from getting into anything they shouldn't. 
 
I installed it within my user account and ran "sudo pessulus" which brought up the GUI with the small wooden shields. After I make the changes I don't see anything being locked down. I want to lock down the panels (appilcations, places, system) from other users being able to modify.
 
Any ideas?

---

### Post by cariboo on 2010-11-05
Did you log out so that the changes could take affect?

---

### Post by scuccii on 2010-11-05
> **cariboo907 said:**
> Did you log out so that the changes could take affect?
I did log out, I actually rebooted and I don't see a change. Maybe I'm doing something wrong.

Are there any other tools or best practices that you would recommend tightening security of the desktop beside Pessulus?

Thanks.

---

### Post by cariboo on 2010-11-06
I personally set my home directory permissions to 700, that way only the owner of the directory and root have access. Shared directories are all mounted in /media so other users have access to files that need to be shared.

---

### Post by scuccii on 2010-11-08
What else can I do to limit what another user can do after logging?

---

