---
title: "Run server inside VMWare"
date: 2008-12-09
forum: Server Platforms
---

### Post by Moezzie on 2008-12-09
I read a brief thing about running a server inside VMWare a couple of months back. I cant really remember what it said or where to find it, but it got me thinking. 
It would be a very practical way to set the OS up inside VMWare and easily back it up when needed since VMWare stores everything in one file. And it would be very easy to transfer it between computers if one should break. Maybe even between different platforms.

My actual questions are:
1. Is it a good idea to set a server up like this? What are the pros and cons.
2. Is there a way to run VMWare in CLI and not having to install all the ubuntu desktop packages?

Thanks in advance!

---

### Post by kulshoks2121 on 2008-12-09
I am using vmware for my TEST server, I use the server for testing things for my local network. But as I see it, it would not be a practical way for using the vmware for ACTUAL servers, it would affect its performance and availability on the network.

---

### Post by PilotJLR on 2008-12-11
I disagree. You most certainly can put production workloads on VMware. The type of hypervisor and the computing power you have available to you would determine how far it can scale.

VMware Server is free and can handle basic workloads well, but it won't scale very far. This product used to be called GSX and was not free until about 3 or 4 years ago.

VMware ESXi is free and is suitable for enterprise workloads. ESX is likewise suitable but is not free.

Regardless of the hypervisor, have realistic expectations based on your hardware. If, for example, you have a 2 disc RAID 1 on your server, then don't expect a lot. Scaling VM's typically requires more i/o than local storage can provide.

---

### Post by Moezzie on 2008-12-14
I've got a server inside vmware up and running now to test it out. So far everything works great. My minimal install of Debian only takes 65mb ram + what vmware needs of corse.
I'll report back if anything should fail so you all know.

---

### Post by fjgaude on 2008-12-14
> **Moezzie said:**
> I've got a server inside vmware up and running now to test it out. So far everything works great. My minimal install of Debian only takes 65mb ram + what vmware needs of corse.
I'll report back if anything should fail so you all know.

Thanks, and please do keep us informed of your experiences!

---

### Post by HermanAB on 2008-12-14
Some types of services, for example Mail servers, Accounting systems and various others can be very hard to configure.  In these cases, it makes sense to install them inside a VM, so that you can keep a preconfigured VM 'on the shelf' and rapidly deploy it for a new customer.  

Also, some servers, while very hard to configure actually use very little resources - accounting for example.  Yet, each client would want to have a separate system.  Again, running these things in VMs make sense.

---

### Post by Moezzie on 2008-12-17
> **fjgaude said:**
> Thanks, and please do keep us informed of your experiences!
So, ive tried VMWare Server out for a couple of days now, and my feelings about it are kind of mixed.

Everything works fine, i get the occasional error here and there, but its usually pretty easy to fix.
Performance wise i cant complain. Im now running my webserver in a virtual machine and it has no significant impact. Im planning to add a mailserver in the near future, but i dont think its going to make a big difference.

On the other hand i've experience lots of trouble trying to move or copy virtual machines. The first thing i tried was to move a vm i created on my desktop computer to the server. That was a real hassle. At first i couldnt get the webclient to connect to the vm. After a fair amount to trying it finally worked. Then i think i spent about 4 hours trying to get the network in the vm to work, with no results. I tied it again with another vm, didnt work this time eather. I finally created a new vm on the server and installed everything over again and this time everything works great.
It seems as as long as you dont move or copy the vms they are going to run just fine. 

The web interface is really a great tool. VMWare has made an extension for firefox(and possibly other browsers) witch lets you view a running vms screen in a browserwindow, kind of like VNC but in firefox. 
I still think there is room for improvement though. I would love to see some kind of export/archiving tool witch preps a vm for copying or moving to another machine.

Ive also had a situation where the VMWare daemon did not shut down or start correctly which totally bricked the hole install so i had to remove and install it again.

Over all i think its a great tool, but with a little room of improvement. There is a good chance i need alot of improvement too :p

---

