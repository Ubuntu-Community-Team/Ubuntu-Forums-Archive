---
title: "Deleting local Active Directory user?"
date: 2007-04-25
forum: Server Platforms
---

### Post by turn1200 on 2007-04-25
Hello All,

I've gotten my Active Directory working for the most part but am wondering how do I delete a domain user who now exists locally?  In other words, I had an Active Directory user login through SSH.  Their /home/DOMAIN/username directory was created and they can login.  I'd now like to delete them only from the local machine.  I tried the following:

sudo smbpasswd -x USERNAME
Failed to delete entry for user USERNAME.
Failed to modify password entry for user USERNAME

AND

sudo userdel USERNAME
userdel: error deleting password USERNAME
userdel: error deleting shadow password USERNAME

Any ideas?

---

### Post by rickyjones on 2007-04-25
They shouldn't have an account on the local machine. The whole point of Active Directory authentication is that the user account exists on the network in Active Directory and they can log into any machine connected to the domain.

What will be on the local machine is their local profile and home directory - in essence deleting that would get rid of the user's information on that computer.

-Richard

---

