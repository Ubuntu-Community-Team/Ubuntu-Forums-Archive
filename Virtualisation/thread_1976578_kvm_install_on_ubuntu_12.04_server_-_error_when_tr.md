---
title: "kvm install on ubuntu 12.04 server - error when trying to use virt-manager"
date: 2012-05-08
forum: Virtualisation
---

### Post by ClientAlive on 2012-05-08
I followed: [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)

and, optionally, installed virt-manager as well. virt-manager launches but when I click "New" to create a virtual machine I see the following error at the bottom of that window:

```

Error: No active connection to install on.

```results of google search on that error are pathetic...

While there are a couple things that occur to me to check into, I'm a little concerned about making changes to the system without understanding what I'm doing. I'd like to somehow verify that everything that's supposed to be running is running, whatever networking is supposed to be in place is correct, etc, etc - that everything is working right. And ultimately just get on with using the stuff.

Can anyone walk me through this?

Thanks in advance

---

### Post by kiCKYou on 2012-05-09
Got the same problem.

---

### Post by kiCKYou on 2012-05-11
I managed to get it working after this command:
$ virt-manager -c qemu:///system kvmhost

Don't forget to add user to groups:
$ sudo adduser `id -un` kvm
$ sudo adduser `id -un` libvirtd

I hope that helps.

---

### Post by ClientAlive on 2012-05-12
> **kiCKYou said:**
> I managed to get it working after this command:
$ virt-manager -c qemu:///system kvmhost

Don't forget to add user to groups:
$ sudo adduser `id -un` kvm
$ sudo adduser `id -un` libvirtd

I hope that helps.


Sorry for the delay and thank you for your reply. I've since changed to fedora as my host. Haven't gotten to try to running virt-manager yet as I'm experiencing a different problem (something I hope to correct this evening). I'm sure that what you've shared will come in very handy at that time though. Again, thanks.

Jake

PS: I'm assuming these are to be done as root - yes?

---

