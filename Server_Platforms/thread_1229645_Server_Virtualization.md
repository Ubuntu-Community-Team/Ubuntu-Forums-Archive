---
title: "Server Virtualization"
date: 2009-08-02
forum: Server Platforms
---

### Post by adamitj on 2009-08-02
Hi everybody!

I need to deploy 4 guest OS instances inside a single powerful server hardware:

- 1) M$ Windows 2003 Server   - App Server;
- 2) Ubuntu Linux 8.04 Server - App Server;
- 3) Ubuntu Linux 8.04 Server - Web Server;
- 4) BrazilFW - Firewall Server;

What you can suggest me to use since VMWare ESXi doesn't worked well?

---

### Post by Cheesemill on 2009-08-02
If you want decent performance for production machines then you need to get ESXi working. The hardware compatability list is quite restrictive but it's well worth it.
 
I run a couple of ESXi hosts at work for production purposes, and run VMware Server on a workstation for testing purposes (over a Ubuntu Server 8.04 minimal install).
 
The only drawback for me is that VMware still haven't released the vSphere client for Linux :(

---

### Post by PilotJLR on 2009-08-02
OP - what part of ESXi did not work well for you? That may be relevant...

---

### Post by windependence on 2009-08-03
That's what I was thinking.

-Tim

---

### Post by dragos2 on 2009-08-03
I chose Citrix FreeXenServer and its working fine with 6 VM's currently on top if it.
It lacks remote iso boot.

---

### Post by adamitj on 2009-08-03
> **PilotJLR said:**
> OP - what part of ESXi did not work well for you? That may be relevant...

Couldn't recognize any hard disk drive. I am able to boot from ESXi instalation to the license agreement, and them it fails telling me there is "no media to install" ESXi.

However... I'm trying to install it into a "testing" hardware (Athlon X2 64 with 2 GB of RAM and NVIDIA chipset).  It's not the final server which is an IBM x3200 series with RAID and 8 GB of RAM. The problem is: my IT manager doesn't allowed the instalation in the production server until test it - and he's right after all.

---

### Post by jamesrfla on 2009-08-03
Do you have RAID setup? Does the BIOS pick up the hard drives?

---

### Post by adamitj on 2009-08-03
> **jamesrfla said:**
> Do you have RAID setup? Does the BIOS pick up the hard drives?

No, in this test machine there is no RAID set. Just the nVidia SATA/IDE controller with BIOS RAID disabled.

---

### Post by jamesrfla on 2009-08-03
Did you check to see if the hard drivers are registered in the BIOS. If the BIOS doesn't show them maybe the hard drives are not plugged in.

---

### Post by jocampo on 2009-08-03
> **adamitj said:**
> Hi everybody!

I need to deploy 4 guest OS instances inside a single powerful server hardware:

- 1) M$ Windows 2003 Server   - App Server;
- 2) Ubuntu Linux 8.04 Server - App Server;
- 3) Ubuntu Linux 8.04 Server - Web Server;
- 4) BrazilFW - Firewall Server;

What you can suggest me to use since VMWare ESXi doesn't worked well?

Ubuntu server with or without GUI? 
If you are not going to deploy any Windows Cluster, maybe you can use VirtualBox via headless server. 

