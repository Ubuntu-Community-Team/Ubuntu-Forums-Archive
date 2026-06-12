---
title: "migrations broken between Ryzen CPUs (5800x to 3700 and below)"
date: 2022-05-25
forum: Virtualisation
---

### Post by mdtancsa on 2022-05-25
Hi All,
I have a number of KVM servers hosting a few dozen VMs.  I try to keep CPU and hardware as close as possible, but recently I added a 5800x CPU to the mix running ubuntu 22 LTS. All was working well, but sometime on the latest kernel upgrade, migrations between the 5800x based server and the 3700X based servers started to fail with the guest freezing or crashing.  I setup a pair of test servers in the back. Both Ubuntu 22 LTS, one on a Ryzen 2700 and one on a Ryzen 5800X. I can migrate guest VMs  TO the 5800 without issue. They run just fine. But as soon as I try to migrate the VM back to the Ryzen 2700, the guest VM once its fully migrated just freezes or crashes. 

e.g. on the 5800x based server  I do 
```
$
virsh migrate --verbose --unsafe --live 13Test qemu+ssh://virtboxtest2/system
13Test
Migration: [100 %]
$
```
which all looks good and fine
but on the destination machine (virtboxtest2), the resultant VM is frozen. In virtmanager, CPU is pegged at 100%.  On my FreeBSD test VM, I eventually get a panic if I touch the console

```
Fatal trap 9: general protection fault while in kernel modecpuid = 0; apic id = 00instruction pointer     = 0x20:0xffffffff8108c2ffstack pointer           = 0x28:0xfffffe00a80f19b8frame pointer           = 0x28:0xfffffe00a80f19b8code segment            = base 0x0, limit 0xfffff, type 0x1b                        = DPL 0, pres 1, long 1, def32 0, gran 1processor eflags        = resume, IOPL = 0current process         = 679 (sendmail)trap number             = 9timeout stopping cpuspanic: general protection faultcpuid = 0time = 1653511702KDB: stack backtrace:#0 0xffffffff80c69465 at kdb_backtrace+0x65#1 0xffffffff80c1bb1f at vpanic+0x17f#2 0xffffffff80c1b993 at panic+0x43#3 0xffffffff810afdf5 at trap_fatal+0x385#4 0xffffffff81087528 at calltrap+0x8#5 0xffffffff8108c775 at restore_fpu_curthread+0x85#6 0xffffffff810854f1 at done_load_dr+0x31#7 0xffffffff80c28892 at mi_switch+0xc2#8 0xffffffff80c790e6 at sleepq_catch_signals+0x2e6#9 0xffffffff80c79312 at sleepq_timedwait_sig+0x12#10 0xffffffff80bafbdd at _cv_timedwait_sig_sbt+0x10d#11 0xffffffff80c8ab35 at seltdwait+0x75#12 0xffffffff80c8a62e at kern_select+0x92e#13 0xffffffff80c8a9d6 at sys_select+0x56#14 0xffffffff810b06ec at amd64_syscall+0x10c#15 0xffffffff81087e3b at fast_syscall_common+0xf8Uptime: 4m8s

```

