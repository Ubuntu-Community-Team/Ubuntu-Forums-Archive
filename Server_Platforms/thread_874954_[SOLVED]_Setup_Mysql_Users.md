---
title: "[SOLVED] Setup Mysql Users"
date: 2008-07-30
forum: Server Platforms
---

### Post by CrusaderAD on 2008-07-30
How do I setup a sql user to access one database? Also, how do I set it up to where one user can access the data from different machines (IP addresses)?

---

### Post by Fire_Chief on 2008-07-30
To allow access to a database, you create a sql user account and then assign it permissions to that specific database (ro, rw, create, delete, etc.). This is easily done through a GUI admin tool such as MySQL Administrator or something similar.

Allowing access over the network should be allowed by default. I'm not sure exactly what you are asking here. Could you be more specific?

Cheers!

---

### Post by CrusaderAD on 2008-07-30
Thanks for the response... I was logging into MySql Admin as a generic user, not root. So was wasn't able to change settings. Just had to log in as root. All better! Thanks!

---

