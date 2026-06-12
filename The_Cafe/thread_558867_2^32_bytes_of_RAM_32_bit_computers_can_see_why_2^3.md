---
title: "2^32 bytes of RAM 32 bit computers can see why 2^32?"
date: 2007-09-24
forum: The Cafe
---

### Post by nb123 on 2007-09-24
I've been trying to read up on this to understand it better, but I'm having a little issue. I understand the RAM limitations involved with 32-bit computing but I don't quite understand how the number 2^32 is arrived at to calculate this 4GB theoretical limitation. I know that it's to do with binary math right? Because each bit is saved as either '1' or '0'. But then, wouldn't 2^32 be the total number of possibilities for the data stored in bytes, and not the actual number of bytes, i.e. 4GB of RAM?  Doesn't 2^32 calculate the possibilities since it takes into account all the combinations of each bit being either '1' or '0'? I'm not understanding this very well?

---

### Post by ~LoKe on 2007-09-24
The range of integer values that can be stored in 32 bits is 0 through 4,294,967,295 or &#8722;2,147,483,648 through 2,147,483,647 using two's complement encoding. Hence, a processor with 32-bit memory addresses can directly access 4 GiB of byte-addressable memory.

---

### Post by samb0057 on 2007-09-24
2^32 does not represent data storage, but a range of addresses.
Each possible number (0 through 4 billion whatever) can be used as an address for a byte of memory. Therefore, using 32-bit, we have 4 billion possible addresses, so 4 billion possible bytes of memory.

---

### Post by nb123 on 2007-09-24
ok I think I'm beginning to understand this more clearly, but I think I'm very confused about some fundamental concepts. So because a 32 bit processor can read a 32 bit location/address at a time, one can store 2^32 addresses of data, because a 32 bit binary line can store numbers 0 to (2^32) - 1 = 4,294,967,295, thus addressing a different location as a different number yeah?

But this is where I'm confused. In order to take advantage of having 2^32 different possibilities, we have to have 4,294,967,295 different 32 bit segments, each segment storing an address? Which means that we actually need 2^32 * 2^5 which is actually 2^37,  which is 128GB of space in order to store all the 2^32 different addresses? I'm really confused!!! :confused:

Also, if all this is being used as address space then where's the actual data being stored? I thought the RAM and L2 cache actually stored data and wasn't just for addressing data on the hard disk or something? :confused:

---

### Post by aks44 on 2007-09-24
> **nb123 said:**
> But this is where I'm confused. In order to take advantage of having 2^32 different possibilities, we have to have 4,294,967,295 different 32 bit segments, each segment storing an address? Which means that we actually need 2^32 * 2^5 which is actually 2^37,

Don't bother with segments. They are old stuff from the i286 ("real mode") era. Now every modern OS runs in "protected mode" where memory is adressed in flat mode. Each and every 32-bit address corresponds to one memory byte.

Granted, protected mode is a way more complex than just flat addressing. But basically that answers your question anyway.

---

### Post by nb123 on 2007-09-24
Okay I've clarified my thoughts a little more, and maybe I can clarify my question too. We can have 2^32 different bytes of memory, or rather 4GB of RAM because the 32-bit processor can only 'find' addresses that are 2^32 long. Thus, the processor searches for a particular address that is given and returns the byte of data associated with it. Please tell me if this is correct?

But if this is the case, then where is the address stored? Doesn't it also have to be stored with the RAM? Doesn't that mean that you need 2^32 * 2^5 = 2^37 bits of data for the addresses? i.e. 2^34 bytes = 16GB just for the addresses to be stored so that the processor can read it? Or is it the case that if the address is the number 13, which can be represented in 4 bits, then only 4 bits is needed for address space, and so the total sum of all address space would be lower?

---

### Post by nb123 on 2007-09-24
Wait so I just saw your message aks44, this would mean that it does need 32 bit for storing the address, so the RAM is 4GB + 16GB in total space like I said in my previous message, or no?

