---
title: "Virtualbox USB Problem"
date: 2015-08-20
forum: Virtualisation
---

### Post by charmcityslacker on 2015-08-20
I'm running UbuntuGnome 14.04 LTS and installed Windows 10 (guest) in Virtualbox 5.0.2. I can't get my vm to recognize any USB devices I connect. I googled around and then tried installing the Virtualbox Extension Pack and added my username to the vboxusers group, but still no luck. When I go to USB in the Devices menu in Vbox everything is grayed out.

Any ideas? I really want to be able to connect and access my android phone from my Windows VM.

Thanks!

---

### Post by kurt18947 on 2015-08-20
What do you see when you click settings -> USB in VirtualBox manager? Is it grayed out? I had your problem but adding myself to vboxusers group fixed it.

---

### Post by v3.xx on 2015-08-20
Also verify that the extpack is installed.

[http://www.itzgeek.com/how-tos/mini-howtos/how-to-install-virtualbox-extension.html](http://www.itzgeek.com/how-tos/mini-howtos/how-to-install-virtualbox-extension.html)

---

### Post by charmcityslacker on 2015-08-20
Nevermind. It totally works now. Must have done something dumb like forgotten to reboot my VM after installing the extpack or adding myself to the vboxusers group. My bad yall. Thanks for the help!

---

### Post by v3.xx on 2015-08-20
A reboot is normally the last thing I try and the first thing to work :lol:

---

