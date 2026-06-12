---
title: "How to change disk permissions permanently ?"
date: 2009-12-16
forum: Virtualisation
---

### Post by Devport on 2009-12-16
I am using Virtualbox to run Windows off a native partition.

Therefore I need to change the permissions of a partition

chmod 664 /dev/sda3

but the permissions get reset during a restart. How can I make the permission change persist ?

Edit :

Solution is to create a udev rule

---

