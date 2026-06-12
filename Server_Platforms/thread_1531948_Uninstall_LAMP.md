---
title: "Uninstall LAMP"
date: 2010-07-15
forum: Server Platforms
---

### Post by 1Nick1 on 2010-07-15
I do not know if this is the right section but anyway..
I need to uninstall Lamp from my Ubuntu 10.04 OS.
I just need to commands etc as I am rather noob at Ubuntu.
I will be installing it again I just have come across several problems.  Thanks.

---

### Post by WernerCD on 2010-07-16
> **1Nick1 said:**
> I do not know if this is the right section but anyway..
I need to uninstall Lamp from my Ubuntu 10.04 OS.
I just need to commands etc as I am rather noob at Ubuntu.
I will be installing it again I just have come across several problems.  Thanks.

sudo tasksel remove lamp

or something close to that

---

### Post by richardjh on 2010-07-20
It really depends on how it was installed.
To check it was installed using tasksel, you can find out by running

```
tasksel --list-tasks | grep lamp

```If the packages were installed in such a way that tasksel can remove them you will see

```
i lamp-server    LAMP server
```The i at the beginning means installed. (If it is u then it is not installed using a package manager.)

Assuming though that this is the case use

```
tasksel remove lamp-server
```to remove it.

Post back if you get problems or errors.

---

