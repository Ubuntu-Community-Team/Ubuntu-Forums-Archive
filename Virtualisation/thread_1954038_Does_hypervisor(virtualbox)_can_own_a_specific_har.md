---
title: "Does hypervisor(virtualbox) can own a specific hardware"
date: 2012-04-07
forum: Virtualisation
---

### Post by jao_madn on 2012-04-07
Hi,

I would like to ask about the hypervisor, in my case im currently using oracle virtualbox, If a certain VM machine can own a single device or card (ex. pci audio mic/speaker card). i know in virtual box features, USB FILTER for usb device but how about the expansion card like audio in/out card.lets just say i want two windows xp vm machine with individual/independent speaker in and out for audio conversation. and not using the host audio in/out

Thanks in advance for any input.

---

### Post by CharlesA on 2012-04-07
Both VMs would share the host's hardware, but I don't know if they would have a separate audio in/out for each as I have never had a need to try that.

---

### Post by Cheesemill on 2012-04-08
Some virtualization hypervisors feature this ability, it is known as PCI passthrough.

You can use PCI passthrough to assign a PCI device (NIC, disk controller,  HBA, USB controller, firewire controller, soundcard, etc) to a virtual  machine guest, giving it full and direct access to the PCI device.

The only solutions that I know of that feature this, however, are bare metal hypervisors such as Xen and ESX, it is not supported using VirtualBox.
Also you need BIOS that specifically supports this feature (which I think is only available on server grade motherboards).

---

### Post by CharlesA on 2012-04-08
I believe KVM supports that as well.

---

### Post by jao_madn on 2012-04-09
@Cheesemill: Thanks for the tips on pci passthrough, i tried it on my amd 6 core desktop with pci express nic dlink and host linux with current virtualbox and it works although their are some requirement i need to enable ioapic=on and chipset=ich9 on the VM, it works on linux VM i did not try it on windows VM maybe tomorrow, I'm planning to buy a pci express audio in/out to test it practically, i think its much cheaper right now..

My objective about this Q is to run a Windows VM on a separate monitor, usb (mouse, keyboard, webcam using usb filtering) and the separate audio in/out for audio call. for separate person while im using. And also i had this in mind to use this concept to build a small business internet cafe in my parents place using one physical hardware CPU with multiple user/monitor for productivity and internet usage, of course not for gaming..

Any input will highly appreciated,

---

### Post by Cheesemill on 2012-04-09
No need to go the VM route, what your after is known as a multi-seat installation.

Just google for 'multi-seat' and you'll find loads of tutorials for both Linux and Windows.
Obviously there are licensing costs involved with going the Windows route (via Windows MultiPoint Server) but using your method you would need a seperate Windows licence for each VM anyway.

[http://www.microsoft.com/windows/multipoint/](http://www.microsoft.com/windows/multipoint/)
[https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)

---

### Post by jao_madn on 2012-04-09
> **Cheesemill said:**
> No need to go the VM route, what your after is known as a multi-seat installation.

Just google for 'multi-seat' and you'll find loads of tutorials for both Linux and Windows.
Obviously there are licensing costs involved with going the Windows route (via Windows MultiPoint Server) but using your method you would need a seperate Windows licence for each VM anyway.

[http://www.microsoft.com/windows/multipoint/](http://www.microsoft.com/windows/multipoint/)
[https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)

@Cheesemill: Thanks very much, i highly appreciate your input, I had no idea before you mention about multi-seat system, just a couple of googling and reading now i totally amazed on the idea and specially the benefits of a multi-seat system..Reading furhter ill be back for some more questions if its ok.

By the way about windows multi-point server im confused on the hardware mapping how about my primary concern on four heads individual audio in/out for video calling, the multi-seat linux system will good for me but for my future plan on something like a cafe i would prefer windows multi-heads and will point me again in the independent audio in/out. Maybe i will better understand first what your share and once again thanks much for the sharing in this one..

---

### Post by Cheesemill on 2012-04-09
I've never set up a multi-seat environment before so can't help much, however, I think the easiest way of doing audio would be to have a USB headset/sound card for each user.

---

