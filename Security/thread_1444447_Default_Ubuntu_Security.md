---
title: "Default Ubuntu Security"
date: 2010-04-01
forum: Security
---

### Post by djbenny on 2010-04-01
for some university coursewrk im testing firewalls in linux (ubuntu) and windows xp

i was wondering if there was any security by default turned on as no ports are currently open. how can i turn it off as i want to have as fair testing as possible

any help will be aprechiated

---

### Post by EJeanmaire on 2010-04-01
There are very few ports open (or none) because you do not have any services running to answer on those ports.  There is no host-based firewall installed by default.

---

### Post by cdenley on 2010-04-01
Technically, there is a firewall by default (iptables), but it is configured to allow everything. It can be easily enabled with a single command (sudo ufw enable) since the ufw iptables configuration utility is installed by default now as well, but isn't enabled by default because there is nothing that needs to be filtered. There are two UDP listening processes: avahi for zeroconf/upnp and dhclient if a network interface is using DHCP. Any additional listening processes would've been installed by the user, or are binded to 127.0.0.1 and can't be accessed remotely (cups print server).

This will list all listening processes:
```

sudo netstat -tulnp

```

---

### Post by dogdo on 2010-04-01
Dont mean to hijack this thread but i did that command with ubuntu 10.04 beta 1 and this is the output i got-what does it all mean?

david@david-laptop:~$ sudo netstat -tulnp
[sudo] password for david: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1272/cupsd      
tcp6       0      0 ::1:631                 :::*                    LISTEN      1272/cupsd      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1734/dhclient   
udp        0      0 0.0.0.0:45011           0.0.0.0:*                           1073/avahi-daemon: 
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1073/avahi-daemon: 
david@david-laptop:~$

---

### Post by cdenley on 2010-04-01
> **dogdo said:**
> Dont mean to hijack this thread but i did that command with ubuntu 10.04 beta 1 and this is the output i got-what does it all mean?

As I said, cups printer server listening on local interface (not accessible remotely) TCP 631.

```
david@david-laptop:~$ sudo netstat -tulnp
[sudo] password for david: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
**tcp**        0      0 **127.0.0.1:631**           0.0.0.0:*               LISTEN      1272/**cupsd**     
**tcp6**       0      0 **::1:631**                 :::*                    LISTEN      1272/**cupsd**      

```
dhclient listening on UDP 68, needed to configure your network interface with DHCP:
```

**udp**        0      0 **0.0.0.0:68**              0.0.0.0:*                           1734/**dhclient**

```
Then avahi also listening on UDP for zeroconf and upnp:
```
   
**udp**        0      0 **0.0.0.0:45011**           0.0.0.0:*                           1073/**avahi-daemon**: 
**udp**        0      0 **0.0.0.0:5353**            0.0.0.0:*                           1073/**avahi-daemon**: 
david@david-laptop:~$
```

Looks like a default configuration.

---

### Post by MCVenom on 2010-04-01
> **djbenny said:**
> for some university coursewrk im testing firewalls in linux (ubuntu) and windows xp

i was wondering if there was any security by default turned on as no ports are currently open. how can i turn it off as i want to have as fair testing as possible

any help will be aprechiated
I believe Ubuntu comes with a no open ports policy, however, I don't know what package enforces this.

---

### Post by cdenley on 2010-04-01
> **BlackOtaku said:**
> I believe Ubuntu comes with a no open ports policy, however, I don't know what package enforces this.

No open TCP ports, anyway, as shown above. I'm not sure there is a formal policy, as it is just common sense. It is not enforced by a package, but none of the meta packages (ubuntu-standard, ubuntu-desktop, etc) which represent a default configuration depend on any packages containing a process which listens on a TCP port by default upon installation.

---

### Post by MCVenom on 2010-04-01
> **cdenley said:**
> No open TCP ports, anyway, as shown above. I'm not sure there is a formal policy, as it is just common sense. It is not enforced by a package, but none of the meta packages (ubuntu-standard, ubuntu-desktop, etc) which represent a default configuration depend on any packages containing a process which listens on a TCP port by default upon installation.
Hey thanks for clearing that up ;)

---

