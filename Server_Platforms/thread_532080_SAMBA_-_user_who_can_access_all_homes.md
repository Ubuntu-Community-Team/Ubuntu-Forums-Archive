---
title: "SAMBA - user who can access all homes ?"
date: 2007-08-22
forum: Server Platforms
---

### Post by renzokuken on 2007-08-22
Heya,

I have a ubuntu 7.04 PDC running for our office.

my supervisor wants to be able to access everybody's home folders as well as his own. how do i do this in smb.conf?

here is my [homes] section

```

[homes]
   comment = Home
   valid users = %S
   read only = no
   browsable = no

```

could i just add ```
admin users = brian
``` to the end of the section?

---

### Post by renzokuken on 2007-08-23
*bump*

---

