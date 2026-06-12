---
title: "Invalid user apache"
date: 2009-04-27
forum: Server Platforms
---

### Post by ubila on 2009-04-27
Hi, 
Im trying to change the ownership of my svn folder to apache 

```
sudo chown -R apache:apache /var/lib/svn/repo1
```This is returning the error:

chown: invalid user: 'apache:apache' 

---

I have apache2 installed and up to date.
Running ubuntu server

Any help would be appreciated :)
Cheers!

---

### Post by TuckLive on 2009-04-27
Try:

```
sudo chown -R apache /var/lib/svn/repo1
```

Just noticed my error as it's www-data.  Apologies

---

### Post by sahabcse on 2009-04-27
Hi

In ubunut apache runs as the user www-data. Not be the user apache

---

### Post by ubila on 2009-04-27
> **sahabcse said:**
> Hi

In ubunut apache runs as the user www-data. Not be the user apache

Hi thanks that worked :)
```
sudo chown -R www-data /var/lib/svn/repo1
```

Thanks again :)

---

