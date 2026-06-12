---
title: "DB Server -- requirements?"
date: 2011-07-08
forum: Server Platforms
---

### Post by garfonzo on 2011-07-08
Hey Folks:

I need to figure out what an optimal server solution would be for me. I can't decide if I need one big server, or many small servers. 

What I am doing is providing clients their own MySQL database which is accessed and used via a web frontend. Each client will be creating thousands, if not hundreds of thousands of records every year. Further, each client will likely have some reports generated using JQuery to make it "pretty". 

So, essentially I need to be able to run several MySQL databases at once, handling millions of records, all through multiple web front ends. I want to do all of this through Amazon's EC2 service running Ubuntu, but I don't know if I should set up a single instance for every client, or create one big instance to handle all clients. At this point, I only have 2 clients, but I may have 5 or so in the next year or two. 

It seems easier (from a security and setup perspective) to simply assign a new instance for every client, but I'm not sure if that is too much processing power and, therefore, a waste of money. However, setting up one powerful server instance will require a lot more setup to handle multiple web frontends and multiple databases. 

Any advice? 

A "Small (standard) Instance":
- 1.7 GB memory
- 1 EC2 Compute Unit (1 virtual core with 1 EC2 Compute Unit)
- 160 GB instance storage
- 32-bit platform
- I/O Performance: Moderate

A "High-Memory Double Extra Large Instance":
- 34.2 GB of memory
- 13 EC2 Compute Units (4 virtual cores with 3.25 EC2 Compute Units each)
- 850 GB of instance storage
- 64-bit platform
- I/O Performance: High

Of course, there are other larger instances, and some smaller instances, but I thought I'd give an idea of what I'm looking at. 

Thanks!

---

### Post by headvampyre@hotmail.co.uk on 2011-07-08
I would say neither of these. Try and get 2 servers with these specs:

24GB RAM
x86_64(Or look out for a 128-bit CPU) - at least 8 cores for the server
500GB storage W/Raid Array
High I/O performance
4+ 1Gbit network adapters

Then cluster them together. You could also try bonding the adapters :) 
You'll wanna use VMWare server to separate each virtual server, and have a VLAN for each one.

---

### Post by garfonzo on 2011-07-08
> **headvampyre@hotmail.co.uk said:**
> I would say neither of these. Try and get 2 servers with these specs:

24GB RAM
x86_64(Or look out for a 128-bit CPU) - at least 8 cores for the server
500GB storage W/Raid Array
High I/O performance
4+ 1Gbit network adapters

Then cluster them together. You could also try bonding the adapters :) 
You'll wanna use VMWare server to separate each virtual server, and have a VLAN for each one.

OK, but your response seems to imply that I would be purchasing servers to set up this configuration. I want to achieve all of this using Amazon's EC2 service. I simply do not have the capital to purchase servers of this magnitude, nor a proper place to run them. Hence, I will be using the EC2. 

Perhaps I'm misunderstanding your response?

---

