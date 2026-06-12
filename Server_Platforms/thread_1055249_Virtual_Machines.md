---
title: "Virtual Machines"
date: 2009-01-30
forum: Server Platforms
---

### Post by SuperMike on 2009-01-30
I've been an Ubuntu workstation user for awhile now. I'm working on a PHP website for job search. I'm thinking of using Ubuntu Server for it on a dedicated server. As I do this, however, it seemed wise to me to go ahead and install Virtual Machines on it so that I can clone these easier, implement web nodes talking to a central database, and make seamless transfers of these VMs from one physical server to another, should we begin to grow.

I've been out of the loop for awhile with Ubuntu Server, so I'm looking for some help. I'd like to know what the recommended free VM tool is to use on Ubuntu Server, and perhaps any other advice you might have with these VMs.

As well, is there a minimum CPU or RAM requirement you might have if I plan to bring up a 4 VM Ubuntu Server initially? One VM will act as the central database server. It will have a twin VM that stays dormant and will be used for me to switch over the database. The other will be a VM for the website, and it will also have a failover twin should I need to engage that. I don't mean hot failovers in this case -- just failovers that I can manually engage.

---

### Post by SuperMike on 2009-01-30
Canonical appears to be putting good support behind JeOS (pronounced "Juice") and KVM. Juice is really geared more for virtual appliance solutions, which isn't what I'm looking for. KVM is the robust solution, and Canonical and Debian support it more than Xen (unlike every other Linux vendor), but KVM is picky about processors and you need a post-2006 processor. We'll have that on the production server, but I won't have this opportunity on my staging server, which has a processor from 2003 unfortunately.

All and all, I realized that we're in a time crunch on this project and I don't need to go putzing with this right now. Instead, I should deploy standalone, and then start experimenting with various VM solutions until I find one that seems to handle a decent load, has other features I like, and is easy to manage. Sun VirtualBox is one of those choices, for instance, and I have good experience with it. I just don't know how well VirtualBox stands up to the performance and manageability of KVM.

So, for now, VM stuff is on hold and I'll revisit it later.

---

### Post by SuperMike on 2009-02-02
Gosh, is this sub-forum dead? I've only had 60 views on this topic according to what the search stats show. And most have probably been me viewing the item. No one has even commented.

You would think that Ubuntu Server discussion sub-forum would be a popular place, as well as a discussion on Virtual Machines inside it.

---

### Post by tomwerner470 on 2009-02-02
I havn't tried KVM to be honest, but Virtualbox I have found can definetely stand on it's own performance wise - I read somewhere what made it quite unique was the way it managed ring 0 code and managed to get performance similar to VmWare and other enterprise products. However, I have found virtualbox might not be as pratical in a server environment in terms of management (however, it would make a great project, all the pieces are there, they just need tying together!). 

From what I did try of KVM it seemed quite good (performance especially) but didn't seem as complete as I would like, however, this was on a nice shiny quad-core hp server so your experiences may vary with the older hardware you mentioned.

Personally, for server virtualisation I would recommend VMware Server 2, it is relatively easy to install, gives quite good performance and has great VM Tools and management interface. 

I have discovered in the last few days something which may also fit the bill which I havn't had a chance to try out yet (no new hardware :-() which if you are running Ubuntu or some other Linux vms will be good as it uses containers instead of virtualisation (large boost in performance hopefully!)

