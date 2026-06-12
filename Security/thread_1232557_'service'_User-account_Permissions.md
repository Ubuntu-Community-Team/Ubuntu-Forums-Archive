---
title: "'service' User-account Permissions"
date: 2009-08-05
forum: Security
---

### Post by aNovitiate on 2009-08-05
Over a few weeks reading, I've been trying to uncover the 'proper' way to configure User-accounts to run PHP, CodeIgniter and Apache.  This is for  notebook development  i.e. **not** for Internet-facing security.

I *chown*'d my web and PHP CodeIgniter directories to *www-data:www-data* (the Apache 'User' and Group).

I added my User-account (*mike*) to the *www-data* **Group**, hoping that the Read & Write Privileges on the *www-data* **Group** would permit me to edit/develop the files.  No such luck!  :confused:

I understand that *www-data* is a ***service***, rather than ***application***, 'User'.

*question*:  Do ***service-Users*** _**not**_ have editing Permissions ?

If not (as I suspect), is there some clever/elegant/proper way to set up a 'development' computer ... with**out** simply resorting to virtually negating all security via **777** Permissions for *user:group* and *other* ?

Thanks - for taking a moment to Reply,

---

### Post by Agent ME on 2009-08-05
There is no real difference between "application" and "service" user accounts (except that on Ubuntu regular user account numbering starts at 1000, and that "service" accounts generally don't have passwords to log in with).

If you change your group membership, you have to log out and log back in before any changes take affect.

---

### Post by aNovitiate on 2009-08-05
> **Agent ME said:**
>   If you change your group membership, you have to log out and log back in before any changes take affect. 

Ah, the logout/login worked!  
I had thought that *file* Permissions changes took effect, immediately.  Duh?   [IMG]http://ellislab.com/images/smileys/question.gif[/IMG] That **Group** memberships require a logout/login is a subtle lesson, I guess?

Please pardon my ignorance ... :)

---

