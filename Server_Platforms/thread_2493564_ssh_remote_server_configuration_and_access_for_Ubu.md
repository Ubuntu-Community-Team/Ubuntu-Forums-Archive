---
title: "ssh remote server configuration and access for Ubuntu server running on Raspberry pi"
date: 2023-12-19
forum: Server Platforms
---

### Post by ujjwalrathod007 on 2023-12-19
Hi,
I have a Ubuntu sever running on Raspberry Pi and want to access it via ssh from remote location.
For that I tried to use ssh remote forwarding method.

First, I registered my DDNS with DDNS provider and opened a port from the router setup. 

BTW, my question is that while it worked yesterday and now it is not working anymore. Can someone has an idea what could have gone wrong?

```
ssh -L portin:ubuntu@mydnsname:portout ubuntu@RPI_LOCAL_STATIC_IP
```

---

### Post by TheFu on 2023-12-19
try
```
ssh -vvvvv  ubuntu@RPI_LOCAL_STATIC_IP
```

That will dump lots of debug output. Look for where the connection isn't made or where the authentication attempted fails.

---

### Post by ujjwalrathod007 on 2024-01-08
Thanks, I had found that the required number of MTU was incorrect. Found on internet how to reduce the MTU, and finally when I set it to 1200 it connected.

---

