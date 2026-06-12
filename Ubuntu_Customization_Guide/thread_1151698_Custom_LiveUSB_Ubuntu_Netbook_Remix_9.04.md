---
title: "Custom LiveUSB Ubuntu Netbook Remix 9.04"
date: 2009-05-07
forum: Ubuntu Customization Guide
---

### Post by Laddy on 2009-05-07
Hi Guy,

Sorry for my english, i speak a little bit.

I want my usb boot mode persistent directly without going through the boot menu with various choices? How can I do?

My USB KEY :

[IMG]http://www.generation-upload-fr.com/upload/1965part.png[/IMG]

I add this in my text.cfg

```

label persistent
  menu label ^ Ubuntu Netbook Remix mode persistent
  kernel /casper/vmlinuz
append file=/cdrom/preseed/netbook-remix.seed boot=casper persistent initrd=/casper/initrd.gz quiet splash locale=fr_FR console-setup/layoutcode=ch console-setup/variantcode=fr --

```Can you help me ? is it possible or not ? How ?

---

### Post by anttir on 2009-12-19
On the USB filesystem at syslinux directory, modify syslinux.cfg with

timeout 20


This will give a 2 second timeout which is usually small enough.


antti
:guitar:

---

