---
title: "VM on desktop cluster"
date: 2008-12-03
forum: Virtualisation
---

### Post by Alexis Phoenix on 2008-12-03
This may be a little OT.

Ok, this is only in my head and on some bits of paper at the moment, but I want to build a kind of "desktop cluster", which would then run a virtual machine and completely hide the fact that it is made of several nodes.

The hardware would be of average specification, something like low-end ITX boards or high end PC104, the storage for each node would be very minimal - something like CF to carry the OS and swap, and it's quantity of RAM being a little on the low side (the final cluster would still appear to have plenty of RAM I believe), and the guest OS would be the users choice of desktop OS.  There would be an external user-space storage device.

Are there any thoughts from the community about what kind of VM and clustering software I should be looking at?  I know about Mosix and Beowulf but very little of the implementation.  I have been playing around with KVM/QEMU but it would be good if I could provide more flexibility and transparency.

This is in it's very early stages, so any thoughts would be appreciated.

TIA
Alexis Phoenix

---

### Post by PilotJLR on 2008-12-03
Virtualization isn't the solution for you... KVM, Xen, VMware, etc etc all require a guest to be run on a single node at a time.

Parallel computer (like Beowulf) would require the apps being run to be written for that purpose, so this would be a complex and probably custom project.

---

### Post by PilotJLR on 2008-12-03
Unless I misunderstood you... do you WANT to aggregate the nodes together and do parallel computing? Or are you planning on running a VM on a single node at a time?

The commercial solutions for this would be VMware View and Citrix XenDesktop. With a small user count, you can get away with just KVM and manually establishing RDP or VNC connections from endpoints to the VM's.

---

### Post by Alexis Phoenix on 2008-12-05
Mmm, thanks for the feedback - I obviously need to do a lot more reading!  Unfortunately I've got this great idea but know very little about clustering or VM's, just that if it can be made to work it is the logical solution for me.

I want to create a transparent cluster with a small number of nodes and a very low number of users.  The very little I've read about Mosix makes me think this may be possible as each node can run as a "normal" computer, and shove processes off onto other nodes as it needs to, which is what I think I want.  I don't actually know anything about Beowulf!  However, I was thinking that a cluster-aware VM would enable normal applications to be run with an ever-expandable supply of resources!

I think it's more of cluster-capable network than a true cluster, as I think about it, however I definitely want to be able to add nodes which do nothing more than increase the available processing power and memory.

The VM side of things is purely so that a user can use the operating system of his or her choice and have no knowledge of the existence of the cluster, so the underlying o/s would need to be little more than kernel, shell, toolkit and system essentials.

I guess you now think I'm completely mad, so I'll stop there!

Once again, thanks for the feedback
Alexis

---

### Post by Morten ML on 2009-09-29
Hi Alexis (and others)

I dont know if this is still relavant, but i like your idea... had the same one myself.
Here is what i have done so far.

Set up a clusterknoppix cluster
installed virtualbox - OBS this didn't seem to work. I was not able to migrate the proseses from the guest OS

Set up a fedora (8) and compiled the mosix kernel for that. Same thing.
Tried with Qemu and xen - none of them worked.
Xen is linked to the hardware and qemu would not migrate...

Currently looking into oracle vm - but i am not sure if its a virtual cluster or a cluster with xen capabilities.

There is also something called cloud xen - not ready yet - but looks very interesting.

If anyone is still interested in this please post.

---

### Post by fokje on 2009-12-04
Still interested. I am sysadmin at a school with 100 PC's. What I'd like to do is, I think, the same as you guys: build a giant cluster and run a virtual image on it. I have workstations, P4 with 256MB RAM. If I were able to run all of these together in a cluster, you should be able to login via RDP or some such and connect to a virtual image residing in that same cluster...that would mean you get enormously fast virtual machines because of the 100 workstations, only 25-40 of them are being used at the same time, so you would have the CPU en RAM of the other unused machines available. But! Is it possible??? I'm looking at centos 5.4 with KVM and SPICE now (spice being a sort of RDP but with allegedly great multimedia capability). It would be fantastic to be able to build a network like this...Although with full virtualisation it can't work. 
Keep me posted!

---

### Post by Alexis Phoenix on 2009-12-05
I think this probably counts as a bump - but...

I actually put this project to one side after reading the responses to my original post - just not had the time or resources.  If enough people are interested in this maybe it would be possible to draft some kind of spec to work towards?

My original project was to develop as maybe a commercial proposition, kit that would have been really cool a few years ago, but I don't think it's really relevant in that context anymore, since PC's have become so powerful now.  Basically it was an expandable modular desktop computer where every (low cost) module is a computer in it's own right, people that bought into the idea would be able to follow an upgrade path where their original kit need never become redundant.  The modules would have been like oversized external drives in terms of dimensions and just stack up like hi-fi separates, with a common PSU.  I more or less worked out the hardware side of things but never the software, beyond what I posted here - hence my original question.

