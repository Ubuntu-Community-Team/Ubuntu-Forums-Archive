---
title: "Help me configure Apache2's StartServers, maxclients... configuration"
date: 2007-01-21
forum: Server Platforms
---

### Post by Quake on 2007-01-21
I'm a little bit confused on how I should configure this section:

```
<IfModule prefork.c>                 
StartServers         5
MinSpareServers      5
MaxSpareServers     10
MaxClients          20
MaxRequestsPerChild  0
</IfModule>

<IfModule worker.c>
StartServers         2
MaxClients         150
MinSpareThreads     25
MaxSpareThreads     75
ThreadsPerChild     25
MaxRequestsPerChild  0
</IfModule> 
```

My server is a:
Pentium 1 Ghz
384 meg ram
4 Gig HD
Intel NIC

---

### Post by tomBorgia on 2007-01-22
Sounds weird but do you need to?

I've set up apache2 on quite an old box with the default settings and it worked fine.

Tom.

---

### Post by MJN on 2007-01-22
Indeed - if you don't really know what you're doing (which I'm guessing you don't hence your question[1]) then I dare say you could do more harm than good!

How busy is your server? I imagine the settings only become relevent at high loads (multi-thousand simultaneous connection territory).

Mathew

[1] I don't know either, so I'm not having a dig! ;)

---

