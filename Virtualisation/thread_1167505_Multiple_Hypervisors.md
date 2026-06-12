---
title: "Multiple Hypervisors?"
date: 2009-05-22
forum: Virtualisation
---

### Post by bkozora on 2009-05-22
I'm wondering if I can have two or more hypervisors installed on Ubuntu 9. I'm running in dual boot and am using Virtualbox on Windows XP. I have virtualbox installed on ubuntu but aren't there faster hypervisors available for linux systems? I want to have the greatest performance possible but would also like to launch my virtual machines regardless of the OS im booted into.

Thanks for any suggestions!

---

### Post by SunnyRabbiera on 2009-05-22
well you could try vmware, Vbox isnt the only fish in the sea.
You could probably install every virtual machine software imaginable without it effecting much though, but be careful as some of them change kernel settings.

---

### Post by bkozora on 2009-05-22
I can try it again but I believe before it wouldn't allow me to install kvm and virtualbox. I believe it was a kernel issue. I'll try to install KVM & QUEMU again and post my progress. Thanks for your fast response!

---

### Post by HDave on 2009-05-24
All modern hypervisors utilize CPU extensions to get maximum performance.  Not only can you not RUN two of them at the same time, you can't even have two of them installed at the same time.

You'll have to uninstall one before trying out another.

It's not for the faint hearted or newbie, but KVM will give you the best performance overall, vmware workstation is super easy and "just works", and virtualbox just won the linux user's choice award.

So I don't see how you can go wrong with any of them.  I use KVM on my servers and VMWorkstation on desktops.  I like VMWare because it runs the same machines on both windows and linux...

---

