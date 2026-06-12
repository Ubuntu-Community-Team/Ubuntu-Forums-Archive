---
title: "How to add a new service???"
date: 2005-07-16
forum: Server Platforms
---

### Post by indispus on 2005-07-16
I've just install DCD (Direct Connect Deamon), and it's working fine. I start it with "dcd" in the terminal. But... i must do that every time i restart my system.

How can i make DCD to start as a service?


P.S.: I'm just another noob :(

---

### Post by alastair on 2005-07-16
There's a "skeleton" service script in /etc/init.d.

/etc/init.d/skeleton

Copy it to, say , dcd :

cp -p /etc/init.d/skeleton /etc/init.d/dcd

and then edit "/etc/init.d/dcd" to start up the daemon etc.

Then add to the services per runlevel using "update-rc.d" (man update-rc.d).

---

### Post by indispus on 2005-07-17
Thank you man... with your help i did it :roll:

---

