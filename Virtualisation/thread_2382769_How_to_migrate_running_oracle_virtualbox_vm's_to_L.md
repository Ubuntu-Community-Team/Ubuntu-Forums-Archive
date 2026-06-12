---
title: "How to migrate running oracle virtualbox vm's to LXD guests - export them as raw?"
date: 2018-01-17
forum: Virtualisation
---

### Post by dirk-lehmann on 2018-01-17
Thinking about to run virtual maschines on LXD as LXD guests instead on virtualbox installed on this ubuntu 16.04.3 LTS server:

How to migrate existing vm's? Simply export as OVA and and import them? Maybe OVA converting required?

First going to install LXD like this: [https://www.ubuntu.com/containers/lxd](https://www.ubuntu.com/containers/lxd)

Then going to get existing Virtualbox vm's up and startet with LXD instead of starting them with VirtualBox.

LXD seems me more performant to this constellation because LXD is *native* or *bare-metal *hypervisor and  VirtualBox ist *hosted *hypervisor.

Any performace comparison benchmarks to look to?

How to get existing virtualbox vms to raw format, like described here: [https://stgraber.org/2012/03/04/booting-an-ubuntu-12-04-virtual-machine-in-an-lxc-container/](https://stgraber.org/2012/03/04/booting-an-ubuntu-12-04-virtual-machine-in-an-lxc-container/)

On server with virtualbox are currently running two vm´s: One more ubuntu 16.04.3 LTS server and one Microsoft Windows 2012 R2 server with Microsoft SQL 2014 Express for SAP Business One.

Anyone who done this and has experience with this "performance tuning" and may give me hints, tipps and tricks in advance?

DL

---

### Post by dirk-lehmann on 2018-01-17
Can I convert my existing vmdk with help of this: [https://docs.openstack.org/image-guide/convert-images.html](https://docs.openstack.org/image-guide/convert-images.html) to raw and is this raw then a lxd compatible image file or not? Or do I need to convert to an other format? Do I need a other tool to convert existing vmdk files to be lxd compatible?DL

---

### Post by DuckHook on 2018-01-17
*Thread moved to **Virtualisation** as the more appropriate forum.*

---

### Post by TheFu on 2018-01-17
Windows won't run under LXD.  It isn't a hypervisor.

---

### Post by bmullan2 on 2018-05-07
[B]
[LXD v3.0.x has been released]("https://discuss.linuxcontainers.org/t/lxd-3-0-0-has-been-released/1491")[/B] (about 2 months ago) and with it came a [I][B]new tool lxd-p2c.

[/B][/I]lxd-p2c can import the filesystem of a physical machine -or- a VM to an LXD container for you.

See below...
**Physical to container migration with lxd-p2c**

 A new tool called lxd-p2c makes it possible to import a system&#8217;s filesystem into a LXD container using the LXD API.
 After building a copy of the tool, the resulting binary can be  transferred to any system that you want to turn into a container. 
Point  it to a remote LXD server and the entire system&#8217;s filesystem will be  transferred over the LXD migration API and a new container be created.
 
The main contributor for this feature, Stéphane Graber (LXD/LXC project lead), gave a  presentation about it at FOSDEM 2018, the video is available here:   [youtube.com/watch?v=JKztAWZOj9g]("https://www.youtube.com/watch?v=JKztAWZOj9g")

---

