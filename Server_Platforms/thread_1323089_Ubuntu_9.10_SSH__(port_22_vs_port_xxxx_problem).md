---
title: "Ubuntu 9.10 SSH  (port 22 vs port xxxx problem)"
date: 2009-11-11
forum: Server Platforms
---

### Post by nhanquy on 2009-11-11
[SIZE=3]
After upgrading to Ubuntu 9.10, besides wireless problem, now I have found a problem with SSH.

The Ubuntu 9.10 box can not make a connection if the server,in my case the box is running Ubuntu 9.04, is using a different port address ([/SIZE][FONT=Arial Black][SIZE=3]not the default 22[/SIZE][/FONT][SIZE=3]).  Change back to port 22, anything is working as expected!

Any idea out there?

Thanks![/SIZE]

---

### Post by DJ_Max on 2009-11-11
How are you making the connection?

---

### Post by wirelessmonkey on 2009-11-11
Are you specifying the port on the client??  ssh -p 12345 user@server, where 12345 is the port ssh server is running on....

---

### Post by nhanquy on 2009-11-11
> **DJ_Max said:**
> How are you making the connection?

Just simple as:
>  ssh -vvv  -p XXXX login@machine

It looks like 9.10 did not pass the port info to the server.

Problem seems similiar to :

[http://ubuntuforums.org/showthread.php?t=893109](http://ubuntuforums.org/showthread.php?t=893109)

---

### Post by wirelessmonkey on 2009-11-13
Is the port above 1024?

---

