---
title: "kvm consumed 100% CPU is it regular"
date: 2010-06-14
forum: Virtualisation
---

### Post by tapas_mishra on 2010-06-14
I am using 
Dell Server R710.Ubuntu 10.04 Server Edition.
I have 5 websites running on it.None of them is known to world.All of them are static pages which are under development.
Today morning I noticed I could not SSH into the Ubuntu server normally.
Upon executing top it showed 100% resource consumption by kvm and apache2 consumed 76% of memory.

A snapshot is [here.]("http://farm5.static.flickr.com/4013/4699631854_1f3c08622d_b.jpg")

What could have been the reason and what should I check?

---

### Post by wcorey on 2010-06-14
This looks like on that box you have a virtual machine installed and running. KVM appearing as the process running merely means there is a virtual machine running. From the host (your Dell box) it does not have visibility into the VM to know what processes are actually running, the aggregate of which are running at 100% of cpu.

In other words, I am running a cloud and on the node controller I can have, say, eight simultaneous instances of a machine image running simultaneously. If I were to run top on the node controller hosting those running instances, it would likely show the eight kvm instances running somewhere towards the top of the top output.

I am unaware of anything that would cause an idle VM to show 100% cpu. Can you shell into that VM and issue the top command there?

---

### Post by tapas_mishra on 2010-06-16
It is not possible to shell into any VM as you said in this situation.
The VMs could not be reached when CPU utilization on Dom0 was 100%.
Any thing else to try?

---

### Post by TheFu on 2010-06-17
Can you connect to the console of the VM?

---

