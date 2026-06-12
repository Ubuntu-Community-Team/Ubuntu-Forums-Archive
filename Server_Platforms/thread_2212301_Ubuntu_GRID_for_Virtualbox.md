---
title: "Ubuntu GRID for Virtualbox"
date: 2014-03-20
forum: Server Platforms
---

### Post by akash5 on 2014-03-20
Dear Geniuses;

_**Matter:**_

Dear Madams / Sirs;

I own a small business. I am attempting to modernise my IT setup. I have some excess IT resources available at hand. I wish to build the contraption displayed in the diagram below. I would like to take the opportunity bestowed on me through this forum and humbly ask for your help in respect of my project. Kindly guide me as to how should I go about building this grid or cluster. I did read quite a bit about grid and cluster setups, however, the knowledge I seek seems to elude me. Hence, I wish to take help of individuals present on this forum who are far more intelligent and knowledgeable than I am to make sense of the vast knowledge available on-line.

If you could please guide me by letting me know that is this actually possible, then, is it worth doing, if not what alternatives are present. I request you to please list out the steps I should take in chronological order, and please write any links to posts / softwares that I might require to make this happen.

Thank you.

_**Objective:**_ 

Re-purpose some (not so) old servers and desktops to create a HPC / Grid that hosts Virtualbox and runs VMs. These VMs are used as RDP / VNC servers, so we'll call them VSs (apologies for terminology).

_**Diagram**_ (again, apologies for horrible drawing):

[IMG]http://www.image-share.com/upload/2484/212.jpg[/IMG]

_**Explanation to the diagram and objective:**_ 

There are a few old servers and desktops, they shall be made into a cluster, one of them being the cluster controller. The entire cluster will run Virtualbox in a way that ensures best utilisation of resources in the entire cluster. The Virtual Machines along with their virtual hard disks will be stored on a NAS. There is a dedicated switch entirely devoted just to manage this setup, separate from other office network equipment.

_**What I do know:**_ 

basic theoretical knowledge of distributed computing, the fact that there will be an o/s capable of this setup required and there may be a middleware like MPICH or similar required, moderate knowledge of programming in some languages and linux.

_**What I don't know:**_ 

How to actually make it happen, the specific applications required, whether this setup is actually necessary or not, any other alternate way of using the resources properly.


Thank you.

---

### Post by TheFu on 2014-03-20
LT;DR in detail.

I don't think a detailed answer is possible to your many questions. There are just too many moving parts.

Virtualbox is a bad choice for this, IMHO.

Look into **openstack** for most common business "internal cloud" needs. It does have certain hardware requirements to be useful and a central storage setup will make life much easier. Clusters and grids don't really have much use in most businesses that need remote desktops and common servers.  HPC is very specialized work - usually thousands of CPUs are deployed to make it worth the effort for any specific problem. Does you business need that? Nodes drop out of those HPC clusters all the time, so maintaining state across the cluster is important, so are high speed interconnections.

There are competitors to openstack - [http://blogs.enterprisemanagement.com/torstenvolk/2013/10/11/war-stacks-openstack-cloudstack-vcloud-amazon-ec2/](http://blogs.enterprisemanagement.com/torstenvolk/2013/10/11/war-stacks-openstack-cloudstack-vcloud-amazon-ec2/) .
Also the amount of MS-Windows in your solution will matter greatly.

If you have less than 50 physical systems, a simple KVM + virt-manager setup will be much easier to manage than an internal cloud stack.

---

### Post by akash5 on 2014-03-21
Dear Sir;

Thank you for your reply, it is highly appreciated. As per your advise, since I have less than 50 physical systems, 32 to be specific, to make the HPC, I shall avoid going on this path. I shall stick to running them all on Linux separately and using VirtualBox / KVM to run the guest Windows O/s for easy BCP DRP through common storage of VMs and VDIs. I shall study OpenStack and see how I can make use of the same, and come back to bother geniuses such as yourself if I get into trouble with OpenStack XD.

Regards.

---

### Post by TheFu on 2014-03-21
I'm not a genius. Just been doing this stuff a long time. There are many others who are much smarter than me here and everywhere else. I'm an idiot about many things.

I'd skip Oracle virtualbox completely. In a corporate environment, license costs are an issue for strong consideration. If you install the "guest additions" and that is pretty much mandatory for desktop VMs, then your company needs to pay Oracle.

Check out **cobbler**, **ansible** and how they integrate with **libvirt** for management of VM hypervisors and client VMs. libvirt is a tool you don't know you use, but it makes controlling most VM hypervisors possible from a central interface like virt-manager. [http://blog.jdpfu.com/2013/11/03/setup-kvm-virtualization](http://blog.jdpfu.com/2013/11/03/setup-kvm-virtualization) attempts to explain.

OpenStack is just 1 option - there are 10+ others.  I only have 30 VMs here, so never needed openstack. The learning curve is steep and the overhead to the infrastructure setup is great. Many metro areas have openstack user groups.  A business partner has done an openstack design and deployment with over 2,000 physical hosts split between multiple data centers in different parts of the country. The networking got ugly. The management of each VM got ugly - puppet seems to be the tool of choice, but sucks in many ways.

Why MS-Windows for the guests?  I've provided remote desktops using Ubuntu-LXDE over NX for years. It works great for productivity stuff, plus hundreds of users can be hosted on a single, shared, VM. That means sharing files and collaboration inside some word processing tools is trivial.

LTSP is something you might enjoy for remote desktops too.

---

