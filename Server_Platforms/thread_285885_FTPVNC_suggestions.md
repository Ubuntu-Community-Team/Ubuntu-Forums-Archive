---
title: "FTP/VNC suggestions?"
date: 2006-10-27
forum: Server Platforms
---

### Post by subnet_rx on 2006-10-27
I've got Apache up and running, now I'm trying to get FTP going, and a VNC connection.  Right now, I'm using proftpd and tightvnc with no luck getting either of them to run.  Any suggestions on programs that you have found to be easily setup?

---

### Post by twistedtwig on 2006-10-27
are you connected directly to the net or behind a router?

also is there a firewall stopping all port connections?

Twiggy

---

### Post by subnet_rx on 2006-10-27
The router might be the issue.  I had set it up for Apache, but not for VNC or FTP.

---

### Post by jms1989 on 2006-10-27
> **subnet_rx said:**
> The router might be the issue.  I had set it up for Apache, but not for VNC or FTP.

How can I get FTP to work within the network because I would like to host a full fledged website within my network?

---

### Post by subnet_rx on 2006-10-27
When I figure it out, I'll let you know.

---

### Post by twistedtwig on 2006-10-28
Ok,

so if you are behind a router then you need to port forward the information to your server.  I have heard of and have had a little experience with vnc port forwarding issues.. ie i cant get it to work and heard others have had some difficulty (not spent more then 15mins playing with it yet though).

to port forward on the router either let someone know what it is and they might be able to help or look at the docs you have with it.  Netgear for example is very easy.  create a service for it and add that to the rules.

If you just want the web to work in your LOCAL network NOT the net then you just need to tell people what ip / computer name to look at for that service (ie apache).  dont know off the top of my head if apache would need to be configured differently or not, dont think so though.

jms1989, you want a website on your network? you dont need ftp for this.  does it need to be secure? ie, do you trust ALL users on your local network?  if so then you can follow Many how to guides on setting up a ftp server, (have been recommended to use pro ftpd).

Twiggy

---

