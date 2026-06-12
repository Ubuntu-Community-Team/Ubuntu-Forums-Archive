---
title: "roaming users linux"
date: 2007-03-28
forum: Server Platforms
---

### Post by eltidi on 2007-03-28
Hi,

I haven't yet find a way to emulate windows roaming profiles using linux tools.
The thing is that using nfs you can have centralized user login and home directories but the problem comes when you have laptop users that come and go. I need a tool to sync those laptops so i can backup the data they use when they travel. Is there any standard way to do this or do I have to hack myself a solution.

Many thanks

---

### Post by Frosty Cold Drink on 2007-03-28
You can use AFS or something similar with caching enabled. Check it out at [http://openafs.org/](http://openafs.org/) . You will, of course, need to cache whatever you use for authentication and directory information, such as LDAP or NIS.

---

### Post by eltidi on 2007-03-29
> **Frosty Cold Drink said:**
> You can use AFS or something similar with caching enabled. Check it out at [http://openafs.org/](http://openafs.org/) . You will, of course, need to cache whatever you use for authentication and directory information, such as LDAP or NIS.

Hi, I have heard that afs gives admin a lot of headaches, is that still true or is it an old story?

---

### Post by Frosty Cold Drink on 2007-03-29
> **eltidi said:**
> Hi, I have heard that afs gives admin a lot of headaches, is that still true or is it an old story?

I couldn't say. I've never had a problem with it.

---

