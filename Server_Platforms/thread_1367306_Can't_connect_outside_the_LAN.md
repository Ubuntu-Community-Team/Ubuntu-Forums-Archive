---
title: "Can't connect outside the LAN"
date: 2009-12-29
forum: Server Platforms
---

### Post by karimone on 2009-12-29
I trying to connect outside the LAN in ssh or ftp, but the connection is refused. Every time I get a **Network error: Connection refused**. The http works and website are visibile outside the lan.

Where I have to check?

---

### Post by cosine352 on 2009-12-29
did you check the router. you have to open the ports for ssh or ftp. may be the router in your home is blocking those ssh and ftp ports.

---

### Post by karimone on 2009-12-29
Everything started after the installation of ehcp. Before that everything worked. I removed ehcp, but nothing changed. :-(

---

### Post by cdenley on 2009-12-29
Unless you created iptables rules to filter those connection attempts, then if it works from inside your LAN, it is a networking issue. If sshd is listening for connections, it doesn't choose which to accept. If a connection fails only for internet connections, then it is because it never reaches your server because the router never forwards it, or it is being filtered.

I'm assuming you configured port forwarding. Are you attempting to connect from within your LAN using your WAN IP? This doesn't work with all routers.

---

### Post by karimone on 2009-12-30
Solved. Was the router that lost the DMZ setting... I don't know why... but now works!

---

