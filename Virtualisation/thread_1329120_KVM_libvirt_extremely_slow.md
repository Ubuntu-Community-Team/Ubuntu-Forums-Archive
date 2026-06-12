---
title: "KVM libvirt extremely slow"
date: 2009-11-17
forum: Virtualisation
---

### Post by nmueller on 2009-11-17
Hi,

I have a Ubuntu 9.10 64bit installation as a host with KVM installed on it. I created a new Ubuntu 9.10 64bit installation using *ubuntu-vm-builder* which works great with the run.sh script generated automatically.

The content of the script is the following:
```
exec kvm -m 1024 -smp 1 -drive file=ubuntu_karmic_64.qcow2 "$@"
```

As I want to test the whole thing with KVM and virt-manager so I used virt-install. I know I used a different os-variant, but karmic was not listed in the man pages yet. So I just used the latest.

```
virt-install --connect qemu:///system --hvm --name vmTestUbuntu --ram 1024 --file /var/lib/libvirt/images/ubuntu_karmic_64.qcow2 --vnc --os-type linux --os-variant ubuntujaunty --import

```

I can start the VM with virt-manager now, but the system is unusable slow. If I start it with the run.sh script its extremely fast. So what is wrong?

Here is my XML configuration file:
```

<domain type='qemu'>
  <name>vmTestUbuntu</name>
  <uuid>e1eb8de0-80e1-ee79-ace4-690bd9092368</uuid>
  <memory>1048576</memory>
  <currentMemory>1048576</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-0.11'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <clock offset='localtime'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <source file='/var/lib/libvirt/images/ubuntu_karmic_64.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <interface type='network'>
      <mac address='54:52:00:7e:44:fd'/>
      <source network='default'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target port='0'/>
    </console>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes' keymap='de'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
    </video>
  </devices>
</domain>                    

```

Here are some additional outputs:

**lsmod | grep kvm**
```

kvm_intel              51528  0 
kvm                   190584  1 kvm_intel

```

[B]egrep '(vmx|svm)' --color=always /proc/cpuinfo
[/B]```

flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority

```
Please tell me, if you need some more information. :-)

---

### Post by nmueller on 2009-11-17
Ok, I think I found the solution by myself.

After I changed domain type to kvm instead of qemu it runs really fast.

---

