---
title: "Got my CDs today, need help before installing server"
date: 2008-08-27
forum: Server Platforms
---

### Post by kabeza on 2008-08-27
Hi guys
I've got today some cds in my post box
I've asked some days ago 1 server and 1 desktop edition

Now, lemme describe the situation
We've a HP server, proliant ML115. We've windows 2003 installed on it, but now we'd like to go with Ubuntu

Our problem resides in that we would not like to loose all the info, but to begin trying the ubuntu server edition in this same server, maybe by creating another partition and making some multiboot menu, etc.

So the initial question would be

1)

Where could I find some info about how to setup a multiboot environment and begin installing the server edition ?

Or will the installer do everything (new partition and boot menu) by itself?

2) 

Is there any way to know if this install will run fine with the std. hardware that this server has from factory?

Thanks a lot in advance,

---

### Post by Iowan on 2008-08-27
[Here]("https://help.ubuntu.com/community/WindowsDualBoot") is a document on Dual-booting.  The installer is pretty good about recognizing used partitions, but if you tell it to use the entire disk, it will. I had a dual-boot desktop machine that went together fairly painlessly.

---

### Post by windependence on 2008-08-28
I don't dual boot much of anything anymore. It would be easier to set up a Virtual machine. VMware server is free as well as VMware ESXi. In this case since there is an existing OS, I would go with VMware server. Here is a link to a how to for the installation:

[http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04](http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04)

To install on Windows is even easier, just follow the documentation on the VMware web site here:

[http://register.vmware.com/content/download-106.html](http://register.vmware.com/content/download-106.html)

Then, you can run Ubuntu right along side of the Windoze install without rebooting!

-Tim

---

### Post by kabeza on 2008-08-28
Hi
VmWare Server is a good idea, but I didn't know it was free

I think the problem will be running (windoze+vmware->ubuntu_server) with 512 ram :lolflag: (no plans to buy more ram for the server in near future)

I didn't know vmware server was free for windows... but I think I'll try the dual boot :)

---

