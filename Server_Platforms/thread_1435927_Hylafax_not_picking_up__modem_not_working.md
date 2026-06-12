---
title: "Hylafax not picking up / modem not working"
date: 2010-03-22
forum: Server Platforms
---

### Post by Bob Bobbio on 2010-03-22
Hello, I just installed a new pci modem on my ubuntu 8.04 server.  I got it after consulting xmodem.org so that it would hopefully work with ubuntu.  It shows up under lspci as

```

05:02.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01) (prog-if 02 [16550])
	Subsystem: 3Com Corp, Modem Division USR 56k Internal FAX Modem (Model 2977)
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at d8f8 [size=8]
	Capabilities: <access denied>

```

I've installed hylafax-server, with the idea of it being a fax server.  I have it set to pick up after 1 ring, but it doesn't pick up at all.  I have no idea how to test if the modem is working with ubuntu.
I assumed that the modem is on /dev/ttyS0, I think this because cat /dev/ttyS0 doesn't instantly fail, but hangs.  Please help me, thank you.

update: I got it working, turns out it was /dev/ttyS1, thank you anyway

---

