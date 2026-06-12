---
title: "Host does not see VirtualBox machine when no physical network is available"
date: 2009-02-02
forum: Virtualisation
---

### Post by bkann on 2009-02-02
Hi -

Apologies in advance if I'm missing something basic.

I am using Ubuntu as the host, WinXP as the virtual machine.  I'm using Ubuntu for a variety of Web development tasks, but I have found it quicker to prototype my databases using MS Access in Windows in conjunction with some 3rd-party SQL tools.  Ultimately, the result is Apache with PHP on the Ubuntu machine, and a MySQL database on the Windows VM.

This is important because I have two network cards configured on the VM, both in 'host interface' mode.  The first is set up for DHCP so that I can get an IP on whatever network I'm connecting to.  The second adapter is set up with a static IP (which happens to match my home network specs, but I don't think this is important).  I do this so that PHP/Apache on Ubuntu can query MySQL on Windows thru the static address and I don't have to specify new connection parameters every time I get a new DHCP lease.

When I have access to a network, this setup is amazingly convenient for me.  However, I found today that, when no network is present (eg., I'm on a plane), this configuration fails.  Ubuntu can't find the static address, can't resolve the Windows box's name, etc.  I don't know how to route to the Win VM, so my servers can't query MySQL on that box.  My dev site therefore fails.

I don't know if I've described this very well.  My goal would be to be able to have a completely autonomous setup when necessary... where Apache on Ubuntu can talk to VB Windows over a static IP or resolvable name even when no real network is present.  This must be possible(?)

Many thanks in advance for any help you might be able to provide!

---

### Post by Jose Catre-Vandis on 2009-02-03
Have a look here for some ideas

[http://opensourceexperiments.wordpress.com/2008/04/18/virtualbox-case-study-making-host-only-networking-work-between-two-ubuntu-guest-os-virtual-machine-on-windows-vista-host/](http://opensourceexperiments.wordpress.com/2008/04/18/virtualbox-case-study-making-host-only-networking-work-between-two-ubuntu-guest-os-virtual-machine-on-windows-vista-host/)

Me thinks you might need to reconfigure and get your host (Ubuntu) running a DHCP server so that the VM can connect to it?

---

### Post by Ng Oon-Ee on 2009-02-05
Hi, I posted a VERY LONG howto [here]("http://ubuntuforums.org/showthread.php?p=6681584") which can help.

Since you're not likely to be wanting to read that whole thing, let me summarize. You can use uml-utilities to create a virtual interface just between you and your VM. Check out the section on "Setting up the virtual interface" in my HOWTO, and set up your VM with Host Networking to the created tap0 + assign 10.0.1.2/255.255.255.0 as fixed IP to the new Network Adapter in VirtualBox. Viola, a LOCAL area network (never seen or heard off outside your machine) which doesn't need anything connected, its always on as long as your host and guest OS are.

---

### Post by zevans on 2009-02-05
I had this problem too. It would seem that Windows is stupid enough to switch off all kinds of networking if none of your network connections are working. 

I've worked around it by making sure "Adapter 1" is an internal-only one, which means in the worst case there is still a dummy there to allow the shares on \\VBOXSRV to appear. It seems like if Windows can't see any adapters it doesn't load the network client at all, so \\anything no longer works.

---

### Post by bkann on 2009-02-06
That's *exactly* what I was looking for, Ng Oon-Ee.  Worked perfectly.  Thanks so much!!

---

### Post by Ng Oon-Ee on 2009-02-07
You're welcome. I found the information useful, myself =).

---

