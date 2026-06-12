---
title: "Allowing KVM virtual machines to host Apache"
date: 2010-09-10
forum: Server Platforms
---

### Post by deltatux on 2010-09-10
Hey guys,

I'm in a bit of a pickle because I don't know how to get this working on KVM. However I do know how to do this on VirtualBox.

Thing is that I'm trying to create a virtual machine in KVM that will be an Apache server host. However, I can't for the life of me find any information that will lead me to allow external machines on the network to access Apache on a KVM virtual machine.

My host machine is running Linux Mint 9 (which is virtually Ubuntu 10.04) and the server running in KVM is Ubuntu Server 10.04.

Please help.

Thanks,
deltatux

---

### Post by alan8 on 2010-09-12
Hi, you will need to configure bridged networking for your KVMs. See

[https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

> [...]to enable external hosts to directly access services on virtual machines  a bridge needs to be configured. This allows the virtual interfaces to  connect to the outside network through the physical interface, making  them appear as normal hosts to the rest of the network. 

---

