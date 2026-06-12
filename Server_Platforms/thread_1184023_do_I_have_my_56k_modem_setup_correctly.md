---
title: "do I have my 56k modem setup correctly?"
date: 2009-06-10
forum: Server Platforms
---

### Post by kustomjs on 2009-06-10
Hi Guys
I just wanted to know if I got my modem setup correctly because when I did a scan using: wvdialconf it comes back with this:

this is on my server 8.04 TLS.

```
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: Scanning ttySHSF0 first, /dev/modem is a link to it.
WvModem<*1>: Cannot set information for serial port.
ttySHSF0<*1>: ATQ0 V1 E1 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 Z -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySHSF0<*1>: Modem Identifier: ATI -- 56000
ttySHSF0<*1>: Speed 4800: AT -- OK
ttySHSF0<*1>: Speed 9600: AT -- OK
ttySHSF0<*1>: Speed 19200: AT -- OK
ttySHSF0<*1>: Speed 38400: AT -- OK
ttySHSF0<*1>: Speed 57600: AT -- OK
ttySHSF0<*1>: Speed 115200: AT -- OK
ttySHSF0<*1>: Speed 230400: AT -- OK
ttySHSF0<*1>: Speed 460800: AT -- OK
ttySHSF0<*1>: Max speed is 460800; that should be safe.
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- æø
ttyS0<*1>: failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   SHSF1 SHSF2 SHSF3 SHSF4 SHSF5
Modem Port Scan<*1>: SHSF6 SHSF7

Found a modem on /dev/ttySHSF0, using link /dev/modem in config.
Modem configuration written to /etc/wvdial.conf.
ttySHSF0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

```

---

### Post by zharmad on 2009-06-10
From the looks of it the system was able to query your modem using AT commands with no problem, and it couldn't find any other modem of ttyS0 so the program gave up. It should be configured right, but the best way to find out would be to try to use it.

---

### Post by kustomjs on 2009-06-10
so how would I get this modem configured for dial up/in server? and I also have ethernet card on this server also that is working just fine.

I just need to know how to configure this 56k modem for the dial up/in server.

---

### Post by cariboo on 2009-06-10
Have a look [here]("http:///www.linux.net.nz/pppconfig/"), this may help you create a script to allow you to connect to your isp.

---

### Post by kustomjs on 2009-06-10
I am not trying to connect to ISP I am trying to make my own dial up server.

---

