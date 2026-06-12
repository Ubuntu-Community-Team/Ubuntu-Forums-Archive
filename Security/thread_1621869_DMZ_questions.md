---
title: "DMZ questions"
date: 2010-11-14
forum: Security
---

### Post by methodtwo on 2010-11-14
Hi there
I'm wanting to run a few servers at home and i want to segregate them from my client machines.Hence i want to run them in a DMZ. The architecture that i want to use is to have a triple homed, dedicated firewall to separate the internal segment from the DMZ. This dedicated firewall will have 3 network interface cards. One card will be attached to the ADSL router, another card will be attached to the DMZ and the other card will be attached to the internal segment.
I will use switches to connect the computers of each segment to each other and the firewall.
The network is depicted below:

```
   
   --------|                            |-------------|
   | ADSL       |------------|  Firewall              |--------DMZ segment
   | router     |                      | (triple-homed)  |
   --------|                      |-------|-----|
                                                        |
                                                        | Internal segment

```
My questions are: where do the servers in the DMZ get their I.P addresses from?. Where do the hosts on the internal segment get their I.P addresses from?. Where does the routers I.P addresses, for it's non-ADSL router interfaces, come from?. And should the interface between the firewall and the ADSL router be configured on the router to be part of the DMZ?. I'm guessing yes.
I wanted to have a dedicated firewall in addition to the packet filtering router, because the servers are in the DMZ after all. I just have no idea how to set this up.
Also i would rather have this architecture than a screened subnet architecture(where the DMZ plugs straight into the router and the internal segment is just protected by another packet filtering router)
Thank you so much for your time
regards

---

### Post by methodtwo on 2010-11-14
Sorry the diagram didn't look anything like how it looked when i did it!. I hope you get the idea though

---

### Post by methodtwo on 2010-11-21
Please ignore the above post i've thought about the question and have worked out what to do.Sorry to waste your time

---

