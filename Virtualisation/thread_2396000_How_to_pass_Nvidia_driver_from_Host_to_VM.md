---
title: "How to pass Nvidia driver from Host to VM"
date: 2018-07-09
forum: Virtualisation
---

### Post by satimis on 2018-07-09
Hi all,

Host - Ubuntu 16.04 desktop
VM - Ubuntu 18.04 desktop
Oracle VirtualBox

I'm following below article to install Tensorflow on Ubuntu 18.04 VM;
Ubuntu-18.04 Install Nvidia driver and CUDA and CUDNN and build Tensorflow for gpu
[https://github.com/nathtest/Tutorial-Ubuntu-18.04-Install-Nvidia-driver-and-CUDA-and-CUDNN-and-build-Tensorflow-for-gpu](https://github.com/nathtest/Tutorial-Ubuntu-18.04-Install-Nvidia-driver-and-CUDA-and-CUDNN-and-build-Tensorflow-for-gpu)

but unable to pass the Nvidia driver from Host.

Is there a solution?  If without solution then I'm compelled to download the pre-built "deep learning + Python Ubuntu virtual machine".

Thanks

Regards
satimis

---

### Post by deadflowr on 2018-07-09
Not easily.
Virtualbox does have a very experimental feature for pci passthrough, which can pass the gpu over.
But it takes a few steps to get there.
See: [https://askubuntu.com/questions/202926/how-to-use-nvidia-geforce-m310-on-ubuntu-12-10-running-as-guest-in-virtualbox]("https://askubuntu.com/questions/202926/how-to-use-nvidia-geforce-m310-on-ubuntu-12-10-running-as-guest-in-virtualbox")
as an example.

---

### Post by satimis on 2018-07-10
> **deadflowr said:**
> Not easily.
Virtualbox does have a very experimental feature for pci passthrough, which can pass the gpu over.
But it takes a few steps to get there.
See: [https://askubuntu.com/questions/202926/how-to-use-nvidia-geforce-m310-on-ubuntu-12-10-running-as-guest-in-virtualbox]("https://askubuntu.com/questions/202926/how-to-use-nvidia-geforce-m310-on-ubuntu-12-10-running-as-guest-in-virtualbox")
as an example.
Hi,

Thanks for your link

Also I found;
Ubuntu 18.04 LTS : KVM : GPU Passthrough : Server World
KVM : GPU Passthrough
[https://www.server-world.info/en/note?os=Ubuntu_18.04&p=kvm&f=11](https://www.server-world.info/en/note?os=Ubuntu_18.04&p=kvm&f=11)

I have KVM machine here.  I'll try and come back afterwards

Regards
satimis

---

### Post by satimis on 2018-07-12
Hi deadflowr,

Tried your link but failed because AMD-v is NOT on BIOS

Also tried;
KVM : GPU Passthrough
[https://www.server-world.info/en/note?os=Ubuntu_18.04&p=kvm&f=11](https://www.server-world.info/en/note?os=Ubuntu_18.04&p=kvm&f=11)

Enabled "IOMMU" on BIOS

# nano /etc/default/grub
line 12:
change;
GRUB_CMDLINE_LINUX=""
to;
GRUB_CMDLINE_LINUX="amd_iommu=on"

# grub-mkconfig -o /boot/grub/grub.cfg```

Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.13.0-45-generic
Found initrd image: /boot/initrd.img-4.13.0-45-generic
Found linux image: /boot/vmlinuz-4.13.0-41-generic
Found initrd image: /boot/initrd.img-4.13.0-41-generic
Found linux image: /boot/vmlinuz-4.10.0-37-generic
Found initrd image: /boot/initrd.img-4.10.0-37-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Ubuntu 16.04.4 LTS (16.04) on /dev/sda1
done

```

Also failed

Regards
satimis

---

### Post by deadflowr on 2018-07-12
> Tried your link but failed because AMD-v is NOT on BIOS
What's the machine?

Also:
I do not see what failed about grub reloading?
Looks normal to me.
The warning message is just that, a warning message. And does not constitute an error or a failure.

---

### Post by kevin160 on 2018-07-12
I haven't tried with Virtualbox, but GPU passthrough is pretty easy with KVM.  Don't freak out that AMD-v isn't listed in your BIOS.  Check from the OS by 'cat /proc/cpuinfo' and seeing if you have "svm" listed.  Nvidia wants you to buy their "server" class cards, so you may need to jump through some hoops to make a pass-through GeForce card work with Nvidia CUDA drivers, including silly fakery like <hyperv><vendor_id state='on' value='1234567890ab'/></hyperv> and <kvm><hidden state='on'/></kvm> in your libvirt XML file.  
If you haven't tried playing with TensorFlow et al in the past, be aware that it will probably use more power than you have ever used gaming on a GPU.  I gamed 3 nights a week for a couple years on a machine with no problems.  hashcat ran without issues as well.   But whenever I ran the tensorflow benchmark it locked up completely.  As you will find in the forums, a beefier power supply is usually the solution.  It was for me.

---

### Post by satimis on 2018-07-12
> **deadflowr said:**
> What's the machine?

Also:
I do not see what failed about grub reloading?
Looks normal to me.
The warning message is just that, a warning message. And does not constitute an error or a failure.
AMD PC

On running following command
# grub-mkconfig -o /boot/grub/grub.cfg```

Code:
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.13.0-45-generic
Found initrd image: /boot/initrd.img-4.13.0-45-generic
Found linux image: /boot/vmlinuz-4.13.0-41-generic
Found initrd image: /boot/initrd.img-4.13.0-41-generic
Found linux image: /boot/vmlinuz-4.10.0-37-generic
Found initrd image: /boot/initrd.img-4.10.0-37-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Ubuntu 16.04.4 LTS (16.04) on /dev/sda1
done

```

Compared to the article of the link

root@dlp:~# grub-mkconfig -o /boot/grub/grub.cfg```
 
# show PCI identification number and [vendor-ID:device-ID] of Graphic card
# PCI number &#8658; it matchs [03:00.*] below, vendor-ID:device-ID &#8658; it matchs [10de:***] below

```

```

PCI Number => it matchs [03:00.*]

```

I need its number to create a new VM

According to the article
[2]	It's OK all. Create a new VM with GPU.
For [--host-device], specify GPU, and for [--machine], specify [q35], for [--features], specify [kvm_hidden=on].```

......
......
--host-device 03:00.0 \

```

Regards
satimis

---

### Post by deadflowr on 2018-07-12
It's a different command
this
```
root@dlp:~# vi /etc/default/grub
# line 12: add (if AMD CPU, add [amd_iommu=on])
GRUB_CMDLINE_LINUX="intel_iommu=on"
root@dlp:~# grub-mkconfig -o /boot/grub/grub.cfg
```
is one set of instructions, and this
```
# show PCI identification number and [vendor-ID:device-ID] of Graphic card
# PCI number &#8658; it matchs [03:00.*] below, vendor-ID:device-ID &#8658; it matchs [10de:***] below
root@dlp:~# lspci -nn | grep -i nvidia 
03:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP106 [GeForce GTX 1060 6GB] [10de:1c03] (rev a1)
03:00.1 Audio device [0403]: NVIDIA Corporation GP106 High Definition Audio Controller [10de:10f1] (rev a1)
root@dlp:~# vi /etc/modprobe.d/vfio.conf
```
is an entirely different set.
Unrelated to one another beyond the need for you to have the setup done in the forst, in order to utilize the next, and then the next set of command after it.

The grub-mkconfig command is update-grub and I have never seen update-grub ever output anything about any GPU or PCI information.
It should and does only show the listings for available kernels and other operating systems you can boot into.

The PCI info comes from the lspci command.
Which you run after setting up iommu in the grub config /etc/default/grub file.

---

### Post by satimis on 2018-07-12
> **kevin160 said:**
> I haven't tried with Virtualbox, but GPU passthrough is pretty easy with KVM.  Don't freak out that AMD-v isn't listed in your BIOS.  Check from the OS by 'cat /proc/cpuinfo' and seeing if you have "svm" listed.  
Thanks for your advice.

Whether follow below link on KVM ?
How to use NVIDIA GeForce M310 on Ubuntu 12.10 running as guest in VirtualBox?
[https://askubuntu.com/questions/202926/how-to-use-nvidia-geforce-m310-on-ubuntu-12-10-running-as-guest-in-virtualbox](https://askubuntu.com/questions/202926/how-to-use-nvidia-geforce-m310-on-ubuntu-12-10-running-as-guest-in-virtualbox)

On KVM box

&#10219; cat /proc/cpuinfo | grep svm```

flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb cpb hw_pstate retpoline retpoline_amd rsb_ctxsw ssbd ls_cfg_ssbd vmmcall bmi1 arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb cpb hw_pstate retpoline retpoline_amd rsb_ctxsw ssbd ls_cfg_ssbd vmmcall bmi1 arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
flags 
.....

```

A big file

> 
Nvidia wants you to buy their "server" class cards, so you may need to jump through some hoops to make a pass-through GeForce card work with Nvidia CUDA drivers, including silly fakery like <hyperv><vendor_id state='on' value='1234567890ab'/></hyperv> and <kvm><hidden state='on'/></kvm> in your libvirt XML file.  


Please explain in more detail.  Thanks

> 
If you haven't tried playing with TensorFlow et al in the past, be aware that it will probably use more power than you have ever used gaming on a GPU.  I gamed 3 nights a week for a couple years on a machine with no problems.  hashcat ran without issues as well.   But whenever I ran the tensorflow benchmark it locked up completely.  As you will find in the forums, a beefier power supply is usually the solution.  It was for me.
My PC -
AMD - 8-cores
RAM onboard - 32G

I suppose I can run Tensorflow on it?

You meant following article on this forum?
View Full Version : [SOLVED] Uninterruptible Power Supply - Soft shutdown with an auto boot
[https://ubuntuforums.org/archive/index.php/t-1633984.html](https://ubuntuforums.org/archive/index.php/t-1633984.html)

Regards
satimis

---

### Post by satimis on 2018-07-13
Hi deadflowr,

Tried again

# nano /etc/default/grub```
 
# line 12:
GRUB_CMDLINE_LINUX="amd_iommu=on"

```

# lspci -nn | grep -i nvidia```

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK208 [GeForce GT 730] [10de:1287] (rev a1)
01:00.1 Audio device [0403]: NVIDIA Corporation GK208 HDMI/DP Audio Controller [10de:0e0f] (rev a1)

```

# echo 'vfio-pci' > /etc/modules-load.d/vfio-pci.conf
# reboot

After reboot
# dmesg | grep -E "DMAR|IOMMU"```
 
[    0.000000] AGP: Please enable the IOMMU option in the BIOS setup
[    1.237642] AMD-Vi: Found IOMMU at 0000:00:00.2 cap 0x40

```

I have already enabled "IOMMU" on BIOS?  

Continue
# dmesg | grep -i vfio```

[    8.941466] VFIO - User Level meta-driver version: 0.3
]/code]

Regarding the 2nd sets of command;
Create a new VM with GPU.
[code]
root@dlp:~# virt-install \
--name ubuntu1804 \
....

```

The Host is Ubuntu16.04.  Whether change the command as```

--name ubuntu1604 \

```
?
and still I need to install ubuntu16.04 on the guest later?

Or keep it as original and install Ubuntu18.04 on the guest later?

Thanks

Regards
satimis

---

### Post by satimis on 2018-07-13
Hi all.

I download the pre-built VM of Tensorflow on Debian;
bitnami-tensorflowserving-1.8.0-0-linux-debian-9-x86_64.ova

from;

BITNAMI TENSORFLOW SERVING STACK VIRTUAL MACHINES
[https://bitnami.com/stack/tensorflowserving/virtual-machine](https://bitnami.com/stack/tensorflowserving/virtual-machine)

and import it to VirtualBox

Now it is working.

I suppose Debian is a server version.  I couldn't start GUI

I'm still interested to install Tensorflow by myself

Regards
satimis

---

