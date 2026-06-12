---
title: "Questions on Server and Network Configuration"
date: 2010-09-14
forum: Server Platforms
---

### Post by Nanix on 2010-09-14
I am considering self hosting a personal blog/website through Apache along with a Minecraft Server and Mail server. If I am not mistaken it is possible to do all on one machine correct? I will be using either a 2007 Intel iMac or an AMD self built from around early 2008. Will these be able to handle that amount of load?

I do however have some concerns about the security risks of having a server and how that might jeopardize my home network. Will that added traffic possibly attract people to security audit my system? How secure can I make things and how easily can that be done? 

[http://www.code-crafters.com/images/network2.gif](http://www.code-crafters.com/images/network2.gif)
I am envisioning that kind of network layout. How much stress will the server put on my network? Will it hog a ton of bandwidth?

Any information would be appreciated.

---

### Post by BobVila on 2010-09-14
> **Nanix said:**
> I am considering self hosting a personal blog/website through Apache along with a Minecraft Server and Mail server. If I am not mistaken it is possible to do all on one machine correct? I will be using either a 2007 Intel iMac or an AMD self built from around early 2008. Will these be able to handle that amount of load?

I do however have some concerns about the security risks of having a server and how that might jeopardize my home network. Will that added traffic possibly attract people to security audit my system? How secure can I make things and how easily can that be done? 

[http://www.code-crafters.com/images/network2.gif](http://www.code-crafters.com/images/network2.gif)
I am envisioning that kind of network layout. How much stress will the server put on my network? Will it hog a ton of bandwidth?

Any information would be appreciated.

This is done all the time. Either machine will handle a typical load without breaking a sweat. Upload speed from a residential connection will likely be a little crappy, but not terrible.

If you're concerned with exposing machines inside your network, run a few VMs on either box to house the net-facing applications. You can sandbox it a bit then, and it'll also give you the option to make snapshots, etc. for backups. This'll come in especially handy while you're setting things up; you can roll back if you break a config.

---

### Post by Nanix on 2010-09-14
> **BobVila said:**
> This is done all the time. Either machine will handle a typical load without breaking a sweat. Upload speed from a residential connection will likely be a little crappy, but not terrible.

If you're concerned with exposing machines inside your network, run a few VMs on either box to house the net-facing applications. You can sandbox it a bit then, and it'll also give you the option to make snapshots, etc. for backups. This'll come in especially handy while you're setting things up; you can roll back if you break a config.

Okay this sounds awesome. I've done VMs before so that shouldn't be a problem. Is VirtualBox sufficient for my purposes? I am most familiar with it. Do I need a separate VM for each application (Apache, Mail, Minecraft) or can I do it all in one?

I realized a problem with my plan. I want the mail server to be run under a different domain name than the blog/personal website. As I understand it I would need a separate IP address (and a separate internet connection) to do this.

---

### Post by BobVila on 2010-09-16
> **Nanix said:**
> Okay this sounds awesome. I've done VMs before so that shouldn't be a problem. Is VirtualBox sufficient for my purposes? I am most familiar with it. Do I need a separate VM for each application (Apache, Mail, Minecraft) or can I do it all in one?

I realized a problem with my plan. I want the mail server to be run under a different domain name than the blog/personal website. As I understand it I would need a separate IP address (and a separate internet connection) to do this.

Virtualbox will work. Some complain about its networking capabilites, but if you're happy/familiar with it, go ahead. 

Separation of vms will be up to you and the specs of your machine. If you want to keep things clean/secure, split 'em up. It'll take more resources, but rolling snapshots back while you get things set up will be easier as you'll only roll back a specific vm/application. If the server is lightweight or you feel comfortable lumping them all together on one vm, there's nothing stopping you.

As far as the domains, it's not really a problem. As long as you own the domains or are using free ones, you'll be fine. Just need to set the A/MX records with whoever is hosting your DNS to point to your external IP address and make sure the ports on the firewall are properly forwarded to your box. Multiple domains can resolve to the same IP address with no problems.

---

### Post by gordintoronto on 2010-09-16
The other question is whether your ISP will allow you to host a web site. Many ISPs block web requests going to a residential customer, and their service contract prohibits web site hosting.

---

