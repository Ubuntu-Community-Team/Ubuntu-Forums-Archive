---
title: "Xubuntu and Linux Frame Buffer (fbset)"
date: 2015-10-04
forum: Ubuntu, Linux and OS Chat
---

### Post by James_Lehman on 2015-10-04
Hello everyone.

I was wondering if there is someone here who knows about The Linux Frame Buffer; as in /dev/fb0 and fbset.

I just built a new computer with Xubuntu installed and an Nvidia graphics card that can do 4K. Plus I got a nice 65 inch curved screen LCD monitor that can do 4K.

On my Raspberry Pi 2, with Raspbian, I can boot into a high-res console and start and stop X easily.

I can also change the screen resolution and pixel color density.

I'd like to be able to do this in Xubuntu.

I'd love to be able to boot into a 32-bit 4K console!

Quite some time ago I wrote ezfb (a Linux Frame Buffer API) and I have been developing it to make it work better on the RPi2.

I'd really like to be able to get it working on this new Xubuntu machine.

I have successfully built kernel 3.19.8 and with that booted, I can get info from fbset as in mode 640x480. But I cannot issue any fbset command that changes anything.

Thanks in advance.

James.

---

