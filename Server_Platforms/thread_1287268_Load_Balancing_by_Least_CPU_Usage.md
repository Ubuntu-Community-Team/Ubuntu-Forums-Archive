---
title: "Load Balancing by Least CPU Usage"
date: 2009-10-09
forum: Server Platforms
---

### Post by NaOH on 2009-10-09
Hey Everyone,

I'm seeking some general guidance, or even speculation on how one may achieve load balancing based on cpu and memory usage.  The idea is this:  I have a 4 terminal servers awaiting usage, and in front of them I have a pair of load balancers issuing this cluster a virtual IP.  So ideally these load balancers would hand off each terminal connection request to the least busy terminal server.  Are these terminal servers MS? Nix? Doesn't matter to me yet.  I'm just looking to see if this is an achievable model.

Secondly, may this be achievable with Layer 4 load balancing?  I've never dealt with Layer 7, and in some ways it seemed fitting considering we are dealing with the application level here, but then again we are dealing with one service alone.

Any advice/insight is most welcome, thanks!

---

### Post by Xianath on 2009-10-10
What kind of load balancer are you employing? It mostly really depends on their own capabilities. The ones I've seen would balance on the number of connections/datagrams (Layer 4) or number of protocol requests/sessions (Layer 7). Windows load balancing (NLBS) even does it at the OS/cluster level itself, not externally, but its recommended use is for stateless protocols, which is quite orthogonal to terminal servers.

Or am I misreading the question and you're still in the planning stages?

HTH,
Peter

---

### Post by NaOH on 2009-10-10
Hey Peter,

I am still in the planning stages, but that is more information than I had.  The load balancers I'd like to employ would be something I'm comfortable with: Ubuntu Server 8/9 + Ultramonkey.  I've had great results using such setups for simple high-availability scenarios for Apache clusters; however, I would be more than willing to strike outside of this setup if necessary.

I did read up on Microsoft's solution for this and I was green with envy:  Seems these load balancing features do just what I'm asking, and its a standard built-in feature.  But whats the fun in that?

More importantly I'm not really looking to deploy a MS Terminal/Citrix environment (yet).  I'll have to retract that statement about the terminal server specifics not being my concern; I'm really looking for these load balancers to be serving a cluster of OSX Servers running Aqua Connect, the Mac terminal server.

---

### Post by NaOH on 2009-10-11
Here is a little of what I found on this:

[http://wiki.linuxquestions.org/wiki/LVS_with_HA_for_Win2k_Terminal_Servers](http://wiki.linuxquestions.org/wiki/LVS_with_HA_for_Win2k_Terminal_Servers)

Here is the same model, but for high availability

Now this I find most enticing:

[http://ganaderia.sagarpa.gob.mx/tarantella/help/en-us/admin/t3loadbal_config.html](http://ganaderia.sagarpa.gob.mx/tarantella/help/en-us/admin/t3loadbal_config.html)

"The Least CPU Usage and Most Free Memory methods calculate the true load of the application server when a user launches an application."

But this is is for Sun Secure Global Desktop.  Its not ubuntu, but a lot closer than MS.

---

### Post by NaOH on 2009-10-14
Bump:  I've been scouring around about this for a while and I wonder now if this is even an open source option yet.  All solutions for cpu/memory load balancing I've found so far are either an MS product, or a paid-for third party solution.  Maybe we should generalize again:  Is there a project for cpu/memory load balancing within Debian?

---

### Post by Xianath on 2009-12-07
I really am not familiar with Linux load balancing solutions. My experience is more around commercial solutions such as F5 BigIP and Cisco CMS. [This]("http://lcic.org/load_balancing.html") looks like a good place to start. Also, the VMware virtual appliance marketplace hosts some projects that can at least tip you in the right direction. Sorry if I can't be more specific. The few times I've looked into setting up Ubuntu as an LB, I've given up. Maybe you'll have more luck, or maybe things have changed in the past couple of years.

Cheers,
Peter

---

