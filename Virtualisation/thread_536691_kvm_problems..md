---
title: "kvm problems."
date: 2007-08-11
forum: Virtualisation
---

### Post by Drone4four on 2007-08-11
I'm using these two guides to get kvm to work:

[http://ubuntu-tutorials.com/2007/07/04/setting-up-qemu-kqemu-on-ubuntu-704-feisty/](http://ubuntu-tutorials.com/2007/07/04/setting-up-qemu-kqemu-on-ubuntu-704-feisty/)

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

I get stuck here:```
drone4four@kubuntu:~$ sudo modprobe kvm-amd
FATAL: Error inserting kvm_amd (/lib/modules/2.6.20-16-generic/kernel/drivers/kvm/kvm-amd.ko): Operation not supported
```Here is dmsg:
```
[377628.752000] has_svm: svm not available
[377628.752000] kvm: no hardware support
[377682.732000] has_svm: svm not available
[377682.732000] kvm: no hardware support
[378313.656000] has_svm: svm not available
[378313.656000] kvm: no hardware support
[379398.116000] has_svm: svm not available
[379398.116000] kvm: no hardware support

```lsmod shows:```
kvm                    61148  0
```Check it:```
drone4four@kubuntu:~$ ls /lib/modules/2.6.20-16-generic/kernel/drivers/kvm/
kvm-amd.ko  kvm-intel.ko  kvm.ko

```What exactly is my dmsg saying and what can I do to proceed with the kvm guides?

---

### Post by Drone4four on 2007-08-15
Should I try posting this thread in a different forum?

---

### Post by Drone4four on 2007-08-28
I asked a question about vmware in the Ubuntu hardware forum:
[http://ubuntuforums.org/showthread.php?t=522801](http://ubuntuforums.org/showthread.php?t=522801)
It hasn't received the attention it should.  I haven't got a single response there.  Where should I have really posted it?

---

### Post by dpar on 2007-08-28
Probably here......vmware is software, not hardware. I don't know anything about it though, so I'm afraid I can't help you:(

---

### Post by southernman on 2007-08-28
> **Drone4four said:**
> I asked a question about vmware in the Ubuntu hardware forum:
[http://ubuntuforums.org/showthread.php?t=522801](http://ubuntuforums.org/showthread.php?t=522801)
It hasn't received the attention it should.  I haven't got a single response there.  Where should I have really posted it?

Maybe if you request here... or in your linked thread that bohdi or another moderator kindly move it into this subforum, it will get the attention you think it should get. 

Ask them to, to remove this thread if you like. Good luck with your vmware problem.

---

### Post by HermanAB on 2007-08-28
Hmm, I have installed VMware Server several times on Redhat and Mandriva. I just follow the instructions on the VMware web site.  It works every time.

For VMware Player, ensure that Ubuntu is *fully* updated and happy, then use Synaptic to install it - nothing to it - clicketyclick done.

Note that you cannot have both on the same machine.  In fact, you can have only ONE kind of virtualization on one machine.  If you wish to change to a different virtualization solution, then you have to re-install Linux.

Hope that helps!

Herman

---

### Post by bapoumba on 2007-08-28
@ Drone4four: I merged the initial thread in here, as you had answers about it, and renamed the thread. Please check the thread title and tell me if it's OK with you :)

---

### Post by david_e on 2007-08-28
It looks like your hardware is not supported by kvm, probably bacause your AMD CPU doesn't support SVM.

You could try QEMU + KQEMU for the hw virtualization.

*** EDIT ***

As you can see SVM is required:

[http://kvm.qumranet.com/kvmwiki/Status](http://kvm.qumranet.com/kvmwiki/Status)

---

### Post by dougwolfe on 2008-01-09
I have a similar problem.

>sudo modprobe kvm-amd
FATAL: Error inserting kvm_amd (/lib/modules/2.6.22-14-rt/kernel/drivers/kvm/kvm-amd.ko): Operation not supported

I have run 
egrep '^flags.*(vmx|svm)' /proc/cpuinfo
as suggested by the kvm package.  I recieved a whole bunch of flags as a response:
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps

As far as I can tell my CPU supports SVM virtualization.
My CPU is the AMD Athlon X2 BE-2400 Brisbane 2.3GHz Socket AM2 45W Dual-Core Processor.

---

### Post by Drone4four on 2008-02-07
> **HermanAB said:**
> Hmm, I have installed VMware Server several times on Redhat and Mandriva. I just follow the instructions on the VMware web site.  It works every time.

For VMware Player, ensure that Ubuntu is *fully* updated and happy, then use Synaptic to install it - nothing to it - clicketyclick done.

Note that you cannot have both on the same machine.  In fact, you can have only ONE kind of virtualization on one machine.  If you wish to change to a different virtualization solution, then you have to re-install Linux.

Hope that helps!

Herman

I thought kvm was different from VMware.  Am I right?

---

### Post by Drone4four on 2008-02-07
> **david_e said:**
> It looks like your hardware is not supported by kvm, probably bacause your AMD CPU doesn't support SVM.

You could try QEMU + KQEMU for the hw virtualization.

*** EDIT ***

As you can see SVM is required:

[http://kvm.qumranet.com/kvmwiki/Status](http://kvm.qumranet.com/kvmwiki/Status)
I think my CPU supports SVM, it's just that either: (a) I haven't enabled SVM in my BIOS or (b)I haven't ompiled a kernel which includes support for SVM or (c) maybe I need to do both.  My questions, therefore, are: (1) what should I look for and where in my BIOS to enable SVM, and (2) where in the kernel do I enable SVM?

Here are my CPU  specifications:```
 drone4four@ubuntu:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : Dual Core AMD Opteron(tm) Processor 175   
stepping        : 2
cpu MHz         : 2211.374
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 4425.62
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : Dual Core AMD Opteron(tm) Processor 175   
stepping        : 2
cpu MHz         : 2211.374
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 4422.97
clflush size    : 64
 
```

---

### Post by Drone4four on 2008-02-07
And my AMD processor is an **Opteron 175** 2200 MHz 2×1024 KiB	1000 MHz 11x1.35/1.3V 110W Socket 939 OSA175DAA6CD** "Denmark" (90 nm)**  

I am running 32bit Gutsy now.  Before I was running 32 bit Fiesty.

---

### Post by Drone4four on 2008-02-25
in the kvm official documentation, this question is answered: How can I tell if I have Intel VT or AMD-V? [http://kvm.qumranet.com/kvmwiki/FAQ#head-a78f5f083749cb9c2e57d7d4efaf2ecf25b9db60](http://kvm.qumranet.com/kvmwiki/FAQ#head-a78f5f083749cb9c2e57d7d4efaf2ecf25b9db60)

The answer is input this command: ```
egrep '^flags.*(vmx|svm)' /proc/cpuinfo
```  The outup on my  end is: ```
drone4four@ubuntu:/usr/src/kvm-61/kernel$ egrep '^flags.*(vmx|svm)' /proc/cpuinfo
drone4four@ubuntu:/usr/src/kvm-61/kernel$ 
```  I think this means I can't use kvm.  Although, what if I changed some settings in my BIOS?  Then would that command produce different results?

---

### Post by Drone4four on 2008-03-15
Maybe I could try this guide here: [http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux)

---

