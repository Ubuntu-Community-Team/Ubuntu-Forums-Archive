---
title: "Help with ubuntu-vm-builder"
date: 2011-07-01
forum: Virtualisation
---

### Post by gabrielpasv on 2011-07-01
What's the option with ubuntu-vm-builder that will setup the name of my VMmachine?

Not the hostname. The file name that will be created ?

Because when I use this command below it already create a VM with the default name



 ubuntu-vm-builder kvm hardy --arch 'amd64'  --mem '128'  --rootsize '4096'  --swapsize '1024'  --kernel-flavour 'generic'  --hostname 'ubuntu'  --mirror 'http://archive.ubuntu.com/ubuntu'  --components 'main'  --name 'Joe Ubuntu'  --user 'ubuntu'  --pass 'ubuntu' 


can anyone please help me with this?


thanks

---

### Post by collisionystm on 2011-07-01
> **gabrielpasv said:**
> What's the option with ubuntu-vm-builder that will setup the name of my VMmachine?

Not the hostname. The file name that will be created ?

Because when I use this command below it already create a VM with the default name



 ubuntu-vm-builder kvm hardy --arch 'amd64'  --mem '128'  --rootsize '4096'  --swapsize '1024'  --kernel-flavour 'generic'  --hostname 'ubuntu'  --mirror 'http://archive.ubuntu.com/ubuntu'  --components 'main'  --name 'Joe Ubuntu'  --user 'ubuntu'  --pass 'ubuntu' 


can anyone please help me with this?


thanks

It sounds like you are using Hypervisor on ubuntu server, correct?

From an Ubuntu Desktop, just install virtual machine manager from the software center. It does an SSH connection to your server so you can build, manage and view your machines all through ssh.

---

