---
title: "[SOLVED] Listening ports and Firestarter rules"
date: 2008-09-05
forum: Security
---

### Post by lovinglinux on 2008-09-05
I'm wondering if any application that I installed could be listening to inbound connections without my knowledge? For instance, MythTV installs MySQL and load it on startup.

So, is there any application that could monitor for listening ports on-the-fly?

I also would like to know if it is possible to export Firestarter rules. I have a separate partition for /home, but every time I re-install Ubuntu I have to insert the Firestarter rules again.

---

### Post by cdenley on 2008-09-05
To check what processes are listening for connections
```

sudo netstat -plntu

```

The firestarter configuration file is located at:
/etc/firestarter/configuration
I would probably just copy that whole directory.

---

### Post by jerome1232 on 2008-09-05
You could also run nmap from another host, running it on the same machine won't be accurate because some apps are setup to listen on the loopback interface (cups for example), these will show up on a scan of localhost but aren't accessible from a remote machine.

---

### Post by cdenley on 2008-09-05
> **jerome1232 said:**
> You could also run nmap from another host, running it on the same machine won't be accurate because some apps are setup to listen on the loopback interface (cups for example), these will show up on a scan of localhost but aren't accessible from a remote machine.

The command I posted shows which interface it is listening on
```

tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      7060/cupsd

```
127.0.0.1=local loopback device

---

### Post by jerome1232 on 2008-09-05
That it does, :) I suppose 0.0.0.0:port number means all interfaces, but what does foreign address mean?

---

### Post by cdenley on 2008-09-05
> **jerome1232 said:**
> That it does, :) I suppose 0.0.0.0:port number means all interfaces, but what does foreign address mean?

```

man netstat

```
> 
Address and port number of the remote end of the socket.  Analogous to "Local Address."

That doesn't really apply for applications that are listening for connections. That is more for when you don't use the "-l" option. It will show what remote hosts you are currently connected to.

---

### Post by jerome1232 on 2008-09-05
I checked the man page but that quote didn't make much sense to me, I get it now though thanks.

---

### Post by lovinglinux on 2008-09-05
> **cdenley said:**
> To check what processes are listening for connections
```

sudo netstat -plntu

```

The firestarter configuration file is located at:
/etc/firestarter/configuration
I would probably just copy that whole directory.

Thank you very much!


> **jerome1232 said:**
> You could also run nmap from another host, running it on the same machine won't be accurate because some apps are setup to listen on the loopback interface (cups for example), these will show up on a scan of localhost but aren't accessible from a remote machine.

Unfortunately, not an option. But thanks anyway.

---

