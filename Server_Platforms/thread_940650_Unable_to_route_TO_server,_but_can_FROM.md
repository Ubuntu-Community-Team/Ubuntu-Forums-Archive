---
title: "Unable to route TO server, but can FROM"
date: 2008-10-07
forum: Server Platforms
---

### Post by drven1005 on 2008-10-07
I'm having a very strange problem and was hoping that someone on here might possibly be able to shed some light on the issue. 

I just installed 6.06 on a new server.  From the server, I'm able to ping anything on the network.  However, if I try to ping the server from a host that I did not try to ping from the server, they time out.  

Example:

Server can ping A.  A can ping Server.  B can NOT ping Server until AFTER Server pings B.

I don't understand whats happening.  From my workstation for example, I'm not able to ssh in until I after I ping myself from the server.

Does anyone have any ideas?

---

### Post by drven1005 on 2008-10-07
It should be noted that even though I'm eventually able to pass packets in both directions after first sending them from the server, in time they start to fail again.

For example, I was logged in via ssh from my work station and it just stops responding after some time.  I was not inactive.  I was still able to ssh in from only one other host on my network (all others were unable to route to the new server at this point), I pinged my workstation and my ssh session resumed. 

I've never seen anything like this before.

---

### Post by drven1005 on 2008-10-07
It seems that upgrading to 8.04 fixed this.

---

