---
title: "port forwarding denied"
date: 2012-05-15
forum: Security
---

### Post by AeonicEntity on 2012-05-15
I have a linux box running ubuntu and we're trying to set it up as a corperate intranet server. We opened up a port in the firewall to allow people to remotely connect to the intranet websites remotely, however, the linux box is rejecting requests to the port, and the connections all time out that we forward to it.

I tested the forwarding to a windows box on our network, and it successfully forwards.

Is there a setting in Ubuntu that prevents it from receiving packets sent via port forwarding?

---

### Post by darkod on 2012-05-15
No, there isn't a setting preventing it to receive traffic as far as I know. Apart from the local firewall of course.

To be exact, the forwarding is done on your router, not on the boxes, so this has nothing to do with whether windows forwards and ubuntu doesn't. They receive, they do not forward anything.

Are you sure you have the firewall settings right? That would be my first suspect.

---

### Post by SeijiSensei on 2012-05-15
First, can you see the websites from machines inside the network?  If not, then the server isn't configured to listen on the correct interfaces, or there's a firewall on the Linux box.  Usually the Apache version that Ubuntu installs listens on all the interfaces (using the *:80 convention in the virtual host definitions), and there is no firewall enabled by default.  Either use a browser on another internal machine and connect to [http://ip.addr.of.server/](http://ip.addr.of.server/) or use "telnet ip.addr.of.server 80"?  Do these work, or do they time out?

If you're trying to forward the router's external port 80 to the Linux server, try a different external port like 8080.  Some ISPs block inbound HTTP connections for clients who haven't purchased a full-blown business-class service.  

I take it when you say you have forwarded a port to a Windows machine it's not the same port as the one you're forwarding to Ubuntu, correct?

---

