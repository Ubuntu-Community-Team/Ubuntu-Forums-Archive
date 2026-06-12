---
title: "Ubuntu Hopes and Dreams"
date: 2009-05-29
forum: Testimonials &amp; Experiences
---

### Post by iKevin09 on 2009-05-29
I really love Ubuntu. I really love Linux. I know some basic commands in Terminal, and I admire the stability and usability of Ubuntu. I've been trying for about two days now to install one program. There's always something wrong with the installation. I either need gettext files, python builds, newer version of intltool to name off a few. I'm trying to install Blueman 1.10 so I can tether my BlackBerry to Ubuntu. That way I can ditch Windows completely and become an Ubuntu man.

I'm still a very fresh new user of Linux and Ubuntu, but I hope to learn more from this site. For now, I really need users help to pull me through this some-what impossible roadblock..

Here's the link to the problem I'm having. If you guys can help, it would be deeply appreciated.
[http://ubuntuforums.org/showthread.php?t=1172877](http://ubuntuforums.org/showthread.php?t=1172877)

---

### Post by HappyFeet on 2009-05-29
Welcome to ubuntu. To get Blueman installed, just insert the following into your sources.list (ask if you don't know how) 
```
deb http://ppa.launchpad.net/blueman/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/blueman/ppa/ubuntu jaunty main
```
then 
```
sudo apt-get update
```
Then you can search for Blueman in synaptic package manager.

Actually, you need to copy and paste the following into a blank text file **first** (before doing sudo apt-get update). (call it what you want):
```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXdhSgEEANHQYiA3beVTW6fb+CoRTyGwBybdgRetQ7/Pi6pSC44Gfd0J1z52sMYkm2MF
wg94pt/gRsx8UaCySoIiBp5FNFcOP5+wZQsQJcKSDQFG7QPJ2izkoUOhZSCHLOkefiru0DKt
maJ+VAhIKU0vEP80sou9mtnhGNumbMtzEMxezUbjABEBAAG0KkxhdW5jaHBhZCBQUEEgZm9y
IEJsdWVtYW4gRGV2ZWxvcG1lbnQgVGVhbYi2BBMBAgAgBQJJd2FKAhsDBgsJCAcDAgQVAggD
BBYCAwECHgECF4AACgkQaxWrkZUdweLSPAP+JbBBMqFge3a/ob3c8t2bLWkhs/5czJ1p5PPI
8lZeyjYF5N7FiuqtiS6joxk1z/w84lYU48JEQRvXTaI1VOQhjV5dHsuFCK4/9hKGWnb3JYDz
XEds+4UrSetPZ6lsXW1sEEwQNI8Jo5u1BaOqn3WgM936pZve48bXXHgsN0OaSl8=
=zUgC
-----END PGP PUBLIC KEY BLOCK-----

```
Then go to System>Administration>Software Sources>Authentication>Import Key File and point it towards the text file you just made. Take your time and it should be no problem.

---

### Post by iKevin09 on 2009-05-30
I was trying to install the incorrect version of Blueman. I downloaded the correct version of Blueman 1.10 and it installed via a GUI. Now my Bluetooth Dongle and my Blackberry Curve 8330 (Sprint) works wonderfully. I love Ubuntu, I'm never going to boot Windows, ever again.

My hopes and dreams are starting to become reality.

---

