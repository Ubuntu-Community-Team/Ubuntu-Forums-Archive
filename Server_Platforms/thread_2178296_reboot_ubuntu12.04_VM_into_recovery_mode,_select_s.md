---
title: "reboot ubuntu12.04 VM into recovery mode, select system-summary, but output is weird"
date: 2013-10-02
forum: Server Platforms
---

### Post by qiubosu2 on 2013-10-02
dear ubuntu community,

i installed several VMs under the same physical server with visualization  features. the hypervisor is KVM and the VM manager tool is virt-manager.  all the VMs have ubuntu 12.04 OS installed and work well. the physical  server and the VMs are all in the same LAN (e.g. 192.168.123.0/24) and  all can well connect to Internet through a NAT router. when reboot and  select "recovery mode" in boot menu, go to the "recovery menu" and  select the "system-summary" option, there is below error message shows  in the prompt for about 2 seconds (normally it will display the summary  of the system, e.g. hard drive partition, network status etc.) and go  back to the "recovery menu" screen

cat: /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies: No such file or directory /lib/recovery-mode/options/sysystem-summary: 29: /lib/recovery-mode/options/sysystem-summary: arithmetic expression: expecting primary: “ / 1000"

this is weird. it is much appreciated if any one can help with this.

kind regards,
q.s.

---

### Post by howefield on 2013-10-02
Thread closed.

Duplicate here : [http://ubuntuforums.org/showthread.php?t=2178297](http://ubuntuforums.org/showthread.php?t=2178297)

---

