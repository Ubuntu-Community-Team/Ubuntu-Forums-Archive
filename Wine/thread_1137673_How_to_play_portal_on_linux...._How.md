---
title: "How to play portal on linux.... How???"
date: 2009-04-25
forum: Wine
---

### Post by dragos240 on 2009-04-25
Ohai.

I used to play portal on my vista, and I was wondering, can I install it again in wine? I did that, but when I play it, my monitor doesn't recognize the screen resolution, and when I put it in window mode, it crawls slower than.... the slowest thing on earth, it moved one frame in 2 minutes. I saw someone using playonlinux to play portal, except it was in french. It seems possible, and since linux doesn't take up as much memory space as windows, it should play faster. Any seggestions? I miss killing GLaDOS.

---

### Post by Mehall on 2009-04-25
define "my monitor doesn;t recognise the screen resolution"

Do you mean it, by default, goes to something like 800x600? becuase mine does that, so I just changed it from Portal's menu.

The Orange Box works perfect in WINE, Portal especially.

---

### Post by dragos240 on 2009-04-25
My monitor displays an error saying "cannot detect display" or something, and then goes on standby. How do you set the screen resolution?

---

### Post by Mehall on 2009-04-25
> **dragos240 said:**
> My monitor displays an error saying "cannot detect display" or something, and then goes on standby. How do you set the screen resolution?

Oh, weeeiirrrdd..... never had that...

I was meaning set the res inside the app, but I was just thinking it was going with a wrong res, not... not working. Any helpers?

---

### Post by dragos240 on 2009-04-25
Argh!!!!!! I figured it out, unfortunately it took about 6 or 7 minutes to wait for the game to exit, 6 minutes of torture!!! DAH!!!! How do I make it stop lagging???

---

### Post by zmjjmz on 2009-04-25
> **dragos240 said:**
> Argh!!!!!! I figured it out, unfortunately it took about 6 or 7 minutes to wait for the game to exit, 6 minutes of torture!!! DAH!!!! How do I make it stop lagging???

Get a better graphics card (or set it to dx8.1)

---

### Post by dragos240 on 2009-04-25
[FALSE]I have one of the best graphics cards out there [/FALSE] :o and I only got this computer 2 years ago, and 2 gb of ram. It must be something else....

---

### Post by Mehall on 2009-04-25
> **dragos240 said:**
> [FALSE]I have one of the best graphics cards out there [/FALSE] :o and I only got this computer 2 years ago, and 2 gb of ram. It must be something else....

What gfx card? just so I know.

EDIT: And if you only care about gameplay, not looks, then setting it to dx8/1 is actually good for a fair fps boost

---

### Post by dragos240 on 2009-04-25
> **Mehall said:**
> What gfx card? just so I know.

EDIT: And if you only care about gameplay, not looks, then setting it to dx8/1 is actually good for a fair fps boost

UHHH...... Will the output of LSPCI work?

```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 
(rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra
nsport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address 
Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Con
troller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscella
neous Control
01:05.0 Network controller: RaLink RT2561/RT61 802.11g PCI
01:06.0 Communication controller: Conexant Systems, Inc. Device 2f40
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Et
hernet Controller (rev 14)
```

I'm terrible at finding this stuff XD.

---

### Post by Mehall on 2009-04-25
Geforce 6150SE.... You *can* play that under Linux, but you'll need tweaks, which I'm not the best at doing. I advise going onto the Steam Forums and asking out (try the Team Fortress 2 section as well as Portal, it's more active, and it's all Source Engine)

---

### Post by dragos240 on 2009-04-25
Oh :( I thought it was a good one :( oh well. Another lie from me ;)

---

### Post by Mehall on 2009-04-25
> **dragos240 said:**
> Oh :( I thought it was a good one :( oh well. Another lie from me ;)

If I'm honest, the Source Engine updates have made stuff a bit bloated. Combine this with the need for nVidia Proprietary drivers that, even in 180.xx form  aren't quite as good as the Windows ones, means that a good fps in Windows when you nought the laptop != good fps in Linux via Wine now.

---

### Post by lovinglinux on 2009-04-25
It was playing perfectly on Hardy. I didn't downloaded it after the upgrade to Jaunty.

Setting the launcher options in the game preferences through Steam interface helps a lot. I use *-dxlevel 81 -w 1024 -h 768* ad it plays perfectly (P4 3.06 Mhz, nVidia 7300GT and 2Gb DDR2).

---

### Post by dragos240 on 2009-04-26
> **lovinglinux said:**
> It was playing perfectly on Hardy. I didn't downloaded it after the upgrade to Jaunty.

Setting the launcher options in the game preferences through Steam interface helps a lot. I use *-dxlevel 81 -w 1024 -h 768* ad it plays perfectly (P4 3.06 Mhz, nVidia 7300GT and 2Gb DDR2).

Yay!! That works great now!!! ^_^

---

### Post by lovinglinux on 2009-04-26
> **dragos240 said:**
> Yay!! That works great now!!! ^_^

Good for you. Cake anyone? :popcorn:

---

### Post by dragos240 on 2009-04-26
No thank you, the blue turret reviled that there are..... some not so appealing ingredients inside that cake.

---

