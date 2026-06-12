---
title: "LUKS Bluetooth keyboard"
date: 2019-04-22
forum: Security
---

### Post by hamburgerjungejr on 2019-04-22
Hi,

I have installed Ubuntu 19.04 with LUKS-Encryption and BTRFS on my laptop following this guide: [https://albertodonato.net/blog/posts/full-disk-encryption-with-btrfs-on-ubuntu-xenial.html](https://albertodonato.net/blog/posts/full-disk-encryption-with-btrfs-on-ubuntu-xenial.html)

Now after coming back to my desk I paired my bluetooth keyboard with Ubuntu and restarted my laptop. 
But after the restart I was not able to tape my encryption password with my bluetooth keyboard, only with the internal keyboard, which is quite uncomfortable. 

I added the following modules to my initramfs

hid_multitouch
usb_common
usbcore
usbhid
ehci_hcd
ohci_hcd
uhci_hcd
hid
bluetooth
bnep
btbcm
rfcomm
btintel

and ran : sudo update-initramfs -u and sudo update-grub

But this changed nothing.

How can I use my bluetooth keyboard to enter my encryption password.

P.S. The keyboard is paired with the internal Intel bluetooth card

---

