---
title: "CIFS server to server on Lucid"
date: 2010-11-18
forum: Server Platforms
---

### Post by bibble235 on 2010-11-18
Hi,

We are experiencing problems copying files from a server to server where the machine issuing the copy is a 32-bit lucid and the mount drive is a 64-bit server.

I have no other information but the md5's are consistently different after doing a copy. The files are > 8mb.

I cam provide logs if someone wants.

Iain

---

### Post by SeijiSensei on 2010-11-18
Do you get the same results with other methods of copying like rsync, scp, or NFS mounts?

---

### Post by bibble235 on 2010-11-18
No, should have mentioned this. Also rebooting the server fixes the problem for a while

---

