---
title: "Completely removing MySQL Server"
date: 2011-07-14
forum: Server Platforms
---

### Post by ki4jgt on 2011-07-14
sudo aptitude remove --purge mysql-server

Will this command completely remove everything, even tables and users? I've found a better way to manage data on my site. IMHumbleO it's a lot less complex, and is more catered to my site than a full out database.

---

### Post by ruffEdgz on 2011-07-14
Actually, if you are using aptitude, you should be able to use this as the command:
```

sudo aptitude purge mysql-server

```
When doing the command 'man aptitude', I found an entry about purge that sounds like it will remove all the configuration file and data:
> 
Purge <package>: remove it and all its associated configuration and data files.
Cheers!

---

### Post by karlson on 2011-07-14
> **ki4jgt said:**
> sudo aptitude remove --purge mysql-server

Will this command completely remove everything, even tables and users? I've found a better way to manage data on my site. IMHumbleO it's a lot less complex, and is more catered to my site than a full out database.

Maybe, maybe not.

If you kept the data files for mysql in default locations then it will remove all DB related information.  If you moved it then it will not.  In addition it would be:
```

sudo aptitude purge mysql-server

```

---

### Post by ki4jgt on 2011-07-14
Thanks guys. I just didn't want stuff taking up space on my drive that didn't need to be there. I only have three variables I need to keep up with, so I decided to just use sockets with a python socket server.

---

