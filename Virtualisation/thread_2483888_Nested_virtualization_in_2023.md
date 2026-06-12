---
title: "Nested virtualization in 2023"
date: 2023-02-12
forum: Virtualisation
---

### Post by frsy on 2023-02-12
Does anybody succedeed to run some latest ubuntu versions in nested virtualization way recently?

I try on an hp proliant gen10 with xen base and on my laptop (for testing purpose) with virtualbox 7 over windows 11 (both platform run on Intel CPU). The result is the same on both platform :
- Virtualized Host Ubuntu 18.04 -> Guest Ubuntu 20.04 and 22.04 : Guest doesn't start and CPU is 100% busy
- Virtualized Host Ubuntu 20.04 -> Guest Ubuntu 20.04 and 22.04 : Host crash, litterally
- Virtualized Host Ubuntu 22.04 -> Guest Ubuntu 20.04 and 22.04 : Guest doesn't start and CPU is running 10-12%

Each test has been perform with an up to date version of ubuntu.
I check configuration and it should be ok : vmx flags ok in Host, kvm-ok is happy, virt-host-validate does not complain. kvm and kvm_intel module are well loaded.
The worst part : I don't have any log to provide... qemu start and nothing... No log, no qemu crash. I try to to force qemu to write log with -D flag, but nothing in the file.

I launched kvm-stat but I don't have the knowledge to understand the output.

I can provide log, trace, anything which could make it functionnal

---

### Post by MAFoElffen on 2023-02-12
I do nested virt's in KVM all the time... Note KVM, not Xen.

From my /etc/default/grub file:
```

GRUB_CMDLINE_LINUX_DEFAULT="-- splash [COLOR=#ff0000]kvm-intel.nested=1[/COLOR] intel_idle.max_cstate=4 video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid"

```
Note that mine is Ubuntu Server 22.04.1, KVM version 6.2.0, libvirtd version 8.0.0, VM Guest Windows Server 2k22 w/ Hyper-V, Nested VM's of Windows 11...

Alternately, you could create file /etc/modprobe.d/kvm.conf and add this line:
```

options kvm_intel nested=1

```
If your computer has AMD CPU, just substitute 'amd' for 'intel'

---

### Post by DuckHook on 2023-02-12
> **MAFoElffen said:**
> I do nested virt's in KVM all the time...
That is so cool. I've heard about it but never tried it. Thanks for the detailed instructions.

How is performance? And, if you don't mind my asking, what do you use it for?

---

### Post by MAFoElffen on 2023-02-13
Besides doing Dev Testing for Ubuntu Desktop and Server... I do Insider Preview Testing for Windows Server and Desktop, as well as Beta Testing for VMware vSphere and vCenter.

It's easiest for me to do all that within KVM VM's. In KVM, I can replicate hardware platforms, and run nested KVM within KVM, Windows Hyper-V within KVM, and Nested vSphere within KVM... as well as run many, many VM Distro's.

When I test my own scripts, such as my UbuntuForums 'system-info' script, we want ensure it runs on various hardware (intel/amd, aarm64, MAC, Linux on IBM360, etc), platforms and various Distro's. With KVM you have the ability to do all that and more.

With support, it's easy to try to replicate a problem, take snapshots, then verify that what you suggest actually works... Or see the results of what you want to do, before you do it on live systems.

Yes. I am pretty sold on KVM as a VM Host. It is very flexible.

---

### Post by frsy on 2023-02-14
Thanks for your answers.

Unfortunatly, on my side, things are not so easy.
Could you tell me what kind of CPU you have? Do you also use gpus?
I will try to deploy a nested kvm (instead of xen/vbox nested) to see if the support IS better.

@Duckhook : on my side, I would like to use nested VMs to manage my openstack deployment. With that, you can deploy smoothly compute or controller node easily and keep performance decent.

EDIT : I confirm, kvm in kvm works really well where virtualbox/xen nested virtualization support is not.
I will keep this solution. Thanks a lot

---

### Post by MAFoElffen on 2023-02-14
KVM added Nested virtualization as a feature in 02/18. I started using it since Ubuntu 20.04 LTS. XEN started supporting nested virtualization in version 4.4 ([https://wiki.xenproject.org/wiki/Nested_Virtualization_in_Xen](https://wiki.xenproject.org/wiki/Nested_Virtualization_in_Xen))

i am using it personally on CPU's AMD Opteron 6420 SE, icore i7-2760Q  and icore i9-10900.

To check if your CPU supports KVM nested virtualization, if Intel do
```

grep . /sys/module/kvm_intel/parameters/nested

```
or else if AMD, do
```

grep . /sys/module/kvm_amd/parameters/nested

```
In AARCH64, nested virtualization was added at ARM8.3. Raspberry Pi4 and Pi 400 supports KVM nested virtualization. I have done KVM nested virtualization on Raspberry Pi4 since since Ubuntu 20.04 LTS.

---

### Post by DuckHook on 2023-02-14
Thank you both for your use cases. Once explained its usefulness for testing is clear. It never occurred to me that it would also be needed in a cloud computing environment, but I see that now.

Learn something new every day.

---

