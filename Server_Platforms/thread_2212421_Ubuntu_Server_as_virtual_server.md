---
title: "Ubuntu Server as virtual server"
date: 2014-03-21
forum: Server Platforms
---

### Post by wvw on 2014-03-21
Hello

I have a bit of an awkward question in that the question consists of multiple questions and I am not sure if this is the correct forum. However if it is incorrect please forgive my ignorance!

Basically what I am trying to do is install Ubuntu server on Windows Server 2012 Essentials using Virtualbox. The reason for this is that I am looking for an alternative to MS Exchange for the office staff. However I am not sure if this will work and would like to know from others whether they have done this (or something similar) and how it turned out for them? I am happy to give it a try, however I am first trying to get some info before I end up doing this.

If someone else has done something similar to the above (i.e. Ubuntu Server in a virtual environment on Windows Server) what they used to setup the environment (if they haven't used Virtualbox) and how it worked for them?

TIA
wvw

---

### Post by TheFu on 2014-03-21
The virtualization used isn't as important as it once was. I know companies who use virtualbox (must pay licenses if used inside a company like this). However, people here are most likely to have used "server-class" virtualization hypervisors like:
* ESXi
* Xen
* KVM / libvirt
* openVZ
You know - Linux-based virtualization - designed for server use.

Virtualbox is fine for workstation -class VMs and desktop-on-desktop VM needs, but for servers the above are better choices - IMHO.  Linux hosts have much less overhead than Windows, which is better for the guestOSes installed.

So - No, I haven't done what you seek.

---

### Post by thufirhawat2 on 2014-03-21
> **TheFu said:**
> The virtualization used isn't as important as it once was. I know companies who use virtualbox (must pay licenses if used inside a company like this). However, people here are most likely to have used "server-class" virtualization hypervisors like:
* ESXi
* Xen
* KVM / libvirt
* openVZ
You know - Linux-based virtualization - designed for server use.

Virtualbox is fine for workstation -class VMs and desktop-on-desktop VM needs, but for servers the above are better choices - IMHO.  Linux hosts have much less overhead than Windows, which is better for the guestOSes installed.

So - No, I haven't done what you seek.

I agree with this post. Having a production server be a virtual machine is a great idea, but you need enterprise level virtualization software, ideally. I have a test server in virtual box at my house that I use just to make sure I understand how to install and configure new software on my live Ubuntu servers, but I would not use virtualbox to run a production server. Since your host is windows based, I would also recommend Hyper-V. That is what I use at the office, and you can export VMs back and forth between it and virtualbox if you still want to use virtualbox to test with or something.

---

### Post by TheFu on 2014-03-21
> **wvw said:**
>  alternative to MS Exchange for the office staff. 

Zimbra (what we run the last 6+ yrs)
Zafara
Citadel

Step away from google-domains, if you care about privacy.

---

### Post by Lars Noodén on 2014-03-21
[Kolab](http://kolab.org/overview) is another option.  Like Citadel, it is quite modular.

Recently [OpenChange](http://www.openchange.org/) was released as a transparent replacement for MS Exchange.  Supposedly you can get it running without having to change any of the clients.  I don't suppose that it loses mail at the rate MS Exchange does however.  

[http://doc.zentyal.org/en/openchange.html](http://doc.zentyal.org/en/openchange.html)

It might help you out of a tight corner and give time to consider longer term solutions on both the client and the server.

---

