---
title: "How can i start Grid-Appliance with kvm and virsh"
date: 2010-03-19
forum: Virtualisation
---

### Post by EiskalterEngel on 2010-03-19
Hallo,

First some sentences about what i want to do:

I wanna build a little Grid-System with Grid-Appliance and kvm under linux. 

The appliance consists of 4 files:

floppy.img
ga.nvram
ga.qcow2
GridAppliance.vmx

I can run the Appliance with:
kvm -m 256 -smp 1 -hda ga.qcow2 -fda floppy.img -net user,vlan=0 -net nic,vlan=0,model=pcnet -boot c
That works fine.

But my Problem is, that i wanna install and configure it on a cluster which is far away and to which i only can connect with a ssh-connection.

because of that I have to use the commandline to run the appliance. 

So i have read that you can use virsh to start VMs only with the commandline.

How can i start the appliance with virsh?

In the most tutorials there is only an example for a fully new VM. But how does it work with the appliance. What must i do, that i can start the appliance with virsh?

At the moment i'm testing all at my own computers at home. If it all works i would install it at the cluster.
I have two computers here, one Core2Quad Q6600 and one P4. So to simulate the Situation i connect from the p4 with ssh to the q6600. At both computers is Ubuntu linux installed (vers. 9.10 Karmic Koala)  and on the Q6600 there is kvm installed.

Sad to say, but i'm a newbie with linux and kvm. Can someone help me please?:confused:

thanks for any answer.

Bests 
Patrick

---

### Post by robinharvey on 2010-03-21
Hi,

Virsh is a command-line client of libvirt - this is a VM management library which can take care of low level details of starting and stopping VMs, including networking.  The idea of libvirt is that you can use it for different kinds of virtualisation, such as KVM or XEN, all with the same interface.

If you want to use virsh on your remote host machine then you should first install libvirt, this includes a management daemon called libvirtd (this is what virsh connects to).  There's some documentation on how to set this up here: [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM).  When you read through this documentation, you'll notice some additional params that you can pass to ubuntu-vm-builder that installs and configures SSHD in the VMs you create so that you can connect over SSH.  Here's a copy of the command I used to do this:
```
sudo ubuntu-vm-builder kvm intrepid \
    --arch 'amd64' \
    --mem '1024' \
    --rootsize '8192' \
    --swapsize '1024' \
    --kernel-flavour 'server' \
    --hostname 'your-web-server' \
    --domain 'pad' \
    --mirror 'http://archive.ubuntu.com/ubuntu' \
    --components 'main' \
    --name 'Eiskalter Engel' \
    --user 'eiskalter' \
    --pass 'whateveryoulike' \
    --mac '54:52:00:43:91:2A' \
    --bridge 'br0' \
    --libvirt 'qemu:///system' \
    --addpkg 'openssh-server'

```

HTH,
--Robin

---

### Post by EiskalterEngel on 2010-03-25
Hello Robin,

thanks for the Answer. I've installed libvirt, etc.

After that i have created the xml-File for the appliance with:

echo "kvm -m 256 -smp 1 -hda ga.qcow2 -fda floppy.img -net user,vlan=0 -net nic,vlan=0,model=pcnet -boot c" > gridclient.txt

and:

virsh domxml-from-native qemu-argv gridclient.txt > gridclient.xml

Then I started virsh and define the VM with:
define gridclient.xml

Now i can see the VM gridclient with the option list --all.

But i can't start the VM.

I get the Message:
ERROR: Domain gridclient couldn't be started
ERROR: Cannot find QEMU binary kvm: No such file or directory

What is wrong? What can I do to getting started the VM?

Bests
Patrick

---

