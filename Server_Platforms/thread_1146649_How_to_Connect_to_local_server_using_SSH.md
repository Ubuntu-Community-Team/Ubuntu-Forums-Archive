---
title: "How to Connect to local server using SSH?"
date: 2009-05-02
forum: Server Platforms
---

### Post by wayne on 2009-05-02
I want to connect to a local server through a Comcast SMC broadband NAT router for admin tasks and just realized I don't know what host name to put in the SSH client app..  I tried the router WAN IP and the server host name but no luck.  I know it's not the server private IP address.  The network is setup as a workgroup not a domain.  The old server was a gateway and had a public address and I just put the public address, user name & password in the SSH software and that was it.  But, this new server is on the local network behind the firewall.  I just setup this Ubuntu 8.04 LTS file server & installed SSH Server & also forwarded port 22 on the router.

I'm stuck and it's probably a simple answer but, can anyone give me some ideas on this?

Thanks in advance

---

### Post by cariboo on 2009-05-02
Check [canyouseeme]("http://www.canyouseeme.org/") to see if your isp is blocking any ports, or to see if you have port 22 open on your router.

---

### Post by wayne on 2009-05-02
Thanks I will try that Monday when I'm in the client's office.  So if the ISP is blocking port 22 I should just change it to some random port #?

Also any thoughts on what host name I might use?

---

### Post by drave99 on 2009-05-04
> **wayne said:**
> Thanks I will try that Monday when I'm in the client's office.  So if the ISP is blocking port 22 I should just change it to some random port #?

Also any thoughts on what host name I might use?

you use the IP or name([www.yourcompany.com](www.yourcompany.com)) of the router.
you also need a port forwarding rule in the router, to forward connections on port 22 to the internal server

---

