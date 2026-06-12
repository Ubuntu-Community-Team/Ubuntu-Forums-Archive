---
title: "openvpn server bridged mode"
date: 2005-12-28
forum: Server Platforms
---

### Post by verdickt on 2005-12-28
Hi,

i installed everything, generated certificates ...

But i have a problem setting up bridged mode and tap devices

I searched the forums here and they link to a debian tutorial but this
link is down at the moment.

So it would be nice if someone could explain me how to setup my eth1 interface in bridge mode with tap devices and how to start them at
startup of the os

thanks in advance

---

### Post by cylon359 on 2005-12-28
Well, you'll first need to create a persistent tap, and set both devices to be up ie:

sudo openvpn --mktun --dev tap0
sudo ip link set dev tap0 up
sudo ip link set dev eth1 up

Then, you need to create the bridge device (sudo apt-get install bridge-utils if you don't have them):

sudo brctl addbr br0
sudo brctl addif br0 eth1
sudo brctl addif br0 tap0

Then you can use br0 as your device name.

If you want this at startup, you'll need to create a startup script for it, but I would try it at the command line first to make sure I have everything correct.

---

### Post by verdickt on 2005-12-28
thanks,

i wil give it a try

---

