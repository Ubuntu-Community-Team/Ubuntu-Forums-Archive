---
title: "default group memberships in Ubuntu"
date: 2012-05-10
forum: Security
---

### Post by hojjat on 2012-05-10
I made the mistake of removing myself from all the groups by running a bad command. I didn't realize until later when I tried to sudo and I got an error message describing my user is not a member of sudoers.

This is a clean installation of Ubuntu 12.04. I have restored sudo access using the recovery mode in the installation CD. Now I want to add this account to all the groups it originally belonged to. Can someone please post a list of all groups that the default account in Ubuntu is in?

PS: I have found some lists online but I need the most up-to-date list for 12.04

---

### Post by hojjat on 2012-05-15
Anyone?

---

### Post by Ms. Daisy on 2012-05-16
So you have restored the initial user created by the Ubuntu installer into the group "sudo," right?  Are you still having problems?

Are there other users on this computer?

BTW, the sudoers group has changed with 12.04:
[QUOTE=wiki.ubuntu.com]Up until Ubuntu 11.10, administrator access using the sudo tool was  granted via the "admin" Unix group. In Ubuntu 12.04, administrator  access will be granted via the "sudo" group. This makes Ubuntu more  consistent with the upstream implementation and Debian. For  compatibility purposes, the "admin" group will continue to provide  sudo/administrator access in 12.04. [/QUOTE]

edit: deleted the incorrect information

---

### Post by Ms. Daisy on 2012-05-16
Google found a thread nearly identical to yours:

[http://ubuntuforums.org/showthread.php?t=1970991](http://ubuntuforums.org/showthread.php?t=1970991)

That should answer your question.

---

