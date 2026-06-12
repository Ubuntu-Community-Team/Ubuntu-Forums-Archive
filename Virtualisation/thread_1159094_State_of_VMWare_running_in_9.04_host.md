---
title: "State of VMWare running in 9.04 host"
date: 2009-05-14
forum: Virtualisation
---

### Post by Nick Rhodes on 2009-05-14
I have been looking at various threads and seems to be a mix of success and failure in running VMWare within a Jaunty host.

So just trying to get a consensus in how stable it is now and also how likely it is to break.

Cheers, Nick

---

### Post by whoop on 2009-05-14
I am running vmware server 2.0 on a 9.04 host. I installed it when it was still running 8.10. The upgrade didn't mess it up. Whenever you install and use a new kernel you have to re-configure vmware server (but that's no biggy). The vmware client interface is a bit slow on response sometimes but the guest os's always seem to run fast and are responsive.

---

### Post by TJet1.8 on 2009-05-14
I'm running VMware Workstation 6.5.2 on my Jaunty.

I had 8.10 and upgraded to 9.04 via Upgrade Manager...this didn't go well and blew up my Laptop.

I proceeded to do a Fresh 9.04 install...and Fresh VMware Workstation 6.5.2 install.
VMware seems to work fine "except" for the Bridged connection.

As I have both Ethernet and Wireless network cards in my laptop, the Automatic function for Bridged Networks doesn't work as advertised (i.e. - It's not Automatic any more). It worked fine in 8.04 though.

I have to go into the VMware Virtual Network Editor, and under the Bridged option, choose either eth0 or wlan0 in order to get it to work.

I tried recreating my VMware modules via vmware-modconfig and tried installing the latest build-essential and kernel-headers to no avail.

Is anyone experiencing this same issue?
Does anyone have a fix?

Thank you :)

---

