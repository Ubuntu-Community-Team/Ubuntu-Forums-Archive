---
title: "Running multiple instances of one virtual machine remotely"
date: 2014-04-23
forum: Virtualisation
---

### Post by oppigard on 2014-04-23
Hi

I have been using Ubuntu Server from time to time, so I know a little bit, but not a lot.

We are going to create a Server at work for backup and centralized storage (samba etc.)
But we also need a virtual machine running Windows 7, that can run a database client (SAP, for registering working hours, billing and so on)
This virtual machine will be using its own physical network adapter, connecting to a windows domain server.
So what I would like is a Ubuntu Server, with a virtual machine running windows 7, that clients can connect to (remote desktop, or remote "app") from windows clients on the same network (not the windows-domain network)
It will probably be a maximum of 15 simultaneous users.

I don't expect a full guide to this, I just want to know if this is possible and what apps/tools I would need.
Licence pricing matters a lot, since the whole idea of moving away from 15 domain clients to 1 shared virtual domain client, is that we are being billed 35.000 NOK ($5.850) yearly for each client, and we only need to be part of the domain to access SAP.

Also, what would be minimum ram, cpu and so on for this usage?
I really appreciate any help.

---

