---
title: "KVM - use root or user?"
date: 2010-03-30
forum: Virtualisation
---

### Post by gunksta on 2010-03-30
I want to use KVM to run a couple of WindowsXP and one Windows7 instance. I hate ActiveX with a passion, but virtualization seems to be the best way to dodge the issue so I can run Linux at work. 

After installing KVM, virt-manager, etc, I read several tutorials/wikis regarding KVM. It's a little more complicated than VirtualBox, but not that bad. I also looked at virt-manager. I started virt-manager as $USER and as root. When creating a new system, they are _nearly_ identical. But, I noticed that I had more options with networking if I installed as root, and some of the stuff I read seemed to imply that this is the better path, so I installed WindowsXP, using virt-manager, as root.

I confess - I am leery about running anything as root -- **Have I made a mistake here?**

In addition to being a little gun-shy about what I've done -- I have noticed a small but significant problem. If I start virt-manager as $USER, I can not see my vm. If I start virt-manager as root, I can see the vm, but it can't start. It tries and eventually dies with a domain socket error.

However, the vm is just fine. If I run sudo kvm /var/lib/libvirt/images/WinXP.img, it works! But, I have to run KVM as root, which may be really stupid on my part.

If I start the vm from the commandline, it works but I get an error stating:

pci_add_option_rom: failed to find romfile "pxe-rtl8139.bin"

I have abolutely not idea if this is related to running kvm as root or if it is separate entirely. I have tried Googling, but can't find many thorough discussions of the pros/cons of running kvm as root or in user-space.

Thus, once again I turn to the gurus here at the ubuntu forums. I appreciate any information/wisdom/guidance you may have. I am especially interested in learning more about running KVM as root and how to use virt-manager to start this silly thing. Eventually I want it to be very very easy for someone to start/stop, without the need to drop to the CLI. If I need to move this image to user space, I am very willing to explore that option.

---

### Post by gunksta on 2010-03-30
Apparently - I somewhat mis-spoke in my first post.

Sometimes, when I start my computer I can use virt-manager to start/stop my vm, without needing to use root. But, sometimes I can't. I don't know why.

However, I can not apparently use kvm to directly start the vm unless I am using root.

I should also note that when I installed kvm I did set $USER to be in the groups libvirt and kvm, which is why I am confused about the permissions thing, but perhaps I simply need to be enlightened.

---

