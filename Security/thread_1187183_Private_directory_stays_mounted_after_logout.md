---
title: "Private directory stays mounted after logout"
date: 2009-06-14
forum: Security
---

### Post by robwicks on 2009-06-14
I have a 64 bit Jaunty machine. I want to be able to log out of my user account, then hibernate or suspend the machine from the GDM login screen. This works fine, but I noticed, when I had switched to another virtual console and logged in directly as root, that my Private directory did not unmount when I logged out of the system. I don't know if this is related, but an "evolution-data-server-2.26" process was still running as the user. It was the only user process still running. Even after I killed it, however, the Private directory remained mounted. I don't want the home directory to remain decrypted after I log out. I think that directory unmounted correctly after logout on previous versions of Ubuntu.

---

