---
title: "New to Sun Blade 100"
date: 2006-11-16
forum: Sun Sparc Users
---

### Post by phillips321 on 2006-11-16
Hi guys,

I have used linux for quiet some time so will be fine with that side of things. The problem is that i have just aquired a Sun blade 100 machiene free of charge.

I'm trying to get the thing to boot an ubuntu cd.

I have plugged in a basic crt monitor and a mircosoft usb keyboard and mouse.

When i switch the machiene on i here the drives spin up but i don't get anything on the display, not even and flicker, nothing at all.

I'm using the onbaord gfx as there is no other card plugged in.

Any ideas? Shouldn't i get a normal boot screen like an x86 pc?

I have never used a sun system before so would be very greatfull for some help.

Many thanks in advance guys

cheers

---

### Post by the_original_billq on 2006-11-17
Are you *sure* you have no other framebuffer on the blade?  Look for a connector called a "13w3" - 13 little pins with 3 fat pins - two on one end, and one on the other.  This would be an add-on PCI card.  Remove this card and try the onboard graphics again.  Also, it may be picky about the monitor.  Do you have a fairly decent monitor connected?

The Sun hardware manuals are [online]("http://www.sun.com/products-n-solutions/hardware/docs/Workstation_Products/Workstations/Sun_Blade_Workstations/index.html")

Hope this helps...

---

### Post by steil on 2007-02-05
Maybe reviving a dead thread, but what it sounds like is your machine might think its headless. Maybe try using a different keyboard, I had to try a couple different ones before I found one that worked.

---

### Post by wolfe716 on 2007-02-05
I would have to agree with the headless part.  What I would recommend doing is what I did. 

I went out to eBay and did a search for Sun keyboards and picked a keyboard and mouse up at a good price.  Once you do get a Sun keyboard (Type 5 I believe) and connect it and the mouse, you will be good to go.

~~ Robert

---

### Post by Moulton on 2007-02-05
When you power on the machine, does the Sun Open Boot splash page come up on the CRT?  If not, your NVRAM might be set to use the serial port as the console.  If so, you will have to hook up a suitable VT terminal to the serial port to change the NVRAM settings back to the CRT and keyboard.

Typically on a Sun machine, the presence or absence of a Sun type keyboard will also switch the console to or from the CRT if the NVRAM settings are at default values.  

One other thing to keep in mind -- some Sun models with onboard graphics adaptors require at least one stick of video RAM to be installed, or the onboard frame buffer won't work.  If your machine has S-Bus slots, it is not uncommon to find an older S-Bus graphic adaptor (eg CGsix) installed rather than shell out big bucks for enabling a fancier graphic adaptor.

Given that Sun machines are often used as headless servers rather than workstations, you might have to do some tinkering to convert it over to use a console keyboard and graphic adaptor.

---

### Post by steil on 2007-02-05
I've had luck using a "Dynex" Keyboard, was black and had multimedia keys. It came in a package with an optical mouse for $19.99 at futureshop ([http://www.futureshop.ca)](http://www.futureshop.ca)). Worked fine. Only thing to remember is if you are booting with a generic pc keyboard, you have to press the power button (i do it 4 consecutive times) after the boot to get into the openboot prompt.

---

