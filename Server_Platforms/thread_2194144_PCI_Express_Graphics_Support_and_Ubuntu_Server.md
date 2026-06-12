---
title: "PCI Express Graphics Support and Ubuntu Server"
date: 2013-12-16
forum: Server Platforms
---

### Post by ooboontwo on 2013-12-16
Hello,

Do most PCI Express graphics cards work "out-of-the-box" with Ubuntu Server 12.04?

I am only running a server terminal, so 3d performance is not even in the equation.

I just need to know whether or not most (or, all?) graphics cards will work without special drivers.

Background info: I made a mistake and bought an FM1 AMD CPU, not an APU and therefore it does not have a graphics chip onboard. So, I'm looking to buy a cheap, passively-cooled discrete GPU for this build.

Recommendations would also be appreciated. I am looking at either an nVidia 8400GS or Radeon HD5450 at the moment. Both are PCI-e 2.0 16x cards.

Thanks,
Cody

---

### Post by Bashing-om on 2013-12-16
ooboontwo; Hi !

I am running  "product: RV515 [Radeon X1300/X1550]", an ATI card installed to the pci-express slot ! - Real cheap card.
No problem at all on my part, outside of the fact that the card has been relegated to legacy status by ATI (AMD).
I do run with the open source driver.

Currently I understand that Nvidia offers the better support for their products in our world.

[INDENT][INDENT]hope that helps
[/INDENT][/INDENT]

---

### Post by papibe on 2013-12-16
Hi ooboontwo.

Ubuntu server and desktop's kernel were merged some time ago, so the 'drivers' compatibility is the same.

Are you running a [terminal server]("https://help.ubuntu.com/community/UbuntuLTSP"), a server version text only version, or just running terminals on a Desktop edition?

Regards.

---

### Post by ooboontwo on 2013-12-18
> **papibe said:**
> Hi ooboontwo.

Ubuntu server and desktop's kernel were merged some time ago, so the 'drivers' compatibility is the same.

Are you running a [terminal server]("https://help.ubuntu.com/community/UbuntuLTSP"), a server version text only version, or just running terminals on a Desktop edition?

Regards.

Hi papibe,

I am running "stock" Ubuntu 12.04.3 LTS Server. It does not have a desktop / GUI.

---

### Post by papibe on 2013-12-18
No problem then.

After you install the new card (and maybe selecting it as a default on the BIOS), you'll be using the open source version of the driver needed.

nouveau for Nvidia cards, and radeon for ATI/AMD cards.

I have an old laptop with Ubuntu Server installed. It has a Nvidia card, and it's using the nouveau driver:
```
$ lspci -nnk | grep -iA2 vga

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV17M [GeForce4 440 Go] [10de:0174] (rev a3)
	Subsystem: Toshiba America Info Systems Device [1179:0001]
	Kernel driver in use: nouveau

```
Hope it helps.
Regards.

P.S.: As far as I can tell, there won't be any boost in performance. May be you'll get a better resolution (more defined though smaller text fonts in this case).

---

