---
title: "User Account"
date: 2009-06-03
forum: Server Platforms
---

### Post by Romala on 2009-06-03
Dear friends,
Is it possible to make an account which have no rights to change server settings? 
Ubuntu 8.10 Server.
Thank you in advance!

---

### Post by smileypaul on 2009-06-03
This can be achieved by denying them access to "sudo"

Do a bit of research, I believe you'll have to take him out of the admin group, and do a bit of work in the /etc/sudoers file.

Hopefully someone will chime in with a more definitive answer.

---

### Post by cdenley on 2009-06-03
Users in the admin group can use the sudo command to escalate to root privileges, which should be necessary in order to make any changes to the system setting. By default, new users you create aren't in the admin group. The user created during the ubuntu install is in the admin group by default. There is no need to edit the sudoers file to create non-admin users.

---

### Post by Romala on 2009-06-07
Thank you, you're right

---

