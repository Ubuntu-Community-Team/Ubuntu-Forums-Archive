---
title: "How do you get KVM  to work with VDE networking on Ubuntu 9.04?"
date: 2009-09-03
forum: Virtualisation
---

### Post by zarthon on 2009-09-03
**Do I need to build vde2 or kvm to use kvm virutal machines with vde virtual networks on Ubuntu 9.04****?**
Dose anyone have this working from the repository versions? ? 

KVM with VDE has been vexing me for days so i really could use some insight. 

I am using Ubuntu 9.04
I enabled backports and proposed and apt-get reported that kvm and vde2 were still at the latest version in the repository.
QEMU PC emulator version 0.9.1 (kvm-84)
ii  kvm             1:84+dfsg-0ubun Full visualization on i386 and amd64 hardware
ii  vde2            2.2.2-3ubuntu1  Virtual Distributed Ethernet


**Simple examples from howtos docs and faqs have the following results:**

**If i use the kvm** command to execute a virtual machine with a vde connection it does not work instead i get:
"Unknown network device: vde"

**If i use vdeq or vdekvm** i get the message
arg ,sock=/tmp/myswitch
TUNGETIFF ioctl() failed: Invalid argument

**IF i use qemu** I do not get an error message on launch. It is not using kvm or kqemu. I have not tested the network beyond configuring the network interface in the virtual machine with ifconfig and verifying that it is connected to the vde switch by going into the vde console. The configuration is unacceptably slow anyway.
****

---

### Post by zarthon on 2009-09-05
I have been through several FAQ's and howtos. I just don't know what is wrong or what I am missing. It is quite honestly driving me *nuts*. I would be very thankful for any help!

---

### Post by bodhi.zazen on 2009-09-13
Personally I just bridge my network card.

[http://blog.bodhizazen.net/linux/virt-manager-bridged-networking/](http://blog.bodhizazen.net/linux/virt-manager-bridged-networking/)

[http://blog.bodhizazen.net/linux/kvm_network_scripts/](http://blog.bodhizazen.net/linux/kvm_network_scripts/)

How is it you run KVM ?

For VDE See :

[http://www.debianadmin.com/create-a-lan-for-virtual-servers-with-kvm-and-vde.html](http://www.debianadmin.com/create-a-lan-for-virtual-servers-with-kvm-and-vde.html)

[http://tjworld.net/wiki/Linux/Ubuntu/VirtualMachinesWithVDENetworking?format=txt](http://tjworld.net/wiki/Linux/Ubuntu/VirtualMachinesWithVDENetworking?format=txt)

---

### Post by riskable on 2009-12-09
> **zarthon said:**
> I have been through several FAQ's and howtos. I just don't know what is wrong or what I am missing. It is quite honestly driving me *nuts*. I would be very thankful for any help!

Did you ever get it working?  I'm having the same problem and I've tried *everything*.  No matter what I try vdeqemu, vdeq, vdekvm...  I always get those TUNGETIFF and TUNSETOFFLOAD errors.  Nothing in any system log is helpful in indicating what is causing this.

What's crazy is that I use to have this working just fine in 9.04.  When I upgraded to 9.10, that's when the problem started happening.  The configs are all the same!

WTF changed that VDE doesn't work anymore?

---

