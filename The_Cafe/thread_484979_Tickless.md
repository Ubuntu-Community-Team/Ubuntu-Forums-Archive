---
title: "Tickless"
date: 2007-06-26
forum: The Cafe
---

### Post by PartisanEntity on 2007-06-26
Been reading about current efforts to make Linux better at saving power. As far as I have read kernel 2.6.21 is now tickless, which means instead checking for tasks between 100 and 1000 times/second it will only be woken up when a task needs to be done.

This will add to power saving at around 15 - 25%.

Also, Intel has released PowerTop, an application that checks how many 'pings' are sent to the processor.

Here is a list of known software:
[http://www.linuxpowertop.org/known.php](http://www.linuxpowertop.org/known.php)

---

### Post by reacocard on 2007-06-26
> **PartisanEntity said:**
> Been reading about current efforts to make Linux better at saving power. As far as I have read kernel 2.6.21 is now tickless, which means instead checking for tasks between 100 and 1000 times/second it will only be woken up when a task needs to be done.

This will add to power saving at around 15 - 25%.

Also, Intel has released PowerTop, an application that checks how many 'pings' are sent to the processor.

Here is a list of known software:
[http://www.linuxpowertop.org/known.php](http://www.linuxpowertop.org/known.php)

This tickless thing sounds really good. A 20% increase on my 6 hours of battery life would be an insane 7+ hours! And that's with wifi on! Doesn't gutsy already have .21? Can any gutsy users confirm a battery life increase?

---

### Post by prizrak on 2007-06-26
> **reacocard said:**
> This tickless thing sounds really good. A 20% increase on my 6 hours of battery life would be an insane 7+ hours! And that's with wifi on! Doesn't gutsy already have .21? Can any gutsy users confirm a battery life increase?

I doubt there would be much increase with Gutsy being a beta and all.

I am tempted to try out the testing builds because battery life is the absolute killer on my laptop. With two batteries (primary and secondary) I can only get 4 hours. This is of course wi-fi + Beryl and an nVidia card.

---

### Post by 5-HT on 2007-06-26
> **reacocard said:**
>  Doesn't gutsy already have .21?  Gutsy has a patched 2.6.22rc
> **reacocard said:**
> Can any gutsy users confirm a battery life increase?
I've been running a custom 2.6.21-ck2 kernel with tickless support for a while now. Haven't really noticed any significant increase in battery life, but I don't really keep my notebook on for long periods of time when idling. Perhaps by tracking down costly wakeups with PowerTop I'd really be able to take advantage of a dynamic/tickless kernel.
cheers,

---

### Post by Mahesh_Roy on 2008-01-14
I ran the x86 based tickless patches and i wish to do the same for my PPC board as well. Are there any patches for PPC32? Can i get these patches anywhere?"

---

### Post by khensucat on 2008-01-14
From what I've read, it takes more than the tickless kernel to give you real-life power savings. In a head to head at Phoronix, Dapper actually gave better battery life than Gutsy because of less overhead and bling, running processes, etc... ;) A tickless kernel underneath Compiz, tracker, etc.. does you almost no good at all.

ETA: That was at release time, though, so that info could be outdated by now.

---

### Post by Presto123 on 2008-01-14
I'm getting about an hour or more extra on my lappy battery with Gutsy than Vista. But, I would guess that's no surprise.

---

### Post by erykroom on 2008-01-14
My battery lasts with Gutsy about 4 hours. In Windows XP it was 7,5 hours. 
Ok when I got the laptop and XP was on it the battery was new, but iI doubt that the lifetime of a battery can degrade so fast. (7 months)

---

### Post by ssam on 2008-01-14
> **erykroom said:**
> My battery lasts with Gutsy about 4 hours. In Windows XP it was 7,5 hours. 
Ok when I got the laptop and XP was on it the battery was new, but iI doubt that the lifetime of a battery can degrade so fast. (7 months)

maybe a specific piece of hardware that linux does not know how to put in to a low energy mode. what graphics card and wirless do you have? what CPU? are you running compiz and tracker?

---

### Post by erykroom on 2008-01-14
I think the hardware should be ok because it's mostly from Intel Corporation and Intel has pretty good driver support. But ofcourse I'm no expert on hardware compability.
My computer 
arko@erykroom:~$ lspci -tv
-[0000:00]-+-00.0  Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
           +-02.0  Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
           +-02.1  Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
           +-1b.0  Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller
           +-1c.0-[0000:0b]--
           +-1c.1-[0000:0c]----00.0  Intel Corporation PRO/Wireless 3945ABG Network Connection
           +-1c.3-[0000:0d-0e]--
           +-1d.0  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller
           +-1e.0-[0000:02]--+-00.0  Broadcom Corporation BCM4401-B0 100Base-TX
           |                 +-01.0  Ricoh Co Ltd R5C832 IEEE 1394 Controller
           |                 +-01.1  Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
           |                 +-01.2  Ricoh Co Ltd R5C843 MMC Host Controller
           |                 +-01.3  Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter
           |                 \-01.4  Ricoh Co Ltd xD-Picture Card Controller
           +-1f.0  Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller
           \-1f.3  Intel Corporation 82801G (ICH7 Family) SMBus Controller

---

