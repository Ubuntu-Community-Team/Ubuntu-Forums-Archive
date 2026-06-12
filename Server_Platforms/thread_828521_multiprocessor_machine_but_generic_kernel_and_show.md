---
title: "multiprocessor machine but generic kernel and showing smaller memory"
date: 2008-06-13
forum: Server Platforms
---

### Post by foramgoram on 2008-06-13
I have a machine with xeon processors and 16 GB of memory. Ubuntu 7 is installed and it's showing 8 processors but only 2.54 GB of ram. uname -r shows 2.6.22-14-generic which should be smp, in my opinion. Please someone tel me what's wrong and how do I fix it.

Thanks a lot
:)

---

### Post by samosamo on 2008-06-13
I think the uname switch you're looking for is -a, as in "all."  As for the RAM, I'm not sure.  Where is it saying 2.54GB RAM?  Thats sort of an odd number.  Type "free" and paste the output here.

---

### Post by windependence on 2008-06-14
> **foramgoram said:**
> I have a machine with xeon processors and 16 GB of memory. Ubuntu 7 is installed and it's showing 8 processors but only 2.54 GB of ram. uname -r shows 2.6.22-14-generic which should be smp, in my opinion. Please someone tel me what's wrong and how do I fix it.

Thanks a lot
:)

The generic kernel is multiprocessor. If not, you would not see all the cores. 

Your memory problem is that you are running the 32 bit OS. You need to be running 64 bit to recognize all the memory above 4 GB. the funky number is just because a full MB is not 1000K, it's 1024.

EDIT: Your memory problem could also be that you don't have the memory slots populated correctly. What board are you using?

-Tim

---

### Post by foramgoram on 2008-06-14
I did a bit search and I came to the conclusion that 32 Desktop version supports upto 4GB memory because the kernel is not configured to use pae. The server edition has it configured.

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

As for the type of board, I have to look it up.

How do I know if I am running desktop or server edition?

Thanks to all for the responses

---

### Post by windependence on 2008-06-15
You can do a sudo uname -a to find the kernel version.

-Tim

---

