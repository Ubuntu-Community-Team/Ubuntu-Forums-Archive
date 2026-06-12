---
title: "ltsp server with X-fi sound"
date: 2008-08-07
forum: Server Platforms
---

### Post by sgk_ on 2008-08-07
Hi guys
I have installed new dell poweredge r200 & Creative X-Fi PCI-Express sound card with Ubuntu Hardy Heron and now with Ubuntu Gutsy GIbbon server edtion for use like ltsp server, so the major problem that i have is with the sound card.I've put pci-express sound card coz there was no other choise

lspci -vn says:

02:00.0 Audio device [0403]: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG [1102:0009]
        Subsystem: Creative Labs Unknown device [1102:0018]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 15
        Region 0: Memory at dfafc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [dc] Power Management version 3
                Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

aplay -l says: 

aplay: device_list:204: no soundcards found...

alsamixer: function snd_ctl_open failed for default: Connection refused

I've tried to install XFiDrv_Linux_US-1.18 drivers, but when i run the installer script it says:

Setup is unable to detect a supported product on your system
Setup will now exit

No idea what to do, if there's someone that want or can help me, i'll be very gratefull!

Greetings

---

### Post by cariboo on 2008-08-07
WHy do you need a sound card on a server? If you can answer that question may be we can help you. Creative products are not the most well supported sounds cards around.

You might want to have a look here:

[http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

Note: these instructions are for hardy.

Jim

---

### Post by sgk_ on 2008-08-08
Hi Jim thanks for your reply
I've put sound card on the dell poweredge r200 server because the server itself doesn't have sound chipset on the motherboard, and i was stuck with problem when I try to make a call via skype and choose pulseaudio as a default server the cpu goes to 90-100% usage, and the server was freezing
So i don't have other choice except to put some sound card and to see if the situation will be better, but it's not :(

The server was bought in here, for upgrade of existing ltsp clients and the old server with debian sarge and xdcmp, created years ago. The company is growing up, so they need better solution.

anyways i have tried to install oss insted of alsa, and it doesn't help
only pulseaudio helps a bit, but there's a problem with skype, and here the company uses skype a lot, for phone call's etc...

when i start pulseaudio from command line it says: (logged as a user)

E: x11wrap.c: XOpenDisplay() failed
E: module.c: Failed to load  module "module-x11-publish" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: failed to initialize daemon.

when i try to comment this modules in /etc/pulseaudio/default.pa then pulse doesn't shows any errors on start, but skype is crashing on every start

Thx a lot for help and suggestions

---

