---
title: "Best Virtualization Solution"
date: 2010-12-02
forum: Virtualisation
---

### Post by mark_smith111 on 2010-12-02
I am in process of putting a virtualization plan in place.  Wondering, from pure virtualization perspective, which hardware vendor provides the best virtualization solution.  Will like to know if any have had any experiences using virtualization on DELL hardware, SUN, HP or IBM. Also wondering, if any of you were able to get a decent discount from any of these hardware or vitualization software vendors.  Appreciate your help

---

### Post by CharlesA on 2010-12-02
It really depends on what you want to use virtualization for.

At the place I work, we are running an ESXi server that hosts VMs. At home, I just use VirtualBox running headless.

---

### Post by thatguruguy on 2010-12-02
I have no idea what you're talking about. What discount, exactly?

I run VirtualBox on my Dell, for the occasional windows app I need.  VirtualBox didn't cost anything, and Dell didn't send me money to use it.

---

### Post by JonM33 on 2010-12-02
> **mark_smith111 said:**
> I am in process of putting a virtualization plan in place.  Wondering, from pure virtualization perspective, which hardware vendor provides the best virtualization solution.  Will like to know if any have had any experiences using virtualization on DELL hardware, SUN, HP or IBM. Also wondering, if any of you were able to get a decent discount from any of these hardware or vitualization software vendors.  Appreciate your help

The last company I worked for ran VMWare on HP servers.

---

### Post by Groodles on 2010-12-05
> **CharlesA said:**
> At the place I work, we are running an ESXi server that hosts VMs. At home, I just use VirtualBox running headless.

I'm very similiar.

We use ESXi in the corporate VM hosting envirnment at work.

I also use VirtualBox at home on Windows and Ubuntu for testing.

I also have a shared lease on a server which runs 4 VMs under VirtualBox (Debian 5 host OS) which obv runs headless.  (We use phpVirtualBox for administration, protected by https).

---

### Post by CharlesA on 2010-12-05
> **Groodles said:**
> (We use phpVirtualBox for administration, protected by https).

I have phpvirtualbox set up the same way. I just wish they'd get the authentication part worked out, since I'm currently using .htaccess to password protect the phpvirtualbox directory. It works, but I am sure there are better ways of doing it.

---

### Post by Santos1204 on 2011-01-11
@ work it's all vmware, which seems ok, and quite simple to use and does have some nice disaster recovery stuff for a corporate environment. 

@ home its KVM/QEMU/virtualbox depending on the O/S needed, I find virtualbox is better for windows/gui based O/S and KVM/QEMU better and simpler for running non gui based O/S. (although the later might just be my incompetence :) )

---

### Post by stanz on 2011-01-20
> **Groodles said:**
> 
I also use VirtualBox at home on Windows and Ubuntu for testing.

I'm here looking for info on which VM to use also for testing Ubuntu releases.
I know we all have our personal preferences, but does it matter to the guys upstairs,
when results are posted, which VM the test was ran in?
:wink:

I installed TestDrive and tinkered with preferences--hit load--and QEMU started-up!
This of course, before I thought to grab VirtualBox.
So I'll try it out and look for...The Best Virtualization Solution!  :razz:

---

### Post by CharlesA on 2011-01-20
It doesn't matter, virtulization is virtualization.

---

### Post by CharlesA on 2011-01-20
It doesn't matter, virtulization is virtualization.

---

