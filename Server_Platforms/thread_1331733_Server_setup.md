---
title: "Server setup"
date: 2009-11-19
forum: Server Platforms
---

### Post by SvEnX on 2009-11-19
Hello everybody!

What is the best option to set up Ubuntu as Server for web hosting and other services?

1. Ubuntu JEOS + VMware with 1 Guest for web hosting and 2 another Guests for game servers etc.
2. Standart Ubuntu Server edition, where LAMP is set up on Host machine and add 2 another Guests?

---

### Post by spikyjt on 2009-11-19
This all depends on what the other services are, the volume of traffice the web server will handle, and how powerful the machine is...

---

### Post by SvEnX on 2009-11-19
I have a SUN FIRE X2200M2 with DUAL AMD Opteron 2210 with 4GB of ram.
Lets say it will be hosting less than 50 web domains with relativly low traffic. Will the option 1 suffer with latency, if it's Guest host? I find that the model/option 1 is better and more secure. I'm I wrong?

---

### Post by Cheesemill on 2009-11-19
If your server is supported (I believe that it is) then I would go for VMware ESXi + 3 Guest VMs running JeOS.
This way all of your virtual servers should run at bare-metal speed.


> 1. Ubuntu JEOS + VMware with 1 Guest for web hosting and 2 another Guests for game servers etc.Do you mean you are thinking of installing JeOS as your host OS?
JeOS is for VM guests, not for a host OS (I do apologize if I've understood incorrectly).

---

### Post by SvEnX on 2009-11-20
> **Cheesemill said:**
> If your server is supported (I believe that it is) then I would go for VMware ESXi + 3 Guest VMs running JeOS.
This way all of your virtual servers should run at bare-metal speed.


Do you mean you are thinking of installing JeOS as your host OS?
JeOS is for VM guests, not for a host OS (I do apologize if I've understood incorrectly).
I'm afraid I cannot affort ESXi, is VMware Server 2.0 really that bad? I think others like Xen, KVM and so long don't have that nice Web Interface, correct me, if I'm wrong.

No, you are right, I was thought that JeOS is for Host machine and not not Guest. Boy, I'm stupid...

---

### Post by spikyjt on 2009-11-20
Your issue is not whether all your 3 servers could run at bare metal speed by themselves, but whether your server can handle the total load of all three. You don't say what the other 2 will be doing. Your machine will be more than powerful enough for your web server, but if the others hog the processor, it won't be.

Regarding virtualisation platforms, I've personally found the free VMware Server to be very capable, however KVM is faster, as is VirtualBox (my preference). VirtualBox has a pretty GUI, but there are GUIs for KVM too.

There is no security advantage to a virtual machine as opposed to a bare metal server. The same security rules apply as for a bare metal box. However separating your web server from other machines may be a security advantage (depending on what the others do).

---

### Post by SvEnX on 2009-11-20
Other two are mostly game servers that are not ported for Linux platform. That's why I need the Windows guests afterall. Actually, I think 1 Windows Guest is enought. What are your thoughts? For example, if I split the resources to half, one for Host another half for Guest and leave the LAMP to bare metal?

---

### Post by Cheesemill on 2009-11-20
> **SvEnX said:**
> I'm afraid I cannot affort ESXi

It's free :)

[http://www.vmware.com/go/get-free-esxi](http://www.vmware.com/go/get-free-esxi)

---

### Post by SvEnX on 2009-11-20
Does this include Virtual Infrastructure (VI) Web Access?

---

### Post by Cheesemill on 2009-11-20
I don't think it has web access, it's meant to be controlled using the vSphere client which functions pretty much identically to the VMware Server 2 web interface only faster as it's a standalone app (this also means that the server doesn't have the extra overhead of running the interface).

All you need to do is point your browser at your ESXi server and you'll get a download link.

At the moment the vSphere client is for Windows only I'm afraid so this may be a problem if you don't have a Windows machine (although they are working on a linux client).

---

### Post by SvEnX on 2009-11-20
How big is the performace difference, between ESXi and VMware Server?
Forgot that I don't have HW RAID. I read somewhere, that ESXi doesn't support software, so I guess I'll stick on VMWare server.

If we go back to my initial question, which is better option on VMware server?

---

