---
title: "Do not have permission to log into my VMWare server..."
date: 2009-02-19
forum: Virtualisation
---

### Post by beastrace91 on 2009-02-19
So I just got VMWare sever 2.0 all install but when I go to [http://localhost:8222/ui/#](http://localhost:8222/ui/#) and enter my normal login name and password it tells me I do not have permission to log into the server... what am I doing wrong?...

Thanks,
~Jeff

---

### Post by bodhi.zazen on 2009-02-19
Please see the vmware how to's posted in the sticky at the top of these forums, it is a sticky for a reason :twisted:

During the installation, you need to set a user as the administrator.

If you did not, hte default user is root, which is less then ideal ...

You have two options.

I advise you re-run the install script and set your user (rather then root) as admin.

The other option is to temporarily set a root password, log in as root, add your user as an administrator, then lock the root account again. This can cause breakage and so go with #1.

---

### Post by equbay on 2010-01-13
> **bodhi.zazen said:**
> Please see the vmware how to's posted in the sticky at the top of these forums, it is a sticky for a reason :twisted:

During the installation, you need to set a user as the administrator.

If you did not, hte default user is root, which is less then ideal ...

You have two options.

I advise you re-run the install script and set your user (rather then root) as admin.

The other option is to temporarily set a root password, log in as root, add your user as an administrator, then lock the root account again. This can cause breakage and so go with #1.

A third option is to edit /etc/vmware/hostd/autherization.xml and change root in
        **<ACEDataUser>root</ACEDataUser>**
line to your account username. 

Save and restart vmware.

Equbay

---

### Post by beastrace91 on 2010-01-13
Thread resurrection much? Also my long-term solution was to install Virtual Box as it does not suffer from silly issues like this ;)

~Jeff

---

### Post by bodhi.zazen on 2010-01-13
> **equbay said:**
> A third option is to edit /etc/vmware/hostd/autherization.xml and change root in
        **<ACEDataUser>root</ACEDataUser>**
line to your account username. 

Save and restart vmware.

Equbay

That works as well, thank you for adding the suggestion. Hopefully it will help others who come across this old thread.

---

