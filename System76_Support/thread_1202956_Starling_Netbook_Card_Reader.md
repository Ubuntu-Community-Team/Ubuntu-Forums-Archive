---
title: "Starling Netbook Card Reader"
date: 2009-07-02
forum: System76 Support
---

### Post by jlkill3r on 2009-07-02
Hello, I've recently received a Starling Netbook and have yet to have any problems with it. I've recently tried using the card reader and tried to use both, a 8gb pny optima and a 1gb fujifilm xd card and have not had any luck with either of them. I've not downloaded anything new other then a media player and a music client. The card reader don't seem to be even reading the card at all.

---

### Post by thomasaaron on 2009-07-03
Another customer has reported that it doesn't support the 8GB card.

As for the fujifilm card, did it come from a camera? If so, there are some camera formats that don't work well with Ubuntu.

Try this: open a terminal and run...

tail -f /var/log/syslog

Then, insert your SD card and post the terminal's output.

---

### Post by jlkill3r on 2009-07-05
Hello, thank you for the quick response, this is the output for the card reader and it is the fujifilm "xd" card.

Jul  5 22:53:36 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Jul  5 22:53:36 system76-netbook avahi-daemon[2628]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.5.50.12.
Jul  5 22:53:36 system76-netbook avahi-daemon[2628]: New relevant interface wlan0.IPv4 for mDNS.
Jul  5 22:53:36 system76-netbook avahi-daemon[2628]: Registering new address record for 10.5.50.12 on wlan0.IPv4.
Jul  5 22:53:37 system76-netbook NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Jul  5 22:53:37 system76-netbook NetworkManager: <info>  Policy set 'Auto LibertyWifi' (wlan0) as default for routing and DNS. 
Jul  5 22:53:37 system76-netbook NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Jul  5 22:53:37 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Jul  5 22:53:42 system76-netbook kernel: [   54.656072] wlan0: no IPv6 routers present
Jul  5 22:53:42 system76-netbook ntpdate[3243]: step time server 91.189.94.4 offset -2.555746 sec

---

### Post by thomasaaron on 2009-07-06
Did you run...

tail -f /var/log/syslog

...*before* inserting your card? If not, that is what you need to do.

If you *did* run it before inserting the card, then the reader didn't detect the card. In this case, run your System76 Driver and try again, making sure you are pushing the card in firmly.

---

### Post by jlkill3r on 2009-07-07
After reinstalling the drivers it seems to now detect the card and after doing what you said I now have:

