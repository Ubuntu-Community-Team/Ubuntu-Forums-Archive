---
title: "Anyone try running BOTH vmware and virtualbox at the same time?"
date: 2009-10-08
forum: Virtualisation
---

### Post by maxxjr on 2009-10-08
Has anyone tried running VMware player or workstation plus Virtualbox on the same PC at the same time?

---

### Post by falconindy on 2009-10-08
Why not run 2 OS's off the same software? Either way, just make sure your rig is up to the challenge. You'll need ample memory (4gb+) and CPU (4-core ideally) to handle the task.

A few weeks back, I accidentally ran my WinXP and Karmic VMs at the same time... let's just say that my computer was probably thinking the apocalypse was near (specs in sig).

---

### Post by maxxjr on 2009-10-08
> **falconindy said:**
> Why not run 2 OS's off the same software? Either way, just make sure your rig is up to the challenge. You'll need ample memory (4gb+) and CPU (4-core ideally) to handle the task.

A few weeks back, I accidentally ran my WinXP and Karmic VMs at the same time... let's just say that my computer was probably thinking the apocalypse was near (specs in sig).

VirtualBox 3.x had a bug with IO APIC on AMD processors when I was trying to decide whether to use VirtualBox or upgrade an old copy of VMware workstation.  This bug made both guest and host OS crawl with multiple virtual CPUs.  At the time, I decided just to start with the demo of VMware workstation.  I have a couple of VMware workstation VM's that are complete in terms of the apps I want running on them.  The demo license expired, but I am still able to run the VMs with VMware player.

VirtualBox has since corrected the bug, so if I want to create a new VM, I can start using VirtualBox.  I am wondering about conflicts if I run VirtualBox and vmware player at the same time.  (I should have the CPU cores and RAM so that there should be no resource issues)

I know there is some ability to import vmware VMs into VirtualBox, but 1) I wonder about Windows Activation issues (my copy is legit, but I have played around installing it enough times that I have to call Microsoft anytime I start over again), and 2) I have a if it ain't broke, don't fix it mentality...if it runs fine with VMware player, don't waste time trying to either port to or start over with VirtualBox.

Thanks!

---

### Post by Perryg on 2009-10-10
This is from the VirtualBox Users guide.  

Warning
Do not run other hypervisors (open-source or commercial virtualization products) together with VirtualBox! While several hypervisors can normally be installed in parallel, do not attempt to run several virtual machines from competing hypervisors at the same time. VirtualBox cannot track what another hypervisor is currently attempting to do on the same host, and especially if several products attempt to use hardware virtualization features such as VT-x, this can crash the entire host.

---

