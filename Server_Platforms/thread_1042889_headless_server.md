---
title: "headless server"
date: 2009-01-18
forum: Server Platforms
---

### Post by wasutton3 on 2009-01-18
i have a headless server running just fine at home while i am at school. i have a web interface running on port 6883. when i try to change the port to 80 it still doesnt show up, its as if apache blocks it from the internet. (apache is necessary for this server) is there a way to set it so that when i enter the hostname, it goes straight to the interface?

---

### Post by jpkotta on 2009-01-18
Is this "web interface" something other than Apache?  Only one thing can listen on a given port.

Is something blocking the port?  From a remote machine:```
nmap -p80 webserver_address
```

Is the server itself firewalling the port?
```
sudo iptables -L
```

---

