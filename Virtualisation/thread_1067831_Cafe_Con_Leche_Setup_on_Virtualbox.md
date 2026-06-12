---
title: "Cafe Con Leche Setup on Virtualbox"
date: 2009-02-12
forum: Virtualisation
---

### Post by adredz on 2009-02-12
Hi... I want to simulate a server-client setup for CCL. Unfortunately I don't have the resources and the only solution I could think of is Virtualization. Is it possible to setup the guest OS as the client and then the host as the server?

---

### Post by zevans on 2009-02-12
> **adredz said:**
> Hi... I want to simulate a server-client setup for CCL. Unfortunately I don't have the resources and the only solution I could think of is Virtualization. Is it possible to setup the guest OS as the client and then the host as the server?

Better to set up two guests, and then you aren't in any danger of affecting the host with your testing. The two guests can be placed on a "network" that is managed entirely by VirtualBox, so they will be able to see one another.

---

### Post by adredz on 2009-02-12
> **zevans said:**
> Better to set up two guests, and then you aren't in any danger of affecting the host with your testing. The two guests can be placed on a "network" that is managed entirely by VirtualBox, so they will be able to see one another.

Have you tried it yourself? Would you mind telling me how to do it step by step? I have no networking skills really... Just the 'how to connect the two guests'.. I would really appreciate it..

---

