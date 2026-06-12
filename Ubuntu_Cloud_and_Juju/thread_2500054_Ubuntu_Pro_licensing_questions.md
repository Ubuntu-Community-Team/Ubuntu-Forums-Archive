---
title: "Ubuntu Pro licensing questions"
date: 2024-08-20
forum: Ubuntu Cloud and Juju
---

### Post by b-9 on 2024-08-20
I run 3 proxmox hypervisors with a total of maybe 30 VMs that will run. We run an ubuntu shop and I'd love to use Landscape to monitor the infrastructure and package updates. The self-hosted setup process has been *mostly* straight-forward, but the licensing still is not entirely clear to me. I am currently running with a personal token but would like to buy our licenses once I can figure out what I need.

Landscape vs Registrations Remaining vs Pro for Managed Computers. 

My Ubuntu Pro dashboard show 5 free personal tokens, with 2 active machines. This makes sense as I have 
- 1 hypervisor, running proxmox (debian), on which I'm running two VMs
   - 1 landscape server (ubnt 2204)
   - 1 landscape client (ubnt 2204)

My Landscape Dashboard lists 1 computer registered with "Remaining registrations: 59". However the breakdown on /account/standalone shows:
Registered computers: 1
Remaining full registrations: 9
Registered VMs, remaining VM registrations: all 0 
Remaining container registrations: 50

When I go to the 1 landscape client Pro Tab in the Landscape dashboard, (/account/standalone/computer/1/ubuntu_pro_info), it says:
> "This computer is not attached to an Ubuntu Pro entitlement"

When I go to the 1 landscape client Info Tab in the Landscape dashboard, (/account/standalone/computer/1/info) it says:
> Landscape, 356245 days left, 9 seats free

When I try to change the license to:
> Landscape for containers, 356245 days left, 50 seats free
It pops up an error:
> Computer 'XXX' cannot be associated with a virtual machine license
It's confusing because the license is called "container" but the error is related to a VM license.

Both landscape-licensed computers (client and server) are VMs running on the hypervisor. 

I would like help to understand:
- Where do all these different quantities of license, token, etc come from?
- What is the license quantity I need to purchase to run 3 hypervisors, running ~30 VMs

---

