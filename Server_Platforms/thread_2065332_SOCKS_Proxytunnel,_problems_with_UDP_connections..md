---
title: "SOCKS Proxy/tunnel, problems with UDP connections."
date: 2012-10-01
forum: Server Platforms
---

### Post by Reverse821 on 2012-10-01
Hello there community. I'm not entirely sure if this is the right subboard to post this on, but here goes anyway:
I'm currently trying to get me a proper SOCKS proxy / SSH tunnel working, in order to be able to use any TCP / UDP services via my servers network connection. It is currently running Ubuntu 12.04 LTS x86 and I tried setting up a SOCKS proxy via danted / sockd 1.3.2 and sshd with putty on windows. I then used proxify to use the proxy on several applications. This works for most services, at least via TCP. As soon as an application like for example Teamspeak 3 opens up its separate port for the actual  connection, the client transmits data, however doesn't receive anything from the proxy.

Looks like this on the sockd log:
> 
Oct  1 21:54:58 (1349121298.158788) sockd[26212]: info: pass(1): tcp/connect ]:    0 -> xxx.xxx.xxx.xxx.50214 85.214.xxx.xxx.9080-> 0, 0 -> 85.214.xxx.xxx.50214 8   5.214.xxx.xxx.41144 -> 0:remote peer error (Connection refused).  Session durat   ion:0s
Oct  1 21:54:58 (1349121298.158980) sockd[26212]: info: pass(1):tcp/accept ]: 0    -> 132.231.xxx.xxx.5021485.214.xxx.xxx.9080 -> 0: remote peer error(Connection refused).  Session duration: 0s


Is there a limitation with SOCKS proxies / tunneling here that I am missing? Is there any way i can get those services to work? Or is it just a simple configuration problem on server/client side?

---

