---
title: "KVM won't boot VM after install"
date: 2010-11-14
forum: Virtualisation
---

### Post by CombinedEffort on 2010-11-14
I have a fresh, 10.10 server install and am using virt-manager to create a VM via it's wizard. 

The VM boots the install CD (also 10.10) and runs through the install, installs GRUB, etc. On rebooting into the installed OS, I just get a cursor in the top-right corner and it hangs there forever at 100% CPU.

I've also tried running KVM from the command line with existing VMs from my Gentoo box and they all hang-on-boot as well.

It's as if KVM is just broken in 10.10!

Rich

---

### Post by CombinedEffort on 2010-11-15
After a little more investigation, the VM will boot with the --no-kvm option, albeit very slowly.

I'm considering installing an alternate kernel version for the host, but am not such if there is such a thing in 10.10?

Failing that, I'll try a clean install of Centos / Fedora and see if that works any better.

---

### Post by gdahlm on 2010-11-15
Open a command prompt and try running the program

kvm-ok

it will tell you if the machine supports KVM, or if it is shut off in the bios.

---

### Post by CombinedEffort on 2010-11-15
Thanks for the reply, but the machine dual-boots Gentoo with a working KVM - I'm trying to migrate away from the Gentoo install, but not having much luck so far!

I'll double-check the kvm-ok, but I'm sure it's 'OK' as I've seen /dev/kvm

Rich.

---

### Post by CombinedEffort on 2010-11-17
OK, as a work around, I installed a fresh 10.04 and KVM worked out the box. I guess there's something hairy about 10.10's kernel.

I'll try and file a bug report, time permitting...

---

### Post by mdavids on 2011-01-17
Ah, so i am not alone! I have the exact same behavior: 10.10 host and a 10.10 guest that won't boot. The installation CD start perfectly, and I can install smoothly, but booting the HD after that is an absolute nogo, unless I start without the '--enable-kvm' option (which is undoable, because it is soooo slow...).

I can boot the install CD, go to rescue mode and then start a shell and mount the root-disk. Works all fine. It is just impossible to boot from that disk :-(

Is there any progress on this issue?

---

### Post by CombinedEffort on 2011-01-17
Thanks for verifying - half the battle is knowing you're not alone!

I'm still running 10.04 at the moment and the KVMs seems stable (2 * 10.04 ubuntu server, 1 * Win XP).

I assume it must be a quirk in a kernel module for the hardware I'm running and that KVM on 10.10 does really run fine 99.9% of the time.

FWIW, I'm using a Asus P5Q Deluxe P45 Socket 775 as my main board. Perhaps we should compare hardware and see if there is anything in common?

---

### Post by mdavids on 2011-01-17
> **CombinedEffort said:**
> 
Perhaps we should compare hardware and see if there is anything in common?

I was just about to propose that. I use a FitPC2i with a 32 bit Intel Atom Z530. It shows up as two CPU's in /proc/cpuinfo (I seem to remember that this is configurable in the BIOS and I went for that option).

I am really surprised that the install CD-ROMs I tried work really well (I even tried a 10.10 Desktop Live-CD, which works pretty well, even though my machine specs are pretty limited). How, why? Because as soon as I boot from a freshly installed virtual HD, it freezes with that single prompt you described (tried various types of virtual HD's, like IDE, Virtio and SCSI ad lot's of other things, but none of them work, unless I turn off --enable-kvm...).

I suspected the 32 bit CPU might me an issue, but your motherboard had 64 bit, right? A colleague of mine uses 10.10 on a 64 bit server and he has no issues.

(I don't want to downgrade to 10.04...)

---

### Post by CombinedEffort on 2011-01-17
Hmm, not much crossover there. I'm running on :

```

ankh@ted:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping        : 11
cpu MHz         : 1603.000
cache size      : 4096 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 4
apicid          : 0
initial apicid  : 0
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority
bogomips        : 4799.98
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual

```I'm wondering if it's a guest BIOS / INT 13 / GRUB issue, since KVM will happily boot a CDROM (syslinux?). I guess one test would be to build a syslinux bootable CD and see if it'll boot off the virtio disk.

p.s. I'm not sure what OS bitiness I went for with 10.10. Certainly the hardware is 64-bit.

---

### Post by mdavids on 2011-01-19
> **CombinedEffort said:**
> Hmm, not much crossover there. I'm running on :

p.s. I'm not sure what OS bitiness I went for with 10.10. Certainly the hardware is 64-bit.

Could be interesting to look at the 32/64 bit OS you run.

In the mean time I tried *lots* of things and did a lot of Googling. The closest thing I could find was:

[https://bugs.launchpad.net/bugs/688085](https://bugs.launchpad.net/bugs/688085)

But that did not help me much either.

But... I am happy at the moment. I installed the new Debian 6.0 (squeeze) RC1 iso as guest system. Works very well for me.

The businesscard i386 iso is really nice (at least for what I wanted to do with my little virtual server):

[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

---

### Post by CombinedEffort on 2011-01-20
The bug reporter in 688085 does seem to duplicate the symptoms I was  seeing. I did look on launchpad at the time, but it looks like this was  submitted a few weeks after.

After a bit of poking around, yes, my 10.10 install was 32-bit, as is my 10.04. I don't really hold with all this 64-bit nonsense ;)

I was originally going to go with Debian Squeeze too, but I think I've committed to Ubuntu Server now.

Cheers,

Rich.

---

### Post by CombinedEffort on 2011-01-20
Dupe post - stupid proxy (mutter, mutter)

---

### Post by CombinedEffort on 2011-01-20
Dupe post - stupid proxy (mutter, mutter)

---

