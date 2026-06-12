---
title: "Sealing off the LiveCD"
date: 2010-05-09
forum: Security
---

### Post by directedition on 2010-05-09
I'm rolling my own version of the LiveCD (directly, not using the apt-based tools) and I'm trying to lock it down. I'm doing things like setting up iptables to only allow network activity with tor and whatnot, but I can't figure out how to lockout root. I've set the password for root and commented everything out of sudoers, but when I boot from the resulting iso, the sudoers file suddenly has "%admin ALL=(ALL) NOPASSWD: ALL" appended to the end, which tells me that somewhere is in the boot process the file is modified to have that. How can I disable this process? I really want to lock down the system so that root is impossible to reach.

---

### Post by lemming465 on 2010-05-10
Not sure about where the modification is coming from, but making sure the live user isn't a member of group admin would help.

---

