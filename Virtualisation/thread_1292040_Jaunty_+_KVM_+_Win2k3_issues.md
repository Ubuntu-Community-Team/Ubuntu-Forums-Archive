---
title: "Jaunty + KVM + Win2k3 issues"
date: 2009-10-15
forum: Virtualisation
---

### Post by CHaoSlayeR on 2009-10-15
I'm having some issues with windows 2k3 64bit SMP guests using KVM.

The first thing is that I am using libvirt (virsh) for management of the VMs. Therefore I cannot use "-vga std" which is the KVM default and does not enable resolutions higher than 1024x768 with 24bit colordepth within the VM. According to the [domain XML format](http://libvirt.org/formatdomain.html#elementsVideo) the <video> element should be used to specify another video driver but that doesn't imply a change of the KVM command invocation.

When running the VM with the "-vga std" option from the console I do get the availability of a higher resolution but windows complains about a problem with the video device saying that it isn't working (although it booted just fine). As soon as I try to "update" the driver windows then searches for awhile and then freezes completely (the KVM process then goes completely into idle without crashing).

The full KVM command I used is this one:

```
/usr/bin/kvm -M pc -m 2048 -smp 4 -name win2k3-001 -uuid b6189950-49d3-e05c-9f93-7e3e4af92cc6 \
    -monitor pty -localtime -boot c \
    -drive file=/home/bob/vms/win2003-001-vm.img,if=ide,index=0,boot=on \
    -drive file=/home/bob/win2003-x64.iso,if=ide,media=cdrom,index=2 \
    -net nic,macaddr=54:52:00:48:d2:7c,vlan=0,model=virtio \
    -net tap,fd=11,script=,vlan=0,ifname=vnet0 \
    -serial pty -parallel none -usb -usbdevice tablet \
    -vga std -vnc 0.0.0.0:66 -k de
```

We are using Windows 2k3 Enterprise x64 SP2. As I have seen many other people using WinXP successfully with the standard VGA device there has to be a solution for my problem.


Thanx for any help.

C]-[aoZ

---

### Post by xOrphenochx on 2009-10-15
This may sound silly, but why not use RDP instead of VNC since it is a Windows machine? Truthfully, using virt-manager, I do remember setting the my resolution to 1280x1024 during all the setup I did prior to enabling RDP.

---

### Post by CHaoSlayeR on 2009-10-15
Thanks for the tip, I'll try the native windows RDP. But as I am unable to use a different graphics device that runs stable I don't understand how this is going to help as the default for kvm is the cirrus adapter with just 4MB memory resulting in very limited display resolution capabilities (of the windows guests point of view).

I can't enable higher resolutions "prior" enabling RDP because it is a headless server machine and I can't change to a higher resolution unless the standard VGA adapter is enabled... vicious circle... ;)

Nevertheless, I'll give it a try and post again if it works.

C]-[aoZ

---

### Post by xOrphenochx on 2009-10-15
It should work, can't quote me on this, but I'm sure it's not actually using the VM's card to do the drawing. I have had machines that can't match my 1920x1200 size because of driver limitations. It should be quick, give it a shot and report in.

---

### Post by CHaoSlayeR on 2009-10-17
Sorry for the late reply.

I tried what you suggested and in deed it works like a charm and in addition to that working on such VMs is much more responsive.

Really good.

The only thing I had to change was the color depth for RDP connections inside the VM:

open regedit, go here:
```
HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows NT\Terminal Services
```

and add a new **DWORD** key called **ColorDepth** with value **4**.

^^ just in case someone searches for similar things again. This also works for Windows XP.


C]-[aoZ

---

