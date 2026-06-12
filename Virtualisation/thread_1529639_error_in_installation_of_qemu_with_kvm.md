---
title: "error in installation of qemu with kvm"
date: 2010-07-12
forum: Virtualisation
---

### Post by aasthakm on 2010-07-12
I am trying to install QEMU on my machine. I get following error message when I try to configure the qemu-kvm package:
"[FONT=times new roman]Error: libpci check failed[/FONT]
[FONT=times new roman]Disable KVM Device Assignment capability.[/FONT]"

I am able to make and make install the package as such. But after that,
when I try to run the following command, it gives me the error as shown
below it.

qemu-system-x86_64 -hda myvm.qcow2

open /dev/kvm: No such file or directory
Could not initialize KVM, will disable KVM support

The VT capability is supported on  my machine, and is also enabled in the BIOS.

Please guide me as  to what could be wrong and what I need to do to get it running.

Thanks in advance,

Aastha.[COLOR=#888888]
[/COLOR]

---

### Post by sh1ny on 2010-07-12
This might help

[https://help.ubuntu.com/10.04/serverguide/C/virtualization.html](https://help.ubuntu.com/10.04/serverguide/C/virtualization.html)

---

### Post by aasthakm on 2010-07-13
Thanks for the link. I ran the first command kvm-ok and it shows 
"bash: kvm-ok: command not found". so does it mean that, hardware virtualization is not supported on my machine?

Aastha.

---

### Post by sh1ny on 2010-07-13
```
sudo apt-get install qemu-kvm
```

Or better yet :

```
sudo apt-get install ubuntu-virt-server
```

---

### Post by aasthakm on 2010-07-14
Could not find the packages from apt-get.

---

### Post by sh1ny on 2010-07-14
What ubuntu version ?

---

### Post by aasthakm on 2010-07-14
It's not ubuntu. It's debian. kernel 2.6.30.10.1.amd64-smp

Thanks for your help.

---

### Post by naelq on 2010-07-14
what debian branch are you running? from the kernel version, you are not on stable..
what do you have in '/etc/apt/sources.list' ?

the package you need to install is **qemu-kvm**, but it's not available from the stable branch!
[http://packages.debian.org/lenny-backports/qemu-kvm](http://packages.debian.org/lenny-backports/qemu-kvm)


nael

---

### Post by aasthakm on 2010-07-16
well, i was trying to use ptlsim 3.0, which is based on qemu-kvm support. i have not been able to build qemu package in that. so, i moved onto another simulator MARSSx86 which is also based on qemu and uses ptlsim. but it could install, and i am able to run it. thanks for your help.

---

