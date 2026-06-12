---
title: "Access to server by name across local network"
date: 2011-01-02
forum: Server Platforms
---

### Post by hundred1906 on 2011-01-02
Have just installed Ubuntu Server edition 10.10. I gave the machine the name Culture-Server and the install was pretty much unmodified from the out-of-the-box download except that I checked the LVM option and also installed SSH.

I can SSH to the server from my ubuntu desktop only by using the local ip address (192.168. etc). I cannot access the server by name and get the response:


"ssh: Could not resolve hostname Culture-Server: Name or service not known"

I know I am just on the first step of the ladder toward setting up a full DHCP service using this server but did not expect to run into such a simple problem so quickly. What do I need to do to enable the rest of my existing network see this new machine.

Assuming here that I am failing to do something pretty obvious.

---

### Post by jgedeon on 2011-01-02
The error "ssh: Could not resolve hostname Culture-Server: Name or service not known" tells you that you don't have the system name in dns.

If you don't have access to your dns server then just add it to your local hosts file until you set up your DNS server.

/etc/resolv.conf will tell you what your dns server currently is.

You local hosts file is at /etc/hosts add a line that has the systems IP address then system name.

---

### Post by hundred1906 on 2011-01-02
Solved thank you.

---

