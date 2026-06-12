---
title: "Need help on networking"
date: 2011-05-12
forum: Virtualisation
---

### Post by kmkmahesh on 2011-05-12
At first i want to tell my system specifications:

UBUNTU 11.04 as Host

Fedora 14 as Guest 

I want big help on connecting two operating systems using network, and i want to share the folders too, if possible i want to share my USB internet connection also

please guide me with perfect commands or perfect notes

Thnx in Advance 

Really need the help

---

### Post by Dedoimedo on 2011-05-12
Networking and sharing, maybe this:
[http://www.dedoimedo.com/computers/virtualbox-network-sharing.html](http://www.dedoimedo.com/computers/virtualbox-network-sharing.html)

USB device sharing, I don't think it's possible. The device needs to be locked by one or the other to prevent data corruption. You can connect/disconnect usb device into the virtual machine, but you won't be able to write to it simultaneously in host and guest. Unless someone knows of a genius way of doing it.

Cheers,
Dedoimedo

---

### Post by collisionystm on 2011-05-12
Using Virtualbox?

---

### Post by kmkmahesh on 2011-05-12
i tried but i just had a webserver (which is not installed in any OS except Fedora 7+)in my guest os working perfectly there, but i just want to run it from my host to learn some thing from it so please help me

---

