---
title: "KVM Guest actual memory ~2% less than given maxmem."
date: 2012-01-31
forum: Virtualisation
---

### Post by CyberAngel on 2012-01-31
Hello,

I realized that when I create KVM virtual machines, they end up having approximately ~2% less memory than the actual max memory given.

For example if I set the max and current memory of a VM to 1024MB of RAM, if I boot it up it will have 997MB of RAM

```
virsh setmaxmem --kilobytes 1048576 VM_Name
virsh setmem --current --kilobytes 1048576 VM_Name
```

For 2048MB it will actually have 2007MB and for 10240MB, 10021MB respectively.

Anyone knows why?
I made some research but I couldn't find an explanation to this.

---

### Post by Alex.Han on 2013-02-04
Any ideas with this question?

I'm also facing similar problem. I Can live with it, but some people complains with the absent memory.

In my case, a VM instance is assigned 8GB of memory, but checking it with top command in the  guest os shows 7.7GB.

---

### Post by CyberAngel on 2013-02-04
> **Alex.Han said:**
> Any ideas with this question?

I'm also facing similar problem. I Can live with it, but some people complains with the absent memory.

In my case, a VM instance is assigned 8GB of memory, but checking it with top command in the  guest os shows 7.7GB.

This is some memory overhead introduced by the Hypervisor to handle the virtual machines, and to let memory overcommitment and dynamic allocation methods like ballooning and shared memory work. It has to do with the internal datastructures of the hypervisor.

I was writing a master thesis and I had to use virtualization when I asked this question but haven't looked deep into many details for the overhead reasons as this is another topic itself :)

---

### Post by Alex.Han on 2013-02-04
Thanks, @CyberAngel

But can you provide me some link stuff so that I can read and understand the reason why that particular memory gap exists?

---

### Post by CyberAngel on 2013-02-04
> **Alex.Han said:**
> Thanks, @CyberAngel

But can you provide me some link stuff so that I can read and understand the reason why that particular memory gap exists?

Make a generic search for virtualization overhead and not only for "memory overhead". You will get many more results on explaining why virtualization has overhead.

I haven't found so many papers addressing the memory overhead clearly but if you read this one it's explaining how VMware hypervisor deals with memory:
[http://www.vmware.com/files/pdf/perf-vsphere-memory_management.pdf](http://www.vmware.com/files/pdf/perf-vsphere-memory_management.pdf)

This link also has an interesting discussion:
[http://communities.vmware.com/message/1994605](http://communities.vmware.com/message/1994605)

A few more quick links:
[http://www.vkernel.com/files/docs/white-papers/vm-memory-vram-sizing-considerations.pdf](http://www.vkernel.com/files/docs/white-papers/vm-memory-vram-sizing-considerations.pdf)
[http://homepages.dcc.ufmg.br/~fabricio/download/ccc07.pdf](http://homepages.dcc.ufmg.br/~fabricio/download/ccc07.pdf)

---

### Post by Alex.Han on 2013-02-04
Thanks a lot, CyberAngel.

---

### Post by wildmanne39 on 2013-02-04
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

