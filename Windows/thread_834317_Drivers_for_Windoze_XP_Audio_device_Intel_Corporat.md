---
title: "Drivers for Windoze XP Audio device: Intel Corporation 82801G (ICH7 Family)"
date: 2008-06-19
forum: Windows
---

### Post by felixdzerzhinsky on 2008-06-19
I am missing drivers for Windows XP Professional. Especially the Audio Device

Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

And the 

VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])

My lspci -v

pjharper@ubuntu:~/download$ lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
        Subsystem: ASRock Incorporation Unknown device 2770
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
        Subsystem: ASRock Incorporation Unknown device 2772
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fde80000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at cc00 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fde40000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: ASRock Incorporation Unknown device 3662
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fde38000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fe000000-febfffff
        Prefetchable memory behind bridge: 00000000fa000000-00000000fcffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fdf00000-fdffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation Unknown device 27c8
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at c400 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation Unknown device 27c9
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at c480 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation Unknown device 27ca
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at c800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation Unknown device 27cb
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at c880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: ASRock Incorporation Unknown device 27cc
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at fde37c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: ASRock Incorporation Unknown device 27b8
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: ASRock Incorporation Unknown device 27df
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: ASRock Incorporation Unknown device 27c0
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at c080 [size=8]
        I/O ports at c000 [size=4]
        I/O ports at bc00 [size=8]
        I/O ports at b880 [size=4]
        I/O ports at b800 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: ASRock Incorporation Unknown device 27da
        Flags: medium devsel, IRQ 5
        I/O ports at 0400 [size=32]

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: ASRock Incorporation Unknown device 8136
        Flags: bus master, fast devsel, latency 0, IRQ 221
        I/O ports at d800 [size=256]
        Memory at fdfff000 (64-bit, non-prefetchable) [size=4K]
        Expansion ROM at fdfc0000 [disabled] [size=128K]
        Capabilities: <access denied>

---

### Post by Enfenion on 2008-06-19
Is this an integrated card in a laptop or on a motherboard?

The easiest way is to go to the manufacturer's website and look there.

---

### Post by mips on 2008-06-21
I don't know why I do this but here goes anyway.

Video Driver:
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&DwnldId=12536&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&DwnldId=12536&lang=eng)

INF Update Utility:
[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=816&OSFullName=Windows*+XP+Professional&lang=eng&strOSs=44&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=816&OSFullName=Windows*+XP+Professional&lang=eng&strOSs=44&submit=Go%21)

The above should do the trick.

The audio is hard to identify from what you gave, a mother board brand & model would be more usefull for identification, you might even have a Realtek chipset for the audio.
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldId=11691&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldId=11691&lang=eng)
[http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)



If you need any other Intel drivers for LAN etc go here:
[http://downloadcenter.intel.com/default.aspx](http://downloadcenter.intel.com/default.aspx)

---

### Post by Midwest-Linux on 2008-06-21
Belarc advisor is another source too.

 "The Belarc Advisor builds a detailed profile of your installed software and hardware, missing Microsoft hotfixes, anti-virus status, CIS (Center for Internet Security) benchmarks, and displays the results in your Web browser. All of your PC profile information is kept private on your PC and is not sent to any web server.

    * Operating Systems: Runs on Windows Vista, 2003, XP, 2000, NT 4, Me, 98, and 95."


[http://www.belarc.com/free_download.html](http://www.belarc.com/free_download.html)

---

### Post by shiv2979 on 2008-09-20
thank u!!!

---

