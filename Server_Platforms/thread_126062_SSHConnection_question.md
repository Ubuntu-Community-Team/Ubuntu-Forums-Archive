---
title: "SSH/Connection question"
date: 2006-02-05
forum: Server Platforms
---

### Post by LightShear on 2006-02-05
Hey all,

I'm running a Breezy 5.10 server. Among other services, it has SSH. Today, I noticed that on the switch the server is connected to, it (the server's light) had intermittent activity. Basically, it seemed as though the server was processing, stopping, processing, stopping, over and over. It used to do the same thing, sort of, when squid was running, but I disabled that and it stopped; I guess someone was trying to use it? When I close the SSH's port in the router, like I did for squid, the activity to stops. Would it be safe to assume that someone was connected to the SSH port and trying to brute force hack the password?

Network set-up (don't think I was too clear above)
Server -> Switch ->Router ->Internet

If my assumption is correct, is there a way to see where the connection is coming from, if I reopened the port?

Thanks.

---

### Post by joft on 2006-02-05
Hi,

did you have a look at /var/log/auth.log ? There you can see "illegal" stuff logged by sshd ...

---

### Post by LightShear on 2006-02-05
Thanks! Looks like I was right. Someone was trying to every possible generic login known to man (guest, root, admin, apache, linux...)

---