It can be found at [http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

Bar proxmox which has a template based system for creating vm's, I would highly recommend the package ubuntu-vm-builder to generate nice little server installs - it uses some funky chrooting and scripting to generate a vm with all the settings you want (partitions, username, ip, dns, additional packages) configured ready for the target platform you choose (kvm, vmware, virtualbox (i think)).

Enjoy!

Welcome back to the forums (feels strange to say that considering I havn't been here long :-))....

Tom

---

### Post by Poleh on 2009-02-03
VMware ESX3i for unparallelled performance, scalability and functionality. The 3i version is freely downloadable, runs on most servers and if/when you get big enough to start needing advanced functionality you can purchase the full product and enable the advanced functionality with a license upgrade (no re-install required).

In addition Ubuntu is an officially supported VM platform for VMware so you're all good.

---

### Post by slakkie on 2009-02-04
I'm using vmware server 2 for my VM's. It is a joy to work with. I like the webbased control over my VM's. Virtualbox doesn't support that, which is a shame really. 

Although the ESX version at work doesn't have good support, because I cannot connect to the console of my VM's..

---

### Post by linux_tech on 2009-02-04
vmware works best for me as long as there is plenty of RAM

---

### Post by albinootje on 2009-02-04
> **SuperMike said:**
> Gosh, is this sub-forum dead?

You're first two posting were a little bit long, and not that so very clear in my opinion.
Perhaps you're better off with paid support elsewhere ;-)

Concerning your question, you didn't talk about OpenVZ, Linux Virtual Server, User Mode Linux, XEN.
If you want to run only Linux, and you want to be able to move installations around fairly easy, then I suggest OpenVZ.
I've been using OpenVZ for years now on a few servers, and I'm very happy with the flexibility and the overhead.

If you need it for a PDC samba server where clients need to be able to "join the domain", then it's more difficult because the default OpenVZ virtual network interface doesn't allow the broadcasting that is needed for that, you will have to use the alternative virtual network interface that OpenVZ offers, and *that* is not that easy to set up.

For things like web server, ssh server, and "regular samba file sharing" you can happily stick to the default virtual network interface of OpenVZ.

Also, OpenVZ has a learning curve, but so does e.g. XEN, UML.

---

### Post by albinootje on 2009-02-04
Here's some more to read :
[http://www.linux.com/feature/114214?theme=print](http://www.linux.com/feature/114214?theme=print)

[http://wiki.openvz.org/Main_Page](http://wiki.openvz.org/Main_Page)
[https://help.ubuntu.com/community/OpenVZ](https://help.ubuntu.com/community/OpenVZ)
[http://www.howtoforge.com/installing-and-using-openvz-on-ubuntu8.04](http://www.howtoforge.com/installing-and-using-openvz-on-ubuntu8.04)
[http://www.howtoforge.com/installing-and-using-openvz-on-ubuntu-8.10](http://www.howtoforge.com/installing-and-using-openvz-on-ubuntu-8.10)

Kernels with OpenVZ support for Ubuntu :
[http://packages.ubuntu.com/search?keywords=openvz](http://packages.ubuntu.com/search?keywords=openvz)

Precreated templates for the containers/VPSes/VEes :
[http://wiki.openvz.org/Download/template/precreated](http://wiki.openvz.org/Download/template/precreated)

[http://en.wikipedia.org/wiki/OpenVZ](http://en.wikipedia.org/wiki/OpenVZ)

GUIs for OpenVZ :
[http://webvz.sourceforge.net/](http://webvz.sourceforge.net/)
[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)
[http://www.vtonf.com/](http://www.vtonf.com/)

---

### Post by Poleh on 2009-02-04
> **slakkie said:**
> Although the ESX version at work doesn't have good support, because I cannot connect to the console of my VM's..

Care to ellaborate? You should be able to get to the server console in two ways:

1) using the virtual infrastructure client
 - point your broswer to the ESX host ip address
 - download the client from the web page above
 - connecting the clienit it to the ESX host IP

2) using the ESX web interface
 - slight reduced functionality but still ok
 - piont your browser to the ESX host ip address
 - log in with your ESX credentials
 - manage away

---

### Post by slakkie on 2009-02-04
> **Poleh said:**
> Care to ellaborate? You should be able to get to the server console in two ways:

1) using the virtual infrastructure client
 - point your broswer to the ESX host ip address
 - download the client from the web page above
 - connecting the clienit it to the ESX host IP

2) using the ESX web interface
 - slight reduced functionality but still ok
 - piont your browser to the ESX host ip address
 - log in with your ESX credentials
 - manage away

The Console plugin won't install. On the vmware community sites (aka the forums) this in known. See this thread: [http://communities.vmware.com/thread/173973?tstart=0&start=15](http://communities.vmware.com/thread/173973?tstart=0&start=15)

---

### Post by Poleh on 2009-02-05
sorry I don't understand your problem.

The VI client allows you to bring up the vm's "screen" which is to say it's exactly like you're at the keyboard and screen of the machine.

To get this straight, you have ESX and are trying to administer the VMs on that ESX from a workstation yes? What OS are you running on your workstation? If it's linux then I see your problem as the VI client is Windows only. Then your only option is Firefox and the web interface.

---

### Post by slakkie on 2009-02-05
The problem is that the plugin that is used to connect via the console does not install. The same plugin which comes with VMWare Server does work. But I cannot use it for ESX since it wants to install a different version, which cannot install (with the error message you see in the vmware forum thread).

---

