---
title: "Resolve External Requests to internal machines"
date: 2011-09-25
forum: Server Platforms
---

### Post by admiralfreak on 2011-09-25
I'm trying to resolve external DNS requests to my internal server but am unsure of how to accomplish this.

I own the domain 'site.co' (for example). What I want to be able to do is access a specific machine by going to 'machine.in.site.co'. I have an internal DNS server setup that lets me access the machines with machine.in.site.co.

How do I set it up so that requests from outside of my network to machine.in.site.co go to that specific machine? I am using GoDaddy's DNS service if that helps.

Thanks!

---

### Post by volkswagner on 2011-09-25
Do you have multiple web servers running or are you trying to utilise file share accessing various machines?

If you are running multiple webservers you may want to look at running a reverse proxy to point to individual machines.

---

### Post by admiralfreak on 2011-09-25
I have 1 server that is running a bunch of VMs. What I'd like to do is set it up so that I can access each of these machines (not all webservers) as <machine name>.in.site.co. This would primarily be to SSH in.

Right now, the machines are:
physical (physical machine), vm1, and vm2. What I want to do is be able to access the services for each machine. So physical.in.site.co:22, vm1.in.site.co:22, and vm2.in.site.co:22 to ssh in.

I only have 1 external IP address so I guess what I need to figure out how to do is route external requests (vm1.in.site.co) to a specific internal ip address (192.168.1.x).

Thanks

---

### Post by patryk77 on 2011-09-25
That's not really feasible on a single Public IP.

Sure, you can make different entries, but they will all point to the same IP.

What you would need to do is forward different ports.

Say you want to SSH, you could forward ports:
2201 &#8594; Machine 01
2202 &#8594; Machine 02 
...
22XY &#8594; Machine XY

Same thing for Apache (8001-80XY).

That would tell you the protocol (or the base port) and the machine number all in one.

---

### Post by admiralfreak on 2011-09-25
Thanks for the help. I had been trying to imitate my school's CS lab but I just realized/figured out that the lab machines all have their own IP addresses. I had been going on the assumption that they didn't.

What I'll end up doing is set up so that I ssh into the physical server and then ssh into the different virtual servers and do all the configuration internally.

Thanks again.

---

