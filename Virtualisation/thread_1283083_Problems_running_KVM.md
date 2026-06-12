---
title: "Problems running KVM"
date: 2009-10-05
forum: Virtualisation
---

### Post by gyz on 2009-10-05
Hi, I have two computers at home which are pretty much always on, my web/mailserver and my mediacenter PC. To cut powerusage I thought it'd be a good idea to merge the two and since my mediacenter pc is more than powerful enough to do both jobs I was thinking of using KVM to run my server tasks on a ubuntu desktop install for my mediacenter needs.

After installing KVM and creating a domain I tried to start it through virsh -c qemu:///system start ubuntu which promptly made my computer hang. Hoping I made some horrible configuration mistake I trieds several things:

[LIST]
[*]Starting kvm from the command line without arguments
[*]Installing ubuntu 9.10 beta
[*]Installing ubuntu 9.10 server beta
[*]turning off nvidia restricted drivers
[/LIST]
but all lead to the same thing: a machine I had to turn off by holding the power button for several seconds.

The processor in my machine is definitely capable of Intel-VT (Q9400) and Virtualization is enabled in my BIOS so that's not the problem.

Could this be a hardware problem?

---

