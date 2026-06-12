---
title: "XEN 4.4 emulated USB not working using xl"
date: 2014-07-04
forum: Virtualisation
---

### Post by ubeauty on 2014-07-04
I cannot get USB emulated passthrough to work.
I'll be dammed! VGA passthrough - no problem, works beuatifully. What I thought would be the "easy bit" - passing through USB - well not so!
ANY suggestions as to where to look/do/try very welcome.

**Results**:
```
xl create windows7.cfg
``` produces no errors on the command line. From there I can RDP to windows, all is well with it. 

Connected VGA displays Windows log in screen, but no mouse/keyboard etc. - no USB
 - sometimes, there is no USB power either in whcih case I need to reboot.
When there is USB power (e.g. USB mouse laser lights up) - same problem exists...

**My setup:**
ubuntu 14.04 server, kernel 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:45:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
hardware Asrock z97 pro4, 3 x SSD, 16GB RAM, i7, VT-d (on) etc.

Simple windows7 config file for xl:
```
builder='hvm'
device_model_version = "qemu-xen-traditional"
vcpus=6
memory=8192
disk = [
'file:/VMPool/Win7/W7ultimate.img,ioemu:hda,w',
'file:/home/nik/images/windows7.iso,ioemu:hdc:cdrom,r'
]
name="windows7"
vif = ['mac=00:26:B9:48:74:d9,bridge=xenbr0']
gfx_passthru=1
pci=['00:02.0']
usb=1
usbdevice=[ 'host:1.1', 'host:2.1', 'host:3.1', 'host:4.1' ]
localtime=1
on_xend_stop='shutdown'
on_poweroff='destroy'
on_reboot='restart'
on_crash='restart'
boot='c'

```

Result of lsusb after xl create
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

**Interesting bits in bold (from /var/log/xen/qemu-dm-windows7.log)**

```
domid: 7
Strip off blktap sub-type prefix to /VMPool/Win7/W7ultimate.img (drv 'aio')
Using file /VMPool/Win7/W7ultimate.img in read-write mode
Strip off blktap sub-type prefix to /home/nik/images/windows7.iso (drv 'aio')
Using file /home/nik/images/windows7.iso in read-only mode
Watching /local/domain/0/device-model/7/logdirty/cmd
Watching /local/domain/0/device-model/7/command
Watching /local/domain/7/cpu
qemu_map_cache_init nr_buckets = 10000 size 4194304
shared page at pfn feffd
buffered io page at pfn feffb
Guest uuid = 4e1fdbd3-7daa-4b24-9737-8815429755e3
Register xen platform.
Done register platform.
platform_fixed_ioport: changed ro/rw state of ROM memory area. now is rw state.
xs_read(/local/domain/0/device-model/7/xen_extended_power_mgmt): read error
[B]husb: open device 1.1
husb: config #1 need -1
husb: 1 interfaces claimed for configuration 1
husb: grabbed usb device 1.1
usb_linux_update_endp_table: Broken pipe
Warning: could not add USB device host:1.1
husb: open device 2.1
husb: config #1 need -1
husb: 1 interfaces claimed for configuration 1
husb: grabbed usb device 2.1
usb_linux_update_endp_table: Broken pipe
Warning: could not add USB device host:2.1
husb: open device 3.1
husb: config #1 need -1
husb: 1 interfaces claimed for configuration 1
husb: grabbed usb device 3.1
usb_linux_update_endp_table: Broken pipe
Warning: could not add USB device host:3.1
husb: open device 4.1
husb: config #1 need -1
husb: 1 interfaces claimed for configuration 1
husb: grabbed usb device 4.1
usb_linux_update_endp_table: Broken pipe
Warning: could not add USB device host:4.1[/B]
xs_read(): vncpasswd get error. /vm/4e1fdbd3-7daa-4b24-9737-8815429755e3/vncpasswd.
medium change watch on `hdc' (index: 1): aio:/home/nik/images/windows7.iso
I/O request not ready: 0, ptr: 0, port: 0, data: 0, count: 0, size: 0
Log-dirty: no command yet.
I/O request not ready: 0, ptr: 0, port: 0, data: 0, count: 0, size: 0
I/O request not ready: 0, ptr: 0, port: 0, data: 0, count: 0, size: 0
vcpu-set: watch node error.
[xenstore_process_vcpu_set_event]: /local/domain/7/cpu has no CPU!
I/O request not ready: 0, ptr: 0, port: 0, data: 0, count: 0, size: 0
xs_read(/local/domain/7/log-throttling): read error
qemu: ignoring not-understood drive `/local/domain/7/log-throttling'
medium change watch on `/local/domain/7/log-throttling' - unknown device, ignored
I/O request not ready: 0, ptr: 0, port: 0, data: 0, count: 0, size: 0
I/O request not ready: 0, ptr: 0, port: 0, data: 0, count: 0, size: 0
dm-command: hot insert pass-through pci dev 
register_real_device: Assigning real physical device 00:02.0 ...
register_real_device: Disable MSI translation via per device option
register_real_device: Disable power management
pt_iomul_init: Error: pt_iomul_init can't open file /dev/xen/pci_iomul: No such file or directory: 0x0:0x2.0x0
pt_register_regions: IO region registered (size=0x00400000 base_addr=0xef800004)
pt_register_regions: IO region registered (size=0x10000000 base_addr=0xd000000c)
pt_register_regions: IO region registered (size=0x00000040 base_addr=0x0000f001)
pci_intx: intx=1
register_real_device: Real physical device 00:02.0 registered successfuly!
IRQ type = INTx
igd_write_opregion: Map OpRegion: bd5e5018 -> fdffc018
pt_iomem_map: e_phys=e0000000 maddr=d0000000 type=8 len=268435456 index=2 first_map=1
pt_iomem_map: e_phys=f1000000 maddr=ef800000 type=0 len=4194304 index=0 first_map=1
pt_ioport_map: e_phys=c200 pio_base=f000 len=64 index=4 first_map=1
platform_fixed_ioport: changed ro/rw state of ROM memory area. now is rw state.
platform_fixed_ioport: changed ro/rw state of ROM memory area. now is ro state.
13048960291467: qemu version = 1
Unknown PV product 2 loaded in guest
PV driver build 1
region type 1 at [c100,c200).
region type 0 at [f1600000,f1600100).
squash iomem [f1600000, f1600100).
13048960291482: disabled qemu devices 03
ACPI:debug: write addr=0xb044, val=0x0.
.....
```

---

### Post by ubeauty on 2014-07-07
I've made zero progress. Tried just rebuilding the machine from scratch, same outcome, video passes through usb won't.
Does anyone have any clue what "usb_linux_update_endp_table: Broken pipe" is referring to or how to go about tracking it down?

---

