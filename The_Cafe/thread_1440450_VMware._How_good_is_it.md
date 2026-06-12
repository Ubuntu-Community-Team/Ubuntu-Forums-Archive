---
title: "VMware. How good is it?"
date: 2010-03-27
forum: The Cafe
---

### Post by yester64 on 2010-03-27
I am thinking now for a couple of weeks what solution might be the best for running Windows side by side of Linux.
Now, to me cost is not an issue. If i need to pay for a solution that is fine.

I read about Vmware and i am curious how good it is. Since i understand that it lets you run windows within Linux, it sounds great.
But how is it in reality. Can you play games within that or is limited to regular applications?
And what machine do you need?

I considered to dual boot. But that would mean that i need to reconfigure my harddrives since they all use ext4. Plus it is a lot of work.

Does somebody use VMWare and can get me some advice?

---

### Post by samalex on 2010-03-27
I'd suggest checking out VirtualBox.  I've been using it for a while with Windows XP and it works great!  And it's free :)

Sam

---

### Post by new_tolinux on 2010-03-27
I use VMware server 2 and it's free also.
I used VirtualBox before ("non-free"-distribution, free of charges, but not open source)

To me VMware is the only solution, after trying VirtualBox and VirtualPC (Microsoft). But that is only because I use NetWare (Novell) and after trying that only worked in VMware.
Besides that: VMware has the option to run a virtual machine from another PC, where VirtualBox is limited to run on the PC where that VirtualBox-machine resides.

After (yet) about a month running VMware and before that running VirtualBox for more than a year.... if remote-use is not at your wish-list, virtualbox has the advantage that you run virtualbox when you need it, where VMware server starts at boot (virtual machines _don't_, unless you change that option).

Edit:
Virtualbox has a repository. VMware doesn't.
VMware needs some tweaking before it runs well on Linux, but there's a working tutorial [here](https://help.ubuntu.com/community/VMware/Server)

---

### Post by naru2bon on 2010-03-27
I'd go for VMware but it still depends on your computer specs. If you think your desktop can crunch that much load then vmware is for you feature-wise otherwise it'll be VB because of its user and pc friendly features, not sure if you can play games with vmware though, haven't tried windows on the latest vmware version yet, google it or wait for someone to confirm it.

---

### Post by yester64 on 2010-03-27
that sounds great. I will try both of them out.
I just don't wont to dual boot and rather have it within linux.
I thank you all for the input. :)

---

### Post by swoll1980 on 2010-03-27
I always liked VirtualBox better.

---

### Post by KiwiNZ on 2010-03-28
I use VM Ware , it is great .

---

### Post by eksasol on 2010-03-28
I can't seem to get VMWare Player 3 to work correctly on linux (Ubuntu/Fedora). It gets extremely slow and freeze up the access to the harddrive. On Windows it works, but that's pointless.

I like Virtualbox, but it would be nice to have better graphic support and Aero.

---

### Post by juancarlospaco on 2010-03-28
> **new_tolinux said:**
> 
where VirtualBox is limited to run on the PC where that VirtualBox-machine resides.


no

*can do that with NFS or SSH*

---

### Post by Chronon on 2010-03-28
> **new_tolinux said:**
> 
Besides that: VMware has the option to run a virtual machine from another PC, where VirtualBox is limited to run on the PC where that VirtualBox-machine resides.


This is in the changelog for VirtualBox 3.1.0:
[LIST]
[*]Teleportation (aka live migration); migrate a live VM session from one host to another (see the manual for more information)
[/LIST]

---

