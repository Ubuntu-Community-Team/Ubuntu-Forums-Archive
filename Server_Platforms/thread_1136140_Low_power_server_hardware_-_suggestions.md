---
title: "Low power server hardware - suggestions?"
date: 2009-04-24
forum: Server Platforms
---

### Post by jbbl on 2009-04-24
The server hardware I'm using now ([http://pentium.com/products/desktop/motherboards/D201GLY2/D201GLY2-overview.htm](http://pentium.com/products/desktop/motherboards/D201GLY2/D201GLY2-overview.htm)) is using way too much electricity, which is fairly expensive where I live. I measured it at 45 watts idle, which is costing me about $15 US per month. If I could find hardware that used much less while idling, it would pay for itself.

I currently have a 1TB SATA drive attached and a PCI gigabit ethernet card, so whatever HW would have to support SATA and either PCI or have onboard gigabit.

I've heard a lot about intel atom and ARM server boards - does anyone have any recommendations or suggestions? Thanks!

---

### Post by Kareeser on 2009-04-24
Atom could work, but the more traffic your server gets, the slower it'll hobble along.

Check out a mini-itx board, those are fancy. Find one that is compatible with a core2duo at the smallest nm you can find...

---

### Post by BkkBonanza on 2009-04-24
The Atom cpu is good and there is a dual core one too. I think it's the 330 model (or something like that). But from what I've read the problem so far is that the cheaper boards all use the Intel chipset that draws a lot of power so you don't get down too low overall. I think there are some Atom boards using a true low power chipset and those are the ones to look at. There was another thread on here last week with info on one dual-cpu atom board but I don't recall the details. A search should pick that up though.

Also to save power look at setting the hard drive spin down mode so that the drive sleeps when it's not been used for a while. There is a utility out there for that but don't recall right now.

---

### Post by jbbl on 2009-04-25
Thanks guys. The system does sit idle most of the time.

The traffic load is quite small though I do not want my traffic to become CPU bound (i.e. it should always be able to saturate the gigabit ethernet)

Currently the cpu (celeron 220 1.2GHz) has no trouble saturating the gigabit, so I would hope an atom is not that behind. Part of the issue is that the celeron has no power saving feature like frequency throttling.

It is mostly static data served through lighttpd, so cpu capability is probably not an issue. However, people also connect through ssh/sftp and so it has to be fast enough to encrypt/decrypt downloads and uploads.

---

### Post by TwiceOver on 2009-04-25
45w is pretty low already.  From what I have read the current Atom processor/chipset combo uses about 40ish watts.

Where do you live?  45w is costing you $15/mo?  That's some insanely expensive electricity.

---

### Post by cariboo on 2009-04-25
I'm using an intel atom motherboard for a media pc, it is the single core version, I haven't checked the power draw, but I have a 60 watt power supply and I haven't had any problems. I have an internal SATA hard drive and dvd r/rw as well as usb wifi adapter and wireless keyboard and mouse.

---

### Post by jbbl on 2009-04-27
you can thank the CA public utilities commission for this one. PGE rates go up to $.35/kwh + tax at 2x baseline. It could be worse, the top rate is $.41 + tax. Likely because most of our power is hydro, nuclear, or natural gas.

(to be fair, it's only that rate beyond the limit they set...but it's very easy to go above it even conserving)

I think I will wait until the low power atom chipsets come out (unless anyone knows of a low power ARM board w/ SATA + ethernet, that can run ubuntu)

Thanks guys!

---

