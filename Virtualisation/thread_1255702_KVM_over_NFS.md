---
title: "KVM over NFS"
date: 2009-09-01
forum: Virtualisation
---

### Post by nkushman on 2009-09-01
Is used KVM over NFS a supported model?
ie. can I run a guest whose hard disk exists on a mounted NFS drive?

I've build an Ubuntu-8.04 guest running with an Ubuntu-9.04 host, and it works fine if I run it locally (i.e. the virtual hard drive exists on a physically attached hard drive), but if I move the virtual hard drive to an NFS partition, then then exact same guest starts to boot and then seems to crash just after it loads the swap partition and checks the root file system (ie. the console says it's loading swap, and checking the root file system and then the guest shuts itself down).  I've tried with both raw disks, and qcow disks.  Is this a supported configuration? Any idea what I might be doing wrong?

Other random aspects of my configuration that may or may not be relevant:
- I'm running Ubuntu-desktop edition for both guest and host
- nfs mounts flags are:  tcp,rsize=32768,wsize=32768
- I installed the guest using virt-manager and an iso (I didn't use vm-builder) and haven't modified the configuration in any meaningful way from the virt-manager defaults
- host and guest are 64-bit

Any help or suggests are greatly appreciated.  I've googled this to death, and I can't find much discussion of it.  Is nobody running KVM with shared storage?  Is NFS a supposed configuration as opposed to some kind of SAN setup?

Thanks much.

-Nate

---

### Post by nkushman on 2009-09-01
So I figured out the problem.

I needed to remove the
<apic>
<pae>

flags in my vm configuration and then it booted fine when the disk was on the nfs partition.

-Nate

---

