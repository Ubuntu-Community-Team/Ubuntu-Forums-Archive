---
title: "Instance not running"
date: 2012-02-04
forum: Ubuntu Cloud and Juju
---

### Post by AkshayLive on 2012-02-04
OK. I am new to cloud computing and need help real soon. 

I am building a cloud just for test purposes so I created 2 VMs on VMWare - one for NC and one for CC.

Let me tell you more bout my setup.
Processor: Quad core AMD
RAM: 12 Gigs
Base OS: Vista, running VMWare workstation 8

Modem's IP - 192.168.1.1
Base OS(Vista)'s IP - 192.168.1.2

I have created two VMs - one CC(using UEC 11.04) and the other NC(also, using UEC 11.04). I have bridged the VM to my modem so CC has IP 192.168.1.6 and NC 192.168.1.7

Also, the range of my Instance IPs is 192.168.1.100-192.168.1.199

I can ping each other and can even access web front end using my Vista(Base OS). I installed an image from UEC store and can even view the images on my elastic fox(on my Firefox on Vista). So, all connections etc are working fine. euca_conf --list-walruses, --list-nodes, --list-clusters, --list-scs, etc are producing expected outputs.

When I try to instantiate an image using elasticfox or otherwise, it goes to pending state. After an hour or so, it terminates saying "Instance expired after not being reported for 600000 ms". It has however gone to "running" state only once and I could not SSH into it nor ping it.

nc.log has error:
libvirt: internal error no supported architecture for os type 'hvm' (code=1)
hypervisor failed to start domain
state change for instance i-4E2F0876: Staging -> shutoff (Extant) 
libvirt: Domain not found: no domain with matching name 'i-3E6007A7' (code=42)
cleaning up state for i-3E6007A7
vmru...

Remember, once it has gone to running state. I want it back! :(

---

