---
title: "Hardy KVM with FreeBSD 7 Guest, Networking Questions"
date: 2008-06-20
forum: Virtualisation
---

### Post by ElroyJetson on 2008-06-20
I have a Hardy host installation with KVM. I have installed FreeBSD 7.0 as a guest, and I am trying to set up networking. I am looking to have the FreeBSD guest have an IP address on my 192.168.0.x network so I can SSH and interact with it. Instead, the guest selects an IP of 10.0.2.15 that I can not reach from the host machine. It uses DHCP to get the address.

I followed this document (and others over the interweb), and have a network bridge setup. Is this correct, and how would I specify to use my 192.168.0.x network for this gueest?

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

Any hints, gotchas, suggestions, or other useful information that I can provide?

Secondly, the guest can get out of the network, but it can not "ping" (unreachable). Is this unusual, or perhaps a firewall rule on the ubuntu host?

Also, when I shut down the guest, it does not stop the machine, nor does the "shutdown" button on virt-manager have an effect. I have to "destroy" the instance after shutdown is complete to stop it running.

Thanks!

---

### Post by igwk on 2008-06-21
By default, kvm/qemu will setup a user-mode networking stack to give network access to your virtual machine.  This method does not allow the virtual machine to "ping" outside machines because kvm/qemu would require root access to create the ICMP packets in your host machine.  See [http://bellard.org/qemu/qemu-doc.html#SEC30](http://bellard.org/qemu/qemu-doc.html#SEC30) for more details.

I believe what you want to do is used bridged networking (which involves creating and using TAP interfaces).  I don't think you can do this over a wireless connection but regular wired ethernet should work.  Unfortunately I haven't tried to setup and use this myself so I can't help you there.

---

### Post by Joco on 2008-06-22
As mentioned bridged networking is what you want. The documentation states this is not available via wireless. Setting up for wired NICs is easy. Just follow the instructions on the ubuntu KVM page.  Took my a couple of minutes to do (including typo checks).

---

