---
title: "Need Recommendation for Virtualization Solution for Lab/home that's easy to setup"
date: 2013-03-29
forum: Virtualisation
---

### Post by kendoori on 2013-03-29
We have a lab box that's currently running Win2k3. That server has WAMP on it, but also some virtual machines that are beginning to cut into its resources. I would like to P2V the machine, and build/buy a new box that has enough RAM to properly support 2-3 VMs running simutaneously (Win2k3, Ubuntu, etc...). Nothing is very processor intensive on any of these instances. This is going to run in a spare room at home, so likely desktop form factor and relatively quiet is what I want to do. 

I use 12.04 as my daily driver for desktop and am considering some flavor of Ubuntu as the host for this as I'm comfortable with it. I have some prebuilt machines in VirtualBox and VMWare all ready to go.

I don't really want to spend a lot of time learning VMWare eSXI, so am looking for a relatively easy recipe to make this all go, including some possible hardware recommendations. Perhaps something like this: [http://www.ebay.com/itm/HP-8200-Elite-626208R-999-F8BQ-i7-2600-3-4-GHz-160GB-SSD-16GB-DDR3-1333-/261192557700?pt=Desktop_PCs&hash=item3cd04a2484](http://www.ebay.com/itm/HP-8200-Elite-626208R-999-F8BQ-i7-2600-3-4-GHz-160GB-SSD-16GB-DDR3-1333-/261192557700?pt=Desktop_PCs&hash=item3cd04a2484)

Would appreciate any comments on this... and if there is a good recipe/cookbook out there on the web, would appreciate this.

---

### Post by CharlesA on 2013-03-29
[Proxmox]("http://www.proxmox.com/") is a baremetal hypervisor, so you would install it on the hardware and manage your guests via web interface.

I've been thinking about migrating to it, but so far I've been sticking with running VBox headless on my server.

That server on ebay looks very similar to mine (well the guts do at least, as mine is in a desktop case).

I've been running an i7 2600K, 16GB RAM, 500GB OS drive and 4TB drive array on my server. The VMs are stored on the array.

---

### Post by kendoori on 2013-03-29
Proxmox looks good, but would prefer to find something with no cost. If I'm reading their website right, theirs is a subscription model.

---

### Post by CharlesA on 2013-03-29
Forgot about that bit.

You could try running KVM or even OpenVZ, but KVM (with virtmanager might work fine for you).

---

### Post by gordintoronto on 2013-03-30
Is there something you want to do which VirtualBox won't do?

---

### Post by dcstar on 2013-03-30
> **kendoori said:**
> We have a lab box that's currently running Win2k3. That server has WAMP on it, but also some virtual machines that are beginning to cut into its resources. I would like to P2V the machine, and build/buy a new box that has enough RAM to properly support 2-3 VMs running simutaneously (Win2k3, Ubuntu, etc...). Nothing is very processor intensive on any of these instances. This is going to run in a spare room at home, so likely desktop form factor and relatively quiet is what I want to do. 

I use 12.04 as my daily driver for desktop and am considering some flavor of Ubuntu as the host for this as I'm comfortable with it. I have some prebuilt machines in VirtualBox and VMWare all ready to go.

I don't really want to spend a lot of time learning VMWare eSXI
.........

If you want to use VMs from within a 12.04 Desktop (manually starting them etc.) then use the free VMware Player, if you want to have a true headless Hypervisor that automatically runs VMs then the free ESXi is not that hard to get going with - the main issue is that it requires a Windows PC to manage it.

---

### Post by kendoori on 2013-03-30
I'm most comfortable with Virtualbox, so I'm going to give a shot at doing a headless setup. I'm also going to see if I can make this work on my Dell Optiplex 755 by adding some RAM (get it to 8 GB) and installing a small  SSD to run the base OS from it. I'm afraid of compatability issues with eSXi. Any tips on the vBox setup on Ubuntu server? or should I run a different distro?

---

### Post by gordintoronto on 2013-03-30
Is memory so tight you need to run Ubuntu Server? Desktop can do everything Server can do, it just has a tiny bit of overhead -- and a lot less learning curve!

