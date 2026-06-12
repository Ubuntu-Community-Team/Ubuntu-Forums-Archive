---
title: "how can I attach an extra (second) virtual interface to a guest OS?"
date: 2009-06-29
forum: Virtualisation
---

### Post by Geran on 2009-06-29
Hello,

I'm learning about using virtualization and the biggest problem for me right now is the networking. How can I attach additional interfaces to my new guest OS?

Thank you,

G

---

### Post by bodhi.zazen on 2009-06-29
Shut down the guest. Then in the networking configuration you will see you can add up to 4 additional interfaces, one tab for each (Adapter) is displayed across the top.

Then restart the guest.

[img]http://buranen.info/wp-content/uploads/2008/06/AddVBoxHostInterface.png[/img]

---

### Post by Geran on 2009-06-29
> **bodhi.zazen said:**
> Shut down the guest. Then in the networking configuration you will see you can add up to 4 additional interfaces, one tab for each (Adapter) is displayed across the top.

Then restart the guest.

[img]http://buranen.info/wp-content/uploads/2008/06/AddVBoxHostInterface.png[/img]

Thank you, but I don't have this interface, does it need to be downloaded? Up until now I have only been using command line methods such as virsh and virt-viewer.

---

### Post by bodhi.zazen on 2009-06-29
Ah, that screen shot is for VirtualBox.

If you want a graphical front end for KVM, use virt-manager (it is in the repos).

If you want to use the command line, use man

man qemu 

Example :

```
qemu -boot c -hda /media/kvm/ubuntu.qcow2 \
 -net nic -net tap,vlan=0,ifname=0 \
 -net nic -net tap,vlan=1,ifname=1
```

man virsh

```
virsh attach-interface ...
```

[http://linux.die.net/man/1/virsh](http://linux.die.net/man/1/virsh)

Personally I find running KVM directly from the command line, with wrapper scripts, is easiest. I do like some of the graphical interfaces, virt-manager in Fedora 11 is nice (IMO) although there are other graphical, web based front ends for KVM (Convirt for example).

---

