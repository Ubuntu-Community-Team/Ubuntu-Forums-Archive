---
title: "problem with firestarter and wireshark"
date: 2010-04-01
forum: Security
---

### Post by amite on 2010-04-01
i am a student . for learning point of view i installed firetarter. But when i start firestarter i couldn't stablish my net connection.i am using 3g mobile broadband connection.to access internet,i had to uninstall firestarter.Please suggest me how to start using firestartrer.


Also i hv installed wireshark1.2.2 ,but it doesn't detect any interface.while  i m using following interfaces:

Hardware Class: network
  Model: "Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8136 "RTL8101E/RTL8102E PCI Express Fast Ethernet controller"

Hardware Class: network
  Model: "Dell Wireless 1397 WLAN Mini-Card"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x4315 "BCM4312 802.11b/g"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x000c "Wireless 1397 WLAN Mini-Card"

does it require any other s/w installation to start ?#-o

---

### Post by uRock on 2010-04-01
Reading this page may help you find how to adjust the option settings to monitor your network. For your firewall, I suggest installing GUFW from the repositories.

---

### Post by HermanAB on 2010-04-02
Howdy,

Firestarter is deprecated.

If you really want to know how IPtables works, then you need to go to Rusty Russell's Remarkably Unreliable Web Site:
[http://people.netfilter.org/~rusty/unreliable-guides/](http://people.netfilter.org/~rusty/unreliable-guides/)

---

### Post by uRock on 2010-04-02
I guess it would've been helpful if I had inserted the link to look at for wireshark, [http://wiki.wireshark.org/CaptureSetup/WLAN](http://wiki.wireshark.org/CaptureSetup/WLAN)

---

