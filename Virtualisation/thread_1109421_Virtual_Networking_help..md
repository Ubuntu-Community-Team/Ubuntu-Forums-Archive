---
title: "Virtual Networking help."
date: 2009-03-28
forum: Virtualisation
---

### Post by solitaire on 2009-03-28
Hope someone can help me out!

I'm trying to get my head around Virtual OS and Networking.

OK setup:
Laptop running: Ubuntu 8.10 + Sun xVM VirtualBox 2.1.4
Virtual OS : Ubuntu 8.10 LAMP server

OK Here's what i;m trying to do!

I'm trying to get my laptop to see the virtual server on VirtualBox. So I can use my main OS to view the website hosted in the virtual Server for testing and experimentation.

I currently don't have a second machine I could use as a test server. and since i'm experimenting i DON'T want the LAMP server installed on my main OS.

How do I configure networking in Ubuntu to see the virtual server?

---

### Post by Dedoimedo on 2009-03-29
You need bridged networking.
There's a sticky here re: this and also, please check my vmgl tutorial, I have the bridged networking covered in the second half of the article.
Dedoimedo

---

### Post by Jose Catre-Vandis on 2009-03-29
Just change your network adapter to host interface and use eth0, then your VM should be present on your LAN if you have a router serving up DHCP addresses.

---

### Post by solitaire on 2009-03-29
> **Jose Catre-Vandis said:**
> Just change your network adapter to host interface and use eth0, then your VM should be present on your LAN if you have a router serving up DHCP addresses.

Tried that. But I'm wireless and it does not pick up a DHCP server. :(


Installed the trial version of VMWare and It works through that. That will keep me going for the next month till i can get the VirtualBox working.

Thanks for the help..

---

### Post by Jose Catre-Vandis on 2009-03-29
> **solitaire said:**
> Tried that. But I'm wireless and it does not pick up a DHCP server. :(

If you are wireless you will need to do some masquerading!

Check out my post on this [here]("http://bimma.me.uk/2007/09/30/ubuntu-creating-host-interface-networking-for-virtualbox/")

Ignore the first section about host interface networking, and scroll down to where it says:

"**Connecting VMs when on a Wireless NIC with encryption using Masquerading**"

and read on from there....

---

