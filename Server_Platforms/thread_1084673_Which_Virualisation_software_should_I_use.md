---
title: "Which Virualisation software should I use?"
date: 2009-03-02
forum: Server Platforms
---

### Post by kell05 on 2009-03-02
Does anyone have thoughts on whether Xen, VirtalBox or VMware is the better product?

---

### Post by barnex on 2009-03-02
I vote for VirtualBox, it's light, fast, and hassle-free.

---

### Post by TwiceOver on 2009-03-02
I'm going to go with VMWare Server2 since you don't need a Desktop Environment to run it.

---

### Post by Brazen on 2009-03-02
It depends on the application.  I use KVM and it rocks on my servers.  On my laptop though, I use VirtualBox.

So in a server environment that needs maximum efficiency and reliability, I strongly suggest KVM.  On a desktop that just needs to be easy and convenient, I use VirtualBox.

---

### Post by volkswagner on 2009-03-02
Hijack warning!

I to am curious about running VM's.

I have been jumping around in my research, and have landed in a more confused state.

What would my options be running Ubuntu 8.04 Server on an Intel Atom 330.  The Intel 330 does not have VT capability.  I know not heavy iron but it's all I got.  The server is not currently under heavy load.

---

### Post by Vegan on 2009-03-02
My old server lacks hardware to run virtual machines but you can use a pure software stack if you have enough RAM.

My old IBM has 768 MB of memory so I could run a few instances. I only use the machine as a web server appliance so I have no need for it as Apache supports virtual hosts directly.

I have looked at KVM and VirtualBox and both have their followers. I have not looked at VMware as I am too cost concious for that product.

Since I use Ubuntu Server 8.10 I only see KVM as suitable, with a desktop VirtualBox is more user friendly.


:guitar:

---

### Post by volkswagner on 2009-03-02
> **Vegan said:**
> My old server lacks hardware to run virtual machines but you can use a pure software stack if you have enough RAM.

My Atom 330 has 2gig's of RAM (current Max).


> **Vegan said:**
> I have looked at KVM and VirtualBox and both have their followers. I have not looked at VMware as I am too cost concious for that product.

Since I use Ubuntu Server 8.10 I only see KVM as suitable, with a desktop VirtualBox is more user friendly.


:guitar:

I'm guessing you feel the free version of VMware will not alway be free?

VMware was what I have been looking into.  I actually wanted to try it on a Windows Core 2 Duo box, and my Ubuntu server.  Their documentation has me confused.  I still cant determine if VMware server will install in WinXP pro or only server editions (seems like the latter).  It say yes for Ubuntu server so that makes me happy.  The variations also are numerous between server, player, etc., ....further adding to my confusion....  Lots of reading ahead.

---

### Post by PilotJLR on 2009-03-02
Given that you don't have Intel VT, then KVM is out. VMware Server is a good choice... it will always remain free (as in no cost).

I'd recommend using Server 1, not the new Server 2. The Server 2 install takes a lot more overhead, as it has a fancy pants web interface. For your needs, I think Server 1 will be more efficient. It runs on Ubuntu just fine. It runs on an XP host as well, but that is not supported and will throw some warnings during installation.

---

### Post by Brazen on 2009-03-03
I would use qemu with the kqemu module.  I have it running on an old computer without virtualization extensions and it works great.  Since it is supported by libvirt, I can manage it just like I do my newer servers running kvm.

There is a community wiki article on setting up the kqemu module.  It's confusing, but it worked for me on the first try.

---

