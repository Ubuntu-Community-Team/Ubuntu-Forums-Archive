---
title: "Suggestion on selecting virtualization software"
date: 2009-05-10
forum: Virtualisation
---

### Post by satimis on 2009-05-10
Hi folks,

Host - Ubuntu 8.10
Guest - Ubuntu 8.10
Mail servers.

I'm prepared to built a new Virtual Machine testing server consolidation.  I have run Xen before it works without problem.  Also I have run OpenVZ.  It has some problem running Ubuntu on it.  This time I'm prepared using Vserver.  Could you please advise whether there are problems running Ubuntu on it?.  What other suggestion on virtualization software you folks will suggest?  TIA

B.R.
satimis

---

### Post by veloce on 2009-05-11
If your host hardware supports it, kvm.  I'm really liking it (though the only thing I'm comparing it to is vmware server).

---

### Post by satimis on 2009-05-12
> **veloce said:**
> If your host hardware supports it, kvm.  I'm really liking it (though the only thing I'm comparing it to is vmware server).
Hi veloce,

Thanks for your advice.

I ran KVM/QEMU before.  What I like is I can run M$Windows on KVM.  I can't run Windows on VServer, Xen and OpenVZ.  I don't run M$Windows OS only for testing.  For Windows applications, if any, I can run them on wine.

Before I tried VMWare a while.  Although it is FREE I prefer helping the Open Source community.  Actually users help the developers to certain extent reporting bugs, raising suggestions, etc.


B.R.
satimis

---

### Post by bodhi.zazen on 2009-05-12
> **satimis said:**
> Hi folks,

Host - Ubuntu 8.10
Guest - Ubuntu 8.10
Mail servers.

I'm prepared to built a new Virtual Machine testing server consolidation.  I have run Xen before it works without problem.  Also I have run OpenVZ.  It has some problem running Ubuntu on it.  This time I'm prepared using Vserver.  Could you please advise whether there are problems running Ubuntu on it?.  What other suggestion on virtualization software you folks will suggest?  TIA

B.R.
satimis

What problems are you having with Ubuntu in OpenVZ ?

If you like I have Ubuntu 9.04 templates (32 and 64 bit). I built them myself , but they work.

---

### Post by satimis on 2009-05-12
> **bodhi.zazen said:**
> What problems are you having with Ubuntu in OpenVZ ?

There are lot of problem on the VE created with their ostemplate.  In my case, Ubuntu 8.04, the problem first started on Shorewall, iptables, clamav-daemon, remote mail client unable to login, etc.

> 
If you like I have Ubuntu 9.04 templates (32 and 64 bit). I built them myself , but they work.
Thanks please advise me the URL to download Ubuntu 9.10.  I'll build the ostemplate myself.  Thanks

Previously I built my own ostemplate.  Later I found their ostemplates.  I used them instead for convenience.  I won't use their ostemplates anymore.

B.R.
satimis

---

