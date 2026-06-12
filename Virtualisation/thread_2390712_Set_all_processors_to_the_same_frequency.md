---
title: "Set all processors to the same frequency?"
date: 2018-05-01
forum: Virtualisation
---

### Post by nbritton on 2018-05-01
I have a Dell R920 with 4x Intel Xeon E7-8895 v2 processors. This system is a KVM hypervisor host that runs Ubuntu Server 18.04. I'm noticing that my VMs are randomly stalling and locking up, I've come to the conclusion that processor frequency auto scaling is to blame for this. I changed the system profile in the BIOS to "Performance Per Watt (OS)" and have set the linux governor to performance. However, when I run "cpupower monitor" I notice that the frequencies are still different among the cores.

How do I configure the system so that all cores are operating at the same turbo boost frequency?

I tried the following: cpupower frequency-set -f 3333

But I get this error:

```
root@lab:~/# cpupower frequency-set -f 3333Setting cpu: 0
Error setting new values. Common errors:
- Do you have proper administration rights? (super-user?)
- Is the governor you requested available and modprobed?
- Trying to set an invalid policy?
- Trying to set a specific frequency, but userspace governor is not available,
   for example because of hardware which cannot be set to a specific frequency
   or because the userspace governor isn't loaded?

```

---

### Post by pqwoerituytrueiwoq on 2018-05-01
Here is a command to check the configs on all 120 cpu threads you have
[FONT=courier new]for i in /sys/devices/system/cpu/cpu*/cpufreq/* ; do echo -e "$(cat $i)\t\t:\t\t$i";done[/FONT]
some files can not be read as they are for input if supported
that command will probably have 1440 lines of output on your system, change the 1st * to a number from 0 to 119 to see a single threads settings

i do not think the xeon chips support forcing a static turbo freq to all cores, you may be able to do that on a k sku cpu, but a non turbo freq should be possible (like 2.8Ghz)

"Performance Per Watt (OS)" does not sound like max performance, sounds like a balance between powersave and performance


Could your issue be thermal throttling? 4 chips in a small area sucking up 155 Watt each is a lot of heat
install lm-sensors and take a look with the sensors command

---

