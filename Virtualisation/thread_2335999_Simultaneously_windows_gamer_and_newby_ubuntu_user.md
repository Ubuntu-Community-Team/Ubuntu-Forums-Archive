---
title: "Simultaneously windows gamer and newby ubuntu user (qemu/kvm, vga passthrough)"
date: 2016-09-03
forum: Virtualisation
---

### Post by bitter.cynic on 2016-09-03
[FONT=verdana]I suck at introductions, hi.

I can probably manage without hand-holding but i reckon i will avoid many dumb mistakes with some good advice.

As the title implies i intend to use a single PC to simultaneously run windows and ubuntu without rebooting.
[I](My gamer habit is a bit excessive, i'd never become a linux user with dual boot.)
[/I]
Afaik i have the hardware support for doing this?
[/FONT]1. Should have vt-x, might have to enable in bios
 2. Slightly concerned about a PCI-E card used for Sata3 and USB3, the SSD does have somewhat higher read speeds via that extension card than the onboard Sata2

Specs:
Motherboard [Asus P6T]("https://www.asus.com/Motherboards/P6T/overview/")
CPU [Xeon W3520]("http://ark.intel.com/products/39718/Intel-Xeon-Processor-W3520-8M-Cache-2_66-GHz-4_80-GTs-Intel-QPI") *(very similar to i7 920)*
Memory triple channel 3x2GB [*Corsair CMX6GX3M3A1600C9*]("http://www.corsair.com/en/cmx6gx3m3a1600c9")
Current GPU (guest) [Sapphire HD7870]("http://www.sapphiretech.com/productdetial.asp?pid=58D84CE3-3BB0-46E0-981A-B86ED31CA295&lang=eng")
Old repurposed GPU (host) XFX HD5770
PCI-E sata3, usb3 extension card [Delock 89359]("http://www.delock.com/produkte/G_89359/merkmale.html")
System SSD *(connected via PCI-E extension card) *[Corsair Neutron 256GB cssd-n256gb3-bk]("http://www.corsair.com/en/neutron-series-256gb-sata-3-6gbs-ssd")
Daily use HDD storage 2x500GB *(connected straight to motherboard Sata2 I/O ports)* Samsung HD501LJ and Seagate ST3500630NS
Network connected via gigabit port on the motherboard

I can't remember the last time i even used the DVD-RW drive so i don't really care if that somehow doesn't work.
Pretty typical wired keyboard and mouse, don't expect problems with that.
Don't really expect problems with monitors either.
A wired xbox 360 gamepad
Occasionally used USB microphone [Samson Go Mic]("http://www.samsontech.com/samson/products/microphones/usb-microphones/gomic/")

[B][Graphics tablet XP-Pen Star 03]("http://www.xp-pen.com/goods/show/id/9.html") alternatively Wacom Intuos CTH-480/S [I](highly prefer/must have the XP-Pen one due to larger size and button layout)
[/I][/B]I will most likely be using Krita most of the time so long as the graphics tablet functions properly, in the worst case i will fall back to using windows for drawing.

Some questions i have:
Can i install ubuntu studio on the windows system drive while keeping the windows installation intact? (Different file systems? Possible to shrink existing NTFS volume to give room for Ubuntu?)

How fast/slow is ubuntu studio on a 7200 HDD compared to an SSD? Maybe it's better to just dedicate one of the 500GB drives or a portion of it to Ubuntu?

How should i expect most of my devices to behave with a virtualized guest windows? Will a typical USB plug and play device (like a gamepad) work as on any other windows computer or does the virtualization complicate things?

Don't really expect anyone to know this but would two different GPUs cause the 16 lane PCI-E to work in v1.1 mode rather than v2.0? For example when i swap the x4 sata exension card over from the slower third slot to one of the first two full x16 lane slots, GPU-Z then reports the GPU working at v1.1 rather than the normal v2.0. [A block diagram for x58 chipset if that helps.]("http://img.hexus.net/v2/cpu/intel/Corei7/X58b.png")

Anything obscure i should know beforehand about qemu/kvm and pci-e passthrough?

Thanks in advance.

---

### Post by howefield on 2016-09-03
Thread moved to the "*Virtualisation*" forum, probably a better fit.

---

