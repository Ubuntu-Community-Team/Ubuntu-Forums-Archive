---
title: "Howto start KVM virtual machine with encrypted disk"
date: 2013-01-27
forum: Virtualisation
---

### Post by David Herring on 2013-01-27
How do you start a KVM virtual machine using either virsh or virt-manager on a remote server once you have encrypted the disk for this guest machine ? I.E where can you type in the password ?

I encrypted the qcow2 disk using the command....

qemu-img convert -o encryption -O qcow2 disk.qcow2 disk-encrypted.qcow2

Then edited the virtual machine to change the disk used to be the encrypted version.

Now I'm unsure how to get the 'console' up where I should type 'cont' and give the password.

The following article talks about the qemu monitor - but I'm unsure how to set this up / get to it ?

Thanks for any help,
Dave

[http://blog.bodhizazen.net/linux/kvm-how-to-use-encrypted-images/](http://blog.bodhizazen.net/linux/kvm-how-to-use-encrypted-images/)

---

