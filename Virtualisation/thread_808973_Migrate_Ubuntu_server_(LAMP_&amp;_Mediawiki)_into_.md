---
title: "Migrate Ubuntu server (LAMP &amp; Mediawiki) into a VM?"
date: 2008-05-27
forum: Virtualisation
---

### Post by mart007 on 2008-05-27
Hi Guys,

I've done a search, but can't seem to find what I'm looking for. Basically,  I've got a Ubuntu server running on an old box here. It's doing well - it's sitting under my desk, and serving out our department Wiki.   All well and good.

However, another team is migrating loads of MS servers to VM's, and running them as such.  I thought this would be a nice little project.. but I can't find a way of migrating my Ubuntu box (LVM) to a virtual machine.  Does anyone have any experience doing this at all??

Cheers
Mart

---

### Post by bradmkjr on 2008-05-27
Here is a product that may be able to do what you want, but because you didn't say if they are running Microsoft Virtual Server or VMware Server or ESX, I can't be sure if this will work for your needs.

[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

> Convert Physical Machines to Virtual Machines – Free!

Use the intuitive wizard-driven interface of VMware Converter to convert your physical machines to virtual machines. VMware Converter quickly converts Microsoft Windows based physical machines and third party image formats to VMware virtual machines. It also converts virtual machines between VMware platforms. Automate and simplify physical to virtual machine conversions as well as conversions between virtual machine formats with VMware Converter.

I used the product to migrate my laptop to a VM so I could reload the laptop and then run it on my faster Virtual Server. I then loaded up 8.04 on the laptop, and accessed Windows via the Virtual Server Client.

Good Luck,
Bradford Knowlton
[http://x86v.com](http://x86v.com)

---

### Post by mart007 on 2008-05-27
Hi,

Thanks for the quick reply.  I've looked at the VMWare converter - but I think it's job is to convert Windows machines to VM's.... (if I'm wrong, I'm happy to admit it!!)

The VM will eventually be running under VMWare (although, to be honest, I'm not totally worried about which VM system it'll be running on... any is fine. But VMWare is what they're going to at the moment)

So I need something to convert my Ubuntu server to a VM... .will VMWare converter do this? The download is an exe after all... (which doesn't bode well!)

Cheers
Mart

---

### Post by bradmkjr on 2008-05-27
There is actually a bootable CD Iso, which you can burn, then run to do the conversion. That should be able to be burned on a linux system. Hopefully you can afford the short downtime during the conversion.

Not sure exactly where to get the ISO, I believe if you download the demo if Virtual Center it maybe part of the download.

Good Luck,
Bradford Knowlton
[http://x86v.com/](http://x86v.com/)

---

### Post by mart007 on 2008-05-27
Excellent- thanks for the info.  I'll go ISO-hunting! 

Cheers
Mart

---

