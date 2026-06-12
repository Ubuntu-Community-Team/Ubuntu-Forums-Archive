---
title: "Strange issue,  input/output issue, host ok. 9.10 host, JeOs on kvm instances"
date: 2009-11-24
forum: Virtualisation
---

### Post by king756 on 2009-11-24
Hi,

I am running a set of kvm based virtual machines on Ubuntu 9.10 headles Server. The virtualised instances are running JeOS and built using the below 

```

vmbuilder kvm ubuntu --suite=karmic --flavour=virtual --arch=i386 --mirror=http://192.168.0.100:9999/ubuntu -o --libvirt=qemu:///system --tmpfs=- --ip=192.168.0.101 --part=vmbuilder.partition --templates=mytemplates --user=admin --name=admin --pass=password--firstboot=boot.sh --mem=512 --hostname=TestServer --dest=/home/admin/virtual-machines

```

I can start the virtualised machines fine from virsh, and they run as expected... for a while. Then for some reason when I come to connect to them after a period of a hour or so ussing SSH i get input/output errors when trying to execute commands via SSH. As I get input/output errors I can not view the log files, if I destroy the VM and restart it the logs are clean (guess it couldn't write the error messages to them). If I do a 'dmesg' I get IO errors on drive /dev/sda .

I'm not to sure where to start looking into this, virsualisation is new to me. Their are no IO errors on the host, '/dev/sda' would be virtualised? 

I am also struggling in that the host is a headless server so not figured out yet how to view the virtualised machine outside of ssh to it. Reading this is done via VNC? The host has no X installed and I can't seem to VNC in from a seperate machine to connect to the virtualised instance, any pointers?

Hi,

I am running a set of kvm based virtual machines on Ubuntu 9.10 headles Server. The virtualised instances are running JeOS and built using the below 

```

vmbuilder kvm ubuntu --suite=karmic --flavour=virtual --arch=i386 --mirror=http://192.168.0.100:9999/ubuntu -o --libvirt=qemu:///system --tmpfs=- --ip=192.168.0.101 --part=vmbuilder.partition --templates=mytemplates --user=admin --name=admin --pass=password--firstboot=boot.sh --mem=512 --hostname=TestServer --dest=/home/admin/virtual-machines

```

I can start the virtualised machines fine from virsh, and they run as expected... for a while. Then for some reason when I come to connect to them after a period of a hour or so ussing SSH i get input/output errors when trying to execute commands via SSH. As I get input/output errors I can not view the log files, if I destroy the VM and restart it the logs are clean (guess it couldn't write the error messages to them). If I do a 'dmesg' I get IO errors on drive /dev/sda .

I'm not to sure where to start looking into this, virsualisation is new to me. Their are no IO errors on the host, '/dev/sda' would be virtualised? 

I am also struggling in that the host is a headless server so not figured out yet how to view the virtualised machine outside of ssh to it. Reading this is done via VNC? The host has no X installed and I can't seem to VNC in from a seperate machine to connect to the virtualised instance, any pointers?

Below is a excerpt I am seeing dmesg, unfortunatley  if I pipe it through less or to a file I get a input/output error which makes it hard chaising this down
```

[ 6697.240297]          res 41/04:08:38:40:0c/00:00:00:00:00/e0 Emask 0x1 (device error)
[ 6697.242048] ata1.00: status: { DRDY ERR }
[ 6697.242498] ata1.00: error: { ABRT }
[ 6697.243656] ata1.00: configured for MWDMA1
[ 6697.243660] ata1: EH complete
[ 6697.243930] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 6697.244514] ata1.00: BMDMA stat 0x5
[ 6697.244946] ata1.00: cmd c8/00:08:38:40:0c/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 6697.244947]          res 41/04:08:38:40:0c/00:00:00:00:00/e0 Emask 0x1 (device error)
[ 6697.246698] ata1.00: status: { DRDY ERR }
[ 6697.247148] ata1.00: error: { ABRT }
[ 6697.250646] ata1.00: configured for MWDMA1
[ 6697.250651] ata1: EH complete
[ 6697.250926] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 6697.251485] ata1.00: BMDMA stat 0x5
[ 6697.251921] ata1.00: cmd c8/00:08:38:40:0c/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 6697.251922]          res 41/04:08:38:40:0c/00:00:00:00:00/e0 Emask 0x1 (device error)
[ 6697.253742] ata1.00: status: { DRDY ERR }
[ 6697.254194] ata1.00: error: { ABRT }
[ 6697.255348] ata1.00: configured for MWDMA1
[ 6697.255356] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6697.255359] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 6697.255362] Descriptor sense data with sense descriptors (in hex):
[ 6697.255364]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00
[ 6697.255370]         00 0c 40 38
[ 6697.255372] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[ 6697.255376] end_request: I/O error, dev sda, sector 802872
[ 6697.255901] ata1: EH complete
[ 6697.257136] EXT3-fs error (device sda1): ext3_find_entry: reading directory #24436 offset 0

```

---

### Post by mycastle on 2009-11-25
I have the same problem.

@king756: You can use virt-viewer (optional embedded in virt-manager) to view the guest's console up from booting the vm.

---

### Post by Boblin on 2010-01-12
I have the same problem.

---

### Post by king756 on 2010-01-12
Unfortunatley I never found a fix for this. It looks like I am not the only person with the issue. What are you guy setups, just to compare?

---

### Post by Boblin on 2010-02-01
I found that in my case was problem with double mounted partition.

---

