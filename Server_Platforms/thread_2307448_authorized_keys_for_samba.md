---
title: "authorized_keys for samba?"
date: 2015-12-25
forum: Server Platforms
---

### Post by macho3 on 2015-12-25
I use authorized_keys  to securely ssh  to a machine without having to provide a password. How can I  do the same to remotely mount a samba share? Is there any way to achieve this without installing and configuring cumbersome kerberos and winbind frameworks? Either way, what are the key lines to include in   smb.conf?

---

### Post by matt_symes on 2015-12-25
Thread moved to **Server Platforms**

You may get better help with your query in this forum.

---

### Post by darkod on 2015-12-25
What type is the server and client OS? Samba is usually used to configure a share on linux server to be accessed from windows client. Do you plan to use it this way? Or maybe linux client to linux server?

---

