---
title: "Virtualization of server on simple hardware"
date: 2012-10-30
forum: Server Platforms
---

### Post by yc2 on 2012-10-30
Hello,

My friend runs a server on an Acer Aspire One Laptop. (He runs Tor because he supports freedom of speech in China.) I connect to it via SSH.

I would like to run LAMP and postfix on it. My friend offers me to do that if we can virtualize a Linux system on it.

I tried to read a little and Xen seems to be a good virtualization engine. So maybe it is possible to make a virtualization of Ubuntu server under Xen?

My friend mentioned UML User Mode Linux. I think he has used it before.

My friend is rather busy and I would prefer not to bother him too much and find a virtualization system that works "out of the box" so he does not have to spend a lot of time fixing with it to make it work.

I think there are ways to point my domain to the virtual server and my friend can keep his domain pointed to his server even though IP are the same?

Thanks for suggestions how to virtualize Ubuntu server on hardware that is rather simple.

---

### Post by CharlesA on 2012-10-30
Xen has a learning curve and you will need hardware that supports hardware virtualization, because it is installed as the OS, as bare-metal. If they already have an OS on it, they could look into KVM, but there will be a learning curve, just like with Xen.

I use virtualbox, but that is mostly because I am lazy and it "just works" for me.

---

### Post by markbl on 2012-10-30
IMO, kvm is a better choice than virtualbox for virtualizing a linux server nowadays, and just as easy to use, if not easier. A kvm linux server guest performance is indistinguishable from the host in my testing, Virtualbox linux server guest is slightly slower.

Just do a "apt-get install ubuntu-virt" and run virt-manager to set your guest machine up. The good thing is that guest machines are created system wide, not per user, so all users in group "libvirtd" can create/modify any machine. You can also check a box to have the guest start up with the host.

Desktop guest machines still work better in Virtualbox because it has 3D  video acceleration.

---

### Post by yc2 on 2012-10-31
Thanks for your replies, I will look into kvm.

---

