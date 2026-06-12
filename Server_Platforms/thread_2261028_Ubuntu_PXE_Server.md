---
title: "Ubuntu PXE Server"
date: 2015-01-15
forum: Server Platforms
---

### Post by andy117 on 2015-01-15
Hi,

I'm wondering if it is possible/anyone knows how to, set up an Ubuntu based PXE server that can deploy both Ubuntu itself and windows image over the Lan. I know i can achieve this using third party software inside a windows VM, but i am curious as to whether or not it is possible using Ubuntu alone?

Ideally clients would boot from the PXE and be presented with a grub type menu offering different images to install, both windows and Linux based.

---

### Post by newbie-user on 2015-01-16
Yes, [http://oss.netfarm.it/guides/ris-linux.php]("http://oss.netfarm.it/guides/ris-linux.php")

---

### Post by darkod on 2015-01-17
Also don't forget that for a PXE boot you have to setup the correct option in your dhcp server. The dhcp has to offer the IP of the PXE server. That is how the clients find it. Apart from receiving ip from the dhcp the client also receives the option where is the PXE server to contact it.

---

### Post by Lars Noodén on 2015-01-18
> **andy117 said:**
> Ideally clients would boot from the PXE and be presented with a grub type menu offering different images to install, both windows and Linux based.

The easy way is to use DNSmasq.  It's a DHCP server but also has a built-in TFTP server which would be used for serving your boot images.  It's pretty easy to set up and just needs a line changed in the configuration for basic PXE.  That's one way I've used.  Another would be to set up dhcpd and tftpd separately.  I'm not sure about Grub though, I didn't have time to get around to trying that since I usually only ever served one image at a time.

---

