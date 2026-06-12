---
title: "Virt-Manager, KVM and USB2.0"
date: 2012-07-24
forum: Virtualisation
---

### Post by duggy on 2012-07-24
I have Ubuntu Server 12.04LTS hosting a KVM guest managed using Virt-Manager from an Ubuntu 12.04LTS Desktop machine. All software has been installed from the standard Ubuntu repositories and not from source.

I have connected a USB CD/DVD drive to the host server and have configured USB passthrough so that the guest can see it, however it only uses USB 1.1 so it is slooooow! I would like to use USB2.0 to speed things up, and the release notes for 12.04LTS imply this should be possible, but after much googling I can't find out how.

I found this article:

[http://www.linux-kvm.com/content/virt-manager-adds-support-usb2](http://www.linux-kvm.com/content/virt-manager-adds-support-usb2)

but although the version of Virt-Manager I'm using reports itself as 0.9.1, I don't see the extra "Controller USB" item in the guest's hardware window, so I can't set the controller to use USB2.0.

Has anyone else had a any luck with this, or knows of any other way to enable USB2.0 passthrough to the guest (eg by editing the guest's xml file on the host)? Any pointers gratefully received.

Thanks,

Duggy

---

### Post by Hammi on 2012-12-02
Am trying to do the same. One option can be found here:

[http://www.linux-kvm.com/content/virt-manager-adds-support-usb2#comment-5437](http://www.linux-kvm.com/content/virt-manager-adds-support-usb2#comment-5437)

If I follow this, however, my dvb usb device produces errors, and after some time, the VM freezes... not sure what to do about that - and whether or not the values in the above link can just be copied onto every machine, or if they need to be adjusted for a particular USB hub in the actual machine, maybe even the one the USB device is connected to?

---

