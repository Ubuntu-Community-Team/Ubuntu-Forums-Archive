---
title: "Trying to get wireless card up: Dell Draft 1500"
date: 2006-09-23
forum: Ubuntu Customization Guide
---

### Post by EmmDoubleEw on 2006-09-23
I'm trying to get my wireless card working, here are the steps I have taken:


My card is supported under ndiswrapper:
Card: Dell Wireless 1500 (802.11draft-n/a/g) WLAN MiniCard 
Chipset: Broadcom BCM4321(?) (rev 01) 
pciid: 14e4:4328 
Driver: [http://ftp.us.dell.com/network/R129083.EXE](http://ftp.us.dell.com/network/R129083.EXE) 
Other: ndiswrapper v1.22-rc1, Ubuntu kernel 2.6.15-26-386

My ndiswrapper version is:

```
martin@martin-laptop:~$ ndiswrapper -v
utils version: 1.7
driver version:        1.8

```

I tried following this tutorial:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-d270600ddc317f671085f088b8eb4b1604d51a91](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-d270600ddc317f671085f088b8eb4b1604d51a91)

But my card doesn't show up under lshw, so none of the tutorial makes sense. For example, it tells me to "add information that should look like this:
> IconExample48.png 
card ""Atheros Communications, Inc.", "AR5001-0000-0000", "Wireless LAN"
  manfid 0x0271, 0x0012
  function: 6 (network)
  bind "ath_pci"
  

What?? Do they expect me to know off the top of my head what manfid, function, whatever whatever is for my card? I'm utterly confused.

I tried installing the .inf file with ndiswrapper, and it shows up in the driverlist:
> martin@martin-laptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present


But that has made absolutely no difference: I still can't connect without a cable and it still doesn't show up under "Network Settings."

Help would be greatly appreciated.

---

### Post by EmmDoubleEw on 2006-09-23
What the hell? When I pressed "New Thread" i was in the beginner section. Can a mod delete this thread please?

---

