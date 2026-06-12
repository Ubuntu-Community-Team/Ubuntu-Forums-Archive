---
title: "ssh with local keyfile?"
date: 2005-12-04
forum: Server Platforms
---

### Post by maol62 on 2005-12-04
I have installed freenx on my ubuntu pc and when I connect to it from my windows laptop the connection demands that I have imported the keyfile client.id_dsa.key into the freenx client. The keyfile has to manually copied from /var/lib/nxserver/home/.ssh to the client pc by me before importing it. Then everything works like a charm, I have tripple security; ssh which is encrypted, I must have the keyfile imported, and I must have the right password for the user I connect with.
But how do I do to achieve the same security with normal login with ssh? If I ssh 192.168.1.2 then I just have to type the client users password and then Im in. I want the ssh connection to demand the local keyfile at the client side as it does when connecting to the nxserver so no one else than me can log in to the server.

---

### Post by nagilum on 2005-12-04
You can disable password authentication in the server's configfile and put your public key in ~/.ssh/authorized_keys.

---

### Post by maol62 on 2005-12-15
Perfect! Thanks!

---

