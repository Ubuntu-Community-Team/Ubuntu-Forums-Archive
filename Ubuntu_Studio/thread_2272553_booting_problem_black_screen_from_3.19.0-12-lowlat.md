---
title: "booting problem black screen from 3.19.0-12-lowlatency"
date: 2015-04-07
forum: Ubuntu Studio
---

### Post by adj2 on 2015-04-07
I ran the Software Updater a couple of days ago and now can't boot cleanly. I can boot into an older kernel. 

The error message from 3.19.0-12 is:

[  1.6795441 ACPI PCC probe failed
[  1.713110 tpm_tis 00:03:  A TPM error (7) occurred attempting to read a pcr value
starting version 219

I'm not sure of the best place to ask this question. What the best way to identify the problem and correct it?

My system is:

Linux adj-HP-Compaq-6910p-GX978UC-ABE 3.19.0-11-lowlatency #11-Ubuntu SMP PREEMPT Tue Mar 31 22:48:17 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
adj@adj-HP-Compaq-6910p-GX978UC-ABE:~$

---

### Post by SponezillA on 2015-04-10
I had terrible experiences with the low latency. I can run the 3.2-generic without trouble. I'd say its best to stick to what works

---

### Post by gordintoronto on 2015-04-11
"PCC probe failed" is a meaningless warning message, you can totally ignore it.

---

### Post by tigermack on 2015-04-25
How do you ignore it when it prevents computer from booting without having to use recover mode. I have this problem since yesterday since I upgraded to 3.19 kernel and it is just a nuisance. I am newish to linux and would welcome help on how to resolve. Thanks.

---

