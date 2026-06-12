---
title: "I am planning to install Ubuntu 16.4 desktop on Virtual Box,  Graphic card"
date: 2016-07-11
forum: Virtualisation
---

### Post by Lukasz Tarkowski on 2016-07-11
I am planning to install Ubuntu 16.4 desktop on Virtual Box,  What Graphic card driver do I need?  My graphic card is AMD Radeon Graphics HD6320. My laptop is Asus 1225B How do I change the grub picture Ubuntu 16.4?

---

### Post by Habitual on 2016-07-11
Better see [http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)

---

### Post by &amp;KyT$0P# on 2016-07-11
> I am planning to install Ubuntu 16.4 desktop on Virtual Box, What Graphic card driver do I need?
VirtualBox Guest Additions provide all the needed graphics driver(s), just be sure to install from the Guest Additions CD image if you want 3D acceleration available

---

### Post by Lukasz Tarkowski on 2016-07-11
How do I install Guest Additions from the cd for Virtual Box?  Do I need to download anything more, or do I keep Ubuntu Desktop 16.04 DVD ISO

---

### Post by courtney2 on 2016-07-11
To install virtualbox guest additions, this tutorial should help

[http://www.tomshardware.com/faq/id-1957309/install-virtualbox-guest-additions-linux-mint.html](http://www.tomshardware.com/faq/id-1957309/install-virtualbox-guest-additions-linux-mint.html)

---

### Post by Lukasz Tarkowski on 2016-07-11
I already installed Guest Additions, How do I connect Ubuntu Desktop 16.04 to Wifi network using Virtual Box,  mine is broadcom my driver

---

### Post by &amp;KyT$0P# on 2016-07-11
What are you trying to achieve by doing that?

Please note that VirtualBox mostly gives VMs their own virtual hardware, independent of your host.  It **does not** just "donate" all of your host's physical hardware to the guest, nor does it emulate 100% your host's exact hardware.
So, as far as drivers & the like are concerned, think of the VM as like to a totally different physical computer.

---

### Post by QIII on 2016-07-11
> **halogen2 said:**
> think of the VM as like to a totally different physical computer.

... with all of it's hardware and drivers included -- and you can't swap it.

---

### Post by wildmanne39 on 2016-07-11
You use the internet from your host machine even if it is a wifi connection it will show an ethernet connection.

As soon as you boot into ubuntu you should have an internet connection from your host if for some reason you want to use wifi on the guest and don't want it to pass through from your host you have to use an usb adapter but I see no reason to go through the trouble and I have been using virtualbox for years.

---

### Post by howefield on 2016-07-12
Thread moved to the "*Virtualisation*" for a better fit.

---

### Post by MAFoElffen on 2016-07-13
Summary of Virtual networking... in ViirtualBox. Your host is running VirtualBox. Is is the software allowing to runing a "virtual Machine" inside your desktop. Network wise, think of a guest as just another machine. Think of their being a virtual network switch inside your host, that is usuing your hosts hardware to make network connections. The VM Guest uses whatver you setup in In the VM Machine setting to make a connection to various virtual switches.

From within the VirtualBox VM Manager, in the Global/VM Manager type of network settings you setup your virtual switches. You map what the hosts network devices, how they will be used by your VM Guests (what kind of virtual device). Default and easiest is to map your wireless as NAT (Network Address translation). Which means it has connection to the outside world (internet), but that those addresses are on a different network ID than your host. So they can communicate with other VM that arre set the same, connection to the internet, but not to your host or devices on your local net. (At least not without another switch). DHCP requests are assigned internally within VirtualBox.

The second is internal, with means they can talk with other VM's, but not to the outside world at all. DHCP requests are assigned internally inside VirtualBox.

The third is bridged, which puts bridge VM's on the same notwork as the host. dhcp requests are assigned by the same mechanism as the other machines on your local net.

That sounds more difficult than it actually is. You put a selection in an option box and it makes the connection type for that virtual switch. But one catch, sicnce you are going wireless, you can only set your wireless device to either NAT or bridge, not both. One type to a device.)

What the halogen2 was trying to explain to you, was that inside the running VM guest, you make those settings as if it where a live device. It may be virtual, but it thinks it's running on hardware with a wired Ethernet connection. There's lots of guides that explain how to set up a wired connection for whatever guest OS that you are running.

As for Video... without Guest additions and the Extension Pack (which I would also suggest that you install), you still get video, but it would be a VGA quality type of graphics, because the Virtual Machine would emulate a generic type of graphics card, going to a generic type of monitor. In VirtualBox, the Virtual Machine is emulated hardware. The Guest Additions add virrtio drivers to the VM guest. The Extension Pack adds a plugin  to VirtualBox Itself to allow the VM Guest to use some of the capabilities of the hosts hardware.

Some of those capabilities depend on the capabilities of your CPU and if it supports hardware virtualization technologies... Since VirtualBox is a type 2 hypervisor, meaning it emulates hardware... even with those 2 extensions improving your video quality and what you can share between your VM Guest and Host... Your VM Guest running inside VirtualBox is never going to see your AMD video card as such. It will have better quality, but will still be an software emulated extension of XVGA.

So there is a reality limit of what it can do in that type of hypervisor.

That is probably more than you expected, but should be enough to make an informed start at it.

---

