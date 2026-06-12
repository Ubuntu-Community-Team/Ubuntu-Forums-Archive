---
title: "Transferring headless 14.04 server to new HW, Want to do a fresh OS build"
date: 2015-03-01
forum: Server Platforms
---

### Post by BrokenPoet on 2015-03-01
Greetings!  I am running an Ubuntu server on an 8-year old barebones box, and recently purchased a never-used Dell PowerEdge T410 as an upgrade.  The server is for home use: File Server, media server, several Minecraft servers for my kids, and hosting local (e.g. intranet) websites (ampache, genealogy, etc.)  My old box is running a 3-disk 1.5TB RAID 5, which I have backed up to a removable drive.  Most other computers in our house are Windows at this point (I was doing well at converting my family, then Windows 8 and touch screen laptops came out and the tide turned.)  I am not a professional IT guy, but am comfortable with the command line with a little help from the forums when I get in over my head.

   I have three questions for the community:
   1) I would like to do a clean install on the new box, but transfer all of my configuration (packages, web sites, app settings, config files) to the new box.  My instinct says that I should just image my hd0 drive to the new machine, boot it, then do a fresh 14.04 install across the top, retaining all of the local configuration files.  I know servers are replicated routinely in the community, but this is the first time I am doing it.  Any advice or links to pertinent threads/sites is appreciated.  (I tried searching on 'transfer' and 'move' in the forums, probably not the right terms.)

   2) (I am not trying to incite a flame war here...) The T410 came with Windows Server 2008.  Is this something that I should be considering using given my usage and technical level?

   3) Is it worth the time to learn how to use Xen (or another hypervisor) and run my main server as a virtual machine?  This would allow me to run both the Ubuntu Server and play with Windows Server 2008, and would let me set up separate VMs for things like Minecraft (where I could let my son learn the administration piece without worrying about him crashing the main file server.)

   Thanks in advance!  This forum has brought me up from a 'windows-only' guy 15 years ago.

---

### Post by TheFu on 2015-03-01
1) I move servers all the time. Here's how. [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview)

2) Couldn't say. I've never used a Windows server. Linux has always seemed 1000x more flexible. There are so many things that Windows cannot do that Linux can and just a few things that Windows does better. If you need those few things that windows does better more than flexibility ... 

3) Xen can be flaky on Debian systems.  KVM is rock solid and part of the linux kernel development.  KVM is routinely the fastest virtualization according to VirtSPEC results.  I know that OEM Windows desktop licenses won't allow moving into a VM, so that could happen with your Windows Server license too ... or not.  Everything I've done the last 8 years has been virtualized unless it couldn't be or that didn't make sense from a security perspective.  In fact, the desktop I'm using now is running inside a KVM VM in a private cloud. The KVM server is headless.  I'm accessing it using x2go which uses NX and that uses an ssh tunnel.  In the same room or from a different continent - x2go is amazing.

Basic security says to have 1 install for 1 service.  This isn't so important if the services aren't internet facing. If they are, it becomes critical. Even so, there are some security things that should never be put into a virtual machine, IMHO.  Edge firewalls, edge routers, things like that.

Plus - don't forget that Linux has lite containers that are easy to spin up/down as needed these days. LXC is nice ... for internal needs. Never put an LXC box on the internet. Not safe and don't believe anyone who claims it is.

---

### Post by BrokenPoet on 2015-03-03
Fu-
   Thank you for the reply!  I tried out x2go with my server, and I agree: The performance (even from across country) is amazing.  After seeing your post I began digging deeper into KVM, and I think that I can easily make it work.  Do you have any suggested sites with potential KVM architecture options?  I'm debating how to logically break up the many items on my current server (e.g. grouping like services together, for example those that use MySQL) while leaving the large hardware raid running on the bare metal with KVM.

---

### Post by TheFu on 2015-03-03
I'd setup a DB server ... mariadb, not mysql, and have all the other systems that need mysql point to it with different application userids and strict firewall rules.

kvm is easy.  Just as easy as virtualbox when you use virt-manager.  There are some simple tuning things that are NOT defaults for some reason.  My blog has some and the same things that make ESX, Virtualbox, Xen work better generally apply to kvm too.  KVM is enterprise level stuff, so it can be tuned beyond what most people care to do.  

Anyway - these are questions for a different forum.

Solved?

---

### Post by BrokenPoet on 2015-03-03
Indeed, thanks again Fu!

---

