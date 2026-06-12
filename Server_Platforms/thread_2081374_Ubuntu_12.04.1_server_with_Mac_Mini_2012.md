---
title: "Ubuntu 12.04.1 server with Mac Mini 2012"
date: 2012-11-06
forum: Server Platforms
---

### Post by JoeGoldman on 2012-11-06
Hi Forum,

 I recently purchased a couple of the new 2012 Mac Mini's released a few months back. I'm having some issues getting them to work, however.

 In comparison, I have a 2009/10 (can't remember) Mac Mini sitting here, that 12.04.1 installed perfect. I am using the exact same installation media (USB stick).

 The first issue I run into, is that I must have noacpi option selected, to even get to the language selection after selecing 'Install Ubuntu Server'. With nothing selected, I get a blank screen. With others selected, I get mixed result of getting to the next screen but no (USB) keyboard support, or blank screen once more.

 The second issue I face is, that in the installation, Ubuntu can't detect the network interface (in this case a Broadcom BCM5701, which is a different chipset to the older Mac Mini I have). I complete the installation however, and can boot into Ubuntu, but can't seem to add support for that chipset to Ubuntu at all.


 I attempted the same with Ubuntu Server 12.10, It eliminated the first issue described in the install process, but still doesn't pick up the interface in install. I didn't bother completing the install after that. Ultimately, I would prefer 12.04.1 for it being LTS.


Any help provided is appreciated :).

Regards,
Joe

---

### Post by bloudraak on 2013-01-17
Hi Joe,

I had the same problems.  The noacpi is required. As for the driver, I created a custom ISO which installed the drivers which I [documented]("http://wernerstrydom.com/journal/2013/01/13/installing-ubuntu-server-12-04-on-a-mac-mini-late-2012/").

You'll have to repeat the the following steps once installation is done:

```
dkms install -m tg3 -v 3.124c
modprobe tg3
```

After that, nothing else is required.  It works pretty well.

Thanks,
Werner

---

### Post by monkeypet on 2013-02-20
I can't seem to get the xorg server to run in the right mode.  It starts up, but the color is all dithered or looks like 256 color mode (8bpp?).  I can't seem to figure it out. I am using HDMI out and I am assuming that this mac mini has the Intel HD 4000 series graphics card.

Anone have any hints?

---

