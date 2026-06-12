---
title: "Can't connect to fresh Hardy Server install"
date: 2008-05-02
forum: Server Platforms
---

### Post by hise0001 on 2008-05-02
I have made a fresh install of Hardy Server with LAMP and SAMBA settings.

From my Hardy Desktop I can successfully ping the Hardy Server; but, if I open a Hardy Desktop browser and enter http://<ip address to Hardy Desktop>, I receive a Unable to Connect (site unavailable) message.

Looking at "ps" on HardyDesktop, it appears apache2 is running.

Does Hardy Desktop default to all ports closed or something?

Any insight would be greatly appreciated.

---

### Post by ghostknife on 2008-05-03
Can you access it by browsing [http://127.0.0.1/](http://127.0.0.1/) on the server itself (inside Firefox)?

If you can, paste the output of the following command:
```

sudo iptables -nL
```

Also, try configuring your firewall on the server. Add inbound port 80 TCP and restart the firewall to be sure changes take effect, if that fixes the problem let me know and I'll give you the port numbers for SAMBA.

---

