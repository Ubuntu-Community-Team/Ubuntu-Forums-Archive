---
title: "Wi-Fi"
date: 2014-06-20
forum: Virtualisation
---

### Post by richstad on 2014-06-20
I cannot get Ubuntu 14 to recognise that I have a wi-fi (and hence I have no internet connection for ubuntu). I am running it in a virtual machine on W8.1. Please help?

---

### Post by steeldriver on 2014-06-20
If you're running in a VM then normally the guest system would use a virtual wired network adapter to connect to the internet via the host OS. You should not need wifi to get an internet connection provided that the host system has one.

---

### Post by slickymaster on 2014-06-20
Moved to the **Virtualisation** sub-forum.

Your virtual machine shouldn't display it as wifi. It should appear as LAN if you have the bridge working properly. You'll need an additional wifi card if you want to be on a separate network in the virtual machine.

See this: [Wireless Network in Virtualbox]("http://askubuntu.com/questions/178804/wireless-network-in-virtualbox")

---

