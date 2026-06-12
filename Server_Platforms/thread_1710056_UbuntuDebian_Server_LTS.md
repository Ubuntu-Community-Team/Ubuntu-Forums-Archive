---
title: "Ubuntu/Debian Server LTS"
date: 2011-03-19
forum: Server Platforms
---

### Post by k0d3g3ar on 2011-03-19
I am considering installing a Debian based server distro for an enterprise class application.  This application is currently running on CentOS, and doing ok.  The only problem is that we are having some issues with TCP traffic handling on that distro, which do not seem to be issues on Debian based installations.  The problems appear to be very low level, and rather than us try to debug those, it makes more fiscal sense for us to just move the application over to a Debian based server.

Having said that, the one thing that attracted us to CentOS was long term support.  This application runs 24/7 and can't be easily taken down for server OS upgrades.  

We are wondering if Ubuntu Server (or any Debian server distro) offers the same level of long term support for older versions as CentOS does?  For example, we still have old CentOS 4 servers in production that work fine.  We can still upgrade packages on it, and they are low maintenance.  Does the Ubuntu Server offer similar long term support, or should I be looking for a different Debian based distro to get this?

K

---

### Post by mikewhatever on 2011-03-19
Ubuntu offers 5 years of support for LTS servers, so that 10.04-server is supported till April 2015. Don't think it matches what CentOS does though.

---

### Post by k0d3g3ar on 2011-03-19
> **mikewhatever said:**
> Ubuntu offers 5 years of support for LTS servers, so that 10.04-server is supported till April 2015. Don't think it matches what CentOS does though.

Five years is not bad for us.  Its certainly better than Fedora! :)

So am I right to assume that the LTS period for Ubuntu servers is far longer than Ubuntu Desktop distros?

K

---

### Post by mikewhatever on 2011-03-19
Yes, it is longer. LTS desktops are supported for 3 years and non-LTS ones for 18 months.

---

### Post by kevin11951 on 2011-03-19
> **mikewhatever said:**
> Yes, it is longer. LTS desktops are supported for 3 years and non-LTS ones for 18 months.

[https://help.ubuntu.com/community/ServerFaq#What%20is%20the%20maintenance%20period%20of%20my%20server?](https://help.ubuntu.com/community/ServerFaq#What%20is%20the%20maintenance%20period%20of%20my%20server?)

> **What is the maintenance period of my server?**

You get free security updates for at least 18 months on the desktop and server. With the Long Term Support (LTS) version you get three years support on the desktop, and five years on the server. 

---

### Post by hawk2010 on 2011-03-21
I highly recommend Ubuntu 10.04 LTS server edition. THe package management is great and the OS is rock solid. I have experience in running a mail server, proxy and file server without any issues, GO ubuntu!

---

