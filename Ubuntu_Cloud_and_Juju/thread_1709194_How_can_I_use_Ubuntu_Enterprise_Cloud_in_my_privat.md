---
title: "How can I use Ubuntu Enterprise Cloud in my private infrastructure?"
date: 2011-03-17
forum: Ubuntu Cloud and Juju
---

### Post by fernandofat on 2011-03-17
Hi,

I am an experienced system/server administrator trying to understand how can I use Ubuntu Enterprise Cloud in my private infrastructure.

I already Googled a lot and all documentation I found has quite the same approach telling the concept, architecture, elements, components but none of them has a practical approach telling what kind of servers it supports and if it is possible to move them into UEC.

Today I have over 80 different servers (windows and linux; physical and virtual) with many different applications I think that moving these servers into UEC would change (for good) the way I manage servers today wich is the traditional management.

So for an example is it possible to migrate my Active Directory server into the UEC?

At this moment I am not interested in technical details just a practical answer on what kind of servers I can host on a UEC environment.

(if I posted on the wrong forum please let me know.)

---

### Post by kim0 on 2011-03-18
UEC doesn't "support" running Windows VMs. You can convince it to run them though with some hacks. Eucalyptus EE does support Windows as per: [http://www.eucalyptus.com/products/eee/features](http://www.eucalyptus.com/products/eee/features)

You might also want to look at other datacenter virtualization tools, like running plain KVM virtualization which supports Windows and can be managed with virt-manager

---

### Post by fernandofat on 2011-03-18
kim0, thanks for the reply.

How about migrating my Fedora Core 14 Squid proxy server to UEC? Is this possible?

---

### Post by kim0 on 2011-03-21
Well yes absolutely, you see UEC is really a management layer (sometimes called orchestration layer) on top of "normal" VMs. So at the end of the day, it's running virtual machines under KVM hypervisor, and yes of course you can run Linux/squid under KVM

---

### Post by fernandofat on 2011-03-21
Yes kim0 now I'm starting to understand but I have another (basic) question.

Technically how does UEC scale up the virtual server resources (memory for example)? The management layer duplicates the virtual machine and the two VM's work as one? Or the memory amount is increased inside the VM?
Does the memory size change for the operating system inside the virtual server?

I would like to say that I apreciate your attention and I'm sorry for such basic questions but I really didn't find these kind of information on the UEC public documentation or any other related hyperlink and for now I'm unable to create a test lab for some experiments and some answers.

If these kind of informations are available on the Internet please feel free to point me at the right direction and I will continue my research.

---

### Post by kim0 on 2011-03-22
I understand your need to understand the basics, somehow they're always assumed to just be known somehow :) To answer your questions, you get scalability and redudancy in "cloud" through launching multiple virtual machines. The memory of each VM does NOT grow larger than the memory of the host it is running on. i.e. you can never "merge" the RAM of two hosts and assign them to one VM. Cloud is really all about smartly managing VMs, if you rewrite your applications to make-use of several VMs in parallel, it becomes very useful. However, with respect to standard applications, cloud is no silver bullet to solve scalability or reliability issues

---

### Post by fernandofat on 2011-03-23
Well kim0 that was a very good answer. Now I understand that applications must be rewritten or adapted to benefit from "cloud" technology.

I still got some questions but I'll try to figure out on my own.

BTW today is going to happen the Cloud Computing 101 IRC event, I'll try to participate. :D

---

