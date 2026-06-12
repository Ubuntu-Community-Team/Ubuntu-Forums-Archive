---
title: "VM over all nodes"
date: 2010-12-23
forum: Ubuntu Cloud and Juju
---

### Post by miszko on 2010-12-23
Hi,

(Sorry for my bad english)

It's possible to make one really big VT over all nodes?
I've got two servers (each one have 2x8 cores processors and 24GB RAM).
I want to make one big instance (32 cores, 48GB RAM). It's possible to make?

Thanks for help ;)
Best regards.

---

### Post by raymdt on 2010-12-23
This is a  nice question,
you can find it out by  yourself. Just set the vmtypes (https://<clc ip>:8443 ---> tab "configuration ) of c1.xlarge to Cpus(32) Memory 48Gb , then try

```


euca-describe-availability-zones verbose


```But i don't think so, because KVM can scale a VM only to one physical host.

---

### Post by kim0 on 2010-12-23
No, that is not possible using any software. What is possible however, is writing your programs to make use of the 2 VMs to get higher aggregate throughput

---

