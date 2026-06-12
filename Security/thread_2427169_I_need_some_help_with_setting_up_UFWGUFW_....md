---
title: "I need some help with setting up UFW/GUFW ..."
date: 2019-09-18
forum: Security
---

### Post by dagmann on 2019-09-18
Is there a list of recommended ports that should be opened and closed?  :confused:

---

### Post by TheFu on 2019-09-18
Simple.
Close them all, except the ones you specifically run network services on that you want available to other systems.

For example, if you run a web server that only listens on port 443/tcp (HTTPS), then that is the only port you would open.

If you run ssh-server, then for the local network, you'd want to allow 22/tcp.  If you allow it from the internet, then I'd strongly suggest running fail2ban which will automatically create a firewall block after 3 failed attempted logins.  BTW, internet attempts shouldn't allow passwords for ssh authentication, only ssh-keys.

Easy enough?

---

### Post by dagmann on 2019-09-19
I am not running a server or any type of service.

 I just want to be able to surf the web, use email and play some games.
Could you tell me what ports to use for the above mentioned usage?

I am new to Linux. I have installed Kubuntu Plasma. It's awesome.
Thanks in advance.

---

### Post by uRock on 2019-09-19
> **dagmann said:**
> I am not running a server or any type of service.

 I just want to be able to surf the web, use email and play some games.
Could you tell me what ports to use for the above mentioned usage?

I am new to Linux. I have installed Kubuntu Plasma. It's awesome.
Thanks in advance.
You don't have to open any ports, if you're not running services. Just enable the firewall and enjoy the internet.

---

### Post by TheFu on 2019-09-19
If you aren't running any services/network daemons, then there is little need for a firewall if you are behind a normal, maintained, patched, router.  If you take a computing device beyond that router or aren't 100% positive that the router is correctly maintained, and patched, monthly, then block all inbound ports with a firewall on the computer.

An unmaintained router is a security risk beyond all others.  Mainly because it provides a false sense of security that doesn't actually exist.

---

### Post by dagmann on 2019-09-19
My router is from Verizon FiOS. As far as I know they update is every now-and-again.

---

### Post by TheFu on 2019-09-19
> **dagmann said:**
> My router is from Verizon FiOS. As far as I know they update is every now-and-again.

I wouldn't trust it.  I've worked at a similar-sized ISP specifically with patching CPE routers.  Don't trust those devices. Their goal is to minimize customer complaints and gather marketing data, not provide the best possible security.  Every time a new firmware is pushed out, some number of devices have a fault of some sort.

I have a mandated ISP router (no choice of mine).  I have my own router just inside it to provide real protection.  Their router runs in bridge mode and acts as a guest wifi for visitors.  Mine runs a router distro that I know is correctly maintained and easily patched.

---

### Post by uRock on 2019-09-19
> **dagmann said:**
> My router is from Verizon FiOS. As far as I know they update is every now-and-again.

In that case, I'd have the firewall enabled. I don't trust ISPs to keep endpoint devices updated. They care more about preventing the cost of sending someone out to do a hard reset or swapping of the router should the firmware upgrade brick it.

---

### Post by dagmann on 2019-09-23
Solved

---

### Post by dagmann on 2019-09-23
Solved

---

