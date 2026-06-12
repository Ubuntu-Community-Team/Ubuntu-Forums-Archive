---
title: "screen: signal out of range"
date: 2012-02-13
forum: Ubuntu Studio
---

### Post by partos on 2012-02-13
I installed UBUNTU STUDIO 10.04 LTS. The OS was installed four times because I got a lot of problems with the screen (when I was working for example with GEDIT the screen was full with noise lines because the display was out of range). When I restart the computer I can see an error message: SIGNAL OUT OF RANGE 93.0 kHz/59 Hz. The problem appears always with or without NVIDIA controllers. My graphic board is: GT3 GEFORCE 7600 gs rev a1

---

### Post by sgx on 2012-02-13
[https://www.google.com/search?q=xorg.conf+signal+range+%22geforce+7600%22&hl=en&authuser=0&num=10&lr=&ft=i&cr=&safe=images](https://www.google.com/search?q=xorg.conf+signal+range+%22geforce+7600%22&hl=en&authuser=0&num=10&lr=&ft=i&cr=&safe=images)

in google:

xorg.conf signal range "geforce 7600"

If you find some useful information from the link, you can
use a live cd/dvd and edit the /etc/X11/xorg.conf on your hard-drive.

You can also try some non-debian distros, fedora, suse, mandriva etc
since the debian hardware sniffer does not always get along with
nvidia. I have two different nvidia setups, and when distro-hopping
among debian systems, it is unpredictable if either one will work.

---

