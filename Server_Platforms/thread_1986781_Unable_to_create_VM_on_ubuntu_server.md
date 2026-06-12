---
title: "Unable to create VM on ubuntu server"
date: 2012-05-25
forum: Server Platforms
---

### Post by abeg on 2012-05-25
I have a test server with ubuntu 12.04 installed and I am trying to learn how to use it for hosting virtual machines.  I tried following the example included in the server documentation below and tweaking it slightly.
Version found in documentation:
sudo virt-install -n web_devel -r 256 \
--disk path=/var/lib/libvirt/images/web_devel.img,bus=virtio,size=4 -c \
jeos.iso --accelerate --network network=default,model=virtio \
--connect=qemu:///system --vnc --noautoconsole -v

Version with my settings:
user123@UBUNTU-HOST:/media/usbdrive$ sudo virt-install -n ubuntubox -r 4096  --disk path=/var/lib/libvirt/images/ubuntubox.img,bus=virtio,size=20 -c desktop.iso --accelerate --network network=default,model=virtio  --connect=qemu:///system --vnc --noautoconsole -v

Here's what I run into when I try executing the commands:

Starting install...
ERROR    internal error process exited while connecting to monitor: char device redirected to /dev/pts/1
kvm: -drive file=/media/usbdrive/desktop.iso,if=none,media=cdrom,id=drive-ide0-1-0,readonly=on,format=raw: could not open disk image /media/usbdrive/desktop.iso: Permission denied

Domain installation does not appear to have been successful.
If it was, you can restart your domain by running:
  virsh --connect qemu:///system start ubuntubox
otherwise, please restart your installation.

I tried running the suggested command and then go this error:
user123@UBUNTU-HOST:/media/usbdrive$ virsh -connect qemu:///system start ubuntubox error: unknown command: 'qemu:///system'

---

### Post by lukeiamyourfather on 2012-05-25
Try using a stable version of Ubuntu Server like 12.04 LTS since 12.10 isn't due out for another five months.

---

### Post by abeg on 2012-05-25
> **lukeiamyourfather said:**
> Try using a stable version of Ubuntu Server like 12.04 LTS since 12.10 isn't due out for another five months.

Whoops.  That was definitely a typo on my part.  Just to be sure, I confirmed that the iso shows "ubuntu-12.04-server-amd64.iso".  I will update my original post with the correct version number.

---

### Post by abeg on 2012-05-26
If anyone happens to have a link to a tutorial on how to create a virtual machine with ubuntu server, I wouldn't mind starting over with a fresh install.  Aside from the official documentation, I haven't been able to find anything that is step by step for beginners.

---

### Post by rwh on 2012-05-29
Looks to me like kvm or libvirt can't access the iso because it's on an automounted USB stick.  By default these are readable only by the currently logged on user, and kvm/libvirt run as the libvirt-qemu user.

There are a couple of easier ways to create VMs for use with KVM.  The most GUI based is to install virt-manager.  This allows you to create VMs with a wizard and install the OS as you usually would with a regular CD iso.

Another method is to use vmbuilder:

[https://help.ubuntu.com/12.04/serverguide/jeos-and-vmbuilder.html](https://help.ubuntu.com/12.04/serverguide/jeos-and-vmbuilder.html)

And the easiest option is probably to check out virtualbox, which is a more desktop-focussed solution, and has more mature video and disk drivers for that purpose.

HTH,

Rob

---

### Post by abeg on 2012-06-14
> **rwh said:**
> Looks to me like kvm or libvirt can't access the iso because it's on an automounted USB stick.  By default these are readable only by the currently logged on user, and kvm/libvirt run as the libvirt-qemu user.

There are a couple of easier ways to create VMs for use with KVM.  The most GUI based is to install virt-manager.  This allows you to create VMs with a wizard and install the OS as you usually would with a regular CD iso.

Another method is to use vmbuilder:

[https://help.ubuntu.com/12.04/serverguide/jeos-and-vmbuilder.html](https://help.ubuntu.com/12.04/serverguide/jeos-and-vmbuilder.html)

And the easiest option is probably to check out virtualbox, which is a more desktop-focussed solution, and has more mature video and disk drivers for that purpose.

HTH,

Rob
Thanks for the response.  Would performance be the major difference between the two?  I've been using virtulbox for a few weeks now and one of the issues I found is with optimizing memory settings.  The memory ballooning function does not seem to be quite the same as dynamic memory allocation with Hyper-v.

---

