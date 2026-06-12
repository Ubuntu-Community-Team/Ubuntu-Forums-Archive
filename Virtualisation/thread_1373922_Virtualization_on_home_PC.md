---
title: "Virtualization on home PC"
date: 2010-01-06
forum: Virtualisation
---

### Post by i.short on 2010-01-06
Hi,

I would like to use a PC I have at home,  as a desktop, and also as web server, that is accessible on my wireless home network.  Currently the PC has ubuntu 9.10 on it.

I guess in an ideal world I would like the PC to function in two ways:

1. Traditional desktop that I can develop web applications on a virtual LAMP server on the same PC

2. Simply power on the PC, leave the room, remotely connect to the PC from my laptop, power on the webserver, and develop using the laptop.

I would greatly appreciate any suggestions as to how I could set up such an arrangement.

Kind Regards,

Ian

---

### Post by kiranmurari on 2010-01-06
You can install VirtualBox ([http://virtualbox.org]("http://virtualbox.org/")) and create a VM which can host your web server. Using RDP you can remotely connect to your PC from your laptop.

Hope this helps.

Regards,
Kiran

---

