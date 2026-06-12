---
title: "Ubuntu PXE install over private network"
date: 2016-05-10
forum: Server Platforms
---

### Post by asuhov on 2016-05-10
Hello!
I am currently trying to do an unattended install of Ubuntu 16.04. My setup looks like this:
PXE server - with tftp,dhcp & http server installed. Kickstart & preseed files are present here, on the http server, as well as ubuntu installation files
PXE client  - where I'm trying to do the install
They share a private connection (no internet access)

I have 2 problems:
1. After booting the client, all works as expected until the network configuration. It's trying to get a nameserver & gateway. But beeing on a private network I don't have any of those.
2. Getting past that and leaving it blank, the install it's trying to get the files over the network. Obviously it fails: it is on a private network, with acces only to the PXE server.

I tried 2 ways to install it: 
1. Insert installation media on client & specify in kickstart file (found on the server) to use cdrom as source
2. Install over the network, from my http server
They both failed, so I'm asking you guys if you have any thoughts on that. You have below my kickstart file, pxe.cfg, pressed file.
One more thing: I set up a rhel & sles on the same server and I didn't had any of these problems, so I'm pretty sure i'm missing something in kickstart/presseed/pxe.cfg file

grub.cfg: [http://paste.openstack.org/show/496560/](http://paste.openstack.org/show/496560/)
ks.cfg: [http://paste.openstack.org/show/496561/](http://paste.openstack.org/show/496561/)
ubuntu.seed: [http://paste.openstack.org/show/496562/](http://paste.openstack.org/show/496562/)

Thanks

---

