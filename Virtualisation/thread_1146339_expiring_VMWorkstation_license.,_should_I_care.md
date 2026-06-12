---
title: "expiring VMWorkstation license., should I care?"
date: 2009-05-02
forum: Virtualisation
---

### Post by jdrodrig on 2009-05-02
Hi,

I have been trying VMWare workstation for a few days and the trial license is expiring tomorrow I think. Besides not being able to create new machines is there a penalty for just staying with VMWare Player?

I mean, is there any performance difference? 

I got atracted to VMware instead of VBox for its ability of assigning two cores to the VMachines; where VBox does not offer that functionality right?

---

### Post by PilotJLR on 2009-05-02
Player can't create VM's, can't do snapshots... basically, it can ONLY run a VM, though the performance would be the same as with Workstation.

Most VM's don't actually need vSMP; unless you want to purchase Workstation, I would move over to VBox.

---

### Post by jdrodrig on 2009-05-03
Thanks for the reply.

I am kind of interested in having SMP; I usually use one machine at a time, either the host or the VM in full screen so having the two cores passed to the VM is kind of crucial to me (otherwise, it would be kind of awaste of CPU)...

I am leaning toward moving to VMPlayer until Vbox support SMP...any idea when that would be?

---

### Post by HermanAB on 2009-05-04
Howdy,

There are actually online web sites that can be used to create a VM for use with VMware Player.  You can also  use the Free VMware Server to create VMs.

So strictly speaking, you don't really need VMware Workstation at all.

---

### Post by jdrodrig on 2009-05-04
I am confused...

so why would anyone pay for VMware workstation?

what is the main practical difference?

---

### Post by maflynn on 2009-05-14
just go to vmware.com and you'll see it there.

---

### Post by Junkieman on 2009-05-25
> **jdrodrig said:**
> I am confused...

so why would anyone pay for VMware workstation?

what is the main practical difference?
@jdrodrig I keep asking myself those same questions ;)

I use VM Player at home and work, yes you can't create VM's using the player itself, but the VM definition is a XML file. Try [easyvmx]("http://www.easyvmx.com/") for creating VM's online, works a treat!

Edit: use the [v2 generator]("http://www.easyvmx.com/new-easyvmx.shtml"). I've created more VM's than I can count, no complaints this side.

---

### Post by veloce on 2009-05-25
> **jdrodrig said:**
> I am confused...

so why would anyone pay for VMware workstation?

what is the main practical difference?

Workstation also has trial 3d support.  (No I wouldn't pay for that.) However, if it was as good as Fusion, I'd certainly pay $75 for it.

(I use vmserver or kvm and rdp to the running machines to get a useful user interface).

---

