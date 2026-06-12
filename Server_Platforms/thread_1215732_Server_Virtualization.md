---
title: "Server Virtualization"
date: 2009-07-17
forum: Server Platforms
---

### Post by adamitj on 2009-07-17
Hi everyone.

I set up Ubuntu 8.04 server in a IBM x3200 server here at my company with no problems, and it is working fine since the beginning of this year (Samba, PostgreSQL, Apache, Glassfish).

Since it is equipped with a Quad-Core Xeon and 4 Gb of RAM (plus very fast disks), I am planning to install some virtualization software to be able of work with another instance of Ubuntu Server, but with testing purporses.

Is there any option in Ubuntu Server, ready to use and easy to maintain?

---

### Post by dragos2 on 2009-07-17
> **adamitj said:**
> Hi everyone.

I set up Ubuntu 8.04 server in a IBM x3200 server here at my company with no problems, and it is working fine since the beginning of this year (Samba, PostgreSQL, Apache, Glassfish).

Since it is equipped with a Quad-Core Xeon and 4 Gb of RAM (plus very fast disks), I am planning to install some virtualization software to be able of work with another instance of Ubuntu Server, but with testing purporses.

Is there any option in Ubuntu Server, ready to use and easy to maintain?

[http://www.ubuntu.com/products/whatisubuntu/serveredition/technologies/virtualization](http://www.ubuntu.com/products/whatisubuntu/serveredition/technologies/virtualization)

As a personal note you can add another 4 Gb of RAM to your machine.

---

### Post by Cheesemill on 2009-07-17
At work I use machines that run Ubuntu Server 8.04 with VMware Server 2 (free) running on top.
 
I run several Ubuntu Server VM's on each machine, using [Ubuntu JeOS 8.04]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos") as the guest OS.
 
If your virtual machines are only going to be for testing then a setup like this should be fine, VMware is controlled through a web UI so no need for a GUI on the server, you can configure and control your VM's from any machine with a web browser.
 
 
If you're looking at putting VM's into production then take a look at VMware ESXi (also free), its a hypervisor which means it's a small translation layer between the virtual machines and the real hardware. With this setup your virtual machines will run at pretty much native performance because there is no OS installed directly on the server, all of the machines are virtual.
The downside to this is that ESXi only runs on specific hardware, there's a compatability list on their [website]("http://www.vmware.com/resources/guides.html"). Also your current Ubuntu server would have to be converted to one (or more) virtual machines if you decided to go down this route.
If you could get your hands on another server to just run VM's then this wouldn't be a problem :)

---

### Post by windependence on 2009-07-17
+1 for ESXi. The main thing you have to worry about on ESXi is the storage controller. There are lots of cheap storage controllers in the $20 range that will work with ESXi though and you won't have any problems. Most machines, even if they aren't on the compatibility list will work with the right controller installed. Pretty much anything based on the Silicon Image Sil3512 chipset will work and will be very cheap.

-Tim

---

### Post by adamitj on 2009-07-18
Thanks a lot for your replies.

I used VMWare Server v1.0.1 in a near time ago, but the host OS was Microsoft Windows 2003 Server. I didn't went too far that time, but I could use it for test reasons perfectly.

Do you know if exists in VMWare (Server or ESXi) a way to start virtual guest operating systems by command-line? My purpose is to start a VM when the host OS boot completes, without needing to enter some intranet HTTP page or doing any kind of manual operation.

By the way... these versions of VMWare are really free? I mean... free for commercial use...

---

### Post by windependence on 2009-07-19
Yup. 

[https://www.vmware.com/tryvmware/index.php?p=free-esxi&lp=1](https://www.vmware.com/tryvmware/index.php?p=free-esxi&lp=1)

Here is a free tool to do backups and move VMs too. 

[http://www.veeam.com/vmware-esxi-fastscp.html](http://www.veeam.com/vmware-esxi-fastscp.html)

-Tim

---

### Post by juancarlospaco on 2009-07-19
Server = UbuntuServerMinimal+KVM+SSH
Admin PC = Convirt

VMware aren't free for commercial use.

---

### Post by windependence on 2009-07-19
> **juancarlospaco said:**
> 

VMware aren't free for commercial use.

You go ahead and keep thinking that, and I'll keep using my high performance free software. ESXi will run rings around your bloated OS on top of an OS setup. 

So you're telling a VMware Partner that it's not free? How about this from the VMware web site:

> **Get Easy-to-Use [COLOR=Red]Production[/COLOR]-Ready Virtualization**

 								Deliver unmatched levels of performance and reliability with VMware ESXi while saving money on hardware, power and cooling costs and running a more responsive datacenter.


> **Deliver Enterprise Performance to Your Applications**

 									 *Run email, databases, ERP and other resource-intensive applications on VMware ESXi&#8217;s bare-metal architecture offering advanced memory management and support for scaled-up physical and virtual machines.  You can also choose from the broadest range of [supported guest operating systems]("http://www.vmware.com/pdf/GuestOS_guide.pdf"), including Windows, Linux, Netware, Solaris and more. *
 
 ***Save More Money than with Other Hypervisors***

 *									 **[I]Get higher consolidation ratios with VMware ESXi. The memory and CPU scheduling optimizations in VMware ESXi let you run virtual machines at [twice the consolidation ratio]("http://blogs.vmware.com/virtualreality/2008/03/cheap-hyperviso.html") possible with other first-generation hypervisors. Fewer servers means more cost savings.*[/I]

[I][I]

[/I][/I]> **VMware ESXi FAQs**

 								    Why is VMware making ESXi free?VMware is making its standalone ESXi hypervisor available at no cost in order to help **[COLOR=Red]companies of all sizes[/COLOR]** experience the benefits of virtualization. Customers have shown tremendous interest in ESXi due to its innovative architecture, simple setup, and high performance. Allowing IT administrators to obtain VMware ESXi for free enables everyone to gain access to VMware's datacenter technology and prove its value in their own companies.


Yep, sure looks like commercial business to me. Get your head out of your butt and read the site before making comments that aren't true. Just because you don't know how to use a product doesn't mean it doesn't work. The management tools come free with the hypervisor, downloadable once you install it, and I just posted some free tools to use from Veeam. This product is the cat's meow. Now go read more proof it's free for commercial use at:

[http://www.vmware.com/products/esxi/uses.html](http://www.vmware.com/products/esxi/uses.html)

Then use what you want, but at least be informed.

-Tim

---

### Post by senor_smile on 2009-08-04
> **windependence said:**
> Yup. 

[https://www.vmware.com/tryvmware/index.php?p=free-esxi&lp=1](https://www.vmware.com/tryvmware/index.php?p=free-esxi&lp=1)

Here is a free tool to do backups and move VMs too. 

[http://www.veeam.com/vmware-esxi-fastscp.html](http://www.veeam.com/vmware-esxi-fastscp.html)

-Tim

With the veeam fastscp tool, do you know if you can backup running vm's, or do they have to be shut down?

---

