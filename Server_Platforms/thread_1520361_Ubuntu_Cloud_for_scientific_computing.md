---
title: "Ubuntu Cloud for scientific computing"
date: 2010-06-29
forum: Server Platforms
---

### Post by vortmax on 2010-06-29
I've hunted on the internet for an answer to this but haven't found much besides buzz about eucalyptus being the greatest thing since sliced bread.

I have a small cluster made up of 4 multi-core machines in my research lab.  We used to use it as a distributed environment using matlab's parallel computing tool box, which works like a standard MPI type cluster.  We wound up not needing that massive parallel capabilities enough, so all of the blades have sort of been retasked to other things, making it more a collection of computers than a cluster.

So I'm thinking about wiping the entire thing and setting it up as cloud, but I'm not sure if it will work the way I want.  Most of our programs and code that are computationally intensive are designed to work with multiple/multi-core procs.  Does anyone know how this type of code runs on this platform?  If I allocate 8 procs to a VM, would the software running in the VM be okay with that?

I might just have to try it and see what happens.

---

### Post by stlsaint on 2010-06-29
[quote[If I allocate 8 procs to a VM, would the software running in the VM be okay with that?[/quote]


Im not sure but im thinking really basic on this and saying that as long as the guest/host OS supports you allocating these resources than yes it will work.

---

### Post by vortmax on 2010-07-07
well I'm not quite sure how the cloud virtualization works.  All of my experience in the field is with VMware, in which you create a VM, allocate a number of procs, RAM, HD space, etc and install an os to the VM.  It looks like with the cloud computing, all of this is dynamic.

What I'm curious about is how the resources are viewed by the host OS when it gets distributed to the other machines.  For instance, if I'm running a matlab script, would matlab just see a single proc (so the job is distributed to multiple machines without matlab knowing it), or would matlab see multiple procs and be able to use it's internal parallelization to take advantage of that.  My worry is that if it's the former, it will actually be a performance hit with all of the overhead, while the latter could be a major performance gain.

---

### Post by sh1ny on 2010-07-07
Cloud != virtualization.

The cloud software that comes with ubuntu **uses** virtualization ( KVM/Xen/VMWare ). So it's no different than running a bunch of virtual machines or a bunch of nodes. Well, with the exception that it manages where each guest is launched and things like that. But in general if you can run an app on 8 cores in KVM/VMWare/Xen, then you can run it on a cloud also, because it's again KVM/VMWare/Xen.

---

