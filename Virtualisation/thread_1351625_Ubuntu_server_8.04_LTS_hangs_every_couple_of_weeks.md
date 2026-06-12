---
title: "Ubuntu server 8.04 LTS hangs every couple of weeks"
date: 2009-12-10
forum: Virtualisation
---

### Post by dave2312 on 2009-12-10
[SIZE=3]Hi Support, we are running ubuntu server 8.04 LTS on VMware in a production environment and we are experiencing an intermittent problem with the server hanging with 100% cpu every couple of weeks. We still havn't found the smoking gun. Virtual center shows the CPU hit 100% and stays there until the box is powered off.You can still ping the box but all processes such as jboss freeze. Access to the box is also unavailable.
I haven't used the live forum before so I was wondering if this is the right place to take this question?[/SIZE]

---

### Post by Druke on 2009-12-10
we're not "official" support we're community* support, just to be clear.

So the sounds of it is that a guest os's cpu seems to freeze every week or so.

Saddly there are alot of potential factors ranging from choice of vm software**, status of your updates, and even your computer architecture.

*[Size="1"]This means we're just regular Joe's sitting around with extra time :p[/size]

**[SIZE="1"](if you are running linux guest vms on linux hosts, you really should use kvm instead of VMware or VirtualBox)[/SIZE]

---

### Post by shairozan on 2009-12-15
Hey there, 

How many virtual CPUs does the problem machine have? Occasionally in the VMware suite, adding an additional virtual CPU can cause issues leading to inexplicable load increases and eventual halting of the system.

For example, you are running a quad core host 3 guests. You assign each host 2 VCPUs. Each host is basically vying for a full CPU core, but the host machine has to start doing calculations to create additional "virtual" CPUs that the hosts can access and utilize. 

Over time, this builds up and you start to see large waits in top. When it hits the crescendo, you start seeing waits of 22.4 for a process and then bam, machine starts to halt. 

In these cases, we have resolved the issue by assigning only one CPU to the guest, or moving it to a more robust host. Another thing to check is your virtual hardware version.

---

