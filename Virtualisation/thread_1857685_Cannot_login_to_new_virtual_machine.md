---
title: "Cannot login to new virtual machine"
date: 2011-10-10
forum: Virtualisation
---

### Post by iburry on 2011-10-10
I've been experimenting with building virtual machines using vmbuilder and kvm, and after much frustration, have succeeded in creating a nominally function VM.  I can start it up. I can shut it down. I can ping it. I cannot, however, login to it.  SSH connections are refused, and when I try the console command from virsh, I get:

```
virsh # console ubuntu
Connected to domain ubuntu
Escape character is ^]
error: internal error cannot find character device (null)
```Is there something I left out in the build, or is there some super-secret way of logging in that I'm not aware of?

vmbuilder script:
```
#!/bin/bash

vmbuilder kvm ubuntu --suite natty --flavour virtual --arch i386 -o \
        --libvirt qemu:///system --ip 192.168.1.100 --part vmbuilder.partition \
        --user user --name user --pass default --addpkg apache2 --addpkg apache2-mpm-prefork \
        --addpkg apache2-utils --addpkg apache2.2-common --addpkg dbconfig-common \
        --addpkg libapache2-mod-php5 --addpkg mysql-client --addpkg php5-cli --addpkg php5-gd \
        --addpkg php5-ldap --addpkg php5-mysql --addpkg wwwconfig-common --addpkg mysql-server \
        --addpkg unattended-upgrades --addpkg acpid --tmpfs - \
        --firstboot ~/faa-serve/boot.sh --firstlogin ~/faa-serve/login.sh
```faa-serve is the working directory. OpenSSH is supposed to be installed when the VM first boots and runs boot.sh

---

### Post by matthew.mattoon on 2011-10-12
The problem with the "console" option is that it is trying to go over the serial port as it would if you were using a truly headless machine, and the guest needs to be configured to accept that.

What I prefer to do on my remote machines is I install virt-manager or virt-viewer.

Then I connect to the kvmhost by:

# ssh -X kvmhost

Which will redirect X back through the SSH tunnel and open the GUI tool on my workstation.  Then I can launch virt-manager and connect to the guest, or use virt-viewer by:

# virt-viewer vname

If you prefer you can install virt-manager on your workstation and connect remotely, but I find it more utilitarian to run virt-manager on the host itself, so that I can launch it from Windows if I need to, or a machine where I cannot install additional programs.

More info on using virt-manager from Windows.

[http://blog.allanglesit.com/2011/03/linux-kvm-managing-kvm-guests-using-virt-manager-on-windows/](http://blog.allanglesit.com/2011/03/linux-kvm-managing-kvm-guests-using-virt-manager-on-windows/)

-matt

---

### Post by iburry on 2011-10-13
This kinda works on my Mac, but there appear to be some key mapping issues with X11.  The really workable solution was to run virt-manager from an Ubuntu desktop virtual. Yes, that's right. I'm managing my KVM virtuals on my server from a Virtualbox virtual on my desktop. Weeee!

But it works. Thanks

---

