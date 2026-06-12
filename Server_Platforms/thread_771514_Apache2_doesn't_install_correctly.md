---
title: "Apache2 doesn't install correctly"
date: 2008-04-27
forum: Server Platforms
---

### Post by markskerr on 2008-04-27
I am trying to install Apache2 using the synaptic package manager. It is not
installing. After Synaptic finishes I cannot find any trace of Apache on my system. I am of course running 8.04. I did not have this problem in 7.10. I should have an /usr/local/apache2 directory, but I don't

Thanks. 

I know this is not the right forum, but I cannot find the new post link anywhere in the development/programming forum.

mark

---

### Post by Oldsoldier2003 on 2008-04-28
> **markskerr said:**
> I am trying to install Apache2 using the synaptic package manager. It is not
installing. After Synaptic finishes I cannot find any trace of Apache on my system. I am of course running 8.04. I did not have this problem in 7.10. I should have an /usr/local/apache2 directory, but I don't

Thanks. 

I know this is not the right forum, but I cannot find the new post link anywhere in the development/programming forum.

mark

Are you getting any error messages when you install or attempt to install?

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install apache2
```

---

### Post by jpeddicord on 2008-04-28
Moved back out to Server Platforms. :)

---

