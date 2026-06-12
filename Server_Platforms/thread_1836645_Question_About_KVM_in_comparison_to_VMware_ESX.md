---
title: "Question About KVM in comparison to VMware ESX"
date: 2011-08-31
forum: Server Platforms
---

### Post by Hexxus on 2011-08-31
Hello there!

I've done a bit of searching on this topic and wasn't able to find a definitive answer. So I thought I would ask the experts :)

Here's the scenario, I have 6 virtual hosts at a data-center that are replicating to each other in pairs (So in case one goes down I can boot up the vm on the other host) and they get backed up via VEEAM. 

Recently we're looking at purchasing a SAN that would help take care of alot of head-aches and be a great DR solution.  The problem is that we're looking at over $4K per 3 hosts in software upgrade costs for VMware to connect to this SAN box via iscsi. 

So I did a bit of playing around and found that I really like KVM alot. Seems to do pretty well!

I just was looking for some feedback on these options (or your own response).

A) Stick with VMware and bite the bullet on the software licensing costs because you know it'll work and can do what I want. 

B) Dig into switching over to KVM and figure out how to do such replications and automated backups  and see if fault-tolerance is a possibility (I really don't know I've done a little bit of digging but I would greatly appreciate help in trying to discover this information)

C) Your own response!


I apologize if this is a really huge/vague conception of my problem but I'm just trying to get better information from people whom actually have been in the virtualization business longer then me who might be able to provide their experiences.

These virtual machines need to have a great uptime track record and they are Microsoft boxes. Most are server 2k3 or 2k8 and 2 Ubuntu Server nodes.  

I'm just looking into recommendations from you the experts and the public.

Thank you for your time and I've actually switched from Windows 7 over to Ubuntu at the office :) Whoot! I also apologize I am rather noobish yet but still learning!

---

### Post by rubylaser on 2011-08-31
I use 4 [Proxmox]("http://pve.proxmox.com/wiki/Main_Page") nodes with our 2 SANs here at work, and it's fantastic.  Supports KVM and OpenVZ, takes snapshots, supports live migration, has a very simple web interface, and the best part, it's free :)

Migrating isn't going to be fun, but if budget is an issue, this is a great solution.

---

### Post by Hexxus on 2011-09-01
Cool Thank you very much for the information! :) 

Anyone else in a similar environment? 

Thanks again!

---

### Post by matthew.mattoon on 2011-10-12
I have never been a fan of VMWare, mostly due to their pricing model and the over sale of features which are neat but mostly unnecessary.  That said I am a huge fan of KVM, and currently run almost everything I have on Linux-KVM (Ubuntu 10.10 or 11.04).  The thing that I really like about KVM is the ability to get down and dirty with libvirt and script the crap out of it.  If you are looking for a bit more hand holding from the tool then Proxmox VE is a fantastic solution as well (I use it for the openvz but not the kvm).

I have a ton of articles on KVM on my blog [http://blog.allanglesit.com/](http://blog.allanglesit.com/)

So I think what you are trying to do is definitely doable, however I clearly don't have all the information, so set up some test boxes (which you have probably already done by now - so what did you find?).

-matt

---

