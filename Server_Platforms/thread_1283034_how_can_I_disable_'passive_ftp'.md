---
title: "how can I disable 'passive ftp' ?"
date: 2009-10-05
forum: Server Platforms
---

### Post by edwardtilbury on 2009-10-05
When I'm remotely trying to ftp my server gives me passive ftp errors. Specifically:

```
Response:    227 Entering Passive Mode (192,168,1,15,195,244).
Status:    Server sent passive reply with unroutable address. Using server address instead.
```Can I just flip a switch and turnoff passive ftp?  I'm using gadmin profftp on Ubuntu 9.04 desktop as my server.

Thanks

---

### Post by Lars Noodén on 2009-10-05
It sounds like a networking problem.  Where are you accessing your server from in relation to your Anonymous FTP server?
(It is Anonymous FTP, right?)

---

### Post by Xianath on 2009-10-06
Short answer:
Bring up a second IP on the server's network card, eg. 192.168.1.115. On the router, forward port 21 as well as a port range >1024 (eg. 10000-10010). Then in proftpd.conf, do the following:

<VirtualHost 192.168.1.115>
  ServerName "PublicIP"
  MasqueradeAddress <your public IP>
  PassivePorts <start port> <end port>
</VirtualHost>

Long answer:
You don't want to disable passive FTP, trust me. You won't be able to connect from almost anywhere. RFC 959 defines the PASV response as the IP:Port that the client should connect to. Now, when your server is behind a firewall and has a private address (192.168.1.15 in your case), you have a problem when you connect from the outside world. Why? Because clients won't be able to connect to that address as RFC 1918 clearly defines it as non-routable.

What you want to do is set up the server so that it responds with its public address rather than its private one. In the above example, clients coming in from the outside will get NAT'ed on the router and hit the 192.168.1.115 IP address, thus falling in the VirtualHost definition and following its rules. The MasquerateAddress directive will tell ProFTPd to respond with its public IP so clients know where to send the data connection request to, and the PassivePorts directive will make sure they are instructed to use a port that will be allowed on the router.

HTH,
Peter

---

### Post by HankB on 2009-10-06
Another answer (question?) would be to ask if you are aware of the insecurities inherent in ftp? It passes your password through the network in clear text that anyone sniffing on the network can then capture and use. If security is an issue, you should consider switching to sftp which establishes an ssh connection and passes your password through the network using that. (Or something along those lines. To be absolutely truthful, I do not the details of ssh authentication, but I do know that it makes it difficult - if not impossible - for someone to sniff your password.)

For the same reason, you should prefer ssh to telnet.

If you are only accessing files over your internal LAN this is not an issue, but you did use the words "router" and "remote."

best,
hank

---

### Post by Xianath on 2009-10-06
FTP has security extensions (see RFC 2228 and 4217) that allow the use of SSL/TLS for the control and/or data channel. ProFTPd supports them, so do curl, lftp, wget, or -- if you'd like a GUI -- jftp or filezilla. You shouldn't even have to bother with CCC unless your router is trying to play smart and inspect FTP traffic (highly unlikely).

SFTP is certainly easier to manage on the firewall level as it only uses one port. It also supports compression. However, unless you run a separate SSH server for your SFTP needs, you'll end up exposing it to the outside world, and that's not a good idea. Give FTP/S a try instead, it's safer.

Cheers,
Peter

---

### Post by HankB on 2009-10-06
> **Xianath said:**
> FTP has security extensions (see RFC 2228 and 4217) ...
Thank you for that additional bit of information. Obviously something I was not aware of.

-hank

---

### Post by edwardtilbury on 2009-10-10
Well, my server is ubuntu..At the moment I'm using GADMIN PROFTP Is there another FTP serving program I can use?

How do I enable all these things, like sftp etc..

Thanks for the help, all the FTP stuff is a mystery to me.

---

