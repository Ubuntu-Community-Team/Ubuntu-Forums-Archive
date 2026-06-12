---
title: "Creating a nearly-root admin group with sudoers"
date: 2009-07-14
forum: Security
---

### Post by steve_c on 2009-07-14
While I feel like this is a long shot I just wanted to check.

Is it possible to create a sudoers file such that members of a certain group (for instance, %admin) have sudo powers for *nearly* everything, but can never become root nor edit things (e.g., the sudoers and/or passwd files) such that they can become root?

At my work we're debating bringing on more people for systems administration whereas previously I'd been the only one. I'm sure by policy I can get the new sysadmin(s) to use their own accounts and sudo to perform their work, but I was wondering (mostly for the sake of auditing) if there was a way to enforce that they were not doing work as root? Disabling the root account entirely is not an option for policy reasons.

Thank you for any help.

---

### Post by bodhi.zazen on 2009-07-14
Yes, this is in fact the benefit of sudo over su (su is all or none).

Make a new group, use visudo to give that group access to the commands you wish to allow.

You can also limit the group with apparmor if you wish, but probably not needed.

See :

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo)

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

