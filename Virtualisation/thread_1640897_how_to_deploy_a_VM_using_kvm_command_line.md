---
title: "how to deploy a VM using kvm command line"
date: 2010-12-08
forum: Virtualisation
---

### Post by swamybabu on 2010-12-08
Hi,

I want to deploy WinXP VM using kvm cli and at the same time I want n/w to my VM. Can someone please help me?

I used the following but, it didn't get any n/w.

sudo kvm -soundhw ac97 -hda /var/lib/libvirt/images/WinXP.img


I deployed using virt-manager but, I am looking for command line way of deploying a VM with networking.

Thanks in advance.
          SWAMY

---

### Post by ortayus on 2010-12-08
How about instead of using virt-manager you use virt-install?

---

### Post by swamybabu on 2010-12-08
I would like to know how to deploy directly using kvm cli.

Thanks,
SWAMY

---

### Post by bodhi.zazen on 2010-12-09
See man qemu =)

Basically you make a virtual disk

and then call kvm from the command line. If you are not running X, use the -vnc option. You can then connect to the guest via a vnc viewer, either locally or from a second machine.

Of course you need to know a bit about networking and bringing up a TAP

See:

[https://help.ubuntu.com/community/KVM/Directly](https://help.ubuntu.com/community/KVM/Directly)

[http://blog.bodhizazen.net/linux/how-to-run-kvm-without-x/](http://blog.bodhizazen.net/linux/how-to-run-kvm-without-x/)

[http://blog.bodhizazen.net/linux/kvm-mouse-integration/](http://blog.bodhizazen.net/linux/kvm-mouse-integration/)

[http://blog.bodhizazen.net/linux/kvm_network_scripts/](http://blog.bodhizazen.net/linux/kvm_network_scripts/)

If you still have specific questions after working through those links, post back.

---

