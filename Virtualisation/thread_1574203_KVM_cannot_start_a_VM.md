---
title: "KVM cannot start a VM"
date: 2010-09-13
forum: Virtualisation
---

### Post by DBQ on 2010-09-13
Hi everybody.

After struggling for a long time with virt-manager, I gave up, and just used vm-builder. I am now able to create a VM.

However when I try to start the VM (called MyServer) I get the following error:

```

$ sudo virsh --connect qemu:///system start MyServer

error: Failed to start domain MyServer
error: internal error Unable to find cgroup for MyServer

```

I googled all over the place but did not find anything helpful.

Few notes: I am running on Lucid.  Also, I start "libvirtd" using command line "sudo libvirtd" at the terminal, prior to using the command above that gives me an error.

Please help!

---

