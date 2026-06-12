---
title: "Virtual Ubuntu 24.04 LTS on UTM on iMac24 has no WiFi"
date: 2024-09-16
forum: Virtualisation
---

### Post by GeoffatMM on 2024-09-16
I am trying to install WiFi drivers on my iMac24 for Ubuntu.

I have the internet on the machine via an Ethernet adapter over a thunderbolt bridge so all packages are up to date.

In fact, I started with the UTM image for 22.04 then updated all packages and then allowed it to upgrade to 24.04 (which then also needed package updating).

as a result there was no opportunity to select the third party drivers for media and WiFi.

1.     How do I find out which WiFi card I am using on the Mac?

2.     How do I then install the drivers to recognize the WiFi card.

All my searching poiints me to using  "lspci | grep Network" but this returns an empty result.

Any help appreciated.

Geoff

---

### Post by GeoffatMM on 2024-09-18
Hmm.  No response yet.

I am utterly confused as I have launched my virtual Ubuntu desktop that tells me that there are no WiFi cards recognised yet I have internet access despite my Ethernet cable being disconnected!

So I have to assume that the WiFi is working but how do I check?  Settings only gives me a "Wired" option and no wifi.  When I search for WiFi in settings it tells me No WiFi Adapter Found.

Is Ubuntu using a "wired" connection to my Mac which then connects it to the WiFi?

Geoff

---

### Post by GeoffatMM on 2024-09-26
Hi again,

Is no one prepared to help me?  I have found out that my chip is a Broadcom 4378 (0x14E4,0x4378) but cannot find any reference to a 4378 chip even on the Broadcom site.

How do I find out which drivers I should use?

Geoff

---

### Post by ajgreeny on 2024-09-27
You must be using the default NAT connection network which will always be seen as a wired ethernet by the VM. That is totally normal and nothing to worry about. It means that your VM is doing exactly what you suspected,  ie, using a wired connection to your host's actual wireless connection.

You would only need to use drivers for your WiFi hardware if you needed a separate bridged network connection which you obviously don't have set up. I've never bothered with bridged networks for my VMs though this could be necessary if you were using the VM as a network server of some kind.

---

### Post by tea for one on 2024-09-27
> **GeoffatMM said:**
> I have found out that my chip is a Broadcom 4378 (0x14E4,0x4378) but cannot find any reference to a 4378 chip even on the Broadcom site.
Just offering info:-
[https://linux-hardware.org/?id=pci%3A14e4-4425-106b-4378](https://linux-hardware.org/?id=pci%3A14e4-4425-106b-4378)

---

