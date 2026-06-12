---
title: "Server kernel in 32bits (Lucid Lynx)"
date: 2010-10-27
forum: Server Platforms
---

### Post by narcisgarcia on 2010-10-27
I've seen that in Ubuntu 10.04 , i686 platforms install linux-image-2.6.32-..-generic-pae but x86_64 platforms install linux-image-2.6.32-..-server

If under 32-bits is used a generic kernel (I suppose with preemption and other desktop optimizations), which is the difference between generic and generic-pae for a server?

1. Why is preferable to use PAE extension in a server with less than 3GiB of RAM?

2. Which are the similarities between generic-pae_i386 and server_amd64 ?

---

### Post by pawnrocket on 2010-10-27
> **narcisgarcia said:**
> I've seen that in Ubuntu 10.04 , i686 platforms install linux-image-2.6.32-..-generic-pae but x86_64 platforms install linux-image-2.6.32-..-server

If under 32-bits is used a generic kernel (I suppose with preemption and other desktop optimizations), which is the difference between generic and generic-pae for a server?

1. Why is preferable to use PAE extension in a server with less than 3GiB of RAM?

2. Which are the similarities between generic-pae_i386 and server_amd64 ?

If you intend on never upgrade the amount of RAM on the server board then -generic would be fine, However if you will in the future need more memory and you are aware of the upgrade coming soon then I think PAE would be required or x86_64 would be required.
Also the 64bit version is recommended.

---

### Post by narcisgarcia on 2010-10-27
With a 32bits computer, everytime "generic" and "generic-pae" kernels are available in repositories.
Then, I can install a server with 1GiB of RAM with "generic" only kernel, and if someday I upgrade it to 4GiB+ of RAM, simply install generic-pae packages.

But this wasn't my question; server installer puts by default the "generic-pae" kernel. Has it some difference else than only PAE capability?

---

