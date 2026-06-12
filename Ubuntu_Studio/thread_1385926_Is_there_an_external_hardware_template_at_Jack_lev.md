---
title: "Is there an external hardware template at Jack level?"
date: 2010-01-20
forum: Ubuntu Studio
---

### Post by mango42 on 2010-01-20
Apologies if I don't describe this too well as I am somewhat brain-weary from getting everything DAW working in Linux just now...

I was rather surprised to find that 'connections' in Jack don't seem to be persistent; then I got to thinking 'do I have to do this every time I start Jack or any prog running under Jack'?

So, what I am searching for is an app that works at the Jack level, a sort of template of my studio equipment that loads with Jack and is readable by all the apps I run (Ardour, Qtractor, Muse, Hydrogen etc).

I wouldn't say my studio is huge but there is a lot of outboard gear (synths, modules, FX etc) and I do have a fully loaded 8x8 MIDI interface (ESI M8 something), the connections to which remain fairly static, so it would aid the creative process no end if Linux kept a template of what is connected to what, that loaded on boot up.

Unless I am missing something fundamental, ISTM unnecessary faffing about to make 16 individual MIDI connections to ALSA Thru everytime Jack is started; then 16 individual connections in Muse or whatever because these programs don't seem to read Jack's 'Connect' dialogue by default. (Perhaps Patchage is supposed to do this job but it never runs for me, just folds when started up).

On the audio side I have come to a halt because this Thinkpad T43 doesn't want to recognise the Expresscard Firewire interface (Lindy 51500 - Texas Instruments) that I was planning to plug a Focusrite Saffire 40 into, so just at present I don't have to think about how to run the Focusrite software mixer applet or Jack's patchbay. Hey ho.

Onwards and upwards and praying there's a way through this dilemma.

Thanks for reading this ramble...I hope someone can make sense of it 8-[

---

### Post by dawiba on 2010-01-20
While the modular system that Linux uses for audio has advantages, this is probably the main disadvantage.

I don't use it myself, but I think there's something called LASH which basically does what you're looking for.

---

### Post by mango42 on 2010-01-20
Thanks for the tip, dawiba; I'll go check it out.

---

### Post by AutoStatic on 2010-01-20
There's LASH indeed, and patchage, and the QjackCtl patchbay that allows you to store connections. And there's also the possibility to script it all: [http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/](http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/)

And concerning the Thinkpad, could you post the output of **lspci**? And is the ExpressCard not working at all or is it being recognised?

---

### Post by mango42 on 2010-01-21
Hi AutoStatic - you are such a helpful poster!

I didn't see anyway that Jack could store setups - next time I have a working audio partition (doing an upgrade to 9.10 last night has totally porked the entire system - no longer even loads ALSA and none of the Applications menus work anymore; hey ho!) I'll take a closer look at the options in QJactCtl.

Yes, the issue with the firewire card was not expected. This T43 is a recent 2nd-hand purchase (whilst my AMD Turion machine is away having its screen fixed) - perhaps the previous owner tried too much hot plugging in the PCMCIA slots - dunno, but as you've so kindly enquired, here's lspci with the Expresscard plugged in:-

> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
04:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
04:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)


I'll reboot then post syslog as well - there's an odd couple of error lines I haven't resolved yet... I still suspect hardware damage, as the firewire i/f is not recognised on Windoze either but is recognised on a friends HP laptop - so the card is okay...

---

### Post by mango42 on 2010-01-21
The relevant part of syslog:-

> getubuntu-savetheworld kernel: [   10.018584] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.018588] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.124995] yenta_cardbus 0000:04:00.0: ISA IRQ mask 0x0c30, PCI irq 18
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.125001] yenta_cardbus 0000:04:00.0: Socket status: 30000006
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.125005] pci_bus 0000:05: Upper limit for fixing this bridge's parent bridge: #04
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.125010] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x7fff
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.125014] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x7fff: clean.
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.125926] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge Memory window: 0xb0300000 - 0xbfffffff
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.125930] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd7ffffff
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.125975] Uhhuh. NMI received for unknown reason b1 on CPU 0.
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.125978] You have some hardware problem, likely on the PCI bus.
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.125981] Dazed and confused, but trying to continue
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.126765] ipw2200 0000:04:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.127451] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.127492] ipw2200 0000:04:02.0: firmware: requesting ipw2200-bss.fw
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.736506] ipw2200: device failed to boot initial fw image
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.736519] ipw2200: Unable to load firmware: -62
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.736524] ipw2200: failed to register network device
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.737280] phy0: Selected rate control algorithm 'pid'
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.742434] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.742506] Intel ICH 0000:00:1e.2: setting latency timer to 64
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.745437] ipw2200 0000:04:02.0: PCI INT A disabled
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.745452] ipw2200: probe of 0000:04:02.0 failed with error -5
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.800851] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.802542] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.803250] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.803851] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Jan 21 11:36:09 getubuntu-savetheworld kernel: [   10.804629] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.

The entry that starts 'Uhhuh, Non-maskable-interrupt' only appears when I boot with the Lindy card in the slot...

---

### Post by AutoStatic on 2010-01-21
Did you try setting up the ExpressCard with [rtirq]("http://ubuntuforums.org/showthread.php?t=1328175")? You can find a lot of information here also: [http://subversion.ffado.org/wiki/IrqPriorities](http://subversion.ffado.org/wiki/IrqPriorities)

---

### Post by mango42 on 2010-01-21
Many thanks - I'll delve into it next time I have a Studio partition working ;)

---

