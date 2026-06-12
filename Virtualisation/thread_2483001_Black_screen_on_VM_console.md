---
title: "Black screen on VM console"
date: 2023-01-17
forum: Virtualisation
---

### Post by klaus-burgundia on 2023-01-17
Hi all :)

I have read a lot about using Ubuntu in VMs and I have a lot of them working on my Microsoft Hyper-V servers.

Because I want to do some training with Tensorflow in Ubuntu, I have added a Geforce 3060 in a Windows server 2019, and using Windows 10 in a VM - it works flawlessly.I can even use the graphics card as an extended desktop.

However, if I install Ubuntu (any version) in a VM, I can get Ubuntu to use the Geforce and it does display an output on the physical graphics card. However, the normal Hyper-V console is black. Also, Xrandr reports that no other display adapter is present but the Geforce - despite the Ubuntu console having loaded using the console. This means that it's impossible to use the VM, except through SSH.

So how does one make Ubuntu see the console again? If I remove "quiet splash" from the grub configuration file, I even have the console text still showing, while the Geforce shows the console loading text.

---

### Post by TheFu on 2023-01-17
Virtual machines need exclusive access to any hardware that is passed through  using VT-d and IOMMU.  This means that 2 GPUs have to be installed in the system.  Most people would assign the iGPU from an intel CPU to their hostOS and assign the better GPU to the VM with the PCIe passthru setup.

If you can, change the thread title to include "Hyper-V" and put this thread into the Virtualization sub-forum to get the experts there to look at it.  A moderator probably has to move the thread.

I've never setup GPU passthru to a VM.  Others here have. Hopefully, they will post.

I'm unfamiliar with hyper-v, but in other hypervisors, the fake GPU  hardware gets provided to the VM.  Cirrus, VGAVM, Virtio, QXL, ... let me look  ... with a specific protocol to enable communications between the host system and the guest.  I use Spice. [https://www.linux-kvm.org/page/SPICE](https://www.linux-kvm.org/page/SPICE)  This is a Linux thing. I don't know what MSFT uses, if anything.  

With other hypervisors, the 2D and 3D acceleration options are available - VirtualBox does these nicely in recent releases.  Ubuntu desktops can support virtio GPU drivers for efficient graphics for normal productivity applications.  This usually isn't sufficient for gaming uses ... and sometimes isn't sufficient for CAD programs.  For those, true GPU passthru is required.  Most active users here that do passthru would have Linux as the hostOS and run Windows inside a VM - mainly for gaming.  There are lots and lots of guides for how to accomplish that for most hypervisors.  The 3060 should be a high enough GPU for that to work.  I know my 1030 doesn't.  Nobody tries to get an $80 GPU to support passthru.  I vaguely remember nvidia required signing up to get needed drivers at some point.  Perhaps my memory is wrong.

For non-experts, only 1 hypervisor can be installed at a time. Beware.

---

### Post by klaus-burgundia on 2023-01-17
Hi TheFu, thank you for your answer. I have no issues in Windows 10 (in a VM) working with the hyper-v console window, and if the physical GPU is removed from the Ubuntu VM - the console is once again used.

I don't need fancy graphics to work in the Hyper-V console, just normal configuration stuff etc.

Since Windows 10 is able to do it flawlessly in a VM, I reckon it's not a hardware setting/limitation of any kind.

---

### Post by TheFu on 2023-01-17
> **klaus-burgundia said:**
> Hi TheFu, thank you for your answer. I have no issues in Windows 10 (in a VM) working with the hyper-v console window, and if the physical GPU is removed from the Ubuntu VM - the console is once again used.

I don't need fancy graphics to work in the Hyper-V console, just normal configuration stuff etc.

Since Windows 10 is able to do it flawlessly in a VM, I reckon it's not a hardware setting/limitation of any kind.

Google found this: [https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/plan/plan-for-deploying-devices-using-discrete-device-assignment](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/plan/plan-for-deploying-devices-using-discrete-device-assignment)

Do you expect graphics that work in MS-Windows to work in any other OS?  
Maybe if you list the available fake GPUs that can be provided to a guest VM, I can suggest something that will work?

