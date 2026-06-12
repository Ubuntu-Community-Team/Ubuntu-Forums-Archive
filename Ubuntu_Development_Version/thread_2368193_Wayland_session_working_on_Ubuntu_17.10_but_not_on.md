---
title: "Wayland session working on Ubuntu 17.10 but not on Ubuntu 16.04."
date: 2017-08-08
forum: Ubuntu Development Version
---

### Post by kagashe on 2017-08-08
My hardware is Lenovo G50-45 which has AMD chip. I don't use any proprietary driver. 

I have downloaded Daily image of Ubuntu 17.10 and could login to Ubuntu Wayland Session and use it without any problem. I have checked suspend/resume and Bluetooth. Bluetooth works with wordaround as posted on the other post.

Since I am using Ubuntu 16.04 LTS which already has gnome desktop, I added gnome-session-wayland and tried to login but immediately logged out to the greeter.
Should I submit a bug report for Ubuntu 16.04 LTS?
ok it is already there
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1695872]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1695872")
I changed to GDM and I could login.

I would like to test Wayland session on Ubuntu 17.10 for my hardware.

Kamalakar

---

