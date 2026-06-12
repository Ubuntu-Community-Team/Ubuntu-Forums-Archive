---
title: "Screen Stays Blank"
date: 2012-10-10
forum: Server Platforms
---

### Post by olograph on 2012-10-10
Hello, I'm quite good in computers but a huge noob in linux.

I installed the latest ubuntu server amd64for my NAS and everything goes lovely except if I leave the console for too long, the screen goes blank and says no signal.

The server's still on... e.g.: I can access my webmin page.

There's no way I can access the console back through the keyboard, I can only restart...

Tell me if you need more info.

Thanks

---

### Post by wojox on 2012-10-10
```
sudo nano /etc/default/grub
```
Look for [GRUB_CMDLINE_LINUX_DEFAULT] and add to the end:
```
acpi=off apm=off
```
Update Grub:
```
sudo update-grub
```
Reboot:
```
sudo shutdown -r now
```

---

### Post by olograph on 2012-10-10
I forgot to mention, when the system boots the screen is also blank. It does that half the time and I have to enter through recovery mode which works marvelously.

I did what you proposed, can't test it till I get to boot by trial and error.

Is there something to do with my screen being blank on startup?

---

### Post by 2F4U on 2012-10-11
Can you provide more information about your hardware? My guess would be that it is a problem with the graphics card.

---

### Post by olograph on 2012-10-11
Motherboard: Gigabyte A75M-S2V.

Processor: AMD A4-3400 APU Dual Core Processor Socket FM1 2.7GHZ

Graphics: AMD Radeon HD 6410D GFX (Integrated on CPU, yes CPU)

RAM: Kingston ValueRAM 4GB PC3-8500 DDR3-1066 DDR3

Utuntu Server's on 8GB USB 3.0 Flash Drive along with another one for swapspace.

---

### Post by wojox on 2012-10-11
> **olograph said:**
> I have to enter through recovery mode which works marvelously.

You can try it in recovery mode, you just don't need sudo cause you should be root.

---

### Post by olograph on 2012-10-12
Thanks a lot wojox.

I added nomodeset, recommended for blanks screen on boot along with the acpi=off and apm=off settings for the screen going blank to the grub file and all works like a charm now.

---

