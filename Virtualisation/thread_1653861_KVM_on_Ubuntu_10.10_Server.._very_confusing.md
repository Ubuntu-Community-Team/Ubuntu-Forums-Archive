---
title: "KVM on Ubuntu 10.10 Server.. very confusing"
date: 2010-12-27
forum: Virtualisation
---

### Post by hdanielb on 2010-12-27
I've been using Ubunu desktop for quite a time, and could install virtualbox in it, and emulate several OSes without problem.

Now I'm looking for a way to install Ubuntu Server in my machine, because I read that I can virtualize with just a little footprint in the system using the built-in KVM.

I have set up one of my system partitions to install Ubuntu server. I already did this.. but .. now what????

The only thing I have is a command line, and a lot of confusion, between kvm, qemu, kqemu, virtinst, and a huge man page for qemu, with almost infinite options. Besides the tests I made to install xp using the following lines:

qemu-img create wxp.img -f qcow 6G
kvm -no-acpi -m 256 -cdrom winxp.iso -hda wxp.img -boot d

and it doesn't work! It takes me to some kind of reboot with a freezed start.

Is there some kind of menu-driven utility to have this working? I don't want graphic environment in my host, but of course I will need for my guests!

And, supposing I could have this running, how do you switch to the host console again to start another guest?

PLEASE HELP WITH THIS!

---

### Post by bodhi.zazen on 2010-12-27
Read the man page, it is long, but quite informative =)

See also:

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

[https://help.ubuntu.com/community/KVM/Directly](https://help.ubuntu.com/community/KVM/Directly)

If you do not have X on the server, you need to run w/o X

[http://blog.bodhizazen.net/linux/how-to-run-kvm-without-x/](http://blog.bodhizazen.net/linux/how-to-run-kvm-without-x/)

I have several blog posts on running KVM =)

Other then that, hard to tell from what you posted. Could be too little ram allocated to the guest. Could be you did not make a hard drive image or do not have a winodws .iso, please post any error message you are getting.

You can use other tools, virtmanager over ssh =)

---

