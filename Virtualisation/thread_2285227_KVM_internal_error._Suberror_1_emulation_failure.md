---
title: "KVM internal error. Suberror: 1 emulation failure"
date: 2015-07-04
forum: Virtualisation
---

### Post by linuxnz123 on 2015-07-04
Hi,
When start VMs with -enable-kvm I get following error message in my qemu.log and the VM does not boot after this:


[LIST]
[*]Warning: nic e1000.0 has no peer 
[*]Warning: nic e1000.1 has no peer 
[*]Warning: nic e1000.2 has no peer 
[*]Warning: nic e1000.3 has no peer 
[*]Warning: nic e1000.4 has no peer 
[*]Warning: nic e1000.5 has no peer 
[*]KVM internal error. Suberror: 1 
[*]emulation failure 
[*]EAX=00000000 EBX=00000000 ECX=00000046 EDX=00000001 
[*]ESI=00000000 EDI=00000000 EBP=00007864 ESP=00007848 
[*]EIP=f000ff53 EFL=00250012 [----A--] CPL=0 II=0 A20=1 SMM=0 HLT=0 
[*]ES =0010 00000000 ffffffff 00c09300 DPL=0 DS   [-WA] 
[*]CS =0008 00000000 ffffffff 00c09b00 DPL=0 CS32 [-RA] 
[*]SS =0010 00000000 ffffffff 00c09300 DPL=0 DS   [-WA] 
[*]DS =0010 00000000 ffffffff 00c09300 DPL=0 DS   [-WA] 
[*]FS =0010 00000000 ffffffff 00c09300 DPL=0 DS   [-WA] 
[*]GS =0030 200e9000 ffffffff 00c09300 DPL=0 DS   [-WA] 
[*]LDT=0000 00000000 ffffffff 00c00000 
[*]TR =0008 00000580 00000067 00008b00 DPL=0 TSS32-busy 
[*]GDT=     00001000 000000af 
[*]IDT=     2010e000 000007ff 
[*]CR0=40000011 CR2=00000000 CR3=00000000 CR4=00000200 
[*]DR0=0000000000000000 DR1=0000000000000000 DR2=0000000000000000 DR3=0000000000000000 
[*]DR6=00000000ffff0ff0 DR7=0000000000000400 
[*]EFER=0000000000000000 
[*]Code=00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 <00> 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
[/LIST]


Any one able help with this error message please.

Thanks

---

### Post by KillerKelvUK on 2015-07-05
Have you confirmed that KVM is loaded? e.g. with "lsmod | grep kvm"

---

### Post by linuxnz123 on 2015-07-06
Yes kvm is loaded. I have checked for this.

---

### Post by Jose_R._Jr. on 2015-07-09
Hi Linuxnz123

I hit same issue here with a fresh install of Ubuntu 14.04LTS Server with Virtualization host software package, after the installation I have only applied update/upgrade and installted virt-inst package.

ym1r@wistar:/var/log/libvirt/qemu$ dmesg|grep -i kvm
[    8.371358] kvm: Nested Virtualization enabled
[    8.371365] kvm: Nested Paging enabled
ym1r@wistar:/var/log/libvirt/qemu$ kvm-ok 
INFO: /dev/kvm exists
KVM acceleration can be used
ym1r@wistar:/var/log/libvirt/qemu$ sudo kvm -vnc :1 -monitor stdio
QEMU 2.0.0 monitor - type 'help' for more information
(qemu) KVM internal error. Suberror: 1
emulation failure
EAX=00000000 EBX=40010000 ECX=00000030 EDX=00000cfd
ESI=00000000 EDI=00000000 EBP=00000000 ESP=00006fcc
EIP=0fedb30c EFL=00000002 [-------] CPL=0 II=0 A20=1 SMM=0 HLT=0
ES =0010 00000000 ffffffff 00409300 DPL=0 DS   [-WA]
CS =0008 00000000 ffffffff 00c09a00 DPL=0 CS32 [-R-]
SS =0010 00000000 ffffffff 00409200 DPL=0 DS   [-W-]
DS =0010 00000000 ffffffff 00409300 DPL=0 DS   [-WA]
FS =0010 00000000 ffffffff 00c09300 DPL=0 DS   [-WA]
GS =0010 00000000 ffffffff 00c09300 DPL=0 DS   [-WA]
LDT=0000 00000000 0000ffff 00008200 DPL=0 LDT
TR =0000 00000000 0000ffff 00008b00 DPL=0 TSS32-busy
GDT=     000f6688 00000037
IDT=     000f66c6 00000000
CR0=60000011 CR2=00000000 CR3=00000000 CR4=00000000
DR0=0000000000000000 DR1=0000000000000000 DR2=0000000000000000 DR3=0000000000000000 
DR6=00000000ffff0ff0 DR7=0000000000000400
EFER=0000000000000000
Code=00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 <00> 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

---

### Post by Jose_R._Jr. on 2015-07-10
Hi Folks,

I solved the issue; sounds like a kernel bug. My nested setup is working with ubuntu inside esxi 5.5 inside of esxi 5.5. For me this is related with kvm_amd not sure if my opteron 6376 is playing something here. But nested esxi worked without issue so passing svm hardware features down to my guest esxi vm worked fine.

So l1 or l2 nested kvm on esxi were falling all the time when trying to run with accelerated hardware functions. When running with software based virtualization not issue at all.

I have upgraded all my ubuntu 14.04.2LTS servers to kernel 3.19.8-031908-generic at not issue now even with l3 nested kvm.

Regards
José

---

