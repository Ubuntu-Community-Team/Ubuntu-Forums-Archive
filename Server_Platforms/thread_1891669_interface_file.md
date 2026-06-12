---
title: "interface file"
date: 2011-12-06
forum: Server Platforms
---

### Post by kumaresan078 on 2011-12-06
Recently i installed ubuntu server but unable to ping to server from client system but when i add the ip through ifconfig command it works fine after restarts it's gone.while adding ip in the /etc/network/interfaces files it's not pinging give me the solution

---

### Post by prodigy_ on 2011-12-06
> **kumaresan078 said:**
> while adding ip in the /etc/network/interfaces files it's not pinging

Did you restart networking? What does **ifconfig** say?

---

### Post by rubylaser on 2011-12-06
What what do the contents of these two files have?

```
cat /etc/network/interfaces
```
```
cat /etc/resolv.conf
```

---

### Post by kumaresan078 on 2011-12-06
> **prodigy_ said:**
> Did you restart networking? What does **ifconfig** say?
 
 
 
 
ya restarted networking services also but same problem ifconfig not showing anything only the loopback is available.
 
if i add ip through ifconfig command it works well.After system restarts it also gone.

---

### Post by volkswagner on 2011-12-07
> **kumaresan078 said:**
> ya restarted networking services also but same problem ifconfig not showing anything only the loopback is available.
 
if i add ip through ifconfig command it works well.After system restarts it also gone.

Sounds like you may have Ubuntu Desktop installed?  If that is true, you can use network manager to edit your interface settings.

/etc/network interfaces should not be missing your main ethernet connection (eth0 or eth1), unless network manager is installed.

---

