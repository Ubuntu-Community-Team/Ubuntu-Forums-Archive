---
title: "Ubuntu server with no video board"
date: 2012-06-20
forum: Server Platforms
---

### Post by bunn on 2012-06-20
Hi! I recently installed ubuntu server 12.04 (64 bits) on a pen drive. I need to use that pen drive do run a NAS. The NAS is currently running FreeNAS 8.2, running from a usb pen drive (that's why I don't have an HD)

Freenas is cool, but I'd rather have Ubuntu's flexibility.

The installation went fine, and I tested it successfully in a couple of machines. However, when I try to run on the intended machine, the SSH server does not respond (ip is configured manually).

That machine does not have a graphics board, and it ran fine the FreeNAS, so the machine does run headless. I tried changing grub to use the serial console instead, but the machine still doesn't boot. When I press power it powers off softly (I don't have to hold the button for 4 seconds), so It's not hanging.

What do I have to change for ubuntu server to boot without complaining that there's no video board/monitor? Adding a VGA to the machine would be impratical, also I don't wan't to tax the power source even more.

---

### Post by papibe on 2012-06-20
> **bunn said:**
> That machine does not have a graphics board...

Do you mean that the machine does not have a monitor connected?

or

Neither the motherboard's integrated graphics, nor a an external graphic card (like AGP, PCI, PCIe, etc) is present?

Regards.

---

### Post by bunn on 2012-06-21
There's no integrated graphics, and no external video board as well

---

### Post by bunn on 2012-06-22
Humm... I guess it can't be done then?

---

### Post by QIII on 2012-06-22
You can try installing xserver-xorg-video-dummy and see if that helps.

But if you are not running a GUI, it doesn't seem that it would matter.

---

### Post by arrrghhh on 2012-06-22
> **bunn said:**
> There's no integrated graphics, and no external video board as well

I've never dealt with such a beast.

How would you set it up initially?  You'd have to get some sort of monitor input, say, to get to the BIOS... No?

---

### Post by rubylaser on 2012-06-23
> **arrrghhh said:**
> I've never dealt with such a beast.

How would you set it up initially?  You'd have to get some sort of monitor input, say, to get to the BIOS... No?

You'd typically connect via serial cable if you don't have monitor input.  Or, if your motherboard is a server board (and supports it), you could connect via IPMI or similar technology to manage your BIOS.

---

### Post by arrrghhh on 2012-06-23
> **rubylaser said:**
> You'd typically connect via serial cable if you don't have monitor input.  Or, if your motherboard is a server board (and supports it), you could connect via IPMI or similar technology to manage your BIOS.

Yea, out-of-band management like a KVM would work.

Never needed to connect a serial cable to a server - only had to do that for routers!

So OP - are either of those options for you?  Not being able to see the boot process or manage the server pre-SSH is pretty crippling.

---

### Post by bunn on 2012-07-03
Sorry for the delay, and thanks everyone for the inputs! I'll try connecting a serial cable to it, and will post here how it went.

---

