---
title: "Ubuntu Server 10.10: iwconfig doesn't install by default"
date: 2010-10-11
forum: Server Platforms
---

### Post by vanquishv12 on 2010-10-11
So I installed Ubuntu Server 10.10 64-bit for testing purposes.  But when I went to connect it to my wireless network at home, it showed that iwconfig wasn't installed by default like it did in 10.04.  Does anyone know how I can either connect my system to the network without using iwconfig, or how I can get iwconfig and install it from a flash drive or some other form of digital media? And I can't do apt-get since I can't get on my network.  And I also can't plug in a ethernet cable because my network port is broken.

---

### Post by '76 on 2010-11-05
I see this post is a bit old, but I had to figure this out today and will put this here for people searching.

Heres what you should have done to install iwconfig.

Run your server install.

when it gets to Software selection screen go down to Manual package selection and hit your spacebar. then enter.

Youll be in aptitude now.

choose Not installed packages
choose Net
choose Main
choose wireless-tools
hit the plus sign on your keyboard to change it to pi in green
hit g
hit g
hit enter after its done
hit q
choose yes

that will include iwconfig in your 10.10 server installation.

---

### Post by arnavk007 on 2010-11-05
Yes he's right as normally servers don't need wifi
you'll need to manually install it as he said otherwise you can download the deb file and use dpkg to install it from pen drive

---

### Post by '76 on 2010-11-05
I dont think gdebi will install automatically so no dpkg.

Can someone detail how to mount a pendrive properly according to what aptitude will accept? 

Also how to install a package from usb with aptitude.

---