Also, which release and DE is being used for Ubuntu?  Is it Wayland or X11?  here's what my desktop reports, running inside a VM:
```
$ inxi -G
Graphics:  Device-1: Red Hat QXL paravirtual graphic card driver: qxl v: kernel 
           Display: server: X.Org 1.20.8 driver: none unloaded: fbdev,modesetting,vesa 
           resolution: 1920x1200~77Hz 
           OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.2.6 

```
So, it is using the QXL driver and X11.  Wayland breaks some of my long-time workflows.  Eventually, perhaps in 5-10 yrs, it will work great, but for now I will keep using X11.  It runs great.  I'm using KVM/QEMU as the hypervisor.  Odd how when the host and guest systems are running software from the same company, things "just work".  The hostOS isn't using the the proprietary GPU drivers for the GPU on that system.  I need a newer kernel for that to work.  About 2 weeks ago, I swapped in a new APU and haven't gotten around to moving to a newer kernel release with the desired support.  Pulled an nvidia GPU out of the system.

My last remaining MS-Windows VM  uses QXL as the video driver.  Had to install that driver package separateky under MS-Windows, since it wasn't included.  Foreign OSes are like that. I don't expect things to work the same between different OSes.

---

### Post by MAFoElffen on 2023-01-17
With Hyper-V, you have limited choices that are geared/favored for their own OS Guests. Remember that Microsoft feels that is is the only OS, and feels it should be. Options are still favored in a vacuum.

What Hyper-V refers to as RemoteFX (Virtual GPU sharing), is a GPU pass-through that takes exclusive control over the (assigned) GPU for exclusive use by VM's. That is how that works. That is fairly common with Hyper-V, VMware, and how KVM mainly works.  KVM now also has VirtGL as an option, which can share extended capabilities of the GPU for OpenGL, while still providing service to the host... But that is just for OpenGL extended capabilities.

