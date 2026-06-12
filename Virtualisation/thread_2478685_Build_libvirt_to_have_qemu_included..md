---
title: "Build libvirt to have qemu included."
date: 2022-09-02
forum: Virtualisation
---

### Post by mathewtfra on 2022-09-02
I have built the latest code from [https://libvirt.org/](https://libvirt.org/). The build commands were 'meson build -Dsystem=true; ninja -C build'. When I list the virsh capabilities, I am seeing only 'lxc' as domain type for x86_64 architecture, I wanted to have qemu and kvm as well as the domain type. libvirt/build/src/qemu is empty. I think the Qemu binaries are not built with my build commands. Can some one point me to include Qemu? Following is the 'virsh capabilities'

```

# virsh capabilities
<capabilities>


  <host>
    <uuid>b271809d-c3e0-4526-92e9-549addb8f948</uuid>
    <cpu>
      <arch>x86_64</arch>
      <pages unit='KiB' size='4'/>
      <pages unit='KiB' size='2048'/>
      <pages unit='KiB' size='1048576'/>
    </cpu>
    <power_management>
      <suspend_mem/>
      <suspend_disk/>
      <suspend_hybrid/>
    </power_management>
    <iommu support='no'/>
    <topology>
      <cells num='1'>
        <cell id='0'>
          <memory unit='KiB'>16384572</memory>
          <cpus num='8'>
            <cpu id='0' socket_id='0' die_id='0' core_id='0' siblings='0'/>
            <cpu id='1' socket_id='1' die_id='0' core_id='0' siblings='1'/>
            <cpu id='2' socket_id='2' die_id='0' core_id='0' siblings='2'/>
            <cpu id='3' socket_id='3' die_id='0' core_id='0' siblings='3'/>
            <cpu id='4' socket_id='4' die_id='0' core_id='0' siblings='4'/>
            <cpu id='5' socket_id='5' die_id='0' core_id='0' siblings='5'/>
            <cpu id='6' socket_id='6' die_id='0' core_id='0' siblings='6'/>
            <cpu id='7' socket_id='7' die_id='0' core_id='0' siblings='7'/>
          </cpus>
        </cell>
      </cells>
    </topology>
    <cache>
      <bank id='0' level='3' type='both' size='16' unit='MiB' cpus='0'/>
      <bank id='1' level='3' type='both' size='16' unit='MiB' cpus='1'/>
      <bank id='2' level='3' type='both' size='16' unit='MiB' cpus='2'/>
      <bank id='3' level='3' type='both' size='16' unit='MiB' cpus='3'/>
      <bank id='4' level='3' type='both' size='16' unit='MiB' cpus='4'/>
      <bank id='5' level='3' type='both' size='16' unit='MiB' cpus='5'/>
      <bank id='6' level='3' type='both' size='16' unit='MiB' cpus='6'/>
      <bank id='7' level='3' type='both' size='16' unit='MiB' cpus='7'/>
    </cache>
    <secmodel>
      <model>none</model>
      <doi>0</doi>
    </secmodel>
  </host>


  <guest>
    <os_type>exe</os_type>
    <arch name='x86_64'>
      <wordsize>64</wordsize>
      <emulator>/usr/libexec/libvirt_lxc</emulator>
      <domain type='lxc'/>
    </arch>
  </guest>


  <guest>
    <os_type>exe</os_type>
    <arch name='i686'>
      <wordsize>32</wordsize>
      <emulator>/usr/libexec/libvirt_lxc</emulator>
      <domain type='lxc'/>
    </arch>
  </guest>


</capabilities>

```

---

### Post by mathewtfra on 2022-09-04
while building the library, pass '-[COLOR=#1D1C1D][FONT=Slack-Lato]Ddriver_qemu=enabled' argument as well.[/FONT][/COLOR]

---

