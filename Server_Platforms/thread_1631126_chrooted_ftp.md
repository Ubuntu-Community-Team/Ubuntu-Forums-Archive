---
title: "chrooted ftp"
date: 2010-11-26
forum: Server Platforms
---

### Post by Matakoo on 2010-11-26
I'm setting up a server that requires ftp-access (only for known users, so no anonymous access). One requirement is that the users are not allowed to browse out of their /home, which I've accomplished by chrooting them.

However, that means that ls doesn't work so they don't get to see their files. The only way out of that dilemma, as far as I know, is to provide a statically build ls. Is there any other way? The reason I ask is because coreutils refuses to compile for me so I have not been able to get that static ls. Or can I found it packaged somewhere? For 10.04 64-bit.

Many thanks if anyone can help me solve this.

---

### Post by elico on 2010-11-26
what ftp server are you using?

---

### Post by James78 on 2010-11-26
I don't know what you're using, but you can get the desired effect in Proftp by adding this to the configuration.
```
DefaultRoot ~
```
Of course, this will chroot to ~, a.k.a. /home/user

---

### Post by Matakoo on 2010-11-26
> **James78 said:**
> Of course, this will chroot to ~, a.k.a. /home/user

That was the desired effect, yes. Turns out it wasn't the ftp-server that was at fault at all. For test-purposes (the server isn't live yet) I had set the login-shell for the test-user to /bin/false since they won't be needing shell-access. Somehow I forgot to turn it back to /bin/bash. Now everything works as intended.

Do I feel silly...

---

