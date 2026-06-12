---
title: "Booting images via any other method than CD/DVD or USB??"
date: 2008-03-08
forum: Server Platforms
---

### Post by brooksbp on 2008-03-08
So I would like to boot images on servers, but through a web interface.  Is there any possible setup that would allow me to do so?  Could I have a dedicated server net boot to the other servers or something?

Basically, our developers have to walk down to the servers... stick in USB... and boot the images... we want to automate that task through a web application.  How can this be done?  Thanks.

---

### Post by Rohan sehgal on 2008-03-08
Yes sir,
This can be done using any internet services including ftp,http,nis.
to do this sir you will require a new server which has boot images in it. you can run dos on your systems with ethernet support and run WUBIBOOT.exe via any system. If not go for fedora linux 8 . It has all these capabilities built in.

---

### Post by brooksbp on 2008-03-08
Can you supply a link to a tutorial or article explaining how this can be done?  Is it possible to load an image via FTP and then remote boot the machine... any more detailed info would be great!

---

### Post by koenn on 2008-03-08
you can "remote boot" a computer if it has a BIOS and a NIC that support 'boot-on-LAN' or "wake-on-LAN"  i.e the machine will boot when the NIC receives a specific bit sequence (a 'magic packet')

a computer can also boot from a remote boot image if its nic supports network boot (eg PXE)
this requires
- a DHCP server that informs the computer of the 'next server', i.e. the server where to download the boot image from, and which boot image to use
- a (usually ftp) server to serve up boot images
(both servers can be on the same machine)
Edubuntu and LTSP use this to implement thin client sollutions

Looks like what you want is a combination of both + a web interface around it to manage and use it. I''m not aware that such thing exists, but you might be able to create it yourself, ot you may come across such a solution while looking up stuff like wake-on-lan, pxe, network boot, etc

---

