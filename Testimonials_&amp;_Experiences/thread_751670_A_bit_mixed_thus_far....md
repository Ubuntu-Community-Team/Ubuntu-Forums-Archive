---
title: "A bit mixed thus far..."
date: 2008-04-10
forum: Testimonials &amp; Experiences
---

### Post by iainv on 2008-04-10
I recently got a new laptop, so decided to give Ubuntu a try on my desktop as I no longer required it day to day.

I decided to go for a clean install, rather than partiitioning, on the basis that if Windows existed as an alternative i'd probably never use Ubuntu.

Install was pretty easy, although I had to search the fora from my other PC a bit to get ndiswrapper to work properly.

My accounting software wouldn't work with WINE, and my scanner isn't supported at all, so I then turned to VirtualBox, which is superb, and although USB support was tricky I finally got my scanner working.

The main problem has been my printer. It's a standard HP laserjet 2500, supposed to work very well, and indeed detected first time. Then it stopped working. Then It came up as "unknown". Then it stopped again. I install hplip and cups and unistalled them and spent weeks pratting about, and I now have no idea why, but if I turn the printer on after the computer's on, it comes up as "unknown" and works.

But if I try and get VirtualBox to recognise it it hangs the whole system!

I also now have a problem with my WiFi dropping out for no apparent reason, and requiring a reboot.

So, on the whole:

Generally good - OpenOffice, VirtualBox, GIMP etc. are amazing applications, and the Compiz Fusion cube makes sitting at the machine working much better - can just flick from surface to surface to change tasks, without having to worry about the silly taskbar getting too full. And it's SO MUCH quicker than it was running XP.

On the downside - some flaky hardware issues with no obvious cause, and no apparent solutions!

In summary? Now i'm running the desktop on just Ubuntu, i'm waiting for Hardy to arrive - if all goes well i'll be losing Vista from my laptop (albeit retaining an XP virtualbox)!

Iain

---

### Post by armandh on 2008-04-10
which ubuntu are you running?

---

### Post by iainv on 2008-04-11
7.10 32-bit (Tried 64-bit but couldn't get ndiswrapper to run my wifi).

Looking forward to Hardy.

---

### Post by mrsudo on 2008-04-13
hopefully hardy will have better support for everything you need.

---

### Post by hyper_ch on 2008-04-14
strange, I thought HP printer support would be excellent (hplibs...)

---

### Post by armandh on 2008-04-14
yes but not every HP printer

---

### Post by ukripper on 2008-04-14
I think Brother printers are also worthwhile taking a look as they supply linux CUPS drivers on their website( I have Brother 130C works great through SMB network or directly connected to USB). 

HP support is suppose to be more than any other though for supplying linux print drivers.

---

### Post by ukripper on 2008-04-14
> **iainv said:**
> 

I also now have a problem with my WiFi dropping out for no apparent reason, and requiring a reboot.


Iain

Are you using Intel 3945 ABG for wifi? Because it has that problem of dropping off. You may want to look into the follwoing solution for that as I had this problem but got sorted by this workaround:

Wireless has some issues here. Gutsy by default uses the ipw3945 driver. This driver is actually depreciated by intel and is replaced by the iwl3945 (hardy's default). There're some issues with the ipw3945 driver a driver crash when transfering big files and suddenly disconnections. The solution is to replace (in Gutsy) the ipw3945 for the iwl3945.

However there're still some issues with the iwl3945 driver.

1. Replace the ipw345 with the iwl3945 driver.

sudo echo blacklist ipw3945 >> /etc/modprobe.d/blacklist-ipw3945
sudo echo iwl3945 >> /etc/modules

2. Solve the iwl3945 issues

Suspend issue (caused by an incomplete rename of the interface):

sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.rules.bak

Hibernate issue

sudo gedit /etc/default/acpi-support

Add iwl3945 to MODULES line.

# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="iwl3945"

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""


After this changes reboot your system. Take into account that the Wireless connectivity after suspend or hibernate would take a few moments to start over again.

I haven't confirmed yet the throughput issue nor found a workaround for it.

Also another annoyance is that the iwl3945 driver doesn't light up the wifi led with the gutsy version. 

taken from - [https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700](https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700)

---

### Post by stchman on 2008-04-14
> **iainv said:**
> I recently got a new laptop, so decided to give Ubuntu a try on my desktop as I no longer required it day to day.

I decided to go for a clean install, rather than partiitioning, on the basis that if Windows existed as an alternative i'd probably never use Ubuntu.

Install was pretty easy, although I had to search the fora from my other PC a bit to get ndiswrapper to work properly.

My accounting software wouldn't work with WINE, and my scanner isn't supported at all, so I then turned to VirtualBox, which is superb, and although USB support was tricky I finally got my scanner working.

The main problem has been my printer. It's a standard HP laserjet 2500, supposed to work very well, and indeed detected first time. Then it stopped working. Then It came up as "unknown". Then it stopped again. I install hplip and cups and unistalled them and spent weeks pratting about, and I now have no idea why, but if I turn the printer on after the computer's on, it comes up as "unknown" and works.

But if I try and get VirtualBox to recognise it it hangs the whole system!

I also now have a problem with my WiFi dropping out for no apparent reason, and requiring a reboot.

So, on the whole:

Generally good - OpenOffice, VirtualBox, GIMP etc. are amazing applications, and the Compiz Fusion cube makes sitting at the machine working much better - can just flick from surface to surface to change tasks, without having to worry about the silly taskbar getting too full. And it's SO MUCH quicker than it was running XP.

On the downside - some flaky hardware issues with no obvious cause, and no apparent solutions!

In summary? Now i'm running the desktop on just Ubuntu, i'm waiting for Hardy to arrive - if all goes well i'll be losing Vista from my laptop (albeit retaining an XP virtualbox)!

Iain

The Color Laserjet 2500 is a Postscript printer and Postscript printers work perfectly OOB with Ubuntu.

[http://openprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_2500](http://openprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_2500)

What wireless card do you have?  Is it a Broadcom?  Broadcom supports sucks for Linux.  Try Intel or Atheros.

I have an Atheros 5006EG on my laptop and it runs perfectly using the restricted driver.

---

### Post by iainv on 2008-04-14
> **stchman said:**
> The Color Laserjet 2500 is a Postscript printer and Postscript printers work perfectly OOB with Ubuntu.

No, they don't. 

They may be supposed to, but they don't.

I've got it printing now, though, as you'll see in the original post, but it's not perfect.

FWIW, my WIFI is a USB philips SN6500, which works perfectly (including lighting up) with ndiswrapper but then drops out, after a random time, for no obvious reason (yet it remains lit).

If you search the fora for drop out wifi you'll find i'm far from the only one with this issue, and it's not card specific.

Hopefully Hardy will help, but I have to confess i'm a bit nervous about upgrading to it when i've only just got everything working.

Iain

---

