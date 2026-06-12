---
title: "Can't see anything after messing up display drivers - Ubuntu 14.04 / VMware Player"
date: 2014-08-30
forum: Virtualisation
---

### Post by 5circles on 2014-08-30
I hope someone can help me with the mess I've created for myself.  I hope that I can remember the steps reasonably accurately.  I'm not sure if this is a virtualisation issue, or just basic display drivers.

I have Ubuntu 14.04 installed as guest OS under VMware Player 6.03, on a laptop with Radeon 6330M and Intel switchable graphics. It was working to some extent, until I decided to take care of a nagging problem.  

The original problem was a screen full of messages about not finding a monitor configuration as the system was logging in.

I deleted .config/monitors.xml - based on a thread about the issue.  First mistake I think.

Next login, the display was in a low-res state.

I read a few things and decided to install the Radeon drivers and Catalyst using synaptic, searching for fglrx-updates.  It looks like that was the second mistake, as now I just see the Ubuntu 14.04 background after logging in.  I'm fumbling with the recovery mode options, but haven't got anywhere so far.  To make things even less fun, the mouse isn't consistently working when I switch between the host and guest.  OK - just figured this out.  Now I understand VMware Ctrl-Alt.

Thanks for any suggestions
Mike

---

### Post by TheFu on 2014-08-31
Virtual machines do not see the real video cards.  They use virtual drivers provided by the VM vendor - VMware in you situation.

It might be easier to ssh into the running VM from a different machine and purge the drivers you loaded, then reboot. Hopefully, that will let the VMware virtual-hardware be seen and Linux should "do the right thing".

Then you need to load the "guest additions" to get nice graphics support inside the VM. This is standard for VMware Player, Workstation, and VirtualBox.

Or just restore from the backup prior to messing this up and load the guest additions.

---

