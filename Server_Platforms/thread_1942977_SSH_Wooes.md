---
title: "SSH Wooes"
date: 2012-03-18
forum: Server Platforms
---

### Post by niranjan_rao on 2012-03-18
I have a 64bit ubuntu 11.10 server which was working fine. Yesterday, we switched it from dhcp to static address mode. Since then SSH to server seems to be acting up.


If I ssh to server, I am able to login (passwordless login) and do get prompt. After than keyboard stops working and after certain time (don't know the duration) I get broken pipe error.

Both on client log and server logs, there seems to be nothing abnormal. I tried ssh -v, but it effectively stopped logging after I got the shell 
prompt.

The server otherwise seems to be ok and web apps its supposed to serve are working as usual.


Any thoughts, ideas are greatly appriciated.

---

