---
title: "Left 4 Dead: Video problems"
date: 2009-02-23
forum: Wine
---

### Post by jalmcbj on 2009-02-23
I have recently installed Left 4 Dead on my computer and I've been having problems running the game. I've looked around and some of the solutions I found in some of the threads here have helped, but I still have a problem.

Every time I run the game (I'm currently running it windowed so I can try and work out the bugs easily) I can clearly hear the audio of the intro video and the main title screen, but the window is completely black and whenever I click nothing happens, though my keyboard appears to work (I was able to skip the video by pressing ESC). I'm wondering if this is a problem with some software on my computer or if I have to shell out some cash for a new video card or something. Can anyone help me out?

---

### Post by Bios Element on 2009-02-23
Left 4 Dead works horribly under WINE. It works, But slow. Sorry for the bad news. >.>

---

### Post by karth on 2009-02-23
That is not true, for I can play that game without glitch and at a fairly good speed (~40fps during a heavy zombie load), and I read other reports of it running well.
[http://ubuntuforums.org/showthread.php?t=991003](http://ubuntuforums.org/showthread.php?t=991003)

Maybe that problem is related to a specific setup.

What is the make of the video controller? I use Nvidia.

---

### Post by jalmcbj on 2009-02-23
I used lspci and it says Intel everywhere, so I'm assuming that's it.

Not sure which part would be important, but here's the output I got if it means anything.

```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
01:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
01:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)
```

---

