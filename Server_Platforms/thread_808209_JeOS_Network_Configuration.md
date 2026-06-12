---
title: "JeOS Network Configuration"
date: 2008-05-26
forum: Server Platforms
---

### Post by leetcharmer on 2008-05-26
Hello,

I want to build a test labs environment at work to test open source alternatives to our proprietary setups.  We have a VMWare ESX Server and now that Ubuntu JeOS is around, I would like to build a lot of modules to simply plug in to our network for the additional features.  To begin creating these Ubuntu JeOS machines, I've set up one Ubuntu box with it's own external static IP to be the host.     Then I installed VMWare Server to create my JeOS machine.  The problem I run into is knowing how to setup the network information.  If I create a LAMP VM, I would like to access it via the eternal IP.  How can I make this happen?

Thanks

---

### Post by bwilhiteforex on 2008-10-06
You need to port-forward from your firewall to the vm.  VMWare makes it pretty easy to do this, compared to VirtualBox.  This is the setup I'm using, and it works quite well for me.

---

