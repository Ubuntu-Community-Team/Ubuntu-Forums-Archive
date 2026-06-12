---
title: "sys76 driver problem on kubuntu?"
date: 2012-12-19
forum: System76 Support
---

### Post by poikiloid on 2012-12-19
I installed kubuntu 12.10 64bit on a panp5 sys76 laptop.

I installed the latest sys76 driver deb (3.2.3) from their site, and restarted computer.

When I try to run the sys76 driver app, I get a kdesudo popup asking me to give admin password to run a python script called System76Drivergtk3.py

After entering my password, the dialog goes away, but the usual window i'm used to in regular ubuntu does not come up, so I can't click "Install Drivers" or "Restore system"... What's up with that? Does the driver install/restore just happen invisibly/automatically under Kubuntu? Anyone experienced this? Is there a way to check if the appropriate drivers did indeed install?

Thank you.

---

### Post by maxvon91 on 2012-12-23
Run konsole and type "sudo system76-driver -d".  You can also type "system76-driver -h" for help.

---

### Post by verdia13 on 2013-04-24
> **maxvon91 said:**
> Run konsole and type "sudo system76-driver -d".  You can also type "system76-driver -h" for help.


Thank you this worked great. Everything works now :-)

---

### Post by FrozenFOXX on 2013-06-19
> **maxvon91 said:**
> Run konsole and type "sudo system76-driver -d".  You can also type "system76-driver -h" for help.

Thank you so much, this definitely helps me as well.

---

