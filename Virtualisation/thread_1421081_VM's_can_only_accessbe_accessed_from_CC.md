---
title: "VM's can only access/be accessed from CC"
date: 2010-03-03
forum: Virtualisation
---

### Post by sticksnleaves on 2010-03-03
I can only access VM's from the CC (ping or SSH). I can't seem to figure out how to access a VM from any other workstation on the network. My network mode is MANAGED-NOVLAN and I installed it using UEC.

---

### Post by sticksnleaves on 2010-03-03
This is Eucalyptus specific.

---

### Post by bmullan on 2010-05-15
> **sticksnleaves said:**
> I can only access VM's from the CC (ping or SSH). I can't seem to figure out how to access a VM from any other workstation on the network. My network mode is MANAGED-NOVLAN and I installed it using UEC.

One thing I found was the netmask of my VMs was different from my local network.

My local net is a 192.168.1.x 255.255.255.0
The VMs were created with a 192.168.1.x 255.255.255.**255**

So the VMs can't talk outside of their subnet which is behind the Bridge br0.

My suspicion is this is related to a feature read about in the UEC Enterprise Cloud Architecture document in the section titled NETWORKING.

UEC has [**3 possible networking modes**]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CBYQFjAA&url=http%3A%2F%2Fwww.ubuntu.com%2Fsystem%2Ffiles%2FUbuntuEnterpriseCloudWP-Architecture-20090820.pdf&ei=qB_vS5yjIoO88gbm6uX9Cg&usg=AFQjCNF_86QBrU-ZavDxaqghkxQcNY34Sw&sig2=hIvYZPcLOXI_hDFA2IpNIQ") you can configure for the VMs.

SYSTEM mode
STATIC mode
MANAGED mode

In the description of Managed Mode they mention that the UEC admin defines the network usually private **and unroutable**

That's what I think might be getting setup but I've not had time to check my own UEC setup yet.

---

