---
title: "Need help with tshark and iwpriv ~~"
date: 2010-03-13
forum: Security
---

### Post by xideadfishix on 2010-03-13
I'm running Intel 5100 AGN and i have 2 issues here, i searched forums and googled for this issues for days now and nothing helpful came out. 

Issue 1: i tried running the " iwpriv wlan0 mode 3 " command and it doesnt seems to work. is there a patch or something that i could use to patch up my current wifi driver?

Issue 2: I need to obtain the MACtime header and it seems to work with those wifi card running on atheros chipsets but since im running an Intel chipset, im not sure if it works. im using tshark with the command " tshark -c 30000 -i wlan0 -z proto,colinfo,prism.mactime.data,prism.mactime.data > out.txt " and i receive an error stating it is not supported. is there another way or in other header where the mactime.data could be obtained?

---

### Post by MarkC502 on 2010-03-13
You can replace the standard Ubuntu Wifi drivers with the ones from wireless-compat for linux site, just google "linux wireless" and they will be on top. Go there and you can get the latest tarball and then you will need to manually install to your system thereby replacing your stock factory wifi driver module with a new one. This is not as complicated as it would seem and they provide pretty decent install instructions for their drivers.

The drivers they provide are already patched for monitor mode as well as packet injection and will probably only require the fragmentation patch if you need it. In general though I would start by determining what wifi chipset you are using. To figure that out you can use the following command

lspci -v

that will list all PCI based devices which your built in wifi will be one. Look for things that say "Ethernet" as you should only have 2 of those 1 will be your wired network adapter and the other will be your wifi adapter. Once you figure out what your wifi chipset is then you can look up the specifics for your driver on the net ( Aircrack or Linux Wireless sites have good info )

You can also download and install the newer version of IW if you want, since the linux wireless people provide that as well.


Good luck,

Mark

---

### Post by adam814 on 2010-03-14
I also have an Intel WiFi Link 5100 AGN.  I use the driver that ships with Ubuntu.  It does work for monitor mode, but as with all (i think) of the mac80211 drivers iwpriv is pretty much useless.

What works for me to put the card in monitor mode is to run "sudo airmon-ng start wlan0" which will create another interface (mon0) that is in monitor mode.  You'll need the aircrack-ng package installed if you don't already have it.

---

