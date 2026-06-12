---
title: "inetd"
date: 2006-09-12
forum: Server Platforms
---

### Post by debryro on 2006-09-12
I am trying to fin the config file for inetd, inetd.conf, but it does not seem to be there in the standard install of the server code. Can anyone tell me where it is?

---

### Post by WagnerVaz on 2006-09-12
in my Ubuntu box it is in /etc/inetd.conf

---

### Post by debryro on 2006-09-12
It's not there! I have already looked in all of the obvious places.

---

### Post by pjbgravely on 2006-09-21
Use xinetd instead. It is the same but more secure. If the config file is blank then you haven't installed anything that it runs yet.

Paul

---

### Post by Iowan on 2006-09-21
> **WagnerVaz said:**
> in my Ubuntu box it is in /etc/inetd.conf
Same here... although my server is still a Breezy box.

---

