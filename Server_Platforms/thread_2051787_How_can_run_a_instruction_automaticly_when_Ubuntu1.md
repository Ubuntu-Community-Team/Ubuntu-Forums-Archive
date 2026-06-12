---
title: "How can run a instruction automaticly when Ubuntu12.04 starting up??"
date: 2012-09-02
forum: Server Platforms
---

### Post by levinie001 on 2012-09-02
I want to run "sudo ifconfig eth0 192.168.64.3"  automaticly when my VM starting up.

---

### Post by ajgreeny on 2012-09-02
> **levinie001 said:**
> I want to run "sudo ifconfig eth0 192.168.64.3"  automaticly when my VM starting up.
Add that command without the sudo prefix to your /etc/rc.local file, just above the "exit 0" line.

---

### Post by rubylaser on 2012-09-02
If you are just trying to set a static ip on eth0, why don't you just make an entry in /etc/network/interfaces for the interface?

---

### Post by xdracco on 2012-09-02
Add ethernet configuration to /etc/network/interfaces as mentioned above then restart networking.

---

