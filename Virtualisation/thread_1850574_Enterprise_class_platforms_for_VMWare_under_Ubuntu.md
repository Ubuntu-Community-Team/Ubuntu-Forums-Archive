---
title: "Enterprise class platforms for VMWare under Ubuntu"
date: 2011-09-26
forum: Virtualisation
---

### Post by DaleAmon on 2011-09-26
I've been tasked with finding a good solution for a first move to virtualization in a corporate rack. We're going to virtualize a bunch of servers and move them to a couple 'cloud machines'.

I'd love to get some inputs on what people find reliable and good value for money in this area. We need to be able to handle a fair number of VM's; we will be using VMWare; most of the VM's will also be Ubuntu but eventually there will be a couple of Windows VM's for Exchange.

Reliability is important. We are talking critical/core business functions.

Dual power supplies are a given. 

I presume we'll want a fair number of cores and many GB of RAM per CPU.

I'd prefer to have SAS/SATA drives. SCSI are just not good value for money
any more. I've worked with the big Intel Servers and that is my biggest complaint about them. I want multi-terabyte drives, not the itty-bitty overpriced disks you can get in SCSI these days.

Two gigE ports, preferably built in. Could take more but that is not a crucial item.
 
A serial port so we can connect to a KVM over ether box.

Ubuntu friendly goes without saying.

Hardware virtualization goes without saying.

I've built machines myself like this from scratch but in this case I'd rather have one with a vendor warranty and a service guarantee. Having one of the boxes go down during critical business meeting could be very costly.

So what are other people who are in a similar enterprise system situation using?

---

### Post by HermanAB on 2011-09-27
Get Vmware Workstation.  You won't be sorry and you'll never look back.

---

### Post by fjgaude on 2011-09-27
Likely you already have considered this: call-in HP or some other known company to make you a proposal, issue an RFP, and see what comes of it.

---

### Post by DaleAmon on 2011-09-27
Yeah, we will ultimately be doing that. The trouble is salesmen will tell you what they want you to hear to buy their product. I'm interested in people's particular experience, good or bad, with enterprise servers in virtualization usage. For example, I've used some of the Intel big iron, but they still go with small SCSI drives, some use pseudo RAID, and the really big ones are operationally complex for a medium size company. But that is in a different application set. 

So again, what are the lemons and what are the peaches for hardware to host critical service virtual machines?

---

### Post by dcstar on 2011-09-28
> **DaleAmon said:**
> 
.........
So again, what are the lemons and what are the peaches for hardware to host critical service virtual machines?

This is basically a pointless question in a forum like this, there are few here who are IT professionals with a level of experience close to being able to answer a question like that.

If you want professional level advice like that you will have to go and pay for it from a place that actually knows what they are talking about.

---

### Post by bodhi.zazen on 2011-09-28
RHEL would be the alternate to VMWare.

[http://www.redhat.com/virtualization/rhev/server/](http://www.redhat.com/virtualization/rhev/server/)

You are on target with hardware requirements. Do not forget a backup strategy.

---

