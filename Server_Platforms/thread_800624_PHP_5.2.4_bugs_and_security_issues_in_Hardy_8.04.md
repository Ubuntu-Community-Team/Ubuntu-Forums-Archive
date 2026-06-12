---
title: "PHP 5.2.4 bugs and security issues in Hardy 8.04"
date: 2008-05-20
forum: Server Platforms
---

### Post by microgluf on 2008-05-20
Hi,

PHP 5.2.4 has numerous bugs, such as security issues and one that concerns me most is [Bug#42548]("http://bugs.php.net/42548") not allowing Mysql Stored Procedures to return results.

When is this going to be addressed, is there a plan to upgrade to 5.2.6 in the very near future ? :confused:

For now I will have to downgrade the servers back to an older release unless someone has a better idea ??

Compiling PHP is not an option at this time, unless there is an easy way to do so without breaking the Ubuntu dependencies... and having to recompile most of the PHP modules ??  Suggestions are welcomed.

I thank all the community for making Ubuntu one of the best distro available. It's a shame that, sometimes, little glitches creap-up and make a version unusable.

Cheers to all.
Pierre

---

### Post by microgluf on 2008-05-22
Meaculpa...

I just realised that PHP 5.2.6 was much more recent than I had in mind....  doh!

---

### Post by dugh on 2008-05-30
Yeah our university now basically shuts down computers not running at least PHP 5.2.6.

Is there a way to install this in Ubuntu Hardy without have to go the compile route.

---

### Post by comandrei on 2008-07-06
You've probably fixed your problem, but here's a possible solution:
[http://dotdeb.org/](http://dotdeb.org/)

---

