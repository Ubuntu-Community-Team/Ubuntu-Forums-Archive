---
title: "New Guest OS on KVM"
date: 2010-06-08
forum: Virtualisation
---

### Post by totallynewbie on 2010-06-08
I created a new guest OS (lucid server) in a host OS (lucid server). I can ping the guest OS after install but i can't ssh.
How can i manage my new guest OS?

---

### Post by benderisgreat on 2010-06-08
if you start the guest with a -vnc option you can get a console through that:
```
$ kvm guest.img -vnc :1
$ vncviewer localhost:1
```
then you could install an ssh-server
```
$ sudo apt-get install openssh-server
```

---

### Post by totallynewbie on 2010-06-09
this is how i install the guest:

#vmbuilder kvm ubuntu --domain=barracuda --mem=1024 --rootsize=102400 --swapsize=512 --cpus=4 --hostname="barracuda" --ip=172.16.88.91 --mask=255.255.255.0 --gw=172.16.88.88 --destdir=/data/virt/barracuda.img --user="theuser" --name="theuser" --pass="thepassword" --mirror [ftp://kambing.ui.ac.id/ubuntu/](ftp://kambing.ui.ac.id/ubuntu/) --components main,universe --addpkg=vim --addpkg=vim openssh-server --libvirt=qemu:///system --bridge=br0 --timezone="Asia/Jakarta" --suite=lucid;

---

### Post by totallynewbie on 2010-06-09
I disabled apparmor, and that's it.
I can ssh to my guest OS.

Why is it so difficult working with apparmor? :p

---

