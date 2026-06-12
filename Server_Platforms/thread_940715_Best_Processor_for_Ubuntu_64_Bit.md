---
title: "Best Processor for Ubuntu 64 Bit"
date: 2008-10-07
forum: Server Platforms
---

### Post by benoybose on 2008-10-07
Can any one help me by suggesting the best available processor for a server system, to be installed with Ubuntu 8.04 64Bit Server version.

My purpose is for hosting a large scale, highly interactive, heavily loaded web portal.

System must run Apache2, MySQL 5.X, PHP 5.2.6, Postfix etc...

---

### Post by Robstarusa on 2008-10-07
> **benoybose said:**
> Can any one help me by suggesting the best available processor for a server system, to be installed with Ubuntu 8.04 64Bit Server version.

My purpose is for hosting a large scale, highly interactive, heavily loaded web portal.

System must run Apache2, MySQL 5.X, PHP 5.2.6, Postfix etc...

What is your budget?

These days I'd make sure the processor meets the following requirements:
1) 64-bit
2) dual core or better
3) HARDWARE VT Extensions. Beware! A lot of the "lower end" intel chips do not have this...E2xxx, E4xxx, Q8200, etc.

For a budget that is > $150 for a CPU I'd say go Q6600.
For sub $100, I'd go with an AMD triple core
For $100-$150 I'd go for a higher speed AMD quad core.

---

### Post by benoybose on 2008-10-07
> **Robstarusa said:**
> What is your budget?

These days I'd make sure the processor meets the following requirements:
1) 64-bit
2) dual core or better
3) HARDWARE VT Extensions. Beware! A lot of the "lower end" intel chips do not have this...E2xxx, E4xxx, Q8200, etc.

For a budget that is > $150 for a CPU I'd say go Q6600.
For sub $100, I'd go with an AMD triple core
For $100-$150 I'd go for a higher speed AMD quad core.

Thanks for the suggestions....

---

### Post by tribaal on 2008-10-07
For web applications you might want to got for as many core as you can, evn if that means a lower clock.
Web applications (Apache) and databases are designed to scale with the number of cores (they are heavily multithreaded).

And most of the times, the CPU power required is pretty low (for a webpage for example), but you need to server many at the same time.

+1 on Hardware VT, if you plan on using virtualization technologies (Xen, VMware, VirtualBox...)

- Trib'

---