Anyway, rant over.  It's probably going to keep me awake all night thinking about it now.

Alexis

---

### Post by PilotJLR on 2009-12-05
I doubt anyone minds a bump after one year.  :-)

If you haven't already, you might want to read over the Beowulf FAQ, specifically this question: [URL="http://www.beowulf.org/overview/faq.html#4"]http://www.beowulf.org/overview/faq.html#4
[/URL]

This isn't a hardware issue, it's a question on what workloads you want to run over the entire grid. Parallel computing requires apps designed for the purpose, and most workloads aren't. A whole lot of apps for desktop users (both linux and windows) aren't even multi threaded, so they won't even run on more than one core on a single proc.

As an aside, I'm not suggesting to give up and follow the crowd, but also consider that a lot of people feel that virtual desktops will be the future of desktop computing. Read up on Citrix XenDesktop or VMware View to get all the marketing info. If this becomes mature and widespread, then desktop PC's will become quite rare (replaced by thin client endpoints and laptops).

---

### Post by Alexis Phoenix on 2010-02-01
I am suitably informed and inspired.  Many thanks.
Alexis

---

### Post by Morten ML on 2010-05-14
Back again

I'll second that opinion about being ran over... its too much work for "hobby time".

But here is a sum of what i know.
Clusterknoppix - very old but could migrate. led to mosix.
Mosix can only migrate processes not threads. 
There is a kernel of opensuse (old, though) outhere with both mosix and xen - I never got it to work though, and i think it is too late now.
It is possible to migrate an _entire_ vm using xen on a cluster (think you can use whatever cluster you want - just have to define DOM0 across it and loadbalance it OBS not easy)
Ubuntu Eucalyptus should be checked out - i hope they implement load balancing!

My final conclusion on this was to buy a new computer - it saves space. Then leave all this migration stuff to the pros ;) Fingers crossed for eucalyptus.

Ironically everybody seems to be implementing multi threaded code now... when load balancing clusters seems to be a thing of the past...

---

### Post by jerim79 on 2012-02-08
Yes, I know this thread is over two years old, but I didn't want to start a duplicate thread.

I have six Optiplex 960 desktop machines. I want to run VMs to serve terminals. I was hoping that I could first cluster the six desktops together using Ubuntu. Basically this would give me a decent server from six desktop machines. Next I would install some sort of VM software through Ubuntu to create my virtual machines.

What I am wanting from the cluster is basically to use a RAID 5 type scheme on the six machines with files spread out over the six nodes. If one node goes out, I can replace it with another machine and it will rebuild the data. I understand technologies parallel processing technologies such as PVM but that just parallels the processing and not the data storage. 

Is this even possible? If so, can someone point me in the right direction? I am not sure if hypervisor clustering is the solution. Pretty sure a Beowulf cluster isn't what I am looking for.

---

### Post by &#23389;&#36154;&#22674; on 2012-02-23
> **jerim79 said:**
> Yes, I know this thread is over two years old, but I didn't want to start a duplicate thread.

I have six Optiplex 960 desktop machines. I want to run VMs to serve terminals. I was hoping that I could first cluster the six desktops together using Ubuntu. Basically this would give me a decent server from six desktop machines. Next I would install some sort of VM software through Ubuntu to create my virtual machines.

What I am wanting from the cluster is basically to use a RAID 5 type scheme on the six machines with files spread out over the six nodes. If one node goes out, I can replace it with another machine and it will rebuild the data. I understand technologies parallel processing technologies such as PVM but that just parallels the processing and not the data storage. 

Is this even possible? If so, can someone point me in the right direction? I am not sure if hypervisor clustering is the solution. Pretty sure a Beowulf cluster isn't what I am looking for.

Hi jerim79 and others! I’m glad to see this thread. these days i am also finding ways how to install one system in more than one computer,and they can work synchronously&#12290;
    I come from China&#12290;I asked this question in the “Ubuntu Forum for China”&#65292;at here&#65306;[http://forum.ubuntu.org.cn/viewtopic.php?f=65&t=364717]("http://forum.ubuntu.org.cn/viewtopic.php?f=65&t=364717")&#12290;But no one could give answer&#12290;
    Finding this topic here&#65292;though no HOW-TO&#12290;But find some meaningful ideas.
    Thank you !

---

### Post by bipinbachhao on 2012-02-24
@jerim79

PVM is a parallel programming interface like mpi(Message passing interface).
Both the PVM and MPI actually gives the multiple machines facility to talk to each other inside the parallel program, so they can share certain value and solve the big sized problems collectively.

The PVM by name parallel virtual machine but its not like Xen, KVM.

You want to virtualize the storage or the servers?

---

