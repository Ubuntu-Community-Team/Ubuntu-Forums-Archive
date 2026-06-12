---
title: "Is this mix of Desktop/ VM Servers safe?"
date: 2010-05-25
forum: Security
---

### Post by bstar on 2010-05-25
[COLOR=black][FONT=Verdana]I recently acquired a new system a buddy built a couple of months ago using some top-of-the-shelf hardware components including Quad-Core's 8gb-ram dual drives, etc. A very nice system...[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I am just beginning to learn and experiment with Oracle's VirtualBox software so here is my security question.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Currently I have the following setup for development. 1.) A 6yr. old development server for Web/php/db. 2.) a 3yr. old production server for 3 low traffic web sites (port 80 for web, port 22 for ssh are port forwarded on my router to this server). 3.) A 6yr. old trusty and time-tested desktop which I do all my development on. So 3 separate computers running 24/7.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Here is what I would like to do, please tell me if this is a safe setup from a security stand-point? Any suggestions or traps to look out for?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Take the new hardware, install Ubuntu 10.04 64bit Desktop Edition. Install Oracle's VirtualBox, create 2 Virtual Machines, each running Ubuntu 10.04 64bit Server Edition. Then Bridge the network adapters on these Virtual Machines so they have their own Internal Network IP. The first one would be the development server. The second I would port forward router ports 80 and 22 for those 3 web sites.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Do I understand it correctly that if the Virtual Machine (#2) was somehow compromised from the outside it would not be possible to see the host computer (Desktop) or #1 server (Dev)?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]All comments, suggestions and first-hand experiences are appreciated![/FONT][/COLOR]

---

### Post by bodhi.zazen on 2010-05-25
The short answer is virtual machines are no more or less secure then physical machines.

If a machine, physical or virtual, is compromised it can potentially be leveraged against the rest of your LAN.

It is not possible, however, to directly access the host OS from a compromised guest.

I would suggest you look at KVM (I am guessing you have the hardware) and either OpenVZ or Linux containers.

---

### Post by spynappels on 2010-05-26
Or look at VMWare ESXi as a bare metal hypervisor....

---

### Post by Chayak on 2010-05-31
> **spynappels said:**
> Or look at VMWare ESXi as a bare metal hypervisor....

+1 If I'm setting up a box to host virtualized systems it's always running ESXi or ESX.  The only downside is the management client is windows software.

There's a bit of a learning curve as well, but worth it.

---

