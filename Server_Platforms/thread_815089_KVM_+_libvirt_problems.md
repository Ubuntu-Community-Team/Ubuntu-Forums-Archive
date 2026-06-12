---
title: "KVM + libvirt problems"
date: 2008-06-01
forum: Server Platforms
---

### Post by Celephais on 2008-06-01
Hi,

I have installed ubuntu 8.04 server for amd64 on a machine.
My aim is to run different OS on my small server inside my local network using kvm and libvirt.

First I tried to install Windows XP: the first installation stage complete (the one with blue background and DOS-style interface) but the second stage stuck at 39 minutes to end.
There is a way to complete the installation or is a waste of time to continue? I used this command for the installation:

sudo virt-install -n winxp2 -r 256 -f /dev/srvMuletto/winxp2 -c /home/mario/xp.iso --os-type=windows --os-variant=winxp --vnc

During this process I found 3 small problem:

1- The vnc screen cannot be used trought the LAN because is bounded to the loopback network interface (127.0.0.1), I have to use a ssh tunnel. Is there a way to make the vnc server to bound to the "real" interface?

2- virt-install assign the iso file as a cdrom but after the first reboot (at the end of the first stage) , the iso in not more mounted, using vrish attach-disk return an error. I managed to resolve this adding by hand the cdrom device in the virtual machine configuration file. The way to attach device and disk is poorly documentated and is not obvius, am I doing something wrong?

3- I found no way to delete virtual machine with virsh or some other command, it have to be done by hand deleting configuration files and image files. Is there a command to do this?

Then I tried to install ubuntu server 8.04 amd64 as a guest using virt-install again, it reach the end but it's terribly slow.

I saw the program ubuntu-vm-builder but as far as I can see there is no way to create virtual machine inside logical volume. Maybe I'm not been able to find the right documentation. Any suggestion?

Thanks

---

### Post by theSeinfeld on 2009-08-13
It is easy to delete from the gui (virt-manager). It is in the api of libvirt but there is no command in virsh to delete (not to my knowledge).

Hope this helps...

---

### Post by drumbug1 on 2009-10-13
> **theSeinfeld said:**
> ...there is no command in virsh to delete (not to my knowledge).

There is a command in virsh to do this:

```
virsh destroy domain
```

You can see the full list of options easily by running:

```
virsh --help | more
```

---

### Post by bmullan on 2009-10-29
> **Celephais said:**
> Hi,

I have installed ubuntu 8.04 server for amd64 on a machine.
My aim is to run different OS on my small server inside my local network using kvm and libvirt.

First I tried to install Windows XP: the first installation stage complete (the one with blue background and DOS-style interface) but the second stage stuck at 39 minutes to end.
There is a way to complete the installation or is a waste of time to continue? I used this command for the installation:

sudo virt-install -n winxp2 -r 256 -f /dev/srvMuletto/winxp2 -c /home/mario/xp.iso --os-type=windows --os-variant=winxp --vnc

During this process I found 3 small problem:

1- The vnc screen cannot be used trought the LAN because is bounded to the loopback network interface (127.0.0.1), I have to use a ssh tunnel. Is there a way to make the vnc server to bound to the "real" interface?

2- virt-install assign the iso file as a cdrom but after the first reboot (at the end of the first stage) , the iso in not more mounted, using vrish attach-disk return an error. I managed to resolve this adding by hand the cdrom device in the virtual machine configuration file. The way to attach device and disk is poorly documentated and is not obvius, am I doing something wrong?

3- I found no way to delete virtual machine with virsh or some other command, it have to be done by hand deleting configuration files and image files. Is there a command to do this?

Then I tried to install ubuntu server 8.04 amd64 as a guest using virt-install again, it reach the end but it's terribly slow.

I saw the program ubuntu-vm-builder but as far as I can see there is no way to create virtual machine inside logical volume. Maybe I'm not been able to find the right documentation. Any suggestion?

Thanks


I've been using 10.0.2.2 as the KVM Host address that the guest should be able to always get to.

I got that from reading the [WindowsXPUnderQemuHowTo]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo")

per that HowTo:

QEmu provides two modes of networking. In both modes, a virtual network adapter is created inside Windows XP guest.

User mode networking section of [WindowsXPUnderQemuHowTo]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo")

In user mode networking, QEmu manages network interface internally in the user mode emulator application. QEmu provides DHCP host which assigns a dynamic IP for the guest OS. TCP and UDP ports can be redirected from the host OS to the guest OS using QEmu command line parameters.

QEMU VLAN <-->  Firewall/DHCP server <--> Host Network[INDENT]          [INDENT][INDENT][INDENT]|          **(10.0.2.2)**[/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT]|
---->  DNS server (10.0.2.3)
|     
---->  SMB server (10.0.2.4)[/INDENT][/INDENT][/INDENT][/INDENT]

---

