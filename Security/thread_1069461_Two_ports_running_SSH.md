---
title: "Two ports running SSH"
date: 2009-02-14
forum: Security
---

### Post by Superdude_123 on 2009-02-14
I've been playing around with my box, and now I have my SSH running on the port that I want and on port 22. How do I close the service on port 22?

---

### Post by punx45 on 2009-02-14
in /etc/ssh/sshd_config

find this line

```
# What ports, IPs and protocols we listen for
Port 22

```

and remove port 22

then restart sshd
```
sudo /etc/init.d/ssh restart
```

---

### Post by Superdude_123 on 2009-02-14
I don't have port 22 there, only the other one i specified. What do I do now?

---

### Post by punx45 on 2009-02-14
try restarting ssh anyway.

if that doesnt work, how did you add the other port?  what other files are in /etc/ssh?

---

### Post by HermanAB on 2009-02-14
Note that if you have an active SSH connection going on a port, then you need to quit that before the connection on that port will be released.  So things are probably working correctly.  It is your active sssion that is hanging on to port 22.

Cheers,

Herman

---

