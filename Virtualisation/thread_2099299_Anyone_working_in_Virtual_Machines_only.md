---
title: "Anyone working in Virtual Machines only?"
date: 2012-12-29
forum: Virtualisation
---

### Post by mreq on 2012-12-29
Is there someone with a virtualbox-only (vmware whatever) host and works, surfs etc. in virtual machines only?

If so, why? What's the advantage?

As for the rest, why don't you? What's the disadvantage? :p

---

### Post by sudodus on 2012-12-29
> **mreq said:**
> ... What's the disadvantage? :p

It is slower. The virtual machine is another layer between your application program and the hardware, and it needs cpu power and ram.

But I use virtual machines to test new distros and to run Windows to get access to things (hardware and software), that won't work in Ubuntu.

---

### Post by alarme on 2012-12-29
Testimonial:

Hello, I'm Alarme, and I'm addict to work with virtual machines...

Five years ago, I decided to introduce virtual machines at my workplace (12 workstations + 3 laptops)

These are my reasons and my experiences with the system:

Initially, with every workstation running Windows natively, it was more than usual:
- Having to stay late some Fridays (or even whole weekends) to fix Windows-related problems
- Or having to constantly be aware of Antivirus software updates/licences/etc, which didn't properly solve virus infections.
    
I decided to migrate to Linux and use Windows VMs as workstations. It wasn't my intent to convince employees to use Linux in their daily tasks (except reading e-mail and web navigation). I only wanted to have them working under Windows, as usual, but in a virtual machine.

I created VMs for every workstation, using a fresh installation which only contained basic system-related stuff (i.e. Windows updates) and whichever applications we use. Of course, I kept images of these installations.

Using a DHCP server I blocked Internet access to those clients running a virtualized Windows (through gateway denial). I am aware that any somewhat experienced user could have bypassed that protection, but that is not of my concern.

Anything that requires Internet access is therefore done under Linux.

In the event that any workplace stops functioning, the time and effort I need to fix them (that is, reverting the machine back to it's initial status) is merely transferring 10GB of data through LAN.

Since I took that decision, I haven't had to waste any other weekend fixing that kind of problems. :-)

---

### Post by Ms. Daisy on 2012-12-29
Good luck on your school essay, mreq ;)

---

### Post by BertN45 on 2012-12-29
Alarme did give a very good example of the advantages of a VM. I would add the following advantages.

- Old applications that only run using say DOS or Windows NT could be put in a VM together with that old OS and could be used on any modern OS/PC, no worry about drivers.
- Many physical servers are under occupied, because they run a certain old server and server OS needed for certain enterprise applications. Virtualising these old relics can reduce the number of servers, the HW and SW maintenance costs and the power consumption. Sometimes you only can buy the spare parts for these old servers on eBay, virtualisation solves that problem.
- It is easier to distribute software, because you don't have to install OS and applications in remote branches of the enterprise, you simply distribute the appliance (VM consisting of OS and Application).
- You do not have to worry about the application behavior in a different environment.
- You can optimise the OS for one application and you do not have to compromise like in the past, when many completely different application had to run on the same OS and HW. The end result could be that the application is more responsive, so it has a better performance then on a general purpose HW server.
- More choice since the OS used for the application becomes irrelevant if the whole runs in a VM. [COLOR="Red"]This is very very good for Linux![/COLOR]
- Reliability gets more affordable, because VMs can easily run on any other server if needed. Today the same appliance on another server will be kept synchronized and will take over automatically in case of HW failures.
- Load sharing between HW servers is often a piece of cake you simply deploy the appliance two, three or more times. If somebody connects to the appliance, you simply connect him to the least loaded server. 

Just for fun I implemented a simple version of the functionality of the last two bullet points (building on Virtualbox) in approx. 2500 lines of shell script.

You have to see the whole in combination with the virtualisation of the storage (disks) system, the virtualisation of the network and also the potential benefits that it provides to the service oriented architectures.

---

### Post by andrew.46 on 2012-12-30
> **mreq said:**
> As for the rest, why don't you? What's the disadvantage? :p

Surely not a school assignment?? Two disadvantages that are a factor in my own usage:

[LIST=1]
[*]Resources: It is a good thing to have enough computer resources to share between host and guest. Not such a great result if these resources are not in place.
[*]3d acceleration: In my own experience with VirtualBox the 3d support is a lot better these days but still has some ways to go.
[/LIST]

Hope this is some help?

---

### Post by Hawkway on 2012-12-31
I'm new to Ubuntu and virtualization but I plan on running a VM inside my production home server for development and testing.  It will help me learn as well as keep my production environment "clean" of mistakes.  Anyone else do this?

---

### Post by sudodus on 2012-12-31
> **Hawkway said:**
> I'm new to Ubuntu and virtualization but I plan on running a VM inside my production home server for development and testing.  It will help me learn as well as keep my production environment "clean" of mistakes.  Anyone else do this?
Yes, we are many people who start testing something new in a virtual machine. Welcome :-)

---

### Post by NeoGreen on 2012-12-31
I use VMWare Player or Virtual Box to test Distros before deploying them to live environments.  It a great way to test how some applications work with the new OS. I also use VM's to run PEN Tests and Audits on networks.

---

### Post by mreq on 2013-01-01
> **Ms. Daisy said:**
> Good luck on your school essay, mreq ;)

Aaand that's a miss.

Not really, I am just interested and considering this option. As a matter of fact, I'm studying statistics at university. Not close to virtual machines, really ;)

Thanks for your opinions everyone.

---

