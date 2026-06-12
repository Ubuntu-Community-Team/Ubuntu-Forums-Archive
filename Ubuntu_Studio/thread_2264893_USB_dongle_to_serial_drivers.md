---
title: "USB dongle to serial drivers"
date: 2015-02-10
forum: Ubuntu Studio
---

### Post by bill76 on 2015-02-10
Hello all. I am considering installing Ubuntu Studio and want to know if Ubuntu Studio has the same Terminal opitions as Unity? Is there support for USB dongle to Serial? 

Thanks.

---

### Post by tgalati4 on 2015-02-12
Yes, most USB-to-serial interfaces are supported.  Plug in your device, open a terminal and look at:

```
lsusb
```

A common chip is the PL2303:

> 
tgalati4@Mint17 ~ $ modinfo pl2303
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/usb/serial/pl2303.ko
license:        GPL
description:    Prolific PL2303 USB to serial adaptor driver
srcversion:     2857FDB314310156D35D9E7
alias:          usb:v0B8Cp2303d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B63p6530d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v11ADp0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v054Cp0437d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04B8p0522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04B8p0521d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0p3524d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5372p2303d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ADp0FBAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp002Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v11F6p2001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v058Fp9720d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp0257d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0731p2003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E55p110Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0413p2101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v079Bp0027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v10B5pAC70d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v078Bp1234d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0745p0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04A5p4027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v11F5p0005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v11F5p0004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v11F5p0003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v11F5p0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04E8p8001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v11F7p02DFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v6189p2068d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0731p0528d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1453p4026d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2478p2008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0584pB000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF7p0620d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EBAp2080d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EBAp1080d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v056Ep5004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v056Ep5003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0547p2008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0557p2008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0A0Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0A03d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v067Bp0307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v067Bp331Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v067Bp0609d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v067Bp0612d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v067Bp0611d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v067BpAAA0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v067BpAAA2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v067Bp1234d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v067Bp04BBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v067Bp2303d*dc*dsc*dp*ic*isc*ip*in*
depends:        usbserial
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512
tgalati4@Mint17 ~ $ 
tgalati4@Mint17 ~ $ cd /lib/modules/3.13.0-24-generic/kernel/drivers/usb/serial/
tgalati4@Mint17 /lib/modules/3.13.0-24-generic/kernel/drivers/usb/serial $ ls
aircable.ko   cypress_m8.ko       io_edgeport.ko  keyspan.ko      mos7720.ko  oti6858.ko      sierra.ko            usbserial.ko          xsens_mt.ko
ark3116.ko    digi_acceleport.ko  io_ti.ko        keyspan_pda.ko  mos7840.ko  pl2303.ko       spcp8x5.ko           usb-serial-simple.ko  zte_ev.ko
belkin_sa.ko  empeg.ko            ipaq.ko         kl5kusb105.ko   navman.ko   qcaux.ko        ssu100.ko            usb_wwan.ko
ch341.ko      f81232.ko           ipw.ko          kobil_sct.ko    omninet.ko  qcserial.ko     symbolserial.ko      visor.ko
cp210x.ko     ftdi_sio.ko         ir-usb.ko       mct_u232.ko     opticon.ko  quatech2.ko     ti_usb_3410_5052.ko  whiteheat.ko


I count 42 different USB-to-serial devices.  The Desktop Environment is independent of the modules that come with the linux kernel.

---

