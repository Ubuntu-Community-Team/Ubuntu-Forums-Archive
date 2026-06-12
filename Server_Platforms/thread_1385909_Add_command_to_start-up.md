---
title: "Add command to start-up?"
date: 2010-01-20
forum: Server Platforms
---

### Post by werner.fletcher on 2010-01-20
Hey there,

I want to add a line to the start-up of my proxy server that does the IPTABLES port re-routing for me automatically instead of having to do it manually every time I restart.  Any help would be appreciated, thank you in advance.

---

### Post by dvlchd3 on 2010-01-20
Any executable scripts in the /etc/init.d/ folder will execute on startup.  If you want the script to run after the network interface is brought up, put the exectuable script in /etc/network/if-up.d/ folder and ensure the filename has no special characters, just numbers and text.

Hope this helps!

---

### Post by werner.fletcher on 2010-01-20
> **dvlchd3 said:**
> Any executable scripts in the /etc/init.d/ folder will execute on startup.  If you want the script to run after the network interface is brought up, put the exectuable script in /etc/network/if-up.d/ folder and ensure the filename has no special characters, just numbers and text.

Hope this helps!

Hey that really helps! Thank you so much, just one question... how does a script look? Is it just a normal file with the command inside?  Sorry but I'm really noob when it comes to scripts.  Thanks :)

---

### Post by gobbledigook on 2010-01-20
hi,

```
#!/bin/bash
```

at the start of your script will do the trick, for a full guide see [_**here**_]("http://www.tldp.org/guides.html")

---

