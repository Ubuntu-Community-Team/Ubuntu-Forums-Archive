---
title: "virtualization with no X on the host machine"
date: 2011-04-18
forum: Virtualisation
---

### Post by daweefolk on 2011-04-18
Is it possible to run any virtualization software with no X server on the host machine? I have a server install and I'd like to know if I need to install X to use qemu, xen, or any other virtualization software.

---

### Post by falko on 2011-04-19
Yes, that's possible! :)

**KVM:**
[http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-10.10](http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-10.10)
[http://www.howtoforge.com/installing-kvm-guests-with-virt-install-on-ubuntu-10.10-server](http://www.howtoforge.com/installing-kvm-guests-with-virt-install-on-ubuntu-10.10-server)

**VirtualBox:**
[http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.0-on-a-headless-ubuntu-10.10-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.0-on-a-headless-ubuntu-10.10-server)

---

### Post by daweefolk on 2011-04-19
I don't have kvm in my kernel, and I'm not sure if I was completely clear when i asked my question.
What i meant was is there a way to virtualize on a server and use the framebuffer to display the vm?

---

### Post by TheR on 2011-04-20
> **daweefolk said:**
> I don't have kvm in my kernel, and I'm not sure if I was completely clear when i asked my question.
What i meant was is there a way to virtualize on a server and use the framebuffer to display the vm?

I believe you can display console locally (although I have never tried it). I use virt-manager constantly from remote machine and connect either to text or gui console. On negative side you have to enable root account on kvm server.

by
TheR

---

### Post by bodhi.zazen on 2011-04-20
> **daweefolk said:**
> I don't have kvm in my kernel, and I'm not sure if I was completely clear when i asked my question.
What i meant was is there a way to virtualize on a server and use the framebuffer to display the vm?

What do you want to display ? X applications ? In that event you will need X, you can use framebuffer to display X apps, but you still need X.

I would add things such as openvz or LXC to the list.

I personally run openvz, LXC, and KVM without X and, with KVM, use the built in VNC server to connect.

You can also use proxmox (openvz + KVM) which has a web interface - you can connect to the guests via the web interface. Does not require X on the server.

---

