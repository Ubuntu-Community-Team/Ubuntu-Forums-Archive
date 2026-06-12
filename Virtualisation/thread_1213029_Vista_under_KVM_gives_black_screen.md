---
title: "Vista under KVM gives black screen"
date: 2009-07-14
forum: Virtualisation
---

### Post by Kilbasar on 2009-07-14
Hi,

I'm trying to get Vista to run under KVM on Jaunty. The installation went perfectly (used the virt-manager installation wizard, mostly default options, selected Vista as the os type). But after install, I cannot boot into the actual OS. All I get is the QEMU fake bios stuff, then a black screen. I've also tried running it from the command line, basically just:

```
kvm -m 1024 -vga std vista.img
```

I've tried each options for "-vga", all give the same result. Anyone gotten around this, or know any other kvm options I should try? Thanks! My XML file for libvirt is below, although it's pretty vanilla.

- Kilbasar

```
# cat vista.xml
<domain type='kvm'>
  <name>vista</name>
  <uuid>73052d3b-02e9-5241-0df2-777a43600f75</uuid>
  <memory>1048576</memory>
  <currentMemory>1048576</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='i686' machine='pc'>hvm</type>
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
      <source file='/etc/vm/vista.img'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <disk type='block' device='cdrom'>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
    <interface type='bridge'>
      <mac address='54:52:00:0b:f8:50'/>
      <source bridge='br0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target port='0'/>
    </console>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes' keymap='en-us'/>
    <sound model='es1370'/>
  </devices>
</domain>
```

---

### Post by juancarlospaco on 2009-07-14
Permisions on image file?
Virtualization extensions?

*It happens to me because no V extensions on CPU.*

---

### Post by skliarie on 2009-08-16
I do have the VMX-enabled processor, and get the same black screen:

# egrep '(vmx|svm)' --color=always /proc/cpuinfo
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority
...

If I disable ACPI, then vista loudly complains about missing APCI support in BIOS and locks up...

---

### Post by skliarie on 2009-09-23
If I run vista from CLI using qemu, the vista works but is unbearably slow:
qemu -m 1024 -name vista -net nic,macaddr=54:52:00:75:83:03,vlan=0,type=ne2k_pci -smp 4 vista.img

How can I run vista using kvm and not all-software qemu emulation?

---

