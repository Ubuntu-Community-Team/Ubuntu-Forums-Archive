---
title: "Set root so Admin account can't edit?"
date: 2009-05-23
forum: Security
---

### Post by fredkrugar on 2009-05-23
How can I set the root account so an admin account can't edit it or access it's files?
I am trying to do this so my mother who is new to linux does not mess anything up with the root account in case it is needed, but is set on having an admin account.

---

### Post by cariboo on 2009-05-24
If your Mom is a typical computer user she will have no idea what a root account is and what it is for. You can set up user privileges in System-->Adinistration-->Users & Groups to allow a user to do anything but administer the system.

---

### Post by fredkrugar on 2009-05-31
ok thanks, i will try that.

---

### Post by Lars Noodén on 2009-06-02
On systems like that make two accounts.  The first one will be an admin account.  Don't give that one out or, if you do, make sure that the user knows it's not for daily activities.  Then give out the second, non-admin account.  

If you are the one doing maintenance, then set up openssh-server with key-based authentication for your remote access to the maintenance account.

---

