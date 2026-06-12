---
title: "How to reduce power consumption in Ubuntu 14.04"
date: 2014-05-24
forum: Ubuntu, Linux and OS Chat
---

### Post by Tejas_Ghalsasi on 2014-05-24
For all people with power problems using Ubuntu 14.04 try downgrading your Linux kernel to Long term supported version

either 3.10 or 3.12 
PS: it worked for me and will work for most of the people as 3.12 kernel is stable



 firstly download the 3 deb files which suit ur system architecture
if for 32 bit =>i386
for 64 bit =>amd64
go for files which have generic written
 [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12.20-trusty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.12.20-trusty/")


Go to the downloaded folder



then run this 



**sudo dpkg -i linux-headers-3.12.20* linux-image-3.12.20* .deb**
 

And then remove the 3.13 default kernel


**sudo apt-get remove linux-headers-3.13.0* linux-image-3.13.* **
And ur through


If possible change the URI for Kernel updates in Software Center.


-Regards Tejas Ghalsasi

<snip>

---

### Post by grahammechanical on 2014-05-26
"It worked for me" is not a sufficient recommendation as far as I am concerned. Please provide statistical evidence of a power consumption reduction.

---