---

### Post by CharlesA on 2013-03-30
> **gordintoronto said:**
> Is memory so tight you need to run Ubuntu Server? Desktop can do everything Server can do, it just has a tiny bit of overhead -- and a lot less learning curve!

+1. I run the server edition of 12.04, mostly cuz I don't need a GUI and the machine just sits in the corner and does it's thing. :)

That being said, the VBox gui is way more friendly than the CLI (which is why I use phpvirtualbox to manage my VMs.)

---

### Post by dcstar on 2013-03-31
> **gordintoronto said:**
> Is memory so tight you need to run Ubuntu Server? Desktop can do everything Server can do, it just has a tiny bit of overhead -- and a lot less learning curve!

The server kernels are compiled with different options and do not support various desktop things like sound, hotplug USB etc.

Having said that, the GUI with any of the desktop options does make like easier in general and you can always use the server kernel for maximum efficiency.

---

### Post by Cheesemill on 2013-03-31
> **dcstar said:**
> The server kernels are compiled with different options and do not support various desktop things like sound, hotplug USB etc.

Having said that, the GUI with any of the desktop options does make like easier in general and you can always use the server kernel for maximum efficiency.
This used to be the case, but it isn't anymore.

Ever since 12.04 both the Desktop and Server versions of Ubuntu use the exact same kernel.

---

### Post by MaxLinuxLover on 2013-03-31
You should use VirtualBox, it is a perfect vm manager and runner, I use it all of the time.

---

### Post by kendoori on 2013-03-31
I do to on the desktop for everyday use... can you recommend how to properly script having vBox load at startup?

---

### Post by CharlesA on 2013-03-31
> **kendoori said:**
> I do to on the desktop for everyday use... can you recommend how to properly script having vBox load at startup?

GUI or headless?

I wrote up a script to start/stop VMs automagically on shutdown/startup, but it only works if you run them headless.

You can find it here:
[http://charlesa.net/scripts/linux/virtualbox-script-ubuntu.php](http://charlesa.net/scripts/linux/virtualbox-script-ubuntu.php)

---

### Post by kendoori on 2013-03-31
I'm thinking of going headless, so thanks for the script. I'm waiting for the RAM and SSD to show up, but will hopefully build this next weekend.

---

### Post by kungfupete on 2013-04-02
Agree about VirtualBox, it has come a long way and is awesome...although so has KVM, LXC and others.  I remember looking into this some time back --you may want to check VBoxTool out:  [http://vboxtool.sourceforge.net/](http://vboxtool.sourceforge.net/)

---

### Post by kendoori on 2013-04-02
Thanks on the vboxtool didn't know about it, but was already planning on using [phpvirtualbox]("https://code.google.com/p/phpvirtualbox/")... I am planning on doing my build with 12.04 server and going headless. I purchased a 2 drive array eSATA enclosure and an SSD for the box to boot and run from. I will report back on results.

---

### Post by CharlesA on 2013-04-03
> **kendoori said:**
> Thanks on the vboxtool didn't know about it, but was already planning on using [phpvirtualbox]("https://code.google.com/p/phpvirtualbox/")... I am planning on doing my build with 12.04 server and going headless. I purchased a 2 drive array eSATA enclosure and an SSD for the box to boot and run from. I will report back on results.

Just an FYI with phpvirtualbox, the developer of it is no longer working on it, so there are a few bugs, but nothing game breaking - at least none I have found yet.

Deleting/Creating/Restoring snapshots will throw an error message, but if you click ok and leave it alone for a few minutes the snapshop operation will complete just fine.

---

### Post by Hexxus on 2013-04-05
I used proxmox for a bit to test it out in comparison to VMware ESXi. I liked alot of the features that it had, but there was a good learning curve changing over as far as how things are done. 

Recently I purchased a 3U 15 Bay supermicro server for really cheap on eBay to be a NAS at home with FreeNAS, then I have a Poweredge 2950 that I've been experimenting with the latest hyper-visors.
It works pretty well with WD Red drives and RE4's.

---

