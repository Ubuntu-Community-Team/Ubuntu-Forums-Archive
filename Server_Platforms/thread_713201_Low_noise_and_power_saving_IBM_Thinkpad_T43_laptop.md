---
title: "Low noise and power saving IBM Thinkpad T43 laptop as home server"
date: 2008-03-02
forum: Server Platforms
---

### Post by hemish on 2008-03-02
My Via Epia low power server board C3M266 died of [capacitor plague]("http://en.wikipedia.org/wiki/Capacitor_plague"), so now I will use an IBM Thinkpad T43 laptop instead, since it uses even less power, has more processing power, small size etc.

I previously ran Gentoo, but have now chosen Ubuntu Gutsy 7.10 Server. 

I now want to make it run as low power and low noise as possible. There are quite a bunch of power management packages and it's a little difficult to decide which works the best, has current support etc. Also relevant threads seems old (not Gutsy). So I hope someone can give me some hints on the currently best methods.

Do I choose apcid or apmd?

Do I use laptop-mode-tools?

How do I setup sleep and hibernate criteria? And can I trigger these modes directly from the command line?

What about setting up wake-on-lan (WOL)?

Fan control using [http://www.thinkwiki.org/wiki/ACPI_fan_control_script](http://www.thinkwiki.org/wiki/ACPI_fan_control_script) seems to require kernel module thinkpad-acpi. Is that available by default in 2.6.22 in Gutsy?
Is [tp-fan]("http://www.gambitchess.org/moin.py/ThinkPad_Fan_Control") the best choice?

---

### Post by ryth on 2008-03-18
I too am interested in setting up a laptop as an email/file server, and am curious as to if anyone has any specific recommendations?

The criteria I'd be looking for are:

1.  Low power consumption
2.  Low noise
3.  Low price

Since i'd only be using it as a fileserv/email set-up, processing power and RAM shouldn't be an issue, so older models that fit these criteria that I might be able to find on ebay would be better even.

Cheers.

---

### Post by hemish on 2008-03-19
> **ryth said:**
> I too am interested in setting up a laptop as an email/file server, and am curious as to if anyone has any specific recommendations?

The criteria I'd be looking for are:

1.  Low power consumption
2.  Low noise
3.  Low price

Since i'd only be using it as a fileserv/email set-up, processing power and RAM shouldn't be an issue, so older models that fit these criteria that I might be able to find on ebay would be better even.

Cheers.

A [NSLU]("http://en.wikipedia.org/wiki/NSLU2") or [Buffalo NAS]("http://en.wikipedia.org/wiki/Buffalo_network-attached_storage_series") are worth considering for low CPU/memory/noise/size demands.

For more power, but still cheap, small and relatively low noise is a solution based on [Intel D201GLY2 Mini-ITX mainboard]("http://www.silentpcreview.com/article780-page1.html"). Or see [VIA Epia mainboards]("http://www.via.com.tw/en/products/mainboards/") for very low power Mini-ITX foundations.

---

### Post by lavinog on 2008-03-19
I would look into via mini-itx's again...i saw one for $80 that ran a 1500 mhz processor.

Using a laptop as an always on server may not be such a good idea. The engineering behind laptops is to be portable.
For example: laptop hard disks are designed to park their heads frequently...check out this thread: [http://ubuntuforums.org/showthread.php?t=591503]("http://ubuntuforums.org/showthread.php?t=591503")

Do you plan to leave your battery in? The heat from computer always being on will reduce the capacity of the battery.  I would question if the power supply is rated to be left on for months...my compaq laptop power supply gets insainly hot after a couple of hours.

Could running a laptop be anymore efficient than that epia? I run a home server off of a via 800mhz epia...it uses only 13 watts during normal operations, occasionaly it draws up to a maximum of 30 watts at 100% cpu load and the hard drive running. I can't remember what my laptop operates at with the lid closed, but I can't see it being any better than the epia.
I am building a new server using an athlon xp 1000mhz processor, I am experimenting with using flash drives configured in a raid 0 setup for instant access with a hard drive for long term storage...I will be using this combination like a hybrid drive to maximize the sleep time on the hard disk.

just my two cents

---

### Post by ryth on 2008-03-20
> **lavinog said:**
> I would look into via mini-itx's again...i saw one for $80 that ran a 1500 mhz processor.

Could running a laptop be anymore efficient than that epia? I run a home server off of a via 800mhz epia...it uses only 13 watts during normal operations, occasionaly it draws up to a maximum of 30 watts at 100% cpu load and the hard drive running. I can't remember what my laptop operates at with the lid closed, but I can't see it being any better than the epia.


Hey thanks for the advice, I was just sort of sending out feelers as I wasn't sure what the best solution was.

What is the compatibility with ubuntu server like with these Epia chips?

 I am certainly interested if they are fully supported.  I would most likely  get one of the more bare-bones ones if I go this route, none of the video out etc, and just ssh in if need be.

Maybe I should start a new thread on this...

---

### Post by lavinog on 2008-03-22
> **ryth said:**
> Hey thanks for the advice, I was just sort of sending out feelers as I wasn't sure what the best solution was.

What is the compatibility with ubuntu server like with these Epia chips?

 I am certainly interested if they are fully supported.  I would most likely  get one of the more bare-bones ones if I go this route, none of the video out etc, and just ssh in if need be.

Maybe I should start a new thread on this...

Having video out is handy when you need to troubleshoot something...ssh is only good if the networking works.
Plus I think you need video to setup ssh if you don't setup a custom install disk or preload the installation. 
There is no real savings from removing the video card anyway. For systems that have shared memory, I just reduce the video memory to its minimum. Power consumption is pretty low too since the only thing being displayed is a text based login screen. I think some of the nano boards let you remove the video card (like a daughter board).

as far as the chip goes, I run a dedicated ut2004 server on it. It works just fine have so many mods on it now it needs a higher clock speed.
I think alot of the people that use mini-itxs put linux on them.

---

### Post by Whiffle on 2008-03-22
ACPI for sure, apm is outdated.

Probably don't need laptop mode tools, they're designed to help with running on battery.

Sleep and hibernate can be triggered from the command line, although I've never used hibernate.   Look around in /etc/acpi, there are many scripts there that deal with this.

WOL I've never used, but I'd imagine its supported.

You could look into tp-fancontrol from thinkwiki for your fan speed needs.

As far as the battery goes, my T43's battery  generally stays cool when its plugged in due to its location.  Right now its been running all day and only the bottom of the laptop is warm, battery is pretty much cool.  You could use sysfsutils and the tp_smapi module to set it so that it doesn't fully charge the battery though, keeping them fully charged is rough on them.

I would probably also go as far as to remove the internal hard drive and run off of a USB drive instead, that would help you out with the heat quite a bit I should think.

---

