---
title: "Not able to use network in VMWare 2 on Ubuntu 8.10 64 bit"
date: 2009-03-05
forum: Virtualisation
---

### Post by EvilPeppard on 2009-03-05
Hello all,

I am using Ubuntu 8.10 64 bit and have successfully installed VMWare 2.0. I've created a 32 bit Windows XP virtual machine which came up fine, network adapter and all. The problem is, the network adapter on my new virtual box did not get a proper DHCP address from our company network. I did get a 192.x.x.x address, but it should have gotten a 10.30.x.x address.

I went in and statically assigned an IP in my virtual machine, but I still cannot ping anything on my network. I'm a total noob to Ubuntu and Linux, along with VMWare. Could you please tell me what I can try so I can get the network talking correctly on my virtual machine?

Thanks in advance for any help.

---

### Post by EvilPeppard on 2009-03-05
I figured it out. I needed to change my adapter in the VM server for this XP Virtual machine from "hostonly" to "bridged", remove my static and put the DHCP back on, then restart the virtual XP machine and I was able to get on the network.

---

### Post by dcstar on 2009-03-05
> **EvilPeppard said:**
> I figured it out. I needed to change my adapter in the VM server for this XP Virtual machine from "hostonly" to "bridged", remove my static and put the DHCP back on, then restart the virtual XP machine and I was able to get on the network.

And to explain a bit to those that are also starting out:

**Bridged** makes your VM use your host LAN card like it is its own, it can get its own IP address via DHCP or use a Static address (just like any other "real" machine you plug into your network).

**NAT** uses the IP address of your host with your VM having its own different network address behind the host (like the way most ADSL modems work with an "external" and "internal" network).

**Host** means that your VM can just communicate with your host - which is just what some people want in certain circumstances like increased security.

---

### Post by EvilPeppard on 2009-03-06
> **dcstar said:**
> And to explain a bit to those that are also starting out:

**Bridged** makes your VM use your host LAN card like it is its own, it can get its own IP address via DHCP or use a Static address (just like any other "real" machine you plug into your network).

**NAT** uses the IP address of your host with your VM having its own different network address behind the host (like the way most ADSL modems work with an "external" and "internal" network).

**Host** means that your VM can just communicate with your host - which is just what some people want in certain circumstances like increased security.
Thanks for the info. :)

---

