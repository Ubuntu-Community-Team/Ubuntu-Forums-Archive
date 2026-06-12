---
title: "KVM, w2k, and blu-ray drive"
date: 2008-04-22
forum: Virtualisation
---

### Post by tek400 on 2008-04-22
hi all,

I've been vexed by a problem since upgrading to Hardy beta. In Gutsy (2.6.22-14) I could use qemu/kvm to boot a virtual w2k guest. From the guest I could run blu-ray apps with -cdrom /dev/scd0 pointing to my LiteOn blu-ray drive.

kvm -no-acpi -m 512 -localtime -hda w2k.img -cdrom /dev/scd0

This worked under Gutsy even though neither w2k nor Gutsy could understand UDF 2.5; I think the app I was running (slysoft's anydvd) had its own udf 2.5 driver.

since upgrading to Hardy this does not work. the above command line is fine, and if I have anything other than a blu-ray disk it is accessible from the guest without any problem. I patched my kernel to understand udf 2.5 and I can see the blu-ray drive structure from Hardy just fine, which is why I don't think this a revocation or other blu-ray related problem.

What's really odd is that if I boot Hardy but use the old kernel 2.6.22-14, presumably with the old modules, the vm still does not allow blu-ray access. I don't know how this could be, since I thought most of kvm/qemu is in the kernel now. Somewhere around qemu-60 a bunch of changes were made to the cdrom code.

The error message in w2k is e:\ drive not accessible incorrect function. Many people have this error when trying to access a RW medium when the OS thinks its RO. info block shows

ide1-cd0: type=cdrom removable=1 locked=0 file=/dev/scd0 ro=1 drv=host_device

Questions:

Is there a way to tell qemu/kvm to make ro=0?
Does drv=host_device enable pass-through of all commands, or does it block some?
w2k sees "QEMU QEMU DVD-ROM" as the device type. can I change this to dvd+rw or something else?

thanks,
tek400

---

