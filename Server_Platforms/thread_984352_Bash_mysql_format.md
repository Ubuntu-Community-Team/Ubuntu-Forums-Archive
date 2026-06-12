---
title: "Bash mysql format"
date: 2008-11-16
forum: Server Platforms
---

### Post by chrisfrog on 2008-11-16
Hey,

I am writing a program where I would like to get information from mysql database.

It is a menu driven program and I would like to create a menu from mysql query.
+----------------+
| servername |
+----------------+
| localhost |
| Server-1 |
| Server-2 |
+----------------+

These will have the IP address of each server in the table to.

The question is how do I format each one of the rows in to a string so that I can do (to create a menu etc):

echo "Server-1"

and then I will used read to check which server was selected. 

Many Thanks

---

### Post by chrisfrog on 2008-11-16
Ok,

Just worked out how to get them in a nice list using -ss.

But how can I get each member in the list to become a $string so that I can use it else where?

Many Thanks

---

