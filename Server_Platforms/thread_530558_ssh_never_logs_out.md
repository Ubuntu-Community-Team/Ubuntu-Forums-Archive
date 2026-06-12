---
title: "ssh never logs out"
date: 2007-08-20
forum: Server Platforms
---

### Post by rbprogrammer on 2007-08-20
i can ssh into my server without a problem.  the only issue i have is that last night i forgot to [FONT="Courier New"]exit[/FONT] from the connection.  so this morning i was still connected.  where can i change it so that after about an hour of inactivity, the connection is automatically closed.

i tried looking in [FONT="Courier New"]/etc/ssh/sshd_config[/FONT] and the only thing that i would consider would fix this is the line:
```
LoginGraceTime 120
```
but clearly it has a value but wont disconnect, so i dont think that line helps me..

anyone know how to change this??

---

### Post by Mr. C. on 2007-08-20
LoginGraceTime is the length of time sshd will wait for you to login.

Search for TMOUT in man bash

MrC

---

