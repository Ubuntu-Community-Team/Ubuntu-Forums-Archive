---
title: "Disable sudo, allow only su"
date: 2010-07-30
forum: Server Platforms
---

### Post by Thyagaraj on 2010-07-30
How to disable 'sudo' for all or a particular user and allow only 'su'?

---

### Post by rubylaser on 2010-07-30
The easiest way to do this would be to edit /etc/group, and remove the user from the admin group.  But the user will have to log out and log back in again before they lose the group memberships in their existing shells. There's no command for dropping group privileges once you have them.  That way the user can't use sudo.

---

### Post by Thyagaraj on 2010-07-30
But the user does not belong to any group except its own primary group and this user is created during the installation of the ubuntu server os. The user can do 'sudo -s' instead 'su'.

---

### Post by cdenley on 2010-07-30
> **Thyagaraj said:**
> But the user does not belong to any group except its own primary group and this user is created during the installation of the ubuntu server os. The user can do 'sudo -s' instead 'su'.

The user created during install belongs to the admin group. By default, sudo is configured to allow only members of that group (or root) to use sudo. Actually, apparently there is now a sudo group as well.
```

id
getent group admin sudo
sudo grep '^[^#]' /etc/sudoers
sudo id

```

---

### Post by Thyagaraj on 2010-07-31
Excellent denley!
 
I dont even know such a group admin would be there.
Is there any way so that removing user from a group sudo or admin will restrict using sudo -s?
#gpasswd -d username groupname           will remove the user?



Thank You!

---

### Post by inphektion on 2010-07-31
if you run 'visudo'
you'll see the groups that have access to use sudo.  just remove any users from those groups and they won't have perms to sudo.

---

### Post by Thyagaraj on 2010-08-30
NO! I could not able to sort out this issue.
As we know we can apply SUID on commands to authenticate the users to use specific commands. I applied suid on the command sudo to restrict a user which is created during server installation. I checked if that user can issue sudo and it gave permission error.

But I have webmin installed and root is restricted for ssh and webmin logins(root is accessed with su). I will backup my data logging in to webmin with normal user(belong to admin group). After disabling sudo for this user I could not login to webmin and I had to enable sudo for this user.

Plz any one help...

---

