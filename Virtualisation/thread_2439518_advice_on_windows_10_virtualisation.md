---
title: "advice on windows 10 virtualisation"
date: 2020-03-28
forum: Virtualisation
---

### Post by kaky951357 on 2020-03-28
Hello people,
My laptop has 8gb of RAM (i plan to upgrade to 16gb) and an intel i7 8650U processor, my plan is to run a lightweight linux distro like lubuntu, and to use kvm to create virtual machines that i will use mainly for work (light use of Matlab  and Skype), i tried to run windows on kvm using VM-manager and i wasn't happy with the performance, the audio and the graphics was slow, the refresh rate on the vm was like 20FPS, even if i give it 6 cores of cpu and 6Gb of RAM. i heard that kvm was very  efficient on running virt machines.
My questions are : Is my computer powerful enough to allow me to do what i want ? what are your suggestions to run my windows vm as fast as possible?
PS : i'm a complete noob 
stay safe an have a nice day.

---

### Post by TheFu on 2020-03-29
There are lots of VM tuning settings, mainly around storage, networking and properly sharing limited resources.
if your primary goal for any guest VM is for high end GPU use, then you will almost always be disappointed using VMs w/o some sort of exclusive GPU passthru.

First, only provide 2 vCPUs to any guest at the most.  More isn't usually better. 1 vCPU is my initial default, but with Windows the OS will load a different kernel if there is only 1 vCPU, so 2 is probably the minimal. Changing the number of vCPUs later is easy. Just shutdown the VM, change the value, start up. For non-Windows VMs, start with 1 vCPU. Never exceed N-1 vCPUs in use with the total number of VMs running. Always leave at least 1 CPU for the hostOS to manage VMs and other hostOS stuff. Don't overcommit CPU or RAM resources.

Second, ensure the storage uses block devices like and LVM-LV would.  Don't use file-based storage back ends. The performance difference in this alone is huge if the storage is spinning rust.  SSD storage, it matters less.  Fully pre-allocated storage will be faster.

Third, use virtio for both the storage and network controllers to the guest VM.  Linux systems all support these controllers out of the box, but i don't know about Win10.  Win7 and earlier all required special drivers to be loaded inside the guest VM from Redhat to support virtio.

Fourth, for GPU performance, the best option is to use QXL and SPiCE.  i don't know how well this works on Win10. Virtual machines are about non-Graphical workloads.  Over the last 15 yrs, great improvements in this area of faster vGPUs, but that isn't exactly a high priority for enterprise servers, as you can imagine.  Amazon.com runs on KVM.  How much of that web server infrastructure even needs a GPU?  None.  Same for every huge website or DB server.  None of them need any GPU at all.  ZERO.

At the core, KVM/QEMU is the most efficient full hypervisor available for linux servers.  More and more often, linux processing is being loaded into "linux containers", which Windows cannot run inside. Today v4.0 of LXD was announced, the Canonical version of linux containers, but it doesn't help at all with Windows.

An article I wrote long ago about hypervisor performance: [https://blog.jdpfu.com/2012/07/30/improving-kvm-performance](https://blog.jdpfu.com/2012/07/30/improving-kvm-performance)
For storage performance, use LVM on SSDs, that's the easy answer, but you'll want to understand LVM to get the most from it.

---

### Post by siepo on 2020-04-01
I am running w10 with KVM on an ubuntu machine with 8GB RAM and an i3 processor. For storage, I use a qcow2 virtual disk, which is the default format. I have no complaints about performance, but I do just command-line stuff and very basic graphics.
I strongly recommend installing windows drivers from [https://www.spice-space.org/download.html#windows-binaries](https://www.spice-space.org/download.html#windows-binaries) .

---

