---
title: "ubuntu 14.04.3 hang during install in kvm under ubuntu 14.04.3"
date: 2015-11-07
forum: Virtualisation
---

### Post by andrey-mavlyanov on 2015-11-07
Hello good people!

Last Thursday I was trying to setup a couple of virtual machines on my Supermicro server with X10DRL-i chaises and Intel(R) Xeon(R) CPU E5-2609 v3 CPU.
```
aim@itis-lan-1:~$ cat /proc/cpuinfo | grep flags | uniq
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht t
m pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pc
lmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 fma cx16 xtpr pdcm pcid dca sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer
 xsave avx f16c rdrand lahf_lm abm arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep
bmi2 erms invpcid xsaveopt
```


I setup Ubuntu 14.04.3 with 3.19 kernel just fine, installed virtualisation packages (currently I have qemu-kvm 2.0.0+dfsg-2ubuntu1.19, libvirt-bin 1.2.2-0ubuntu13.1.14 and virtinst 0.600.4-3ubuntu2) and started to setup my first vm on it with the following command: 
```
virt-install --connect=qemu:///system \
             --name=test \
             --description="Tes" \
             --hvm \
             --cpu=host \
             --vcpus=2 \
             --ram=1024 \
             --memballoon virtio
             --disk path=/var/lib/libvirt/images/test.qcow2,format=qcow2,bus=virtio,size=80 \
             --cdrom=/home/User/Downloads/ubuntu-14.04.3-server-amd64.iso \
             --network=bridge=br0,model=virtio,mac=52:54:00:12:8f:32 \
             --boot=cdrom,hd,menu=on \
             --video=qxl \
             --graphics=vnc,password=SomeGoodPassword,listen=0.0.0.0 \
             --noautoconsole \
             --autostart

```


The installation process started, but hang on the "disk detection" fase (it's right after we choose time zone). I was curious what happend and ask colleague with linux on a desktop (I personally use mac) to connect via virtual-manager to my host and switch to console to check out logs. We found (unfortanutaly I don't have any screenshot right now) that kernel dumped at some sort of raid6 driver.

Lately I was trying to install Ubuntu 15.10, debian 8, Fedora 23 - they all hang at disk detection fase - I'm attaching the fedora screenshot below.

[ATTACH=CONFIG]265408[/ATTACH]

So, can you please help me to figure out my issue with the server?!

---

### Post by TheFu on 2015-11-07
I've never used virt-install. Does it create the qcow2 storage? I know that libvirt doesn't do that on 14.04.   QCOW2 storage has to be manually created with qemu-img. Some quick searches seem to confirm that the qcow2 storage needs to  be created before virt-install. virt-install can make other types of containers, just not qcow2.

BTW - did you manually create the bridge, br0.   Were bridge-utils installed?

RAID6?  Any idea about that? Doesn't make sense.

Lastly, try not using qxl.  vmvga or cirrus work easier....

My experience is with 14.04, nothing newer.

---

### Post by andrey-mavlyanov on 2015-11-08
Doh! Yes, I have the qcow2 storage, previously created br0 and etc.

I've digged some and found the same issue with the centos host: [https://www.centos.org/forums/viewtopic.php?t=48615](https://www.centos.org/forums/viewtopic.php?t=48615)

---