results are the same if I dont do a live migration 
```
virtboxtest3:~$ virsh migrate --verbose 13Test qemu+ssh://virtboxtest2/system
Migration: [100 %]
virtboxtest3:~$ 





Fatal trap 9: general protection fault while in kernel mode
cpuid = 0; apic id = 00
instruction pointer     = 0x20:0xffffffff8108c2ff
stack pointer           = 0x28:0xfffffe0068d469e8
frame pointer           = 0x28:0xfffffe0068d469e8
code segment            = base 0x0, limit 0xfffff, type 0x1b
                        = DPL 0, pres 1, long 1, def32 0, gran 1
processor eflags        = resume, IOPL = 0
current process         = 582 (syslogd)
trap number             = 9
timeout stopping cpus
panic: general protection fault
cpuid = 0
time = 1653512644
KDB: stack backtrace:
#0 0xffffffff80c69465 at kdb_backtrace+0x65
#1 0xffffffff80c1bb1f at vpanic+0x17f
#2 0xffffffff80c1b993 at panic+0x43
#3 0xffffffff810afdf5 at trap_fatal+0x385
#4 0xffffffff81087528 at calltrap+0x8
#5 0xffffffff8108c775 at restore_fpu_curthread+0x85
#6 0xffffffff810854f1 at done_load_dr+0x31
#7 0xffffffff80c28892 at mi_switch+0xc2
#8 0xffffffff80c790e6 at sleepq_catch_signals+0x2e6
#9 0xffffffff80c78de9 at sleepq_wait_sig+0x9
#10 0xffffffff80baf75c at _cv_wait_sig+0xec
#11 0xffffffff80c8ab5d at seltdwait+0x9d
#12 0xffffffff80c8a62e at kern_select+0x92e
#13 0xffffffff80c8a9d6 at sys_select+0x56
#14 0xffffffff810b06ec at amd64_syscall+0x10c
#15 0xffffffff81087e3b at fast_syscall_common+0xf8
Uptime: 15m6s
Automatic reboot in 15 seconds - press a key on the console to abort
```

I dont see much in the system's syslog which is receiving the guest VM

```
May 25 21:09:11 virtboxtest2 kernel: [1230622.159602] audit: type=1400 audit(1653512951.197:164): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libvirt-a51b968e-424e-4f20-a60b-9f332529b90a" pid=51349 comm="apparmor_parser"
May 25 21:09:11 virtboxtest2 kernel: [1230622.276846] audit: type=1400 audit(1653512951.313:165): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirt-a51b968e-424e-4f20-a60b-9f332529b90a" pid=51352 comm="apparmor_parser"
May 25 21:09:11 virtboxtest2 kernel: [1230622.406953] audit: type=1400 audit(1653512951.441:166): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirt-a51b968e-424e-4f20-a60b-9f332529b90a" pid=51356 comm="apparmor_parser"
May 25 21:09:11 virtboxtest2 kernel: [1230622.536461] audit: type=1400 audit(1653512951.573:167): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="libvirt-a51b968e-424e-4f20-a60b-9f332529b90a" pid=51360 comm="apparmor_parser"
May 25 21:09:11 virtboxtest2 networkd-dispatcher[911]: WARNING:Unknown index 22 seen, reloading interface list
May 25 21:09:11 virtboxtest2 systemd-udevd[51364]: Using default interface naming scheme 'v249'.
May 25 21:09:11 virtboxtest2 kernel: [1230622.694004] audit: type=1400 audit(1653512951.729:168): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirt-a51b968e-424e-4f20-a60b-9f332529b90a" pid=51374 comm="apparmor_parser"
May 25 21:09:11 virtboxtest2 systemd[1]: Started Virtual Machine qemu-15-13Test.
May 25 21:09:12 virtboxtest2 systemd-networkd[884]: macvtap13: Link UP
May 25 21:09:12 virtboxtest2 systemd-networkd[884]: macvtap13: Gained carrier
May 25 21:09:12 virtboxtest2 kernel: [1230623.752178] audit: type=1400 audit(1653512952.789:169): apparmor="DENIED" operation="open" profile="libvirt-a51b968e-424e-4f20-a60b-9f332529b90a" name="/etc/ssl/openssl.cnf" pid=51377 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=64055 ouid=0
May 25 21:09:13 virtboxtest2 systemd[1]: session-397.scope: Deactivated successfully.
May 25 21:09:14 virtboxtest2 systemd-networkd[884]: macvtap13: Gained IPv6LL
May 25 21:09:14 virtboxtest2 ModemManager[48708]: <info>  [base-manager] couldn't check support for device '/sys/devices/pci0000:00/0000:00:01.3/0000:03:00.2/0000:20:01.0/0000:23:00.0': not supported by any plugin
```

not sure if that is normal or not ?   Like i said, it was working OK a few weeks ago.

---

### Post by TheFu on 2022-05-25
Check the specific CPU model in each VM XML settings.  The lowest CPU must be set there.

