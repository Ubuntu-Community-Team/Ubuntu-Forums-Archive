---
title: "Problem on installing KVM/QEMU"
date: 2022-01-09
forum: Virtualisation
---

### Post by satimis on 2022-01-09
Hi all,

Ubuntu 20.04

I follow below document to install KVM/QEMU

KVM hypervisor: a beginners’ guide
[https://ubuntu.com/blog/kvm-hyphervisor](https://ubuntu.com/blog/kvm-hyphervisor)

On Terminal run;
$ sudo apt -y install bridge-utils cpu-checker libvirt-clients libvirt-daemon qemu qemu-kvm

$ kvm-ok```

INFO: /dev/kvm exists
KVM acceleration can be used
```

$ sudo virt-install --name ubuntu-guest --os-variant ubuntu20.04 --vcpus 2 --ram 2048 --location [http://ftp.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/](http://ftp.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/) --network bridge=virbr0,model=virtio --graphics none --extra-args='console=ttyS0,115200n8 serial'```

N: Unable to locate package virt-install

```

$ sudo apt-get install virtinst

$ sudo virt-install --name ubuntu-guest --os-variant ubuntu20.04 --vcpus 2 --ram 2048 --location [http://ftp.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/](http://ftp.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/) --network bridge=virbr0,model=virtio --graphics none --extra-args='console=ttyS0,115200n8 serial'```

ERROR    Failed to connect socket to '/var/run/libvirt/libvirt-sock': No such file or directory

```

Please help.  Thanks

Regards

---

### Post by Dennis N on 2022-01-09
That looks complicated for a simple Desktop installation. I needed no commands with complicated options like you are showing. 

I did notice in reading articles on installing QEMU/KVM on Ubuntu that different articles list different sets of packages to install. Confusing. 

After I installed QEMU/KVM on Ubuntu 20.04 on Apr 30, 2021, I wrote down in my log what I thought was necessary. Maybe the list could be shorter, as I suspect a couple of these would be dependencies of others in the list if you install in a certain order. 

```
qemu-kvm
libvirt-clients
libvirt-daemon-system
virtinst
virt-manager
libvirt-daemon
virt-viewer
libspice-server1

```

Add yourself the the libvirt and kvm groups. Then you can launch from the Virt-Manager Icon and make a VM.

Some of these guys are telling us to install bridge-utils as required (as your article does). I left it out and it wasn't needed for my usage, as I can connect to my host and internet without it. Probably its for more advanced setups? 

My primary VM host is Fedora, installed several years ago. To install QEMU/KVM on that, I just needed one command:
```
sudo dnf install @Virtualization
```
then add user to the right groups, and done. Very nice.

---

### Post by satimis on 2022-01-09
> **Dennis N said:**
> That looks complicated for a simple Desktop installation. I needed no commands with complicated options like you are showing.

- snip - 
Thanks for your advice.

You're right.  Reading documents online made me quite confusing.  There are many suggestions.

Finally I figured out my problem running following commands on Terminal:-

$ sudo apt install libvirt-daemon-system

$ sudo adduser 'satimis' libvirt
$ sudo adduser 'satimis' kvm
$ sudo virsh list --all```

 Id   Name   State
--------------------

```

$ sudo systemctl enable --now libvirtd
$ sudo apt install virt-manager
$ sudo usermod -G libvirt -a satimis

reboot PC 

Now I can start virt-manager, adding it to favorites.  The 1st client created is Linuxmint (Mint00)

The icon of virt-manager is NOT very clear.  I have download a new icon on Internet.  How can I change its icon?

Regards

---

### Post by MAFoElffen on 2022-01-10
Even the later was made more difficult than it needed to "be"... Too late not, but there are easier ways to do those.

---

### Post by satimis on 2022-01-10
I have started a new posting re: change of icon on menu bar

---

