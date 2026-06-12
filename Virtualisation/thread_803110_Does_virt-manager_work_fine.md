---
title: "Does virt-manager work fine?"
date: 2008-05-22
forum: Virtualisation
---

### Post by Bou on 2008-05-22
Hi,

I'm a total newbie when it comes to virtualisation. Yesterday afternoon was the first time I tried, but it got me so convinced that I decided to wipe my extra partition for testing unstable releases, and do that through virtualisation.

I have two questions, the first one is: is that a good idea? Do any of you guys do it? The second question is, what's the best virtualisation software for that purpose? From my -almost nil- experience, VirtualBox is the one that gave me the best results but I'm a gnome whore, so I'd rather use virt-manager given the chance. Does it work properly on Hardy?

Thanks in advance.

---

### Post by vvlist on 2008-05-22
I'm using it right now. I've used virtualbox and qemu in the past, and so far KVM + virt-manager hasn't thrown me any curve balls. After I installed virt-manager it wasn't very difficult to begin installing XP. It's installing right now and it seems really fast. You don't need a separate partition for virtualization, virtual machines are stored in a large file. Virt-manager makes it for you through the "wizard." Many people use Virtualbox in the Ubuntu community. But I heard somewhere (so it might not be true) that using KVM + virt-manager would be even faster than virtualbox. And if you have used Virtualbox, the experience isn't much different. Give it a try!

---

### Post by Bou on 2008-05-22
Is there anything special that I have to do to get it working? Install any additional package, add myself to a group, and so on?

---

### Post by vvlist on 2008-05-22
I followed [this]("https://help.ubuntu.com/community/KVM") to get started with KVM. virt-manager is the GUI for KVM. Everything you -should- need is on that page. First find out if your CPU supports VT, then go from there.

---

### Post by Bou on 2008-05-22
Whoops!

> If nothing is printed, it means that your CPU doesn't support hardware virtualisation.

Nothing is printed here. Does it mean I can't use KVM? Virtualbox seems to work fine, though.

---

### Post by markba on 2008-05-22
> **vvlist said:**
> But I heard somewhere (so it might not be true) that using KVM + virt-manager would be even faster than virtualbox.

In this benchmark, KVM is almost as fast as native, so it will be faster (or at least even fast) then vbox:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_virt_benchmarks&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_virt_benchmarks&num=1)

> **Bou said:**
> Whoops!
Nothing is printed here. Does it mean I can't use KVM? Virtualbox seems to work fine, though.

This is my main concern: vbox can run everywhere, KVM only on specific hardware (which I currently do not have :-( ). 

As virt-manager cannot be used for vbox (see my feature request [http://www.virtualbox.org/ticket/1019](http://www.virtualbox.org/ticket/1019)), I was looking for using virt-manager with qemu (and the accelarator kqemu). Has anyone experience with this combination?

---

