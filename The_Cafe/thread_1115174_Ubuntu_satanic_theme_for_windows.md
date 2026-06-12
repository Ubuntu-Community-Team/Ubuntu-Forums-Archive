---
title: "Ubuntu satanic theme for windows?"
date: 2009-04-03
forum: The Cafe
---

### Post by blithen on 2009-04-03
Does it exist? Or at least something similar. I'm unfortunately stuck on windows at the moment, because linux doesn't seem to enjoy playing nicely with my wireless.

---

### Post by billgoldberg on 2009-04-03
> **blithen said:**
> Does it exist? Or at least something similar. I'm unfortunately stuck on windows at the moment, because linux doesn't seem to enjoy playing nicely with my wireless.

There are lots of theming possibilities for Windows.

There is Windows Blinds, there are alternative shells, ...

---

### Post by CraigPaleo on 2009-04-03
> **blithen said:**
>  linux doesn't seem to enjoy playing nicely with my wireless.

Have you tried many different distros? There may be one that supports it out of the box. Otherwise, I'd do a search for your wireless card and see if there are any fixes for it in the forums or wiki. I assume you've tried a satanic ritual already? :p

---

### Post by liamnixon on 2009-04-03
If your wireless doesn't work OTB in Ubuntu, try Fedora or Mandriva.  I have an Atheros 5007 which isn't supported natively in Ubuntu.

---

### Post by Sealbhach on 2009-04-03
Also try using wicd rather than network manager. What kind of wireless connection do you have?


.

---

### Post by pissedoffdude on 2009-04-03
Hmm, why not try getting the wireless card to work one more time?
Try this:

```
wget -c http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3942-20090205.tar.gz 
tar xvf madwifi-hal-0.10.5.6-r3942-20090205.tar.gz 
cd madwifi-hal-0.10.5.6-r3942-20090205
sudo apt-get update && sudo aptitude install build-essential
sudo make install
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta
```

Then reboot and you should have wireless internet.
Just be sure you're connected with an ethernet cable or something

---

### Post by SunnyRabbiera on 2009-04-03
I thought the default XP theme was evil enough myself :D

---

### Post by flashgig on 2009-04-03
> **billgoldberg said:**
> There are lots of theming possibilities for Windows.

There is Windows Blinds, there are alternative shells, ...

Yeah, I use Windows blinds and find it great. I have a few zipped themes if you need them let me know :)

---

### Post by albinootje on 2009-04-03
> **blithen said:**
> linux doesn't seem to enjoy playing nicely with my wireless.
What card is it ? 
Please post the "lspci" and "lsusb" output.

(Or.. try with Linux Mint or SimplyMepis)

---

### Post by billgoldberg on 2009-04-03
> **albinootje said:**
> What card is it ? 
Please post the "lspci" and "lsusb" output.

(Or.. try with Linux Mint or SimplyMepis)

Or just load the Windows driver with Ndiswrapper.

---

### Post by tjwoosta on 2009-04-03
> **blithen said:**
> Does it exist? Or at least something similar. I'm unfortunately stuck on windows at the moment, because linux doesn't seem to enjoy playing nicely with my wireless.

windows xp or vista?

---

### Post by blithen on 2009-04-04
> **SunnyRabbiera said:**
> I thought the default XP theme was evil enough myself :D

Haha! Like I said I don't want to be on Windows.

---

### Post by blithen on 2009-04-04
> **tjwoosta said:**
> windows xp or vista?

Vista, I tried to get XP working, but that was a no go.

---

### Post by blithen on 2009-04-04
I'm...I'm in shock. o_o I'm wirelessly on the forums right now on my laptop...I need to post in the community cafe more often. >_>;

---

### Post by blithen on 2009-04-04
Hey... little problem actually
when I put in this command
```
sudo modprobe wlan_scan_sta
```
I get this error.
```
blithen@blithen-laptop:~$ sudo modprobe wlan_scan_sta
[sudo] password for blithen: 
FATAL: Error inserting wlan_scan_sta (/lib/modules/2.6.27-7-generic/net/wlan_scan_sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

---

