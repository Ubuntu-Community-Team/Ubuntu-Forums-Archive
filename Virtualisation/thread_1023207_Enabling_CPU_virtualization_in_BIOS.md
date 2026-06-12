---
title: "Enabling CPU virtualization in BIOS"
date: 2008-12-27
forum: Virtualisation
---

### Post by nbotticelli on 2008-12-27
In the BIOS of my laptop (Toshiba Portege m400 S5032 tablet) it has an option for enabling hardware based virtualization for the processor but I am not sure if it would offer any benefit for my current use.

Does enabling hardware based virtualization do anything for a system running a regular host based OS with something like VMware Server or Virtualbox installed with VM's inside of them?

Or does it only offer benefit to a system where the virtualization program is running on the 'metal' itself?

Thank You!

---

### Post by bodhi.zazen on 2008-12-27
it will enable "KVM"

VirtualBox can make use of this technology 

With the guest off, In the General Tab -> Advanced -> check off the "Enable VT-x/AMD-V" box.

You can not run both KVM and Virtual box at the same time.

I am not sure if VMWare will make use of this technology or not.

EDIT: VMWare can use this technology as well

[http://communities.vmware.com/docs/DOC-9150](http://communities.vmware.com/docs/DOC-9150)

And according to this page, server as well 

[http://en.wikipedia.org/wiki/X86_virtualization](http://en.wikipedia.org/wiki/X86_virtualization)

---

### Post by inobe on 2008-12-27
VT will also help running vm's on 64 bit systems !

one example: the host operating system can be 32 bit, the guest can be 64 bit only if VT is enabled....... the vm must support it for any of it to work.

list of intel cpu's that have VT ability 

[http://www.intel.com/cd/channel/reseller/asmo-na/eng/products/desktop/processor/processors/core2duo/feature/index.htm](http://www.intel.com/cd/channel/reseller/asmo-na/eng/products/desktop/processor/processors/core2duo/feature/index.htm)

---

### Post by nbotticelli on 2008-12-27
Neat. Thank you.

I'm currently using VMware server but I first started using VirtualBox last spring and so far actually like VMware server better at this point.

I'll have to try enabling it in the BIOS and then on the VM itself to see if there really is much of an improvement or not then.

---

### Post by AlexanderDGreat on 2009-12-17
How do you enable VT if it's not in the bios?

---

### Post by bodhi.zazen on 2009-12-17
> **AlexanderDGreat said:**
> How do you enable VT if it's not in the bios?

As far as I know you can not.

Call your hardware manufacturer for assistance.

---

### Post by AlexanderDGreat on 2009-12-17
Hey man, thanks for that quick reply, I was hoping there was light in my problem. Can updating the bios do it for me then? I searched 1 person in the whole www that said a bios upgrade can do the job. Don't know if it's true though...

---

### Post by bodhi.zazen on 2009-12-17
Do you know what chip (CPU) you have and what motherboard ?

---

### Post by djchandler on 2009-12-18
CPU is a T5600. According to [URL="http://www.cpu-world.com/CPUs/Core_2/Intel-Core%202%20Duo%20Mobile%20T5600%20LF80537GF0342M%20%28BX80537T5600%29.html"]CPU World, virtualization is supported.
[/URL]
There's a [battery recall on that model]("http://cdgenp01.csd.toshiba.com/content/pr/download/CPSC%20Posting.pdf") btw.
[]("http://cdgenp01.csd.toshiba.com/content/pr/downl")

---

### Post by dcstar on 2009-12-19
> **bodhi.zazen said:**
> 
.......
EDIT: VMWare can use this technology as well

[http://communities.vmware.com/docs/DOC-9150](http://communities.vmware.com/docs/DOC-9150)

And according to this page, server as well 

[http://en.wikipedia.org/wiki/X86_virtualization](http://en.wikipedia.org/wiki/X86_virtualization)

Apparently you need to add this to the VM's .vmx file to enable it:

```
monitor.virtual_exec = "hardware"
```

---

### Post by AlexanderDGreat on 2009-12-19
Can I do it with Virtualbox? VMX files are for VMware, right? And VDI for Virtualbox.

---

### Post by AlexanderDGreat on 2009-12-19
> Do you know what chip (CPU) you have and what motherboard ?

Is this for me? I have Intel DG31PR mobo, Intel E7400 C2D procie.

---

### Post by bodhi.zazen on 2009-12-19
See this thread :

[http://communities.intel.com/message/74230](http://communities.intel.com/message/74230)

---

### Post by AlexanderDGreat on 2009-12-20
Hey, @bodhi.zazen, this is the ONE I'm Talking about, one person who Had The solution in the WWW!

How did you find it? It must've been very hard because for me, it was the whole afternoon. Thanks for the troubles man, will do it right away. :) More power to you!

---

### Post by bodhi.zazen on 2009-12-20
:lolflag:

Best of luck, hope it works.

---

### Post by tomski on 2010-10-25
i have never been able to use mine
i have AMD X2 64 4200+
hardware virtualization is turned on in bios
when i start my mac osx snow leopard VM it complains about using software virtualization!!!!

egrep '(vmx|svm)' /proc/cpuinfo
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy

SVM for both cores show i can use hardware VT

im so confused

---

### Post by bodhi.zazen on 2010-10-26
> **tomski said:**
> i have never been able to use mine
i have AMD X2 64 4200+
hardware virtualization is turned on in bios
when i start my mac osx snow leopard VM it complains about using software virtualization!!!!

egrep '(vmx|svm)' /proc/cpuinfo
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy

SVM for both cores show i can use hardware VT

im so confused

First this is an old thread, you should probably start your won thread.

Second, be sure to describe your problem. What virtualization technology are you having a problem with ?

KVM , Virtualbox, VMWare ?

Problem with host or guest ?

---

