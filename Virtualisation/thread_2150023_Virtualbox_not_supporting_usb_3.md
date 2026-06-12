---
title: "Virtualbox not supporting usb 3??"
date: 2013-05-30
forum: Virtualisation
---

### Post by Timmy0829 on 2013-05-30
Hi,

I was trying to use my pendrive in virtualbox win7 guest. After 1-2 days searching I couldn`t make it work.

And I had an idea, that it maybe because I only have usb 3.0 ports, and my pendrive is usb 3 as well.

And I found this: [https://www.virtualbox.org/ticket/8873](https://www.virtualbox.org/ticket/8873)

Does anyone know anything more? If i dont have usb 2.0 how can I make it work?

Cheers

---

### Post by JKyleOKC on 2013-06-02
When I ran into this problem, I did a bit of googling and found VMWare Player, which is now a free product. I had switched from VMWare to VirtualBox several years ago, because the VMWare Server I had originally did not permit reliable control of its configuration. However, I needed USB support on a new machine, and VBox wouldn't do it. I downloaded VMWare Player, installed it, and it has been working wonderfully ever since. The configuration problems have been solved, and I'm a happy camper with it. USB works just as it should.

I still run VBox on my main production machines, but for any new machine I add, will be installing VMWare Player!

---

### Post by Timmy0829 on 2013-06-05
Thanks for the reply.

I will check out the VMWare Player too.

---

### Post by Rebelli0us on 2013-06-06
VirtualBox host can hand over to the guest any USB device, but I think that the guest must have support for USB 3.0 to it to work.

---

### Post by JKyleOKC on 2013-06-06
According to this thread ([https://www.virtualbox.org/ticket/8873](https://www.virtualbox.org/ticket/8873)) as of just three weeks ago VBox did not support USB3 and there was no plan to make it do so in the foreseeable future.

I certainly wish that it did, because the VBoxManage utility provides far more capability to customize a VM than does its equivalent in VMWare Player -- but Oracle apparently doesn't believe it's needed, and they own the product now.

---

### Post by Timmy0829 on 2013-06-06
Yes, I agree. I just couldn`t do anything to make it work. And I think its just because of I dont have any usb 2.0.

---

