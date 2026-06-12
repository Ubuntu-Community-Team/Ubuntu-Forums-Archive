---
title: "MAAS hysteria and OpenStack, not open-wallet"
date: 2013-04-19
forum: Ubuntu Cloud and Juju
---

### Post by jandersonlee on 2013-04-19
Thanks heavens I have thick hair, otherwise I'd be balding from pulling it out by now.

I'm trying to (re)build a cluster that was put together using 10.04 LTS + PXE boot + kickstart + custom scripts. I'd like to switch to 12.04 LTS using something more modern and less custom, like say MAAS, from which I could bootstrap Puppet, OpenStack, etc. (The OpenStack install docs seem to say, "first start with a 12.04 cluster...")

But when I've tried test installs with MAAS:

1. It's not clear how best to work with multiple network interfaces, 
2. the auto-magic package install seems to hide *too many* parameters,
3. the standard Rabbit install, for one, seems to be insecure, 
4. it seems to want to take-over managing the whole subnet (not possible), and
5. I'm not finding documentation on how to clean it up, secure it, adapt it.

Can anyone help point me to more detailed documentation on how to either (a) turn a test installation into a production-quality one or (b) step-by-step how to install a production-grade version of MAAS?

Barring that, are people using other open-source/public-domain tools to set up OpenStack on Ubuntu clusters these days, or have we moved on the the point where it's open-wallet, hire-consultant? (Alas, no budget line for that.)

Thanks.

Jeff Anderson-Lee

---

### Post by tgalati4 on 2013-04-19
I would look into [http://devstack.org](http://devstack.org) if you want to install/manage your own cloud service.  

The official maas documentation:  [http://maas.ubuntu.com/docs/install.html](http://maas.ubuntu.com/docs/install.html)

The *devstack* scripts are designed for devops--turning development cloud services into operational services.

---

### Post by jandersonlee on 2013-04-19
> **tgalati4 said:**
> I would look into [http://devstack.org](http://devstack.org) if you want to install/manage your own cloud service.  

The official maas documentation:  [http://maas.ubuntu.com/docs/install.html](http://maas.ubuntu.com/docs/install.html)

The *devstack* scripts are designed for devops--turning development cloud services into operational services.

Right, but [http://devstack.org/guides/multinode-lab.html](http://devstack.org/guides/multinode-lab.html) says:

    "You need to have a fresh install of Ubuntu 12.04 (Precise) on all of your nodes."

So what's the recommended way to do *that*? The MAAS install (at least the media based one) seems to assume it can take-over your subnet. I'll try the package-based install and see if that is any better.

---

### Post by tgalati4 on 2013-04-19
How many nodes are you looking to manage?  The docs recommend loading the minimal Precise install (27 MB) plus whatever additional packages that you need.  Typically you set up one machine with all of your services, then reroll into an ISO--essentially making a custom distro.  Then install that custom distro on all of your nodes.

I'm not sure why taking over a subnet would be a problem.  You could simply create another subnet for nodes that you don't want managed by the maas.

---

### Post by castrojo on 2013-04-20
Have you seen [https://help.ubuntu.com/community/UbuntuCloudInfrastructure](https://help.ubuntu.com/community/UbuntuCloudInfrastructure) yet?

devstack is for running openstack on one machine for development.

---

### Post by jandersonlee on 2013-04-22
Yes. Neither option (1) "Ubuntu Cloud Live Image", nor (2) "Ubuntu Cloud Infrastructure with MAAS and Juju", seems to produce the sort of result I want and option (3) "Install Ubuntu Cloud Infrastructure from packages: the hard way" is apparently left as an exercise for the reader.

---

### Post by jandersonlee on 2013-04-22
> How many nodes are you looking to manage?

O(100)

> Typically you set up one machine with all of your services, then reroll  into an ISO--essentially making a custom distro.  Then install that  custom distro on all of your nodes.

Most of the machines don't have CD drives. 100 USB stick installs would be painful. Looking to find a less painful way to roll out the initial cluster. Was hoping MAAS might be it, but not much luck so far. I've been using kickstart+bash with u10.04 but was hoping for something more integrated with u12.04.

> I'm not sure why taking over a subnet would be a problem.  You could  simply create another subnet for nodes that you don't want managed by  the maas. 				

Lets just say there are overlapping domains of authority. I have 100% control of the machines, less control over networking (physical and logical), and gaining IPs for a new/separate subnet is politically difficult if nothing else.

I can completely control tftboot, make changes to the existing DHCP service (which also serves many other nodes), request (minor) changes to DNS, *maybe* get some rack-level wiring changes, but working with the existing single-network-interface and assigned IPs is the least disruptive approach.

---

### Post by tgalati4 on 2013-04-22
If you set all of your servers to PXE boot over the network, you could set up one "Live Ubuntu Server Installer Instance" and use PXE to boot each server into this Live Instance, then rlogin to each (since ssh won't be configured yet) and use a text-based installer script to load your custom disto.  It's a chicken-and-egg situation.  You need each server running some framework that allows you to customize it, but it is a chore to load that framework initially to each server.  PXE might solve that problem, but you still need to go into the BIOS of each server to switch off PXEboot after you have loaded your custom distro so that it boots normally off of the hard disk.

USB installs are not bad if have your basic configuration set up so that there is minimal customizing on each server.  With persistance, your config files will be saved on the USB stick and you can keep modifying as you work from machine to machine.

---