lance@system76-netbook:~$ tail -f /var/log/syslog
Jul  7 15:13:02 system76-netbook avahi-daemon[2559]: Registering new address record for 10.5.50.254 on wlan0.IPv4.
Jul  7 15:13:02 system76-netbook dhclient: bound to 10.5.50.254 -- renewal in 1785 seconds.
Jul  7 15:13:02 system76-netbook avahi-daemon[2559]: Registering new address record for fe80::217:c4ff:fe76:a05f on wlan0.*.
Jul  7 15:13:03 system76-netbook NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Jul  7 15:13:03 system76-netbook NetworkManager: <info>  Policy set 'Auto LibertyWifi' (wlan0) as default for routing and DNS. 
Jul  7 15:13:03 system76-netbook NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Jul  7 15:13:03 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Jul  7 15:13:02 system76-netbook ntpdate[3179]: step time server 91.189.94.4 offset -2.015138 sec
Jul  7 15:13:09 system76-netbook kernel: [   57.728074] wlan0: no IPv6 routers present
Jul  7 15:17:01 system76-netbook /USR/SBIN/CRON[3330]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  7 15:18:56 system76-netbook kernel: [  405.522031] pciehp 0000:00:1c.0:pcie02: Card present on Slot(0)
Jul  7 15:18:56 system76-netbook kernel: [  405.656221] pci 0000:01:00.0: reg 10 32bit mmio: [0x000000-0x0000ff]
Jul  7 15:18:56 system76-netbook kernel: [  405.656304] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
Jul  7 15:18:56 system76-netbook kernel: [  405.656432] pci 0000:01:00.2: reg 10 32bit mmio: [0x000000-0x0000ff]
Jul  7 15:18:56 system76-netbook kernel: [  405.656618] pci 0000:01:00.3: reg 10 32bit mmio: [0x000000-0x0000ff]
Jul  7 15:18:56 system76-netbook kernel: [  405.656805] pci 0000:01:00.4: reg 10 32bit mmio: [0x000000-0x0000ff]
Jul  7 15:18:56 system76-netbook kernel: [  405.657096] pciehp: Could not get hotplug parameters
Jul  7 15:18:56 system76-netbook kernel: [  405.657241] pciehp: Could not get hotplug parameters
Jul  7 15:18:56 system76-netbook kernel: [  405.657379] pciehp: Could not get hotplug parameters
Jul  7 15:18:56 system76-netbook kernel: [  405.657518] pciehp: Could not get hotplug parameters
Jul  7 15:18:57 system76-netbook kernel: [  405.736489] sdhci: Secure Digital Host Controller Interface driver
Jul  7 15:18:57 system76-netbook kernel: [  405.736497] sdhci: Copyright(c) Pierre Ossman
Jul  7 15:18:57 system76-netbook kernel: [  405.785601] sdhci-pci 0000:01:00.0: SDHCI controller found [197b:2382] (rev 0)
Jul  7 15:18:57 system76-netbook kernel: [  405.785651] sdhci-pci 0000:01:00.0: enabling device (0000 -> 0002)
Jul  7 15:18:57 system76-netbook kernel: [  405.785681] sdhci-pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul  7 15:18:57 system76-netbook kernel: [  405.785908] sdhci-pci 0000:01:00.0: setting latency timer to 64
Jul  7 15:18:57 system76-netbook kernel: [  405.786110] mmc0: SDHCI controller on PCI [0000:01:00.0] using ADMA
Jul  7 15:18:57 system76-netbook kernel: [  405.786164] sdhci-pci 0000:01:00.2: SDHCI controller found [197b:2381] (rev 0)
Jul  7 15:18:57 system76-netbook kernel: [  405.786207] sdhci-pci 0000:01:00.2: enabling device (0000 -> 0002)
Jul  7 15:18:57 system76-netbook kernel: [  405.786236] sdhci-pci 0000:01:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul  7 15:18:57 system76-netbook kernel: [  405.786269] sdhci-pci 0000:01:00.2: Refusing to bind to secondary interface.
Jul  7 15:18:57 system76-netbook kernel: [  405.786292] sdhci-pci 0000:01:00.2: PCI INT A disabled
Jul  7 15:20:01 system76-netbook /USR/SBIN/CRON[3440]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

---

### Post by thomasaaron on 2009-07-08
Then can you read the card now?

Or, can you read a different card?

---

### Post by jlkill3r on 2009-07-08
Unfortunately I do not know anyone who has a card of their own so I'm unable to determine if another card can be read though, I'm still having difficulties with this one. I do not seem to see it under devices either and for some reason when I insert it the log does not change now, I even tried reinstalling system76 drivers again and still no change.

---

### Post by thomasaaron on 2009-07-09
If you've run the System76 driver and rebooted...

and then went to a terminal and run...

```
tail -f /var/log/syslog
```

...and *THEN* inserted the card...

and the logs that you see inside of the terminal do not update to indicate a card has been detected, then you may have a faulty card reader.

If it *does* update the log inside of the terminal, but doesn't auto-mount the card, you probably have an incompatible card.

---

### Post by ants280 on 2010-03-03
thomasaaron, I did what you asked, installed the driver, did the tail, then inserted the card.  It did not show up on "df" or "fdisk -l. I have an Olympus M 1Gb xd card.  It is about 2-3 years old. On the back it reads "MXD1GM3 L846216KNG 0744MAD JAPAN by TOSHIBA" (I think, The printing is small without very good printing).

I have a "star1" starling netbook on UNR 9.10 (which I got February 2010 - last week).

