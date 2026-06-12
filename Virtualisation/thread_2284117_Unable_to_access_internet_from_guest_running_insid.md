---
title: "Unable to access internet from guest running inside qemu. Guest not assigned an IP"
date: 2015-06-27
forum: Virtualisation
---

### Post by paranoid_android2 on 2015-06-27
Hey!

My first post on the forum!

My guest OS (MacOS) running in qemu isn't able to access internet. 
I went to network utility in MacOS and this is what I found: 

IP Address(es): Unknown

MAC address: [a valid MAC address]

So I guess the network adapter is working correctly, but the guest OS hasn't been assigned an IP address. How do I do this?

These were to instructions I followed to run Mac OS on qemu:

[http://nnucomputerwhiz.com/run-osx-in-ubuntu-with-qemu.html](http://nnucomputerwhiz.com/run-osx-in-ubuntu-with-qemu.html)

The only change I had to make was this:
Ethernet driver: PCGENRTL8139  was not available in the list for me. So I installed all the available ethernet drivers.

The only problem however is that I'm unable to connect to the internet from Mac OS.
 
My host machine is connected to wifi internet. But the guest Mac OS machine isn't able to connect to it.

PS: From what I read online, qemu should readily work  to allow internet access in guest. Why doesn't it work for me?
I don't need to access the guest from host via network or anything. I just want to be able to access the internet from the guest.

---

### Post by QIII on 2015-06-27
While it is not a violation of Apple's EULA to run other operating systems on their hardware, it is a violation of their EULA to run Apple operating systems on hardware other than Apple - physical or virtual.

Please refer to the [Forum Rules]("http://ubuntuforums.org/misc.php?do=showrules"):

> We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalised with infractions and warnings.

Thread closed.

---

