---
title: "Proper configuration of User Account"
date: 2006-06-29
forum: Server Platforms
---

### Post by cochrannd on 2006-06-29
I created a new account and deleted my old.  My main group of the new account is username, shell is /bin/bash, home directory is /home/username.   After deleting the old account I found out that the new account is not a member of sudoers.  I used a live cd to add 'username'  ALL=(ALL) ALL to the file.  Now I can access administrative functions with sudo.  I just want to make sure that this is a secure account and I am not romping through my system as root.  Thanks in advance.

---

### Post by Maggot on 2006-06-29
You should be fine.  My /etc/sudoers has:

%admin ALL=(ALL) ALL

and my user is in the admin group. Essentially its the same thing. You would only be concerned about the admin group if you were managing a lot of users.

---

### Post by cochrannd on 2006-06-29
Ok, thanks.  Kind of a pointless post now though because my whole system crashed.  I think it is time for me to read a lot more about bash and become familiar with system before trying to change anything else.

---

