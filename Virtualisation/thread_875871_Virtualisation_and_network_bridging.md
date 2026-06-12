---
title: "Virtualisation and network bridging"
date: 2008-07-31
forum: Virtualisation
---

### Post by evildmp on 2008-07-31
I'm trying to work out if this is possible, and if so, how.

I have a physical server running Hardy Ubuntu Server Edition. It picks up a public IP address and fully-qualified domain name via DHCP (along the lines workstation55.example.com) from our institutional network.

I want to install some virtual servers on it, for web development and testing. Because my institution will not, at this stage, give me any more IP addresses, the virtual network inside will need to be a private one.

I'd like the virtual machine to pick up their IP addresses via DHCP from the host server.

I would also like to be able to address these virtual machines from the rest of the world - if I call them django and plone, I'd like to be able to reach them at django.workstation55.example.com and plone.workstation55.example.com, for example.

So, is it possible to make addressing the virtual machines this easy?

Thanks for any help.

---

