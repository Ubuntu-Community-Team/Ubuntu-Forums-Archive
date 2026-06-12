---
title: "Ubuntu Server as a Firewall"
date: 2011-04-19
forum: Server Platforms
---

### Post by Jonny87 on 2011-04-19
I want to set up Ubuntu Server as a firewall in which I want to direct my internet connection through where Ubuntu Server will block, filter, and monitor anything that come into either three of my computers using the same internet connection.

Is this easy to do?

Can someone sum up the steps that I will have to go through to establish this, and any relevant information, and where I might be able to find necessary information etc.

I plan to use ubuntu-10.04.2-server-i386.

---

### Post by hawk2010 on 2011-04-19
In order to accomplish this you need to use a proxy service like Squid and then control access using ACL's. User activity will be recorded on the logs. Ubuntu 10.04 is fine for this. Your server should have two network interface cards to accomplish this.



> **Jonny87 said:**
> I want to set up Ubuntu Server as a firewall in which I want to direct my internet connection through where Ubuntu Server will block, filter, and monitor anything that come into either three of my computers using the same internet connection.

Is this easy to do?

Can someone sum up the steps that I will have to go through to establish this, and any relevant information, and where I might be able to find necessary information etc.

I plan to use ubuntu-10.04.2-server-i386.

---

### Post by garycahill on 2011-05-24
Or you could just enable IP Forwarding and treat the firewall like a router with IPtables.

---

### Post by brettg on 2011-05-25
The [guide here]("http://tuxnetworks.blogspot.com/2011/02/howto-configure-ubuntu-as-router.html") will walk you through setting up a router with a basic firewall. Good luck!

---

