---
title: "Error: Cannot open NBD: No such file or directory"
date: 2012-06-27
forum: Server Platforms
---

### Post by KenSharp on 2012-06-27
I have exported an NBD on another machine and am trying to connect to it from a server machine, but
> #nbd-client *hostname* 2000 /dev/sdb
Error: Cannot open NBD: No such file or directory
Please ensure the 'nbd' module is loaded.

Where on Earth do I get the nbd module from and why isn't it included with the nbd-client package **or** what am I missing?

---

