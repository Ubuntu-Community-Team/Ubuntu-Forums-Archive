---
title: "Virtualization workstation?"
date: 2011-05-26
forum: The Cafe
---

### Post by hambone79 on 2011-05-26
I have two workstations in my home office that are currently connected through a KVM switch to several monitors. One is a general purpose Linux box and the other is my Windows 7 CAD workstation. I'm currently looking to upgrade both computers, but I'm thinking it may be better to build one big system to virtualize both operating systems. Here is what I would like to do:

1. Run Linux and Windows simultaneously without a significant slowdown.
2. Have full 3D support for both operating systems so that I can run CAD software and games.
3. Support for me to run all 4 of my LCD displays.
4. Ability to share file systems seamlessly
5. Ability to share desktops seamlessly.
6. Ability to share hardware seamlessly.

Anyone ever done this?

---

### Post by Bandit on 2011-05-27
> **hambone79 said:**
> I have two workstations in my home office that are currently connected through a KVM switch to several monitors. One is a general purpose Linux box and the other is my Windows 7 CAD workstation. I'm currently looking to upgrade both computers, but I'm thinking it may be better to build one big system to virtualize both operating systems. Here is what I would like to do:

1. Run Linux and Windows simultaneously without a significant slowdown.
2. Have full 3D support for both operating systems so that I can run CAD software and games.
3. Support for me to run all 4 of my LCD displays.
4. Ability to share file systems seamlessly
5. Ability to share desktops seamlessly.
6. Ability to share hardware seamlessly.

Anyone ever done this?
Yes. Most every large company does this in some shape or form with out the exception of the displays.
Most large corperations have a few rack servers with multiple computers running Linux and VBox or VM ware and have multiple OS's running everyhing from SQL servers, Java serves, Apache/IIS services or mail services. All running independent of each other all running in a VM on Linux. The benefit it load balancing and cost savings. This practice is very common and taught in college now.

---

### Post by toupeiro on 2011-05-29
Bandit oversimplifies, or I overcomplicate...

It sounds like you want a bare metal hypervisor (Virtualize BOTH operating systems)...  Going this route with bare metal virtualization (no HOST OS e.g. virtualbox)ou are not simply talking about virtualization, you need to push GPU hardware assist and oversubscribe it.

As far as everything else, yes thats a no brainer.  I've achieved virtualization ratio's of 40:1 using the right CPU's and enough RAM.

To solve your "Full 3D" scenario, you're going to need to do a little research into the graphical stack CAD is using.  (OpenGL, Direct3d?)  It CAN be done on bare metal in a few different scenarios but depending on how much you're actually doing, your mileage is going to vary.  The issue always comes back to what kind of direct access instruction is needed by the software to the hardware.  Traditional Virtualization does a SIGNIFICANT amount of offloading to the CPU, which simply cannot handle "FULL 3D" as I am imagining you might push it to as a GPU could do.  To get GPU acceleration into your VM using bare metal hypervisors is not yet as perfect of a science as the rest of the VM world.

I recommend you look into the following Technologies for bare metal:

PCoIP (Teradici)
Spice Protocol (you get this with redhat KVM)
RDP 7
and a thin client to do some client GPU assist with the two above mentioned protocols.

However, what I really recommend in your case is you do "Host based Virtualization" which implies a Host OS already on the machine and serves virtual machines on top of it. You're going to save money and get more out of it.  The solutions I mentioned above are more for of a business/enterprise approach due to the costs involved.  For true desktop performance in a virtual machine,  This method will provide enough horsepower to use things like CAD and other some types of 3d work. 
In this case, I recommend Parallels over virtualbox.  While Virtual box can extend some 3d acceleration, it can only do it to one VM at a time.  If you plan to need 3d acceleration in multiple VM's simultaneously, parallels is the very best host based virtualization software to do this.  They were the first (and still are the best) at being able to take multiple GPU's and assign them to virtual machines for true GPU accelerated VM's.

---

