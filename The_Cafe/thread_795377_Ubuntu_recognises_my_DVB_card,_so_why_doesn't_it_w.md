---
title: "Ubuntu recognises my DVB card, so why doesn't it work?"
date: 2008-05-15
forum: The Cafe
---

### Post by Bou on 2008-05-15
Hi,

This is neither a rant, nor a plea for help. After googling for some minutes, I got my card working just fine and dandy. There's just something I don't understand and I hope you can help me with that.

The thing is, I bought [this]("http://www.bestbuy.es/fichaProdExtensa.asp?IdProductos=219") DVB card. When I plugged it in, Ubuntu seemingly recognised it as the system log said:

>     May 14 09:20:08 david-laptop kernel: [ 3404.858890] usb 4-3: new high speed USB device using ehci_hcd and address 4
    May 14 09:20:08 david-laptop kernel: [ 1943.173758] usb 4-3: configuration #1 chosen from 1 choice
    May 14 09:20:08 david-laptop kernel: [ 1943.182103] input: Afatech DVB-T as /devices/pci0000:00/0000:00:1d.7/usb4/4-3/4-3:1.1/input/input10
    May 14 09:20:08 david-laptop kernel: [ 1943.201066] input,hidraw1: USB HID v1.01 Keyboard [Afatech DVB-T] on usb-0000:00:1d.7-3

But it still wouldn't work. So I got to [this]("http://www.ubuntu-es.org/index.php?q=node/76680") howto, and learned how to get it working:

> sudo apt-get install mercurial linux-headers-$(uname -r) build-essential gcc make
wget [http://www.telecable.es/personales/bbbaaa/dvb-usb-af9015.fw](http://www.telecable.es/personales/bbbaaa/dvb-usb-af9015.fw)
sudo cp dvb-usb-af9015.fw /lib/firmware/2.6.20-14-generic
hg clone [http://linuxtv.org/hg/~anttip/af9015/archive/tip.tar.gz](http://linuxtv.org/hg/~anttip/af9015/archive/tip.tar.gz)
cd tip.tar.gz
make && sudo make install
sudo gedit /etc/modules &#8594; include "dvb-usb-af9015"

The thing is, I always thought the Linux kernel already had all the available drivers. And yet Ubuntu wouldn't get my card working, despite the fact that it COULD identify it and that a working driver exists. Is there a way to get it in the kernel? To get Ubuntu to make a package, so I can just sudo apt-get install some package and get done with it?

---

