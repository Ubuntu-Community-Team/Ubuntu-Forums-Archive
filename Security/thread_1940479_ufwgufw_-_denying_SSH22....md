---
title: "ufw/gufw - denying SSH/22..."
date: 2012-03-13
forum: Security
---

### Post by youngunix on 2012-03-13
I followed this guide [http://ubuntuforums.org/showthread.php?t=1893751&highlight=port+123](http://ubuntuforums.org/showthread.php?t=1893751&highlight=port+123) to configure ufw/gufw. As the guide suggested; I allowed all the outgoing ONLY (ports: 20, 21, 53, 80, 123, 443) + (22). then in gufw I set "ougoing" & "incoming"-> "deny". 

I can surf the web and access all the sites I need to. BUT, I can't access Ubuntu through SSH/22 even tho it's added to "allow" ports. 
qBittorrent is added through gufw as an application and it is getting denied.

Is there any tweaking that I missed?

---

### Post by youngunix on 2012-03-13
[SIZE=2]**I solved the SSH/22 issue**[/SIZE] :-D. Still working on qBittorrent.

---

### Post by Ms. Daisy on 2012-03-13
I don't have time at the moment, but perhaps you can compare that thread to this one:

[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

The one thing I notice is that the thread you followed writes rules to deny everything but a few ports.  Whereas the thread I posted above denies all traffic then you write rules to allow certain ports.

---

### Post by youngunix on 2012-03-13
> **Ms. Daisy said:**
> I don't have time at the moment, but perhaps you can compare that thread to this one:

[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124) 

Threads are similar except for the gufw part. 

> The one thing I notice is that the thread you followed writes rules to deny everything but a few ports.  Whereas the thread I posted above denies all traffic then you write rules to allow certain ports.

That's basically the same configuration.

---

### Post by lovbuntu on 2012-03-13
> **youngunix said:**
> [SIZE=2]**I solved the SSH/22 issue**[/SIZE] :-D. Still working on** qBittorren**t.

I think qBittorrent uses port 6881 by default.```
sudo ufw allow out 6881/tcp
```

---

### Post by youngunix on 2012-03-14
> **lovbuntu said:**
> I think qBittorrent uses port 6881 by default.```
sudo ufw allow out 6881/tcp
```

That's already been exhausted with no luck.

---

