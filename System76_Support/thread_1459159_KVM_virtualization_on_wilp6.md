---
title: "KVM virtualization on wilp6"
date: 2010-04-21
forum: System76 Support
---

### Post by jpv on 2010-04-21
Anyone get KVM working on a Wild Dog Perf 6?

"egrep 'flags.*:.*(svm|vmx)' /proc/cpuinfo" gives me all kinds of stuff, so in theory I think it should work.  But in practice:

# modprobe kvm-intel 
FATAL: Error inserting kvm_intel (/lib/modules/2.6.31-19-generic/kernel/arch/x86/kvm/kvm-intel.ko): Operation not supported

## Running stock System76 Karmic 64-bit, fully up-to-date
# uname -a
Linux 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

Do I have to fiddle in the BIOS?  I don't want to reboot this machine unless I really have to, and it'll actually help.

---

### Post by thomasaaron on 2010-04-21
If you have a VT enabled CPU, there is an option under the Security tab in the BIOS to enable VT.

---

### Post by jpv on 2010-06-18
<and much time passes...>

Yes, once I finally got around to rebooting, there was an option in the BIOS, I turned it on, and now it all Just Works.  (I has assumed that would be on by default.  I mean, why not?)

As Bhaskar said in a similar thread last month, "Thank you, Tom & System 76."

---

