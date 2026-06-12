---
title: "Not able to connect to internet"
date: 2009-02-11
forum: Server Platforms
---

### Post by Reid_PMP on 2009-02-11
I can connect to my server via SSH from my Vista PC, but I'm not able to connect to the internet from my server.

When I run route I get the following results;

Destination = 192.168.1.0
Gateway = *
Genmask = 255.255.255.0
Flags = U
Metric = 0
Ref = 0
Use = 0
Iface = eth0

If I try to ping [www.google.com](www.google.com) I get "connect: Network is Unreachable"

Any ideas on how to resolve this? I was able to connect before and I haven't added, updated, or upgraded anything since then.

---

### Post by linux_tech on 2009-02-12
Try rebooting first

---

### Post by Neural oD on 2009-02-12
also see that you are not going through a gateway - this could be the ip address of your router

---

### Post by Reid_PMP on 2009-02-12
> **linux_tech said:**
> Try rebooting first

I thought that was only for PCs! Just kidding, that was my first action. 

Where do I check for the gateway setting?

I do remember changing the IP address to a static address a few months ago. I can't remember trying to access the internet since then.

Maybe that is my problem. I'll go back to the instructions for setting the static IP address. The file I changed was /etc/network/interfaces.

I'll let you know if that worked.

---

### Post by conjur3r on 2009-02-12
Does the interfaces file have a **gateway** statement?  While you're at it, how is your DNS resolutions - working?

---

### Post by Reid_PMP on 2009-02-12
It wasn't a technical problem after all. The problem originated from the desk chair and the occupant.

I typed in the wrong gateway by one digit.

I corrected the gateway value and everything is working.

I'm admitting to my mistake so others may learn from it.

Have a good day.

---

