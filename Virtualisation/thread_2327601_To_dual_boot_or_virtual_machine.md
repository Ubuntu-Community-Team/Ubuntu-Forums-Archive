---
title: "To dual boot or virtual machine?"
date: 2016-06-12
forum: Virtualisation
---

### Post by jake-swensen on 2016-06-12
I am transitioning from using only MS Windows to using both Windows and Linux for practical home use (office apps. suite, file and printer sharing, basic gaming, internet access, Netflix).

To allow usage of a great number of such applications (more freedom), minimize the weekly time spent in configuring and maintaining the system (fixing, backing up, updating), and other factors that I may be unaware of, should I:

(A) install both operating systems as primary and dual boot or
(B) install one OS as primary and create the secondary OS as a virtual machine?  Which OS should be primary?

---

### Post by SeijiSensei on 2016-06-12
Most games won't run well in a virtual machine.  So I have both arrangements configured, a dual-boot with Linux and Windows, and VirtualBox VMs on both sides that run the other OS.

---

### Post by jake-swensen on 2016-06-12
So in what kinds of scenarios do you use the VMs?  I mean how would they be helpful for someone who already has a dual boot setup?

---

### Post by Omar_Jair on 2016-06-12
VM could be used for testing purposes, if you wanna learn the basics, play or experiment with the system or so on, however if you use it as a primary OS you can extract most of the juice out of your computer, I would reccomend ubuntu on a VM if you dont know much about it or use it on a dual boot with Windows (pssst: ubuntu is great).
I would use a VM when i test an OS to see if i like it, of course I wont have like 7 OS on my computer but its good to test or use any other OS for fun like Puppy Linux or DSL

---

### Post by jake-swensen on 2016-06-13
Thanks.  Now I understand some of the reasons for using VMs.

---

### Post by MAFoElffen on 2016-06-15
One more sidenote plug for virtualizations...One my old dev machine, that use now mostly for my server management and for support for this forum... That machine is dual-boot (actual more than just dual).

On Ubuntu and on Winodows, I have VirtualBox and VMware Player installed. That way, if in either, I can load up an opposite flavor VM, to be in either OS at the same time and pop from one to another. Also on each side, I have virt-manager loaded, so I can look at my KVM and Xen Servers. 

On the Windows side, I have putty loaded, but would rather load a VM to use a Linux terminal session, to ssh into my servers. Also VMware client only works on Windows... Windows Remote Desktop Manager sessions to a Hyper-V Server and it's VM guests, well M$ thinks they are the only one that matters. I could setup differently (Spice or VNC), but no matter.

Even though I do most things using virtual's, where the host I'm running from (local or remotely) is shielded from it's VM guest sessions ... some things just run "faster" on iron. If I'm gaming (on either Linux or Windows) games, and gaming controllers are more reactive on iron. That is why I still keep that machine as a multi-boot system.

Another plus for virtualization is virtual networking. That is a big plus to segment a VM guest from the main stream. You can setup virtual network to include or exclude VM's from the rest of your network.

VM's allow you to reduce your physical footprint. I used to have separate servers, to do different jobs. I reduced my footprint by migrating them to Virtual Hosts. If I need another server to test on or to do a different job, I "create" one.

---

### Post by SeijiSensei on 2016-06-16
> **MAFoElffen said:**
> VM's allow you to reduce your physical footprint. I used to have separate servers, to do different jobs. I reduced my footprint by migrating them to Virtual Hosts. If I need another server to test on or to do a different job, I "create" one.

I reduced my physical footprint by migrating my servers to [Linode]("http://www.linode.com/").  $10-20/month is a small price to pay so I don't have to deal with cooling, power outages, Internet outages, bandwidth limits, backups, etc., etc.  Commercial Internet connections are still pretty pricey.  I had one with Verizon at nearly $100/month.  Now I have a residential connection and virtual servers located in New Jersey and California.

You can spin up a VM in minutes, and you only pay for the length of time it is in operation.  I've created a server and torn it down in the same day and got charged nothing for it.

---

### Post by jake-swensen on 2016-06-16
Many good points.  I too use PuTTY for ssh and I was thinking about maybe installing Cygwin but a Linux VM might be much better.  For my next project, a home server (combined file server, print server, media server Subsonic, backup server etc.), would it be better to make a real server?

Oh, I guess I already have VMs, then, because I recently signed up with Digital Ocean to try out a LAMP stack with ownCloud etc.  For me DO is easier to use compared to Linode but I'm not sure which service offers more advanced features.

---

### Post by SeijiSensei on 2016-06-16
Linode gives you a full virtual machine that you can configure however you'd like.  The Digital Ocean alternative sounds more like a web-hosting service.

---

### Post by MAFoElffen on 2016-06-16
As for real vs virtual. For businesses who want a server, I used to just build them physical servers for a specific "job." Now my choice is to recommend a Virtual Host Server that I can create a VM Server image for them, for that job. Once configured, I clone it. Between backups, snapshots and occasional syncs between the two images ... If something goes wrong with the primary, it's easy to bring up the second image in it's place... All the while, the physical host is shielded and scalable for their future growth and needs.

For businesses on the fence, I drop a minimal VM Host Demo Machine there with a VM Server configured to demonstrate what the possibilities could be. (A glimpse.) I let them "see." Most don't know something is possible until you can take their mental picture and show them a glimpse of their possible reality. Also, that confirms that what they envision is the same as my understanding of that. 

If they buy into that, then I can spec a scaled up version of their solution, modified to their needs.

It's sort of the UNIX model-- separate the pieces so they are interchangeable, no matter where those pieces are (My motto: Modules and Layers.) Once you do that then you can change the pieces, add the services you need, and scale it to your needs.

---

### Post by jake-swensen on 2016-06-17
Digital Ocean is an actual virtual machine service not just a web hosting service.  I'm not endorsing them but I've currently set up my choice of operating system (Ubuntu), OpenVPN, ownCloud etc on multiple VMs.  They're just called Droplets (marketing term) according to Digital Ocean, so I didn't think of them as VMs, but they're essentially VMs.

---

### Post by jake-swensen on 2016-06-17
Sounds like scaling for their needs also allows you to scale your efforts, a win-win :-)

---

