---
title: "Breezy Badger: How do I execute a script on startup?"
date: 2007-07-05
forum: Server Platforms
---

### Post by CzarAlex on 2007-07-05
Where can I specify a script or two to be run when my system boots up? On newer versions of ubuntu, its something like like rc.local.

What about Breezy Badger? I don't have an rc.local file in /etc/

---

### Post by meatpan on 2007-07-05
The general steps are going to be:

o Create a suitable startup script
o  Add the script to the directory /etc/init.d
o  run the command update-rc.d, with appropriate options


There are quite a few details to know, but the process is still pretty straight forward.

Check out /etc/init.d/README for a nice overview.  Also, you might find this overview helpful: [http://www.debianadmin.com/manage-linux-init-or-startup-scripts.html](http://www.debianadmin.com/manage-linux-init-or-startup-scripts.html)

---

### Post by CzarAlex on 2007-07-05
Actually, I was planning on a bash script. Thanks for the info. I`ll read up on that right away.

---

