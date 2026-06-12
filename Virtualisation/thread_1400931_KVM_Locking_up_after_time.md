---
title: "KVM Locking up after time"
date: 2010-02-07
forum: Virtualisation
---

### Post by slick666 on 2010-02-07
Dear forum members

I've started playing around with KVM. I created a VM of Ubuntu 64-bit On the VM I installed the Transmission daemon and added about 4 or 5 torrents.

The problem is when I start the VM everything is fin but after a few hours when I check back the VM is unresponsive to pings and it is pegging one of my CPUs. I have not idea where to start looking and what the problem could be. Is this a problem with the KVM with the VM itself? Any help would be appreciated.

---

### Post by slick666 on 2010-02-08
Bump Bump

Anyone seen this issue with KVM?

---

### Post by stephanhughson on 2010-02-12
It could be lots of things.

I recommend opening up two SSH sessions and leaving then running top and just waiting for it to happen, so you can see what was happening at the time.

Also, each of your virtual machines should have a VNC screen, depending on how you set it up.

If you are using libvirt, then try virsh vncdisplay XXXXXXX
where XXXXXXX is the name of your virtual machine.

If the KVM virtual machine is crashing, I would expect there to be something on the actual screen.

Other places to check are log files. That should get you started at least.

Hope that helps a bit.

---

### Post by lavinog on 2010-02-12
> **stephanhughson said:**
> 
Also, each of your virtual machines should have a VNC screen, depending on how you set it up.


I just read that kvm uses SDL and not vnc to display the screen.

@OP: what command line are you using to start the vm?

Do you have firefox running in the background?

htop is a little nicer than top.

---

