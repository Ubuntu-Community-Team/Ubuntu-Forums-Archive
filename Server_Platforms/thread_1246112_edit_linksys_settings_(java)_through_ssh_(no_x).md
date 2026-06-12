---
title: "edit linksys settings (java) through ssh (no x)"
date: 2009-08-21
forum: Server Platforms
---

### Post by gypsumwolf on 2009-08-21
I have a server running "Ubuntu Server (no x)" behind a linksys router. The router uses java for its settings page so I can not use links (web-browser) to edit it. I want to forward 2 ports. 

```

[Laptop (ssh)]

---------------
| Router      |
| --Server 1  |
| --Server 2  |
---------------
```

---

### Post by grantemsley on 2009-08-21
Here's what I do:

From a linux machine:  "ssh -f user@server1 -L 80:<routerip>:80" 

From a windows machine, run putty (ssh client).

In hostname, put in the ip address or name of the server.
In SSH --> Tunnels put in source "80", destination "<routerip>:80" and click add.

Click open, login through SSH, then open a web browser to [http://localhost:80](http://localhost:80)

This creates a tunnel that fowards localhost:80 through the SSH server to the router's web server.  The router's IP will be the private one on the network, usually 192.168.0.1 or 192.168.1.1.

This trick can be used for almost any service on the lan :)

Another trick, you can make it act like a socks proxy.  Put source port 8080, leave destination blank, and check dynamic below.  Then set your web browser to use a socks5 proxy on port 8080.  After that, it will act like you were browsing from the server.

---

### Post by gypsumwolf on 2009-08-21
> **grantemsley said:**
> Here's what I do:
From a windows machine, run putty (ssh client).


Thanks for the trick. Why use a windows machine? I don't want to ;)

---

### Post by grantemsley on 2009-08-21
Well, it all depends on what you have.

My servers are all linux, my desktops are mostly windows.  So putty works well.  If you are on a linux system, obviously use the linux way :)

---

