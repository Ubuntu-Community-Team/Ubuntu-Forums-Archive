---
title: "Ubuntu server 11.10 wifi not working on virtualbox"
date: 2012-02-15
forum: Virtualisation
---

### Post by polo84 on 2012-02-15
Hi....My OS is LinuxMint 11 and I have a Ubuntu Server 11.10 that I virtualize on VirtualBox 4.1.8 (the latest).  I want to be able to connect WIFI on this Ubuntu.   How do I proceed, i've tried to put a second network interface on VB  as wlan0 but in the ifconfig i only see the "eth0" and the "lo"  interface.  

Do i need to install additional driver for my wifi card to make a compatibility with my VM or its the VM that need additional drivers to detect my wifi card ?

If somebody have the knowledge for this, I would appreciate a little help on this one to live better...  

Thanks

Seb

---

### Post by haqking on 2012-02-15
> **polo84 said:**
> Hi....My OS is LinuxMint 11 and I have a Ubuntu Server 11.10 that I virtualize on VirtualBox 4.1.8 (the latest).  I want to be able to connect WIFI on this Ubuntu.   How do I proceed, i've tried to put a second network interface on VB  as wlan0 but in the ifconfig i only see the "eth0" and the "lo"  interface.  

Do i need to install additional driver for my wifi card to make a compatibility with my VM or its the VM that need additional drivers to detect my wifi card ?

If somebody have the knowledge for this, I would appreciate a little help on this one to live better...  

Thanks

Seb


you can use a USB wifi device in the VM itself

Or use your hosts wifi connection through NAT or bridged mode.

---

### Post by polo84 on 2012-02-15
Thanks for your reply...

I don't have a wifi Usb card and I would prefer to use my integrated interface if possible.  I've tried a bridged or a NAT adapter but if still make my wifi card invisible in the "ifconfig".

Do you have any others solutions ?
Thank you

---

### Post by haqking on 2012-02-15
> **polo84 said:**
> Thanks for your reply...

I don't have a wifi Usb card and I would prefer to use my integrated interface if possible.  I've tried a bridged or a NAT adapter but if still make my wifi card invisible in the "ifconfig".

Do you have any others solutions ?
Thank you

it will be invisible.

the VM wont see it as wifi hardware.

It will see it as a ethernet device probably eth0.

Just use NAT which is the simplest linked to your wlan device in the host and thats it.


The VM will see it as ethernet

---

### Post by polo84 on 2012-02-15
Waow man it working now thank you sooooooo much for this you made my day  :D

I putted the adapter to NAT and now that i'm connected wifi, my VM actually use that connection.  

You Rock !!      SOLVED!1

---

### Post by haqking on 2012-02-15
> **polo84 said:**
> Waow man it working now thank you sooooooo much for this you made my day  :D

I putted the adapter to NAT and now that i'm connected wifi, my VM actually use that connection.  

You Rock !!      SOLVED!1

no worries, you are welcome.

Peace

---

