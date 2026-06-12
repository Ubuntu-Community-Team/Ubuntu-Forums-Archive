---
title: "Remote Access question"
date: 2009-01-16
forum: Server Platforms
---

### Post by blozancic on 2009-01-16
We place alot of servers behind firewalls that are for some reason unable to open up a port for ssh connectivity.  Is there a software like logmein.com that we can use that will let us access these servers.  I've seen alot of stuff for windows, like gotomypc.com and logmein.com, is there anything like that for Ubuntu.
Thanks

---

### Post by slacker9876 on 2009-01-16
You could use XDMCP, this is an actual console login like you are at the local machine.

---

### Post by HermanAB on 2009-01-16
SSH by default runs on port 22 TCP.  If your servers are behind a NAT firewall, then you can only forward port 22 once.  However, you can run SSH on any port you want.  See /etc/ssh/sshd_config.  Then you can forward a different port in the firewall for each server.

Cheers,

Herman

---

### Post by timcredible on 2009-01-16
agreeing with the other poster, xdmcp is the goal, but a firewall will block it's ports - also there's problems with a plain xdmcp connection through a firewall because the client requests a connection, then the server has to initiate a new connection on a different port.  so, what you want to do it is tunnel xdmcp through ssh.  not difficult if you can get ssh working on the firewalls.  use the -X option when opening the ssh connection, then run Xnest from the server (i haven't done this in a while, it's something like):
```

(from client): ssh -X <server>
(from server while connected via ssh): Xnest :30 -query <client ip address>

```

---

### Post by blozancic on 2009-01-16
Thanks for all your replies, unfortunately we can't have a port open on these firewalls.  We need something like an agent that gets installed on these machines that accessess a host on the internet.  We then connect to the host and through it get to the server.
Thanks again.

---

