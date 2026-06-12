---
title: "Should I use UEC or just qemu/kvm virtualization"
date: 2011-01-14
forum: Virtualisation
---

### Post by tomoki.taniguchi on 2011-01-14
We have a bunch of vmware esxi servers running hosting our various servers.
Webserver, Mailserver and so on.

We migrated from a Xen based environment to ESXi a few years back for a couple or reasons.
1) ESXi has a simple user interface for creating/starting/stopping VMs (though only for windows) :(
2) ESXi was free as long as you give up a few options ( live migration, centralized management)
3) And most importantly it was very simple to setup a shared storage on iscsi disks (no need to mess with clustering)

Linux virtualization seems to have matured greatly in the past couple of years 
and i am considering moving our infrastructure to a linux/kvm based systems.
1) there are now nice GUI based tools like virt-manager to manage systems
2) obviously still free. and i get back lost options like live migration and centralized management
3) i am still researching the whole shared storage situation, but i am sure it is much simpler now

What i am trying to figure out at this time is if I should migrate to a CLOUD environment using UEC 
or should i stick with a simple QEMU/KVM hosts with centralized management.  

My knowledge of CLOUDs is very limited and so i was hoping some one can inform me about:
1)  The benefits/advantages of using UEC over a simple virtualization.
2) Are there any disadvantages to using UEC over simple virtualization?
3) Which is more for replacing my current setup?

My current setup:
     a) 21 host machines located across 6 locations. 
     b) minimum of 2, maximum of 7 host machines in a single location
     c) each location has at least 1 iscsi server, max 3
     d) 85% of VM instances are running linux, other 15% runs windows servers
     e) most of the linux servers runs either ubuntu 8.04 or 10.04, a few runs 10.10.
     f) most servers have a UNIQUE purpose.  (WEB, MAIL, WEBAPP, VPN, AUTH) 
     g) some servers are mirrored for redundancy but usually located at a different location, so would not be in the same cluster.
     h) display/console access is usually only needed during install/maintenance for linux servers, but needed for windows servers.

Any advice will be appreciated
TIA,
Tomoki

---

### Post by TheR on 2011-02-06
> **tomoki.taniguchi said:**
> We have a bunch of vmware esxi servers running hosting our various servers.
Webserver, Mailserver and so on.

We migrated from a Xen based environment to ESXi a few years back for a couple or reasons.
1) ESXi has a simple user interface for creating/starting/stopping VMs (though only for windows) :(
2) ESXi was free as long as you give up a few options ( live migration, centralized management)
3) And most importantly it was very simple to setup a shared storage on iscsi disks (no need to mess with clustering)

Linux virtualization seems to have matured greatly in the past couple of years 
and i am considering moving our infrastructure to a linux/kvm based systems.
1) there are now nice GUI based tools like virt-manager to manage systems
2) obviously still free. and i get back lost options like live migration and centralized management
3) i am still researching the whole shared storage situation, but i am sure it is much simpler now

What i am trying to figure out at this time is if I should migrate to a CLOUD environment using UEC 
or should i stick with a simple QEMU/KVM hosts with centralized management.  

My knowledge of CLOUDs is very limited and so i was hoping some one can inform me about:
1)  The benefits/advantages of using UEC over a simple virtualization.
2) Are there any disadvantages to using UEC over simple virtualization?
3) Which is more for replacing my current setup?

My current setup:
     a) 21 host machines located across 6 locations. 
     b) minimum of 2, maximum of 7 host machines in a single location
     c) each location has at least 1 iscsi server, max 3
     d) 85% of VM instances are running linux, other 15% runs windows servers
     e) most of the linux servers runs either ubuntu 8.04 or 10.04, a few runs 10.10.
     f) most servers have a UNIQUE purpose.  (WEB, MAIL, WEBAPP, VPN, AUTH) 
     g) some servers are mirrored for redundancy but usually located at a different location, so would not be in the same cluster.
     h) display/console access is usually only needed during install/maintenance for linux servers, but needed for windows servers.

Any advice will be appreciated
TIA,
Tomoki


I didn't choose UEC neither. For one reason I think that clustering is required. The way I see cloud computing it is more commercial hype behind the idea of selling cheap computer space on the Internet. So if you are creating lots of similar machines, cloud software will help you create and manage them quickly. 

But I am writing to you because I want to encourage you. I am using similar system (although only on single location) for almost a year now in production and there are no problems. Live migration mostly works although sometimes some machine do choke when migrating. iscsi with lvm works without problems. All server machines are Ubuntu 10.04. with kvm.

by
TheR

---

### Post by FiVAL on 2011-03-16
Hello Tomoki,

I'm in the same situation as your are, or maybe you were... ;-)
And now, after two mounths, I'm courious where you stands.

Hopefully you like to share (in short) your 'research' ??

Thanks in advanced!

---

### Post by capscrew on 2011-03-16
I just installed the distro called Proxmox VE 1.7.  It is based on Debian 5 (Lenny).  This incorporates both OpenVZ containers and KVM.  The web interface is very fast and includes a VNC interface for the guest hosts.  Best of all it is free!

I have just started on my project, but I am very pleased.  I can run Windows or Linux from an ISO install in KVM or OpenVZ templates of Linux images.

Check it out at [**_[COLOR="Blue"]Proxmox VE[/COLOR]_**]("http://www.proxmox.com/products/proxmox-ve").

---

### Post by FiVAL on 2011-03-17
> **capscrew said:**
> Check it out at [**_[COLOR="Blue"]Proxmox VE[/COLOR]_**]("http://www.proxmox.com/products/proxmox-ve").

Thx capscrew. I certainly gonna give this a try @ home.
But I don't think I'll use for production...

We need a solution with a large community. And for some
of our servers we even want a long term support with
security updates.

We also like the commandline/ssh very much, so for the company
the web-interface only _could_ be a security downgrade.

Also we want to use the [ubuntu-vm-builder]("http://doc.ubuntu.com/ubuntu/serverguide/C/ubuntu-vm-builder.html"),
or does this script also work on the proxmox-ve??

---

### Post by capscrew on 2011-03-17
> **FiVAL said:**
> Thx capscrew. I certainly gonna give this a try @ home.
But I don't think I'll use for production...

We need a solution with a large community. And for some
of our servers we even want a long term support with
security updates.
 
We also like the commandline/ssh very much, so for the company
the web-interface only _could_ be a security downgrade.

Also we want to use the [ubuntu-vm-builder]("http://doc.ubuntu.com/ubuntu/serverguide/C/ubuntu-vm-builder.html"),
or does this script also work on the proxmox-ve??

I understand that a large corporation wants some accountability.  Proxmox, does provides fee based support for those that need it.  

All of what you are contemplating is FOSS based and the community, while large, are composed of independent FOSS projects. By that I mean Debian, OpenVZ, LVM, Perl, Python, etc. 

The web based interface is not the only method of running the Proxmox host node (HN).  You can use the command line.  Remember it is a Debian Lenny based OS.  I use SSH to login.  I believe the Apache server could be turned off if you only wanted CLI.

I don't see any difference between the Proxmox project and the Ubuntu-vm-builder it theory.  They both use the same building blocks.

---

