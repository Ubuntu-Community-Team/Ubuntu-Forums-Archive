---
title: "XEN - Windows guess, power control from Windows"
date: 2019-06-06
forum: Virtualisation
---

### Post by jagie on 2019-06-06
Hi

I have setup XEN on a Laptop - and I am currently setting up a Windows guest.

Question is, what options do I have for enabling the laptop itself to shutdown/restart/sleep when the Windows guest does so?

I assuming PCI Passthrough of SMBus if it does work has the potential to cause more than a few issues.

Jamie

---

### Post by TheFu on 2019-06-08
I waited to respond. Hoped that someone with current Xen knowledge will respond.  I used Xen long ago, but never for anything like this.

You could script something over a network connection from the guestOS to ask the hostOS to shutdown and hope the guest finishes shutting down before the timeout wait time ends and the hostOS kills the guest VM.  I've never done this, but it should be possible.  High level idea ....
On Windows - ssh to the hostOS, run the **shutdown now** command
On Windows - run the **shutdown.exe** command
Train users to run that script instead of clicking the Windows shutdown button. The restart button will work as normal.

Guest VMs can be setup to autostart at boot, but if they have a GUI that cannot be accessed without the client-viewing programming running already. rdp connections would work from any machine on the LAN.
I run a Win7 VM on a headless KVM server (not Xen). It starts at boot.  To access Windows, I use an ssh tunnel that opens a SPICE display channel to the Windows VM from any computer on the same network. To me, it is just a doubt-click program. I've never accessed the VM from the physical computer running the hypervisor and VM.

SPICE only works with specific QXL drivers and with KVM-based hypervisors. I don't think it works with Xen or any other hypervisor.  With libvirt, it is the default and fairly easy AND extremely fast - not fast enough for video, but more than fast enough for business productivity applications.  It is even better than x2go, which I use over the internet for the same purposes.  

If you shutdown the laptop, all running processes, like Xen, are told to shutdown and given some time to accomplish that. 

KVM and Xen really aren't designed for laptops.  There are lots of network complications since the networking on the server isn't static with a laptop.

---

