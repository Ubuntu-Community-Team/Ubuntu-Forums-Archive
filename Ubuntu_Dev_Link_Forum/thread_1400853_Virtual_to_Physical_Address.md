---
title: "Virtual to Physical Address"
date: 2010-02-07
forum: Ubuntu Dev Link Forum
---

### Post by DBQ on 2010-02-07
Hi everybody. Is there a way to find out all PHYSICAL addresses which belong to the specific process? I do not care whether we do it from user space or kernel space.

I was able to get the virtual address ranges for stack, heap, and etc for the process. However, my understanding is that I cannot simply use virt_to_phys or similar function to convert the starting and ending address of the memory range I want. This is because these address ranges, although virtually contiguous, may not necessarily be physically contiguous (No?)

Also, when using virt_to_phys to convert a start of the memory section virtual address to physical,  the value I get is ridiculous -- it exceeds the physical memory size.  What I am doing wrong?

Also, is there a way, given a physical address, to find out to which process it belongs to right now (i.e. I think the same physical address can correspond to multiple virtual addresses, so at different times a different running process may be using the same physical address).

Thanks for your help.

---

### Post by Maz_ on 2010-02-12
i cannot really give answers, but i can confirm some assumptions. So yes, even if some virtual address block was continuous, physical needs not to be. It is often highly HW dependant how physical addresses are used. There may be some I/O memory, which can be assumed continuous, but standard mem cannot. And yes, same physical mem can be mapped for different processes, thats the usual case with shared libs for example.

---

### Post by Maz_ on 2010-02-13
Allright. After a little investigation upon virt_to_phys, it seems that can only be used for kmalloc'd memory, or directly mapped IO mem. But you may (or may not) find this interesting:
[http://www.scs.ch/~frey/linux/memorymap.html](http://www.scs.ch/~frey/linux/memorymap.html)

---

