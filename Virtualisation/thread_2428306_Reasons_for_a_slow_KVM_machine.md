---
title: "Reasons for a slow KVM machine?"
date: 2019-10-02
forum: Virtualisation
---

### Post by Tadaen_Sylvermane on 2019-10-02
I'm trying to work out something involving my 18.04 upgrade. I thought I had succeeded, but alas one problem remains for full upgrade. I normally use LXD containers to test things but LTSP can't seem to easily create what it needs in a container so I'm using a full vm via kvm.

This thing is slow. It has 2 cores of my i5, 2gb of ram. Even idling it is dead dog slow. I can type a command over ssh or through virt-manager and I can count a couple seconds before it responds. On the host everything is damn near instant.

I've double checked everything for virtualization is enabled in the bios. It is running on a spinning hard drive admittedly, but would that make that big a difference in running a simple ls command? It works, and I can use it but I'm curious as to why it is so so slow to use. My hardware isn't exactly a high powered machine, but this is just sad to be honest. Worse yet, in virt-manager it shows the cpu barely being used. Is this just lack of ssd? Have I just gotten so used to ssd's and this is what a computer used to feel like on a spinner?

---

### Post by TheFu on 2019-10-02
Simple things.

Always use virtio drivers for networking and disk controllers.
Preallocate the storage if you are using file-based storage.  LVM backed storage is native performance, IME.
Use only 1 vCPU, unless you are doing something heavy.  My desktop is a VM with 4G and 1 vCPU. Most of my servers have 1 vCPU, except a pretty heavy communications server which gets 2 vCPUs.
Leave 1 GB RAM on the HostOS for managing everything.

Don't use virt-manager unless you need a console. Always use either ssh or **any** other virtual desktop solution, though SPICE/QXL from vinagre clients is pretty good too.  From Windows clients, I use x2go. Same if I'm going over the internet.

The hostOS needs to be good at sharing system resources.  Doing heavy processes on the host will slow down all guest machines.

---

### Post by Tadaen_Sylvermane on 2019-10-03
Using defaults in Virt-Manager which is virtio. Hard drive was not LVM, ssd is. Using a single cpu now on a fresh vm with 1gb of ram. Using ssh only. Virt-Manager is just for creation / installing ssh of / to the vm. No need for graphics.

I didn't realize I had 50-60gigs of my ssd unclaimed by lvm. Created a volume and mounted, added as location for running vms via virt-manager. VM runs great now. Just like the host. Not sure if all you said+ssd, just ssd, or the lvm change... but it's almost native speed now like I'm used to.

The single vcpu is even managing to create my ltsp squashfs image in a reasonable time frame. Not baremetal quad, but acceptable.

---

### Post by TheFu on 2019-10-03
Sharing resources is critical.  Reducing context switching matters too.  That's why high-performance VM setups pin specific VMs to specific CPUs.

SSD will help drastically, but so does getting away from file-based storage like vdi/vdkm/qcow2. If you pre-allocate a fixed size for the VM storage, that works for HDD storage performance.  On an SSD, you can use vdi/qcow2 or whatever. Doubt it would matter since an x4 SSD performs so fast.  

LVM provides block storage to the VM.  That removes another layer from the storage between the VM so reading/writing the bytes on the media is faster.

---

