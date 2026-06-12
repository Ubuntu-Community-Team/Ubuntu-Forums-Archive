---
title: "Security Problem on Ubuntu v12.04_LTS-server (64BITS)"
date: 2013-03-14
forum: Server Platforms
---

### Post by sebounetino on 2013-03-14
Hello,

I'm installing a remote hosted server Ubuntu v12.04_LTS-server (64BITS) and my problem is that there ares "robots" (I'm not sure) which send requests all the time to my open ports, this the case for example for my websocket server (JWebSocket).

- For my website, I have a haproxy Which forwards the request to the Ws Server on the same machine. It Works well. HaProxy is the only element connected to the Websocket server.
- There are queries each second coming from the localhost(127.0.0.1) source address. These queries can"t coming from haproxy cos the problem is here when haproxy is down. I think they comes from outside, but I dont know How they appears with the locahost address source in the logs !!!...

If I block in IPtables with the 127.0.0.1 address on the good port, it block all, and my website does not work either...

How I can secure my server to not have this kind of stupid problem !!!

Please help me

Attachement : the logs

Sorry for my approximative english ...

---

### Post by thnewguy on 2013-03-14
Why do you think the connection is coming from outside when the IP address is for your local host? Are you quite sure the connection really isn't coming from your own machine?

---

### Post by sebounetino on 2013-03-15
Sorry I was a little bit exhausted last night and In fact the problem disappeared when haproxy was down... In fact, I found the problem, it was from my Haproxy wich send request each second to my backend servers for the load balancing (health check). I just forgotten to disable it for my Websocket server.

Thanks for help...

---

