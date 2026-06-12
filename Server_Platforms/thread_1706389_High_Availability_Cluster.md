---
title: "High Availability Cluster"
date: 2011-03-13
forum: Server Platforms
---

### Post by paulmchugh on 2011-03-13
Hi All,

I'm new to Linux and the forums here (first post) so please be gentle!

I'm looking to set up a high availability server cluster to run a LAMP stack and a few other services. I've done a fair bit of googling and played around with some virtual 10.04 server builds and everything seems to be making sense, but I just wanted to check with those in the know.

Essentially what I am planning is 3 physical servers running 10.04 server and KVM as a host for two virtual 10.04 server machines. One will be the main LAMP node and the other to act as a load balancer. So I will have 3 virtual LAMP servers and 3 load balancers running to give maximum uptime.

Firstly, is this a good way to go or will this virtual setup eat my system resources (fairly old servers, HP Proliant ML370 G4).

Also, am I correct in assuming that the load balancers will distribute the workload eavenly across all availble LAMP nodes so I don't have redundant servers sitting there 'just in case'?

And assuming that all of the above makes sense, where would I best sit Squid and DansGuardian as a proxy? I'm not sure if the LAMP servers or the load balancer machines would be most economical?

One last thing; I've played around with ebox and webmin for some remote configuration. Webmin seems pretty complete but I'm sure I read somewhere that it doesn't always play nicely with Ubuntu - any thoughts?

Grateful for any pointers or words or encouragement!

Thanks,

Paul

---

### Post by paulmchugh on 2011-03-14
OK, a little complication; I've just run:

egrep -c '(vmx|svm)' /proc/cpuinfo

and it looks as though my server CPU does not support hardware virtualization.

Where does this leave me with regards to setting up these virtual servers; should I install X and use something like virtualbox or is this going to eat away at performance too much?

Another options I've thought of is to use the servers with a standard Lucid build to handle the LAMP stuff and setup a number of old P3 laptops we have lying around to take care of the load balancing / Squid services. My reservation here is that the laptops of course only have one NIC and I understand that load balancers work best with 2. Aghhhhhhh!

Thanks

---

### Post by paulmchugh on 2011-03-15
So I dug out the old P3 laptops to have a play, only to discover they don't have network cards at all - nightmare!

I've now got vbox running headless and installing a Lucid server guest to act as my first load balancer. Not sure what performance will be like, but at least I can add extra NICs and use bridge mode to make sure the throughput is up to the job.

I'd still appreciate some pointers on where to sit the Squid proxy or any other thoughts about this whole configuration if anyone wants to chime in.

Paul

---

### Post by BkkBonanza on 2011-03-15
VirtualBox is pretty good as far as cpu overhead. I think only a few percent lost. 

For a server solution I'd try out [OpenVZ]("http://wiki.openvz.org/Main_Page") - it's the open source version of Virtuozzo, which is used world wide by many, many VPS hosting providers. I used it for a while as a test, setting it up on my server and running several virtual servers on it. It also has very low overhead but is more suited to typical hosting arrangements. There are some control panels that let you manage the servers from a web based interface.

I see they even have a LiveCD now so you can boot and test run it without an install.

And there's Xen as well, which is what Amazon EC2 is based upon (I've heard).

---

### Post by paulmchugh on 2011-03-15
Thanks bkk,

Do you have a feel for how I should allocate memory to the VMs whilst still leaving enough for the host server? I've got 1.5Gb to play with but I'm thinking the load balancer VM won't need as much as the Lamp VM? Would 256mb be enough for the host or should I give it 512?

Thanks again,

Paul.

---

### Post by BkkBonanza on 2011-03-15
It would just depend on what you want to run on each server. For tasks requiring little memory there is no reason to waste it by allocating too much.

Also some apps are ridiculous in their memory footprint. Apache is pretty bad that way and will consume a lot of memory for each process it starts. On the other hand I always use Nginx now and it takes almost no memory. Same can be said for several other server apps. eg. Bind vs. TinyDNS, and so on.

I used to run a VPS sized at 64MB and it worked fine. But most hosting providers that offer VPS systems wouldn't offer one so small because most people want to use Apache and it needs more. But I can run Nginx, qmail and TinyDNS all in less than 64MB. So it all just depends on your app requirements. 

You can adjust size afterwards to fit, so start with something like 256MB and run it in a typical load and see how much memory it uses, and then scale it down/up to suit. Also, if you don't have a bunch of non-essential stuff running then it helps. On servers I generally remove as much as I can for security reasons but it also helps for memory too.

MySql is going to depend on a lot of other factors too. It really only needs a lot of memory for highly active large size databases. Most of it used for table caches but you can control that in the config file. 

I run Nginx, PHP and MySql on my VPS now and it generally only uses about 96MB. My VPS is sized at 1024MB but that's only because of the deal I got when I started and honestly it never uses that. But it's not that busy either. From what I recall with Apache (years ago now) it was taking about 16MB for each process. Nginx is using something around 1-2MB for any number of worker threads. 

I always find it amusing when people pay so much more to have extra memory when by just changing their web server program they could cut it way down, and their costs too. So, anyway, that's just some of my experience over the last few years. I don't think a load balancer would need much memory. 

Nginx can be used as a load balancer too so I don't imagine it should use more than that though I've never used it that way.

---

