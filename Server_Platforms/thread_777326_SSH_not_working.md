---
title: "SSH not working"
date: 2008-05-01
forum: Server Platforms
---

### Post by Zipster90 on 2008-05-01
For some reason my ubuntu server is not allowing me to log into it via ssh. I have openssh-server installed, but when I try to use putty on my Windows machine to ssh into it, it says the connection was refused. How do I fix this? Thanks.

---

### Post by hatoyu on 2008-05-01
same to you 
wait reply too

---

### Post by cdenley on 2008-05-01
> **Zipster90 said:**
> For some reason my ubuntu server is not allowing me to log into it via ssh. I have openssh-server installed, but when I try to use putty on my Windows machine to ssh into it, it says the connection was refused. How do I fix this? Thanks.

post this output
```

netstat -tln
sudo ufw status
sudo iptables -L INPUT

```

Is the windows client on the same local network as the ubuntu server? Is there a firewall or router between them?

---

### Post by Dr Small on 2008-05-01
It is a blocked port either on the system that is hosting the ssh server, on the router (while you are connecting from outside), or both.

Dr Small

---

### Post by Zipster90 on 2008-05-01
> **hatoyu said:**
> same to you 
wait reply too

?????

Anyway, I'm not at work now, so I'll get those results posted once I get back. Thanks.

---

### Post by cdenley on 2008-05-01
> 
same to you
wait reply too

I think that translates to...
> I have the same problem.
I will be waiting for a reply, too.

---

### Post by exaviorn on 2008-05-01
If it is a port blocked go to [http://portfoward.com]("http://portfoward.com") and find your router then select ssh,you will find a good tutorial!!

---

