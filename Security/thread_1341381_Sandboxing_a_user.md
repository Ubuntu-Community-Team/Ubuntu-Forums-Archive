---
title: "Sandboxing a user"
date: 2009-11-29
forum: Security
---

### Post by harry71194 on 2009-11-29
I know this has probably been asked before, but I searched and couldn't find a nice easy answer. How can I sandbox a user? Basically, give someone I don't trust 100%, SSH access to my system. Allow them to run scripts etc in PHP (they want to use my server to test some PHP code), but not allow them to touch any of my files outside of their /home/ directory.

How can I do this? Thank you in advance.

---

### Post by kevdog on 2009-11-29
Do a search for linux jail.  Openssh can do this along with some outside programs such as jailkit.

---

### Post by rookcifer on 2009-11-29
Just use the already built in chroot.  You don't need any outside programs.  OpenSSH does this already.

Google: "chroot openssh"

---

