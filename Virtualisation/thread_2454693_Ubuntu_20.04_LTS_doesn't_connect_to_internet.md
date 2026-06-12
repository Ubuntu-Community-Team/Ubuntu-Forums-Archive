---
title: "Ubuntu 20.04 LTS doesn't connect to internet"
date: 2020-12-04
forum: Virtualisation
---

### Post by urost on 2020-12-04
Hello everyone I am somewhat new to Linux in general and have run into a problem with Ubuntu 20.04.

I have a virtual machine I made and installed Ubuntu 20.04 on it but it can't connect to internet.

I am using VMware for virtualization and for the adapter type I chose VMXNET 3 since on the same infrastructure there is already one Ubuntu server and it has that adapter type on it.

What can I do to try and solve this?

I know there is not a lot of information here but as I am new to this forum and Linux I am not sure what you need, sorry for that.

---

### Post by howefield on 2020-12-04
Thread moved to the "*Virtualisation*" forum as probably a better fit.

---

### Post by kevdog on 2020-12-08
Can you make another adapter and bind to that interface?  I think one adapter per VM.

---

### Post by urost on 2020-12-10
Hello,

Sorry for the late answer kevdog.
If by interface you mean adapter type I have tried E100E as well and got the same results.

Network that it needs to connect to is from 172 range not 192 not sure if that makes any difference or if that needs something packet installed.

---

