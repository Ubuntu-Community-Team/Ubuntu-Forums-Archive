---
title: "Ubuntu Server central management"
date: 2008-08-27
forum: Server Platforms
---

### Post by D8TA on 2008-08-27
With Canonical looking to bring Ubuntu more into the Enterprise environments I am wondering if there is a central management tool like Novell has, Zenworks Linux Management, for Suse. Ubuntu server would be nice from a cost perspective but there is a need for managing these servers centrally if one doesn't already exist. How or what are some of you others managing your Ubuntu servers? I would have probably close to 60 at one site and 180 throughout the US which would be both physical and virtual.

Thanks in advance.

---

### Post by gtdaqua on 2008-08-27
This is going to be interesting. I am subscribing to this thread.

But what you want to administer is the question. If you want to monitor, then you can use any NMS based on SNMP. I use Zenoss Core and some zenpacks to monitor the logical and physical health of all Ubuntu servers.

If you are looking at updates, then you can use apt-mirror to download all updates to one master server and have other servers pull from the master. You can also set the updates to happen automatically. 

What are the 'exact features' you are looking at when you want to manage centrally?

---

### Post by windependence on 2008-08-28
I agreem this should be an interesting thread. I would like to see something like Vmware VirtualCenter for virtualization on Ubuntu using KVM or Xen or whatever path they are going to take. It looks like KVM is promising right now. Hopefully it will mature into a good product.

Something to both monitor AND manage servers would be great though.

-Tim

---

### Post by D8TA on 2008-08-28
> **gtdaqua said:**
> This is going to be interesting. I am subscribing to this thread.

But what you want to administer is the question. If you want to monitor, then you can use any NMS based on SNMP. I use Zenoss Core and some zenpacks to monitor the logical and physical health of all Ubuntu servers.

If you are looking at updates, then you can use apt-mirror to download all updates to one master server and have other servers pull from the master. You can also set the updates to happen automatically. 

What are the 'exact features' you are looking at when you want to manage centrally?


I am coming from a patch/security standpoint. I am currently running Nagios for service monitoring on SLES servers and ZLM (Zenworks Linux Management) for patching and application updates. Where could I find more information pertaining to your scenario of using a master server and apt-mirror? Where on the other servers do you configure where to look for updates? In this case the secondary servers pointing at the master server for potential updates.

---

### Post by gtdaqua on 2008-08-29
> **D8TA said:**
> I am coming from a patch/security standpoint. I am currently running Nagios for service monitoring on SLES servers and ZLM (Zenworks Linux Management) for patching and application updates. Where could I find more information pertaining to your scenario of using a master server and apt-mirror? Where on the other servers do you configure where to look for updates? In this case the secondary servers pointing at the master server for potential updates.

apt-mirror is meant for conserving bandwidth so that your 100 ubuntu servers do not talk to internet directly for updates. However, an open solution to 'push' 'certain updates' to 'certain servers' is what would draw attention. 

[This]("http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror") is a nice guide detailing how to get apt-mirror working.

Ubuntu already maintains cfengine, a tool to manage networked machines and I quote ubuntu here: *"It takes a while to set up cfengine for a network (especially an already existing network), but once that is done you will wonder how you ever lived without it!"*

---

### Post by promodus on 2008-08-29
[http://www.canonical.com/projects/landscape](http://www.canonical.com/projects/landscape)

> What is Landscape?

Landscape is a system management service that allows you to manage multiple Ubuntu machines as easily as one. Canonical Support customers can manage many machines in a complex environment through a single web-based interface. Simply register the machines in Landscape to gain control of numerous systems management and resourcing tools. 

---

### Post by gtdaqua on 2008-08-29
Its $150 per year per node! If you want spend that, you might as well look at other enterprise linux management. That said, you might as well go ahead and look at RHEL servers. 

Is there an open-solution? cfengine2 looks promising.

But thanks for the Landscape suggestion though- some might be interested.

---

### Post by promodus on 2008-08-31
One question:
Are all these servers for the same company?




A few links for managing many systems, while not directly related to your situation:

[Smart Software synchronization]("http://209.85.171.104/translate_c?hl=en&sl=auto&tl=en&u=http://www.smart-software-synchronisation.de/index.php/Hauptseite&usg=ALkJrhh3iL_nUN3j6OmaiMaMuDzVtjxsTw")


[SYMSALABIM]("http://symsalabim.sourceforge.net/")

[Real men don't click]("http://isg.ee.ethz.ch/tools/realmen/index.en.html")

[OPSI]("http://www.opsi.org/")

[OCS Inventory]("http://www.ocsinventory-ng.org/")

[WPKG]("http://wpkg.org/")

[Unattended]("http://unattended.sourceforge.net/")

---

### Post by promodus on 2008-08-31
> **gtdaqua said:**
> Its $150 per year per node! If you want spend that, you might as well look at other enterprise linux management. That said, you might as well go ahead and look at RHEL servers. 

Is there an open-solution? cfengine2 looks promising.

But thanks for the Landscape suggestion though- some might be interested.

I'm not sure to the specifics of the licensing.
But the bottom line is, if it saves you time, and the amount saved is greater than the cost of the license... It's worth it. 

If you want everything *for free* the externalities would be **your time**.

Also, it may not just be $150 per node / year, there could be support along with that. A phone number to call when things aren't working right. Waiting for IRC or a forum can be gambling when servers are down and SLA's aren't met.

---

### Post by D8TA on 2008-09-06
> **promodus said:**
> One question:
Are all these servers for the same company?




A few links for managing many systems, while not directly related to your situation:

[Smart Software synchronization]("http://209.85.171.104/translate_c?hl=en&sl=auto&tl=en&u=http://www.smart-software-synchronisation.de/index.php/Hauptseite&usg=ALkJrhh3iL_nUN3j6OmaiMaMuDzVtjxsTw")


[SYMSALABIM]("http://symsalabim.sourceforge.net/")

[Real men don't click]("http://isg.ee.ethz.ch/tools/realmen/index.en.html")

[OPSI]("http://www.opsi.org/")

[OCS Inventory]("http://www.ocsinventory-ng.org/")

[WPKG]("http://wpkg.org/")

[Unattended]("http://unattended.sourceforge.net/")

Yeah, most of these links are for Windows. This is an Ubuntu forum so these are definitely no go, thanks anyways.

Landscape does look sweet but for the price I would purchase Zenwork Linux Management from Novell to manage Red Hat or Suse. 

I am going to try and take a closer look at cfengine and run with Ubuntu server and see what happens.

Thanks everyone!

---

### Post by Robstarusa on 2008-10-03
> **promodus said:**
> I'm not sure to the specifics of the licensing.
But the bottom line is, if it saves you time, and the amount saved is greater than the cost of the license... It's worth it. 

If you want everything *for free* the externalities would be **your time**.

Also, it may not just be $150 per node / year, there could be support along with that. A phone number to call when things aren't working right. Waiting for IRC or a forum can be gambling when servers are down and SLA's aren't met.

The problem is, production support even for something like RHEL is often not better than forums or irc.

---

### Post by bluefrog on 2008-10-03
OCSng inventory and GLPI can do what you want and that's what they are made for.

For windows? Well if you wish. Personally I prefer to run them on Linux.

The remark about time, support SLA... is a pretty good one anyway.
You can have everything for free but can you afford it?

James Dupin

---

