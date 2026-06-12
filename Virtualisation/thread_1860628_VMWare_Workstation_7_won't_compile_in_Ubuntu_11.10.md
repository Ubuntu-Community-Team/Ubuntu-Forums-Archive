---
title: "VMWare Workstation 7 won't compile in Ubuntu 11.10"
date: 2011-10-14
forum: Virtualisation
---

### Post by Tanker Bob on 2011-10-14
I upgraded from 11.04 to 11.10 yesterday. VMWare Workstation 7.1.4 worked fine in Natty. After upgrading to Oneiric, Workstation tries to compile its kernel modules and fails right away on the virtual machine monitor module. VMWare Player does the same, which isn't surprising since they use the same kernel modules. VMWare Workstation 8 isn't an option since its installation breaks Ubuntu. Is there any patch or work-around to get VMWare Workstation 7 to work on Oneiric?

---

### Post by skatona on 2011-10-15
same problem here. hoping to see a solution ....

---

### Post by Tanker Bob on 2011-10-15
I found the solution process, including at tip for 7.1.5 [on this blog](http://reformedmusings.wordpress.com/2011/10/15/fixing-vmware-workstation-7-14-and-7-15-in-ubuntu-11-10-with-kernel-3-0-0-12/). I worked for me.

---

### Post by skatona on 2011-10-15
> **tanker bob said:**
> i found the solution process, including at tip for 7.1.5 [on this blog]("http://reformedmusings.wordpress.com/2011/10/15/fixing-vmware-workstation-7-14-and-7-15-in-ubuntu-11-10-with-kernel-3-0-0-12/"). I worked for me.

thank you!

---

### Post by tijs14tijs on 2012-04-05
You can always try to boot from an older (vmware supported) kernel, and then 
sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)
apt-get source linux-image-$(uname -r)see [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) for more info
That way vmware will also run, if nothing else works..

---

### Post by dcstar on 2012-04-05
This old thread is no longer relevant.

The Workstation 8 problem that originally broke Ubuntu systems is long solved.

---

### Post by lisati on 2012-04-06
> **dcstar said:**
> This old thread is no longer relevant.

The Workstation 8 problem that originally broke Ubuntu systems is long solved.

Exactly: a solution was found and mentioned in the third post of this thread.

Thread closed.

---

