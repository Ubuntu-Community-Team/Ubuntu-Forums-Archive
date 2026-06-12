---
title: "selecting a processor"
date: 2009-07-21
forum: Server Platforms
---

### Post by abraham.varricatt on 2009-07-21
Does anyone have links for any RECENT reviews between Xeon and Opteron? I've been googling for a while and all I find are 2003 or 2005 based reviews at different sites.

I'm deciding on which processor I should go for in a server. The server will be used for virtualization (KVM based).

Also, is the manufacturer a concern? I'm thinking of Dell, but I heard a rumor that it's better to only buy intel chips from them?!

---

### Post by dragos2 on 2009-07-21
> **abraham.varricatt said:**
> Does anyone have links for any RECENT reviews between Xenon and Opteron? I've been googling for a while and all I find are 2003 or 2005 based reviews at different sites.

I'm deciding on which processor I should go for in a server. The server will be used for virtualization (KVM based).

Also, is the manufacturer a concern? I'm thinking of Dell, but I heard a rumor that it's better to only buy intel chips from them?!

No, but **Xeon** versus Opteron surely exists :P

For Virtualization Xeons are better, preferably a Quad Core 3 Ghz. But they have a higher power
consumption.

---

### Post by abraham.varricatt on 2009-07-21
:oops: Opps!

It's fixed in the OP now.

Hmm... power consumption is not a priority for me at this time. I'm thinking about a Xeon 2.66Ghz. Any thoughts ?

---

### Post by dragos2 on 2009-07-21
> **abraham.varricatt said:**
> :oops: Opps!

It's fixed in the OP now.

Hmm... power consumption is not a priority for me at this time. I'm thinking about a Xeon 2.66Ghz. Any thoughts ?

What do you want to achieve ?

How many virtual hosts, what applications, number of users ?

---

### Post by abraham.varricatt on 2009-07-21
> **dragos2 said:**
> What do you want to achieve ?

How many virtual hosts, what applications, number of users ?

Thanks for all your replies.

This is for a small business operation. We're migrating from having multiple desktop's to a single server. What I'm hoping is, to buy a new server and virtualize all our different desktop needs with that. This way it should be a lot easier to configure the virtual desktops with different RAM or HDD settings as required.

If I buy a server with 8GB of RAM on it, how much is the total RAM I can allocate to the different virtual systems on it? eg- for testing, on a desktop(with 512MB RAM) I ran VirtualBox to run a system with 256MB RAM. It failed on me after 5 minutes indicating that my host system was running low on RAM.

---

### Post by dragos2 on 2009-07-21
> **abraham.varricatt said:**
> Thanks for all your replies.

This is for a small business operation. We're migrating from having multiple desktop's to a single server. What I'm hoping is, to buy a new server and virtualize all our different desktop needs with that. This way it should be a lot easier to configure the virtual desktops with different RAM or HDD settings as required.

If I buy a server with 8GB of RAM on it, how much is the total RAM I can allocate to the different virtual systems on it? eg- for testing, on a desktop(with 512MB RAM) I ran VirtualBox to run a system with 256MB RAM. It failed on me after 5 minutes indicating that my host system was running low on RAM.

Virtualization is not the best answer to your problem, but remote desktop is
with NX or LTSP(which I saw is more popular over here), or the general thin client.

Virtualization is overhead here because you want to virtualize desktops and you work
way more time to install and configure all those desktops.

---

### Post by abraham.varricatt on 2009-07-21
> **dragos2 said:**
> 
Virtualization is overhead here because you want to virtualize desktops and you work
way more time to install and configure all those desktops.

I forgot to mention that we do NOT use the GUI-front end on our linux desktops. I am aware of that causing issues, but for terminal needs, I think virtualization should be suffice, right? :-?

EDIT: A limitation with LTSP is that it forces the clients to use the same host-environment. In some cases, we need Ubuntu, others Fedora, ...etc. So, I figured, why not try virtualization? In our environment, installing and configuring the desktops is not really an issue. But, the final running performance of the system IS.

---

