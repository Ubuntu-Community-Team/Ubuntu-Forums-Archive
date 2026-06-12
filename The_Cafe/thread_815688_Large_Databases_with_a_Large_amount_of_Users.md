---
title: "Large Databases with a Large amount of Users"
date: 2008-06-01
forum: The Cafe
---

### Post by Black Mage on 2008-06-01
This is just a random questions but do large databases, such as Facebook, create a table for each user?

---

### Post by Mateo on 2008-06-01
Without having access to their database you can't say for certain.   But almost certainly the answer is no.  A database with millions of tables is a horribly, horribly designed database.  Presumably they have a master user table and all the other stuff hangs off of that.

---

