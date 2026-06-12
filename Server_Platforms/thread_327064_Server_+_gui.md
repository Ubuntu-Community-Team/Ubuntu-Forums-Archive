---
title: "Server + gui"
date: 2006-12-28
forum: Server Platforms
---

### Post by jonathan.lees on 2006-12-28
I'm thinking about replacing Fedora Core on my servers with Ubuntu for the LTS. I'm also considering installing VMware and running virtual machines which I guess will need some gui work.
 
If I install 6.06 and then install xfce, can ubuntu be configured to not boot straight into X and for xfce to run upon request, like Fedora's startx script.

thanks

---

### Post by Mike'sHardLinux on 2006-12-28
Yes, you can do that.

I just just did a fresh install of Ubuntu server without a gui, and also installed VMware server. You don't need to install a gui on the server, only some of the libs for X.

I connect to the VMware server and create/run the virtual machines from another machine.

---

### Post by jonathan.lees on 2006-12-29
Did you install the MUI to run / monitor your virtual machines? Or can you remotely run / monitor via SSH and if so how?

 I'm thinking about starting small with consolidating non critical print servers to begin with.  I also run M$ servers and I'm debating putting a secondary DC on it too. Can anyone advise me a bit on this, like is anyone running VMware with anything more important than simple print servers?

thanks

---

### Post by Mike'sHardLinux on 2006-12-29
Hi!

What is 'MUI'?

I installed the VMware server on the CLI only server, mostly as an experiment to see how well this would work, and if there's any use to even doing this. I have the VMware Server on the server. I also have VMware installed on a "workstation". On the workstation, I run Vmware and connect "Remote Host", which is the server. Then, I can create/edit/delete virtual machines that are being hosted by the server. That is why the server does not need a GUI to run VMware server.

If you are wanting to run a regular server, as in print servers, file servers, domain controller, mail servers, web servers, etc....; then you don't need Vmware. 

I think I am unclear on exactly what it is you are trying to do. :-k 

If you want to run a Linux server for a windows network, look into LDAP, Samba, and CUP. I believe those are what you need, not Vmware.

---

### Post by Mike'sHardLinux on 2006-12-29
I just realized you are replacing a FC server. I also run a couple of FC servers (FC4), and am thinking of replacing them with Ubuntu LTS. But, I will only be running the CLI. I'm trying to learn more of the inner workings, and using a GUI makes it far too easy.

Which Fedora are you currently using?

---

### Post by Brazen on 2006-12-29
I believe what VMWare calls the "MUI" is the web interface, which of course does not require a gui on the server (you access it from a workstation, but you install it on the server).  The VMWare Client is what you need to install on a workstation to access the virtual machines (the web interface is pretty sparse).

I had used VMWare Server extensively last year, with critical servers running on it.  Never had any problems with it, in fact it was a godsend one time when I had to restore a snapshot.  We have since moved most of those to ESX Server, but we have two highly critical servers still running in virtual machines on the free VMWare Server.

It sounds like you have the right idea, installing VMWare Server and then putting all your services on servers in the virtual machines.  Keep your services on seperate virtual machines (eg print services in one, domain controller in another), and you'll be glad you did.  It's much easier down the road than loading everything up on a single server (real or virtual).

---

### Post by jonathan.lees on 2006-12-29
That's right Brazen, I want to use VMware or perhaps Xen and put my network services in virtual machines starting with the less critical print servers moving up to authentication servers. I'm hoping that not only will this improve management but also cut down on our electricity bill. I currently use FC5 for proxy/filter/Firewall/DHCP/NTP/email servers, been using it since Redhat9, I can't be bothered to do another upgrade to FC6 and so on!
thanks for the advice.

---

### Post by Brazen on 2006-12-29
> been using it since Redhat9, I can't be bothered to do another upgrade to FC6 and so on!So are you switching to Ubuntu for the LTS then?  I also switched from Fedora 4 (had been using it since taking over an outdated Redhat5 (I think) around the time 8 was just coming out).

---

### Post by Mike'sHardLinux on 2006-12-29
I never thought of using virtual machines in that way. Sounds interesting.

How many VMs do you think you can efficiently run on one server? What kind of server are you running? Single, dual or multi processor? How much RAM? Seems like that's a good idea, but will require a heavily configured machine versus running all the services from the host OS.

