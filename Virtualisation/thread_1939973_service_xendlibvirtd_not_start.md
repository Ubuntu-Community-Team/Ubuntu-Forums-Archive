---
title: "service xend/libvirtd not start"
date: 2012-03-12
forum: Virtualisation
---

### Post by farzin on 2012-03-12
hello
I compile and install xen 4.1.2 after that I make and install kernel 3.0.23 on ubuntu 11.10 32bit version.I did this steps
A)
apt-get install bcc bin86 gawk bridge-utils iproute libcurl3 libcurl4-openssl-dev bzip2 module-init-tools transfig  texinfo texlive-latex-base texlive-latex-recommended texlive-fonts-extra texlive-fonts-recommended pciutils-dev  build-essential make gcc libc6-dev zlib1g-dev python python-dev python-twisted libncurses5-dev patch libvncserver-dev libsdl-dev libjpeg62-dev iasl libbz2-dev e2fslibs-dev git-core uuid-dev ocaml libx11-dev bison flex xz-utils ocaml-findlib 
libvirt-bin libvirt-dev libvirt-doc mercurial tgif xen-docs-4.1 xen-utils-4.1  xen-tools xen-utils-common  xenwatch xenstore-utils  python-vm-builder
B)
tar -xzvf xen-4.1.2.tar.gz // in my favorite path /usr/src
make xen
make tools
make stubdom
make install-xen
make install-tools PYTHON_PREFIX_ARG=
make install-stubdom
change /etc/xen/xend-config.sxp.back uncomment this part ------>(xend-unix-server yes)
update-rc.d xencommons defaults 19 18
update-rc.d xend defaults 20 21
update-rc.d xendomains defaults 21 20
update-rc.d xen-watchdog defaults 22 23
C)
tar xvf  linux-3.0.23.tar.bz2 //unzip in this path   /usr/src
cd /usr/src/linux-3.0.23
cp /boot/config-3.0.0-12-generic .config
make menuconfig //appear menuconfig window did following settings

ACPI (Advanced Configuration and Power Interface) Support -enabled
Processor type and features &#8594;
    Paravirtualized guest support [y] &#8594;Xen guest support &#8211; enabled
    Allocate 3nd-level pagetables from highmem - disabled //because my ubuntu is 32 bit
    High memory support (64GB)
    PAE (Physical Address Extension) Support - enabled
Bus oprions (PCI etc.) &#8594;Xen PCI frontend &#8211; enabled
Device Drivers &#8594;
    Block Devices 
[*] &#8594;
        Xen virtual block device support &#8211; enabled
        Block-device backend driver &#8211; enabled
    Network device support 
[*] &#8594;
        Xen network device frontend driver &#8211; enabled
        Xen backend network device &#8211; enabled
    Input device support &#8594;
        Miscellaneous devices &#8594;
            Xen virtual keyboard and mouse support &#8211;enabled
    Character devices &#8594;
        Xen Hypervisor console support &#8211; enabled
    Xen driver support &#8594;
        Xen memory balloon driver &#8211; enabled
        Scrub pages before returning them to system &#8211;enabled
        Xen /dev/xen/evtchn device Backend driver support&#8211; enabled
        Xen filesystem &#8211; enabled
        Create compatibility mount point /proc/xen &#8211;enabled
        Create xen entries under /sys/hypervisor &#8211; enabled
        userspace grant access device driver &#8211; enabled
        User-space grant reference allocator driver 

make
make modules_install install
cd /boot
mkinitramfs -o initrd.img-3.0.23 3.0.23
update-grub
D) after reboot system
cat /proc/xen/capabilities   //output is control_d
xm list / xm info show appropriate results and shown domain0 is running 

E)this problems occured in my terminal :I entered these command 

----------------------------- --------
root@LIFEBOOK-AH530:~# service libvirtdd status
libvirtdd: unrecognized service
------------------
also  when I want to install domu gest via virt-manager in last window 
virtual network 'default'(NAT) comes with a red notation and when point on it this message appears:"Could not initialize HAL for ...." 
after all  device share....(vibr0) was choosen
please guide me to solve these 3 problem



