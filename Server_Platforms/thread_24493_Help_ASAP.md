---
title: "Help ASAP"
date: 2005-04-07
forum: Server Platforms
---

### Post by Nez7165 on 2005-04-07
Im trying to connect to a windows remote desktop how do i do this. Thanks

---

### Post by lao_V on 2005-04-07
You need to use [SMB]("http://www.samba.org")

---

### Post by pug on 2005-04-07
I think he meant the "remote control software" e.g. he's trying to connect to the so called terminal server on his windows machine. What you want to do is probably:

apt-get install grdesktop rdesktop

which should get you a terminal server client.

-pug

---

