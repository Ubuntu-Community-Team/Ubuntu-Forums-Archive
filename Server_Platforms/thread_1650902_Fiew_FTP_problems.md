---
title: "Fiew FTP problems"
date: 2010-12-22
forum: Server Platforms
---

### Post by Eleeist on 2010-12-22
When I try to upload files via FTP to a specific folder (/var/www/myfolder/) I get the message 550 permission is denied. I set CHMOD 777 for this folder (I had to do this via SSH cause I was not allowed to do this in FileZilla) but this does not help.

Also, I cannot delete files - also 550 permission denied.

Any advice?

---

### Post by arrrghhh on 2010-12-22
Who owns /var/www/myfolder/?  chmod 777 should take care of any ownership issues however....

Have you tried restarting the FTP server after making that chmod change?

---

### Post by Eleeist on 2010-12-22
Well, it has CHMOD 777...

How do I check who owns the folder?

---

### Post by arrrghhh on 2010-12-22
```
ls -la
```

---

### Post by tad1073 on 2010-12-22
chmod 777 is not good for that folder. a better implimentation would be chown -R username:groupname /var/www/myfolder/, then chmod -R 766 /var/www/myfolder/

---

### Post by tad1073 on 2010-12-22
> **arrrghhh said:**
> Who owns /var/www/myfolder/?  chmod 777 should take care of any ownership issues however....

Have you tried restarting the FTP server after making that chmod change?

only problem with 777 is it make it world writeable and executable which could cause a potential security risk.

---

