---
title: "[SOLVED] clamav update problems"
date: 2008-05-04
forum: Security
---

### Post by Kognit on 2008-05-04
Recently i have tried to install clamav 0.93 and i deleted. In the middle of installation of 0.93 i removed 0.91 version.
When now i wanna update signatures (now i have againe 0.91, because i have problems with 0.93) i get this message:
"freshclam: error while loading shared libraries: libclamav.so.4: cannot open shared object file: No such file or directory"

What can i do for resolve my problem

Thanks for answers

---

### Post by Monicker on 2008-05-04
Did you install clamav from source or using the Ubuntu package management system?

---

### Post by Kognit on 2008-05-04
i installed from the source version 0.93, then when i removed it in installed from the package 0.92.1 version

---

### Post by Monicker on 2008-05-04
Sounds like you may not have properly removed the source package.  Did you do use "make uninstall" from the source directory?

I would also do this:

```
sudo apt-get --purge remove clamav
sudo apt-get install clamav
```

---

### Post by Kognit on 2008-05-04
i have tried but the same message still appears when i type "freshclam".

---

### Post by Monicker on 2008-05-04
> **Kognit said:**
> i have tried but the same message still appears when i type "freshclam".

Based on some info from a Google search

[http://forum.configserver.com/showthread.php?p=3720]("http://forum.configserver.com/showthread.php?p=3720")


Try this:
```

sudo ldconfig
```

If that does not work, I don't know what else to tell you.

---

### Post by Kognit on 2008-05-04
> **Monicker said:**
> Based on some info from a Google search

[http://forum.configserver.com/showthread.php?p=3720]("http://forum.configserver.com/showthread.php?p=3720")


Try this:
```

sudo ldconfig
```

If that does not work, I don't know what else to tell you.

I wrote it, then typed freshclam and get this:
```

ERROR: Please edit the example config file /usr/local/etc/freshclam.conf.
ERROR: Please edit the example config file /usr/local/etc/clamd.conf.
ERROR: Can't parse the config file /usr/local/etc/clamd.conf
```

---

### Post by Monicker on 2008-05-04
Are you SURE you uninstalled everything from the source version???  Looks like you have a mix of stuff on your system now.  Follow the instructions in the source package for uninstalling it.

---

### Post by Kognit on 2008-05-05
i did ```
sudo dpkg-reconfigure clamav-base
``` and works fine. Thanks for your help. 
The link that you wrote was fine  but for me (as new in linux) too complicated for now.

Thanks for all the help and time

---

