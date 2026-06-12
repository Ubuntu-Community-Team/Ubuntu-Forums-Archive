---
title: "virsh kvm CPU affinity problems"
date: 2010-04-01
forum: Virtualisation
---

### Post by jetwins on 2010-04-01
We can use taskset to bind the qemu-kvm process into any of specified cpu cores, I wonder if we can use "virsh vcpupin" to do the same thing? Why the result always inconsistence between these two commands?

For example, there is a 4 cores hypervisor, use taskset to bind the KVM guest process 2856 to 1st core, but check with the virsh vcpuinfo, the guest still be bind on the 3rd core.

[root@PC Server]# taskset -p 0 2856

[root@PC Server]# taskset -pc 2856

pid 2856's current affinity list: 0
(shows currently this VM is binding with the 1st core)

[root@PC Server]# virsh vcpuinfo test2
VCPU: 0
CPU: 2
State: running
CPU time: 485.9s
CPU Affinity: --y-
(shows currently this VM is binding with the 3rd core)

Also the cpu affinity specified by virsh vcpupin is mismatched with the taskset, is there any limitation? can anyone help me?

P.S. Is there another tools can check which cores are bind with the process?

Thanks,

---

