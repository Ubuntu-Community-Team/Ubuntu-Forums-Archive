---
title: "Bluetooth on Gazelle Value?"
date: 2007-06-11
forum: System76 Support
---

### Post by IgnacioMiller on 2007-06-11
Hi all,

I was looking at my hardware using System>Preferences>Hardware Information and noticed that it had detected a bluetooth device. I installed a program off the repos (Bluetooth File Sharing) but I couldn't figure out how to get it to work.

I am trying to connect to a motoral phone to transfer some pictures from it. How do I/can I get my bluetooth to work?

Thanks,
Dan

---

### Post by AusIV4 on 2007-06-11
Unless they've changed their systems, the Gazelle does not have bluetooth. I think nearly any adapter you buy will work fine (I bought the cheapest USB adapter I could find, it worked out of the box), but it doesn't come built in.

---

### Post by tedrampart on 2007-06-12
my gazelle performance has bluetooth, it took awhile to setup though.. I would search the regular ubuntuforums on how to setup bluetooth.  I installed the gnome-bluetooth package, and bluez-pin, plus some obex file transfer software, and after a bit of setup it worked.  the current system76 driver doesn't seem to support the bluetooth I guess.  for now your best bet is to do it manually.

---

### Post by AusIV4 on 2007-06-12
This has me curious. My hardware manager indeed reports bluetooth, but I can't find it with lsusb, lspci, etc, so I'm not entirely convinced it's there. If there's a way to get it recognized I'd love to have bluetooth on my Gazelle without an obtrusive dongle.

---

### Post by thomasaaron on 2007-06-12
Hey, folks.

There were a few Gazelle Performances sent out with bluetooth.
If you weren't specifically told that you had one, you don't.

Best,
Tom

---

### Post by tedrampart on 2007-06-12
well that answers it.

I have a d-link usb adapter, and it was only about 40bucks, and it worked no problem.  I'm sure you can find one for cheaper than that, the dlink works forsure though.. DBT-122

---

### Post by thomasaaron on 2007-06-12
It would also have a bluetooth sticker beneath the 'powered by ubuntu sticker.'

---

### Post by IgnacioMiller on 2007-06-12
Tom: What if I have a Gazelle Value with Bluetooth? How can I use it?

Thanks,
Dan

---

### Post by thomasaaron on 2007-06-12
To be honest, I'm not exactly sure -- and I've got a Darter with bluetooth! :(  Shame on me.

If you go to Applications -> Add / Remove Software and type bluetooth in the search field, a number of bluetooth applications are available.

There is also some Ubuntu documentation on Ubuntu here:
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

Best,
Tom

---

