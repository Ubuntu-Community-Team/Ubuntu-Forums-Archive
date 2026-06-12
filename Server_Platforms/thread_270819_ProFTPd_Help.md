---
title: "ProFTPd Help"
date: 2006-10-03
forum: Server Platforms
---

### Post by Zephirus on 2006-10-03
New to the program and I was wondering where the config files are for it.  IM new to ubuntu and linux for that matter.  

I am running 3 virtual servers for different websites and I want to give an FTP user access to their OWN directory ONLY.  


THanks for the help!

---

### Post by sonic2000gr on 2006-10-04
The file you are looking for is /etc/proftpd/proftpd.conf
To limit user access to their home directories, add the  following to the configuration file:

```

<Global>
DefaultRoot ~
</Global>
```

---

