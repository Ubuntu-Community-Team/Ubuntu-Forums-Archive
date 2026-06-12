---
title: "Need network settings help. Ubuntu Server in Ubuntu Desktop"
date: 2011-10-26
forum: Virtualisation
---

### Post by Swerve1000 on 2011-10-26
Hi,

I need some help with how to configure the network settings in VirtualBox.

The host machine is Ubuntu 11.04 Desktop. The guest is Ubuntu Server Ed.

I am trying to SFTP into the guest, but I cannot get the network settings correct, here are two screenshots:


[IMG]http://i42.tinypic.com/25uifzp.png[/IMG]

[IMG]http://i42.tinypic.com/29xz1u9.png[/IMG]

I really dont care how I get access to the files I have in the guest, I just need to get them out from it.

Can anyone tell me how to 'reset' or get it working? Been stuck trying all day.

Thank you very much :)

---

### Post by haqking on 2011-10-26
> **Swerve1000 said:**
> Hi,

I need some help with how to configure the network settings in VirtualBox.

The host machine is Ubuntu 11.04 Desktop. The guest is Ubuntu Server Ed.

I am trying to SFTP into the guest, but I cannot get the network settings correct, here are two screenshots:


[IMG]http://i42.tinypic.com/25uifzp.png[/IMG]

[IMG]http://i42.tinypic.com/29xz1u9.png[/IMG]

I really dont care how I get access to the files I have in the guest, I just need to get them out from it.

Can anyone tell me how to 'reset' or get it working? Been stuck trying all day.

Thank you very much :)

You are bridged to your eth interface, is that the one you you use on your host ? if not and you are using wlan for example you need to bridge to that.

If you just want the files though then drop them into your shared folder ?

---

### Post by Deepak Goel on 2011-10-26
Did you try using NAT instead of Bridge. The NAT option is a default option and it works pretty well.

Thanks,
Deepak

---

### Post by collisionystm on 2011-10-26
You want to use Bridged. Not NAT.

In your server, why is there a "virbr0"

Did you do something in there? A default install will only have eth prefixed adapters.

Either way... Can you ping 192.168.122.1 ?

---

### Post by haqking on 2011-10-26
> **collisionystm said:**
> You want to use Bridged. Not NAT.

In your server, why is there a "virbr0"

Did you do something in there? A default install will only have eth prefixed adapters.

Either way... Can you ping 192.168.122.1 ?

virbr0 is a virtual bridge.

The OP as far as he has mentioned so far just wants access to some files, i dunno why they cant just use shared folders ?

but yeah if you want networking and dont need to use bridged then go for the default NAT

---

### Post by collisionystm on 2011-10-26
> **haqking said:**
> virbr0 is a virtual bridge.

The OP as far as he has mentioned so far just wants access to some files, i dunno why they cant just use shared folders ?

but yeah if you want networking and dont need to use bridged then go for the default NAT


Weird.. all the Virtualbox installs I have ever done, I have never had a virtual bridged adapter.

Networking with NAT only works in one direction. From guest to host, not the other way around.

The shared folder idea will work with NAT.. but sftp... no.

---

### Post by haqking on 2011-10-27
> **collisionystm said:**
> Weird.. all the Virtualbox installs I have ever done, I have never had a virtual bridged adapter.

**Networking with NAT only works in one direction. From guest to host, not the other way around.**

The shared folder idea will work with NAT.. but sftp... no.

Yeah i know that, which is why my first reply never mentioned using NAT, the OP is already using bridged.  However it is not strictly true semantically speaking as you can configure port forwarding to allow outside the guest to communicate with the guest [http://www.virtualbox.org/manual/ch06.html#natforward](http://www.virtualbox.org/manual/ch06.html#natforward)

Shared folders works regardless of NAT or bridged, though im sure you know that, your wording looks like it is Network configuration dependant.

Anyways all semantics until the OP gets back ;-)

Peace

---

