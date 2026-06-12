---
title: "LTSP - DHCP horror"
date: 2005-11-21
forum: Server Platforms
---

### Post by apjone on 2005-11-21
Hi , I have a Linux Terminal server running its own DHCP server , but i also have 3 windows server running dhcp. When i boot with my dumb terminal half the time it wont find the Linux Terminal server. Anyone know how to fix this . And yes I need the windows dhcp servers.

---

### Post by cactus on 2005-11-21
I stand in wonderment at the need for three dhcp servers on one broadcast domain.

---

### Post by Glut on 2005-11-21
Sometimes it will find the machine and sometimes not.
Your dchpd should be logging all requests that it receives. Check that it gets a request. If it fails to get a request then you probably have a networking issue. Ditto if it responds but the response is never received.
Hopefully, you will get a request and an error message in the log.

Just for curiosity, why are the windows servers necessary and why 4 dhcp servers?

---

### Post by cactus on 2005-11-21
i doubt he is failing to get a response. More likely, it is chance that sometimes the first dhcp server to respond is the one he wants. I mean..with 3 or 4 of them.. it is going to cause nothing but problems. 
He really only needs one, and needs to set it up appropriately.

---

### Post by apjone on 2005-11-22
Its a works domain with windows NT to 2k3 and a few linux servers. Is there any sort of RDP connections that you can use to gain access to the LTS instead of bootin straight to it?

---

