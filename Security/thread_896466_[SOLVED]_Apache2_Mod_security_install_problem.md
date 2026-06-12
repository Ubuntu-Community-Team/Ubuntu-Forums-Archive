---
title: "[SOLVED] Apache2 Mod_security install problem"
date: 2008-08-21
forum: Security
---

### Post by terry123b99 on 2008-08-21
The Error

> 
root@terry-laptop:~# sudo apt-get install libapache2-mod-security
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


All am trying to do is install the mod_security, but get stuck with above error.

am using version 8.04 Hardy Heron and the latest version of apache2

any help would be appreciated

---

### Post by cdenley on 2008-08-21
Is synaptic running?
```

sudo lsof /var/lib/dpkg/*

```
Once you close synaptic, you will discover that libapache2-mod-security does not exist in hardy.

---

### Post by terry123b99 on 2008-08-21
Cheers for the info, have found an alternative to mod_security now.

---

### Post by chamkaran on 2008-09-04
Hi there
I am also having the same problem and getting the error during installatin of mod-security.
the error is E: could't find the package mod-security
the command i am using is sudo apt-get install mod-security.
I also download the package and tried with dpkg as
sudo dpkg -i libapache2-mod-security2
and got the error againg.
Yours help will be appreciated.

---

### Post by cdenley on 2008-09-04
> **chamkaran said:**
> Hi there
I am also having the same problem and getting the error during installatin of mod-security.
the error is E: could't find the package mod-security
the command i am using is sudo apt-get install mod-security.
I also download the package and tried with dpkg as
sudo dpkg -i libapache2-mod-security2
and got the error againg.
Yours help will be appreciated.

Try reading my post
> 
libapache2-mod-security does not exist in hardy


---

### Post by 2smooth on 2008-09-05
> **terry123b99 said:**
> Cheers for the info, have found an alternative to mod_security now.

And that is?

---

### Post by 2smooth on 2008-09-05
> **cdenley said:**
> Is synaptic running?
```

sudo lsof /var/lib/dpkg/*

```
Once you close synaptic, you will discover that libapache2-mod-security does not exist in hardy.

What can you use in place of mod_security?

I mainly use it for stopping spam?

---

