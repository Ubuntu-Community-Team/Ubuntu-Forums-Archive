---
title: "Difference between a CPU's cache and register"
date: 2007-05-15
forum: The Cafe
---

### Post by ubuntukid on 2007-05-15
I'm reading up on computer and I'm having a hard time working out what the difference between the CPU cache and register are. From the little information I've found, it seems almost as though they perform the same task which confuses me. As far as I can tell, information going from RAM to, for example, the ALU first goes through the cache, then the register and into the ALU. Now I've found plenty of information on the cache about how it's used to store bits of information which are used several times during a task and is stored in the cache because it is much faster to access than RAM. But what is the purpose of the Register?

---

### Post by mips on 2007-05-15
[http://en.wikipedia.org/wiki/Processor_register](http://en.wikipedia.org/wiki/Processor_register)
[http://en.wikipedia.org/wiki/CPU_design](http://en.wikipedia.org/wiki/CPU_design)
[http://portal.acm.org/citation.cfm?id=17400&dl=ACM&coll=GUIDE](http://portal.acm.org/citation.cfm?id=17400&dl=ACM&coll=GUIDE)
[http://portal.acm.org/ft_gateway.cfm?id=17400&type=pdf&coll=GUIDE&dl=ACM&CFID=18753989&CFTOKEN=71942766](http://portal.acm.org/ft_gateway.cfm?id=17400&type=pdf&coll=GUIDE&dl=ACM&CFID=18753989&CFTOKEN=71942766)

Read the above, especially 1.2 in the PDF file.

---

### Post by saulgoode on 2007-05-15
Accessing registers is faster and more efficient than accessing cache. This is mainly owing to the register's "address" being encoded into the opcode of the machine instruction. For example, "add eax, ebx" only requires a 32-bit instruction because the source and destination are both encoded into the opcode; "add eax, 0xffffffff" would require at least 64-bits of instruction because the memory address needs to specified. There might also be a delay in cache handling/translating the memory address but in an ideal world this should not be necessary (i.e., it takes place in less than a single clock cycle).

Another difference is that cache can contain instruction code whereas registers cannot. You might have a very efficient code loop that executes entirely from the cache and never needs to access off-chip memory. Machine instructions are not stored in registers.

I would also assume that in multiple core processors, registers share a common cache. You may have two sets of registers (and two ALUs) on the same chip operating in parallel, but when cache memory is accessed it is from the same location. (I am not certain of this, but it would be how I would design things :) ).

---

### Post by Daveski on 2007-05-15
Nice description by saulgoode.

In simple terms, the cache is rather like the disk cache which means that access to data stored on a slow device like a hard disk can be cached in a faster store like system memory. The CPU cache uses very high speed memory on chip to speed up access to the much slower system memory. In both cases clever algorithms can be employed to 'look ahead' and pre-cache data which is likely to be used.

The Registers are rather like variables in a high level language and are used to store values which are actually being processed. For example with C = A + B, the values of A and B are loaded into Registers (like assigning variables) and then the instruction 'add A and B and store in C' is executed. Sometimes the next instruction would be to place this value back into system memory (probably via the cache to speed up instructions which subsequently read this value).

---

### Post by Polygon on 2007-05-15
the cache is "farther away" then the register.

The register is really freaking fast and really freaking small memory used as temporary storage places when the processor is adding, subtracting or comparing stuff. The cache is used for storing information that does not need to be referred to as often.

---

