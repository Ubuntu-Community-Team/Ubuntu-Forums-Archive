---
title: "[starling, karmic, upgrade] wireless fails on star1 after jaunty -&gt; karmic"
date: 2010-01-21
forum: System76 Support
---

### Post by tlroche on 2010-01-21
I have a nearly-new Starling with minimal customization. (It came with a DVD, and I switched my desktop from UNR mode to "Classic Ubuntu"--that's about it.) I just upgraded from jaunty to karmic using Update Manager per the [wiki directions]("http://knowledge76.com/index.php/KarmicUpgrade"). I was able to login as me, and see System76 driver version=2.4.4 per System>Administration>System76 Driver>About. However in jaunty I had wireless networking and now I do not. With ethernet cable attached (which I'm using now),

[LIST]
[*]I can nslookup (and browse the web, etc)
[*]Network Manager is barely visible in the panel. When I click on it, the menu items are ```

Wired Network [in bold]
  device not managed [greyed out]
--------------------
  VPN Connections  >
```[/LIST]
But without CAT5 attached
[LIST]
[*]I get same Network Manager appearance and behavior
[*]nslookup fails
[/LIST]

What's the fix?

---

### Post by tlroche on 2010-01-21
> **tlroche said:**
> Network Manager is barely visible in the panel.

The NM UI problem appears to be desktop-related. While in jaunty, I had used desktop-switcher, and was running from "Classic Ubuntu" mode when I ran Update Manager. In karmic, I retain the Classic desktop though desktop-switcher and the associated UI elements seem to have disappeared. In karmic Classic the NM panel icon appears greyed-out and is difficult to resolve. However when my girlfriend logs in, she gets the UNR desktop, and sees NM in the panel in all its glory ... except for a big red X, even though the box is on the wire, which is working. Furthermore, clicking on the NM panel icon gives the same behavior in UNR as in Classic:

> **tlroche said:**
> When I click on it, the menu items are ```

Wired Network [in bold]
  device not managed [greyed out]
--------------------
  VPN Connections  >
```[/LIST]


Unfortunately the lack of wireless networking is not desktop-related.

---

### Post by thomasaaron on 2010-01-21
First, run all System updates. Then reboot.

Second, download and install the 2.4.4 version of the driver from...
[http://planet76.com/repositories](http://planet76.com/repositories)
...It will be the second link from the bottom.

Third, go the the System76 Driver and click the Restore tab and the Restore button. Then reboot your computer.

EDIT: That's interesting. 9.10 doesn't have the classic desktop mode anymore. They did away with it. So, it must have retained it from your 9.04 install. Clever.

---

### Post by tlroche on 2010-01-22
> **thomasaaron said:**
> First, run all System updates.

Done.

> **thomasaaron said:**
> Then reboot.

Done.

> **thomasaaron said:**
> Second, download and install the 2.4.4 version of the driver from... [http://planet76.com/repositories](http://planet76.com/repositories) 

Done:```

URI="http://planet76.com/repositories/system76-driver-2.4.4.deb"
FN="$(basename ${URI})"
FP="/tmp/${FN}"
wget -O ${FP} ${URI}
sudo dpkg -i ${FP}

```

> **thomasaaron said:**
> Third, go the the System76 Driver and click the Restore tab and the Restore button.

Attempted. I tried running Restore last night ~6pm, logged in as me (the user with Classic Ubuntu). Restore was still running (i.e. the dialog=Restoring was up, with "Factory settings are being restored") when I got up this morning, so I killed it, restarted, logged in as my girlfriend (who has UNR mode), and reran Restore. It was still running when I got home this evening, so I killed it.

Is there something else I need to do to make Restore work?

Just now I burned a UNR 9.10 CD and was able to boot that using the USB DVD drive. Interestingly, the wireless works when I boot that.

---

### Post by tlroche on 2010-01-23
> **tlroche said:**
> Just now I burned a UNR 9.10 CD and was able to boot that using the USB DVD drive. Interestingly, the wireless works when I boot that.

So I just installed from that:

[LIST]
[*]backed up /home
[*]installed from CD, using "Erase and use the entire disk": restarted with wireless working!
[*]installed System76 driver: downloaded, then System>Administration>System76 Driver>Install Drivers>Install
[*]restarted: showed "no network connection", and Network Manager showed no available connections, until I fiddled with the hardware WiFi/3G switch and restarted, then wireless was happy again.
[*]recreated users
[/LIST]

I'll restore /home as soon as I can get GF off the box. Meanwhile, karmic seems to be working.

---

