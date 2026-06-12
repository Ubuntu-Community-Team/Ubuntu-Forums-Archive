---
title: "Hardy freezing while running KVM"
date: 2008-03-05
forum: Virtualisation
---

### Post by drdabbles on 2008-03-05
I am trying to build a new Windows VM on my Hardy box using KVM/QEMU instead of the VMWare one I have now. However, when I use the virt-manager GUI, I get an error when attempting to enable full virtualization. Also, when running KVM from the CLI, my system will reboot, or freeze randomly. This all happens BEFORE windows is installed.

My platform is 32-bit Hardy with the latest updates as of today. I am running on an AMD chip, and here's the output from /proc/cpuinfo:
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 67
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
stepping	: 2
cpu MHz		: 2600.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy ts fid vid ttp tm stc
bogomips	: 5215.16
clflush size	: 64

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 67
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
stepping	: 2
cpu MHz		: 2600.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy ts fid vid ttp tm stc
bogomips	: 5215.16
clflush size	: 64


If anybody else is experiencing this issue, please let me know how you fixed it, or if you're still having the problem. If there is no fix, I'd like to open a bug.

Also, please do not tell me that Hardy is "Alpha" and that bugs are to be expected. I understand that, and I am trying to find out as much as I can so I may help fix the bug in the final release.

Thanks!

---

### Post by simplyw00x on 2008-03-23
I experience this issue, and the only time I can now run images is by the following process (but it doesn't always avoid a panic):
```

# rmmod kvm-amd
# rmmod kvm
# modprobe kvm-amd
$ kvm .... etc.

```

---

### Post by emonticel on 2008-05-25
I have the same issue on a DELL laptop (latitude d531) with Ubuntu 8.04 (32 bit). CPU is AMD Turion 64. Whenever I invoke kvm (or qemu-system-x86_64) the  system freeze or reboot. Tried also ubuntu-8.04 for amd64 but no 

Try looking:

[https://answers.launchpad.net/ubuntu/+question/33131](https://answers.launchpad.net/ubuntu/+question/33131)

[https://bugs.launchpad.net/ubuntu/+bug/230569](https://bugs.launchpad.net/ubuntu/+bug/230569)

---

