---
title: "hosts.deny denies all connections"
date: 2012-11-29
forum: Security
---

### Post by dellett on 2012-11-29
Hi all, 

I was trying to set up the hosts.deny/hosts.accept files for a virtual machine which I can only access through ssh and I stupidly set up the files as follows:

hosts.deny
ALL:ALL

hosts.accept
localhost 127.0.0.1

So you can see, I can't log in to the VM at all. Since it is a VM and I can't just log on to the physical machine, do I have any way of getting in to the system and/or changing the hosts.deny file? Or am I just going to have to get a new VM?  If anyone has any ideas, feel free to share.

---

### Post by CharlesA on 2012-11-29
Since it's a VM, I assume you have access to the host? Just login to the console and clear out the hosts.deny file.

---

### Post by Hungry Man on 2012-11-29
Is this a VM hosted elsewhere? You'd have to talk to the administrator/ whoever you're paying. If it's a VM you own/ that you have access to... just log into it and deal with it locally.

---

