---
title: "My VM won't start after server reboot after changing libvirt domain name-KVM"
date: 2021-02-14
forum: Virtualisation
---

### Post by piscesiscariot on 2021-02-14
I am running a VM on KVM running in Ubuntu Server 18.04.5.

The VMs have been set out to autostart, but after I changed the libvirt domain name the VM is unable to start automatically. 

See below KVM details:



[B][FONT=arial]uname -r
4.15.0-118-generic


 /usr/bin/qemu-system-x86_64 --version
QEMU emulator version 2.11.1(Debian 1:2.11+dfsg-1ubuntu7.32)


$ virsh version
Compiled against library: libvirt 4.0.0
Using library: libvirt 4.0.0
Using API: QEMU 4.0.0
[/FONT][FONT=Monaco][FONT=arial]Running hypervisor: QEMU 2.11.1[/FONT]

[/FONT]
[/B][COLOR=#F2F2F2][FONT=Monaco]
[/FONT][/COLOR]

---

### Post by TheFu on 2021-02-16
What does : /etc/libvirt/qemu/autostart have?  Look at where those links point. Are those all correct still?

Looks like you may need to patch your VM host.  I have a newer release of qemu-system-x86_64 on my 18.04 host.

---

### Post by piscesiscariot on 2021-02-16
I changed the VM domain name the following way:

```
virsh domrename vpre21 {New name}
```

set the new VM domain to autostart and when I navigate to /etc/libvirt/qemu/autostart 

I can only see the old VM domain but it shows a different colour: vpre21 is the old domain name

Can you please advise what qemu version you are running on your environment?

Thanks. 

```
pladmin@myr-devtest-kvm:/etc/libvirt/qemu/autostart$ ls -ltrh
total 0
lrwxrwxrwx 1 root root 26 May 11  2020 vpic.xml -> /etc/libvirt/qemu/vpic.xml
lrwxrwxrwx 1 root root 26 May 21  2020 vpsm.xml -> /etc/libvirt/qemu/vpsm.xml
lrwxrwxrwx 1 root root 37 Dec 31 14:35 license-manager.xml -> /etc/libvirt/qemu/license-manager.xml
lrwxrwxrwx 1 root root 28 Jan 26 11:10 vpre21.xml -> /etc/libvirt/qemu/vpre21.xml
lrwxrwxrwx 1 root root 30 Feb  3 11:57 elements.xml -> /etc/libvirt/qemu/elements.xml
```

---

### Post by TheFu on 2021-02-17
Sorry I wasn't clear.

The fix is to make a symlink from  /etc/libvirt/qemu/autostart  to the xml file for any VMs you want automatically started. That's the solution. The XML file needs to be "defined" already.  I tend to use virt-manager from a workstation to deal with VM stuff - have for about a decade.  Feel free to open a bug about the domrename not working with autostart symlinks, if you think that is useful.  The first thing the project will do is have you load the current, latest, libvirt and test. If that is something you aren't willing to do, a workaround is the best answer, as provided above.

In non-trivial environments, using the autostart symlink method probably isn't all that useful.  A startup script is needed to bring up VMs in the correct order with small delays before dependent VMs are brought up.  Similarly, bringing down the VMs is also needed, to prevent a DBMS VM from disappearing before the front-end web-app is shutdown.  These scripts don't need to be complex.

---

