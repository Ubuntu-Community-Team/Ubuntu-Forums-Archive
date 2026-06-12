---
title: "Lubuntu VM (VirtualBox) with 4G LTE USB Stick - slow internet speed"
date: 2019-11-21
forum: Virtualisation
---

### Post by roycehun on 2019-11-21
Hi!
My english is pretty poor, so bear with me please.
I'm running a Lubuntu 19.10 x64 VM on a Windows10 host, using VirtualBox 6.0. I'm using a Huawei E3372 LTE USB stick to access to the internet on the VM, but the bandwith is terrible. 
The LTE connection on the host OS is 60Mbps download, 15Mbps upload, 28ms ping.  On the virtualized Lubuntu (with the same stick), the download is 0.8Mbps, the upload is 5Mbps, and the ping is 55ms. I did not install any additional drivers on the VM for the stick, it picked up automatically. I installed the Guest Additions package on the guest OS, it didn't change anything regarding the internet speed.
VM settings:
-ICH9 chipset
-PAE/NX disabled CPU
-default paravirtualization interface
-USB 2.0 (EHCI) Controller (tried with 3.0 too, no change)

I found draisberghof's USB modeswitch thread, but I'm not sure that is a solution for my problem.

Any ideas? Please help me.

---

### Post by TheFu on 2019-11-22
Don't try to use usb passthrough to the guestOS.  Just let the hostOS manage the networking and have the guest use virtio for network connections.  The performance should be the same as what the host sees.

The virtualbox manual chapter on networking explains the different types of network configurations possible. Back when I used vbox, I used bridged networking so the guest VMs were on the same subnet as the host and other LAN devices.

---

### Post by roycehun on 2019-11-22
Sadly the bridged network is not an option, I really need to use the USB stick dedicated to the VM.

---

### Post by SeijiSensei on 2019-11-22
Unless the host has no network connection I don't see the reason for that. NAT or bridged networking are far better options.

---

### Post by TheFu on 2019-11-23
> **SeijiSensei said:**
> Unless the host has no network connection I don't see the reason for that. NAT or bridged networking are far better options.

There some security and testing considerations where NOT using the host connection can be highly useful. These are specialized situations.

But it definitely is much easier to use NAT or bridged networking managed by the host.

---

### Post by SeijiSensei on 2019-11-23
> **TheFu said:**
> There some security and testing considerations where NOT using the host connection can be highly useful.
I can believe that, but I doubt most people here have those kinds of advanced requirements.

---

### Post by roycehun on 2020-06-06
Bump - I'm still struggling with this problem, I really need to make the LTE stick work. Please help me.

---

### Post by DuckHook on 2020-06-06
:confused:
[list=1]
[*]It's been over half a year since you've checked back with this thread. Both TheFu and SeijiSensei (two of our best) were helping you, but without your timely feedback and response, how can anyone help?
[*]> **TheFu said:**
> Don't try to use usb passthrough to the guestOS.  Just let the hostOS manage the networking and have the guest use virtio for network connections.  The performance should be the same as what the host sees.

The virtualbox manual chapter on networking explains the different types of network configurations possible. Back when I used vbox, I used bridged networking so the guest VMs were on the same subnet as the host and other LAN devices.Your question has already been answered.
[*]If bridged is not an option, use NAT.
[*]Hopefully, this won't be interpreted as a reproach because such is certainly not my intent, but without a fuller context, we are left stumbling in the dark just guessing at your end goal. What are you trying to achieve? You say bridged is not an option; why not?
[/list]

---