How to deploy
[http://www.sucka.net/2009/07/virtualbox-3-0-2-on-ubuntu-9-04-i386-or-amd64/]("http://www.sucka.net/2009/07/virtualbox-3-0-2-on-ubuntu-9-04-i386-or-amd64/")
How to manage and create VMs via console
[http://www.sucka.net/2009/07/vboxheadless-and-how-to-swing-it/]("http://www.sucka.net/2009/07/vboxheadless-and-how-to-swing-it/")


Is this a lab or for a real production environment?

---

### Post by jamesrfla on 2009-08-03
> **adamitj said:**
> 
What you can suggest me to use since VMWare ESXi doesn't worked well?

You could always try VMware Server. It doesn't require a GUI and is all controlled through a web interface. It has to be installed on a existing OS.

---

### Post by Cheesemill on 2009-08-03
As I said, > The hardware compatability list is quite restrictive.... :)
 
I'm sure you've read this by now but check out the official HCL to see if your production server will run ESXi before you get any further into testing:
[http://www.vmware.com/resources/compatibility/search.php](http://www.vmware.com/resources/compatibility/search.php)
 
If you Google for "[esxi whitebox compatability]("http://www.google.com/search?q=esx+whitebox+compatibility")" you can find several sites which have lists of officially unsupported hardware that's known to work, you may be able to get away with using something you already have, one of my ESXi hosts at work is an HP dc7900 that used to be my workstation, ESXi installed with no complications.

---

### Post by jamesrfla on 2009-08-03
> **Cheesemill said:**
> As I said,  :)
 
I'm sure you've read this by now but check out the official HCL to see if your production server will run ESXi before you get any further into testing:


I am trying to figure out if I should use VMware ESXi or VMware Server. The server I am getting might be compatible with it. Witch one would use less RAM? Is the ESXi hard to configure. I heard it the VMware Server and ESXi come with a web configuration interface right?

---

### Post by Cheesemill on 2009-08-03
If your hardware is compatible then go for ESXi, it's a bare-metal hypervisor which means it doesn't need a host OS to install, its just a translation layer between the VM's and the physical hardware. You should get close to native performance from your VM's.
 
Installing an OS and then VMware Server is just adding an extra unnecessary layer of software to your machine.
 
Unlike VMware Server 2.0 (which is web-based), you need to use the vSphere Client application to configure/administrate the ESXi machine and it's VM's (unfortunately it's not yet available for Linux :()

---

### Post by jamesrfla on 2009-08-03
It looks like I have to pay for this vSphere Client. Is there any other way to control ESXi?

---

### Post by adamitj on 2009-08-03
> **jamesrfla said:**
> Did you check to see if the hard drivers are registered in the BIOS. If the BIOS doesn't show them maybe the hard drives are not plugged in.

Yes, they are plugged and fully functional. Only ESXi cannot find them. I sae in VMWare's site that most of common hardware cannot be identified, so I'm not considering ESXi.

If you have other suggestions they're welcome...

---

### Post by jamesrfla on 2009-08-03
Try VMware Server. Just install it on your current OS.

---

### Post by adamitj on 2009-08-03
> **Cheesemill said:**
> As I said,  :)
 
I'm sure you've read this by now but check out the official HCL to see if your production server will run ESXi before you get any further into testing:
[http://www.vmware.com/resources/compatibility/search.php](http://www.vmware.com/resources/compatibility/search.php)
 
If you Google for "[esxi whitebox compatability]("http://www.google.com/search?q=esx+whitebox+compatibility")" you can find several sites which have lists of officially unsupported hardware that's known to work, you may be able to get away with using something you already have, one of my ESXi hosts at work is an HP dc7900 that used to be my workstation, ESXi installed with no complications.

Thanks Cheesemill. My hardware definitely isn't compatible with ESXi. I will ask my IT manager to make things easy and buy another hardware for ESXi testings... it would not be too much expensive :)

---

### Post by Cheesemill on 2009-08-03
> **jamesrfla said:**
> It looks like I have to pay for this vSphere Client. Is there any other way to control ESXi?
 
vSphere Client is free, just point your browser at the address of your ESXi host and download it.

---

### Post by jamesrfla on 2009-08-03
> **Cheesemill said:**
> vSphere Client is free, just point your browser at the address of your ESXi host and download it.

Okay I will have to try that as soon as I get my server. Thanks for your help. I will try the ESXi first before I try the VMware Server.

---

### Post by pizmooz on 2009-08-03
Basically ESXi is the 'embedded' version of ESX.  ESXi is just the vmware's kernel which a thin bootstrapping layer to get it started and manage it, where as ESX has a more full gnu-linux based 'console OS' which boots and manages it.  I personally like ESX because it allows you to leverage your knowledge of linux to control vmware's virtualization function.  Both versions still have the vmware kernel on a linux kernel.

In Redhat 5.4 they will be ditching Xen and going to KVM/QEMU as their virtualization solution.  It is ideal because it uses linux *as* the hypervisor.  It just make sense to include virtualization in the linux kernel since it already has the memory management and processor scheduling taken care of.  Infact with KVM/QEMU your VMs are just privileged processes.  However KVM is still not suitable for production server, yet but it is extremely powerful.

If you are doing this for business I would go with ESX for now, it is rock solid.  Yes, you will need a decent scsi or sas based hd controller to run ESX or ESXi.   Make sure your processor supports x86 hardware virtualization(on intel VTx), you need to turn it on in the BIOS.

have fun!

---

### Post by Brazen on 2009-08-03
I use libvirt at home and at work.  I use it with qemu/kvm on servers with the virtualizations extensions and with qemu/kqemu on machines that lack the virtualization extensions.  In both cases it works great.  I'm replacing our ESX servers at work with it, and even with qemu/kqemu I'm getttings bit better performance out of my virtual machines.

---

### Post by jamesrfla on 2009-08-03
Will the ESXi work with a Server with 2 500Gb hard drives in RAID 1? I guess I will go with ESXi instead of ESX. I am also looking into Citrix XenServer and Xen. Although I am not sure how you mange those. If it is free I will consider them.

---

### Post by pizmooz on 2009-08-03
> **jamesrfla said:**
> Will the ESXi work with a Server with 2 500Gb hard drives in RAID 1? I guess I will go with ESXi instead of ESX. I am also looking into Citrix XenServer and Xen. Although I am not sure how you mange those. If it is free I will consider them.

It depends on *which* RAID controller you are using.  In ESX/ESXi There is basically no support for IDE or SATA based controllers.  There is good support for most modern SCSI or SAS based controllers.

---

### Post by jamesrfla on 2009-08-03
I will be using a LSI MegaRAID controller.

---

### Post by pizmooz on 2009-08-03
[vmware compatibility guide]("http://www.vmware.com/resources/compatibility/search.php?action=base&deviceCategory=server")

You should be able to look up your specific controller under the I/O tab.  You should be able to look up your specific model.

---

### Post by jamesrfla on 2009-08-03
It looks like they don't have my server. I guess since it is a barebone server I want to get. Well here is what I want to get [http://www.newegg.com/Product/Product.aspx?Item=N82E16816110030](http://www.newegg.com/Product/Product.aspx?Item=N82E16816110030) with this processor [http://www.newegg.com/Product/Product.aspx?Item=N82E16819117165](http://www.newegg.com/Product/Product.aspx?Item=N82E16819117165)

---

### Post by PilotJLR on 2009-08-03
I work with VMware everyday, both in a consulting and sysadmin capacity. My opinion - if your machine is not on the HCL, don't even try it. I would not attempt to run ESX/ESXi on an unsupported whitebox like this.

Open source Xen or KVM or maybe even VMware Server is your best bet for this hardware.

What you really need to do is buy a SUPPORTED host, like my all time favorite HP DL380G5/G6. Nothing is truly free, so you need supported server hardware, bottom line.

---

### Post by pizmooz on 2009-08-03
> **PilotJLR said:**
> I work with VMware everyday, both in a consulting and sysadmin capacity. My opinion - if your machine is not on the HCL, don't even try it. I would not attempt to run ESX/ESXi on an unsupported whitebox like this.

Open source Xen or KVM or maybe even VMware Server is your best bet for this hardware.

What you really need to do is buy a SUPPORTED host, like my all time favorite HP DL380G5/G6. Nothing is truly free, so you need supported server hardware, bottom line.

true dat!

---

### Post by jamesrfla on 2009-08-03
> **PilotJLR said:**
> I work with VMware everyday, both in a consulting and sysadmin capacity. My opinion - if your machine is not on the HCL, don't even try it. I would not attempt to run ESX/ESXi on an unsupported whitebox like this.

Open source Xen or KVM or maybe even VMware Server is your best bet for this hardware.

What you really need to do is buy a SUPPORTED host, like my all time favorite HP DL380G5/G6. Nothing is truly free, so you need supported server hardware, bottom line.

I don't really have that much money for this server. It wouldn't hurt to try it. It is not like software is going to fry my hardware. If it doesn't work then I will use VMware Server.

---

### Post by Brazen on 2009-08-10
> **jamesrfla said:**
> Will the ESXi work with a Server with 2 500Gb hard drives in RAID 1? I guess I will go with ESXi instead of ESX. I am also looking into Citrix XenServer and Xen. Although I am not sure how you mange those. If it is free I will consider them.

Xen?  Are you masochist?  If you are then go with Xen.  Otherwise, go with libvirt on either kvm (if your processor and motherboard supports it) or kqemu.

---

