---
title: "Need urgent help on getting internet connection Ubuntu Virtual Machine"
date: 2008-11-14
forum: Virtualisation
---

### Post by manisha on 2008-11-14
Hi friends,

I am new to Ubuntu.
I am using a VirtualBox on Windows XP where the VM is Ubuntu.
Now i want to get internet connection on my VM i.e.Ubuntu.
I want to use the connection that i already have on the host OS i.e. Windows, but dont know how to do it.
Can anyone please help me out?I will be really thankful.

---

### Post by olivesandtrees on 2008-11-14
I am not super familiar with VirtualBox, but with most virtual software you will probably have three communication options when it comes to adding a network interface: NAT, bridged, or host only.  You are probably going to have the best luck using NAT or bridged where the VM will be in a totally different network range then the host machine, but will, like their name implies, either bridge the two networks or use address translation to let the VM communicate with the host system's network.  Which in turn, will give it internet access.

---

### Post by manisha on 2008-11-14
yes i am using NAT. still its not working:(

---

### Post by olivesandtrees on 2008-11-14
Have you double checked your virtual network settings?  Is the interface NAT pointed at the correct default gateway in the main network?  Have you tried changing how the interface comms with the network (I.E. switched it to bridge mode) and if you have did you make sure the virtual interface was bridging to the correct physical interface?

I'm basing all of this off of my experience with VMware so I don't know how much that will help.

...maybe look into using VMware

---

### Post by olivesandtrees on 2008-11-14
Just another thought, what's Ubuntu reporting when you run a ifconfig?

---

### Post by ideebe on 2008-11-15
[img]http://www.ideewomen.com/index.jpg[/img][http://www.ideejewelry.com](http://www.ideejewelry.com/)

---