---

### Post by Henry Rayker on 2007-09-24
The processor doesn't read the addresses. The memory in a system has an address decoder built into it. The address decoder is basically logical gates that guide the data being stored to the proper location (or tell which location should write to the data out bus)

---

### Post by aks44 on 2007-09-24
There's no need to "store" addresses.

```
Address =  0 1 2 3 4 5 6 7 8 9 ...
Data    = [? ? ? ? ? ? ? ? ? ? ...]
```

The RAM only contains the "Data" part, it knows how to directly retrieve the data when it is given the address by the processor.

---

### Post by nb123 on 2007-09-24
Oooohhhhh, awesome, I think I get it now, at least better than before! Thanks a lot guys!

---

### Post by psusi on 2007-09-24
The addresses are stored in ram as well, but you don't need to store every possible address; you only need addresses that are important.  For instance, if there is a string somewhere in ram, you don't need the address of every byte in the string - only it's first byte.  

That address takes up 32 bits somewhere else in ram.

---

### Post by mridkash on 2007-09-24
Almost all basics of this stuff gets cleared when you read first few chapters of an assembly language book.

---

### Post by nb123 on 2007-09-24
ahh, that's probably why I haven't stumbled upon this info :), I'll put the assembly language book on my to-do list.

psusi - then how is the 1st byte linked to the 2nd? Is it to do with the way they are physically stored in RAM?

---

### Post by aks44 on 2007-09-24
> **nb123 said:**
>  then how is the 1st byte linked to the 2nd? Is it to do with the way they are physically stored in RAM?

If the first byte of the string is stored at, say, address X, then the second byte is at X+1 etc. Really, RAM is just a big unidimensional array of data (logically, not physically, mind you).

---

### Post by nb123 on 2007-09-24
cool, thanks man, I finally get the whole idea of how much RAM a processor can 'see'

---

### Post by nb123 on 2007-09-24
actually one more thing :), I know that even though 4GB is the techincal limit a 32bit processor can see, some of it is used to address other memory storage, like your video card for example and is therefore 'not seen' in your operating system so to speak. Is this because the addressing is done on the RAM because that's the only way the CPU can interact and locate data on other devices? Or does it depend on the device itself, whether the CPU can interact with it directly? Am I making sense? :)

---

### Post by aks44 on 2007-09-24
> **nb123 said:**
> 4GB is the techincal limit a 32bit processor can see, some of it is used to address other memory storage, like your video card for example [...] does it depend on the device itself, whether the CPU can interact with it directly?

Some devices are indeed "memory mapped", ie. the processor accesses them as if they were RAM (address + data buses). But they are not normal RAM, the OS can't store whatever data it wants there. So it doesn't count those areas as RAM.

Some other devices can communicate with the CPU through other means than the main bus (the so-called "I/O ports").

---

### Post by BuffaloX on 2007-09-24
You just be glad you never had to program 8 bit computers.
The 8 bit 6502/6510 processor in commodore 64 could access 128KB of memory.
Talk about painful programming...
This was possible because two registers were used for adressing, plus one extra bit for so called "shadow" RAM.

Actually the number of bits in the processor is not all ways the same as the number of address lines. I doubt todays 64 bit CPUs have 64 address lines.

The good old Motorola 68000 had 24 address lines, but was a genuine 32 bit CPU because it had 32 bit data lines, and worked internally with 32 bit.

When the CPU needs to read or write data to RAM, the address is stored in one or more address registers.
The maximum data to read is determined by the number of data lines.

A 32 bit CPU with only 16 data lines, will need to make two ram requests to read a complete 32 bit register. This was used for the old Intel 8088 Which was a 16 bit CPU with only 8 data lines. and the Motorola 68008 which was a 32 bit CPU with only 16 data lines.
This was done to make the systems cheaper, but of course it was also slower, because two data accesses to ram was needed instead of just one.

To sum it up, address lines and data lines are two completely separate things.

