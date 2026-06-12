---
title: "Connect virtual routers together"
date: 2014-10-02
forum: Virtualisation
---

### Post by didigno on 2014-10-02
Hi All,

I am new as ubuntu user and I am trying to connect some routers together.

The point is that I am not able to interconnect the devices togther.

This is the output that I have:


bridge name    bridge id        STP enabled    interfaces
virbr0        8000.fe54005e407b    yes            vnet5
virbr1        8000.52540057a0d8    yes           virbr1-nic
                                                                 vnet1
                                                                 vnet4
                                                                 vnet7
virbr2        8000.5254007e8261    yes        virbr2-nic
                                                              vnet0
                                                              vnet6
virbr3        8000.525400371f5b    yes        virbr3-nic
                                                              vnet2
virbr4        8000.5254009849a6    yes        virbr4-nic
                                                              vnet3
virbr5        8000.5254007d75a7    yes        virbr5-nic
                                                              vnet8
virbr6        8000.525400be7348    yes        virbr6-nic



Now my question is the following:

I have 4 routers and I want to connect them togheter

R1-R2 port 1/1
R1-R3 port 1/3
R2-R4 port 1/3
R3-R4 port 1/1

How can I associate the right router with the right ports?

R1 o far is showing that 4 ports are up even though the routers are not runnnig.

Sorry if it is a silly question.

Thanks for you help

didigno

---

### Post by bashiergui on 2014-10-05
If the virtual routers are all running on the same host, you can NAT them instead of bridge them, that would route them all through your host. 

Maybe if you're more descriptive about your end goal you'll get better suggestions.

---

