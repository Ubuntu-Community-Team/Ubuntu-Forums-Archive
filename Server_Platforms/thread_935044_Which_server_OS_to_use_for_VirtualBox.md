---
title: "Which server OS to use for VirtualBox?"
date: 2008-10-01
forum: Server Platforms
---

### Post by hydeciel on 2008-10-01
Hey everyone,
I just recently bought a server, putting the pieces together myself. I am making a remote cisco lab for myself and friends so we can access the cisco switches, ASA device, and routers, as well as a Virtual machine server all from a remote location. 

The goal here is to run Pen tests and configure VMs and cisco equipment to make a secure and operational network, save those configurations and document them. 

I have IPSEC VPN setup on my cisco ASA security appliance so i can remote to my network and access all network services. I will be running a lot of differnt VMs including Windows 2003 server, ubuntu server, ubuntu desktop, Windows XP, Backtrack 3, etc...

What is the best OS server for Virtualbox? I will probably only run VMs on the server. I can't find any real benchmarks, Windows server 2003 vs Ubuntu Server. 
Here is what I want:
Low power useage
64-bit OS
High performance
Able to use Raid 0+1

Here are my system specs:
Intel core 2 Quad core Q9550
8GB of DDR2 1066 5-5-5-15
4U server case
ASUS P5Q Mobo
6 x NICs

Any help guys? 



Thanks,

---

### Post by lykwydchykyn on 2008-10-01
I don't have benchmarks, but I would certainly choose some kind of Linux over Windows for this application for several reasons:
 - You don't need a web browser, GUI, media player, or solitaire game installed if you don't want it.
 - You won't get updates rebooting your machine at random times
 - When VMware wanted an OS for a bare-bones VM server, they went with Linux.  (refer to VMware ESX server)
 - The open source edition of VirtualBox is in the repositories, so you can keep up-to-date with only your regular updates.

Maybe some of that sounds like cheerleading, but those would be my reasons.  Well, that and the cost of W2K3 server.

As to which Linux, that's another debate.  VirtualBox seems to have decent support for Ubuntu, at any rate.

---

### Post by hydeciel on 2008-10-01
hhmmm, I've been moving towards linux anyways.

Ubuntu Server just as good as any other distro? Or is there a better one out there, performance wise speced to my system?

Also does Ubuntu server support 6+ nic cards?

---

### Post by lykwydchykyn on 2008-10-01
I honestly couldn't give you a reason why Ubuntu would be better or worse than any other distros.  I personally like using Debian based distros (which Ubuntu is) because of the package management, and I feel they are easier to maintain from the command line than some others (notably Suse).  Ubuntu's release cycle is quicker than Debian's, but that's about the biggest difference.

I have not honestly tried to put 6 NICs in a system, but I can't see anything in the way the network system is put together that would prohibit you from doing that.  Maybe others can offer more advice there.

---