If you think of RAM like lots and lots of boxes. In some storage facility.
The boxes need to accessed by a mechanical arm.
The length of the arm determines how many boxes can be reached.
This would be equivalent to address lines.
Longer arm = more address lines.= ability to use more RAM.
If you only have few boxes, it doesn't help to have a longer arm.
And adding more boxes than the arm can reach wont increase how much you can store either.

Some arms are able to fetch only one box, so boxes are handled one at a time.
Better ones can handle multiple boxes at a time, so they can be filled or emptied 
simultanously. This would be like having more datalines.
If one box = 1 byte, ability to fetch 4 boxes is equal to 4 bytes = 32bit.

As you can see ability to fetch multiple boxes, and ability to reach far for the boxes, has nothing in common.

As mentioned earlier most assembler books will attempt to explain this.
They'll probably do a better job than this, so if this confuses you, don't despair. I think thats quite normal.

Ups this got a bit longer than expected.
Hope someone finds this useful. :p

---

### Post by nb123 on 2007-09-24
Thanks for the detailed response, but I'm not understanding it very well, do you think you could guide me a little more?

> 
If you think of RAM like lots and lots of boxes. In some storage facility.
The boxes need to accessed by a mechanical arm.
The length of the arm determines how many boxes can be reached.
This would be equivalent to address lines.
Longer arm = more address lines.= ability to use more RAM.
If you only have few boxes, it doesn't help to have a longer arm.
And adding more boxes than the arm can reach wont increase how much you can store either.


I have an Intel Core2 Duo T7200 (2 GHz/4MB L2 Cache) 32 bit x86 processor. It's 32 bit which means it can address 32 bits yeah, which means it has a much longer 'arm' than say a 8 bit processor that you mention. A normal 8 bit processor (not the special one you mentioned) can only address 2^8 locations right? So that'll be 256 bytes of RAM, my god that's horrible :), and even if it had 1GB of RAM it could not use all of it.

So that's to do with address lines right?

Now, I understand from your data lines explanation how the address and data lines are unrelated. The 8 bit processor may be able to address only 256 bytes but it can pull out all the bytes at the same time? :) Is it possible? But how do I find out how many data lines my processor has? Is it just 32 bit data lines?

Just to make sure I'm seeing this clearly, let's say you do confirm that my processor can access 32 bit data lines, the same amount as address lines. Then, applying these ideas to 64 bit processors, for it to be faster than a 32 bit processor (besides FSB being faster and other things I don't understand :)) , it could have 64 bit data lines that will enable it to pull data out faster? Correct? But it's ability to see 2^64 bytes of RAM is not related?

---

### Post by psusi on 2007-09-24
Your processor actually has 36 address lines and 128 ( or was it 256? ) data lines.  That means it can transfer 16 ( or 32 ) bytes at a time if it chooses to, and uniquely address up to 2^36 memory locations.  Since each memory location is defined to be one byte, that means it can address 64 GB of ram.  

Those are physical lines though.  Logically, programs only use 32 bits to address their ram, and those addresses are then translated from virtual to physical addresses via hardware and page tables.  This means that any one process can still only address 4 GB of ram ( some of which is used for the OS, typically 1 GB ), but the OS can set up the page tables of each process differently so that they are each using different parts of the 64 GB physical address space.

---

### Post by BuffaloX on 2007-09-25
Just like psusi says...

Processors are rarely pure 32 or pure 64 bits.
The processors have different units which each can work with different amount of bits.

The 6502 bit processor isn't special, other  8 bit processors were similar, 8 bit CPU's normally have 16 bit address space.

It could not "see" all memory at once, and it couldn't see 256 bytes at once. to do that an obscene number of data lines would be required. 256 bytes is equal to 4096 bits. to fetch and store that in one go, it would need 4096 data lines.
It only had 8 datalines, enabling it to see only 8 bit or one byte at a time.

In an 8 bit CPU accessing memory requires to use two registers.
You could say they could only fetch one box at a time, but had access to 256 rows in 256 columns of boxes a total of 256 x 256 = 65536 boxes or 64KB.
The 8 bit CPU cannot ask directly for box number 12000, because it's beyond the number it can handle. so instead it asks for box 224 in section 46.

Since the Pentium the number of data lines has been greater than the number of bits the CPU processes, the Pentium was 32 bit but had 64 data lines.
This can be used, because an extra "stage" has been added to the CPU pipeline. Which means the CPU can prefetch data to cache, so RAM operations are more efficient, especially when working with linear jobs like media encoding or decoding. When the CPU asks for boxes 24-27 the boxes 28-31 are fetched at the same time, and if the CPU asks for those next, they are ready in advance.

To sum it up.
RAM is accessed in bytes, the amount of bytes the CPU can access, depends on the number of address lines.
16 lines = 64 KB
32 lines =  4GB
36 lines =  64 GB

The amount of bytes that can be read or written in one go depends on the amount of data lines
8 lines = 8 bit = 1 byte
16 lines = 16 bit = 2 bytes 
32 lines = 32 bit = 4 bytes 
64 lines = 64 bit = 8 bytes 
128 lines = 128 bit = 16 bytes

Hope things are a little clearer now. :)