------------------------------------------XEND.LOG-----------------------

[2012-03-20 02:12:19 5447] INFO (SrvDaemon:332  ) Xend Daemon started
[2012-03-20 02:12:19 5447] INFO (SrvDaemon:336 ) Xend changeset: unavailable.
[2012-03-20 02:12:19 5447] DEBUG (tcp:96 ) Listening on :8002
[2012-03-20 02:12:19 5447] INFO (XendNetwork:114 ) Not recreating missing unmanaged network xenbr0
[2012-03-20 02:12:20 5447] DEBUG (XendNode:332 ) pscsi record count: 14
[2012-03-20 02:12:20 5447] DEBUG (XendCPUPool:747 ) recreate_active_pools
[2012-03-20 02:12:20 5447] DEBUG (XendDomainInfo:151 ) XendDomainInfo.recreate({'max_vcpu_id': 3, 'cpu_time': 850088379376L, 'ssidref': 0, 'hvm': 0, 'shutdown_reason': 255, 'dying': 0, 'online_vcpus': 4, 'domid': 0, 'paused': 0, 'crashed': 0, 'running': 1, 'maxmem_kb': 4294967292L, 'shutdown': 0, 'mem_kb': 2838244L, 'blocked': 0, 'handle': [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], 'cpupool': 0, 'name': 'Domain-0'} )
[2012-03-20 02:12:20 5447] INFO (XendDomainInfo:169 ) Recreating domain 0, UUID 00000000-0000-0000-0000-000000000000. at /local/domain/0
[2012-03-20 02:12:20 5447] DEBUG (XendDomain:476 ) Adding Domain: 0
[2012-03-20 02:12:20 5447] DEBUG (XendDomain:410 ) number of vcpus to use is 0
[2012-03-20 02:12:21 5447] DEBUG (XendDomainInfo:1881 ) XendDomainInfo.handleShutdownWatch
[2012-03-20 02:12:21 5447] DEBUG (XendDomainInfo:260 ) XendDomainInfo.createDormant({'vcpus_params': {'cap': 0, 'weight': 256}, 'PV_args': '', 'features': '', 'cpus': [[]], 'use_tmp_kernel': False, 'devices': {'6e5ad638-060a-ce73-9207-c1ce07b25aa7': ('vkbd', {'uuid': '6e5ad638-060a-ce73-9207-c1ce07b25aa7', 'backend': '0'} ), 'e13adc28-d7d9-1124-8862-cac9022b04dd': ('vbd', {'uuid': 'e13adc28-d7d9-1124-8862-cac9022b04dd', 'bootable': 1, 'driver': 'paravirtualised', 'dev': 'hda:disk', 'uname': 'file:/var/lib/libvirt/images/ubuntu-hd.img', 'mode': 'w', 'VDI': '', 'backend': '0'} ), 'c9dd5568-2d4d-d3a2-2134-64265fbe0c30': ('vfb', {'vncunused': '1', 'keymap': 'en-us', 'vnc': '1', 'uuid': 'c9dd5568-2d4d-d3a2-2134-64265fbe0c30', 'other_config': {'vncunused': '1', 'keymap': 'en-us', 'vnc': '1'}} ), 'a3912607-107b-e3e2-d4a3-f490a19fd19a': ('vif', {'bridge': 'virbr0', 'mac': '00:16:3e:7a:b8:b8', 'script': '/etc/xen/scripts/vif-bridge', 'uuid': 'a3912607-107b-e3e2-d4a3-f490a19fd19a', 'backend': '0'} ), 'abea384a-301d-bd12-2b6d-da25057cf32a': ('vbd', {'uuid': 'abea384a-301d-bd12-2b6d-da25057cf32a', 'bootable': 0, 'driver': 'paravirtualised', 'dev': 'hdc:cdrom', 'mode': 'r', 'VDI': '', 'backend': '0'} )}, 'memory_sharing': 0, 'superpages': '0', 'VCPUs_live': 1, 'PV_bootloader': '', 'actions_after_crash': 'restart', 'vbd_refs': ['e13adc28-d7d9-1124-8862-cac9022b04dd', 'abea384a-301d-bd12-2b6d-da25057cf32a'], 'PV_ramdisk': '', 'is_control_domain': False, 'name_label': 'ubuntu-hd', 'VCPUs_at_startup': 1, 'HVM_boot_params': {'order': 'c'}, 'platform': {'tsc_mode': '0', 'timer_mode': '1', 'soundhw': 'es1370', 'hpet': '0', 'device_model': '/usr/lib/xen/bin/qemu-dm', 'vpt_align': '1', 'boot': 'c', 'rtc_timeoffset': '0', 'loader': '/usr/lib/xen-default/boot/hvmloader', 'xen_platform_pci': '1', 'acpi': '1', 'pci': [], 'pae': '1', 'apic': '1', 'serial': 'pty', 'parallel': 'none', 'viridian': '0', 'nomigrate': '0', 'usb': '1'}, 'PV_kernel': '', 'console_refs': ['c9dd5568-2d4d-d3a2-2134-64265fbe0c30'], 'vif_refs': ['a3912607-107b-e3e2-d4a3-f490a19fd19a'], 'on_xend_stop': 'ignore', 'pool_name': 'Pool-0', 'memory_static_min': 0, 'HVM_boot_policy': 'BIOS order', 'description': '', 'VCPUs_max': 1, 'start_time': 1332096136.96, 'memory_static_max': 268435456, 'actions_after_shutdown': 'destroy', 'use_tmp_ramdisk': False, 'on_xend_start': 'ignore', 'memory_dynamic_max': 268435456, 'actions_after_suspend': '', 'is_a_template': False, 'PV_bootloader_args': '', 'memory_dynamic_min': 268435456, 'uuid': '4f106f4d-8cb7-dd98-f2ad-e75095d1e4fb', 'shadow_memory': 3, 'target': 0, 'vcpu_avail': 1L, 'notes': {'SUSPEND_CANCEL': '1'}, 'other_config': {}, 'auto_power_on': False, 'actions_after_reboot': 'restart', 'Description': '', 'status': '1', 'vtpm_refs': []} )
[2012-03-20 02:12:21 5447] INFO (SrvServer:184 ) unix path=/var/lib/xend/xend-socket
[2012-03-20 02:12:21 5447] WARNING (XendAPI:708 ) API call: VBD.set_device not found
[2012-03-20 02:12:21 5447] WARNING (XendAPI:708 ) API call: VBD.set_type not found
[2012-03-20 02:12:21 5447] WARNING (XendAPI:708 ) API call: session.get_all_records not found
[2012-03-20 02:12:21 5447] WARNING (XendAPI:708 ) API call: event.get_record not found
[2012-03-20 02:12:21 5447] WARNING (XendAPI:708 ) API call: event.get_all not found
[2012-03-20 02:12:21 5447] WARNING (XendAPI:708 ) API call: VIF.set_device not found
[2012-03-20 02:12:21 5447] WARNING (XendAPI:708 ) API call: VIF.set_MAC not found
[2012-03-20 02:12:21 5447] WARNING (XendAPI:708 ) API call: VIF.set_MTU not found
[2012-03-20 02:12:21 5447] WARNING (XendAPI:708 ) API call: debug.get_all not found
[2012-03-20 02:12:21 5447] INFO (XMLRPCServer:161 ) Opening Unix domain socket XML-RPC server on /var/run/xend/xen-api.sock; authentication has been disabled for this server.
[2012-03-20 02:12:21 5447] INFO (XMLRPCServer:161 ) Opening Unix domain socket XML-RPC server on /var/run/xend/xmlrpc.sock.



