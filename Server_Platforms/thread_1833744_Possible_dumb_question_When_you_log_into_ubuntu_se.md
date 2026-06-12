---
title: "Possible dumb question: When you log into ubuntu server, system info is displayed..."
date: 2011-08-26
forum: Server Platforms
---

### Post by pconwell on 2011-08-26
When you log into a server install, certain information is displayed like so:

    ```
System information as of Fri Aug 26 12:18:12 CDT 2011

    System load:    0.0               Processes:           89
    Usage of /home: 0.7% of 25.21GB   Users logged in:     0
    Memory usage:   5%                IP address for eth0: 192.168.1.149
    Swap usage:     0%                IP address for eth1: 192.168.0.1

```Is There a way to change what is displayed? For example, one of my other partitions was getting full and it popped up a warning that said something like

```
      Usage of /directory:  87% of 316.7GB
```I would like to see the usage of /directory all the time, not just when it is almost full. I tried googling for an answer, but I couldn't find anything, and I'm not sure what it is called, so I don't know what to search for anyway.

Sorry if this is a dumb question...

---

### Post by Entilza on 2011-08-26
check out /etc/update-motd.d/

---

### Post by SoFl W on 2011-08-26
As stated above it is called MOTD - "Message of the Day" but I think it only changes once a day, not every time you log in.

---

### Post by pconwell on 2011-08-27
Okay, Thanks. It looks like it is a combination of /etc/update-mod.d/50-landscape-sysinfo and /usr/bin/landscape-sysinfo.

Thanks again.

---

