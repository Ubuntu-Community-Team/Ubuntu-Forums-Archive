---
title: "Cannot connect to localhost through SSL"
date: 2011-09-05
forum: Server Platforms
---

### Post by Magnesium on 2011-09-05
Hi folks,

Very puzzling and important problem. Here's the summary:
Using wget, curl, and openssl s_client:

[LIST]
[*]Server can successfully connect to remote https address
[*]Remote client can successfully connect to server
[*]Server **cannot** connect to itself
[/LIST]

For the last entry, I think openssl gives the most informative error:
```
4321:error:140770FC:SSL routines:SSL23_GET_SERVER_HELLO:unknown protocol:s23_clnt.c:601:
```

*More info*
I was running this server on 32-bit arch originally. I reinstalled on a new 64-bit arch platform. Previously there were no SSL problems. I am using a signed cert from comodo...but also tried using a self-signed cert created on the new installation...no luck. Even directly copying the /etc/ssl and /etc/apache2 dirs from my backup and restarting has done nothing.

Help please!

---

### Post by Magnesium on 2011-09-05
Well as soon as you finally get around to asking, you figure it out. I tried openssl s_client to my IP address instead of my domain name, and....it worked! I added the line 

```
[my IP]   [my domain name]
```

to /etc/hosts, and everything is fixed. Funny thing is, that line was not their in the previous install either, yet it worked. Oh well, problem solved.

---

