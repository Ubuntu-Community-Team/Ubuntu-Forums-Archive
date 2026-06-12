---
title: "a question about windows linux and apache"
date: 2009-11-13
forum: Server Platforms
---

### Post by rongngusay on 2009-11-13
is there any way that windows and ubuntu can use same partition with full control 
so: i setup LAMP on ubuntu an WAMP on windows and all i want is
WAMP an LAMP use one root directory

can i do that and how ?

thanks for read !!!

---

### Post by Vegan on 2009-11-13
Use an old machine for Linux and set that machine as you LAMP stack as Windows is useless in my opinion as a web appliance.

---

### Post by lykwydchykyn on 2009-11-13
Sure, basically:

 - Set up a common partition that either OS can mount.

 - Set the webroot in both of them to a directory on that partition.
 
Do you need help with the particulars of either of those processes?

---

