---
title: "totem upgrade 404"
date: 2006-08-02
forum: Repositories &amp; Backports
---

### Post by smpolymen on 2006-08-02
I did a fresh install of dapper and am getting the following with the updates:

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/libtotem-plparser1_1.4.3-0ubuntu1_i386.deb
  404 Not Found [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-gstreamer_1.4.3-0ubuntu1_i386.deb
  404 Not Found [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem_1.4.3-0ubuntu1_all.deb
  404 Not Found [IP: 146.137.96.7 80]



```
opening the url in firefox shows 1.4.1 and 1.5.90 but no 1.4.3 but this is what synaptic is telling me to get

doing sudo apt-get update or clicking check doesn't fix it.

--EDIT
Ok. problem solved... just remove the us. in the urls.

---

### Post by N8MAN1068 on 2006-08-02
I'm trying to run the 6.06 upgrade from 5.10, and also have the same problems, even thought totem isn't currently installed.
I installed totem+co, and still have the same error.

---

### Post by Hillbilly Tilley on 2006-08-02
I have the same problem.  I did not understand the solution.  Can someone explain?

Thanx

---

### Post by bmonkey on 2006-08-02
they havent uploaded the files on the server yet :/

---

### Post by GadgetsGuy on 2006-08-02
I too am getting 404 errors when upgrading my ubuntu

they are the same totem file .... has anybody figured out how to correct this yet??:confused:

---

