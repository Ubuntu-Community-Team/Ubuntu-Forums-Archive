---
title: "Server setup"
date: 2016-08-27
forum: Server Platforms
---

### Post by TheMTtakeover on 2016-08-27
Hello! I am looking at setting up a home file server. I would setting it up on a System 76 Meerkat. I would be using the standard desktop version of Ubuntu not the server edition. It would be using SMB/Samaba for file sharing. It has to be accessed by macOS, Windows, and Linux.

It would be connected to the Internet mainly so I can get the machine up to date. I would set up ssh on it so I can ssh into the machine and not have to worry about connecting it to a mouse and keyboard all the time. What kind of security risks am I looking at by leaving this connected to the Internet? I do not plan to ever ssh into the machine other than when I am on my local network and no files will ever be accessed other than on my local network.

---

### Post by ajgreeny on 2016-08-27
Why bother with a DE and GUI for a file server that you seem to be using ssh connections to administer?

If you must have a GUI it would make a lot more sense to use a much less resource-hungry DE than the standard unity of Ubuntu.

---

### Post by TheMTtakeover on 2016-08-27
> **ajgreeny said:**
> Why bother with a DE and GUI for a file server that you seem to be using ssh connections to administer?

If you must have a GUI it would make a lot more sense to use a much less resource-hungry DE than the standard unity of Ubuntu.


I understand, but there are times where I may be on the server itself and it would be beneficial for me to have a GUI at times and the resource usage isn't that much of a concern to me.

---

### Post by wildmanne39 on 2016-08-27
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2016-08-28
A few simple firewalling rules will help:
```

# allow localhost
/sbin/iptables -A INPUT -i lo -j ACCEPT

# allow replies to requests we make
/sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# allow local network
/sbin/iptables -A INPUT -s 192.168.1.0/24 -j ACCEPT

# block everything else
/sbin/iptables -A INPUT -j REJECT

```

Now only machines with IP addresses beginning with 192.168.1 can connect to the server.  You'll need the proper IP subnet for your own local network if 192.168.1.0/24 isn't correct.  You can figure that out from the "ip route" command.  You'll see a line like this:
```
192.168.101.0/24 dev eth0  proto kernel  scope link  src 192.168.101.1 
```
The proper network subnet address appears at the beginning of this output, "192.168.101.0/24" in this case.

You can add these rules to /etc/rc.local so they will be run when the server boots up.  Put them above the "exit 0" line.

---

