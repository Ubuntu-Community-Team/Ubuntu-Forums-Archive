---
title: "SSH port change"
date: 2005-11-28
forum: Server Platforms
---

### Post by GuruMadMat on 2005-11-28
I installed ssh and i want to change the port to 25002
how can i do this?

---

### Post by LordHunter317 on 2005-11-28
Editing the Port directive in /etc/ssh/sshd_config.  But if your'e doing this for security, you won't gain any.

---

### Post by GuruMadMat on 2005-11-28
i know but it's more convenient for me

---

### Post by squirrelyosis on 2005-11-28
I changed my port because I was getting tons of dictionary attacks in my auth.log Now since I've changed the port I don't see any.  It seemed to have worked for me.  Why do you say it wouldn't improve security?

---

### Post by LordHunter317 on 2005-11-28
Because those dictionary attacks aren't very smart, and even a reasonably strong password will stop them.

Moreover, it's a temporary fix.  What happens when no one runs on port 22?  The automated attacks port scan first, find you, and just continue.  You've just obscured yourself.

The correct solution is to use and enforce strong passwords.

---

