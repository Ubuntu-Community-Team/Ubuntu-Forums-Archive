---
title: "Struggling with KVM"
date: 2009-10-09
forum: Server Platforms
---

### Post by as2003 on 2009-10-09
I'm struggling to set up virtualisation on a headless ubuntu server install.

I checked my CPU supports virtualisation (it does), installed kvm, created an image with ubuntu-vm-builder, enabled virtualisation in the BIOS (it was disabled), added a vga=XXX setting to /boot/grub/menu.1st (because I have no X stuff installed and without it my VM wouldn't boot)

So now I can go to the directory where ubuntu-vm-builder created the image and run.sh, and run run.sh and not get any errors...

But now what? How do I connect to this VM (from the local host, and from other machines on the network)? Does it have an IP address?

Thanks a million

---

### Post by mbeach on 2009-10-09
its been awhile since I played with kvm, but I seem to recall that when you start the virtual machine, there is a -vnc flag, and if you set it to something like -vnc :1, then you can use a vnc client to connect to the ip on port 5901.

I don't have kvm installed here now, but I suspect reading through the man pages will highlight some further detail on the vnc option.

EDIT
yes, something like:
[http://www.linux-kvm.com/content/new-vnc-authentication-and-acl-support](http://www.linux-kvm.com/content/new-vnc-authentication-and-acl-support)
might shed some light.

---

