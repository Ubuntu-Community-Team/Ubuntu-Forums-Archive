---
title: "ssh: connection to host port: 22: Connection timed out lost connection"
date: 2007-03-13
forum: Server Platforms
---

### Post by cocotu on 2007-03-13
We have 2 linux boxes on 2 different floors.  I'm able to transfer files from Box A to Box B, but not from box B to box A.  When I try to transfer files from B to A I get:

ssh: connect to host 10.0.0.1 port 22: Connection timed out lost connection

What might be the problem here??  I'm able to ping from both machines: A to B and B to A with no errors.

Thanks

---

### Post by ujeezy on 2007-03-13
Is the OpenSSH server running on B?

---

### Post by cocotu on 2007-03-13
Yes, but it seems to be a problem with firestarter. Port 22 was blocked.

thanks

---

