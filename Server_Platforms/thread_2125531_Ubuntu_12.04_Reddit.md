---
title: "Ubuntu 12.04 Reddit"
date: 2013-03-14
forum: Server Platforms
---

### Post by keepow on 2013-03-14
Hi All,

Maybe this need to be in the third party sections, please move if so.

I run a virtual machine ubuntu 12.04, on wich i can browse the web. I can also visit and work in my local reddit installation this is the same server (localhost / reddit.local). 

Now in the domain i can ping the server. Seems to work perfectly fine.

The probleem is, i cannot acces the reddit instance through my domain PC.

Is this a common problem or can someone help me out with this.

Note: i am a new reddit user, this is the first install i did.

Yours,

Keepow

---

### Post by TheFu on 2013-03-14
> **keepow said:**
> Hi All,

Maybe this need to be in the third party sections, please move if so.

I run a virtual machine ubuntu 12.04, on wich i can browse the web. I can also visit and work in my local reddit installation this is the same server (localhost / reddit.local). 

Now in the domain i can ping the server. Seems to work perfectly fine.

The probleem is, i cannot acces the reddit instance through my domain PC.

Is this a common problem or can someone help me out with this.

I've never run a reddit server and have only visited the main website a few times.
If you can explain the server setup a little, perhaps someone can help solve the issue?  For example, I don't understand what a "domain PC" is or what "in the domain i can ping the server" - - Is this a name resolution issue or because the server isn't actually running?  Was there a how-to instruction that you followed?
Did you follow these [https://github.com/reddit/reddit/wiki/reddit-install-script-for-Ubuntu](https://github.com/reddit/reddit/wiki/reddit-install-script-for-Ubuntu) instructions? 
Did you read the FAQ? [https://github.com/reddit/reddit/wiki/FAQ](https://github.com/reddit/reddit/wiki/FAQ)
What do the log files show? [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

We'd like to help, but just need a little more information.

---

### Post by keepow on 2013-03-14
Basicly we have a domain, user accounts and servers pc's etc. are all in here. It is windows. We have 50 virtual servers more or less.

Now we decided to test reddit in a virtual ubuntu server. This is server is not connected in the domain, but is has a internet connection. 
From a windows pc i can ping the server by ip. From the ubuntu machine i cannot ping my pc wich i currently work on.

I can browse the reddit instance only on the ubuntu machine the host name is reddit.local. I can ping the machine, the machine is connected to the web. What do i need to do to see "reddit.local" on my domain pc.

I hope this is a little clear? If not please say so.

---

### Post by TheFu on 2013-03-14
> **keepow said:**
> Basicly we have a domain, user accounts and servers pc's etc. are all in here. It is windows. We have 50 virtual servers more or less.

Now we decided to test reddit in a virtual ubuntu server. This is server is not connected in the domain, but is has a internet connection. 
From a windows pc i can ping the server by ip. From the ubuntu machine i cannot ping my pc wich i currently work on.

I can browse the reddit instance only on the ubuntu machine the host name is reddit.local. I can ping the machine, the machine is connected to the web. What do i need to do to see "reddit.local" on my domain pc.

I hope this is a little clear? If not please say so.

Microsoft "domains" mean nothing to UNIX/Linux systems.  It was a poor choice of names by Microsoft and leads to much confusion. Unless you specifically force Linux to talk microsoft domains, it will not. I have not done this - EVER.

DNS could be the issue. A FQDN [https://en.wikipedia.org/wiki/Fully_qualified_domain_name](https://en.wikipedia.org/wiki/Fully_qualified_domain_name) is made up of the "hostname" AND the internet "domain name."  Wikipedia will explain these in more detail if you need help.  A FQDN relates to 1 or more IP addresses using DNS or other methods.

Do the clients have some way to resolve the Linux hostname, reddit.local, used?  The Linux server does not need to resolve any of the client PCs.  

You have a Windows networking question here.  Do whatever you would to make any Windows PC see any other Linux (or IP) host any where on the local network. That can be by running a DNS server, making an entry in the existing DNS server or modifying "hosts" files on each PC.  On Linux, this file is located in /etc/hosts, but I don't recall where Microsoft buries it ... somewhere under drivers/ I think.  For any network with more than 5-10 machines, running DNS is the easy way to handle name resolution.  How your setup does it and who is responsible for managing - I cannot answer.

You can run a DNS on Linux too, but that is probably not the best way in a Microsoft shop.  Many MS-shops use an MS-Windows DNS server as part of their DHCP server.  Talk to those guys. That is where I'd start.

**I could have headed completely in the wrong direction so far too.** For the virtual machine, which sort of networking was created?  Does it have a static IP?  Is that IP route-able on the LAN? Is it on the same subnet as the other systems?  Bridge-mode is usually the easy way to handle this. Forcing it to host-only or internal-network will block access from any systems outside the VM unless additional, more complex configurations are employed.  Using bridge is what I do for almost all VMs.

So, if the server has a static IP, who told you which IP to use?  That same person should be able to setup the DNS entry OR they will explain why it cannot be used on the network.

**Update:**
To fix whatever this current issue is, 
* ping the VM from any client by IP address. Does this work?
* ping the VM from any client by the FQDN. Does this work?
* nslookup from any client using the FQDN, then using the IP address. These should return the opposite FQDN or IP.

Which of these fails tells you if the issue is at the network level or the DNS level.

Anyway, I hope this is helpful.

---