--------------------------XEND-DEBUG.LOG--------------------------

Xend started at Tue Mar 20 02:17:55 2012.
cat: /sys/bus/scsi/devices/host0/vendor: No such file or directory
cat: /sys/bus/scsi/devices/host0/model: No such file or directory
cat: /sys/bus/scsi/devices/host0/type: No such file or directory
cat: /sys/bus/scsi/devices/host0/rev: No such file or directory
cat: /sys/bus/scsi/devices/host0/scsi_level: No such file or directory
cat: /sys/bus/scsi/devices/host1/vendor: No such file or directory
cat: /sys/bus/scsi/devices/host1/model: No such file or directory
cat: /sys/bus/scsi/devices/host1/type: No such file or directory
cat: /sys/bus/scsi/devices/host1/rev: No such file or directory
cat: /sys/bus/scsi/devices/host1/scsi_level: No such file or directory
cat: /sys/bus/scsi/devices/host2/vendor: No such file or directory
cat: /sys/bus/scsi/devices/host2/model: No such file or directory
cat: /sys/bus/scsi/devices/host2/type: No such file or directory
cat: /sys/bus/scsi/devices/host2/rev: No such file or directory
cat: /sys/bus/scsi/devices/host2/scsi_level: No such file or directory
cat: /sys/bus/scsi/devices/host3/vendor: No such file or directory
cat: /sys/bus/scsi/devices/host3/model: No such file or directory
cat: /sys/bus/scsi/devices/host3/type: No such file or directory
cat: /sys/bus/scsi/devices/host3/rev: No such file or directory
cat: /sys/bus/scsi/devices/host3/scsi_level: No such file or directory
cat: /sys/bus/scsi/devices/host4/vendor: No such file or directory
cat: /sys/bus/scsi/devices/host4/model: No such file or directory
cat: /sys/bus/scsi/devices/host4/type: No such file or directory
cat: /sys/bus/scsi/devices/host4/rev: No such file or directory
cat: /sys/bus/scsi/devices/host4/scsi_level: No such file or directory
cat: /sys/bus/scsi/devices/host5/vendor: No such file or directory
cat: /sys/bus/scsi/devices/host5/model: No such file or directory
cat: /sys/bus/scsi/devices/host5/type: No such file or directory
cat: /sys/bus/scsi/devices/host5/rev: No such file or directory
cat: /sys/bus/scsi/devices/host5/scsi_level: No such file or directory
cat: /sys/bus/scsi/devices/target0:0:0/vendor: No such file or directory
cat: /sys/bus/scsi/devices/target0:0:0/model: No such file or directory
cat: /sys/bus/scsi/devices/target0:0:0/type: No such file or directory
cat: /sys/bus/scsi/devices/target0:0:0/rev: No such file or directory
cat: /sys/bus/scsi/devices/target0:0:0/scsi_level: No such file or directory
cat: /sys/bus/scsi/devices/target1:0:0/vendor: No such file or directory
cat: /sys/bus/scsi/devices/target1:0:0/model: No such file or directory
cat: /sys/bus/scsi/devices/target1:0:0/type: No such file or directory
cat: /sys/bus/scsi/devices/target1:0:0/rev: No such file or directory
cat: /sys/bus/scsi/devices/target1:0:0/scsi_level: No such file or directory
cat: /sys/bus/scsi/devices/host6/vendor: No such file or directory
cat: /sys/bus/scsi/devices/host6/model: No such file or directory
cat: /sys/bus/scsi/devices/host6/type: No such file or directory
cat: /sys/bus/scsi/devices/host6/rev: No such file or directory
cat: /sys/bus/scsi/devices/host6/scsi_level: No such file or directory
cat: /sys/bus/scsi/devices/target6:0:0/vendor: No such file or directory
cat: /sys/bus/scsi/devices/target6:0:0/model: No such file or directory
cat: /sys/bus/scsi/devices/target6:0:0/type: No such file or directory
cat: /sys/bus/scsi/devices/target6:0:0/rev: No such file or directory
cat: /sys/bus/scsi/devices/target6:0:0/scsi_level: No such file or directory

---

