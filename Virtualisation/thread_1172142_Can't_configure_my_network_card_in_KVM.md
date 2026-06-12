---
title: "Can't configure my network card in KVM"
date: 2009-05-28
forum: Virtualisation
---

### Post by zoho on 2009-05-28
Ubuntu 9.04 x64 Virtual Machine Manager was used to setup a KVM. Every thing worked fine, but I can not modify the virtual network card settings e.g. to use NAT or bridging mode with the real network card of the host. 
What could be possible reasons for this ?

---

### Post by zoho on 2009-05-28
Found the solution finally. It is not possible as kvm user to configure enhanced virtual network card functions with the virt-manager. It needs to be started by the command line "sudo virt-manager". Now enhanced virtual network card options like bridging are available. An hint or an option to switch to root for the setup would be very helpful here.

So there is room for improvement here. At least when the KVM is configured and the user tries to modify the virtual network card settings an option to switch to root for the enhanced configuration should be available like in other system menus e.g. "User and Groups".

---

### Post by Pnuts on 2009-05-28
I assume your working on the local system in a GUI?

I wish I could find a way to do this remotely via virt-manager. For now I simply create my VM's from teh command line via ssh and then am able to connect to them via virt-manager.

---

### Post by zoho on 2009-05-29
You are right. I am currently working on localhost. 
The next step will be to setup a server. 
I will connect to it by ssh from my current GUI notebook and set a KVM on the server by remote. I will keep you posted

---

### Post by zoho on 2009-06-09
I could create a KVM via virt-manager on the remote server.
- create ssh connection from client to server
- copy the ubuntu iso to the /var/lib/libvirt/images folder
- start virt-manager on the client as root (sudo -i)
- connect qemu ssh to server
- right-click the server connection and select "Details->Storage"
- Create a new volume for the Ubuntu iso here
- Now create a KVM via virt-manager and point to the iso location configured above
...

Now I will try to manage the server kvm with a normal user.

---

