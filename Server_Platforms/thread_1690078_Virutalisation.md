---
title: "Virutalisation"
date: 2011-02-17
forum: Server Platforms
---

### Post by naesin on 2011-02-17
Hi,

I kinda new to Unix/Linux but thought I would jump in at the deep end and build myself a couple of servers. Thing is I only have the one spare computer and was wondering if it was possible to do virtualisation without the desktop component?

Any ideas,

Naesin

---

### Post by volkswagner on 2011-02-17
Virtualization has many choices.  Each has their own +'s and -'s.

If you only want to run virtual machines without a GUI, perhaps [KVM]("https://help.ubuntu.com/community/KVM") will be a good solution for you.

Other choices include VmWare or [XenServer]("http://www.citrix.com/English/ps2/products/product.asp?contentID=683148"), each offers bare metal solutions in their product line.  A couple caveats for me on XenServer are USB passthrough and needing an MS Windows to run the graphical manager.  There is OpenXenCenter, but proved too buggy for me, So I use a Windows Guest to manage the server along with the command line.   Of course this is after creating the first Windows VM with my dual boot machine.  I never used any VMWare products so I can't comment on function.

You may also be able to run [VirtualBox]("http://www.virtualbox.org/") on Ubuntu Server.  Found [this thread]("http://ubuntuforums.org/showthread.php?t=616334") but is is quite old...may get you started.

---

### Post by kevinthecomputerguy on 2011-02-17
Im a huge VMWare fan.
 
Download a "esxi 4.1" iso from vmware's website. Download the vsphere client, and you will be up and running in a few minutes.
 
My guide at [http://woodel.com](http://woodel.com) shows you how to do it with a non gui linux box, but esxi is probably what your after, as a newb.
 
-Kev

---

### Post by elico on 2011-02-18
the problem with esx and esxI that it has hardware requirments.

you can always run headless virtualbox and also Xen or KVM server.
im using this
[http://techsnail.com/general/centos-5-5-x86-64-hypervisor-edition/](http://techsnail.com/general/centos-5-5-x86-64-hypervisor-edition/)
a centos based xen kernel hypervisor and it rocks!!

---

### Post by HugoSerrano on 2011-02-18
You can install Ubuntu Server, and choose the virtualization package.

Then you can manage your virtual machines from command line, or install virt-manager in you Ubuntu Desktop, and manage the servers.

Regards!

---

### Post by naesin on 2011-02-18
Nice one guys, thanks a bunch. Lots of ideas which one out of those do you thnk would best suit a noob?

---

### Post by HugoSerrano on 2011-02-18
If you got time, try them all ;-)

---

### Post by rubylaser on 2011-02-20
I use/love Proxmox VE.  It has OpenVZ/KVM built-in with a nice web interface to manage it all.  
[http://pve.proxmox.com/wiki/Downloads]("http://pve.proxmox.com/wiki/Downloads")

---

