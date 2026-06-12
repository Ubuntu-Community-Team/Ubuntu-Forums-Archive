---
title: "Can I keep using Virtualbox?"
date: 2024-10-19
forum: Virtualisation
---

### Post by marcgala on 2024-10-19
I've heard that Virtualbox is no longer recommended and instead I should use kvm+qemu+libvirt+virt-manager.

However, these seem to require some prior reading and setting up, while I'm already somewhat familiar with virtualbox and it is dead simple to set up. Don't throw things at me please :), but currently I'm just not in the mood to spend some time on tinkering and learning.

Are there any important reasons NOT to continue using VBOX? or is this kvm+qemu+libvirt+virt-manager stack just the currently cool kid? In the latter case I guess it should be safe to still use Vbox for now and return to kvm+qemu+libvirt+virt-manager later.

Note: If this matters, I'm a home user and I want Ubuntu Desktop guest on an Ubuntu Desktop host.

---

### Post by deadflowr on 2024-10-19
Sure.
Just because others like using kvm doesn't mean you have to.

Keep using Virtualbox as long as you want.

> Are there any important reasons NOT to continue using VBOX? 
Not a reason to not use it per se, but one of the reason you see kvm pushed is that the kvm driver is built into the kernel as part of the kernels development.
So it works pretty much out of the box everytime.
One of the issues you might run into with virtualbox is the fact that the driver's are not built into the kernel,
and various kernels might have an odd issue here or there with loading the driver properly.

But that's really the case with most drivers not built into the kernel as the many threads about nvidia can attest.


Edit:
Not to say that it will be a problem only that it could be.
You might be able to run it fine for 50 years without ever having to deal with an issue like that.

---

### Post by TheFu on 2024-10-20
You should use whatever OS and programs you like, that meet your needs.  If that is Virtualbox, great.  If it is kvm+qemu+libvirt+virt-manager, great.  Whatever meets your needs.

The only reason I'd worry about using vbox is their license for the guest additions isn't f/loss.  It is something else that might be fine for you, but if you don't actually read it, you may not know what it requires to be compliant with the license terms.  For most home users, my take on the vbox guest additions license is that it doesn't matter ...   I think people should be 1000x more worried about the current MSFT EULA instead. There are some nasty bits in that one, definitely.

BTW, I switched from vbox and VMware ESXi to KVM/qemu+libvirt+virt-manager around 2010 and have no regrets.  For the most part, virt-manager makes KVM easy to use, once you create a normal Linux bridge manually. KVM also has many more options for storage than vbox supports. That may be important or not at all. Only you can decide.  If you are a home user and place all your fake VM storage onto SSDs, there's probably not much performance to be gained using more advanced storage backends that libvirt supports.

Use what works for your needs. That should always be the rule.

---