Yes, as expected, if I turn on RemoteFX in Windows Hyper-V, I lose the ability to use that specific GPU for the host.
[https://www.nakivo.com/blog/how-to-deploy-graphics-devices-using-remotefx-vgpu/](https://www.nakivo.com/blog/how-to-deploy-graphics-devices-using-remotefx-vgpu/)

---

### Post by QIII on 2023-01-17
Thread moved to Virtualisation as a more appropriate sub-forum.

---

### Post by klaus-burgundia on 2023-01-18
> **TheFu said:**
> Google found this: [https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/plan/plan-for-deploying-devices-using-discrete-device-assignment](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/plan/plan-for-deploying-devices-using-discrete-device-assignment)

Do you expect graphics that work in MS-Windows to work in any other OS?  

It's not just Microsoft, the exact same problem occurs with Proxmox: [URL="https://forum.proxmox.com/threads/new-proxmox-7-install-ubuntu-20-04-pci-passthrough-black-screen.92708/"]https://forum.proxmox.com/threads/new-proxmox-7-install-ubuntu-20-04-pci-passthrough-black-screen.92708/

[/URL]There are no fake GPUs being listed. Xrandr in Ubuntu reveals just the Geforce adapter, and the ports on the GPU - including the socket being used by the monitor.

I do know about RemoteFX - tried it a while back, and noticed that both Photoshop and Firefox had a lot of issues - so stopped there. Today, I need to train AI with Tensorflow on Ubuntu. And anyone having tried to install an Ubuntu 17 or older, know the struggle of installing/updating from scratch, with an outdated OS. A working VM can be imported on any new hypervisor from Microsoft, thus a perfect solution for a future with changing servers. And the console is even working, until the part where the loading logo/text ends and the user account screen is loading.

---

### Post by MAFoElffen on 2023-01-18
Okay...

TensorFlow installed on VM Ubuntu Lunar Lobster 23.04 alpha w/ Linux Kernel 6.2.0-rc3
```

>>> print(vtf.__version__)
2.11.0
>>> exit()
(vultr-tensorflow) mafoelffen@lunar-lander-007:~/tensorflow_files$ uname -r
6.2.0-060200rc3-generic
(vultr-tensorflow) mafoelffen@lunar-lander-007:~/tensorflow_files$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Lunar Lobster (development branch)
Release:    23.04
Codename:    lunar
(vultr-tensorflow) mafoelffen@lunar-lander-007:~/tensorflow_files$ 

```
TensorFlow installed on Live (on metal) Ubuntu Jammy Jellyfish 22.04 LTS
```

>>> print(vtf.__version__)
2.11.0
>>> exit()
(vultr-tensorflow) mafoelffen@Mikes-ThinkPad-T520:~/tensorflow_files$ lsb_release -a
LSB Version:    core-11.1.0ubuntu4-noarch:printing-11.1.0ubuntu4-noarch:security-11.1.0ubuntu4-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:    22.04
Codename:    jammy
(vultr-tensorflow) mafoelffen@Mikes-ThinkPad-T520:~/tensorflow_files$ uname -r
5.15.0-57-generic

```

There is no reason to install TensorFlow on an outdated, unsupported version of Ubuntu: [https://www.vultr.com/docs/how-to-install-tensorflow-on-ubuntu-22-04/](https://www.vultr.com/docs/how-to-install-tensorflow-on-ubuntu-22-04/)

On the first install above, I installed it during my dev tests today, on a daily build. During test on calc's while running TensorFlow, It could not find the NVidia Cuda drivers, because I didn't have any NVidia GPU on that VM Host...

On the second install above, I installed it on metal on my Ubuntu Laptop with NVidia. It still had errors not finding the NVidia Cuda drivers, as, even though I have NVidia GPU on that machine, I do not have the NVidia Cudu Drivers installed on it...

So no, you do not need to load an old outdated version of Ubuntu, but yes, you need to passthorugh the NVdia GPU, for you to be able to load the NVidia Cuda Drivers. And yes, you are going to lose use of that GPU from the host, during that VM instance running...

---

### Post by klaus-burgundia on 2023-01-18
> **MAFoElffen said:**
> orFlow on an outdated, unsupported version of Ubuntu: [https://www.vultr.com/docs/how-to-install-tensorflow-on-ubuntu-22-04/](https://www.vultr.com/docs/how-to-install-tensorflow-on-ubuntu-22-04/)



Unfortunately, Coqui only trains on Tensorflow 1.15.5 - and the only Python version, which seems to make needed components work, is 3.8. Ubuntu 20.x has that version installed.

I have tried installing the latest Ubunti, the latest Debian etc., and it did not make the Hyper-V console work.

---

### Post by MAFoElffen on 2023-01-19
TensorFlow seems to be very, very picky about which Cuda version is installed...

---

### Post by klaus-burgundia on 2023-01-20
> **MAFoElffen said:**
> TensorFlow seems to be very, very picky about which Cuda version is installed...

Exactly. And replicating the needed outdated enviroment is a nightmare, borderlining the impossible - thus why virtualization is great, when you can save/export the VM.

---

### Post by MAFoElffen on 2023-01-20
From [https://mathiashueber.com/pci-passthrough-ubuntu-2004-virtual-machine/](https://mathiashueber.com/pci-passthrough-ubuntu-2004-virtual-machine/)
> PCI devices are organized in so called IOMMU groups. In order to pass a device over to the virtual machine, we have to pass all the devices of the same IOMMU group as well. In a prefect world each device has its own IOMMU group &#8212; unfortunately that&#8217;s not the case.

Passed through devices are isolated, and thus no longer available to the host system. Furthermore, it is only possible to isolate all devices of one IOMMU group at the same time.

This means, even when not used in the VM, a device can no longer be used on the host, when it is an &#8220;IOMMU group sibling&#8221; of a passed through device. 
Like we said, if you are going to do GPU passthrough, you are going t need another GPU for the Host Console, unless you do like me (when I did that), the host console as via SSH to that specific server... Or I connected a CGA cable to integral Matrox GPU of that server...

Note later on:
> 
    Attention!

    After the upcoming steps, the guest GPU will be ignored by the host OS. You have to have a second GPU for the host OS now!

It works the same for Windows RemoteFX

---

