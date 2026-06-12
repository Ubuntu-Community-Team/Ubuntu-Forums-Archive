---
title: "Using gpsd to be an NTP stratum 1 server?"
date: 2010-02-09
forum: Server Platforms
---

### Post by nutznboltz on 2010-02-09
Hi,

I'm interesting in hearing if anyone has any experience to share with using a budget GPS device and [gpsd]("http://gpsd.berlios.de/gpsd.html#ntp") to be an [NTP stratum 1 server]("http://www.eecis.udel.edu/~ntp/ntpfaq/NTP-s-algo.htm#Q-ALGO-BASIC-STRATUM-1").

I can find USB GPS dongles for $25 USD online.  What I'd like to know is if it's worth the effort.

Please do not reply with "you should just get your time over the network" because I'm in a location where that is not possible.

Thanks

---

### Post by tgalati4 on 2010-02-09
You should just get your time over the network.

Oh, well, then gpsd would be the next best thing.

You don't need to classify yourself as a stratum 1 server.  I don't think consumer gps dongles would meet chronometer specifications.

But you can serve time locally (on your LAN) using gpsd as a time base.

Set up your ntp.conf file appropriately:  (this is from a Dapper Drake machine)

tgalati4@tubuntu2:/etc$ cat ntp.conf
# Updated 20 Oct 08 to add new servers
logfile /home/tgalati4/ntp_stuff/ntp_trace.log
driftfile /var/lib/ntp/ntp.drift
# The next 4 lines adds statistics to /var/log/ntpstats--hopefully
statistics loopstats peerstats #  clockstats
statsdir /var/log/ntpstats/
filegen peerstats file peers type day link enable
filegen loopstats file loops type day link enable
# filegen clockstats file clockstats type day link enable
server tick.cs.unlv.edu
server tick.mtnlion.com
#server tick.jpunix.net
server ntp1.stsn.net
server north-america.pool.ntp.org
server time.apple.com
# Beef up security policy--see hpubuntu's /etc/ntp.conf
restrict default kod notrap nomodify nopeer noquery
restrict 127.0.0.1 nomodify
broadcast 192.168.1.255

----------------

If you collect statistics, you can print out some neat graphs to determine how well your clock compares to peers.  With error-correction, your local system clock can be within 1 millisecond of the "master clock".

When you broadcast time on your local network, linux machines on that network will synchronize automatically.

---

### Post by nutznboltz on 2010-02-09
Oh, I found this:

[http://lists.berlios.de/pipermail/gpsd-users/2006-September/001960.html](http://lists.berlios.de/pipermail/gpsd-users/2006-September/001960.html)

and this:

[http://gpsd.berlios.de/hardware.html#timing](http://gpsd.berlios.de/hardware.html#timing)

---

### Post by nutznboltz on 2010-02-10
So according to the gpsd hardware compatibility page the SiRFstar3 (GlobalSat MR-350P) with the DB-9 RS232 serial + PS2 option cable will deliver high accuracy pulse-per-second (PPS) for use with NTP.

Note that you need a computer with DB-9 RS232 serial.  The power for the GPS comes through a PS2 port but it should be possible to use an adapter for USB to PS2 since they both use 5 volts.

```
USB pinout

1 VCC +5V
2
3
4 GND ground

PS/2 mouse and keyboard pinout

1
2
3 GND ground
4 VCC +5V
5
6

MR-350P -> PS/2 male -> PS/2 female adapter to USB for +5 volts DC
   |
   V
9-pin RS232

```

Also there are caveats about reception not being good indoors in all cases.

---

### Post by tgalati4 on 2010-02-10
Indoor reception can be crappy.  Moisture and nails in the roof can degrade the signal quite a bit.  You want it near a window or outside if possible.  It needs a clear view of the entire sky.  Trees blocking a sector will clobber any satellites in that sector.

Most USB gps pucks work fine with gpsd.  There is a serial-to-USB converter inside the device (PL2303 typically) so you don't need to fuss with a serial connection.  You just need to specify the device when starting gpsd.  Typically a usb puck will by at /dev/ttyUSB0 or something similar.  Just take note of the time you plugged in the device and then compare that to when the device file got created.  The device file gets created a few seconds after plugging in the USB device.

The links you provided just demonstrate that a serial connection is syncronous.  A USB signal is asyncronous, so it can't be as accurate.  The demonstrated USB accuracy is 250 ms, which is a 1/4 second.  Certainly good enough for home use.

I have a nokia n800 and I have used a little utility called gps-clockd that adjusts the time on the device with the average gps time.  It's compiled for ARM processor.  Perhaps there is a debian version for x86.  Try contacting the author for the source code.

[http://nitapps.com/](http://nitapps.com/)

---

### Post by hvengel on 2011-07-04
GPSD is not needed.  The linux kernel has had build in PPS support since 2.6.32 and NTP has drivers that support all kinds of reference clocks including many GPS models.  

Some GPS models are highly optimized for time keeping and are widely used for that purpose.  For example the Motorola Oncore VT, UT, UT+ and M12T models are specifically for time keeping and the PPS pulse form these are accurate to with in a few nanoseconds.  The M12T is considered the radio time keeping gold standard and with saw tooth correction, which is supported in the NTP driver, is accurate to +-2 nanoseconds (IE. +-0.002 microseconds).   

Working Oncore UT+ units are available on ebay as cell sight pulls for around $15 plus shipping but the added parts to create a fully functioning reference clock (ttl to RS-232 circuit and antenna and feedline) bring the cost of doing one of these into the $50 to $100 range depending on what parts you choose to use.  These are only a little less accurate than the M12T. Wiring up a working Oncore ref clock is not difficult but you do need to have a certain comfort level with this type of thing.  These use the ntp Oncore driver.    

Many users use the Garmin GPS-18 series for this as well.  These are  not timing specific although the PPS pulse is +- 1 microsecond.  These  are inexpensive (around $70 new) and simpler to wire up for this  purpose than the Oncore GPSs.  This requires about $5 of additional parts and these are supported by the  ntp NMEA driver. 

I have been using a Oncore UT+ GPS for some time with my Gentoo setup and am about to give it a try with Ubuntu 11.04.  The 11.04 kernel is build with the PPS related modules available (pps_core and pps_ldisc) but I have not gotten far enough to know if the ntp build has reference clock support.   

Also for those wondering why go to the effort.  First you will no longer need a network connection to have accurate time.  Second your clock will be MUCH more accurate than using a network based time server.  I typically see times that are microsecond accurate once the system clock has stabilized and synced with the GPS.  In general using a remote time server will get the clock synced to within perhaps 5 milliseconds so we are talking more than 3 orders of magnitude more accuracy with a local reference clock.  In addition it is an interesting and inexpensive project for those who like that sort of thing.

The PPS line from the GPS can be wired to the DCD line of a serial port or to the parallel port (never done this myself) for current un-patched kernels to work.  There are kernel patches that allow you to wire this to a GPIO pin but this also requires that you run wires to the motherboard.

NTP and the kernel PPS stuff will work with any PPS source and GPS's that have a PPS but no device specific NTP driver can still be used although you will have to do some work arounds.

---

### Post by hvengel on 2011-07-04
Just found that the stock ntp in Ubuntu does NOT have reference clock support built in.

Also is there a version of the ntp package available from some 3rd party that is built with reference clock support?  If not is there an "Ubuntu way" of hand building software such that the package manager knows what is going on?

---