---

### Post by nb123 on 2007-09-25
Awesome, thanks man, okay, I get everything you're saying, one thing though, Since my processor has 36 address lines, but it's a 32 bit, I know it has like 8 registers or something? So that is how it's able to access like 64GB of RAM yeah? (psusi - I understand what you're saying about physical vs. logical) As in it must be doing something like the 8 bit processor is with its 256 column and 256 row system yeah? But that's why it's called 32 bit, because it can only 'process' 32 bits at a time even though it has 36 address lines? But it sets it up in a clever way so that it does not have to directly ask for any box number bigger than (2^32-1) :), it just asks for something in some sort of a row/column complicated system? Is that correct?

Also, where can I find how many data and address lines a processor has, I can't seem to see it on intel's website or find it in google.... are address line and data line just terms you guys made up to make it easy for me to understand? :) All the help is much appreciated!

---

### Post by BuffaloX on 2007-09-25
The Core2 is a 64 bit CPU!

[http://en.wikipedia.org/wiki/Intel_Core_2]("http://en.wikipedia.org/wiki/Intel_Core_2")

If you use 32 bit OS, you can only access 4GB. This is because 32 bit OS's are not made to use the extra functionality of Core2.
The most important of which is 64 bit processing and SSE3.

The CPU could be made to be able to use all 36 bit address lines even in 32 bit mode. Just like you mention, it could use methods like the old 8 bit CPU's did.

But they probably haven't done that, because programs would need to be rewritten to use it, and if you rewrite the programs, you might as well use all the new functions. Also enabling the full addressing system for 32 bit mode, would very easily break compatibility with old software.
Usually this is handled by an ability to switch mode between 32 compatibility an full  64 bit functionality.

---

### Post by psusi on 2007-09-25
What you describe sounds like segmentation.  Technically pentium class cpus have 6 segment selector registers: data segment, code segment, extra segment, stack segment, global segment, and far segment.  Instructions are fetched from the code segment, data is fetched from an address within the data segment, unless you prefix the instruction with an override to specify the extra, global, or far segments.  The stack lives in the stack segment.  Technically each segment is its own 4 GB address space that could be at different locations in physical ram, but all modern operating systems don't bother using segments and just set them all to the same flat 32 bit address space, and everyone just pretends segments don't exist.  

That leaves the processor with the ability to select from 4 GB of ram at a time, but the OS can change the page tables when switching processes so that the ram that the processor thinks is 0-4 GB may actually be somewhere in the 4-64 GB range.  The page tables define a mapping for every 4kb page of virtual ram to some 4k page of physical ram ( or nowhere if that page is not valid ).

---

