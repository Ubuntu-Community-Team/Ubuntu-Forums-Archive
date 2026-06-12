---
title: "Wireless cards that actually work"
date: 2007-07-28
forum: The Cafe
---

### Post by forrestcupp on 2007-07-28
I've seen threads that talk about wireless that doesn't work.  How about one where we talk about wireless cards that actually work with Ubuntu?

I have heard that Dynex cards work very well.  What other ones have you gotten to work?

---

### Post by jimbob on 2007-07-28
Cards with  Atheros chips are supported but I do not know the particular brand names.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by Paul820 on 2007-07-28
Here's mine: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

Worked as soon as i plugged the router into the wall.

---

### Post by aysiu on 2007-07-28
Intel Pro Wireless 2200

---

### Post by thisllub on 2007-07-28
The inbuilt wireless in my Acer laptop works beautifully.

I gave up on an Asus usb yesterday and left it booting Windows.
Avoid RT73 usb at all cost.

---

### Post by mcurtiss1970 on 2007-07-28
linksys wpc11 VER.3

---

### Post by x0as on 2007-07-28
Belkin f5d7050 works with both ndiswrapper & the rt2570usb serialmonkey drivers.  Belkin f5d7010 works with ndiswrapper & Realtek 818x xp driver, drivers on the cd dont work though..

---

### Post by jiminycricket on 2007-07-28
Intel pro 2200 bg works perfectly

WUSB54G Linksys (uses a Ralink chipset which dosn't work with WPA anymore after network-manager was integrated.  Waiting for some new drivers that are in development to fix this)

---

### Post by forrestcupp on 2007-07-28
> **jimbob said:**
> Cards with  Atheros chips are supported but I do not know the particular brand names.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

Best Buy's house brand, Dynex, uses Atheros chips.

---

### Post by cmat on 2007-07-28
I have a D-Link PCIMA card on my laptop that was plug and play with my laptop. All I had was the MadWIFI drivers. I picked it up at Staples. It was a D-LINK WNA-1330 Wireless G Notebook Adapter. It has satisfactory range but it was the lower end model of what was there. I would assume that the range booster variants would work and have better range.

---

### Post by PenguinLover4Life on 2007-07-29
Atheros A500EG7 works great, but I have to use ndiswrapper and it took a bit of work to get it working. If you are patient you can make it work.

---

### Post by Spr0k3t on 2007-07-29
Just a note on the Atheros chipsets.  There is one AR5008 that does not work in Linux... yet.  The MadWifi group has a working trunk but it is very unstable.  The problem stems from the undocumented 802.11n.  So far I've only found DLink and Linksys to use this chipset.  Linksys has since moved their DraftN card over to Broadcom so I hear but it doesn't report the chipset in Linux.

That said... Atheros AR5212 802.11/ABG Rev 01 works like a charm (plug and play).  This chipset is on the Netgear WG311T.

---

### Post by Polygon on 2007-07-29
this site is a pretty good guide:

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

---

