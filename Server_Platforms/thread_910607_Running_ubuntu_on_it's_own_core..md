---
title: "Running ubuntu on it's own core."
date: 2008-09-04
forum: Server Platforms
---

### Post by Sir Jake on 2008-09-04
Hello there, I am looking for a how to on making Ubuntu run on it's own core. It would be very handy for my quad core servers and dual quad cores. I tried a little search on here and Google. 
Thanks for any help.
Jake

---

### Post by promodus on 2008-09-04
I think what you're trying to describe is a

"Bare metal hypervisor"

---

### Post by Sir Jake on 2008-09-04
Nope, not trying to setup a vmware server.
I run game servers from my dedicated servers and it would help with performance being able to have the system only run on one core of the server so the other cores will not have a load switched onto them.

---

### Post by promodus on 2008-09-04
VMWare GSX or ESX?

---

### Post by windependence on 2008-09-05
> **promodus said:**
> VMWare GSX or ESX?
Either of these would work but not the way he thinks it might work. To my knowledge. there is no way to limit traffic to just one core, and why would you want to anyway? for gaming, the load balancing that happens on die in the CPU is much better than trying to use just one core exclusively. I don't think you would gain anything useful from doing this.

VMware ESXi is free if you want to experiment with that but for gaming, virtualization usually doesn't work well.


-Tim

---

### Post by promodus on 2008-09-05
This is incorrect:
> **windependence said:**
>  there is no way to limit traffic to just one core

```
man taskset
```
The definition to this would be process affinity. 

Windependence raises a good point, I/O Latency could be an issue.
IF it works, it works.

VMWare ESX Server is a bare metal hypervisor, I do not know how to set affinity to a process or virtual machine, yet. 

VMWare GSX Server is hosted, you'll have to set the affinity.
do a 

```

CORE=0
VMXNAME=name_of_your_vmx.vmx
taskset -c ${CORE} -p $(ps x | grep ${VMXNAME} | grep -v "grep" |  awk '{print $1}')
```

If you need a breakdown, bump.

---

### Post by windependence on 2008-09-05
I don't think you can turn off the scheduler in ESX, and it probably wouldn't be agood idea anyway.

As you said, in GSX or VMware server, you could probably do it but again, I am quite sure performance would be pretty bad. This way, you can't take advantage of unused CPU cycles that would otherwise be available.

I didn't even think about the affinity angle, but yes, you COULD do it but I wouldn't necessarily WANT to. ;)

-Tim

---

### Post by Sir Jake on 2008-09-06
Hey thanks guys, I never thought about it like that. 
I'll just stick to taskset and run each one on it's own core. :)
Thanks for the help.

---

### Post by windependence on 2008-09-06
Check it for yourself but I would bet you will actually see a DECREASE in performance that way. Please let us know how it turns out though, I am curious. ;)

-Tim

---

