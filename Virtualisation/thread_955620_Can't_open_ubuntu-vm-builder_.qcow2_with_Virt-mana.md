---
title: "Can't open ubuntu-vm-builder .qcow2 with Virt-manager"
date: 2008-10-22
forum: Virtualisation
---

### Post by NaughtyusMaximus on 2008-10-22
I created a KVM vm using the instructions here: [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

I'd like to manager the created vm using virt-manager. The only way I can think of to import the VM into the virt-manager GUI is to go to 'file->restore saved machine', and then select 'xxx.qcow2', I get an error message which says "The file '.../xxx.qcow2' does not appear to be a valid saved machine image'

Am I doing this wrong, or is there a proper way to convert the image?

---

### Post by bodhi.zazen on 2008-10-22
I am no expert on Virt-manager, and do not get me wrong, it is nice to have a gui.

With that said, I am an old time qemu user and, IMO, kvm is a little easier to run from the command line. Virt manager seems to have limitations and sometimes you can only get it to do things by running it as root.

What is it you are converting ?

---

### Post by NaughtyusMaximus on 2008-10-22
I'm actually looking for the best way to set up a (qausi) high availability email server.

I have two physical machines (one is primary, and the other is secondary), and an iscsi array.  I'll be using the physical machines to host several VMs.  My thought was to run the VM off of physical server 1, and if there are any hardware problems on Physical 1, I can turn on the VMs on Physical 2 as a backup.

I was actually hoping to use convirt (formerly xenman) to do live migration in case of failure, but I can not seem to get that working properly under Hardy.

---

### Post by bodhi.zazen on 2008-10-22
If I am following your you are trying to copy a virtual machine. 

The qcow2 image is a hard drive, a virtual machine = hard drive + additional settings (ram, # CPU, etc.).

I think what you are wanting to do is copy the image and then boot it on another machine.

Simply 

cp image1.qcow2 image2.qcow2

then make a new machine in virt manager and assign image2.qcow as the hard drive.

Personally for me virtual machines are no more then a simple bash script

> #!/bin/bash

kvm <long line of options, ie memory, hd, interface>

I then launch the virtual machine from the command line by name (of the script). This way I do not have to specify all the options all the time, just edit the bash script if the options change.

To see the options see man kvm and man qemu.

=======

So just copy the image and boot :)

---

### Post by NaughtyusMaximus on 2008-10-23
I was actually referring to live migration - which I have gotten to work with the command line as follows:

Start VM on main machine as normal: kvm imagename.qcow2
Start kvm on secondary machine in 'listen' mode: -incoming tcp://0:4444
Migrade w/ primary machine: migrate -d tcp://secondary_ip:4444

Works like a charm.  My main thoughts are that since the GUI tools are improving, eventually it may make sense for me to use either convirt or virt-manager to manage my machines - or at least to show junior admins how to do simple tasks.. And when I've created the machines with the command line, I've not been able to open them with virt-manager at all.

---

### Post by NaughtyusMaximus on 2008-10-23
And now to answer my own question:

If I create a VM with virt-install, I can still use virt-manager.  It will not show up in the default 'localhost' connection window, but I can see the list if I connect to 127.0.0.1 through ssh

---

### Post by bodhi.zazen on 2008-10-23
Sweet, yes that is more complex.

My 2c is that Virt-man is not quite there yet, there are still things that I find easier via the command line.

I am hoping as virt manager matures it will continue to improve.

---

