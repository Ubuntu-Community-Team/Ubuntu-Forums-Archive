---
title: "[SOLVED] AWStats Set Up Error"
date: 2008-04-18
forum: Server Platforms
---

### Post by wormser on 2008-04-18
> Error: Couldn't open server log file "/var/log/apache2/access.log" : Permission deniedI get the above error when setting up AWStats.  I changed the permissions to 777 and the error is still there.  I suspect the owner needs to be changed.  Who should own the file, which group and what should the permissions be?

> -rwxrwxrwx  1 root adm  1380873 2008-04-18 16:50 access.logThanks

---

### Post by conjur3r on 2008-04-19
What's the permissions on the /var/log/apache2 folder?

---

### Post by wormser on 2008-04-19
ls -lad /var/log/apache2
> drwxr-x--- 2 root adm 4096 2008-04-13 18:47 /var/log/apache2

---

### Post by conjur3r on 2008-04-19
That is saying do not allow anyone (except root and anyone in the adm group) to traverse down this folder.  This is probably why your awstats generation was failing (unless of course you ran it as root).  Allow anyone to traverse down with the following:

# sudo chmod 755 /var/log/apache2

---

### Post by wormser on 2008-04-20
> **conjur3r said:**
> That is saying do not allow anyone (except root and anyone in the adm group) to traverse down this folder.  This is probably why your awstats generation was failing (unless of course you ran it as root).  Allow anyone to traverse down with the following:

# sudo chmod 755 /var/log/apache2

That did it!  Thanks.

---

