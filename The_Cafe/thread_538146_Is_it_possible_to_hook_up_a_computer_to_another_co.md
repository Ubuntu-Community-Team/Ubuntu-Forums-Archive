---
title: "Is it possible to hook up a computer to another computer via a USB or Firewire cable?"
date: 2007-08-29
forum: The Cafe
---

### Post by user1397 on 2007-08-29
I'm seeing all of these different usb and firewire cables on bestbuy.com, and I got to thinking, because I wanted to transfer a bunch of songs from my brother's macbook to my new vista desktop.

I'm seeing these USB A/A male to female, and firewire 4-pin to 4-pin...(is 4-pin the most common one?)

Does this mean that both ends for these cables are the same, so I can basically just hook up both computers with one cable? (Where would a macbook show up on in windows explorer if I did hook it up?)

Yes I know that USB 2.0 is technically faster than firewire (480Mbps vs 400 Mbps)

---

### Post by John.Michael.Kane on 2007-08-29
> **ubuntuman001 said:**
> I'm seeing all of these different usb and firewire cables on bestbuy.com, and I got to thinking, because I wanted to transfer a bunch of songs from my brother's macbook to my new vista desktop.

I'm seeing these USB A/A male to female, and firewire 4-pin to 4-pin...(is 4-pin the most common one?)

Does this mean that both ends for these cables are the same, so I can basically just hook up both computers with one cable? (Where would a macbook show up on in windows explorer if I did hook it up?)

Yes I know that USB 2.0 is technically faster than firewire (480Mbps vs 400 Mbps)

Yes it's possible.
[Connecting Two PCs Using an USB-USB Cable]("http://www.hardwaresecrets.com/article/248")
[USB Direct Connection]("http://www.conniq.com/FAQ/DCC-USB-cable-bridge.htm")

Note: The preferred method is using a ethernet crossover cable.

---

### Post by user1397 on 2007-08-29
> **SD-Plissken said:**
> Yes it's possible.
[Connecting Two PCs Using an USB-USB Cable]("http://www.hardwaresecrets.com/article/248")
[USB Direct Connection]("http://www.conniq.com/FAQ/DCC-USB-cable-bridge.htm")

Note: The preferred method is using a ethernet crossover cable.Ah, ok.
Why is ethernet recommended? Is it just because it is less of a hassle to set-up? Because USB is much faster than ethernet as far as I understand.

Also, is an RJ45 ethernet cable the same as a crossover cable?

---

### Post by John.Michael.Kane on 2007-08-29
> **ubuntuman001 said:**
> Ah, ok.
Why is ethernet recommended? Is it just because it is less of a hassle to set-up? Because USB is much faster than ethernet as far as I understand.
Not so much less hassle, As it is personal preference. Also in certain cases a ethernet crossover cable is easier to obtain.

> **ubuntuman001 said:**
> Also, is an RJ45 ethernet cable the same as a crossover cable?

Yes it's is RJ45 base, however. Compared to standard Ethernet cables, the internal wiring of Ethernet crossover cables reverses the transmit and receive signals.

---

### Post by reacocard on 2007-08-29
> **ubuntuman001 said:**
> Ah, ok.
Why is ethernet recommended? Is it just because it is less of a hassle to set-up? Because USB is much faster than ethernet as far as I understand.

Also, is an RJ45 ethernet cable the same as a crossover cable?

No its not the same, but you can get a little adapter to turn it into one for $7 from thinkgeek: [http://www.thinkgeek.com/gadgets/tools/7470/](http://www.thinkgeek.com/gadgets/tools/7470/)

---

### Post by user1397 on 2007-08-29
> **reacocard said:**
> No its not the same, but you can get a little adapter to turn it into one for $7 from thinkgeek: [http://www.thinkgeek.com/gadgets/tools/7470/](http://www.thinkgeek.com/gadgets/tools/7470/)already done :) tho it's more than $7 when you factor in shipping; that number actually doubles.

---

### Post by macogw on 2007-08-30
Ethernet also probably transfers faster than USB.

DO NOT use a USB A/A cable to do it.   It *has to* be a USB Transfer Cable.  If it's just a straight-up A/A, you might blow the USB ports on both computers.

---

### Post by user1397 on 2007-08-30
> **macogw said:**
> Ethernet also probably transfers faster than USB.

DO NOT use a USB A/A cable to do it.   It *has to* be a USB Transfer Cable.  If it's just a straight-up A/A, you might blow the USB ports on both computers.Okay, but I thought USB speeds were something like 480Mbps for USB 2.0, and ethernet was only 100Mbps (my network card only goes up to 100Mbps)

So how can the ethernet option possibly be faster than any USB 2.0 cable?

---

### Post by ssam on 2007-08-30
those are maximum signalling speeds. actual transfer speed depends on how efficient the protocols are.

in most cases for external disks firewire 400 is faster USB2. (firewire goes up to 800 Mbit/s these days (since 2003)). There is also a IP over firewire specification, for using firewire for networking.

have a read of
[http://en.wikipedia.org/wiki/Usb](http://en.wikipedia.org/wiki/Usb)
[http://en.wikipedia.org/wiki/Firewire](http://en.wikipedia.org/wiki/Firewire)

if one of the computers is a mac (i know this used to work with powerpc macs). try target disk mode [http://docs.info.apple.com/article.html?artnum=58583](http://docs.info.apple.com/article.html?artnum=58583) (it makes a mac pretend to be a disk). i dont know if vista can be made to read mac HFS+ partitions though.

---

### Post by viciouslime on 2007-08-30
> **ubuntuman001 said:**
> Okay, but I thought USB speeds were something like 480Mbps for USB 2.0, and ethernet was only 100Mbps (my network card only goes up to 100Mbps)

So how can the ethernet option possibly be faster than any USB 2.0 cable?

I don't know exactly how they get away with claiming that speed, it's a bit like wifi, a 54mbps wifi connection will never give you 54mbps throughput usually more like 20mbps. It's all to do with optimum conditions etc. etc.

A 100mbps ethernet connection will generally give you exactly that.

---

### Post by user1397 on 2007-08-30
> **ssam said:**
> those are maximum signalling speeds. actual transfer speed depends on how efficient the protocols are.

in most cases for external disks firewire 400 is faster USB2. (firewire goes up to 800 Mbit/s these days (since 2003)). There is also a IP over firewire specification, for using firewire for networking.

have a read of
[http://en.wikipedia.org/wiki/Usb](http://en.wikipedia.org/wiki/Usb)
[http://en.wikipedia.org/wiki/Firewire](http://en.wikipedia.org/wiki/Firewire)

if one of the computers is a mac (i know this used to work with powerpc macs). try target disk mode [http://docs.info.apple.com/article.html?artnum=58583](http://docs.info.apple.com/article.html?artnum=58583) (it makes a mac pretend to be a disk). i dont know if vista can be made to read mac HFS+ partitions though.ah, thanks for the speeds correction. I guess I'll read up on that.

Yea one of the computers is a macbook, but the other is a vista desktop, so I don't think that article applies to this case, since it says that the requirements for the host is to have a Mac OS.

---