Do you happen to have any links with information or examples of this? I'm going to google right now.

---

### Post by Brazen on 2006-12-29
> **Mike'sHardLinux said:**
> I never thought of using virtual machines in that way. Sounds interesting.

How many VMs do you think you can efficiently run on one server? What kind of server are you running? Single, dual or multi processor? How much RAM? Seems like that's a good idea, but will require a heavily configured machine versus running all the services from the host OS.

Do you happen to have any links with information or examples of this? I'm going to google right now.

Running a single service per server has been considered a "Best Practice" among enterprise server admins for ages.  This is one of the biggest issues virtual machines are meant to tackle (that and testing/development work).  How many vms it can handle depends on the load of each server.  VMWare says "10" on each ESX Server, but the way processor and RAM capacity is filling up, I'm guessing we will get more like 4-6.  These are on dual 3.6 Ghz Xeon/4GB RAM blade servers.

At home I had 1 Apache server, 1 Samba server, and 1 MySQL server (all in vms) on a 600 mhz Celeron with 1GB PC100 SD-RAM.  All these were GUI-less and I really only noticed a lag in serving up files or webpages when I had a 4th vm running for testing, but it did take a pretty big hit when I fired up that 4th machine.  If you run all GUI-less, the linux servers are really efficient with resources, most of the resources are used by the service you are providing, so there is less overhead than you might think running seperate virtual machines this way.

To be honest, I did eventually combine all my services onto the host OS in hopes of getting some speed increase, but it still bogs down once I power up that 1 testing virtual machine, although _maybe_ not as much.

---

### Post by Mike'sHardLinux on 2006-12-29
Jonathan, sorry for hijacking your thread. :( 

Brazen, thanks for the information!!  :-D 

This gives me a whole new perspective and things to experiment with at home. In order to test out all these concepts at home, and being on a limited budget, I bought a used poweredge server (dual Piii866) which will probably limit how much I can do. I also want to get a storage array to play around with, but it's hard for me to know what hardware I should get. I've been doing a lot of googling lately.

I assume I can run a VERY stripped down host OS on the server, with just enough to run VMware server, and try out running several VMs as you stated. I really want to try out Linux from Scratch, too.

---

### Post by rickyjones on 2006-12-29
I spent the summer working at a global corporation. Heavy Microsoft shop - one of the guys on my team was leveraging VMWare's ESX Server to transition from physical boxes to virtual boxes. Basically we were consolidating as many servers as possible. Great idea, and this is the way of the future I think.

---

### Post by jonathan.lees on 2006-12-30
> So are you switching to Ubuntu for the LTS then?
Yep, I've been using Ubuntu on my desktop since 6.06, it works really well for me and I especially appreciate the speed of apt compared with yum. I tried out FC6 when it came out but I'd been grabbed by the Ubuntu bug by then and switched back but to 6.10.

On the server side, I've already built a test server at work, it installs a whole lot quicker than FC, 1 disc as opposed to 5, and then all the services I used were installed via apt. I was impressed with the speed of install, I should imagine that the services will be equally a stable but won't know until I go live. I manage a network at a high school where we have over 1200 users with potentially 400 of them using the services concurrently.

> Jonathan, sorry for hijacking your thread. No worries Mike, surely this is what forums are for!

For me server consolidation using virtualization is the way to go if only to cut down our electricity costs.

---

### Post by Brazen on 2006-12-30
> **jonathan.lees said:**
> Yep, I've been using Ubuntu on my desktop since 6.06, it works really well for me and I especially appreciate the speed of apt compared with yum. I tried out FC6 when it came out but I'd been grabbed by the Ubuntu bug by then and switched back but to 6.10.

On the server side, I've already built a test server at work, it installs a whole lot quicker than FC, 1 disc as opposed to 5, and then all the services I used were installed via apt. I was impressed with the speed of install, I should imagine that the services will be equally a stable but won't know until I go live. I manage a network at a high school where we have over 1200 users with potentially 400 of them using the services concurrently.You say you went back to Ubuntu at 6.10, but are you still using 6.06 on the server at work?  You know 6.10 does not have LTS and 6.10 is more of a bleeding edge release, which could present some funkiness.

---

### Post by jonathan.lees on 2006-12-30
I use 6.10 at home and work for a desktop, I'm still using FC 5 on my servers!

---

