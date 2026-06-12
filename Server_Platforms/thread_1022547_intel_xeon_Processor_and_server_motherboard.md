---
title: "intel xeon Processor and server motherboard"
date: 2008-12-26
forum: Server Platforms
---

### Post by madmax1735 on 2008-12-26
hey

i am planning to assemble a new server. based on the requirements i have a chosen an Intel Xeon E5430 2.66 Ghz LGA 771 processor. i am also planning to get an intel server motherboard for the system.

but i am unsure about the compatibility of intel server motherboards compatibility with ubuntu server 64 bit as the site only lists compatibility with red hat and suse. 

server motherboards supported by the above processor are Intel 5000P, 5000V, 5400A, 5100, 5400B.

Are there any problems like 'noapic' error that i might face with the above motherboards.

any info will be appreciated.

thnx

---

### Post by cariboo on 2008-12-27
If the motherboard works with Redhat and Suse, it will work the same way with Ubuntu. Linux distributions all use the same kernels so any problems that the distributions have will also apply to Ubuntu.

Jim

---

### Post by madmax1735 on 2008-12-27
i know that should work that ways but unfortunately it doesnt.....


thr r ubuntu specific bugs like 'no-apic' bug [https://bugs.launchpad.net/ubuntu/+bug/274022](https://bugs.launchpad.net/ubuntu/+bug/274022) which i faced recently on a amd 64 bit processor on a MSI motherboard while installing ubuntu 8.10 server 64bit edition.....

it would cause the system to shutdown during installation itself....


are there any such know problems that i might face with a intel server board??????

---

### Post by windependence on 2008-12-27
No.

-Tim

---

### Post by madmax1735 on 2008-12-27
really short reply :confused:

---

### Post by windependence on 2008-12-27
Just because MOST server boards work with Linux. Especially server class hardware like Xeon processors should not be any problem. You can also google your board with Ubuntu as a keyword and quickly see if anyone is having problems. I like to use Ubuntu in some cases but almost always if it doesn't work, another distro such as OpenSuSE works just fine. CentOS is also good (a clone of Red Hat).

-Tim

---

### Post by martien on 2008-12-28
Buy your hardware and give your new server a test month - install ubuntu and try it.. watch how the system goes and if there is any trouble reinstall with another distribution. At the end of this month you will have an experience and you will be able to solve future problems. Also in this month you will be able to decide witch distribution type you like - rpm or debian(deb) based.. (by switching more than 1 distro of course).
Good luck.

---

### Post by madmax1735 on 2008-12-29
we are already running the system successfully with a P4 and 512mb ram....

ubuntu server works fine with this system................ but if we start squid internet generally slows down for hosts (we have 350 of these lill pests mostly on windows)

yes we did try out different distros, open suse, etc........... i have to say i like debian based distro's better....... ubuntu being favourate.... cause its easiest to run and understand.....


we need a better machine cause we are gonna shift to a 2mbps 1:1 leased line and need to run squid in order to restrict access to bandwidth hoggin websites like rapidshare, etc.

so i guess intel xeon 2.6 quad core would b enough.... with 4gb ram?

thnx for all the help....

---

### Post by windependence on 2008-12-29
> **madmax1735 said:**
> we are already running the system successfully with a P4 and 512mb ram....

ubuntu server works fine with this system................ but if we start squid internet generally slows down for hosts (we have 350 of these lill pests mostly on windows)

yes we did try out different distros, open suse, etc........... i have to say i like debian based distro's better....... ubuntu being favourate.... cause its easiest to run and understand.....


we need a better machine cause we are gonna shift to a 2mbps 1:1 leased line and need to run squid in order to restrict access to bandwidth hoggin websites like rapidshare, etc.

so i guess intel xeon 2.6 quad core would b enough.... with 4gb ram?

thnx for all the help....

RAM would be the best improvement you could make on that box. You are starved for RAM right now. Generally, processor isn't a problem.

-Tim

---

