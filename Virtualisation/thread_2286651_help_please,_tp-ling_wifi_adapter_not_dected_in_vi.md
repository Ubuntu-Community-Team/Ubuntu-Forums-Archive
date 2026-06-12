---
title: "help please, tp-ling wifi adapter not dected in virtualbox :("
date: 2015-07-13
forum: Virtualisation
---

### Post by patrick100 on 2015-07-13
ok,  so i have ubuntu 14.04 LTS installed on my labtop(which i love)

i downloaded kali linux and installed in a virtualbox, when i plug in my tp-link usb wifi adapter but when i try to add a usb filter in settings
it says "no device availble" it works grand with ubuntu, but i want it to work in virtualbox and kali linux

can anyone help??? :(


ps the driver for the tp-link usb wifi adapter is ; rtl8192cu

---

### Post by ajgreeny on 2015-07-13
Assuming your host is attached to the network the guest will also normally be connected and will not need any specific hardware.  However as your adapter is a USB, maybe there is a conflict when you try to add the adapter to the guest as that means it is no longer available to the host.  Try networking in the guest with that adapter USB disabled in the Devices set-up so it is available to the host and you may get a connection.

I have never used a USB connection adapter in a VM so I am not sure about my suggestion, but it is not permanent so worth a try.

Are you using the default NAT networking in VBox or a bridged connection?

---

### Post by patrick100 on 2015-07-14
bridged adapter, wlan1, iv tried wlan0 and etho and still got this when i type airmon-ng in the terminal, and stil doesnt show when i try to add a usb
filter :(

also i updated to virtualbox 5.0 today and still the same

[IMG]http://i886.photobucket.com/albums/ac64/planetpatrick/vbox_zpsgsnl7ihb.png[/IMG]

---

### Post by ajgreeny on 2015-07-14
Sorry but I know nothing of bridged connections in VBox, so can't help you with that problem any more, I'm afraid.

Incidentally I have tried VBox 5 on two machines, a desktop with i5-3570K and integrated HD4000 graphics, and a dual core laptop with  T3400 cpu and Mobile 4 Series Chipset IGP.  The laptop works fine but screen brightness is at about 20% on the desktop making it absolutely useless, so on that machine I have downgraded to VBox 4.3.30 again, which is fine.

---

### Post by patrick100 on 2015-07-16
can anyone else help?

---

### Post by v3.xx on 2015-07-16
Hummm..

Should work, but it don't.

I wonder if guest additions would do anything.  Got it installed?

---

### Post by patrick100 on 2015-07-17
nope, how do install that? would that help?

---

### Post by v3.xx on 2015-07-17
> **patrick100 said:**
> nope, how do install that? would that help?
I know you need it for usb access, I do not know if it will help you.
[https://www.virtualbox.org/manual/ch01.html#intro-installing](https://www.virtualbox.org/manual/ch01.html#intro-installing)

Be sure to download the correct extension pack version.
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

To install
[https://www.google.com/search?client=ubuntu&channel=fs&q=install+virtualbox+guest+additions&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=install+virtualbox+guest+additions&ie=utf-8&oe=utf-8)

---

### Post by patrick100 on 2015-07-20
ok, thanks anyway

---

