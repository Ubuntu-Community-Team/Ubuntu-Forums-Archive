---
title: "[SOLVED] Unable to mount usb in XP on Virtual Box"
date: 2008-12-16
forum: Virtualisation
---

### Post by emilbugge on 2008-12-16
Hi

I'm running windows XP on Virtual Box in Ubuntu 8.10.... i've tried everything i can think of... please help me.

Hi

I'm running windows XP on Virtual Box in Ubuntu 8.10.... i've tried everything i can think of... please help me

---

### Post by bumanie on 2008-12-16
The OSE version doesn't provide usb support, so if you are using that you are ](*,). Go to sun/innotek site and download the proprietry 'free for home use' version. Then follow [this]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html"). It's about a year old, but still works as far as I know.

---

### Post by nhasian on 2008-12-16
you can download the latest Virtualbox from their server here:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Add one of the following lines according to your distribution to your /etc/apt/sources.list with the command:

```
sudo gedit /etc/apt/sources.list
```

then add one of these lines to the end:
```
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
deb http://download.virtualbox.org/virtualbox/debian hardy non-free
```

The Sun public key for apt-secure can be downloaded [here]("http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc"). You can add this key with

```
sudo apt-key add sun_vbox.asc
```

or combine downloading and registering:

```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```

The key fingerprint is

```
AF45 1228 01DA D613 29EF  9570 DCF9 F87B 6DFB CBAE
Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>
```

once Virtualbox is installed, and you've installed your OS in there, you need to run the VirtualBox Guest Additions to make usb & network work

---

### Post by bodhi.zazen on 2008-12-16
Threads merged and moved :)

---

### Post by Knark on 2008-12-16
I would recommend this guide: [http://productivelinux.com/2008/11/09/how-to-get-usb-working-in-virtual-box-on-ubuntu-intrepid-ibex/](http://productivelinux.com/2008/11/09/how-to-get-usb-working-in-virtual-box-on-ubuntu-intrepid-ibex/) 

It really helped me

---

