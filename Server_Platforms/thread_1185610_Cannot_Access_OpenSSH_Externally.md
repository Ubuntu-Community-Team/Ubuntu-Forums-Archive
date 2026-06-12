---
title: "Cannot Access OpenSSH Externally"
date: 2009-06-12
forum: Server Platforms
---

### Post by afawcett on 2009-06-12
I am running an Ubuntu server box on my network, and I installed OpenSSH. I can access it just fine from my local network. I forwarded port 22 to my machine, and preceded to ssh to it using my external ip address. The connection eventually times out. I also checked to see if the port was open with canyouseeme.org, and I got the following message:
[COLOR=green]"Success:[/COLOR] I can see your service on x.x.x.x on port (**22**)
Your ISP is not blocking port 22"

---

### Post by cdenley on 2009-06-12
SSH would only time out if it couldn't establish a connection. If that service says port 22 is open, then it should be establishing a connection. Try running this command from outside your network to verify whether a connection can be established, or post your IP/domain so we can.
```

nc -zv [my domain or IP] 22

```

---

### Post by afawcett on 2009-06-13
haha, so i think i discoered why i would time out. i was trying to establish a connection from my external ip to my external ip. when i wasn't at home i tried it and it worked like a charm. thank you :)

---

### Post by cdenley on 2009-06-14
Some routers will route those connection attempts according to your port forward settings, and some will not.

---

