---
title: "Cannot set tap on KVM"
date: 2015-07-20
forum: Virtualisation
---

### Post by Yannis_P on 2015-07-20
Dear fellows,

I would like to thank you in advance for you patience but the whole virtualization think for me is quite new.
So the problem is as follows.

I run an Ubuntu server on my home and I want to try OSSIM on a VM.
I want the web interface of OSSIM accessible from my laptop when I'm connected to the wifi but my problem is that because the server connects to the home network solely with a wifi card I cannot enable Bridge Mode.
I have found a couple of guides to the internet on setting a tap on the server / VM host and use it to put the guest on my network but something I'm doing wrong and I have no success.

Can anybody give me a hand?

Thanks.
Yannis

---

### Post by TheFu on 2015-07-23
You can use a bridge with a wifi connection.  Just be certain the wifi is already "up" with a static IP **before** you bring up the VM.

BTW - doing this will be a pain, day after day, it will suck.  VM servers really need to be connected with an ethernet cable.

---

### Post by Yannis_P on 2015-07-25
Hello there.

Thank you a lot for your response.
I don't know if you have time to help further but it seems that I'm still in troubles.

First of all, my server is always up and even I reboot it the wireless gets up automatically and connect to my access point.
The problem is when I try to associate the bridge interface (br0) with the wireless (wlan) by issuing the command:
> brctl addif br0 wlan0
I get:
> can't add wlan0 to bridge br0: Operation not supported
According to all the guides i have found so far in the net you can not create a bridge on KVM with wlan (e.g. [http://unix.stackexchange.com/questions/118891/wireless-bridged-networking-in-kvm-why-is-it-so-complicated](http://unix.stackexchange.com/questions/118891/wireless-bridged-networking-in-kvm-why-is-it-so-complicated)).

Any ideas?

---

### Post by TheFu on 2015-07-25
Did you attempt to use the conf file?  /etc/network/interfaces

---

