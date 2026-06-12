---
title: "Multiple NICs in KVM"
date: 2009-02-04
forum: Virtualisation
---

### Post by Drate on 2009-02-04
My Goal:

To be able to add a second (or third, etc.) nic to a Guest VM using Ubuntu's KVM installation and thereby create a server/gateway VM for other Guest VMs to connect through.  That is, if the "Gateway" VM crashes, the other Guest VM's should be virtually inaccessible (har har) to the outside world.

What I have found so far:

/etc/libvirt/qemu/virtual_guest.xml

I managed my way to the network interface entry, and saw the "<source network='default'/>" option, but I have no idea what to put in place of default to make it local to the VM's only.

The best I can find on the Google-Net is a vague reference or two to using VDE and setting up an interface in the OS for VDE to use, and then let this VDE act as a switch between the Gateway Guest and the Client Guests.

The funnest part about that of course, is Network-Manager seems to not have any configuration settings ANYWHERE that I can manually add an interface for such use and the nm-applet doesnt even recognize the automatically generated "vnet0" interface that I presume was being used by my one current VM Guest.

SO... can anyone point me to a doc, tell me what I'm missing, or give me any (re)direction as to how to add multiple NIC's to a VM correctly, and have at least one of them not be connected to the outside world?

---

### Post by Drate on 2009-02-10
Bump.

---

### Post by Drate on 2009-02-11
Is bumping a lost cause on this one?

---

### Post by mfinlayson on 2009-08-12
I had a similar working configuration and posted an update to the networking section in the KVM docs here on Ubuntu.

[https://help.ubuntu.com/community/KVM/Networking#Using%20multiple%20nics%20with%20multiple%20subnets%20i.e.%20vlans](https://help.ubuntu.com/community/KVM/Networking#Using%20multiple%20nics%20with%20multiple%20subnets%20i.e.%20vlans)

I imagine that you will need to add an additional network parameter the the VM's xml config file.

    <interface type='bridge'>
      <mac address='%MAC%'/>
      <source bridge='brN'/>
    </interface>

Hope that help!

---

### Post by changlinn on 2010-06-27
This maybe too late as the thread is old, but I found this thread via google, then seconds later worked out how to do it in the gui.
Open the virtual machine from libvirt, then click on view and toolbar. Now click the blue information icon and click add hardware, add a nic and you are done.

---

