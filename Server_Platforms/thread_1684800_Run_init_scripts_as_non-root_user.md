---
title: "Run init scripts as non-root user?"
date: 2011-02-09
forum: Server Platforms
---

### Post by MadJester on 2011-02-09
I wrote a custom init script for a java application.  The script resides in /etc/init.d and follows the convention for the init.d scripts.  However, the script runs the java process as root.  I need these processes to run as a non-root user.  Is there a way besides using sudo or su in the script (seems inelegant), to run the script as a specific non-root user?  Perhaps using a .conf file in /etc/init or a daemon wrapper?  What would the Ubuntu way of doing this be?

---

### Post by Kooothor on 2011-02-09
Hello,
Try to place this in you /etc/rc.local.
Let's say you want it started by user john :
```
su john -c '/etc/init.d/yourscript start'
```

---

### Post by sisco311 on 2011-02-09
> **MadJester said:**
> seems inelegant

It's not.

Contact the developers of the software and ask them to include a *--run-as-user=username* option...

---

