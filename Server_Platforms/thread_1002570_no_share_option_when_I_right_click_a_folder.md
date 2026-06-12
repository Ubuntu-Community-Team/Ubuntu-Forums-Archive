---
title: "no share option when I right click a folder"
date: 2008-12-05
forum: Server Platforms
---

### Post by b-boy on 2008-12-05
Hi 

I have a problem trying to share a folder on my ubuntu server when I right click there is not share option in the menu
I do have samba installed

please assists

---

### Post by chewearn on 2008-12-05
Instead of trying to fight the build-in file sharing options (which in my personal experience has been PITA), I suggest to use system-config-samba.

To install:
```
sudo apt-get install system-config-samba
```

Find it in:
System > Administration > Samba

---

### Post by b-boy on 2008-12-05
> **chewearn said:**
> Instead of trying to fight the build-in file sharing options (which in my personal experience has been PITA), I suggest to use system-config-samba.

To install:
```
sudo apt-get install system-config-samba
```

Find it in:
System > Administration > Samba

thanks that worked

---

