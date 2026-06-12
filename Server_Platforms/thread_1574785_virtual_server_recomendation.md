---
title: "virtual server recomendation"
date: 2010-09-14
forum: Server Platforms
---

### Post by jonny.milano on 2010-09-14
Is there a good service or product out there that one could buy/use running on ubuntu-server?

---

### Post by arrrghhh on 2010-09-14
Are you looking for a hosted solution that's off-site...?

If that's the case, I wouldn't worry about virtualization, the provider will handle all of that stuff.

If you're looking for personal reasons, it really depends on what you need.  VirtualBox is good, but needs a host OS.  ESX-i is great... and as far as I know you can get most of the pieces for free, you just won't get any support or vSphere, etc.

Most of the virtualization platforms do require a host OS tho...

---

### Post by e79 on 2010-09-14
> ..ESX-i is great... and as far as I know you can get most of the pieces for free..For only one virtual server/machine ,VMware ESXi (now called VSphere Hypervisor) might be overkill. If you are looking to setup a Home/Small Office Virtual Server yourself, like 'arrrghhh' stated, VirtualBox could do the job. Other options (if you have a dedicated machine would be VMware Server (free version) running on top of Linux or if your server is already installed with a M$ product, you could always try M$ Virtual Server (also free) or M$ Hyper-V.

VMware ESXi :  [http://www.vmware.com/products/vsphere-hypervisor/index.html](http://www.vmware.com/products/vsphere-hypervisor/index.html)
VMware Server : [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)
VirtualBox : [http://www.virtualbox.org/](http://www.virtualbox.org/)
M$ Products : [http://www.microsoft.com/windowsserversystem/virtualserver/downloads.aspx](http://www.microsoft.com/windowsserversystem/virtualserver/downloads.aspx)


Hope this helps

---

### Post by jonny.milano on 2010-09-14
> **e79 said:**
> For only one virtual server/machine ,VMware ESXi (now called VSphere Hypervisor) might be overkill. If you are looking to setup a Home/Small Office Virtual Server yourself, like 'arrrghhh' stated, VirtualBox could do the job. Other options (if you have a dedicated machine would be VMware Server (free version) running on top of Linux or if your server is already installed with a M$ product, you could always try M$ Virtual Server (also free) or M$ Hyper-V.

VMware ESXi :  [http://www.vmware.com/products/vsphere-hypervisor/index.html](http://www.vmware.com/products/vsphere-hypervisor/index.html)
VMware Server : [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)
VirtualBox : [http://www.virtualbox.org/](http://www.virtualbox.org/)
M$ Products : [http://www.microsoft.com/windowsserversystem/virtualserver/downloads.aspx](http://www.microsoft.com/windowsserversystem/virtualserver/downloads.aspx)


Hope this helps

It does help! Now, what about a provider (commercial) off site so I don't have to worry about admining the server myself??

---

### Post by CharlesA on 2010-09-14
> **jonny.milano said:**
> It does help! Now, what about a provider (commercial) off site so I don't have to worry about admining the server myself??

Any decent VPS will do.

---

### Post by bmathis on 2010-09-14
[BlueMile Cloud]("http://my.bluemilecloud.com/aff.php?aff=059") is good. I have 2 vps' with them (used to be FiveBean).

---

### Post by e79 on 2010-09-14
> It does help! Now, what about a provider (commercial) off site so I don't have to worry about admining the server myself??If you mean not having to set up the Virtualizing platform on which Ubuntu Server would run as a virtual machine; maybe some ISP or Internet Providers in your area could provide you with that service for a price.

The company I work for for asked me to build such system a while ago; we bought a server and rent a 'rack space' in a DataCenter (where all critical systems are protected and redundant, you don't have to worry about fire, flood, thieves, electrical hazard etc). I then installed VMware ESXi as a Bare-Metal OS and started building virtual machines on top of it (Linux and Windows server).

But if you are looking at only 1 Ubuntu Server, you don't necessarily need Virtualization, only one dedicated server and rent some rack space in a Datacenter and install Ubuntu Server and voila !

---

### Post by mdlueck on 2010-09-15
We too are shopping for a next Ubuntu VPS provider. Do NOT go with a vendor which uses Virtuozzo as it has a number of most annoying limitations.

1) Being able to remotely attach to the server console, watch the boot process, fix sshd if it should become disabled or otherwise, etc...

2) Do the official Ubuntu Linux distro upgrades, such as from 9.10 --> 10.04 LTS.

3) Run IPTables. Which really means run the standard Ubuntu kernel which does not have things neutered out that IPTables requires!

4) Access to /etc/fstab to control mounting options. Specifically Virtuozzo does /etc/fstab from the admin side (hosting provider side) and the version of Virtuozzo that is running the VPS we administer does not support ACL's on the filesystem... so the hosting provider can not just put a check mark in the ACL box as there is none in this version of Virtuozzo.

Xen seems to support those things... but the Xen camp is fragmented with various flavors of Xen... which I have not had the time yet to fully understand, decide on which flavor, shop for a vendor which runs said flavor, etc...

VMware is said to support the same, but I have yet to find a VPS vendor serving on a VMware platform.

Our current provider has a total ban on adult content in their hosting environment. I appreciate that about them. In my initial checking, seems that is rather uncommon amongst hosting providers. So if I wish to maintain that aspect... Oy!

Sincerely,

---

### Post by jonny.milano on 2010-09-15
mdlueck, e79: thanks guys! Actually, thanks to all! This is most helpful. I have setup server myself before (only with ubuntu) but would like the safety of an off-site solution as I'm ready now to start running some more critical things. Is Rackspace any good?

---

### Post by mdlueck on 2010-09-15
> **jonny.milano said:**
> Is Rackspace any good?

I have not reviewed their offerings in a few months. My impression is that they tipped more and more to dedicated server hosting. Prior to VPS getting popular, I thought they offered shared web hosting, but I looked a few years ago and could not find such at Rackspace. Even then (a few years ago) seemed like they were focusing on dedicated servers.

---

### Post by mdlueck on 2010-09-15
> **mdlueck said:**
> My impression is that they tipped more and more to dedicated server hosting.

I take that back. Seems at Rackspace they call their VPS a cloud.

"Cloud Servers - Virtual Server Hosting"
[http://www.rackspacecloud.com/cloud_hosting_products/servers](http://www.rackspacecloud.com/cloud_hosting_products/servers)

And in the specs I see that they are using Xen. There are a few forks in the Xen world, so I need to decide which fork of Xen works best for us and verify which fork Rackspace is using.

---

### Post by Baked- on 2010-09-15
Since no one has mentioned it I would recommend citrix xen.  They have a free version that has almost all of the features and if you do decide you need the enterprise level features licensing for that is MUCH cheaper than vmware.

---

### Post by jonny.milano on 2010-09-15
> **mdlueck said:**
> I take that back. Seems at Rackspace they call their VPS a cloud.

"Cloud Servers - Virtual Server Hosting"
[http://www.rackspacecloud.com/cloud_hosting_products/servers](http://www.rackspacecloud.com/cloud_hosting_products/servers)



Exxxcccelllent...

---

### Post by gmanigault on 2010-09-15
> **e79 said:**
> For only one virtual server/machine ,VMware ESXi (now called VSphere Hypervisor) might be overkill. If you are looking to setup a Home/Small Office Virtual Server yourself, like 'arrrghhh' stated, VirtualBox could do the job. Other options (if you have a dedicated machine would be VMware Server (free version) running on top of Linux or if your server is already installed with a M$ product, you could always try M$ Virtual Server (also free) or M$ Hyper-V.

VMware ESXi :  [http://www.vmware.com/products/vsphere-hypervisor/index.html](http://www.vmware.com/products/vsphere-hypervisor/index.html)
VMware Server : [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)
VirtualBox : [http://www.virtualbox.org/](http://www.virtualbox.org/)
M$ Products : [http://www.microsoft.com/windowsserversystem/virtualserver/downloads.aspx](http://www.microsoft.com/windowsserversystem/virtualserver/downloads.aspx)


Hope this helps



Isn't ESX 64 bit?

---

### Post by CharlesA on 2010-09-15
> **gmanigault said:**
> Isn't ESX 64 bit?

They have a 32-bit version as well, but why run a 32-bit server?

---

### Post by jonny.milano on 2010-09-21
Just an FYI. I have been in touch with Rackspace and have been very impressed with the level of service. Also, the price is nice.. and no, I don't work for them!

---