---

### Post by mdtancsa on 2022-05-25
Thanks, I forgot to mention, I tried booting with the vm set to kvm64 and other lower end CPUs
ie
```
  <cpu>
  <cpu mode='custom' match='exact' check='none'>
    <model fallback='forbid'>kvm64</model>
  </cpu>

```
and the same result.  Are there other cpu options to try ?

---

### Post by TheFu on 2022-05-25
[https://qemu.readthedocs.io/en/latest/system/qemu-cpu-models.html](https://qemu.readthedocs.io/en/latest/system/qemu-cpu-models.html)
> **Other non-recommended x86 CPUs**

The following CPUs models are compatible with most AMD and Intel x86 hosts, but their usage is discouraged, as they expose a very limited featureset, which prevents guests having optimal performance.

Why did you forbid?

---

### Post by mdtancsa on 2022-05-25
Not sure how/why that got there by virtmanager.  If I make an Ubuntu 22 image on the Ryzen 2700, I start with the following CPU in the xml def

```
  <cpu mode='custom' match='exact' check='partial'>
    <model fallback='allow'>EPYC-IBPB</model>
  </cpu>
```

and /proc/cpu looks like
```
cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 23
model           : 1
model name      : AMD EPYC Processor (with IBPB)
stepping        : 2
microcode       : 0x1000065
cpu MHz         : 3692.850
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm rep_good nopl cpuid extd_apicid tsc_known_freq pni pclmulqdq ssse3 fma cx16 sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx f16c rdrand hypervisor lahf_lm svm cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw topoext ibpb vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx clflushopt sha_ni xsaveopt xsavec xgetbv1 arat npt nrip_save
bugs            : fxsave_leak sysret_ss_attrs null_seg spectre_v1 spectre_v2 spec_store_bypass
bogomips        : 7385.70
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
```

but once I migrate it over to the 5800 it looks like this?
```
  <cpu mode='custom' match='exact' check='full'>
    <model fallback='forbid'>EPYC-IBPB</model>
    <feature policy='disable' name='monitor'/>
    <feature policy='require' name='x2apic'/>
    <feature policy='require' name='hypervisor'/>
    <feature policy='require' name='topoext'/>
    <feature policy='require' name='npt'/>
    <feature policy='require' name='nrip-save'/>
  </cpu>

```
then I migrate it back, it looks like this 
```
  <cpu mode='custom' match='exact' check='partial'>
    <model fallback='allow'>EPYC-IBPB</model>
  </cpu>

```
but its hung and then a crash
```
traps: PANIC: double fault, error_code: 0x0
double fault: 0000 [#1] SMP NOPTI
CPU: 0 PID: 173 Comm: multipathd Tainted: G        W         5.15.0-1005-kvm #5-Ubuntu
Hardware name: QEMU Standard PC (i440FX + PIIX, 1996), BIOS 1.15.0-1 04/01/2014
RIP: 0010:0xffffffffa38c0146
Code: 5c 65 c6 05 df aa 75 5c 00 eb bc cc cc cc cc cc cc cc cc cc 55 48 89 e5 41 57 41 56 41 55 49 89 f5 41 54 49 89 fc 41 0f 20 d6 <65> 48 8b 04 25 40 ac 01 00 48 8b 80 d8 03 00 00 0f 0d 48 78 8b 05
RSP: 0008:00007f09778d6018 EFLAGS: 00010097
RAX: 00000000a3a00de7 RBX: 0000000000000000 RCX: ffffffffa3a00de7
RDX: 0000000000000000 RSI: 0000000000000000 RDI: 00007f09778d6048
RBP: 00007f09778d6038 R08: 0000000000000000 R09: 0000000000000000
R10: 0000000000000000 R11: 0000000000000000 R12: 00007f09778d6048
R13: 0000000000000000 R14: 000000000001ac40 R15: 0000000000000000
FS:  00007f0977915600(0000) GS:ffff9c91bbc00000(0000) knlGS:ffff9c91bbc00000
CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
CR2: 00007f09778d5ff8 CR3: 0000000103590000 CR4: 00000000001506b0
Call Trace:
Modules linked in: nls_iso8859_1 nls_cp437 vfat fat loop kvm_amd pata_acpi dm_multipath dm_mod fuse configfs ip_tables x_tables
---[ end trace 6052303c1c5f9b3b ]---
RIP: 0010:0xffffffffa38c0146
Code: 5c 65 c6 05 df aa 75 5c 00 eb bc cc cc cc cc cc cc cc cc cc 55 48 89 e5 41 57 41 56 41 55 49 89 f5 41 54 49 89 fc 41 0f 20 d6 <65> 48 8b 04 25 40 ac 01 00 48 8b 80 d8 03 00 00 0f 0d 48 78 8b 05
RSP: 0008:00007f09778d6018 EFLAGS: 00010097
RAX: 00000000a3a00de7 RBX: 0000000000000000 RCX: ffffffffa3a00de7
RDX: 0000000000000000 RSI: 0000000000000000 RDI: 00007f09778d6048
RBP: 00007f09778d6038 R08: 0000000000000000 R09: 0000000000000000
R10: 0000000000000000 R11: 0000000000000000 R12: 00007f09778d6048
R13: 0000000000000000 R14: 000000000001ac40 R15: 0000000000000000
FS:  00007f0977915600(0000) GS:ffff9c91bbc00000(0000) knlGS:ffff9c91bbc00000
CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
CR2: 00007f09778d5ff8 CR3: 0000000103590000 CR4: 00000000001506b0
Kernel panic - not syncing: Fatal exception in interrupt
Shutting down cpus with NMI
Kernel Offset: 0x22000000 from 0xffffffff81000000 (relocation range: 0xffffffff80000000-0xffffffffbfffffff)
Linux version 5.15.0-1005-kvm (buildd@lcy02-amd64-089) (gcc (Ubuntu 11.2.0-19ubuntu1) 11.2.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #5-Ubuntu SMP Wed Apr 20 05:41:50 UTC 2022 (Ubuntu 5.15.0-1005.5-kvm 5.15.30)
Command line: BOOT_IMAGE=/boot/vmlinuz-5.15.0-1005-kvm root=PARTUUID=e58420d6-3a2a-4d04-9f8a-8931390c10fc ro console=tty1 console=ttyS0 panic=-1
x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
signal: max sigframe size: 1776
BIOS-provided physical RAM map:
BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
BIOS-e820: [mem 0x0000000000100000-0x00000000bffd7fff] usable
BIOS-e820: [mem 0x00000000bffd8000-0x00000000bfffffff] reserved
BIOS-e820: [mem 0x00000000feffc000-0x00000000feffffff] reserved
BIOS-e820: [mem 0x00000000fffc0000-0x00000000ffffffff] reserved
BIOS-e820: [mem 0x0000000100000000-0x000000013fffffff] usable
NX (Execute Disable) protection: active
SMBIOS 2.8 present.
DMI: QEMU Standard PC (i440FX + PIIX, 1996), BIOS 1.15.0-1 04/01/2014
Hypervisor detected: KVM
kvm-clock: Using msrs 4b564d01 and 4b564d00
kvm-clock: cpu 0, msr ad0f9001, primary cpu clock
kvm-clock: using sched offset of 212506061702 cycles
clocksource: kvm-clock: mask: 0xffffffffffffffff max_cycles: 0x1cd42e4dffb, max_idle_ns: 881590591483 ns
tsc: Detected 3692.850 MHz processor
last_pfn = 0x140000 max_arch_pfn = 0x400000000
x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
last_pfn = 0xbffd8 max_arch_pfn = 0x400000000
found SMP MP-table at [mem 0x000f5b40-0x000f5b4f]
Using GB pages for direct mapping
ACPI: Early table checksum verification disabled
ACPI: RSDP 0x00000000000F5910 000014 (v00 BOCHS )
ACPI: RSDT 0x00000000BFFE180E 000030 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
ACPI: FACP 0x00000000BFFE16F2 000074 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
ACPI: DSDT 0x00000000BFFE0040 0016B2 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
ACPI: FACS 0x00000000BFFE0000 000040
ACPI: APIC 0x00000000BFFE1766 000080 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
ACPI: WAET 0x00000000BFFE17E6 000028 (v01 BOCHS  BXPC     00000001 BXPC 00000001)
ACPI: Reserving FACP table memory at [mem 0xbffe16f2-0xbffe1765]
ACPI: Reserving DSDT table memory at [mem 0xbffe0040-0xbffe16f1]
ACPI: Reserving FACS table memory at [mem 0xbffe0000-0xbffe003f]
ACPI: Reserving APIC table memory at [mem 0xbffe1766-0xbffe17e5]
ACPI: Reserving WAET table memory at [mem 0xbffe17e6-0xbffe180d]
No NUMA configuration found
Faking a node at [mem 0x0000000000000000-0x000000013fffffff]
NODE_DATA(0) allocated [mem 0x13fffb000-0x13fffdfff]
Zone ranges:
  DMA32    [mem 0x0000000000001000-0x00000000ffffffff]
  Normal   [mem 0x0000000100000000-0x000000013fffffff]
Movable zone start for each node
Early memory node ranges
  node   0: [mem 0x0000000000001000-0x000000000009efff]
  node   0: [mem 0x0000000000100000-0x00000000bffd7fff]
  node   0: [mem 0x0000000100000000-0x000000013fffffff]
Initmem setup node 0 [mem 0x0000000000001000-0x000000013fffffff]
On node 0, zone DMA32: 1 pages in unavailable ranges
On node 0, zone DMA32: 97 pages in unavailable ranges
On node 0, zone Normal: 40 pages in unavailable ranges
```

---

### Post by mdtancsa on 2022-05-25
Tried a very minimal install 
```
virt-install --name manualBSD --memory 4096 --vcpus 2 --disk /vms/13m.qcow2,bus=virtio --import --os-variant freebsd13.0 --network default
```
and the same behaviour

I am going to re-install the original Ubuntu 22 as it used to work without issue and then try with some older kernels to see if its the kernel or libvirt updates.  This doesnt seem to be an issue with 20.04 LTS as I have a 5800 in that mix. However, thats an older kernel and hypervisor

---

### Post by TheFu on 2022-05-26
Just throwing out ideas at this point, but I don't know.

Doesn't storage has to be shared by the 2 machines to work.  That's always been a requirement.  iSCSI, NFS, or a clusterFS like Gluster, or Sheepdog are common.
[https://www.linux-kvm.org/page/Migration#Requirements](https://www.linux-kvm.org/page/Migration#Requirements)
> Requirements

[LIST]
[*]    The VM image is accessible on both source and destination hosts (located on a shared storage, e.g. using nfs).
[*]    It is recommended an images-directory would be found on the same path on both hosts (for migrations of a copy-on-write image -- an image created on top of a base-image using "qemu-image create -b ...")
[*]    The src and dst hosts must be on the same subnet (keeping guest's network when tap is used).
[*]    Do not use -snapshot qemu command line option.
[*]    For tcp: migration protocol
[*]    the guest on the destination must be started the same way it was started on the source.
[/LIST]


I'm still confused by the 
```
<model fallback='[COLOR="#FF0000"]forbid[/COLOR]'>EPYC-IBPB</model>
```
That forbid needs to be '[COLOR="#008000"]allow[/COLOR]', doesn't it?

I've not done a live migration, but I have migrated at least 30 different VMs between different systems, including changing CPUs and even changing from Intel to AMD CPUs.

Completely off topic, but have you seen that lxd can manage KVM VMs now and if you use ZFS as the backing storage, the same migrations that lxd supports with lxc can be done for kvm/qemu?

---

### Post by mdtancsa on 2022-05-26
Just confirmed that if I install 20.04.4 everything works as expected. I can migrate guests back and forth without issue using 5.4.0-113. I then updated the kernel to HWE using 5.13.0-44 and made sure all apps are upto date and still all good with that kernel as well.

---

### Post by mdtancsa on 2022-05-26
The storage is shared over nfs. Live migrations etc, have been working for quite some time in this setup. Its only in the past 2 - 3 weeks that they all of a sudden broke.  If there is no shared storage, the migration will not proceed.  In my case, the sender and receiver both think it worked, but the resultant guest is either hung or crashes.  The same results happen if I dont do a live migration

---

### Post by mdtancsa on 2022-05-26
> **mdtancsa said:**
> Just confirmed that if I install 20.04.4 everything works as expected. I can migrate guests back and forth without issue using 5.4.0-113. I then updated the kernel to HWE using 5.13.0-44 and made sure all apps are upto date and still all good with that kernel as well.

OK, did a fresh install of 22 LTS with 5.15.0-25.   It works as expected for migrating between hosts.  I then do an 


```
apt dist-upgrade






The following NEW packages will be installed:
  linux-headers-5.15.0-33 linux-headers-5.15.0-33-generic linux-image-5.15.0-33-generic linux-modules-5.15.0-33-generic linux-modules-extra-5.15.0-33-generic
The following packages will be upgraded:
  apport base-files bind9-dnsutils bind9-host bind9-libs curl distro-info-data dnsmasq-base dpkg firmware-sof-signed git git-man libcurl3-gnutls libcurl4 libfribidi0 libjson-c5 libldap-2.5-0 libldap-common libnss-mymachines libnss-systemd
  libpam-systemd libpcre3 librados2 librbd1 libssl3 libsystemd0 libudev1 libxml2 libxml2-utils linux-firmware linux-generic linux-headers-generic linux-image-generic logrotate motd-news-config needrestart networkd-dispatcher openssl
  python3-apport python3-libxml2 python3-problem-report python3-software-properties python3-twisted rsyslog snapd software-properties-common systemd systemd-container systemd-sysv systemd-timesyncd ubuntu-advantage-tools udev
52 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
29 standard security updates

```

and reboot to the new kernel, and migrations fail as described in the original post. 

if I reboot back to the original 5.15.0-25 kernel, again migrations work.

---

### Post by Doug S on 2022-05-26
As a further test, I suggest you try [mainline kernel 5.18]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.18/"). The reason is to know if the issue has already been fixed upstream or not. If it has been fixed upstream, then it should be just a matter of time until it propagates down to the 5.15 series. If it hasn't been fixed, then a bug report or bisecting the kernel to isolate and identify the problem commit.

---

### Post by DuckHook on 2022-05-26
Just a FYI, but your posts are difficult to read. Please use [noparse]```

```[/noparse] tags for posting terminal input/output. Also refrain from using nonstandard fonts and styles when posting. Some of the odd colours could not render properly on my screen.

---

### Post by TheFu on 2022-05-27
When the migration works, is the 'forbid' line still there?  Asked about that line a few posts ago - never saw an answer.
> <model fallback='forbid'>EPYC-IBPB</model>

---

### Post by mdtancsa on 2022-05-27
> **TheFu said:**
> When the migration works, is the 'forbid' line still there?  Asked about that line a few posts ago - never saw an answer.

On one of my test VMs while the guest is idle, the cpu settings look as follow

```
  <cpu mode='custom' match='exact' check='partial'>
    <model fallback='allow'>EPYC-IBPB</model>
  </cpu>
[COLOR=#000000]
[/COLOR]
```

I then start it up, and then do a dumpxml to that VM, the output is different.  So not sure why the hypervisor does that. This is literally virsh start vm, virsh dumpxml vm before any sort of migration.  

```

 virsh dumpxml u22 | grep -A10 "cpu mod"
  <cpu mode='custom' match='exact' check='full'>
    <model fallback='forbid'>EPYC-IBPB</model>
    <feature policy='disable' name='monitor'/>
    <feature policy='require' name='x2apic'/>
    <feature policy='require' name='hypervisor'/>
    <feature policy='require' name='topoext'/>
    <feature policy='require' name='npt'/>
    <feature policy='require' name='nrip-save'/>
  </cpu>
  <clock offset='utc'>
    <timer name='rtc' tickpolicy='catchup'/>

```

I then do a migration, and on the target server running 5.15.0-25 (last known working version of the ubuntu kernel for me on 22 LTS)
```

 virsh dumpxml 3 | grep -A10 "cpu mo"
  <cpu mode='custom' match='exact' check='full'>
    <model fallback='forbid'>EPYC-IBPB</model>
    <feature policy='disable' name='monitor'/>
    <feature policy='require' name='x2apic'/>
    <feature policy='require' name='hypervisor'/>
    <feature policy='require' name='topoext'/>
    <feature policy='require' name='npt'/>
    <feature policy='require' name='nrip-save'/>
  </cpu>
  <clock offset='utc'>
    <timer name='rtc' tickpolicy='catchup'/>

```

I then do a migration back
```

 virsh migrate --verbose --unsafe --live u22 qemu+ssh://virtboxtest2/system
Migration: [100 %]

```

and on the original server where I started it up
```

 virsh dumpxml u22 | grep -A10 "cpu mod"
  <cpu mode='custom' match='exact' check='full'>
    <model fallback='forbid'>EPYC-IBPB</model>
    <feature policy='disable' name='monitor'/>
    <feature policy='require' name='x2apic'/>
    <feature policy='require' name='hypervisor'/>
    <feature policy='require' name='topoext'/>
    <feature policy='require' name='npt'/>
    <feature policy='require' name='nrip-save'/>
  </cpu>
  <clock offset='utc'>
    <timer name='rtc' tickpolicy='catchup'/>

```


If I then shutdown the VM, its back to where I started.
```

mdtancsa@virtboxtest2:~$ virsh console u22
Connected to domain 'u22'
Escape character is ^] (Ctrl + ])


test2 login: 
test2 login: 
test2 login: 
mdtancsa@virtboxtest2:~$ virsh destroy u22
Domain 'u22' destroyed


mdtancsa@virtboxtest2:~$ 
mdtancsa@virtboxtest2:~$ virsh dumpxml u22 | grep -A10 "cpu mod"
  <cpu mode='custom' match='exact' check='partial'>
    <model fallback='allow'>EPYC-IBPB</model>
  </cpu>
  <clock offset='utc'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
mdtancsa@virtboxtest2:~$ 

```

I am not an KVM expert, so I dont know if that is normal or expected.

---

### Post by mdtancsa on 2022-05-27
> **Doug S said:**
> As a further test, I suggest you try [mainline kernel 5.18]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.18/"). The reason is to know if the issue has already been fixed upstream or not. If it has been fixed upstream, then it should be just a matter of time until it propagates down to the 5.15 series. If it hasn't been fixed, then a bug report or bisecting the kernel to isolate and identify the problem commit.

Thanks, I havent used any kernels outside of what gets pushed via apt dist-upgrade.  I take it I just download and install those .deb files ?  Is there documentation you can suggest around this process  ?

EDIT: OK, that was easier than I thought!  I downloaded those .deb files and installed and rebooted to the new kernel. So far so good on a couple of tests. I will try the same on the semi production machine too!  Thanks for the suggestion

---

### Post by mdtancsa on 2022-05-27
OK the behaviour has for sure improved. Most of my VMs I can migrate back and forth. However, a FreeBSD vm thats RELENG12 crashed. This had a CPU setting inherited from long ago
```

  <cpu mode='custom' match='exact' check='full'>
    <model fallback='forbid'>Nehalem</model>
    <feature policy='require' name='vme'/>
    <feature policy='require' name='x2apic'/>
    <feature policy='require' name='hypervisor'/>
  </cpu>

```

but if I change it to 
```

  <cpu mode='custom' match='exact' check='partial'>
    <model fallback='allow'>EPYC</model>
  </cpu>


```

migration works.  I am not sure at this point if things were working all these years by happy accident, and now with newer kernels, migrations are more strict.  But the same xml definitions work without problem on ubuntu 20.x on this hardware mix.  On Ubuntu 22 with its latest official kernel, migrations dont work at all. With the mainline kernel "5.18.0-051800-generic #202205222030 SMP PREEMPT_DYNAMIC Sun May 22 20:33:46 UTC 2022", migrations between the Ryzens work, but only if the CPU def is set to EPYC or EPYC-IBPB.

I think in general I need to get my head around CPU options and such for guest VMs. Can anyone suggest some good, upto date docs to read around this ?

So to summarize,

On ubuntu 20.04 LTS with latest Ubuntu updates, I can migrate VMs back and forth between a 3700x and a 5800x without issue. Guests are a mix of Ubuntu, Fedora and FreeBSD
On Ubuntu 22 LTS, with the original kernel from release day, I can migrate VMs back and forth between a 3700x and a 5800x without issue
On Ubuntu 22 LTS with everything up to date as of mid May 2022, I can migrate from the 3700X to the 5800x without issue. But going from the 5800x to the 3700x results in a migrated VM that either crashes inside the VM or has the CPU pegged at 100% spinning its wheels with the guest frozen and needing a hard reset. This is with --live or without and with --unsafe or without. The crash / hang happens once the VM is fully migrated with the sender thinking it was successfully sent and the receiver thinking it successfully arrived in. 
On Ubuntu 22 LTS with everything up to date as of mid May 2022 with 5.18.0-051800-generic #202205222030 SMP PREEMPT_DYNAMIC Sun May 22. I can migrate VMs back and forth that have as its CPU def EPYC or EPYC-IBPB. If the def (in my one test case anyways) is Nehalem then I get a frozen VM on migration back to the 3700X.

I have 3 different 5800x based machines. One running 20.04 LTS in production that has stayed running 20.04LTS. Another in semi production running 22 LTS and the 5.18 kernel, and then one test 5800x which I installed fresh copies of 20, 22 and the 5.18 kernel to test with.

---

### Post by Doug S on 2022-05-27
Thanks for your investigation and write up. I wouldn't necessarily expect a vCPU set to "Nehalem" (an older Intel processor) to work. Myself, the cpu emulations is not something I mess around with. Mine are all as default:

```
doug@s19:~$ sudo grep "cpu mode" /etc/libvirt/qemu/*.xml
/etc/libvirt/qemu/desk-ff.xml:  <cpu mode='host-model' check='partial'/>
/etc/libvirt/qemu/desk-hh.xml:  <cpu mode='host-model' check='partial'/>
/etc/libvirt/qemu/desk-ii.xml:  <cpu mode='host-model' check='partial'/>
/etc/libvirt/qemu/serv-xx.xml:  <cpu mode='host-model' check='partial'/>
```

---

### Post by mdtancsa on 2022-05-27
> **Doug S said:**
> Thanks for your investigation and write up. I wouldn't necessarily expect a vCPU set to "Nehalem" (an older Intel processor) to work. Myself, the cpu emulations is not something I mess around with. Mine are all as default:

```
doug@s19:~$ sudo grep "cpu mode" /etc/libvirt/qemu/*.xml
/etc/libvirt/qemu/desk-ff.xml:  <cpu mode='host-model' check='partial'/>
/etc/libvirt/qemu/desk-hh.xml:  <cpu mode='host-model' check='partial'/>
/etc/libvirt/qemu/desk-ii.xml:  <cpu mode='host-model' check='partial'/>
/etc/libvirt/qemu/serv-xx.xml:  <cpu mode='host-model' check='partial'/>
```

Another datapoint. If I use host-model as above, migration works as expected in both directions. However if I select 
```

<cpu mode='host-passthrough' check='none' migratable='on'/>

```
its back to the borked behaviour with the mainline kernel where I cant migrate from the 5800x even on the latest mainline kernel

At this point, I am still not sure if this is a bug/regression or the fact that things worked up until some kernel post 5.15.0.25 just by fluke.  re: Nehalem, I would have thought it would work in that its more of a lowest common denominator.

---

