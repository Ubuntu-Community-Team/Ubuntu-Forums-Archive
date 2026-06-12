---
title: "Axigen"
date: 2006-01-16
forum: Server Platforms
---

### Post by Cubicegg on 2006-01-16
Hi List,

I'm trying to figure out how to start AXIGEN during the boot process or at least during login, does anybody know how to do this?

thanks James

---

### Post by Glut on 2006-01-18
1. Create a script to run axigen
2. Copy the script to /etc/init.d, check that it runs
3. update-rc.d *scriptname* defaults

You could also install rcconf and do it that way.

---

