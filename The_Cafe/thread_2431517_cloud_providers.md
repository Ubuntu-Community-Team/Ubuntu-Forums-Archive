---
title: "cloud providers"
date: 2019-11-17
forum: The Cafe
---

### Post by Skaperen on 2019-11-17
i already know of a few cloud providers and already use AWS.  i am looking to expand my cloud usage.  i am only interested in those that offer IaaS (infrastructure as a service) on a time-used basis.  although i intend to also use other services they might have, time-used IaaS is the critical requirement.  i have tried to sign up at a few others but discovered their IaaS offering is not time-used.  it's more like VPS, where you rent a whole server for a whole month or as many as you want.  and i am not interested in Azure or Google.  **any suggestions out there?**  being able to run the cloud version of Ubuntu there is a big plus (as i do at AWS).

---

### Post by SeijiSensei on 2019-11-18
[Linode](https://www.linode.net) charges for time used. I don't know what "infrastructure-as-a-service" is though. I just rent entire virtual machines and configure them to my liking.

---

### Post by esa1975 on 2019-11-18
I run mainly web services but some basic infrastructure as well on both Vultr and DigitalOcean. Both are VPS hosts with similar pricing, their own infrastructures and so on. Vultr has many more locations so it's easier to find a server near where it's needed.

---

### Post by Skaperen on 2019-11-18
"infrastructure-as-a-service" basically means that the provided service is a software managed data center infrastructure where you configure what the hardware layer looks like (including networking), even though it is literally a couple layers higher.  i can attach storage volumes to virtual machine instances at whatever position i want.  and lots of big ones if i want to pay that much.  if i briefly need to have 8 TB of disk space, i can create it and delete it when i am done, paying for it only for the time it exists and the I/O operations i do.  there's a way to create many instances of an unimaginably huge NFS file structure that you pay per allocated file and can share among many virtual instances (i even tunneled it to my laptop once).

---

### Post by Skaperen on 2019-11-18
> **esa1975 said:**
> I run mainly web services but some basic infrastructure as well on both Vultr and DigitalOcean. Both are VPS hosts with similar pricing, their own infrastructures and so on. Vultr has many more locations so it's easier to find a server near where it's needed.

i tried signing up on DigitalOcean once but i could not get past the need to set up a virtual server for a whole month.  i just wanted to try one for a couple hours (which would cost a few pennies, at most, on AWS).  so i didn't run anything.  i will give Vultr a try.

---

### Post by SeijiSensei on 2019-11-19
Linode offers storage at $0.10/GB/month with hourly billing.

[https://www.linode.com/products/block-storage/](https://www.linode.com/products/block-storage/)

---

### Post by Skaperen on 2019-11-20
i would want more than storage.  i want to be able to launch an instance set to run a particular thing that can shut itself down and disappear when done.  it should have cost from the start time to the end time.  that's how AWS EC2 works.  AWS can even do this on a bidding price demand basis so prices go down at time demand goes down.

---

### Post by disabled20191124 on 2019-11-29
I use [MEGA]("https://mega.nz/"), free 50 gB of storage. Fine by me since I use it only as third back up for my data.

---

### Post by Skaperen on 2019-11-29
> **SeijiSensei said:**
> Linode offers storage at $0.10/GB/month with hourly billing.

[https://www.linode.com/products/block-storage/](https://www.linode.com/products/block-storage/)

the hourly billing is at least better than monthly.   what about other resources?

AWS offers minute billing for instances/VMs.

---

### Post by Skaperen on 2019-11-29
> **disabled20191124 said:**
> I use [MEGA]("https://mega.nz/"), free 50 gB of storage. Fine by me since I use it only as third back up for my data.

storage is just a start.  i need other cloud service to go along with it.  also, MEGA bills monthly quantity.  that is probably OK since the bulk of my data just sits there all the time.  but some comes and goes and this billing model may mean i have to pay the peak level all month, or worse, pay an estimated level all month.  but i will need networking, database, web service, and computing.

i also need system image storage that instances or VMs can be launched from.  and it needs to be R/O shareable to other users.

---

