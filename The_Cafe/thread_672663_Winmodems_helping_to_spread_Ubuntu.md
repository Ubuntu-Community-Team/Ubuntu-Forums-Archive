---
title: "Winmodems helping to spread Ubuntu"
date: 2008-01-19
forum: The Cafe
---

### Post by Raval on 2008-01-19
Just a note, some members feel winmodem support isn't a big deal most common response being "get DSL" but for those of us in the third world it's a no can do.

Since better Connextant modem driver support exist thanks to Dell for making them available I have signed on one person and about to switch my girlfriend and her entire family to Ubuntu.

As long as they can connect to the internet people are showing interest in trying Ubuntu.

BTW if anyone has 128MB or higher PC100 memory they'd like to donate please send me a PM.

My GF's machine is a HP Pavilion with 600MHz Celeron and two slots filled with 64MB PC100 each.

Anyone load Gutsy on a PC with these or similar specs?

---

### Post by Andrewie on 2008-01-19
that computer should run ubuntu or kubuntu, the ram is a little small so make a pretty big swap file (don't over do it) and things should run ok.

---

### Post by Sef on 2008-01-19
> Anyone load Gutsy on a PC with these or similar specs?

With 128 mb ram, I would use Xunbuntu.  It is made for older computers and will work much faster.

---

### Post by Raval on 2008-01-20
a swap of about 512mb?

---

### Post by Raval on 2008-01-20
> **Sef said:**
> With 128 mb ram, I would use Xunbuntu.  It is made for older computers and will work much faster.

I don't have Xubuntu and I'm on dialup. I have 7.04 and 6.10.

---

### Post by az on 2008-01-20
> **Raval said:**
> 
Since better Connextant modem driver support exist thanks to Dell for making them available I have signed on one person and about to switch my girlfriend and her entire family to Ubuntu.

Di you still have to enter a code to activate the full-speed use of the modem?  Usually, you need to pay 20 USD to register.

From [http://www.linuxant.com/drivers/hsf/install.php](http://www.linuxant.com/drivers/hsf/install.php)
[I]LICENSE KEYS / REGISTRATION
To enable your modem's full functionality (high-speed 56k data and FAX), a license registration key must be obtained from Linuxant and entered with "hsfconfig --license".

Without a proper license key, the modem can only operate in FREE mode, limited to a maximum speed of 14.4Kbps (V.32bis) and the FAX functionality will not be available.[/I]

> **Raval said:**
> 

As long as they can connect to the internet people are showing interest in trying Ubuntu.

BTW if anyone has 128MB or higher PC100 memory they'd like to donate please send me a PM.

My GF's machine is a HP Pavilion with 600MHz Celeron and two slots filled with 64MB PC100 each.

Anyone load Gutsy on a PC with these or similar specs?

A Conexant software modem will use 350MHz of your CPU cycles to run the HSF modem.  On more powerful machines, this is not an issue.  But on a 600 MHz Celeron, it's barely usable.

---

### Post by Raval on 2008-01-20
> **az said:**
> Di you still have to enter a code to activate the full-speed use of the modem?  Usually, you need to pay 20 USD to register.

From [http://www.linuxant.com/drivers/hsf/install.php](http://www.linuxant.com/drivers/hsf/install.php)
[I]LICENSE KEYS / REGISTRATION
To enable your modem's full functionality (high-speed 56k data and FAX), a license registration key must be obtained from Linuxant and entered with "hsfconfig --license".

Without a proper license key, the modem can only operate in FREE mode, limited to a maximum speed of 14.4Kbps (V.32bis) and the FAX functionality will not be available.[/I]



A Conexant software modem will use 350MHz of your CPU cycles to run the HSF modem.  On more powerful machines, this is not an issue.  But on a 600 MHz Celeron, it's barely usable.

I'm using the driver Dell has made available to everyone.

WHat should I do then?

---

### Post by az on 2008-01-21
Get a hardware modem.  Even a Controllerless modem (a modem with one more chip on it than a software modem - sometimes referred to as a semi-hardware modem) will consume about 150 MHz of your CPU's power.

---

### Post by persev on 2008-01-21
> **az said:**
> Get a hardware modem.  Even a Controllerless modem (a modem with one more chip on it than a software modem - sometimes referred to as a semi-hardware modem) will consume about 150 MHz of your CPU's power.

Could you recommend one? I set up a Ubuntu CE box for my 62 year old Mother-in-law and she only has dial-up available out the country where she lives. The box I set up has an Asus a7n8x mobo that has no rs232 serial port so I am looking for easy to get working pci modem. By the way it is a 4 hour road trip to "grand-ma's" house.

---

### Post by gradedcheese on 2008-01-22
Soft modems are when the modulator/demodulator is implemented in software, so they're basically cheap sound cards that rely on software to do the modulation.  Companies feel that this scheme is valuable intellectual property, so they won't release it to the public.  In the case of Linuxant, they had to license the modulator/demodulator and it cost them a bunch of money, the $20 fee is something they then have to 'pass on' to you.  It's not their fault.  Dell may or may not have paid that, I'd imagine that they have though.  It should be easy enough to find out, I suppose.

If you have a serial port, then a safe bet for a 'hardware modem' is an external, such as one of the old serial port modems (USRobotics, etc) that you might find for sale used somewhere (they haven't been made in years).  

Hardware modems have both the sound card part and the modulator/demodulator implemented as chips.  With a PCI or ISA card, it's really hard to tell if that's the case unless you can read about the particular model in question.  With an external serial port modem, it's a safe bet.

---

### Post by Dragonbite on 2008-01-22
Dial-up isn't just for 3rd world countries too.

I've been using a USRobotics External Modem.  That has been working like a charm because I can use it with just about any Linux distro I get my hands on (and I'm a distro-hound..).

If you get an external modem, it will ikely be located as a /dev/ttyS0 or ttyS1 or you can use 
# wvdialconf to detect and configure the modem (then you can edit the /etc/wvdial.conf file to add your username and password).

Dial-up is a pain, but in spite of what a lot of people thing, it works.

---

### Post by persev on 2008-05-19
I tried everything and just couldn't get anything to work from the desktop. I even bought an external hardware modem and couldn't use it as the mobo had no rs232 port. I bought a pci card with rs232 ports on it and the modem still wouldn't work. In the end I just installed XP on it. 

Here is what is odd, I was able to connect using linux with my T23 thinkpad using the conexant driver.

---

### Post by Raval on 2008-05-19
> **persev said:**
> I tried everything and just couldn't get anything to work from the desktop. I even bought an external hardware modem and couldn't use it as the mobo had no rs232 port. I bought a pci card with rs232 ports on it and the modem still wouldn't work. In the end I just installed XP on it. 

Here is what is odd, I was able to connect using linux with my T23 thinkpad using the conexant driver.


A PCI winmodem SHOULD be cheap in most parts of the world these days. See if you can find a winmodem with a conexant chip on it, and try to buy from a store that easily accepts refunds incase you wish to return it.

---

### Post by LaRoza on 2008-05-19
> **Raval said:**
> 
BTW if anyone has 128MB or higher PC100 memory they'd like to donate please send me a PM.

My GF's machine is a HP Pavilion with 600MHz Celeron and two slots filled with 64MB PC100 each.

Anyone load Gutsy on a PC with these or similar specs?

I have a computer with similiar specs. I added RAM though to max it out at 256 MB. I have the extra 64 MB DIMM, but I doubt you want that...

I use Debian on it, but I had Wolfix on it. Wolfix is easier to use I think and has many more GUI tools. See my blog (I put Debian back on with a few essential applications)

---

### Post by Raval on 2008-05-19
> **az said:**
> Di you still have to enter a code to activate the full-speed use of the modem?  Usually, you need to pay 20 USD to register.

From [http://www.linuxant.com/drivers/hsf/install.php](http://www.linuxant.com/drivers/hsf/install.php)
[I]LICENSE KEYS / REGISTRATION
To enable your modem's full functionality (high-speed 56k data and FAX), a license registration key must be obtained from Linuxant and entered with "hsfconfig --license".

Without a proper license key, the modem can only operate in FREE mode, limited to a maximum speed of 14.4Kbps (V.32bis) and the FAX functionality will not be available.[/I]


The modems do not require any license for full speed.

I use a Dell B110 that comes with a Connexant modem and I use the same .deb driver and get full 56k.

BTW for the record there is also a driver for modems with Intel 537EP chips. I also have one of these modems in my PC and it works.

FYI for those not in the know with a .deb file you just right click and select install and that all the work you have to do it install these modem drivers. Also is you search the forums and Ubuntu wiki pages you will find these drivers for your version of Ubuntu I've used then on 6.04, 7.04, 7.10 and now 8.04

---

### Post by Raval on 2008-05-19
> **LaRoza said:**
> I have a computer with similiar specs. I added RAM though to max it out at 256 MB. I have the extra 64 MB DIMM, but I doubt you want that...

I use Debian on it, but I had Wolfix on it. Wolfix is easier to use I think and has many more GUI tools. See my blog (I put Debian back on with a few essential applications)

64MB wouldn't make much sense, I need one or two 128mb sticks, I see you realized that already.

I've got Xubuntu 7.10 loaded but it freezes a lot.

---

### Post by DoctorMO on 2008-05-19
> The modems do not require any license for full speed.

I've never known any driver software to get away with proprietary natures other than nvidia and ati. The kernel guys get upset with this sort of thing.

---

### Post by Raval on 2008-05-19
> **DoctorMO said:**
> I've never known any driver software to get away with proprietary natures other than nvidia and ati. The kernel guys get upset with this sort of thing.

With out those drivers I would have no internet under Ubuntu which in turn means I would have any need for Ubuntu.

While I think the nature of open source software it a great one, I am for paid software since I see nothing wrong with someone charging a price for their idea. It is up to an individual to decide if they are willing to pay for it or not.  

I support Ubuntu & Linux (in general) because I support having an alternative to OS to Windows. Also being from a third world country Ubuntu allows poor people to legally use an OS for zero cost.

Free speech not free beer.

---

### Post by LaRoza on 2008-05-19
> **Raval said:**
> 64MB wouldn't make much sense, I need one or two 128mb sticks, I see you realized that already.

I've got Xubuntu 7.10 loaded but it freezes a lot.

You can try Debian. It will be mostly familiar to Ubuntu users.

---

