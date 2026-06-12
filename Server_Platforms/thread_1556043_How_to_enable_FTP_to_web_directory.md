---
title: "How to enable FTP to web directory"
date: 2010-08-18
forum: Server Platforms
---

### Post by mlinux on 2010-08-18
Currently I am using webmin to upload web design to the local apache server within the same local network. FTP can only upload to my own account only and no access to www directory. How can I enable FTP to access it? BTW it is on Ubuntu 10.04.

---

### Post by terazen on 2010-08-19
Maybe create a link in your home folder to the /var/www directory?
```
ln -s /var/www ~/to-var-www
```

Does your user account have permissions to /var/www?

---

### Post by mlinux on 2010-08-19
> **terazen said:**
> Maybe create a link in your home folder to the /var/www directory?
```
ln -s /var/www ~/to-var-www
```

Does your user account have permissions to /var/www?

Already set www to 664. When I login using putty, I can cd to /var/www but not SFTP via SSH port 22 from "coffeecup".

Edit:
644 cause problem for the webpage so revert back to 755 and now I can use FTP32 to access the www but not the sub. I will change the sub to the same and proceed from there. coffeecup always point to the home/user directory. I will stick with the FTP32 for the time being until found the setting for coffeecup.

---

### Post by Lars Noodén on 2010-08-23
> **mlinux said:**
> Already set www to 664. When I login using putty, I can cd to /var/www but not SFTP via SSH port 22 from "coffeecup".

Edit:
644 cause problem for the webpage so revert back to 755 and now I can use FTP32 to access the www but not the sub. I will change the sub to the same and proceed from there. coffeecup always point to the home/user directory. I will stick with the FTP32 for the time being until found the setting for coffeecup.

Can you get to /var/www using the SFTP client?

For permissions, the directories should be 755 (or 775) the files should be 644 (or 664).

---