Here is my "tail -f /var/log/syslog" from the point I inserted my xd card (I renamed my computer to "NIBBLER".
```

Mar  3 09:34:17 NIBBLER kernel: [  153.936694] pciehp 0000:00:1c.0:pcie04: Card present on Slot(0)
Mar  3 09:34:17 NIBBLER kernel: [  154.057264] pci 0000:01:00.0: reg 10 32bit mmio: [0x000000-0x0000ff]
Mar  3 09:34:17 NIBBLER kernel: [  154.057345] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
Mar  3 09:34:17 NIBBLER kernel: [  154.057515] pci 0000:01:00.2: reg 10 32bit mmio: [0x000000-0x0000ff]
Mar  3 09:34:17 NIBBLER kernel: [  154.057738] pci 0000:01:00.3: reg 10 32bit mmio: [0x000000-0x0000ff]
Mar  3 09:34:17 NIBBLER kernel: [  154.057964] pci 0000:01:00.4: reg 10 32bit mmio: [0x000000-0x0000ff]
Mar  3 09:34:17 NIBBLER kernel: [  154.058164] pciehp: Could not get hotplug parameters
Mar  3 09:34:17 NIBBLER kernel: [  154.058194] pciehp: Could not get hotplug parameters
Mar  3 09:34:17 NIBBLER kernel: [  154.058221] pciehp: Could not get hotplug parameters
Mar  3 09:34:17 NIBBLER kernel: [  154.058245] pciehp: Could not get hotplug parameters
Mar  3 09:34:17 NIBBLER kernel: [  154.189290] jmb38x_ms 0000:01:00.3: enabling device (0000 -> 0002)
Mar  3 09:34:17 NIBBLER kernel: [  154.189314] jmb38x_ms 0000:01:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  3 09:34:17 NIBBLER kernel: [  154.189332] jmb38x_ms 0000:01:00.3: setting latency timer to 64
Mar  3 09:34:17 NIBBLER kernel: [  154.195656] sdhci: Secure Digital Host Controller Interface driver
Mar  3 09:34:17 NIBBLER kernel: [  154.195665] sdhci: Copyright(c) Pierre Ossman
Mar  3 09:34:17 NIBBLER kernel: [  154.241173] sdhci-pci 0000:01:00.0: SDHCI controller found [197b:2382] (rev 0)
Mar  3 09:34:17 NIBBLER kernel: [  154.241208] sdhci-pci 0000:01:00.0: enabling device (0000 -> 0002)
Mar  3 09:34:17 NIBBLER kernel: [  154.241227] sdhci-pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  3 09:34:17 NIBBLER kernel: [  154.241312] sdhci-pci 0000:01:00.0: setting latency timer to 64
Mar  3 09:34:17 NIBBLER kernel: [  154.241420] Registered led device: mmc0::
Mar  3 09:34:17 NIBBLER kernel: [  154.241522] mmc0: SDHCI controller on PCI [0000:01:00.0] using ADMA
Mar  3 09:34:17 NIBBLER kernel: [  154.241554] sdhci-pci 0000:01:00.2: SDHCI controller found [197b:2381] (rev 0)
Mar  3 09:34:17 NIBBLER kernel: [  154.241583] sdhci-pci 0000:01:00.2: enabling device (0000 -> 0002)
Mar  3 09:34:17 NIBBLER kernel: [  154.241600] sdhci-pci 0000:01:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  3 09:34:17 NIBBLER kernel: [  154.241618] sdhci-pci 0000:01:00.2: Refusing to bind to secondary interface.
Mar  3 09:34:17 NIBBLER kernel: [  154.241631] sdhci-pci 0000:01:00.2: PCI INT A disabled

```

Edit: the second time I try to insert the card, nothing happens to /var/log/syslog.  Restarting the computer resets this trait (It will show up once after the computer reboots).  This only happens when I reboot the computer, not if I logout, login, then try it again.

---

### Post by thomasaaron on 2010-03-04
Dummy me. I just noticed you were saying XD card (and I've been thinking SD card). I'm not sure if the slot supports XD cards or not (and I don't have one to test with at the moment). 

Does the card seem to seat well into the socket?

(I'll see if someone around here has one to test with.)

---

### Post by ants280 on 2010-03-04
Yes, it is a **X**d card.  I didn't buy the laptop in hopes of getting a xd card reader, but when I noticed that there was a xd logo above the slot yesterday, I pushed it in.  It fine fine, but I had to make sure I was inserting it correctly (not at an angle in any direction).  It would be really cool if a driver could be written for Linux to support xd cards or anything it that card reader (I assume there is none at the moment).

My xd card is for my Olympus stylus camera, the cool waterproof/shockproof one (I have an old 790 SW).  The pictures are decent and it works great on the beach, in the cold, or in the snow.  It also survived a long tumble I took a few years ago, sustaining only a few scratches.

---

