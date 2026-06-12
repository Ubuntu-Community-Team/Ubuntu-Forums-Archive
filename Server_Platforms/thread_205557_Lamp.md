---
title: "Lamp"
date: 2006-06-28
forum: Server Platforms
---

### Post by Koybe on 2006-06-28
Hi

I've set up my dapper with apache2, php5 and mysql5, everything works fine.

But now i just want to install bbclone, but when i apt-get it, it wants to remove php5 and reinstalled php4 instead. How can i tell him that's it's ok with php5?

```
sudo apt-get install bbclone
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libapache2-mod-php4 libzzip-0-12 php4 php4-common
Suggested packages:
  php-pear
The following packages will be REMOVED:
  libapache2-mod-php5 php5-mysql php5-mysqli
The following NEW packages will be installed:
  bbclone libapache2-mod-php4 libzzip-0-12 php4 php4-common
0 upgraded, 5 newly installed, 3 to remove and 0 not upgraded.
Need to get 2434kB of archives.
After unpacking 2499kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort. 
```

Thank you

---

### Post by Maggot on 2006-06-28
If you don't have any other programs wanting php5 already and won't ever need it....yes.

---

### Post by Koybe on 2006-06-28
What if i want to use php5 for my own use then?

---

### Post by Maggot on 2006-06-28
Then no :)  ... at least I don't believe so.

Can bbclone use php5? The package may have been compiled with php4, if so, look to see if there's a package for php5 or manually compile (install) it (bbclone).

---

### Post by Koybe on 2006-06-29
OK Thank you

---

