---
title: "CUPS printer management, .htpasswd?"
date: 2009-10-12
forum: Security
---

### Post by StrangeWill on 2009-10-12
I would like to use a .htpasswd file to allow access to localhost:631 however it seems that cups.conf does not accept the apache command. I don't want to create users on the system for those who can access the print queue.

Any ideas?

---

### Post by cariboo on 2009-10-12
Why no make the users members of the lpadmin group, that way they have rights to administer the printers.

---

### Post by StrangeWill on 2009-10-12
> **cariboo907 said:**
> Why no make the users members of the lpadmin group, that way they have rights to administer the printers.
Well they're not users on the system, I don't want them to be. If it comes down to it I can do that, but already have an .htaccess file for non-user accounts that get access to files through apache. I wanted to be able to use that same file for printer management.

---

### Post by StrangeWill on 2009-11-01
So they must be members of the system? No way in getting CUPS to authorize via an .htaccess file?

---

### Post by cariboo on 2009-11-01
Have you had a look at the access control options in the printer properties?

---

