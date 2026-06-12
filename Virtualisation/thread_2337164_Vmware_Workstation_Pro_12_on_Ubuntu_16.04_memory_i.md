---
title: "Vmware Workstation Pro 12 on Ubuntu 16.04 memory issue"
date: 2016-09-15
forum: Virtualisation
---

### Post by fracarfzx on 2016-09-15
Hi all.
I have an issue with Vmware Workstation Pro 12 installed on Ubuntu 16.04.
My PC has 32 GB RAM and an i7 CPU.
I have create a VM with 16 GB RAM and 2 vCPU.
At power on of the VM I saw on my host so much shared memory that is allocated how much RAM is configured in the VM: 16 GB

before VM start
fra@K95VM:~$ free -hm
                   total        used        free      shared  buff/cache   available
Mem:            31G        1,2G         28G        385M        1,6G         29G
Swap:           31G          0B         31G

after VM start
fra@K95VM:~$ free -hm
                   total        used        free      shared  buff/cache   available
Mem:            31G        1,3G         12G         16G         17G         13G
Swap:           31G          0B         31G
fra@K95VM:~$

The problem is that I can not turn on another VM because I do not have enough memory available

I tried the same thing on Debian and the problem does not occur: I can start two VM each with 16 GB RAM and the host allocates memory when needed

I think the problem depends on the installed kernel version. Ubuntu 16.04 has the kernel 4.x while Debian has kernel 3.x

Does anyone have the same problem and/or a solution?

Thank you very much!

---

### Post by fracarfzx on 2016-09-16
really no one has the same problem? I really need a solution! Thank you!

---

### Post by fracarfzx on 2016-10-12
No one has the same problem?
Please, I still need a solution.
Thank you!

---

### Post by howefield on 2016-10-12
If you are not prepared to bump your thread a bit more often then  don't complain if you get no response.

You might be better having a look at the VM Ware documentation, it appears pretty extensive and there is also the [forums]("https://communities.vmware.com/community/vmtn/workstation"). Who better to ask ?

---

